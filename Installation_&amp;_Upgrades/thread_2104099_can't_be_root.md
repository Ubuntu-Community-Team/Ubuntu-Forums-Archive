---
title: "can't be root"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by wuqs233 on 2013-01-12
At the beginning I just want to install the sqlite3 program,  but I got a  problem that seems like share lib of sqlite3 is a wrong version. 
Then I found some guy had solved this problem, just like this:
[http://www.kubuntuforums.net/showthread.php?60125-Can-t-install-anything-bad-libsqlite3-0-amd64](http://www.kubuntuforums.net/showthread.php?60125-Can-t-install-anything-bad-libsqlite3-0-amd64)
So I follow his step to solve my problem:
```
sudo dpkg --force-depends --purge libsqlite3-0:amd64
```And  then, I can't use sudo again! when I attempt to do anything what needs a  root permission, a "Segmentation fault" is waiting for me.
So, you  know, can't install anything or copy anything to root folder,  can't  open Ubuntu Software Center (It return as a "System Program Problem"),  or EVEN Can't power off the machine! WTF!
I'v gotten a deb package and a rpm package of libsqlite3, but how can I install it into the system?
Please help me!

ps.  I'm Chinese, but my iBus is not access now.(It needs to be root to  change the input method huuuu?)  My English is poor. Somebody can  understand me? Should I reinstall Ubuntu at the last?

---

### Post by dino99 on 2013-01-12
you still can unplug the power cord to shutdown that system  ):P

and dont be so worry, your english is not worst than mine  :p

why have you not installed sqlite3 from the ubuntu repo ?

```
sudo apt-get install sqlite3
```

you might be able to boot in recovery mode (hit "shift" key down at bios end process to get the grub menu on a single OS system), and select to repair the system

---

### Post by wuqs233 on 2013-01-12
> **dino99 said:**
> you still can unplug the power cord to shutdown that system  ):P

and dont be so worry, your english is not worst than mine  :p

why have you not installed sqlite3 from the ubuntu repo ?

```
sudo apt-get install sqlite3
```you might be able to boot in recovery mode (hit "shift" key down at bios end process to get the grub menu on a single OS system), and select to repair the system
Thanks a lot for your answer dino99~
As a fact I tried ```
sudo apt-get install sqlite3
``` when I want install sqlite3, but something went wrong seems like caused by the share lib -- libsqlite3-0 of a wrong version, so I try to repair it and then got the bigger problem -__-||| 
My computer is a dual OS system, Ubuntu 12.04 + Windows7. How can I enter recovery mode -- without a Ubuntu OS Image CD ?
By the way, I type this message with a dictionary on-line , so English of mine......

---

