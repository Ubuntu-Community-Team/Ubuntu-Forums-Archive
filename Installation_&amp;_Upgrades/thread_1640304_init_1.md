---
title: "init 1"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by consultpa on 2010-12-07
Trying to upgrade BIOS. running 10.04 an using gnome.  open a terminal windowthen -   Says to got to init 1.  I've tried init 1    telinit 1.   Just get Ubuntu image and never returns.   I've seem someone else asked this but I never found the answer.    I assume it is something obvious but I'm clearly not finding it.  Help is appreciated!  thanks

---

### Post by sisco311 on 2010-12-07
Welcome to the forums!

If you can't switch to runlevel 1 (a.k.a single user mode or recovery mode), then try to boot directly in it.

During the boot-up hold down *Shift*. When the Grub menu shows up select *recovery mode* and wait for all the boot-up processes to finish, then select *Drop to root shell*. When you are done, run **exit** and select *resume normal boot*.

---

### Post by SQuIDers on 2011-08-13
Hi. I see a couple of threads with init 1 problem, and everyone suggesting booting into recovery mode from GRUB as a solution.

Even though booting into recovery mode from GRUB works, this does not help me. I like not to restart my computer unless when upgrading the kernel. Has anyone found a way of making init 1 to work without freezing the computer? I have verified this problem with several machines running ubuntu 11.04 64bit on various architectures (laptops, PCs, Intels, AMDs).

Would anyone be interested in troubleshooting this issue with me, and maybe helping me report this as a an issue in the Ubuntu bug tracker? 

Thank you.

---

