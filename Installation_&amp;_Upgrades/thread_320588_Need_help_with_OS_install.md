---
title: "Need help with OS install"
date: 2006-12-17
forum: Installation &amp; Upgrades
---

### Post by yfronto on 2006-12-17
I'm trying to install from a 6.06.1 CD, but I'm having trouble. I'm running four 80gig HDs on a RAID0 configuration through the bios. XP pro came pre-installed on the machine, and I don't want to wipe that partition. Here's what I've done so far:

[LIST]I downloaded and installed dmraid. Now it sees my 4 drives as one device under /dev/mapper. [/LIST][LIST]I used ntfsresize and then fdisk to make another partition, then I had my 150gig partition for Windows and an empty 175gig for Ubuntu. [/LIST]

I haven't started the install yet, but everything seemed to work fine so far, as I can mount the new drive with no problem from a LiveCD (after installing dmraid every time I boot with the CD, obviously), and it still boot into Windows. I want to make sure I have a few kinks worked out before going ahead, since I don't want to make my system unbootable. I prefer Grub, since it's what I'm familiar with, but any bootloader will work, I just would like to know how to make sure the RAID drivers are loaded after the install. In summation (since I'm somewhat long-winded at times):

[LIST]I have a partition ready for an install, but it's only seen when I load dmraid before starting the install.[/LIST][LIST]I want to make sure my bootloader will read the RAID partitions; instead of seeing HD(0,2) as my 3rd physical disk, it should see it as my linux partition (0,0 being NTFS and 0,1 being my swap).[/LIST]

Any ideas?

Thanks

Note: Be gentle, I'm a long-time slacker new to Ubuntu. :)

---

### Post by yfronto on 2006-12-17
Went ahead and tried to install the system on the partition that the partition loader sees, got this error:

The attempt to mount a file system with type swap in LVM VG nvidia_ecbfcgcd2, LV nvidia_ecbfcgcd2 at none failed.

You may resume partitioning from the partitioning menu.

Choices are "Go Back" and "Continue", both of which close the dialog box and nothing else.

Any help?

---

