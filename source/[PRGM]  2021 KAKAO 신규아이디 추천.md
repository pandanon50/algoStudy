# [프로그래머스] [2021 KAKAO] 신규 아이디 추천

[https://programmers.co.kr/learn/courses/30/lessons/72410]

### 문제 접근 방법
    1. 문자열 구현 문제
    2. 문제 순서를 보면서 하나씩 적용
### 코드
```
def comma(arr):
    temp = arr
    if len(arr) != 0:
        if arr[0] == '.': 
            temp = arr[1:]
        if arr[-1] == '.': 
            temp = arr[:-1]
    return temp

def solution(new_id):
    answer = ''
    exc = '0123456789abcdefghijklmnopqrstuvwxyz-_.'
    answer = new_id.lower()
    temp = ''
    for item in answer:
        index = exc.find(item)
        if index != -1:
            temp += item
    answer = ''
    count = 0
    for item in temp:
        if item == '.':
            count+=1
        else:
            if count >= 1:
                answer+='.'
            answer+=item
            count = 0
    answer=comma(answer)
    if len(answer) == 0:
        answer ='a'
    if len(answer) > 15:
        answer = answer[0:15]
        answer = comma(answer)
    if len(answer) < 3:
        while len(answer) < 3:
            answer += answer[-1]        
    return answer
```

### 시간 복잡도
    O(string length)

### 공간 복잡도

### 해결하지 못한 이유 & 어려웠던 점
    정규식이나, 다른 문법으로 깔끔하게 표현할 수 있는 아쉬움이 있엇음.
### 피드백 정리
