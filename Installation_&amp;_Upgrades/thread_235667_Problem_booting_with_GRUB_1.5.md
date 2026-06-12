---
title: "Problem booting with GRUB 1.5"
date: 2006-08-13
forum: Installation &amp; Upgrades
---

### Post by oggna on 2006-08-13
This is not specific to Ubuntu. Sorry for the wall of text in advance. Okay, so I have a Sony VAIO RC-210G. It came with Windows Media Center 2005 installed. It came with two 160GB HDs which appeard as one 320GB HD in Windows. I figure it was using some sort of software RAID cause when I boot the Ubuntu 6.06.1 Live CD I can see them as two separate drives. Anyways, first install I removed all the partitions (one NTFS partition) on the first drive (sda) and created one 154GB ext3 partition (sda1) and one 6GB Linux sawp partition (sda5). Ubuntu installs okay, no errors or anything. I mount sda1 to make sure it looks okay, and everything is there. I remove the CD and reboot. GRUB throws error 17 (unrecognized filesystem). I boot the Live CD again and also erase the NTFS partition off the second hard drive (sdb) and reinstall Ubuntu on sda. I reboot again and this time it sits at "GRUB loading, please wait...". I would really appriciate any ideas you may have on what may be going on. Thanks.

---

### Post by zxee on 2006-08-13
Boot from the live cd try 'sudo grub-install' from the terminal. You will likely need to include the drive notation so this, hopefully, will work.
> sudo grub-install hd0 Note 'hd0' isn't a mistake the grub commandline only recognizes 'hd' when listing drives-even sata drives.
If that doesn't work post the errors/messages that you get.

---

### Post by oggna on 2006-08-13
ubuntu@ubuntu:~$ sudo grub-install hd0
Could not find device for /boot: Not found or not a block device.

Also I guess the Vaio has some sort of integrated RAID controller. From `lspci`:
0000:00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=RAID (rev 01)

---

### Post by zxee on 2006-08-13
> **oggna said:**
> ubuntu@ubuntu:~$ sudo grub-install hd0
Could not find device for /boot: Not found or not a block device.

Also I guess the Vaio has some sort of integrated RAID controller. From `lspci`:
0000:00:1f.2 RAID bus controller: Intel Corporation 82801GR/GH (ICH7 Family) Serial ATA Storage Controllers cc=RAID (rev 01)

Ok, Use the live cd and mount the partition your ubuntu install is on.
You can do sudo fdisk -l to see your partions/drives.

First create a directory to mount to.> sudo mkdir /mnt/sdaX
Instead of X use the actual # of the partition

the mount command is > sudo mount /dev/sdaX /mnt/sdaX
Note: where I've put X's use the actual # of the partition.

Now > sudo chroot /mnt/sdaX
from the chroot environment do > grub
at the grub prompt which looks like this grub>
do > find /boot/grub/stage1
The previous command should provide output and it should be the partition in grub notation of your install.
If you get that then do > setup hdX Hope that helps.

---

### Post by oggna on 2006-08-14
> 
grub> find /boot/grub/stage1
Error 15: File not found
grub> setup (hd0)
Error 12: Invalid device requested


My device.map:
> 
(hd0)   /dev/sda
(hd1)   /dev/sdb
(hd2)   /dev/sdc
(hd3)   /dev/sdd


---

### Post by zxee on 2006-08-14
If the find command doesn't find a stage1 then it seems that grub wasn't correctly installed.
You will need to install grub from the live cd or the chroot environment.
grub-install hd0
grub can be difficult at times so hang in there.
Perhaps this tutorial could help? [http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/9398-solving-boot-problems-grub-2nd-edition.html)

---

### Post by oggna on 2006-08-14
I will give that a try when I get home tonight. Thanks alot for your help so far.

---

