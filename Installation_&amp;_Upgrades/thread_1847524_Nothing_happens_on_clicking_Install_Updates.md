---
title: "Nothing happens on clicking Install Updates"
date: 2011-09-20
forum: Installation &amp; Upgrades
---

### Post by anjanesh on 2011-09-20
System > Administration > Update Manager
On clicking Install Updates, nothing happens. The screen just blinks for a second.
I am using Ubuntu 11.04

---

### Post by mörgæs on 2011-09-21
If you boot the computer, close all windows that might open and run

```
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade
```

what happens?

---

### Post by anjanesh on 2011-09-21
Command line worked ! Thanks !
I still can't get the update manager GUI to work though.

---

### Post by mörgæs on 2011-09-21
Good. If you feel that the problem is solved, please mark the thread so using 'thread tools'.

---

### Post by ktbos on 2011-10-04
Unlike the OP, I wouldn't have considered this "SOLVED" until he was able to get Update Manager working - command line is only a work around.  I had the same problem and here is what I did to fix it:  In the Startup Applications, I had inadvertently turned of policykit.  I turned that back on and rebooted and everything worked with Update manager as it should have.  

A little more detail:  As with the OP, everything about Update Manager seemed to be working except for the ability to actually install the updates.  Clicking that button would just make the window blink and then be right back where it started.  

I looked through a lot of discussions about Update Manager.  My problem did not seem to be related to the problems that people have that are fixed with clearing out the apt/lists directory - that problem gives a clear error.  My problem was also different than this reported bug:  [https://bugs.launchpad.net/update-manager/+bug/414181](https://bugs.launchpad.net/update-manager/+bug/414181)  because in that bug, you can workaround the issue by clicking Check first and that didn't solve the issue for me.  

So since this problem was different than anything out there posted about Update Manager problems, I wanted to report back with my fix.  Hope it helps somebody else.

---

