# Computational Thinking For Problem Solving (University of Pennsylvania Engineering Online Learning)

## 4 pillars of computational thinking:
- Decomposition (taking a complex problem and breaking it into more manageable sub-problems)
- Pattern Recognition (after decomposing we'll find common patterns amongst sub-problems - good for desired repetitive tasks for several identical data in any area in life)
- Data Representation and Abstraction (determining what inputs of problem are important)
- Algorithms (step by step instructions on how to solve the problem and this course uses flowchart for instructions but ill be translating that to pseudocode)   

algorithm cross_street()
  look to the right
  look to the left
    if car coming
      do not cross
    else
      cross
    return

## Common Algorithms pt.1 (unordered Largest/smallet value)
exs:

1) There's a list of values and you want to create an algorithm that returns the largest value in that list:

1.1) My first idea was:

algorithm find_largest()
  set index0 of list to max_so_far variable # the current max recorded as list is iterated
  iterate the next value
  compare new_value and max_so_far
  if
    new_value>max_so_far
    max_so_far=new_value
  go back to "iterate the next value"
  return max_so_far

1.2) My flowchart-to-pseudocode solution was interpreted like:

algorithm find_largest()
get input list
  if input empty
    stop
read the first item in list and store it in "max" variable
if for item in list, item>max  
  max = item
  are there any other items in the list?
    read next untested item
    go back to "if for item in list, item>max"
  else
    return max
    stop
else
  go back to "are there any other values in the list?" line

1.3) Chatgpt's solution for pseudocode was:
checks if the list is empty first. If not, it sets the first item as the initial maximum, then iterates through the remaining items to update the maximum as needed, finally outputting the largest value in the list.

Algorithm Find_Max()
    Input: list
    If list is empty then
        Output: "N/A"
        Stop
    End If
    
    Read first item in list and store value in max

    While there is an untested item in list
        Read next untested item
        If item > max then
            Store item in max
        End If
    End While

    Output: max
    Stop
End Algorithm

1.4) Actual solution was:
algorithm find_largest()
  input: list_collection
  output: max_so_far_value
max_so_far_value = list_collection[0]
for item in list_collection:
  if item > max_so_far_value:
    max_so_far_value = item
output max_so_far
stop

1.5) extra: now find the smallest value

algorithm find_smallest()
get list
  if list empty
  stop
min = [0]list
if for item in list, item<min:
  min = item
  are there any other items in the list?
    read next item
    go back to "if for item in list, item<min:" line
  else
    return min
    stop
else
    go back to "are there any other items in the list?" line

## Common Algorithms pt.2 (unordered Linear Search - does a collection contain a value?)
exs:

1) determine whether a list of values contains a target value:

1.1) My first idea was:
algorithm_linear_search()
have a data point defining target_value
iterate list 1-by-1 or if data is better structured create a better algo to see if item==target_value

1.2) My flowchart-to-pseudocode translation was interpreted like:
algorithm_linear_search()
get input list
has this current item in list been compared to target_value?
if yes
  read next item in list
  if item == target
    return "true"
    stop
  else
    go back to "is there another item?" line
else
  return "false"
  stop

1.3) Chatgpt's Solution to Flowchart was:
i mean it's in the wording itself. it literally just compares each item to a target and only spits out something if there's a match. so it's basically a loop of comparisson against the same value and if nothing comes out as a match then it's a false.

Algorithm Linear_Search()
    Input: list, target_value
    While there is an untested item in list (only doesnt work for 1st value if list is empty)
        Read next item in list (this is the item i was considering in the previous line)
        If item == target_value then
            Output: true
            Stop
        End If
    End While
    Output: false
    Stop
End Algorithm

1.4) Actual solution as seen in 3.5
algorithm linear_search
  inputs: list_collection, target_value
  output: true if match, false if not
for item in list_collection:
  if item=target
  then output: true
    stop
output: false


## Common Algorithms pt.3 (Algorithmic complexity - how long will algo take to execute if input increases?)

Complexity is just an expression of the number of operations in an algorithm.

You tend to focus on the worst case scenario, so i need an answer as to what the worst case scenario is 

Going back to the algorithm find_largest, we made n-1 comparisons with n == # of items and it would always maintain no matter the linear operation performed on n - this means the # of comparissons is roughly the same as number of elements so the algorithm has linear complexity

