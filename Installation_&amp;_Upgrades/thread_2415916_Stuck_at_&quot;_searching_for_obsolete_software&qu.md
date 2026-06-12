---
title: "Stuck at &quot; searching for obsolete software&quot;"
date: 2019-04-02
forum: Installation &amp; Upgrades
---

### Post by somnus67 on 2019-04-02
Just upgraded from 16.04 to 18.04. Got the command from the internet to put into the terminal. Everything went through fine now I am stuck at "searching for obsolete hardware" the screen keeps going from light gray to dark gray. Any suggestions?  The only similar thread (2016) the guy had a " power failure"  while waiting for a response. Starting to think that's what I need.

---

### Post by #&amp;thj^% on 2019-04-02
you might have a hidden window that was asking you to confirm that you wanted to remove the obsolete packages that dist-packages found. If you're experiencing this, click on the "Distribution Upgrade"(In software-updater) Menu icon to check for hidden windows.
If you want to avoid the hidden windows, open terminal and run:
```
sudo do-release-upgrade
```
Now the process is visible in the terminal.
Yep I now see that you did up-grade through the terminal, so was there any added PPA's prior to the up-grade?

---

