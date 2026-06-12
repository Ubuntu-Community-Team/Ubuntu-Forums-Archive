---
title: "Grub Hosed, Can No Longer Boot"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by danben on 2010-03-29
I have an HP Envy with two software-RAIDed disks on which I wanted to install Ubuntu.  I had heard from other Envy owners that Lucid provided the best hardware support; however, the version of GParted on the Lucid Alpha 3 ISO wasn't using dmraid to see the partitions.  My solution was to partition the drive with a Karmic Live CD, then install Lucid 3.

I had some problems with Lucid, so I decided to go back and try Karmic with an updated kernel, so I wiped the partition containing Lucid from Windows and installed Karmic.

Now when I boot, GRUB gives the following error message:

"error: no such device: <long string>"

and I find myself in grub-rescue (I have no idea whether this is GRUB or GRUB 2).  A google search about the problem turned up a few suggestions, none of which I have been able to use as the only command I can get it to recognize is ls.  For what it's worth, ls shows me the following:

(hd0) (hd0,4) (hd0,3) (hd0,2) (hd0,1)

which I imagine correspond to the drive and its four partitions.

I can boot from the LiveCD (on a USB stick, since this machine has no optical drive), so I tried to wipe the partition and reinstall Karmic, but now the install fails when it tries to install GRUB.  /boot/grub contains one file, grubenv, which has no discernible useful data inside of it.

After a couple of hours of searching around aimlessly, I've decided I'm far over my head here.  Can anyone help?

---

### Post by drs305 on 2010-03-29
I don't use RAID, but try holding down the SHIFT key during boot. 

If you can get to a menu, and if it's GRUB 2, highlight a menu entry and press "e". This should open the selection for editing. Cursor to the line which starts with "search" and use the DEL key to remove the entire line.

Press CTRL-x to begin the boot. If it boots normally, post back and we can edit some files if necessary to eliminate the "search" line permanently. Or you can refer to this post on how to modify /usr/lib/grub/grub-mkconfig_lib.
[http://ubuntuforums.org/showthread.php?t=1441237]("http://ubuntuforums.org/showthread.php?t=1441237")

If this doesn't help, also check your BIOS settings to make sure they are still set correctly.

---

### Post by danben on 2010-03-29
Holding down SHIFT didn't do anything useful.  BIOS settings all look fine -- then again, I don't see anything in the BIOS that would particularly affect this.  Only boot order seems related, and it is definitely booting from the hard drive when I get the error.  My guess is that if there's any solution, it's going to involve booting via the Live CD and reconfiguring or reinstalling GRUB from there, but nothing I've tried so far has been successful.

---

### Post by drs305 on 2010-03-29
Here is the link to reinstalling G2 from the LiveCD if you haven't already seen it. Best of luck.

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by danben on 2010-03-29
Thanks for the link.  I got to step 4 in the first section, but 

```

sudo mount /dev/sda1 /mnt

```gives me

```

mount: special device /dev/sda1 does not exist

```(though it does show up in fdisk -l).

In the second section, I got to step 4e before finding that I have no device.map file.

Any ideas on how to proceed?  I haven't been able to find anything related to a missing device.map.

---

### Post by danben on 2010-03-29
After some more struggling, I've decided that the only reason to keep Windows around would be if I wanted to sell the machine, and no one's going to buy it as it is, so I think I might just wipe all the partitions and install Karmic, then take it from there.  Thanks for the help.

---

### Post by danben on 2010-03-29
Wait, one more thing - if I'm understanding all this correctly (and I very well may not be), it isn't that I overwrote the Windows MBR with GRUB, but that the MBR on this machine had some pointer to the Windows bootloader that was overwritten with a pointer to GRUB on my Karmic partition, right?  If that's the case, then why does GRUB run at all if I remove the Karmic partition and reboot?

Then again, if GRUB was contained entirely within the Karmic partition, I'd think it wouldn't know how to launch Windows, so maybe I've got it all confused.  Can anyone shed some light on this?

---

### Post by oldfred on 2010-03-30
There have been issues with drives that have hidden raid info on them. If you are not running raid now.


If you are still running raid do not do this:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb

sudo apt-get remove dmraid

If you are running raid:
If you are installing on RAID you need to use the Alternate Install CD (image). Read here about the difference:
[http://releases.ubuntu.com/karmic/](http://releases.ubuntu.com/karmic/)

---