Going back to the algotithm linear_search, regardless of whether there's a match or not, no matter item/target_value position, n size is irrelevant as algo stops when finds a match. but worst case scenario it doesnt find a match which should be worse than finding a match at last - therefore also linear complexity (no shit name of algo was linear search) as worst case scenario is n operations.

## Common Algorithms pt.4 (Binary Search - how long will algo take to execute if input increases?)

Here ordering lists is introduced to create better algos, therefore turning linear search into binary search in regards to most efficient algo

Since binary search is dividing by 2 as many times needed and worst case scenario is no match for maximum number of operations, this means it has y=log2(x) logarithmic complexity with y = number of comparisons/operations in worst case scenario and x the number of items in a list

exs:

1) determine whether a sorted list of values contains a target value

1.1) my first thought:
algorithm_binary_search()
get sorted list
loop break list in half with 1 pointer at one item
if pointer==target, return true
if pointer>target
  remove pointer and any value above it from the searchable list
if pointer<target
  remove pointer and any value below it from the searchable list

1.2) interpretation of flowchart
i actually got it right but there's other ways to write it like chatgpt

1.3) chatgpt interpretation of flowchart:
This pseudocode continuously checks the middle element of the list. If it matches the target, it outputs true and stops. Otherwise, it eliminates either the first or last half of the list based on whether the middle element is less than or greater than the target. If the list becomes empty without finding the target, it outputs false.

Algorithm Binary_Search()
    Input: list, target_value

    While list is not empty
        Read middle item, mid
        If mid == target_value then
            Output: true
            Stop
        End If

        If mid < target_value then
            Eliminate mid and first half of list
        Else
            Eliminate mid and last half of list
        End If
    End While

    Output: false
    Stop
End Algorithm

## Common Algorithms pt.5 (Brute Force)

In this example brute force had an exponential complexity of 2^n since for each meeting of the group of meetings was either apart of the solution or not

Worst way to employ brute force is when permutations (order) matters like a djiskra type algo for shortest multi path since all # possibilities == n! so this is actually named factorial complexity

A few years ago, I taught a class with eight teaching assistants and I wanted to meet all of them once a week. I know the students are busy and it would be hard to get all of us together in the same place at a reasonable time of day. So, I gave them five options for meeting times as you see here, and then I wanted to choose some combination of meeting times so that I could meet each TA at least once during the week, even if it meant having multiple meetings. So, an algorithm we could use here is to use brute force to find all possible combinations of the five meeting times and then identify those combinations where I can meet all TA's and then optimize it by finding the combination with the smallest number of meetings because I'm busy too. So, how many possible solutions are there? To determine the number of possible solutions using brute force, we can look at each potential meeting time and say that we either will or will not include it in the solution. For example, from Monday 4:00 PM, I either do or do not have a meeting at that time. So, there are two options for Monday 4:00 PM because I either do or do not include it in the solution. Likewise for Tuesday 6:00 PM, I either do or do not include it in the combination of meeting times. So, there are two options for it as well and so on. Now let's look at the combinations of options like we did for the museum example starting with just the first two times. One combination is to have meetings at both Monday 4:00 PM and Tuesday 6:00 PM. That is, I can include both in my solution. Another combination is to have a meeting on Monday at 4:00 PM but not Tuesday 6:00 PM, that's part of another solution. The third combination is to not meet on Monday at 4:00 PM, but to meet Tuesday at six, that's yet another solution. The fourth combination of these two times is to not have meetings at either time. So, you see again that we're just multiplying the number of options. For each of the five meeting times, we either do or do not include it. 

## Common Algorithms pt.6 (Greedy Algorithms)

A simple approach that doesn't always give the best algorithm solution but it's close to optimal in much less time. Contrary to brute force, you make a decision that seems best currently (just the mental translation of "you gotta start somewhere" and you eye-scan the best option to start with) and keep repeating the same decision until done. So in a way greedy algorithms are better for human use vs computer use to get a somewhat right answer with a large input size.

So let's assume i got a daily schedule full of classes and some breaks. I want to solve the problem of my laptop battery going dead, therefore i need to charge it during class breaks. but i want to charge it as few times as possible. instead of looking at all possible breaks and going brute force thinking "i either charge or not charge per every break", a greedy algorithm that only charges right after or before battery going dead for the first time and repeating for next times might very well be the optimal solution.

