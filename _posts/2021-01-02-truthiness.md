---
layout: post
title: Ruby Foundations - Truthiness
excerpt_separator:  <!--more-->
---

Although this article is about truthiness in Ruby, truthiness is relevant to all languages (at least all languages that I've come across), so it's an important concept to understand. This article will walk you through what truthiness means and what Ruby considers to be truthy and falsy. 

Truthiness means that any value or object can be evaluated to either "true" or "false".  This doesn't mean that the values are equal to the actual Boolean literals of `true` or `false`. It just mean that if the program needs to reduce the object down to a Boolean, it can do so. 

Programmers will typically need to utilize this type of reduction when working with conditionals such as `if` statements, `case` statements, or in loops like `while`. They may also come up in predicate functions, which are functions that evaluate to either `true` or `false`. A few examples of predicate functions in Ruby are `Array#include?` or `String#start_with?`. 

As you're working with different languages, make sure you learn how that language treats truthiness. Every language has its own convention, and you cannot assume that the convention in one language will be the same in another. For example, Ruby treats every value as truthy except  `false` and `nil`. JavaScript is similar, but it also treats `0`, `null`, `undefined`, `NaN`, and empty strings as falsy.

Imagine if you had the following code running in Ruby and converted it to JavaScript. 

```ruby
# Ruby

bank_account_value = 0

if bank_account_value
	puts "Account exists with $#{bank_account_value}."
else
	puts "Account does not exist."
end

# => Account exists with $0.
```

```jsx
// JavaScript

let bank_account_value = 0

if (bank_account_value) {
	console.log("Account exists with $#{bank_account_value}.")
} else {
	console.log("Account does not exist.")
}

// => Account does not exist. 
```

You would get different results! Thus, you must understand how the programming language you are using treats truthiness. 

As you're working with truthiness, it's important to highlight that although a programming language can evaluate an object to "true" or "false", the object is not actually equal to `true` or `false`. Only the  Boolean literals of `true` and `false` are equal to `true` and `false`, respectively. 

Let's walk through some examples in Ruby. 

Example 1:

```ruby
greeting = 'hello'

if greeting
	puts greeting
else 
	puts 'false'
end

# => hello

# hello is outputted to the screen because it is considered
# to be a truthy value. The if branch executes because
# greeting evalutes to true. 

greeting == true

# => false
# false is returned because although greeting is a truthy 
# value, it is not actually equal to true. 
```

Example 2:

```ruby
age = 97

if age
	puts "You're #{age} years old."
else
	puts "false"
end

# => You're 97 years old.

# Similar to the first example, the number 97 is treated 
# as a truthy value. The if branch excutes because age
# evaluates to true. 

age == true

# => false

# But again, the number itself is not equal to true. 

```

Example 3:

```ruby
value = nil

if value
	puts "true"
else
	puts "false"
end

# => false

# In this example, we're testing out if nil will evaluate to
# false, and it does. The program skips the if branch and
# moves to the else branch and outputs 'false'.

value == false

# => false

# Like the examples above, nil does not equal to false. nil 
# is a falsy value, but only false is equal to false. 
```

In essence, truthiness is an important concept for all programmers to know, because it pertains to all languages and affects how your program evaluates objects. For Ruby, just remember that everything is considered truthy except for `false` and `nil`.