---
title: "Installation 10.04 - strange happenings"
date: 2010-06-04
forum: Installation &amp; Upgrades
---

### Post by ibates on 2010-06-04
I use an ASUS P5VD2-X with Intel Core Duo.  I have two IDE HDD running under Windows XP (Win XP OS is on one of these HDD).  Two SATA HDD - one for Ubuntu OS the other for Ubuntu backups.  Further, I run two large SATA HDD under a JMicron RAID setup.  These latter HDD were formatted under Win XP, but have hitherto been available for file storage and retrieval under Ubuntu 9.10 as well.

Problem:  I could not get Ubuntu 10.04 to install by any method until I selected "nodmraid" at the initial page of the installation.  (Unless this was selected, the installation invariably failed with a message about "ubi-partman crashed").  Ubuntu 10.04 then installed OK and seems to running reasonably well - the odd random hang for whatever reason (it is a virgin installation so should have no bugs).  But I cannot access the JMicron RAID seet as I could under Ubuntu 9.10.

It should be stated here lest hardware is suspected, the Windows XP system operates faultlessly (thank goodness - as a reliable backup is still required, even after making every effort to change to Ubuntu for well over a year now).

But, pressing on; following selection of Ubuntu at the GRUB screen, I see pages of "no-IRQ" messages followed by a couple of lines of dialogue concerning not being able to find some files for the JMicron RAID set.  Eventually the log-in screen appears, and off we go OK.

I am totally confused.  Can anyone shine some light on this problem.

Log files are available if that would be of assistance in diagnosing the problem.

---

### Post by ibates on 2010-06-17
Further to the above, I have eliminated the problem by rearranging my HDD with the aid of trayless enclosures so I can plug in whichever HDD I require.  Thus the need for the JMicron RAID array no longer exists.  It is therefore not used.  No problems with the installation now.  Everything is installed and up and running.

But why do I have to look at a most unprofessional looking couple of pages of lines and lines of "No IRQ" messages which come up after the GRUB loader has selected the Ubuntu OS and it is booting up.

Everything appears to be operating normally despite this annoying information - except of course, the random hanging which occurs from time to time (and did with Ubuntu 9.x as well).  This cursed hang is always preceded by a "flash" on the monitor.  The input power supply is from a UPS and is "spike" filtered.

Any thoughts on either of these issues would also be appreciated.

---

### Post by ronparent on 2010-06-17
The question is can you boot the live cd without using the nodmraid parameter (probably not, but give it a try)?

---

### Post by ibates on 2010-06-20
Yes I could.

But as I said, I have circumvented the problem and as such the aim of the game has been achieved.

Many thanks for your thoughts.

---

