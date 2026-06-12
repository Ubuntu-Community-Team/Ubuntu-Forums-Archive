---
title: "Reinstalling partition running ubuntu without formatting"
date: 2012-12-22
forum: Installation &amp; Upgrades
---

### Post by GuilhermeBrant on 2012-12-22
Hi everybody,

I have two partitions on my PC (both of them running ubuntu). On one of them, the computer crashed (due to overheating) while upgrading from 12.04 to 12.10. Now I can boot it, but before the login display appears it pops a window telling me that something gone wrong(something related to graphics card and/or IO devices) and offers me some options to try fixing the problem. 

I guess the easiest way to fix it would be to reinstall that partition, since there is no data in there that I need to keep. But I'd like to do it without messing with bootloader and without formatting the other partition (the one I'm using right now). 

If, when installing ubuntu via a USB storage, I choose "manually edit partitions" and select the partition I want to reinstall, will I correctly reinstall ubuntu on that partition only without changing anything besides that?

---

### Post by darkod on 2012-12-22
Yes. Choose the manual install (Something Else) and in the partitioning step it will show you the partitions list. Select the one you want to reinstall (make sure you select the correct one), click the Change button below.
In the windows that opens select the Use As as ext4 (or another filesystem if you want), select the mount point / and tick the format box because you need it to format and delete the previous install.
For the bootloader location select the MBR of the disk, for example /dev/sda. There should not be a number in it.

Earlier you could avoid installing the bootloader grub2, but now you have to select a destination and install it. But that's not a problem, because if you want your other installation to control the bootloader, you can simply boot it later and install its own bootloader to the MBR.

---

