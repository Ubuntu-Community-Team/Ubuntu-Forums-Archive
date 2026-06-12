---
title: "Ubuntu on second hard drive"
date: 2011-08-07
forum: Installation &amp; Upgrades
---

### Post by karmic-koala on 2011-08-07
I recently bought a Dell XPS17 laptop. It came with Windows 7 pre-installed on the first hard drive. Second hard drive, I installed Ubuntu on it. After installation, just before install process ends I got a message saying GRUB failed to install or something on those lines. When I boot my laptop, I don't see no Ubuntu only Windows 7.

I tried the GRUB recovery guide at
[http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)

But every time I try setup(hd0) the command fails with the following error:

Error 17: Cannot mount selected partition

Any help appreciated :)


Here's what my fdisk -l looks like



ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x07f2837e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          13      104391   de  Dell Utility
Partition 1 does not start on physical sector boundary.
/dev/sda2   *          14        2563    20480000    7  HPFS/NTFS
/dev/sda3            2563       60802   467799064    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x521e459d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60802   488384513    5  Extended
Partition 1 does not start on physical sector boundary.
/dev/sdb5           60677       60802      999424   82  Linux swap / Solaris
/dev/sdb6               1       60677   487385088   83  Linux

Partition table entries are not in disk order

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc72e530f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1      121601   976760001    7  HPFS/NTFS

---

### Post by oldfred on 2011-08-07
What version of Ubuntu. Unless you have 9.04 or before or up graded from the old verisons, you now have grub2, but are following the instructions for grub legacy (0.97).

If you did get grub legacy installed  it may conflict but I would just first try installing grub2 to the MBR.

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sdb6 and want grub2's bootloader in drive sdb's MBR:
#Find linux partition, change sdb6 if not correct:
sudo fdisk -l
#confirm that linux is sdb6
sudo mount /dev/sdb6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sdb
#If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sdb
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sdb
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
#How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
#Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by karmic-koala on 2011-08-07
Hello and thanks for responding.

All but last command failed, should I be worried? I guess I'll find out after I restart :P Here's the output

ubuntu@ubuntu:~$ sudo mount /dev/sdb6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sdb
Installation finished. No error reported.
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot stat `aufs'.
ubuntu@ubuntu:~$ 

Update:  After restarting and changing boot load order from CD,HDA1,HDA2 to HDA2,HDA1,CD I get the GRUB prompt
and with HDA1 set to load first I go straight into Windows 7

---

### Post by oldfred on 2011-08-07
You have to reboot into your (hopefully) working system before you can run the update-grub command.

---

### Post by karmic-koala on 2011-08-07
I tried rebooting but it kept going into GRUB prompt. After a while I gave up and shrunk my NTFS partition on disk 1 and installed Ubuntu on the same disk as Windows with no problems.

Lesson learnt, if installing Ubuntu on a disk other than the primary one that's got Windows on do your homework and be prepared to do some debugging on the GRUB prompt.

---

