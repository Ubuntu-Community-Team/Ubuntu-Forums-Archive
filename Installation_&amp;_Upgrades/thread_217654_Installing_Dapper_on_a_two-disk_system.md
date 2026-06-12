---
title: "Installing Dapper on a two-disk system"
date: 2006-07-17
forum: Installation &amp; Upgrades
---

### Post by infidel on 2006-07-17
Hello, all. I have a new computer coming in the next day or two, and I plan to install Dapper on it. Sadly, I'll need to leave the OEM Windows partition in place (it's a long story). I'm no stranger to dual-booting from a single hard disk, but I would like to install a second disk in this machine and install Ubuntu to that. Is there anything in particular I need to watch out for? Is it as simple a matter as installing the drive and booting from the Ubuntu install media (i.e., is Ubuntu going to see that second drive and be able to make use of it), or is there anything special I should do, or be on guard for? Is my bootloader going to need some hands-on attention in order to be able to boot either OS? (If it matters, Ubuntu will be booted FAR more often than the Windows partition).

I have absolutely no experience in dealing with more than one internal hard disk under Linux, so any and all guidance would be greatly appreciated. Thanks very much in advance.

---

### Post by confused57 on 2006-07-17
Here's how I set my system up:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

I like this method, because it doesn't install grub to the Windows mbr.

---

### Post by atrophic on 2006-07-17
Ubuntu makes it really easy if you don't mind overwriting the Windows MBR or have ubuntu installed on your first hard drive (as that's what ubuntu's installer will write grub to).  The guide confused57 posted is very useful too.  I had some problems mixing SATA and IDE drives on a dual boot system but it was eventually resolved too.

---

### Post by infidel on 2006-07-19
I agree that confused57's guide is great, but I've run into some trouble. It may be as simple as the jumpers on the drives being wrong (though I've checked them over and over); perhaps not.

I took out the Windows drive and replaced it with a blank drive, jumpered as primary master and plugged into master position on the primary IDE cable. Installed Dapper onto this drive, applied all available updates and installed a couple of other necessities, then shut down and reinstalled the Windows drive, cabled and jumpered as primary slave. Rebooted Ubuntu, and added this to /boot/grub/menu.lst :
```
title      Windows XP
root      (hd1,0)
savedefault
makeactive
map      (hd0)(hd1)
map      (hd1)(hd0)
chainloader      +1
```
(I also "un-hid" the boot menu and increased the timeout a bit).

I rebooted, and got this:
```
root      (hd1,0)
savedefault
makeactive
map (hd0)(hd1)

Error 11: Unrecognized device string.
```
Noting that confused57 mentioned a possible reboot error, I changed 'root      (hd1,0)' to 'rootnoverify      (hd1,0)', but unfortunately had the same result.

I'm no hardware guy, but I'm near-certain that I have the jumpers and cabling right. (I say "near" because the guy who put together the diagrams may have been drunk.) Does this mapping error suggest otherwise? Ought I to have done something in the BIOS?

Any further guidance would be greatly appreciated. Thanks very much in advance.

EDIT: In the meantime, I may have stumbled across a functional (though non-ideal) workaround-- using my computer's own <F10>-at-startup boot menu, I can choose which drive to boot from. Windows booted from the second drive without complaint; sadly, I'm downloading a boatload of Winblows updates right now and can't test whether or not this method did anything funky to the Ubuntu drive. Is that likely, and/or are there any other reasons why I shouldn't use this method to dual-boot? Thanks.

---

### Post by confused57 on 2006-07-19
I've seen other posters who use the bios to select which OS to boot into, so it shouldn't be a problem...don't think it would affect either OS.

What is your output of:

```
cat /etc/fstab
```
and
```
sudo fdisk -l
```
The -l is a small "L"

Here's an excellent grub tutorial:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

Did a google search and found this:
[http://www.justlinux.com/forum/showthread.php?t=126755](http://www.justlinux.com/forum/showthread.php?t=126755)

---

### Post by infidel on 2006-07-20
cat /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
```
And fdisk -l:
```
Disk /dev/hda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19795   159003306   83  Linux
/dev/hda2           19796       19929     1076355    5  Extended
/dev/hda5           19796       19929     1076323+  82  Linux swap / Solaris

Disk /dev/hdb: 164.6 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *         581       20022   156167865    7  HPFS/NTFS
/dev/hdb2               1         580     4658818+   b  W95 FAT32

Partition table entries are not in disk order
```
I'm a bit puzzled by the stats on /dev/hdb -- I didn't expect to see two partitions there. Could that be part of the problem?

At any rate, I hope this provides some useful information.

To be honest, though, if there's no immediate fix for booting Windows from GRUB, I would be completely satisfied to keep using the BIOS option. It hasn't led to any trouble yet.

Thanks for looking.

---

