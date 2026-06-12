---
title: "Need help installing grub on the root partition"
date: 2005-06-08
forum: Installation &amp; Upgrades
---

### Post by asphyx on 2005-06-08
Hello,

I get the following messages when I try to install grub on my root ubuntu partition :
[I]
root@asphyxia:~ # grub-install /dev/sda6
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)   /dev/fd0
(hd0)   /dev/sda
(hd1)   /dev/hda
[/I]

Could anyone tell me what the problem is. I tried googling but didn't find anything helpful. I installed a few fonts usng apt-get in an attempt to de-uglify gtk fonts and after that grub stopped working. (I wouldn't know if theres a connection)
I'd not installed grub on the MBR but on the root drive and was using the linux.bin file to boot using windows bootloader. 
After installing the fonts GRUB refused to start and it just shows the 'GRUB' text on the top left corner of the screen and no activity at all.

Is there a problem with my hard drive/partition or something or is it just the software ?

I'm confused
Help
 :neutral:

---

### Post by alastair on 2005-06-08
There are no errors there :

"Installation finished. No error reported."

So, something else is wrong.

I cannot see how installing fonts can cause this problem. I assume your PC BIOS is the same e.g. disk boot order etc.?

---

### Post by asphyx on 2005-06-11
Yes, my pc bios order is the same, besides I changed the order and have tried a few times too, same message. Is xfs_freeze related to the X font server or is it something else ? grub installs and works fine on the MBR, but not on the root partition.
I wanted to install it on the root partition to be able to use the windows bootloader to boot into linux. Doesn't seem to work :(

---

