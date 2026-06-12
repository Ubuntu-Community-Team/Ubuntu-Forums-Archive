---
title: "File System Creation Fails.  Why?"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by FireDemonSiC on 2010-08-08
I'm trying to install Ubuntu alongside windows 7 on my machine, and currently I am having difficulty doing so.

Upon initial boot of the LiveCD, it says the installer has encountered an unrecognized error and just goes straight to desktop environment.  From there, I can restart the installer just fine but here is where the trouble starts.

Currently, I have a 2TB RAID 0 array utilizing 4 500GB Seagate barracuda SATA II drives.  The controller is an nForce 780a NVRaid.  I currently have two NTFS partitions for windows.  One 150GB primary partition for C:, and another 781GB D: for the storage of games, music and movies.

When I try to manually setup the partitions in the Ubuntu installer, I do it like this.

- 200MB ext2 primary partition for /boot
- 150GB xfs logical partition for /
- approx 750GB xfs logical partition for /home (You've probably figured out I'm following the same C: and D: scheme as in windows)
- 8192 MB partition for swap

I then proceed with the install.  I see the progress bar complete for the boot partition, but then at about 7% for / it stops and gives a message saying partition creation has failed.  I even tried using different filesystems like ReiserFS and Ext4.  Same thing every time.

What is going on here?

I am running a 64bit quadcore system BTW if that is of any importance.

---

### Post by Rubi1200 on 2010-08-08
The latest version of Ubuntu has issues with RAID.

You need to install using the Alternate CD; should work fine.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download#alternate)

---

### Post by FireDemonSiC on 2010-08-08
Right back in the same boat I was when I tried gentoo LOL!  Thanks.

---

### Post by FireDemonSiC on 2010-08-09
I just tried the alternate install CD, and it only made matters worse.  It gives the exact same problem as the graphical installer, and on top of that it had the courtesy to corrupt my C: partition so I have to reinstall windows 7 now.

Guys, unless someone can come up with a solution I'm going with a different distro.  This is becoming ridiculous and I'm already starting to hate ubuntu because of it.

Two things I have noticed is that the filesystem creation is successful ONLY if using ext2.  Anything else (Journaling issue perhaps) fails.  I've also noticed that the installer appears to be overestimating free space.  Identifying partitions at 8xxGB when they are really 7xxGB.

---

### Post by Rubi1200 on 2010-08-09
I am really sorry to hear that this has caused so many problems.

I don't know if this will help, but take a look here:

