---
title: "Installation hangs at 70% in partioning...."
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by spect8 on 2010-03-12
Hi.

I'm having problems installing Jaunty.
I've installed it in Win7, and after I boot up in Ubuntu, and start the "Install ubuntu 9.10", it stops at 70% in the "finding filesystem". I can't seem to get through that point, and I know I'm not the only one having that problem but haven't been able to find a solution anywhere.

I hope you can help, as I see this as a bug in Ubuntu.

Thx in advance.

/Mike

---

### Post by spect8 on 2010-03-13
Can't anyone help? :(

---

### Post by RJARRRPCGP on 2010-03-13
You probably have a bad HDD.

---

### Post by Mark Phelps on 2010-03-14
First of all, Jaunty is not 9.10; Jaunty is 9.04.  So, if your installer is saying 9.10, you're trying to install Karmic.

Second, if you're trying to install 9.10 INSIDE MS Windows, using Wubi, on a machine that came preinstalled with Win7, you're taking a very difficult route.  Have seen LOTS of posts from folks unable to do this, and none so far from anyone who's succeeded.

Third, if you really want to install Ubuntu to a preinstalled Win7 machine, do two things first:
1) Launch Win7 and use the backup utility to create and burn a Win7 Repair CD,  You will most probably need this later.
2) While in Win7, use the Disk Management utility to shrink the OS volume to make room for Ubuntu.  Do not format the new unallocated space.

After that, you can boot into the Ubuntu CD and use the largest free space option to install ubuntu to the unallocated space.

Do NOT use the Ubuntu installer to shrink the Win7 OS to make room for Ubuntu. Doing so runs the risk of corrupting your Win7 installation and rendering it unbootable.

---

### Post by Cwashpimp on 2010-03-14
installed ubuntu from wubi on windows 7 asus laptop no problem...... i believe the errors have been fixed recently

---

### Post by spect8 on 2010-03-15
Thx for the replies.

I meant Karmic, not Jaunty.
My computer is not preinstalled, and yes, I'm trying to install it with Wubi, and have a HD only for that.

The problem is, I can't even choose anything when I boot up in ubuntu and starts the installer, it just stops at 70% when its running "Finding filesystems".

---

