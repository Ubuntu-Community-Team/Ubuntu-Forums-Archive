---
title: "&quot;Operating system not found&quot;"
date: 2007-11-03
forum: Installation &amp; Upgrades
---

### Post by kristjans on 2007-11-03
There is only one, new 20 GB  hard drive in the computer, which is set as secondary master. Installed Ubuntu 5.10 and later Kubuntu 7.10 sucessfully, but on boot to hard drive (From boot menu, which opens up on F8) it gives "Operating System Not Found".

Tried some other suggestions offered in the forum:
> [17:57] <Zaborg> GNU GRUB version 0.95 (640K lower / 3072K upper memory) 
 [17:57] <Zaborg> [ Minimal BASH-like line editing is supported. For the first word, TAB 
 [17:57] <Zaborg> lists possible command completions. Anywhere else TAB lists the possible 
 [17:57] <Zaborg> completions of a device/filename. ] 
 [17:57] <Zaborg> grub> 
 [17:57] <Zaborg> grub> find /boot/grub/stage1 
 [17:57] <Zaborg> (hd0,0) 
 [17:57] <Zaborg> grub> 
 [17:58] <Zaborg> grub> root (hd0,0) 
 [17:58] <Zaborg> Filesystem type is ext2fs, partition type 0x83 
 [17:58] <Zaborg> grub> 
 [17:58] <Zaborg> grub> setup (hd0) 
 [17:58] <Zaborg> Checking if "/boot/grub/stage1" exists... yes 
 [17:58] <Zaborg> Checking if "/boot/grub/stage2" exists... yes 
 [17:58] <Zaborg> Checking if "/boot/grub/e2fs_stage1_5" exists... yes 
 [17:58] <Zaborg> Running "embed /boot/grub/e2fs_stage1_5 (hd0)"... 17 sectors are embedded. 
 [17:58] <Zaborg> succeeded 
 [17:58] <Zaborg> Running "install /boot/grub/stage1 (hd0) (hd0)1+17 p (hd0,0)/boot/grub/stage2 
 [17:58] <Zaborg> /boot/grub/menu.lst"... succeeded 
 [17:58] <Zaborg> Done. 
 [17:58] <Zaborg> grub> 
 [17:58] <Zaborg> ubuntu@jannu-uriiniaut:~$ sudo grub 
 [17:58] <Zaborg> Probing devices to guess BIOS drives. This may take a long time. 
 [17:58] <Zaborg> ubuntu@jannu-uriiniaut:~$

> [18:39] <Zaborg> ubuntu@jannu-uriiniaut:~$ sudo fdisk -l 
 [18:39] <Zaborg> Disk /dev/hdc: 20.5 GB, 20576747520 bytes 
 [18:39] <Zaborg> 255 heads, 63 sectors/track, 2501 cylinders 
 [18:39] <Zaborg> Units = cylinders of 16065 * 512 = 8225280 bytes 
 [18:39] <Zaborg> Device Boot Start End Blocks Id System 
 [18:39] <Zaborg> /dev/hdc1 * 1 2409 19350261 83 Linux 
 [18:39] <Zaborg> /dev/hdc2 2410 2501 738990 5 Extended 
 [18:39] <Zaborg> /dev/hdc5 2410 2501 738958+ 82 Linux swap / Solaris 
 [18:39] <Zaborg> ubuntu@jannu-uriiniaut:~$

Neither solved the problem.

---

### Post by Jose Catre-Vandis on 2007-11-03
Put it on the primary IDE

[edit] sorry, that's a bit terse (it's late here). why have the hard drive on the second IDE? It's only going to give you problems like the one you have.

---

### Post by kristjans on 2007-11-04
The hard drive is second IDE, because the IDE-cable won't reach the primary IDE slot on the motherboard. It would reach only the hard drive, but not the CD-ROM device. He tried to change it to primary before, but then nothing happened. I suppose the GRUB settings would have to be changed using the live CD? Well, thanks for your reply, and I guess it's time to do some shopping now.

---

### Post by Jose Catre-Vandis on 2007-11-04
Shame, I have a bagful of IDE cables here :)

---

### Post by kristjans on 2007-11-04
Looks like he actually found another IDE-cable. Hopefully it will work out. He really had a distorted idea of what Ubuntu is. He thought that the only things you can do on it are using Firefox and chatting on some messenger, and that it was not capable of running *any* games.

Once he is proven false, I hope to explain him that huge web sites are not created in webpagemaker. :)

---

