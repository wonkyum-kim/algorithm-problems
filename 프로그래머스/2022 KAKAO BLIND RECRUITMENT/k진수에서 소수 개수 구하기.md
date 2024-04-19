## k진수에서 소수 개수 구하기

양의 정수 n을 k진수로 바꾸는 방법은 JS에서 쉽게 할 수 있습니다.

```js
const result = n.toString(k);
```

그리고 `0`을 기준으로 문자열을 분리한 후, 각 문자열이 소수인지 확인합니다.

## 코드

```js
function isPrime(n) {
  if (n < 2) return false;
  for (let i = 2; i <= Math.floor(Math.sqrt(n)); ++i) {
    if (n % i === 0) return false;
  }
  return true;
}

function solution(n, k) {
  const changed = n.toString(k).split('0');

  const ans = changed.reduce((acc, str) => {
    if (str !== '' && isPrime(parseInt(str))) {
      return acc + 1;
    }
    return acc;
  }, 0);
  return ans;
}
```
