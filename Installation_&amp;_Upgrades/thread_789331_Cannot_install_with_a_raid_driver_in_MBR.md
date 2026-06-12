---
title: "Cannot install with a raid driver in MBR"
date: 2008-05-10
forum: Installation &amp; Upgrades
---

### Post by mattinger on 2008-05-10
For some reason, it seems that i cannot install ubuntu properly into a system which has a prioprietary raid driver installed into the MBP by the windows installer.

Hardware Info:
ABIT P965 Pro motherboard, Core 2 duo 1.86 Ghz CPU

Steps followed:
1.  Install Windows XP Pro, including the prioprietary JMicron RAID driver (via floppy disk in the windows installer) onto partition 1, which occupies 1/2 of the drive.

2.  Install Ubuntu onto partitions 2(swap)/3(ext3) which occupy the rest of the drive

At this point, I can boot Ubuntu, but can not boot windows anymore.  I get an error about some part of the ntkernel not being found in the "Windows boot drive>system32" directory.  I don't have the exact error, as I've had to redo my installation since.

Once I redid my installation, I have also tried to do an installation inside windows, so as not to affect the MBR.  However, when I try to boot to ubuntu, it is not able to succesfully boot (again, i don't have the exact error message, but i could reinstall and try again to get the error message).

It seems that either grub or ubuntu itself is not dealing well with raid drivers installed into the MBR.

---

### Post by Pumalite on 2008-05-10
Does this apply to you?:
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
[http://ohioloco.ubuntuforums.org/showthread.php?t=630644](http://ohioloco.ubuntuforums.org/showthread.php?t=630644)

---

### Post by mattinger on 2008-05-11
My real concern is that I'm not actually booting to a RAID drive.  I'm trying to use the RAID as a data drive, and keep the two operating systems on the main drive.

However, in order to even install windows xp, i needed to install that driver from the floppy disk in the MBR via the xp installer.

And as I said earlier, grub overwrote that, and xp fails to boot.  It's not that linux is not seeing the drive, it's that windows can't boot anymore.

As an alternative, i tried the "Install Inside Windows" option, and ubuntu won't event boot in that case.

Not that i can't execute the instructions given in the posts, but half the point of ubuntu is to make linux easy to deal with for the masses.  Try getting a linux newbie to understand, much less execute, these instructions.

Isn't there any way that ubuntu can install itself on a physical partition, without altering the MBR, and configure the windows boot loader to start it up?

---

### Post by Pumalite on 2008-05-11
You can install Grub to its own partition and later boot it with Super Grub: [http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)

---