[https://help.ubuntu.com/community/Installation/SoftwareRAID](https://help.ubuntu.com/community/Installation/SoftwareRAID)

and here:

[https://wiki.ubuntu.com/ReliableRaid](https://wiki.ubuntu.com/ReliableRaid)

See also here:

[http://ubuntuforums.org/showthread.php?t=408461](http://ubuntuforums.org/showthread.php?t=408461)

The thread is very old, but some of the things may still apply and I saw that the OP links to a number of different sources.

Hope this helps!

:)

---

### Post by ronparent on 2010-08-10
The basic problem is that gparted, as distributed, will not recognize raid or raid partitions. To get around this, I suggest booting to a live cd and installing from there. _Before_ you start the install use the synaptics pakage manager to install kpartx for the live session. After this the install should proceed normally. You may and will probably get a 'fatal error' on the grub install - this is fixable. Let us know how you make out. Good luck.

ps At last look the fakeRAID how to wasn't updated for an install to lucid.

---

### Post by FireDemonSiC on 2010-08-16
> **ronparent said:**
> The basic problem is that gparted, as distributed, will not recognize raid or raid partitions. To get around this, I suggest booting to a live cd and installing from there. _Before_ you start the install use the synaptics pakage manager to install kpartx for the live session. After this the install should proceed normally. You may and will probably get a 'fatal error' on the grub install - this is fixable. Let us know how you make out. Good luck.

ps At last look the fakeRAID how to wasn't updated for an install to lucid.

When installing grub, is this the same as the oldschool days I remember where it had to be installed on a partition that resided on the first 1024 cylinders of the drive in order to be bootable?  I thought I read somewhere it can now be installed anywhere.

---

### Post by ronparent on 2010-08-16
No, grub can be installed anywhere on any size drive as long as the installation can be found by uuid. I have found consistently that the result of where grub writes to a MBR has been inconsistent when the OS is installed to a raid (if that makes any sense). In other words despite specifying a raid MBR location in the advanced box in step 8 of 8 during the install I don't find it on reboot and have to fix it with a live cd session.

---

### Post by FireDemonSiC on 2010-08-19
OK what the...

---

### Post by ronparent on 2010-08-20
Either you didn't install kpartx before proceeding with the installation, or, there is an additional bug that doesn't permit creation of an xfs file system (perhaps maybe the latter)?

---

### Post by FireDemonSiC on 2010-08-20
> **ronparent said:**
> Either you didn't install kpartx before proceeding with the installation, or, there is an additional bug that doesn't permit creation of an xfs file system (perhaps maybe the latter)?

It's the latter, which is what I've been hinting at since the beginning of this post.

I tried running the gparted application seperately from the LiveCD which actually recognized partition sizes properly and allowed me to setup my layout.  However, the formatting process still fails.  I can format everything in ext2 but any partition that I set as ext3, xfs or reiserfs fails to format.  Any ideas?

---

### Post by FireDemonSiC on 2010-08-20
Well guys, I finally got the XFS partitions to create.  What was the big mystery?  Apparently, it didn't like it when the "Round to cylinders" box wasn't checked.  This must be something that the installer disables by default because it never even gave the option and it failed every time.

After installing kpartx then using gparted, the XFS partitions created fine as long as I was rounding to the closest cylinders, and now my partition table looks like this :popcorn::

---

### Post by FireDemonSiC on 2010-08-20
OK one last hurdle to overcome.

The install went fine.  Lucid installed and gave no errors throughout.  However, upon reboot, it just boots straight into Windows 7 as if GRUB doesn't exist.

I told the installer to place the bootloader on the third partition which is my 200MB ext2 partition for /boot.

How do I go about correcting this?

---

### Post by ronparent on 2010-08-20
Yes, the installer does seem to have a problem getting the grub 2 install right. Check out this reference: 

[https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands](https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands)

The section on "Reinstalling GRUB 2" should handle it.

---

### Post by FireDemonSiC on 2010-08-20
> **ronparent said:**
> Yes, the installer does seem to have a problem getting the grub 2 install right. Check out this reference: 

[https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands](https://help.ubuntu.com/community/Grub2#Post-Restoration%20Commands)

The section on "Reinstalling GRUB 2" should handle it.


After installing Ubuntu, the Software Center will not load and I cannot install software via .deb files either.  I am unable to fix GRUB because I cannot load kpartx and recognize my RAID array.  Any idea why this is happening?

---

### Post by ronparent on 2010-08-20
You need kpartx primarily to allow gparted to recognize your raid partitions. You can install kpartx using synaptics (System> Administration> Synaptics Package Manager) or thru a terminal with the command - sudo apt-get install kpartx

You need to be following the instructions in the grub 2 reference I gave you. What you are trying to do is to write the grub boot leader to the MBR. The MBR you are trying to write to resides on the raid array if that is what you are trying to boot on (ie /dev/mapper/<your raid array>) - not to an individual disk device (/dev/sda, sdb, etc). The raid partition you are installed to is the root, not the target for the boot loader.

---

### Post by FireDemonSiC on 2010-08-22
Thank you that worked perfectly.  However, I now face another post install problem.

[http://ubuntuforums.org/showthread.php?p=9752533#post9752533](http://ubuntuforums.org/showthread.php?p=9752533#post9752533)

---

