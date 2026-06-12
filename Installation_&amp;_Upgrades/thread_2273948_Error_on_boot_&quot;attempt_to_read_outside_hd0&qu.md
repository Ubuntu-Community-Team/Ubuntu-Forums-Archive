---
title: "Error on boot &quot;attempt to read outside hd0&quot; after working for several months."
date: 2015-04-16
forum: Installation &amp; Upgrades
---

### Post by malfindin on 2015-04-16
I have read all the current information on "attempt to read outside hd0" and even in the solved threads none of them seem to be the problems I'm having.

I'm running Ubuntu 14.04 on a Rocket RAID 5 4.5 Gig partition. With dual boot to Win 7 on a remaining 500gig single partition on one of the 4 RAID drives.

It installed and worked just fine FOR MONTHS.

Then I started getting "attempt to read outside hd0" and a kernel panic crash on the current installed Kernel.

If I use advanced options I can go back to an earlier Kernel and it boots. If I reboot from there that Kernel crashes and I have to go back to an even earlier Kernel...

At this point I have but one working Kernel left and cannot reboot again for fear of never seeing my desktop again...

~Frank

---

### Post by yancek on 2015-04-16
I'm not sure if I'm reading this part of your post correctly "I'm running Ubuntu 14.04 on a Rocket RAID 5 4.5 Gig partition".  Does that mean Raid 5 on a 4.5GB partition?  Is this a server edition because my recollection of the standard Ubuntu Desktop it requires 6+GB to install.

Were there any changes made immediately prior to seeing this problem?
Have you done a filesystem check from a Live CD/flash drive?  Try that:  sudo fsck -c /dev/sda3  (Replace sda3 with the correct partition number(s))

Can you mount any partitions with a Live CD and view files?  I have a friend who reported this same problem yesterday so I've done some searching online.  Haven't found anything reeally useful and most info I have seen seems to indicate bad hard drive(s)?  I don't use RAID so I'm not familiar with it and how it would complicate a problem of this sort.  Do you have a separate boot partition?  I would check the boot partition or directory to see if things look alright there, correct files available.  Have you made any partition changes?

---

### Post by malfindin on 2015-04-16
Yes so sorry... Terabyte not Gig. it's a RAID5 4 drives of 1.5 terabyte each striped.

Yes I can run live and read the drive.

I'm typing now on my VERY OLD Kernel from the machine with the issue. 

The issue occurred AFTER a Kernel update and is not the result of BAD drives.

But what's happening now is each time I reboot the system it corrupts whatever Kernel I'm running, requiring going back to an earlier Kernel. I'm out of "reboots"...

The next time I reboot will be the last time I see my desktop...unless I can FIX the issue.

---

### Post by malfindin on 2015-04-16
Yes so sorry... Terabyte not Gig. it's a RAID5 4 drives of 1.5 terabyte each striped.

Yes I can run live and read the drive.

I'm typing now on my VERY OLD Kernel from the machine with the issue. 

The issue occurred AFTER a Kernel update and is not the result of BAD drives.

But what's happening now is each time I reboot the system it corrupts whatever Kernel I'm running, requiring going back to an earlier Kernel. I'm out of "reboots"...

The next time I reboot will be the last time I see my desktop...unless I can FIX the issue.

---

### Post by malfindin on 2015-04-16
Also this system ran with the same configuration it now has since 2009 on Ubuntu 9.10 without issue.

The issue occurred 3 months after upgrading to Ubuntu 14.04. The BIOS is the same. The drives are fine. The RAID is unchanged and healthy.

Something in an update caused the issue. I believe it was a BIG update with Nvidia drivers. I have since purged Nividia.

---

### Post by malfindin on 2015-04-16
Now running on Kernel:

3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by oldfred on 2015-04-16
I have seen similar issue with very old BIOS and the 137GB boot limit. Also similar issue on USB drives.
An update adds a new kernel beyond the BIOS limit of 137GB where all previous kernels were within the limit.
There were similar issues with older versions of grub2 and drives somewhat over 500GB, but that was fixed as far as I know.

Where on drive are kernels. Boot-Repairs Summary Report often shows it, but Desktop does not have RAID drivers and Boot-Repair can get confused with RAID & LVM as both use /dev/mapper/....

Be sure to install RAID drivers to Desktop live installer first.
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by malfindin on 2015-04-17
Thank you. I'm out of town for the weekend so I won't be trying anything until at least Monday. I'll try it and let "the thread" know if that fixes the issue. Please keep the thread open until I give it a try... Thanks...

---

