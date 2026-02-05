## Solution to Problem 1

(a)

line 3; line3

(b)

line2; line5; line 5; line 1

## Solution to Problem 2

(a) Execution trace:

```
pow(2, 3)
-> if 3 > 0 then 2 * pow(2, 3 - 1) else 1
-> if true then 2 * pow(2, 3 - 1) else 1
-> 2 * pow(2, 3 - 1)
-> 2 * pow(2, 2)
-> 2 * (if 2 > 0 then 2 * pow(2, 2 - 1) else 1)
-> 2 * (if true then 2 * pow(2, 2 - 1) else 1)
-> 2 * (2 * pow(2, 2 - 1))
-> 2 * (2 * pow(2, 1))
-> 2 * (2 * (if 1 > 0 then 2 * pow(2, 1 - 1) else 1))
-> 2 * (2 * (if true then 2 * pow(2, 1 - 1) else 1))
-> 2 * (2 * (2 * pow(2, 1 - 1)))
-> 2 * (2 * (2 * pow(2, 0)))
-> 2 * (2 * (2 * (if 0 > 0 then 2 * pow(2, 0 - 1) else 1)))
-> 2 * (2 * (2 * (if false then 2 * pow(2, 0 - 1) else 1)))
-> 2 * (2 * (2 * 1))
-> 2 * (2 * 2)
-> 2 * 4
-> 8
```

(b) Tail-recursive implementation

```scala
def powTail(x: Int, n: Int): Int =
  def loop(acc: Int, i: Int): Int =
    if i < n then loop(acc * x, i + 1) else acc
  loop(1, 0)
```

Execution trace:

```
powTail(2, 3)
-> loop(1, 0)
-> if 0 < 3 then loop(1 * 2, 0 + 1) else 1
-> if true then loop(1 * 2, 0 + 1) else 1
-> loop(2, 1)
-> if 1 < 3 then loop(2 * 2, 1 + 1) else 2
-> if true then loop(2 * 2, 1 + 1) else 2
-> loop(4, 2)
-> if 2 < 3 then loop(4 * 2, 2 + 1) else 4
-> if true then loop(4 * 2, 2 + 1) else 4
-> loop(8, 3)
-> if 3 < 3 then loop(8 * 2, 3 + 1) else 8
-> if false then loop(8 * 2, 3 + 1) else 8
-> 8
```