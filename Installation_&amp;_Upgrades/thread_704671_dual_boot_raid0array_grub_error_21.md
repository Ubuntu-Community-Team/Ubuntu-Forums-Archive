---
title: "dual boot raid0array grub error 21"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by jskiff on 2008-02-22
Hello all. I am new to this and need some help, possibly on multiple issues. I have 2 80Gb. serial ATA drives in a raid0 array with a promise raid controller for my XP, and want to dual boot using a new 250Gb.SATA for a dedicated Ubuntu 7.10 AMD64 partition. The drives work fine if formatted in XP but I get a grub error 21 at reboot after installing 7.10 via "guided" installation. I cannot boot to either XP or 7.10 although both drives appear in my hardware. I have tried reinstalling windows and 7.10 and have tried booting from the other drive but nothing seems to have helped thus far. I have been loading from a verified disk and have tried every bios setting I can think of. Is there a trick to this?

---

### Post by dstew on 2008-02-22
So, do you have 3 SATA drives in there, or two? Can you boot an Ubuntu live CD? If so, post the output of the command ```
sudo fdisk -l
```You enter this command in the terminal, in Applications menu.

---

### Post by jskiff on 2008-02-22
Yes, there are a total of 3 SATA drives in there and I am booting from my live CD. I will paste the output as you suggested. This was my last effort where I was trying to boot from the Ubuntu disk. If it would help, I could reinstall and to boot from the RAID 0 and send the output of that instead.Thank you.
   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       30215   242701956   83  Linux
/dev/sdc2           30216       30401     1494045    5  Extended
/dev/sdc5           30216       30401     1494013+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

