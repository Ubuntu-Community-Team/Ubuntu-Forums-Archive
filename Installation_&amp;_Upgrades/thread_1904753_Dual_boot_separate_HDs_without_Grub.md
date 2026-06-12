---
title: "Dual boot separate HDs without Grub"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by Vtwin on 2012-01-05
I want to dual boot Win7 and Ubuntu 11.4 on separate HDs but I want to choose which to boot in the BIOS not Grub. So I don't want Win7 added to Grub menu or Windows mbr altered. Will Grub do this automatically though when it updates or even when it finds the Win7 HD. Can anyone enlighten me on this situation, thanks.

---

### Post by oldfred on 2012-01-05
It will not do it automatically, but it is the way I suggest for all with multiple drives. Then each drive can be booted from BIOS, but grub will let you also boot Windows so you can set BIOS to boot the Ubuntu/grub drive and just choose in the grub menu. Then the Windows MBR is not changed at all. Instructions for second drive are the same for any drive not the first drive as the main difference is the manual partitioning and choice of where to install boot loader.

To get grub to install to sdb or the second drive, you have to use manual install or Something else. Then on the partitioning screen is a combo box that will default to sda. You have to change to sdb, but not any partitions like sdb1, sdb2 etc.

If you have Windows on the second drive, it may have its boot loader on the first drive in the 100MB boot/repair hidden partition, so check what is where.

Install to external drive 11.04.
[http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/](http://www.linuxbsdos.com/2011/05/23/install-ubuntu-11-04-on-external-hard-disk/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

### Post by Mark Phelps on 2012-01-05
Have similar preferences -- multiple drives, each with its own OS, each bootable on its own.

Found the safest approach is to have only the target OS drive connected during OS installation.  That way, there is no risk of boot loaders getting installed to the wrong drive.

---

### Post by Grenage on 2012-01-05
A low-tech alternative would be to unplug the Windows HD and then install Ubuntu.  Then you've got two drives, with two boot-loaders.

Personally, I'd also use Grub.

---

### Post by Rebelli0us on 2012-01-05
If you can, just disconnect your Windows disk during the Ubuntu install. Then reconnect it and use BIOS to choose the boot disk.

---

### Post by Vtwin on 2012-01-05
Thanks for your help everyone. I did disconnect the Win7 drive and installed Linux. I have the option to press a key when booting (F8) and can then choose which drive to boot. Seems OK and working without any problems.

---

