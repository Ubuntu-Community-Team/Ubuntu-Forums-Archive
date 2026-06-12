---
title: "Installing Ubuntu Server 10.04 with software RAID"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by Ellutu on 2010-09-17
I recently assembled a small pc with two 2TB harddisks to set up as a home server, and I figured I'd install Ubuntu Server 10.04 on it. As simple as that sounds I'm pretty close to restructuring the machine with a kitchen knife ;-).

Oh well, the situation: The data on the server will mainly consist of backups so I'd like the disks configured in RAID 1, a hardware RAID controller was way over budget/overkill since software raid seemed perfectly sufficient for this purpose. So I downloaded the 64-bit server installer for 10.04, put it on an usb-stick (no optical drive in the machine) using the usb-creator tool. Everything goes perfectly well up to the partition editor. I try to create the partitions I want for the RAID configuration, but I **cannot switch the boot-flag to on** when I select "physical volume for raid". When trying to switch it briefly shows a progress bar and it's still set to off. I got this problem in both the 8.10 and 10.04 installers (I figured I'd try configuring in a different version, but no luck). 

Right now I just configured the boot partition (and several others) to be on one disk and the data partition the only one configured as RAID-1, which took ages to apply (I actually thought that had crashed too when I started this topic..) but this is far from ideal since I won't be able to boot from disk if one of them fails and it might be a pain to recover the data. I noticed a post with a similar problem here: [http://ubuntuforums.org/showthread.php?t=1407682](http://ubuntuforums.org/showthread.php?t=1407682) with not a single reply, so no help there..

So the question basically is: how do I make a "physical volume for raid" bootable in the installer? Hopefully someone here knows how to solve this.

---

### Post by Ellutu on 2010-09-24
*kick*

Really, no one any thoughts :(?

---

### Post by putz3000 on 2011-04-17
I am now having this exact problem with exact sized HD's as yours. My thread has turned into a debate about needing or not needing boot flag.  all I know is Grub will not install period.  The more looking I do, the more I see this as an issue and yet I do not see it officially addressed.  I am following - or attempting to follow - the official Ubuntu Server guide and it is physically impossible to follow those steps and have a two hard drive RAID1 system.  Very frustrating for someone who is not well versed in Linux to get through this experience.

---

