---
title: "Grub boot loader problem...I think."
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by prizefighter on 2005-05-08
First of all, I'm green....real green.

After loading ubuntu on my hdb seemingly successfully I get no boot loader menu to select my OS which is on hda.  During the installation, it loaded Grub to the beginning of hda like I expected it to.  The pc rebooted and after POST, the screen goes black for a few seconds and up comes linux.  No menu which also means no way to get back to Windows.  So since I'm a noob, I decide to fix the MBR to get it the way it was, wipe and re-install ubuntu and try to use Lilo if possible as a boot loader because that worked when I had a previous installation of Mandrake on my 2nd hard drive.

The problem now is I don't get video of my windows boot disk anymore.  After giving me the 'checking hardware config' message, it goes blank but it still looks like its doing what its supposed to based on the sounds the CD and the hard drive makes.

I'm not sure if this can be solved within linux or if there is something else i can do.  Any help would be appreciated.

---

### Post by spd106 on 2005-05-09
Hi, I would suggest using a live cd of Ubuntu or perhaps Knoppix to boot up the pc and check out what's going wrong. You will probably need to look at /boot/grub/menu.lst and maybe /etc/fstab to check on the partition structure.

Look at the following for a similar guide

[http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows](http://www.ubuntulinux.org/wiki/RecoveringUbuntuAfterInstallingWindows)

If you know what's in fstab then it may be possible to create a floppy boot disk with grub or lilo. This link may be useful
[http://www.ubuntulinux.org/wiki/HowToMakeAGRUBBootFloppy](http://www.ubuntulinux.org/wiki/HowToMakeAGRUBBootFloppy)

This may also yield some results
[http://www.ubuntuforums.org/showthread.php?t=23368](http://www.ubuntuforums.org/showthread.php?t=23368)

Good luck

---

