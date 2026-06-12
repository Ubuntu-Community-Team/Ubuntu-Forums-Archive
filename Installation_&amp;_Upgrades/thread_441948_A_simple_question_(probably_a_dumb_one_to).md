---
title: "A simple question (probably a dumb one to)"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by zarilion on 2007-05-13
What is the difference between: sudo apt-get and sudo aptitude ?

---

### Post by bulldog on 2007-05-13
There are no dumb questions,you would be stupid if you didn't ask :) 

I'll try to explain.
Basically to do the same thing,install a application.
**BUT** with installing such apps. there are other dependencies installed which are needed for the app to function properly.

When you decide to un install such application,when you did install with apt-get,all the dependencies and such will remain on your hdd.
When you did install with aptitude,it will remember all which came with the application and remove them to, if no longer necessary,so your install will be cleaner over time.

So remember install with aptitude and un install with aptitude,and forget about apt-get.
Installing with apt-get and un install with aptitude doesn't work.
Installing with aptitude and un install with apt-get doesn't work either.
Installing with aptitude and un install with aptitude does the trick.

Have fun.

---

### Post by zarilion on 2007-05-13
Thank you:) That was a easy understandable guide:)

---

### Post by bulldog on 2007-05-13
Your welcome :)

---

