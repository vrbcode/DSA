# 🚀 Live Class Monitoring Dashboard  
### 📊 Track Learner Submissions & Status

> ## ⚠️ Important Note to Instructor
>
> - 🔓 Please **unlock all assignment problems** before starting the session.
> - 📈 Keep the **Metabase Live Tracking Query** open in another tab throughout the session to monitor real-time learner progress.

---

# 📌 Agenda & Session Overview

| ⏱️ Duration | 🎯 Problem | 💡 Core Technique / Pattern |
|------------|------------|-----------------------------|
| 15 mins | Ath Largest Element in Every Window | Min-Heap / Max-Heap Window Tracking |
| 15 mins | Merge K Sorted Lists | Min-Heap / Priority Queue |
| 15 mins | Free Cars | Greedy + Min-Heap |
| 15 mins | Distribute Candy | Two-Pass Greedy |

---

# 🏢 Problem 1: Ath Largest Element in Every Window

## 📄 Problem Statement

Given an integer **A** and an array **B** of size **N**, find the **Ath largest element** in every prefix window from **0 to i**.

If the number of elements is less than **A**, output **-1**.

---

## 🖼️ Illustration

<p align="center">
  <img src="https://raw.githubusercontent.com/vrbcode/DSA/main/assets/images/ath-illu.svg" width="650" alt="Meeting Rooms II Heap Visualization"/>
</p>

---

## 🎥 Animation

<p align="center">
<img src="./images/ath-largest-animation.gif" width="700"/>
</p>

---

## 🔄 Flowchart

<p align="center">
  <img src="https://raw.githubusercontent.com/vrbcode/DSA/main/assets/images/ath-flow.svg" width="650" alt="Meeting Rooms II Heap Visualization"/>
</p>
---

## 📊 Dry Run

<p align="center">
  <img src="https://raw.githubusercontent.com/vrbcode/DSA/main/assets/images/ath-dry.svg" width="650" alt="Meeting Rooms II Heap Visualization"/>
</p>
---

## 💡 Heap Visualization

<p align="center">
  <img src="https://raw.githubusercontent.com/vrbcode/DSA/main/assets/images/ath-heap.svg" width="650" alt="Meeting Rooms II Heap Visualization"/>
</p>
---

## Example

### Input

```text
A = 4
B = [1,2,3,4,5,6]
```

### Output

```text
[-1,-1,-1,1,2,3]
```

### Explanation

- i = 0,1,2 → Window size < 4 → -1
- i = 3 → [1,2,3,4] → 4th largest = 1
- i = 4 → [1,2,3,4,5] → 4th largest = 2
- i = 5 → [1,2,3,4,5,6] → 4th largest = 3

---

> ## ⏱️ Learner Exercise (3 mins)
>
> Ask students:
>
> **"Why do we only need to keep track of A elements instead of sorting every element processed so far?"**

---

# 🐢 Approach 1 — Brute Force

## Idea

For every index:

- Take subarray **0...i**
- If size < A → answer = -1
- Otherwise
  - Sort descending
  - Pick Ath element

---

## Complexity

| Approach | Time | Space |
|----------|------|-------|
| Brute Force | O(N² log N) | O(N) |

---

# ⚡ Approach 2 — Min Heap (Optimal)

> ## ⏱️ Discussion & Coding (7 mins)
>
> Maintain a **Min Heap of size A**.
>
> The heap top always represents the **Ath Largest Element**.

---

## Execution Logic

1. Create Min Heap
2. Traverse array
3. Insert current element
4. If heap size > A
   - remove smallest
5. If heap size < A
   - answer = -1
6. Else
   - answer = heap.peek()

---

## 💻 Pseudocode

```text
function solve(A,B):

    heap = MinHeap()

    for element in B:

        heap.push(element)

        if heap.size > A:
            heap.pop()

        if heap.size < A:
            answer = -1
        else:
            answer = heap.peek()

    return answer
```

---

## Complexity

| Time | Space |
|------|-------|
| O(N log A) | O(A) |

---

# 🔢 Problem 2: Merge K Sorted Lists

## 📄 Problem Statement

Given **K sorted linked lists**, merge them into one sorted linked list.

---

## 🖼️ Illustration

<p align="center">
<img src="./images/merge-k-illustration.svg" width="700"/>
</p>

---

## 🎥 Animation

<p align="center">
<img src="./images/merge-k-animation.gif" width="700"/>
</p>

---

## 🔄 Flowchart

<p align="center">
<img src="./images/merge-k-flowchart.svg" width="700"/>
</p>

---

## 📊 Dry Run

<p align="center">
<img src="./images/merge-k-dryrun.svg" width="700"/>
</p>

---

## Example

### Input

```text
[
1 -> 4 -> 5,
1 -> 3 -> 4,
2 -> 6
]
```

### Output

```text
1 -> 1 -> 2 -> 3 -> 4 -> 4 -> 5 -> 6
```

---

> ## ⏱️ Learner Exercise (3 mins)
>
> Ask:
>
> **"Which data structure helps us obtain the minimum head among K lists in O(log K)?"**

---

## 💡 Core Insight

Only the current heads of every list can be the smallest element.

Store all heads inside a **Min Heap**.

---

## Algorithm