## Case Studies

The centre problem had 27 groups requesting meetings and they wanted to meet as many as possible.
1st decompose into subproblems determining which group to meet and when to remove conflicting requests
2nd through pattern recognition realise that the loop is to look at requests and choosing the best one (we ended up choosing the one with the earliest starting time or ending time ex. even if meeting A starts at 8:00 am, meeting B can have prevailance over meeting B if meeting B ends before meeting A)
3rd through data representation and abstraction meeting requests are represented using start and end times
4th through algorithms choose a request to schedule and remove conflicting requests and repeat until done

The pseudocode for this can be found in 3.5

This was chatgpt's attempt at it: 

Algorithm Scheduling()
    Input: Collection of all requests

    If collection is empty then
        Output: schedule
        Stop
    End If

    Set earliest_request to first request in collection

    While there are more requests in collection
        Look at next request
        If end time of next request is before end time of earliest_request then
            Set next request as earliest_request
        End If
    End While

    Add earliest_request to schedule

    While there are more requests in collection
        Look at next request
        If start time of next request is before end time of earliest_request then
            Remove next request from collection
        End If
    End While

    Repeat process with remaining requests

    Output: schedule
    Stop
End Algorithm


In regards to complexity, even though both loops, individually, are linear, you have an inner loop within a outter loop so if you increase input size you'll have to do twice as many things, twice as many times == quadratic/n^2 complexity as 2x inputs results in 4x as many operations

Then the dog center problem.
1st decompose subproblems: determine similarity, find 3 most similar dogs, do a majority vote for disaster search and rescue suitability prediction
2nd pattern recognition: repeated process of calculating similarity for each dog using each individual test result
3rd data representation and abstraction: dogs are represented as test results, as well as whether they are suitable for disaster search and rescue
4th algorithm: calculate similarity for each dog, find 3 max similarity values between a pair of dogs, count number of similar dogs that are suitable for disaster search and rescue via creating some logic around quantifying the qualitative aspects of the problem

The pseudocode for this can be found in 3.5

This was chatgpt's attempt at it:

Algorithm Prediction()
    Input: collection of dogs, new_dog

    While there are more dogs in collection
        Calculate similarity between this dog and new_dog
    End While

    Repeat 3 times
        Set most_similar_dog to first dog in collection
        
        While there are more dogs in collection
            Look at next dog
            If this dog is more similar to new_dog than most_similar_dog then
                Set this dog as most_similar_dog
            End If
        End While
        
        Add most_similar_dog to list of similar dogs
        Remove most_similar_dog from collection
    End Repeat

    Set vote to 0

    For each dog in list of similar dogs
        If dog is suitable for Search & Rescue (S&R) then
            Increment vote
        End If
    End For

    If vote >= 2 then
        Output: "suitable"
    Else
        Output: "not suitable"
    End If

    Stop
End Algorithm

This is actually a popular machine-learning algorithm known as K-Nearest Neighbors. For some value of k, which is usually odd like three in this case, we find the most similar or nearest elements for which we already know some piece of info and use that to predict the info for some new elements.

So, what's the complexity of this algorithm? This algorithm consists of three parts, calculating the similarity of each dog, finding the three most similar dogs and conducting the vote. The first part is definitely linear. We do the calculation once for each dog. If there are twice as many dogs, it takes twice as many steps. The second part is also linear. In finding the most similar dog, we look at each dog in the list once. If we had twice as many dogs, we'd need to do twice as many comparisons. Now, you might say "Wait, isn't this quadratic like the scheduling algorithm, since we have the loop within a loop?" But, it doesn't matter that we go through the list three or five or a hundred times, because it's independent of the number of dogs. So, it's linear overall. If we doubled the number of dogs, we only double the number of steps. Conducting the vote is also linear. In the worst case, if we were doing a vote over all the dogs, then we'd have to look at each dog's value and that's linear. Since all parts of the prediction algorithm are linear, the algorithm as a whole is also linear. Because again, if for instance, we doubled the number of inputs, we have to do all the parts twice as many times. So overall, we just have twice as many total operations, which means it's linear.

