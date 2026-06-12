---
title: "Ubuntu Dapper drive transplant woes"
date: 2007-09-08
forum: Installation &amp; Upgrades
---

### Post by tristan on 2007-09-08
I recently decided to upgrade my ageing ASUS / P4 / 7600GT system dual booting Ubuntu 6.06 and Win XP on different IDE drives.
 
I put together a system with an ASUS / Core2 Duo / 8600GT, with a 320Gb SATA drive. I installed windows to this drive (for games mainly) and the system runs beautifully. My intention was to install the 160Gb IDE drive containing Ubuntu into the system and thus be able to dual boot in a similar manner to my previous system. Sounds reasonable?

Well I did just that and the system boots to the grub screen no problems. I can select and boot XP without a hitch. If I try to load ubuntu then the system hangs up at "waiting for root filesystem", eventually dropping back to a shell.

If I boot in recovery mode then I get no further, it just says that it can't find dev/hda2. 

If I try booting from a 386 kernel - same deal.

I also have GEEXBOX intalled on this drive and it will boot without a hitch, which made me think that the problem was ubuntu specific. And in fact I can't even boot the Ubuntu 6.06 install CD. Nor a Xubuntu 6.10 CD, nor a Ubuntu 7.04 CD.

Has anyone else experienced such a problem? Are there ways around it. For the time being I'm stuck using windows, using YAREG to copy over files from my reiserfs ubuntu disk.

Thanks in advance!

---

### Post by Pumalite on 2007-09-08
Try Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
See if you can re-install Grub
If not, try this: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Your main problem here is mix of SATA and IDE
You could post: sudo fdisk -lu... and cat /boot/grub/menu.lst to give us a better idea of what's going on.

---

### Post by tristan on 2007-09-08
Hi Pumalite, thanks for the quick reply.

I treid out supergrub - very nice system but it didn't help.

I think the problem is ubuntu specific, not sata/ide related, as geexbox linux boots fine.

When the system fails to boot and drops to a shell I don't actually have fdisk so I can't see what the system is labelling the disks.

Thanks again, I'll just keep trying.

---

### Post by Pumalite on 2007-09-08
What about geexbox?. Cannot give you an fdisk or menu.lst mounting appropriate partition?

---

