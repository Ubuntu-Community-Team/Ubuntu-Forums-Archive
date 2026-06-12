---
title: "No XP in Grub menu"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Psyphre on 2007-05-05
Hi, I've installed ubuntu many times on this hard disk before with no problems. This time, when i installed ubuntu, XP no longer appears in the grub list even though my XP partition is accessable within ubuntu.

Is there any way to fix this without having to install XP and then reinstall ubuntu again?

Thanks.

---

### Post by KIAaze on 2007-05-05
Try editing your /boot/grub/menu.lst file. (Back it up first of course!)

The entry for Windows should look something like this:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows, Codename: XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I cannot garantee that it will work, since I have never tried it before.
All I did until now with my menu.lst file was adding boot options (boot as root for example ("single user mode")) or changing the names of the entries.

But there's no risk in trying it.
As long as you leave the other entries as they are, you'll always be able to boot back into a working OS. ;)

re-edit:
And if you want to do things with a GUI instead, try this:
[http://ubuntuforums.org/showthread.php?t=228104]("http://ubuntuforums.org/showthread.php?t=228104") ;)

edit:
Here's some more info about how the menu.lst file works:
[http://www.gnu.org/software/grub/manual/grub.html#Filesystem]("http://www.gnu.org/software/grub/manual/grub.html#Filesystem")
> 
The device syntax is like this:

     (device[,part-num][,bsd-subpart-letter])

`[]' means the parameter is optional. device should be either `fd' or `hd' followed by a digit, like `fd0'. But you can also set device to a hexadecimal or a decimal number which is a BIOS drive number, so the following are equivalent:

     (hd0)
     (0x80)
     (128 )

part-num represents the partition number of device, starting from zero for primary partitions and from four for extended partitions, and bsd-subpart-letter represents the BSD disklabel subpartition, such as `a' or `e'.

A shortcut for specifying BSD subpartitions is (device,bsd-subpart-letter), in this case, GRUB searches for the first PC partition containing a BSD disklabel, then finds the subpartition bsd-subpart-letter. Here is an example:

     (hd0,a)

The syntax `(hd0)' represents using the entire disk (or the MBR when installing GRUB), while the syntax `(hd0,0)' represents using the first partition of the disk (or the boot sector of the partition when installing GRUB). 

So (hd0,0) should hopefully work. :)

---