1. Push all non-null heads
2. Create dummy node
3. Repeat until heap empty
   - Pop minimum
   - Attach to answer
   - Push next node

---

## 💻 Pseudocode

```text
function mergeKLists(lists):

    heap = MinHeap()

    for head in lists:
        if head != null:
            heap.push(head)

    dummy = ListNode(0)
    tail = dummy

    while heap not empty:

        node = heap.pop()

        tail.next = node

        tail = tail.next

        if node.next:
            heap.push(node.next)

    return dummy.next
```

---

## Complexity

| Approach | Time | Space |
|----------|------|-------|
| Sort Everything | O(N log N) | O(N) |
| Min Heap | O(N log K) | O(K) |

---

# 🎯 Problem 3: Free Cars

## 📄 Problem Statement

Each car has

- Deadline
- Profit

Buying a car takes **1 unit of time**.

Find the maximum possible profit.

---

## 🖼️ Illustration

<p align="center">
<img src="./images/free-cars-illustration.svg" width="700"/>
</p>

---

## 🎥 Animation

<p align="center">
<img src="./images/free-cars-animation.gif" width="700"/>
</p>

---

## 🔄 Flowchart

<p align="center">
<img src="./images/free-cars-flowchart.svg" width="700"/>
</p>

---

## Example

### Input

```text
Deadline = [1,3,2,3,3]

Profit = [100,200,150,50,80]
```

### Output

```text
530
```

---

## Explanation

- t = 0 → 100
- t = 1 → 150
- t = 2 → 200

Optimal replacement with heap results in **530**

---

## ⚙️ Approach Comparison

```text
Brute Force
      ↓
O(2ⁿ)

Greedy + Min Heap
      ↓
O(N log N)
```

---

> ## ⏱️ Discussion (5 mins)
>
> Sort by deadline first.
>
> If schedules conflict,
> replace the minimum profit job.

---

## 📊 Dry Run

| Step | Car | Heap | Time | Action |
|------|-----|------|------|--------|
|1|(1,100)|100|1|Add|
|2|(2,150)|100,150|2|Add|
|3|(3,200)|100,150,200|3|Add|
|4|(3,80)|100,150,200|3|Ignore|
|5|(3,50)|100,150,200|3|Ignore|

---

## 💻 Pseudocode

```text
sort by deadline

heap = MinHeap()

time = 0

for each car

    if deadline > time

        push profit

        time++

    else if profit > heap.peek()

        pop

        push profit

return sum(heap)
```

---

## Complexity

| Time | Space |
|------|-------|
| O(N log N) | O(N) |

---

# 🍬 Problem 4: Distribute Candy

## 📄 Problem Statement

Every child must receive

- at least one candy
- higher rating ⇒ more candy than neighbors

Return minimum candies required.

---

## 🖼️ Illustration

<p align="center">
<img src="./images/distribute-candy-illustration.svg" width="700"/>
</p>

---

## 🎥 Animation

<p align="center">
<img src="./images/distribute-candy-animation.gif" width="700"/>
</p>

---

## 🔄 Flowchart

<p align="center">
<img src="./images/distribute-candy-flowchart.svg" width="700"/>
</p>

---

## Example

### Input

```text
A = [1,5,2,1]
```

### Output

```text
7
```

---

### Explanation

```text
Candy

[1,3,2,1]

Total = 7
```

---

## 📊 Dry Run

| Index | Rating | Left Pass | Right Pass | Final |
|-------|--------|-----------|------------|-------|
|0|1|1|1|1|
|1|5|2|3|3|
|2|2|1|2|2|
|3|1|1|1|1|

---

> ## ⏱️ Discussion & Coding (10 mins)
>
> One pass cannot satisfy both neighbour conditions.
>
> Hence,
>
> ✔ Left → Right
>
> ✔ Right → Left

---

## Strategy

1. Initialize candies = 1
2. Left Pass
3. Right Pass
4. Take maximum
5. Sum all candies

---

## 💻 Pseudocode

```text
candies = [1...]

Left Pass

for i = 1

    if rating[i] > rating[i-1]

        candies[i] = candies[i-1] + 1

Right Pass

for i = n-2

    if rating[i] > rating[i+1]

        candies[i] = max(
            candies[i],
            candies[i+1] + 1
        )

return sum(candies)
```

---

## Complexity

| Time | Space |
|------|-------|
| O(N) | O(N) |

---

# 🎯 Session Summary

| Problem | Pattern | Time | Space |
|----------|---------|------|-------|
| Ath Largest Element | Min Heap | O(N log A) | O(A) |
| Merge K Sorted Lists | Priority Queue | O(N log K) | O(K) |
| Free Cars | Greedy + Min Heap | O(N log N) | O(N) |
| Distribute Candy | Two Pass Greedy | O(N) | O(N) |

---

# 📚 Key Takeaways

- ✅ Fixed Size Min Heap
- ✅ Priority Queue
- ✅ Greedy Scheduling
- ✅ Heap Replacement
- ✅ Two-Pass Greedy
- ✅ Dry Run First, Then Code
- ✅ Complexity Analysis

---

<div align="center">

### ⭐ Happy Coding! ⭐

Made with ❤️ for Live DSA Classes

</div>
