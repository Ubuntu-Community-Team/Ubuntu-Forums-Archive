---
title: "Trouble installing on multi-drive system w/ ATA expansion"
date: 2012-02-07
forum: Installation &amp; Upgrades
---

### Post by Boozin on 2012-02-07
OK, to begin a bit about the hardware setup that I am trying to work with.  This box is an older amd athlon using onboard PATA interface VIA and an expansion PATA card of the IT821x chipset.

Drive list:
Onboard VIA PATA chipset (pata_via)
1st channel master: 20GB "boot"/root drive
1st channel slave: CDROM
2nd channel master 200gb data drive for softraid
2nd channel slave: unused

Expansion ITE821x: (pata_it821x)
1st channel master: 200gb
1st channel slave: 200gb
2nd channel master:200gb
2nd channel slave:200gb

Ideally, I would like to run softraid 5 on the 200gb drives.  Now, the trouble is that the kernel seems to insist on mixing up the order of the drive designations.

Seems that most of the time the kernel insists on putting the IT821x expansion adapter as the first ATA interface.  So it gives SCSI0 and SCSI1 channels to the IT821x, and scsi2 and scsi3 to the onboard chipset.  So the drive designations become as follows after boot:

/dev/sda 200gb on expansion 1st channel master
/dev/sdb 200gb on expansion 1st channel slave
/dev/sdc 200gb on expansion 2nd channel master
/dev/sdd 200gb on expansion 2nd channel slave
/dev/sde 20gb on onboard 1st channel master (boot drive!)
/dev/sdf 200gb on onboard 2nd channel master

Now this is fine and all, I don't really care what the drives end up being named, but this seems to throw a wrench in the grub installation process.  The crux of the matter seems to be how the BIOS seems to think the drives should be named and how linux does it.  When grub gets installed, it sucessfully installs to /dev/sde but it cannot boot.  I suspect that grub sees the drives differently and it can't get to the root partition properly.  Any pointers on how to fix this? Boot parameters? Fudging grub's config file?

---

### Post by oldfred on 2012-02-10
Normally BIOS defines boot order and grub just installs to sda. The expansion card must be confusing things. Old IDE devices only booted from primary master.

Have you tried just reinstalling grub to the drive that is sda as well as the boot drive that ends up as sde?

Example is for sda5 and installing to sda, but you can install to any or all drives.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD/usb, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If grub 1.99 with Natty or later uses boot not root.
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

