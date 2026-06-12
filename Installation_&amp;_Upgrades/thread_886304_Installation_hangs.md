---
title: "Installation hangs"
date: 2008-08-11
forum: Installation &amp; Upgrades
---

### Post by Delta62 on 2008-08-11
I've been trying to get a variant of Ubuntu onto my laptop, but all of the installation disks I have tried either freeze or crash. I have tried both the desktop and alternate CDs for both Ubuntu and Xubuntu, but none of them will complete successfully. All of the disks were burned at the slowest speed possible (1X), and all verify themselves normally using the check CD option. I have run memtest several times, no errors are ever found. I can install windows XP fine onto the computer, and have also successfully installed Fluxbuntu successfully. The computer has 512 MB of RAM, and I have also tried creating a 1 GB swap partition.

I would really like to get xubuntu installed here the most. Using the alternate CD, everything will work fine until it gets to the progress bar for select and install software, then it will freeze at 6%. It has been left alone for upwards of 1 hour, so it's not just slow.

Is there an installation log I can access somewhere? 
What can I do to fix this?

Thanks in advance.

---

### Post by cariboo on 2008-08-11
Try the mini.iso and do a net install. The ini.iso is available here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

Jim

---

### Post by Delta62 on 2008-08-11
Here are the results of the mini ISO:

The installer works fine until the same point. it completes the 'base system installation' and then proceeds to ask me which options (if any) I would like to add. I have tried installing both the xubuntu and ubuntu desktops, and each one of them stalls the progress bar at 6%. It does not say what file specifically it is installing, only "Please wait..."

---

### Post by Delta62 on 2008-08-11
It looks like I spoke too soon. After leaving he installation at 6% for a while, it picked up again and eventually finished installing correctly. The bootloader also installed, and is now working normally.

However, now there is a new problem. I have noticed the same symptoms when booting from the desktop CDs to try Ubuntu without making any changes. Before the OS completes loading, the following text comes onscreen:

*starting anac(h)ronistic cron anacron          [OK]
*starting deferred execution scheduler atd      [OK]
*Starting periodic command scheduler crond      [OK]
*Checking battery state                         [OK]
*Running local boot scripts (/etc/rc.local)     [OK]
_


The underscore there is a blinking cursor. Needless to say something is preventing Ubuntu from loading right.

I have installed the core system files and the Ubuntu desktop only.

---

