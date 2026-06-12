---
title: "iso to usb, boot sector empty"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by MichaelBurns on 2011-01-07
I dd'ed a backtrack iso onto a usb stick:
```
dd if=backtrack.iso of=/dev/sda
```
(i.e. not to a partition, but directly to the stick).  It won't boot (no surprise of course).  I checked the boot sector:
```
dd if=/dev/sda skip=0 count=1 bs=512
```
and it is full of null bytes (i.e. empty, and particularly not marked as bootable).  I browsed the isofs for a boot install script, but didn't find one.  (There are actaully very few files in there, maybe about 20 total.)  I am thinking to use fdisk to set the bootable flag, but it wants to write a partition table.  How can I prevent fdisk from writing a partition table?

[i]
edit:
I decided to just copy the boot flag from my running Ubuntu installation (after first confirming that it is indeed the expected 55aa):
```
dd if=/dev/hda skip=255 count=1 bs=2 of=/dev/sda seek=255
```
Of course, I don't expect this to work since it is just a flag, and there is no boot code in the rest of the sector, but I have no idea what I'm doing, so I'm just going to try it.  We'll see.  If my computer doesn't explode, I'll try to remember to report back here with the results.
[/i]

---

### Post by oldfred on 2011-01-07
I believe this script will install backtrack to a flash drive:

MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)

and this one:

multicd.sh - combine Linux ISOS into one
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)

---

### Post by C.S.Cameron on 2011-01-07
UNetbootin should also work with BackTrack.

---

### Post by MichaelBurns on 2011-01-08
Thanks for the help.  I am already aware of unetbootin.  I am just playing around.  After a long time trying, I still cannot get my head around the boot process.  BTW, just setting the boot flag did not work, of course.

---

### Post by oldfred on 2011-01-08
Boot flag is used by windows & lilo to know what partition to jump to to find more boot code in the partition boot sector. Grub does not have code in the partition boot sector (normally) so it does not use boot flag. Some BIOS, though, will not let you boot at all unless you have a boot flag on a primary partition.

While mostly about windows, this helps you understand the boot process with MBR(msdos) systems. Lots of details, but pictures explain a lot:

Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

