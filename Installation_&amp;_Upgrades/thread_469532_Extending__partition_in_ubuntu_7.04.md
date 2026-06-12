---
title: "Extending / partition in ubuntu 7.04"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by sudarsanyes on 2007-06-10
Hai,

I am using Ubuntu 7.04 now and i have allotted 3 gb for the root.
Recently i ran out of space in the root. Now i am not able to log in
to my Ubuntu. When i try to log in it says that there is not disk
space on the / to login :( . Can somebody help me in extending the /
partition (is it possible) ?
P.S.: My home is 5gb. I also have a win xp in the same hdd.

---

### Post by Nanoboy on 2007-06-10
Boot with a Ubuntu live CD, then you can log in live without running the OS on your harddisk.  Then use gparted to change the size of your partition.

---

### Post by sudarsanyes on 2007-06-10
>> Then use gparted to change the size of your partition.

I am in LiveCD now. Opened gParted. Now confused what to do next. How can i change the size of my / which in 3gb ? Thats my question.

---

### Post by Nanoboy on 2007-06-10
In gparted, you can use the slide bar on each of the file system partition to adjust size and make space for others?

---

### Post by sudarsanyes on 2007-06-10
Here is a screenshot of my gParted. The last one in the list is the /. 
[IMG]http://img143.imageshack.us/img143/6688/screenshotqd7.png[/IMG]
[http://img143.imageshack.us/img143/6688/screenshotqd7.png](http://img143.imageshack.us/img143/6688/screenshotqd7.png)

---

### Post by Nanoboy on 2007-06-10
i think you just need to click on a big partition which you wish to reduce the size of in order to make space first, say e.g. u click on your 15GB one, then use the resize button on the top and make it smaller, then you would have some spare space, then click on your root linux partition use the resize button and increase it.  I think it is recommended to have 10GB for your root, at least.  I'm no expert though.

---

