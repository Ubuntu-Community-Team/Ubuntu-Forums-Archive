---
title: "&quot;Gave up waiting for root device&quot; at initramfs, along with keyboard lockup"
date: 2019-08-03
forum: Installation &amp; Upgrades
---

### Post by balefulbadger on 2019-08-03
So, in the last month I bought some new parts and put them together (default everything, except a change to the bios to allow the USB boot).
     - asrock z390 phantom 4 motherboard
    - intel i5-9400f cpu
     - 16GB corsair memory
- Sapphire R570 video card
    - seagate barracude 2 TB drive (sata6)
The USB stick started the Ubuntu 19.04 LiveCD without issue. I installed to the hard drive, having Ubuntu format the drive as one partition. (In truth, I also attempted separate partitions at first and tried many things over a few days, based on web posts and what I learned from them, but my break point occurred when I went for "let the install do everything and see if it works" and still received the error message and keyboard lockup).

So, the solution that worked was to run LiveCD, use these commands to format the drive with gpt and create the partition, then installed 19.04 without allowing LiveCD to format any portion of the drive. 
    - sudo parted /dev/sda mklabel gpt
    - sudo parted -a opt /dev/sda mkpart primary ext4 0% 100%
    - sudo mkfs.ext4 -L NewPartition /dev/sda1

I'm posting this info because:
   - maybe it will be useful to someone building a new PC
   - it seems odd that this solution worked but I didn't see it anywhere else
   - it seems strange the installed Ubuntu could not see the disk during initramfs, even though the installation process chose the MBR format and also chose the installation's boot settings

---

### Post by oldfred on 2019-08-03
If using gpt, you must have either an ESP - efi system partition for UEFI boot (recommended) or a bios_grub partition for the now very old BIOS boot or CSM.
        CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

I normally partition in advance & use Something Else to choose which partition is which.
Often best not to have / (root) as one very large partition. Ubuntu was configured years ago when drives were much smaller or users were dual booting and somewhat larger drive was shared.  Now with TB sized drives it make a very large / by default.

For a new user a separate /home is easier as it creates mount point, adds entry to fstab, and sets ownership & permissions for user. Some also like data partition(s) but then have to do all the configuration manually. Not really difficult once you know, but a lot for a new user.

---

### Post by balefulbadger on 2019-08-04
I'm just hoping that it will be noted that the mbr  formatted drive was not being found during initramfs, even though Ubuntu  was currently being booted from that same drive and that LiveCD had chosen  the mbr format. Or, that if someone else has this issue, they find the solution takes less time than it did for me.

Since the install is working now, I set up separate partitions so I can have multiple linux versions that share user/data partitions. I'm not completely new to this, but then again, still new to  this...

---

### Post by oldfred on 2019-08-04
I do not think for most systems it matters if Ubuntu live installer is MBR or gpt. A few will only boot from one or the other.

So did you install in the old BIOS/MBR configuration, even though new UEFI system?

---

### Post by balefulbadger on 2019-08-05
Yes, I obeyed the internet and ran fdisk or gdisk on the new drive, and e2fsck, and chose mbr when I needed to run gpt... This makes sense now... the formatting of the partition table is not the same as the formatting of the data portion of the drive. The LiveCD process probably doesn't touch the partition table for good reasons, but I read the "Erase disk and install Ubuntu" choice on LiveCD to mean more than it did.

Thank you for talking this out :p

---

