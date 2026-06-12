---
title: "no CD-rom - can't restore MBR - how to grow XP partition and single boot?"
date: 2007-02-17
forum: Installation &amp; Upgrades
---

### Post by brallan on 2007-02-17
Hi, i'm giving away my old dell laptop and the person who wants to use it needs more room in the XP partition (0,0) and I'm worried that growing the partition to fill the entire disk will break GRUB.  

The CD-Rom is broken so I can't use the restore MBR option (that comes with the XP CD) or wipe the disk with a new install. 

It's got GRUB with dapper as default (0,1) and XP way down the list (0,0) and I'd like to just set XP as default and reduce time to one second or something like that but I fear that if I wipe the linux partition GRUB will no longer work. since the conf files are in the /etc directory on the (0,1) partition.

Is that correct?

And I also worry that if I install another bootloader like GAG choosing (0,0) as the default OS that it will just chainload into GRUB, solving nothing.

Is that true?

thanks! brian

---

### Post by Kateikyoushi on 2007-02-17
Grub should be in /boot you could get rid of unnecessary files and resize the partitions with gparted. Unfortunately if it does not work out and partitions get borked you have to netinstall windows or something.

---

### Post by louieb on 2007-02-17
If your using Ubuntu the GRUB configuration  files and programs are in /boot/grub.
Just look around there are a lot of post on how to alter the /boot/grub/menu.lst file to boot automatically  to windows.
Yes if you remove Ubuntu you will kill GRUB.
If its got a floppy drive you might try bootdisk.com and see if there is something there to restore the MBR so it boots straight to windows.
Its my understanding that to resize partitions on a drive, that the drive can't be mounted or active. So you need to boot to a CD or floppy in order to adjust the partitions on the hard drive.  I guess its time to check Ebay.

---

### Post by Kateikyoushi on 2007-02-17
I think resizing can be done from windows as well or not ?

---

