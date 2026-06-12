---
title: "Computer freezes after log in"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by John_MacDonald on 2014-04-19
I have an 3 your old AMD computer with 4 MB's of ram and a 500 MB hard drive.
I am trying to leave Win XP on part of the drive and install Ubuntu on another part. I had a copy of 13.1 so I used that. The first time I I partitioned the hard using 200 mb's for Ubuntu.
That didn't work at all. As soon as I booted it froze up. So I re-installed 13.1 again, the box where I would completely remove the old 13.1. and thing time I selected to download updated files during the installation and it did this and upgraded me to 14.01. That allow me to get to the log in screen but once I logged in every thing froze.
So I downloaded the 32 bit version of 14.01 and and tried again. This time I got logged in but the mouse almost froze. I can move it a few inches every 15 minutes. The desktop looks normal.
I don't really want to put Ubuntu on the complete hard drive as there is still some files on Win XP that I want to have access to.
I am running Ubuntu 13'1 on an IBM Think Pad and it works fine.
Any ideas on how to get it working on this AMD processor.
I did see a download called Mac and 64 bit but the link was dead.

John

---

### Post by Iowan on 2014-04-19
> **John_MacDonald said:**
> I have an 3 your old AMD computer with 4 MB's of ram and a 500 MB hard drive.
I presume you mean GB instead of MB ...

---

### Post by grahammechanical on 2014-04-19
A Ubuntu install typically needs from 5 - 6 GB. So, if you are having problems it might not make much difference if Ubuntu is installed into 10GB or 500 GB. And I would not say that 3 years is "old" for a computer. My machine dates back to 2007 and has only 1GB or RAM and Ubuntu 14.04 installs and runs fine. My graphic card has 1GB of its own memory and that I think makes a difference. I do not think that the problem is to do with the size of the Ubuntu partition. It might have something to do with the graphics in that machine. What graphic card do you have and is it hybrid graphics?

I personally would never install Ubuntu and tick the Install Third Party Software option. That will install a proprietary video driver and that can work but sometimes it does not. At the Grub menu select Advance Options for Ubuntu and then select Recovery Mode. At the Recovery menu select Resume. That may get you to a desktop without using a proprietary video driver. From there you can go to System Settings>Software and Updates>Additional Drivers tab and experiment with video drivers.

When we try Ubuntu using a live session we use an open source video driver. If that works fine but we then have problems like this when we reboot after installing, then I would look to the proprietary video driver as the cause of the problem.

Regards.

---

### Post by John_MacDonald on 2014-04-19
This computer has 200 gb allotted to Ubuntu. It has 4 mb's a ram and an AMD Athlon II X2 processor.
It has windows XP on the other partition. XP was always on this computer. I also loaded the 32 bit version.
I did't check that Install third party software.
What I don't understand is that I have installed Ubunty at least a dozen times on various computers and have never had anything like this happen.
I think this evening I will try Mandriva a try or maybe drop back to Ubuntu 12


I'm won

---

