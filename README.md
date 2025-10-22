<h1>Exp-No 5 : Implement Simple Hill Climbing Algorithm</h1> 
<h3>Name: Sanjana Sri N         </h3>
<h3>Register Number: 2305003007            </h3>
<H3>Aim:</H3>
<p>Implement Simple Hill Climbing Algorithm and Generate a String by Mutating a Single Character at each iteration </p>
<h2> Theory: </h2>
<p>Hill climbing is a variant of Generate and test in which feedback from test procedure is used to help the generator decide which direction to move in search space.
Feedback is provided in terms of heuristic function
</p>


## Algorithm: Hill Climbing String Matching

1. Evaluate the initial state:

    - Generate a random string of the same length as the target string.

      If the random string matches the target string, stop — it is the goal state.
 
      Otherwise, continue with this random string as the current state.

2. Loop until the goal is found (or no improvement occurs):

    - Randomly select a position in the string.

    - Replace the character at that position with a random printable character.

    - Evaluate the fitness (difference) between this new string and the target string.

3. Evaluate the new state:

    - If the new string exactly matches the target string, return it and quit (goal state reached).

    - If the new string is closer (better score) to the target string than the previous best,
      make this new string the current best (move to this state).

    - If the new string is not better, discard it and continue the loop with the current state.

4. Repeat the above steps until the string completely matches the target string (score = 0).
   
<hr>
<h3> Steps Applied:</h3>
<h3>Step-1</h3>
<p> Generate a random string (sol) of the same length as the target string entered by the user.
This is the initial state.</p>
<h3>Step-2</h3>
<p>Select one random character position and mutate it — replace that character with a random printable character.
This produces a new candidate string.</p>
<h3>Step-3</h3>
<p> Compute the fitness function (score) using:</p>

<img width="343" height="68" alt="image" src="https://github.com/user-attachments/assets/5422d120-1978-4292-b9cf-ba04f5c1c01a" />

<P>for every character pair (a, b) from the candidate string and the target string.
A smaller score means the candidate string is closer to the target.</P>
<h3>Step-4:</h3>
<p> If the new string has a lower score (better fit) than the current best,
make it the new best string.
Otherwise, continue mutating without updating.</p>
<h3>Step-5</h3>
<p>Repeat Steps 2–4 until the score becomes zero — meaning the generated string matches the target exactly.
Then, print the final string and stop (global minimum reached).</p>

## SAMPLE PROGRAM
```python
import random
import string
def generate_random_solution(answer):
    l=len(answer)
    return [random.choice(string.printable) for _ in range(l)]
def evaluate(solution,answer):
    print(solution)
    target=list(answer)
    diff=0
    for i in range(len(target)):
        s=solution[i]
        t=target[i]
        #to calculate the "difference" between two strings, character by character.
        #ord(s) - ord(t) calculates the difference between the ASCII values of the characters s and t.
         #abs() takes the absolute value of this difference to ensure that it is non-negative. This is important because the difference could be negative if s is less than t in terms of ASCII value.
         #The absolute value ensures that the difference is always positive or zero.
        diff += abs(ord(s) - ord(t))    return diff
def mutate_solution(solution):
    ind=random.randint(0,len(solution)-1)
    solution[ind]=random.choice(string.printable)
    return solution
def SimpleHillClimbing():
    answer="Artificial Intelligence"
    best=generate_random_solution(answer)
    best_score=evaluate(best,answer)
    while True:
       print("Score:", best_score, " Solution: ", "".join(best))  
       if best_score == 0:
           break
       new_solution = mutate_solution(list(best))
       score = evaluate(new_solution, answer)
       if score < best_score:
           best = new_solution
           best_score = score
SimpleHillClimbing()
```

<hr>
<h2>Sample Input and Output</h2>
<h2>Sample String:</h2> Artificial Intelligence
<h2>Output:</h2>

<img width="1164" height="531" alt="image" src="https://github.com/user-attachments/assets/28af10cf-3585-4977-9fcd-9f0c758c10ab" />
.
.
.
.
<img width="1155" height="504" alt="image" src="https://github.com/user-attachments/assets/444ae76f-71d3-4f73-8acd-b6320ee960a4" />

## PROGRAM:
```python
import random, string

def hill_climb():
    target = input("Enter the target string: ")
    sol = [random.choice(string.printable) for _ in target]
    score = lambda s: sum(abs(ord(a) - ord(b)) for a, b in zip(s, target))
    best, best_score = sol, score(sol)

    while best_score:
        print(best_score, "".join(best))
        new = best.copy()
        new[random.randrange(len(new))] = random.choice(string.printable)
        new_score = score(new)
        if new_score < best_score:
            best, best_score = new, new_score

    print("Final:", "".join(best))

hill_climb()

```
<hr>
<h2>Input and Output</h2>

<h3> String:</h3> COMPUTER

<h2>Output:</h2>

<img width="923" height="485" alt="image" src="https://github.com/user-attachments/assets/f4f6e5da-9e33-49fd-982a-0cdf880c3af5" />

<img width="797" height="474" alt="Screenshot 2025-10-17 133603" src="https://github.com/user-attachments/assets/532e7452-2400-4569-919d-15a0d31e38cd" />


## RESULT:

Thus the program to Implement Simple Hill Climbing Algorithm has been executed successfully.
