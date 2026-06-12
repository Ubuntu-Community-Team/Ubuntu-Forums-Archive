---
title: "How can one use multi threading in PHP applications"
date: 2017-01-26
forum: Installation &amp; Upgrades
---

### Post by makeshaun on 2017-01-26
Is there a realistic way of implementing a multi-threaded model in  PHP whether truly, or just simulating it. Some time back it was  suggested that you could force the operating system to load another  instance of the [PHP]("http://www.phptherightway.com/") executable and handle other simultaneous processes.


  The problem with this is that when the PHP code finished executing  the PHP instance remains in memory because there is no way to kill it  from within PHP.  So if you are simulating several threads you can  imagine whats going to happen.  So I am still looking for a way  multi-threading can be done or simulated effectively from within PHP.  Any ideas?

---

### Post by igdfpm on 2017-01-26
[https://tudorbarbu.ninja/multithreading-in-php/](https://tudorbarbu.ninja/multithreading-in-php/)

---

### Post by tech-j on 2017-01-26
makeshaun

If you don't want to use the Thread process that igdfpm provided you above, another alternative is:
You can simply add "-j 4" (Without the quotes) to the end of your PHP script line to have it use (4) processors to run.
Simply change the Number to however many cores you want to dedicate to the script you are running, but be careful NOT to allocate more cores than you have.
Enjoy.
-Tech-J

---