Finishing thoughts by the professor: When I was a graduate student, I taught an introduction to computer science class, and our textbook defined computer science as the study of algorithms. But, you don't have to be a computer scientist to think algorithmically or to use algorithms. As we've seen in this part of the course, there are lots of common algorithms and patterns among them. There are some basic algorithmic approaches that can be used in solving lots of different problems. Once we've used computational thinking and developed an algorithm, the next step is to express the algorithm to a computer. In order to do that, we need to know the language that the computer understands. But, in order to do that, we first need to know what the computer is capable of doing. That's what we'll see in the next part of the course.

# von Neumann architecture

Modern computing is done under this architecture where CPU instructions and data is stored separatly in RAM memory in an address.

Memory (RAM): Stores both program instructions and data. Memory is organized in bytes, with each byte being eight bits (binary digits), where each bit represents a value of either 0 or 1. The CPU accesses memory by unique addresses to either write or read data. Smaller data types like letters are stored in one byte, while larger numbers use multiple bytes (e.g., 2, 4, or 8 bytes).

CPU (Central Processing Unit): Executes program instructions, composed of:

Control Unit: Fetches, decodes, executes instructions, and moves to the next one, following a repetitive cycle. It uses registers (temporary memory) to store operands and results temporarily.
Arithmetic and Logic Unit (ALU): Handles basic math and logical operations, such as addition and comparison. These simple operations can be combined to implement complex algorithms.
Input/Output (I/O): Facilitates interaction between the computer and external devices (e.g., keyboard, mouse, monitor). Devices send signals (interrupts) to notify the CPU when they have data, and the CPU signals them when it has data to display or process.

Programming Basics: Writing a program is expressing an algorithm in a way the computer can understand. A program manipulates data, running an algorithm on that data, which is stored in memory at a specific address.

Memory Addresses and Variables:Modern computers automatically manage memory addresses, so programmers use variables (labels or names) to represent memory addresses.
This abstraction lets programmers focus on the data without needing to know its specific memory location, similar to using the label “Empire State Building” instead of knowing the actual address.

Types of Variables:
- Single Value Variables: Variables like count store individual values, such as a number or letter.
- Collections (Arrays): Variables can hold multiple values in contiguous memory locations, allowing for easy sequential access.
  - Example: values is a collection, where each element can be accessed by its index (e.g., values[2] for the third element in a zero-based index system).

Indexing in Collections:
- Many languages use zero-based indexing, where the first element has index 0.
- Indexing enables direct access to specific elements within a collection.

Objects: Objects allow grouping of values under a single name, with distinct labels for each attribute.
Example: A dog object named Jake might include properties like age and weight. The entire grouping is the object, but each property has its own label within that object.

Practical Use of Variables: Variables simplify memory operations by allowing read and write operations based on labels rather than actual memory addresses.
For example, assigning count = 0 writes 0 to memory at the address corresponding to count, determined by the CPU, not the programmer.

Now how does the control unit execute instructions within a program and provide conditional and iterative control for program flow?

Control Unit's Role in Execution:
- The control unit performs a repetitive four-step cycle: fetch, decode, execute, update, and then repeat.
- In simple cases, the control unit moves from one instruction to the next sequentially in memory. For instance, to add two numbers and store the result, the control unit fetches each number, sends them to the ALU (Arithmetic and Logic Unit) for addition, and writes the result to memory, then moves to the next instruction.

Conditional Execution:
- Conditional execution allows the program to perform one instruction in certain cases and a different one in others, an essential capability for flexible programming.
- This structure is often visualized in a flowchart and is handled by the control unit through an if-then-else construct. For example, the control unit may execute an instruction to compare values and, based on the result (true or false), direct the program to follow one of two possible instructions.
- In programming, these conditions are expressed as if-then-else or nested as if-then-elseif to handle more complex decision-making.

Loops and Iteration:
- Loops allow repeated execution of instructions until a specified condition is met. This flow is crucial for algorithms that require iteration.
- The loop checks a condition after each cycle; if true, the program returns to a previous instruction to repeat the steps. Once the condition evaluates to false, the loop exits, and the program continues with the subsequent instructions.

Programming Constructs:
- If-Then-Else Construct: Executes different instructions based on a condition.
- If-Then-ElseIf: A more complex version that checks multiple conditions in sequence.
- Loops: Used for repeated instruction execution based on a condition.

