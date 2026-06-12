---
title: "Dapper hangs on mounting Filesystem"
date: 2006-06-13
forum: Installation &amp; Upgrades
---

### Post by brucenduane on 2006-06-13
I copied a working Dapper system from one drive to another drive.
The original drive had 4 partitions and Dapper was in sda1 with swap in sda4

New drive has 10 partitions with the Dapper copy in sda6, swap in sda3, and a happily working Breezy in sda1.

I have copied other Linux distributions between drives by copying all the files and then changing three files  /boot/grub/menu.lst   /etc/mtab  and /etc/fstab    and it works with Breezy and other linux distributions.   I changed sda1/boot/grup/menu.lst since that is the menu.lst that boots this disk.

This didn't work with Dapper.  It hangs with a kernel panic while mounting the  filesystem (second line on the startup screen)  
I changed grub/menu.lst from "ro quiet splash"  to " ro vga=791" to get more detail.

The message just before the kernel panic talks about missing file under scripts..../nfs-prefetch/    This directory is empty on my other Dapper system.  (The problem system is at a friend's house and not in front of me now.)

The problem Dapper image is running on the same hardware in the same box but on a different disk drive.  The disk drives are in removable drawers so Dapper in the 4 partition drawer works.  The Dapper in the 10 partition disk doesn't.

Is there another file I need to change to get Dapper running?
Is lvm (load but not being used)  or udev causing this problem?
The only other file that mentions the disk partitions in /etc  is /etc/lvm/.cache
It still cache's the old 4 partitions -- Can I delete this file and let lvm rebuild it?  

Thanks for reading this and for the great help!
-bruce.

---

### Post by brucenduane on 2006-06-18
Problem solved!

I got to work on my friends computer today and got Dapper working.

Changes:
sudo mv /etc/lvm/.cache x.cache  # renamed the old .cache file so system would build new one.

edit file: /etc/mkinitramfs/conf.d/resume
change RESUME=/dev/sda4  to RESUME=/dev/sda3   to point to swap in sda3

added "resume=/dev/sda3"  to the kernel line in /boot/grub/menu.lst

Dapper booted fine and we were able to download the pending 112 updates.

So in summary for Dapper to be copied to a new drive:
Modify the following files:
/boot/grub/menu.lst         #define the proper drives, add  "resume=<swap device>"  ie resume=/dev/sda3
/etc/fstab      # define the drives
/etc/mtab      # define the drives
/etc/mkinitramfs/conf.d      # RESUME=<swap device>  ie =/dev/sda3

Remove or rename the file:  /etc/lvm/.cache

Dapper should then boot in the new drive.
-Bruce.

---

