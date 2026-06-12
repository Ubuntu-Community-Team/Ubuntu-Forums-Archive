---
title: "How to bring back the OLD grubMBR after Reinstalling XP"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by gurugeek on 2006-08-26
I want to reinstall my windows XP but I think it will overwrite my MBR.

How can I recover my old MBR (GRUB) after reinstalling Windows XP?

Can I do it without the UBUNTU cd?

---

### Post by Herman on 2006-08-26
The following code, when entered after a terminal prompt, will back up the first 446 bytes of your partition table, which currently contians your IPL for the Grub  bootloader.
```
sudo dd if=/dev/hda of=/home/ubuntu/OLDMBR.img bs=446 count=1
``` 
The following code will restore it again,```
sudo dd if=/home/ubuntu/OLDMBR.img of=/dev/hda bs=446 count=1
``` All you will need maybe is a Grub CD or floppy disk to boot Ubuntu with before you will be able to use the restore command.
A good one is 'Super Grub Disk', it's free and only a little more than 500Kb download. [Super Grub Disk]("http://adrian15.raulete.net/grub/tiki-index.php")

Regards, Herman :D

EDIT: If you have a SCSI or Sata disk, replace 'hda' with 'sda in the above codes.
And, actually, (by the way) Super Grub Disk can easily restore Grub to MBR for you too, without you needing to type any codes. :D

---