Application in Algorithms: With conditional and iterative control, the control unit's abilities align with foundational algorithmic structures. This knowledge prepares students to think about programming and algorithms in terms of conditions and repetitions, essential for writing efficient and logical code.

# Expressing algorithms in pseudocode

exs:

1) understand the pseudocode below:
stop ← number of items in list - 2
for each item in list
    for i in range 0 ... stop
		    if list[i] > list[i+1]
		    then
			    temp ← list[i]
			    list[i] ← list[i+1]
			    list[i+1] ← temp
output: list

Here is an explanation of the solution:

As the hint suggests, let’s create a simple input list with values {4, 2, 3, 1} and see what happens on each step.

1: stop is set to the number of items in list - 2, which is 4 - 2 = 2

2: we start looping and set item to the first element of the list, which is 4

3: we have another loop with i set to 0

4: we see if list[0] > list[1], which sees if 4 > 2, which is true

6: the variable temp holds list[0], which is 4

7: list[0] is set to list[1], which is 2, which means our list now contains {2, 2, 3, 1}

8: list[1] is set to temp, which is 4, so our list is now {2, 4, 3, 1}

3: we continue with the inner loop, with i now set to 1

4: we see if list[1] > list[2], which sees if 4 > 3, which is true

6: the variable temp holds list[1], which is 4

7: list[1] is set to list[2], which is 3, so now the list is {2, 3, 3, 1}

8: list[2] is set to temp, which is 4, so the list becomes {2, 3, 4, 1}

3: we continue the inner loop, with i now set to 2; note that because stop is 2, this is the last time we will execute this inner loop

4: we see if list[2] > list[3], which sees if 4 > 1, which is true

6: temp holds list[2], which is 4

7: list[2] is set to list[3], so the list is now {2, 3, 1, 1}

8: list[3] is set to temp, which is 4, so the list becomes {2, 3, 1, 4}

At this point it may be possible to speculate what this algorithm does after just one pass through the outer loop, but let’s do the outer loop one more time just to check. 

Let’s simplify things a bit, though, and note that lines 6-8 simply switch the values of list[i] and list[i+1]; we won’t walk through all three of those steps as we continue the example.

Now that we’ve completed the inner loop, we continue the outer loop, keeping in mind that list is now {2, 3, 1, 4}:

2: we continue looping and set item to the next element of the list, which is 3; note that item is not actually used anywhere other than line 2. All this does is ensure that the loop on lines 3-8 is executed the same number of times as there are items in the list.

3: we restart the inner loop with i set to 0

4: we see if list[0] > list[1], which sees if 2 > 3, which is false, so we do not execute lines 6-8

3: we continue with the inner loop, with i now set to 1

4: we see if list[1] > list[2], which sees if 3 > 1, which is true

6-8: we swap list[1] and list[2], so the list now becomes {2, 1, 3, 4}

3: we continue the inner loop, with i now set to 2

4: we see if list[2] > list[3], which sees if 3 > 4, which is false, so we do not execute lines 6-8, and because i reached the value of stop, we are done with the inner loop

Now the list is {2, 1, 3, 4}. Can you see what is happening? Let’s try one more:

2: we continue looping for the third time

3: we restart the inner loop with i set to 0

4: we see if list[0] > list[1], which sees if 2 > 1, which is true

6-8: we swap list[0] and list[1], so the list is now {1, 2, 3, 4}

3: we continue looping with i set to 1

4: we see if list[1] > list[2], which sees if 2 > 3, which is false

3: we continue looping with i set to 2

4: we see if list[2] > list[3], which sees if 3 > 4, which is false

Now we’re done with the inner loop and the list is {1, 2, 3, 4}. We do have one more iteration of the outer loop to perform, but we’ll stop here because perhaps you see what’s happening: as we go through the inner loop, bigger numbers are being swapped with neighboring smaller numbers so that the bigger numbers are moving to the right. Each time we do the outer loop, the biggest number moves all the way to the right, up until it hits the numbers that are bigger than it. The result is that the numbers end up in sorted order.

