---
title: "How to clear Printer History???"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by emarkay on 2009-03-30
This is something new I see in 9.04.  Unwanted to say the least...

---

### Post by mc4100 on 2009-03-30
> **emarkay said:**
> This is something new I see in 9.04.  Unwanted to say the least...
View -> Show Completed Jobs?

---

### Post by emarkay on 2009-03-30
That shows it, but there is no "clear history" for them.

---

### Post by andrewabc on 2009-03-30
> **emarkay said:**
> That shows it, but there is no "cleat history" for them.

I'm guessing what you want is to remove history, so that when "show completed jobs" is enabled you don't want some or all print jobs to be listed. Just to clarify that for others.

So if you printed a document titled "omg ponies" and you don't want any trace of that ever happening.

I'm currently on intrepid and have no idea to get rid of my previous print jobs.

Only guess would be to delete printer, and then re-add it, maybe that would delete completed jobs as well. But that is a lot of work for something simple.

google had no easy solutions.
[http://ubuntuforums.org/showthread.php?t=1052311](http://ubuntuforums.org/showthread.php?t=1052311)

[A way to delete finished jobs needed](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/158487)

Go to
[http://localhost:631/](http://localhost:631/)
And jobs menu. They are listed there (select show all jobs). No idea how to remove them.

---

### Post by emarkay on 2009-03-30
I added comment to Launchpad bug.

[https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/158487?comments=all](https://bugs.launchpad.net/ubuntu/+source/system-config-printer/+bug/158487?comments=all)

---

### Post by kansasnoob on 2009-03-30
I agree that it would be nice to have a gui option to selectively delete printer history.

But I've tested and if you go to System > Administration > Printing > Server > Settings > Advanced you can change the option from "Preserve job history but not files" to "Do not preserve job history".

Of course that doesn't clear the previous history, but it prevents the recording of any new history.

IMHO that should be the default anyway!

Pic:

[ATTACH]108117[/ATTACH]

---

### Post by emarkay on 2009-04-03
No solution yet, but see here:
[http://ubuntuforums.org/showthread.php?p=7009485#post7009485](http://ubuntuforums.org/showthread.php?p=7009485#post7009485)

---

