---
title: "Side-By-Side or Different Partition?"
date: 2014-01-31
forum: Installation &amp; Upgrades
---

### Post by Gremlin! on 2014-01-31
I'm a returning Ubuntu user with much more experience on Evil Empire MS shells than Unix-based ones, so forgive my ignorance (the only reason I use an Evil Empire Operating System is that very few of the games I like run on Linux platforms). EEOSs generally are not "friendly" with regard to "alien" operating systems residing on the same disk. It's been so long since I had Ubuntu and Windows on the same machine (the last time was Ubuntu 9.10), and there has been significant improvement with each release, so I need to now what the wisest method of installation should be, install with WUBI with Windows 7 Ultimate x64 up and running, or install Ubuntu on a dedicated partition of the same hard drive? Logic should dictate that the latter is a viable option and that on subsequent reboots, the boot manager should ask me which operating system to load, but where Windows is concerned, I've learned much to my chagrin that it's not always a matter of logic with them. I *would *install Ubuntu on a hard drive of its own, but my "spare" drive is down, in need of a new SMART card. The specific reason I want Linux on a separate partition is that I am concerned that if something happened to the Windows system that Ubuntu files might be compromised, that BOTH OSs would be damaged. I like Ubuntu for two *very* good reasons: It is far less susceptible to malicious code, and file fragmentation is virtually unheard of.

What can I expect with vis-à-vis HDD0 with Windows 7 on one of its partitions and Ubuntu on the other, smaller, one?

---

### Post by Bucky Ball on 2014-01-31
Welcome. Wubi is no longer supported really, even though it is available. Being phased out so don't go there.

A side by side install IS a dual-boot. Wubi is installed INSIDE Windows. 

Please use paragraphs. Many people will move right along when confronted with a big blob of black text. It will improve your chances of getting help.

PS: You can expect to have Windows on one partition and Ubuntu on another. They have nothing whatever to do with each other. When one is booted, the other is not part of the equation. They are COMPLETELY independent installs and do not rely on each other in any way (apart from both use the Ubuntu boot menu in most instances but this is set up automatically during the Ubuntu install).

---

### Post by oldfred on 2014-01-31
Many pre-installed Windows 7 systems use all 4 primary partitions. So you may have to back one up and convert it to an extended partition. Then you can have an unlimited number of logical partitions. If dual booting I also suggest a shared NTFS data partition. Often a lot of data may be wanted in both systems. And usually best not to directly write into the Windows system partition, just read from it.

Post this to see existing partitions.

sudo parted -l

Best to backup Windows and make a Windows repairCD or flash drive.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

   Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by Mark Phelps on 2014-01-31
You need to see the disk partitions when you boot into Win7 and use the Disk Management utility. Count the partitions you see. IF there are already four of them, and you are using MBR partitioning (not GPT) that is the maximum allowed. IF you FORCE the creation of another, not only will that automatically convert the Basic Volumes into Dynamic Disks (something you do NOT want to do), it will then PREVENT the installation of Linux.

If you decide to continue on with dual-boot, then use ONLY the Win7 Disk Management utility to shrink the Win7 OS partition to make room on the drive. Win7 is very finicky about its OS partition being messed with from "outside" with other tools -- like GParted. While it may be OK, it's more likely to result in filesystem corruption, which will then render Win7 unbootable.

And, after you create some free space, do NOT format it using the Win7 Disk Management utility; leave it as free space.

Then BEFORE you install Ubuntu, use the Win7 Backup feature to create and burn a Win7 Repair CD.  You might need this later if the dual-boot install corrupts the Win7 boot loader.

When you then install Ubuntu, use the "Something Else" option to allow Manual Partitioning.

---

### Post by Gremlin! on 2014-02-01
Thank you, BuckyBall (and I know what a BuckyBall is!). Yeah, gotta watch that tendency to HUGE block paragraphs.

---

### Post by Gremlin! on 2014-02-01
Presently, there is only a single partition, that which Windows resides on. lthoug I have not INSTALLED such configurations, I've used computers that had as many as SIX operating systems in residence, any of which you could select using the boot process. AND I've had dual boot-side-by-side configs I've done myself...it's just been a while, and some things I forget. Thanks. I'm going with the side-by-side dual partition configuration, REALLY not liking the WUBI thing for obvious reasons. I just couldn't remember how the Windows MBR reacts under these circumstances. I seem to remember, however, when I was dual-booting Ubuntu 9.10 with Windows Vista, that the Windows boot manager was overridden by GRUB, and that IT would ask me to select the OS/partition to boot from. I just wanted to ensure nothing significant had changed in that regard between then and now before I implemented any changes.

---

### Post by Gremlin! on 2014-02-01
I don't understand the "pre-installed" stuff. Pre-installed MFR Windows is crap; I don't DO that. MFR particularly bad in that regard is HP with their laptops. SUPPOSEDLY the dedicated partition in such a config ensures security and restoration, when in fact it does NOT. HP has a nasty habit (that may have changed now) of putting crap that should be motherboard-resident-only partly on the motherboard and partly on the hard drive, which quickly turns into a bricking situation when things go bad (as they did). Since then, I build my OWN desktops from scratch, and I HAVE to say that the Linux community is REALLY great in supporting do-it-yourselfers. NONE of my Ubuntu installations, for instance, have EVER been the target of a virus, not EVER.

---

### Post by Bucky Ball on 2014-02-02
When you get to the partitioning section of the install set up your partitions and not long after that process you will be shown the Win install and asked 'If all other OSs are shown it is safe to install grub to sda.' Or something like that. Agree. Reboot and you should see the grub menu with Win and Ubuntu. If you don't:

Get Boot Repair:
[http://sourceforge.net/projects/boot-repair/?source=directory](http://sourceforge.net/projects/boot-repair/?source=directory)

Use Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Yannbuntu's thread:
[http://ubuntuforums.org/showthread.php?t=1769482](http://ubuntuforums.org/showthread.php?t=1769482)

A pre-installed Win8 uses five partitions before you even get started! You have no other option but to boot EFI (which doesn't have a four partition limit but 128). If you install it yourself it still gobbles three, which, even on a legacy install which is limited to four partitions, leaves one partition for Ubuntu. This won't work cos where does /swap go? In that case, the fourth partition needs to be a big exteneded partition with Ubuntu and it's partitions inside that as logical partitions ...

---

