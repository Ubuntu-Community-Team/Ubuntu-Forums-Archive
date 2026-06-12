---
title: "Dual partitioning ubuntu11.04 and win7 set-up -- can someone check this?"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by skoomafiend on 2011-08-20
Hi! 

I'm looking to dual-boot Windows 7 (already on my laptop) and Ubuntu 11.04. I'm completely new to all of this, but I've been looking things up for the last couple days...

I've added a picture of my current HD as a screen cap below. As you can see, there are already three primary partitions on it -- two for recovery, and one with Win7. I have about 52GB of "unallocated space" marked as a logical partition, and I want to convert this into smaller logical partitions for ubuntu, as well as a logical partition for storage accessible to both Win7 and ubuntu. 

Here is my "hypothetical set-up", where the liliac is what is already on my HD and the orange is what I plan to make out of the "unallocated space" (the logical partition): 

[IMG]http://i.imgur.com/U7w5O.jpg[/IMG]

Is this feasible? 

I'm planning to use EASEUS or Partition Wizard to make those two new logical partitions, and then use Wubi to install Ubuntu onto the new 15GB drive. Will this work? 

Thank you for reading! I'm an absolute beginner and scared of arbitrarily partitioning off my HD, so any advice is appreciated!

---

### Post by oldfred on 2011-08-20
I think you have mixed up full partition install and wubi. Wubi is for windows users who are not sure they want Ubuntu but want a longer trial than what a liveCD gives. It also lets you save data, but is not intended for long term use. It is easy to uninstall as it is inside the NTFS windows partition and uses the windows boot loader.

Full partition install requires separate partitions for root and usually swap. Alternatively you can create a separte /home partition, but if you have a shared NTFS partition most of your data should go there and then a separate /home is not really required (you still should back up all of /home especially before a version upgrade or reinstall).

Make sure you have made good backups. A user recently selected the wrong install choice and totally overwrote his windows install. If you partition in advance and choose partitions you should not have that problem.

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

I suggest using windows to shrink the windows c: drive or sda2 partition and then use gparted to create Linux partitions. Your shared should be logical and NTFS.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by skoomafiend on 2011-08-20
Thank you for your thorough response (: ! I'll report back once I've tried it out, or if I run into any other problems...

---

### Post by YesWeCan on 2011-08-20
I agree with oldfred. Your 53GB unallocated is fine for creating a 4th primary partition of type "extended", which you can then subdivide into as many logical partitions as you like for Ubuntu.

An easy method is to boot a Ubuntu live CD/USB and run GParted to make the new partitions. Here's guide: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) :)

Do not mess with your existing partitions unless you do it from Windows.

Always back up vital files before you mess with partitioning and dual installing. :!:

---

### Post by skoomafiend on 2011-08-20
Thanks guys! Everything worked out fine and now have a dual boot between Windows 7 and Ubuntu 11.04 set up successfully :)

---

### Post by oldfred on 2011-08-20
Glad it worked.:)

---

