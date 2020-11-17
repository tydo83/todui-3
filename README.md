# TodUI 3 - ToDONE

### A Note On Abstraction

Abstraction is the process of taking code and hiding it from yourself and other coders on the project. There are times when you might want to do this already to avoid repeating yourself. For example, we have two of the same loop displaying all of our todos. But if we want to change that how those todos are displayed (and we will), we'd have to hunt down the other loop after we're done. And there might be (there will be) more times we'll want to run that code. So! By putting it in a function, we'll have one place where we'll change the code if we need to, and otherwise we'll never have to look at it. It will, essentially, be hidden from us. (Often in another file!)

If at any point you find yourself duplicating code a few times, you might consider putting it in a function.

Up to you when to do this, but it's a good thing to practice thinking about!

Okay... let's begin.


### Displaying Numbers

The first thing we'll want is to change our todo-printing loop to display numbers instead of bullets. Why? So that our user can select a todo!

* The main thing you're going to want to do is convert your `for of` (which you should've defaulted to using!) into a `for i` loop, because we need to know which number each `todo` is at. But what's the relationship between each todo's index in the array and its number? The number is the `i` plus 1, because, of course, humans want to count starting at 1, not 0 like us computers...

  I mean... computers. I'm not a computer. Definitely not!

  Anyway.

* The next issue you'll face is that making it an `i` loop means you'll have to refer to `todos[i]` again. You can still get the `text` property of that object, of course, but the syntax gets a little busy. If it helps, make an intermediate variable called `todo`, and put whatever's in `todos[i]` there.

* So now that we've got our todo object and our `i`, instead of printing out an asterisk, print out the current todo's `i` plus 1, followed by the todo's `text` property, and you should see a nice numbered list. Try it out!


### Removing Todos

Removing a todo is probably the simplest of the remaining features, so let's dive in there first.

* In our menu-handling function, let's replace our under construction message with a loop displaying our numbered list of todos (or a function call that does that for us, if you abstracted it away).
* Below that, we'll add an `interface.question` call where we ask, "Which todo do you want to remove?", and give as our second argument a `remove` function.
* Now let's write that `remove` function! The most basic thing we need is a call to `interface.question` to set up our menu again. (Should we move this line to a function called `displayMenu`? Maybe!)
* But before that, let's actually remove whichever todo they wanted removed. First step: which todo should be removed? The answer is the one they typed in, but it makes the most sense to have them type it in as a number, so let's assume they've done so. Where will that number be? Like all functions passed to `interface.question`, the user's input to our question will get passed in for us as the parameter. Give it a name like `num` or `number` or `selection` or... whatever you think is appropriate.
* Now all we have to do is `splice` the item at that location in the array. What you want to research for this one is how to use `splice` to remove one item only at a certain index. And remember! They're not actually passing you an index... they're passing you a _number_, which means your 0-based counting will be off by 1.
* Then, of course, we'll need to show the user their new todo list, with the todo they picked `splice`d right out. And display the menu again, looping them back to your menu-handling function.

To wrap up: you'll know you're done with this part when you can choose `2` from the menu, see a numbered list of your todos, enter a number from it, and see an updated todo list printed, followed by the menu again. Try removing a couple, try adding a couple back, and try going back and forth, making sure that your list updates correctly as you go!