So the point of this algorithm is to sort a list in ascending order. It will, however, most likely do unnecessary operations to achieve that. Let's try an initial list [23, -345, 243, 0, 0, -40, 50]. So stop, the number of times the inner loop will run for each list item, equals 7-2=5. For the outer loop, in the 1st iteration it would set i=0, compare index 0 with index 1 (23 and -345) and since 23>-345 it swaps them and the current list becomes [-345, 23, 243, 0, 0, -40, 50]. Then do the same until i=5 where the current list after 1st outer loop iteration will be [-345, 23, 0, 0, -40, 50, 243]. Then repeat this until the 7th outer loop iteration is done where the current list will be [-345, -40, 0, 0, 23, 50, 243] - a fully ascending sorted list by comparing each element to the next one and swapping them if need be

This algorithm is known as bubble sort and is one of the simplest algorithms for sorting elements in a list. It is called bubble sort because on each iteration of the outer loop, the largest value “bubbles” its way to the top (or to the right), until it reaches its place in the sorted list.

Although bubble sort is simple to implement, it is very inefficient and exhibits quadratic complexity, meaning that an input of N elements would require around N^2 operations, and that doubling the input’s size would require four times as many operations. The most efficient sorting algorithms, such as merge sort and quick sort, require NlogN operations, which are much fewer than N^2 for large values of N, but are more complicated to implement.

# Case studies

Back to the center problem. Solution to it was:

algorithm centre_meetings
  inputs: requests_collection (elements with start and end times)
  output: scheduled_requests the full schedule that contains requests that don't overlap
while requests is not empty
  #find request to schedule using the greedy approach earlier in which we choose the meeting request with the earliest ending time. so this code is just going through the collection requests and finding the minimum value
  earliest_start_time = requests_collection[0]
  earliest_end_time = requests_collection[0].end_time (earliest end time to be the end time of the first request)
  for each request in requests_collection
    if request.end_time < earliest_end_time (if end time is less than the earliest end time we've seen so far)
    then
      earliest_request = request (update earliest request)
      earliest_end_time = request.end_time (and update earliest end time)
  add earliest_request to scheduled_requests (we now know earliest request represents the one with the earliest ending time and we add it to our collection which we'll use for holding the output)
      
  #remove any requests that cannot be scheduled
  for each request in requests (inner loop all the requests)
    if request.start_time < earliest_request.end_time
    then remove request from requests

Now back to the dog rescue problem. Solution was:

algorithm dog_rescue
  inputs: dogs_collection (elements that have values for catwalk_test, surface_test, conflict_test, suitable, and similarity to the new dog), and new_dog (same 3 elements but does not have similarity and suitable values)
  outputs: majority value of suitable for the 3 elements in dogs that have the highest similarity values - a prediction of whether new dog will be suitable for search and rescue. take the 3 dogs with highest similarity, then take the majority value for their suitable values

#calculate similarity for each dog
for each dog in dogs_collection
  dogs.similarity = 0
  if dog.catwalk_test = new_dog.catwalk_test
  then dog.similarity = dog.similarity + 1
  if dog.surface_test = new_dog.surface_test
  then dog.similarity = dog.similarity + 1
  if dog.conflict_test = new_dog.conflict_test
  then dog-similarity = dog.similarity + 1
  
#find 3 most similar dogs - This is very similar to the algorithm we saw on previous part of the course in which we look for the largest value in a collection, and it's also similar to the scheduling algorithm we just saw, except that that one was looking for the smallest value. Because we're looking for the three highest values, we'll repeat these steps three times.

loop 3x
  most_similar_dog = dogs[0] (lets say the most similar dog so far is the first iteration)
  highest_similarity = dogs[0].similarity (and lets assume the highest similarity so far is the first iteration)
  for each dog in dogs:
    if dog.similarity > highest_similarity
    then
      highest_similarity = dog.similarity (update highest_similarity variable by assigning the similarity of the iterated dog)
      most_similar_dog = dog (update most_similar_dog variable by assigning the iterated dog)
  add most_similar_dog to similar_dogs (add the most similar dog to a collection called similar_dogs)
  remove most_similar_dog from dogs (remove the recently added most similar dog from the list of all the other potential)

#find majority value for 3 most similar dogs - do a vote based on whether they were suitable for disaster search and rescue
vote = 0
for each dog in similar_dogs (iterate over the 3 dogs)
  if dog.suitable = true
  then vote = vote + 1
if vote ≥ 2 (since there are 3 dogs a majority would be 2 or more)
then output: true (the new dog is suitable for at least 2 of the most similar dogs)
else output: false
