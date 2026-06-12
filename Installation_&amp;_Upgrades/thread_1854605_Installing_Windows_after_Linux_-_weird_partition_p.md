---
title: "Installing Windows after Linux - weird partition problem"
date: 2011-10-04
forum: Installation &amp; Upgrades
---

### Post by jonathan2216 on 2011-10-04
Hello all, and thanks in advance for your help.

I've searched the forums and can't find anything similar which might help me with the problem I'm about to describe.

Put simply, my PC has a 500GB drive which I had partitioned solely with Linux, then shrunk the root partition by 80GB to install Windows XP. Here's a screenshot of gparted showing how the disk is currently set up.

[IMG]http://i53.tinypic.com/mbuatd.png[/IMG]

You can see the unallocated 80GB of space there, and my thoughts were that the Windows installer would be able to use that.

However, on reaching the point of selecting the partition to install Windows to, the installer reports as follows - (apologies for the poor image quality, this is a photo of my monitor's display at the time)

[IMG]http://i56.tinypic.com/330a2jd.jpg[/IMG]

Rather than the 80GB I'd expect the Windows installer to see, it's reporting just over 131GB. All of the options available to me at this point seem potentially destructive to how the disk's partitioned at the moment so I'm reluctant to proceed with the installation.

I'd be grateful for some expert advice on this. I don't understand why the Windows installer is reporting 131GB when 80GB is left unallocated, and as you can see from the gparted shot that no partition is even remotely 131GB.

Again, many thanks in advance.

- Jonathan

---

### Post by ajgreeny on 2011-10-04
Very odd!

Perhaps it is worth formatting the unallocated space as ntfs with gparted and seeing what happens then when you try to install windows.  I can not see any good reason for the discrepancy in sizes shown, not even the potential difference of 1024:1000 ratio would do that if one system used 1024 Mb per Gb, and the other 1000 Mb per Gb.

---

### Post by Shazaam on 2011-10-04
Windows has always shown my linux partitions as "Unknown" That is your Ubuntu partition so don't install Windows there. You will want to install it to an unpartitioned space.

Easy fix.
Boot your Ubuntu livecd. Open gparted and highlight the ext4 partition, choose "Resize/move". Move the Ubuntu partition to the right. This will take a while to run.
When done, try to see if Ubuntu boots. If it does fine, if not you will have to reinstall (or maybe just update) grub after you install Windows by using the Ubuntu livecd.
Install Windows in the new unpartitioned space at the front of the drive.

Now for a word of caution...
Windows loves to take over the whole drive when you install it. Make dead sure you choose the right place to install it.

---

### Post by jonathan2216 on 2011-10-05
Thanks ajgreeny and Shazaam for your replies.

**ajgreeny** - I'd tried formatting the unused space as a new NTFS partition and the Windows installer is showing the exact same outcome as the photo in my opening post in this thread. Good suggestion though, thanks.

**Shazaam** - I moved the unused 80GB of space to the start of the disk as you suggested. The move took about 3 hours to complete and when it did I formatted the 80GB to NTFS as **ajgreeny** suggested. 

The disk partitions now look like this (screenshot taken before I did the NTFS format):
[IMG]http://i51.tinypic.com/2wnmzwh.png[/IMG]

I tested it with a reboot back into Linux with no problems so I rebooted again with the Windows XP installation CD. Back to the partition setup stage of the Windows install process and... it's *still* reporting a 131GB partition and nothing else - exactly the same as before!

What on earth is going on with this thing?

---

### Post by SirDrexl on 2011-10-05
Windows is seeing the ext4 as nothing-it might as well be unallocated.   Remember that the Windows XP setup program dates back to 2001; I don't  think it was updated in the service packs.  You can't even install it to  a drive in AHCI mode without having the driver on a floppy and  intervening by pressing F6.

I don't know why it's not seeing the NFTS partition, but I think it's  best to just install Windows first, to an empty drive, then add Linux.   Let each installer do the formatting.  I remember Windows having to run a  check on a partition resized with Gparted, so maybe there's something  Windows (initially) doesn't like about the way Gparted handles NTFS?

---

### Post by oldfred on 2011-10-05
I do not know why Windows does not correctly see the unallocated, but when you formatted the NTFS partition, did you add the boot flag.

Boot flag = active partition in Windows and windows only installs or repairs active NTFS  primary (sda1 thru sda4) partitions. But it should see the unallocated as long as a primary partition was still available to assign.

---

