---
title: "Cinelerra installation problems"
date: 2007-08-29
forum: Installation &amp; Upgrades
---

### Post by dbsoundman on 2007-08-29
I'm resurrecting this thread because I'm looking for a current source of an rpm for cinelerra that still works. All the ones I found specified here don't appear to exist anymore. I tried installing cinelerra from synaptic, but it never works; it shows up in the application menu, and if I click on it, all I see is a window flash up and disappear. Help?

-Dan

---

### Post by yabbadabbadont on 2007-08-29
> **dbsoundman said:**
> I'm resurrecting this thread because I'm looking for a current source of an rpm for cinelerra that still works. All the ones I found specified here don't appear to exist anymore. I tried installing cinelerra from synaptic, but it never works; it shows up in the application menu, and if I click on it, all I see is a window flash up and disappear. Help?

-Dan

Try opening a terminal window and then running cinelerra from there.  Hopefully it will spit out an error message that will help you find the problem.

---

### Post by dbsoundman on 2007-08-29
Here's what happens when I launch cinelerra:
```
dan@blackdiamond:~$ cinelerra
Cinelerra 2.1CV (C) 2006 Heroine Virtual Ltd.
Compiled on Tue Apr 24 13:45:37 UTC 2007

Cinelerra is free software, covered by the GNU General Public License,
and you are welcome to change it and/or distribute copies of it under
certain conditions. There is absolutely no warranty for Cinelerra.
Illegal instruction (core dumped)

```

Any ideas?

-Dan

---

### Post by yabbadabbadont on 2007-08-29
Nope.  Search the bug tracker to see if this issue has already been reported and, if not, submit a new bug.

By the way, I asked a mod to split these posts off into their own thread as this is support related and not backport related.  :)

Edit: I didn't look at all the cinelerra bugs on launchpad, but the two likely looking ones don't appear to be this issue.

---

### Post by dbsoundman on 2007-08-29
Oops...I didn't even look at the previous 5 pages or so...I just found the one about installing from an rpm and went from there...

-Dan

---

### Post by Amazona aestiva on 2007-08-31
See the second link in my signature!

---

### Post by dbsoundman on 2007-08-31
I followed the instructions in your post verbatim, and I still get the same error message unfortunately. Thanks for the tip though!

-Dan

---

### Post by kelvin spratt on 2007-08-31
[http://ubuntuforums.org/showthread.php?t=464223](http://ubuntuforums.org/showthread.php?t=464223)
[http://ubuntuforums.org/showthread.php?t=463275](http://ubuntuforums.org/showthread.php?t=463275)
This is how i installed Cinelerra its not the latest version its the Dapper version and it does support a lot more Avi Formats than the latest version and is stable, looking at the feedback their are lots of problems installing cinelerra, what works for one system may not work for another, and many people give up.

---

### Post by cotcot on 2007-09-03
I got cinelerra installed by transforming a cinelerra rpm-package to .deb. The other ways as described in this thread failed.

---

