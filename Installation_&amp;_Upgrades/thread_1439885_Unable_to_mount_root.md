---
title: "Unable to mount root"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by golfnut324 on 2010-03-26
Ok, I messed up. New to Linux and somehow got Ubuntu 9.10 set up dual boot on my Vista laptop. I installed it somehow off the live cd. Everything working fine and then I decided to update from the update manger to Ubuntu 10.04 (dummy me)! :oops:
 
Got half way through installation and system froze for more than an hour. Had to shut down computer. Now when I select to boot to Ubuntu, computer freezes with this message:
 
[ 1.068088] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(8,1)
 
Can anything, within reason, be done? Should I use windows to uninstall Ubuntu and then try to re-install? If so, can someone tell me how I might have setup dual boot off the live cd? Should I just flog myself?
 
Thanks so much for helping.
 
Craig

---

### Post by stlsaint on 2010-03-26
You will need to point fstab to your new mount point for root. Overall i would suggest re-installing ubuntu 9.10 as a fresh install and waiting until 10.04 is fully released into production in April.

---

### Post by golfnut324 on 2010-03-27
> **stlsaint said:**
>  Overall i would suggest re-installing ubuntu 9.10 as a fresh install and waiting until 10.04 is fully released into production in April.
 
 
Sounds like good advice. Should I work on the mbr as described in the links and un-install ubuntu, then re-install or just re-install from where I am?
 
Thanks

---

### Post by golfnut324 on 2010-03-28
> **stlsaint said:**
> You will need to point fstab to your new mount point for root. Overall i would suggest re-installing ubuntu 9.10 as a fresh install and waiting until 10.04 is fully released into production in April.


Just to follow-up, I came to the realization that I used wubi to install Ubuntu on my Vista machine. It was then a simple matter to reinstall using wubi and all was good again. Thanks for the help and sorry to be such a noob. Learning every day.

---

