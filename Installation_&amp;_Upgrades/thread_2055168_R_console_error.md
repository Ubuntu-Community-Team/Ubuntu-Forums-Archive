---
title: "R console error"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by 2uRcJQ34G1 on 2012-09-08
Hello,

I recently installed R for my university class. Unfortunately whien I type "R" in the console it starts and exits with the following message:

```
Error: segfault from C stack overflow
There were 47 warnings (use warnings() to see them)
Segmentation fault

```

any help is appreciated.

Cheers :D

---

### Post by 2uRcJQ34G1 on 2012-09-09
Strangely, when I tried to run the program again today, it only showed 24 errors!?

I even tried to run it in valgrind and it just exited after the warning, hunh?

gdb did not recognise /usr/bin as a valid executable.

I have already tried to remove and reinstall all the package to no avail, seriously nobody has this problem??

---

### Post by 2uRcJQ34G1 on 2012-09-09
Interesting fact: every time I run the program, it segfaults with a different number of warning number?

Most bizarre...

---

### Post by Lars Noodén on 2012-09-09
Which front-end are you using for R?  rkward is highly recommended.

---

### Post by rewyllys on 2012-09-09
> **Lars Noodén said:**
> Which front-end are you using for R?  rkward is highly recommended.
Also widely recommended is *RStudio*.

---

### Post by 2uRcJQ34G1 on 2012-09-10
Thanks for the replies, but I am not using any front end(at this point), I like the console :).

I have solved(?) my problems though(somewhat), I had installed R directly from the software packages. Instead this time, I added a mirror directly from their dedicated servers to the Software Sources list; then I simply reinstalled. Done!!

This kind of works in the sense that R at least starts, however, it gives me the following messages:

```

During startup - Warning messages:
1: Setting LC_CTYPE failed, using "C" 
2: Setting LC_COLLATE failed, using "C" 
3: Setting LC_TIME failed, using "C" 
4: Setting LC_MESSAGES failed, using "C" 
5: Setting LC_PAPER failed, using "C" 
6: Setting LC_PAPER failed, using "C" 
7: Setting LC_MEASUREMENT failed, using "C" 

```

Everything I need works now, so I may or may not update this thread. For now, I am marking this as solved.

Cheers,

G

---

