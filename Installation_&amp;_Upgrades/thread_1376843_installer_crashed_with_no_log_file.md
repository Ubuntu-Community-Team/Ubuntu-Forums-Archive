---
title: "installer crashed with no log file"
date: 2010-01-09
forum: Installation &amp; Upgrades
---

### Post by hater1 on 2010-01-09
Hi, 

i have new HP notebook with preinstalled windows and i'd like to have ubuntu too. But it's rather difficult. Long story:

First I wanted dual boot, Ubuntu on separate partition, but then I discovered that I have four primary partitions for windows.
SYSTEM (I think nessesary for windows boot)
c: (where windows is installed)
RECOVERY (for restoring factory settings)
HP_TOOLS (needed for right function of HP BIOS)

ok, what now? Windows partition tool let me create dynamic partition (not extended) but ubuntu partition tool can see only four partitions. 

Then the wubi idea came. If I can't have dual boot wubi can be solution. But it failed too. Behavior is similar to 

[http://ubuntuforums.org/archive/index.php/t-1163971.html](http://ubuntuforums.org/archive/index.php/t-1163971.html)

that is installer say "extracting kernel" and few seconds later just close. Sadly I can't find log file (searching filesystem for word wubi and searching directory c:/users/hater/appdata/local/temp) to discover what's the problem.

Any suggestions?

---

### Post by hater1 on 2010-01-10
I was thinking about something like start wubi in verbose mode form command line or start with log location parameter. Can anybody help?

---

### Post by hater1 on 2010-01-12
What about this bug? 

[https://bugs.launchpad.net/wubi/+bug/503701](https://bugs.launchpad.net/wubi/+bug/503701)

Is there any connection?

---

### Post by hater1 on 2010-01-28
Ok, dynamic disks is not causing this trouble:
[LIST=1]
[*]Deleted all partitons, created new primary partitons (not dynamic) and installed windows
[*]Wubi installation was finished, no problem
[*]Then I uninstalled wubi and made disk dynamic
[*]Again wubi installation was finished, no problem.
[/LIST]So the cause of my problems is something else. And log file is there, I can view it.

---

