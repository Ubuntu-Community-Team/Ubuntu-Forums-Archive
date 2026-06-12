---
title: "grub does not boot after install on other sata drive"
date: 2008-04-03
forum: Installation &amp; Upgrades
---

### Post by fboecom on 2008-04-03
This is not only a post with a problem but also with a solution attached.
I chose the subject based on what I was searching for when trying to fix what I see as a ridiculous behaviour of grub.
In the 'similar' topics of this forum there is not a comprehensive overview of my situation.

I have a very well running dual boot Win98/XP system, but wanted to add the sympa Ubuntu as a third OS.
My config is 3xIDE CD/DVD and 4x SATA. 
Of course I boot from what I selected in the BIOS as the first Sata; the ntloader is on the first partition (C: drive) but my regular XP installation is at E:, the second partition on what windows sees as 'Disk 2'. No worries, this (and its installation) works very well. Thank you Bill.

I expected a flawless installation of Ubuntu from the LiveCD. I chose my 4th Sata drive for the ‘/’ and ‘/home’ partitions, since it had enough space.
Installation went OK (I checked advanced and had grub install at (hd0), until, what a surprise, when I rebooted, the good old Window boot menu came up.
I rebooted from the Ubuntu live CD and selected 'boot from first hard drive' but that had no effect either.

Since I was not directly going to give up on the sympa Ubuntu, I started digging and digging.
In fact the solution was quite simple when I had known 2 things:
1. after install of ubuntu on another disk than the windows boot disk, I have to change the boot order of my disks in the BIOS so the Ubuntu disk comes first
2. Grub plays a cat and mouse play with me by changing the (hdx) numbers during and after boot.

To document more fully, here is my complete install process described. Of course change numbers to match your system and check other posts to understand the full options available in some of my subjects.
I know there are some other solutions to this, but my described process works fine and is not complex despite the 13 bullet points.

1. I have Windows 98 and XP installed on (sata) disk 2, on the first and second partition, no worries, this is my 1st boot disk in BIOS that works fine every day.
2. Reboot& hit DEL for the BIOS - make the CD player as my first boot device in Bios and reboot with the Ubuntu LiveCD in the CD drive- checked the CD and (re)start Ubuntu from it.
3. There came up issues what is on what partition when installing. The good thing is Windows Computer Managment and Ubuntu install use the same order of disks, that is: disk0 becomes /dev/sda, disk1 /dev/sdb etc. So I am prepared and know my disk layout before installing and where to let the Ubuntu install and formats go.
Further: I do not make a mistake to open&explore one of my disks recognized by the LiveCD of Ubuntu, before double clicking the install on Ubuntu: it will not be able to install on a disk if that is opened / mounted.
4. Now I install Ubuntu with Manual partition; I see (that is: already know) my Windows 98 and XP are in partitions device /dev/sdc 1 and 2(displayed in the partition manager as /media/sdcx, where x=a number)
5. Since I know my drive's partition layouts I select the two partitions on drive3 (/media/sdd1 and /media/sdd2) and mount/format 20Gb as / and mount 5Gb as /home; further a swap partition somewhere on another disk.
6. Now Next Next and install - that goes fine.
7. Reboot and hit Del for the BIOS, now make my Ubuntu installed disk (hopefully I don't have 4 completely the same disks, so I know which one to put first) the first boot disk and make windows disk the second if I like.
8. Reboot again and wow! there comes grub. Now if I would continue and select Ubuntu it would fail since it cannot find the partition to boot from.
9. Instead, I move the cursor to the upper line and press 'e' on the keyboard. Now I see that grub thinks the boot is on root (hd3,0). Press again 'e' amd change that into root (hd0,0) and press b - the system will boot into Ubuntu.
10. Once in Ubuntu, open a terminal window and enter *sudo /boot/grub/menu.lst*. Scrolling down I see that there is still root (hd3,0) as the Ubuntu boot partition. Change that into *root (hd0,0)*.
11. I also see my windows partition is having the wrong settings. It says it is in hd2 (that was true when installing) now it has to be hd1 and I also have to change the 'hd2' values into 'hd1' values in the map statements.
12. Save and close. In order to see what grub now thinks about its settings, I enter: *sudo grub* once in grub I enter *find /boot/grub/stage1 *and grub will reply to me *root(hd3,0)*. So: proof: grub changes its drives when booting into other values after booting. Great.
13. Reboot and I select any of my 3 OSes - they all boot.

They beauty of this setup is that when I change the boot order of my drives in BIOS to let the Windows disk be again the frist boot disk; I am not even bothered by Grub at boot time.

I am really really puzzled why this boot behaviour of Grub is not documented more clearly.

Some copies of my drives from the
*sudo fdisk -l* (sorry for the Dutch text):

Schijf /dev/sda: 250.0 GB, 250059350016 bytes
255 koppen, 63 sectoren/spoor, 30401 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x6de57c88

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1       15804   126945598+   7  HPFS/NTFS
/dev/sda2           15805       30401   117250402+   7  HPFS/NTFS

Schijf /dev/sdb: 160.0 GB, 160041885696 bytes
255 koppen, 63 sectoren/spoor, 19457 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x8ebb7c0a

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1               1        9539    76621986    7  HPFS/NTFS
/dev/sdb2            9540       19457    79666335    f  W95 Uitgeb. (LBA)
/dev/sdb5            9540       19457    79666303+   7  HPFS/NTFS

Schijf /dev/sdc: 37.0 GB, 37019566080 bytes
255 koppen, 63 sectoren/spoor, 4500 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x81088108

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdc1   *           1         984     7903948+   b  W95 FAT32
/dev/sdc2             985        3530    20450713+   7  HPFS/NTFS
/dev/sdc3            3531        4500     7791525   82  Linux wisselgeheugen

Schijf /dev/sdd: 122.9 GB, 122942324736 bytes
255 koppen, 63 sectoren/spoor, 14946 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
Schijf-ID: 0x4f004eff

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdd1               1        2432    19535008+  83  Linux
/dev/sdd2            2433        3069     5116702+   6  FAT16
/dev/sdd3            3070       14946    95402002+   f  W95 Uitgeb. (LBA)
/dev/sdd5            3070       14946    95401971    7  HPFS/NTFS

the grub /boot/grub/menu.lst section for normal Ubuntu boot says:
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=b4495a62-c0a8-4089-8512-8108283cff05 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet


but once in grub, it reports:
grub> geometry (hd0)
drive 0x80: C/H/S = 30401/255/63, The number of sectors = 488397168, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x7

grub> geometry (hd1)
drive 0x81: C/H/S = 19457/255/63, The number of sectors = 312581808, /dev/sdb
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7

grub> geometry (hd2)
drive 0x82: C/H/S = 4500/255/63, The number of sectors = 72303840, /dev/sdc
   Partition num: 0,  Filesystem type is fat, partition type 0xb
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 2,  Filesystem type unknown, partition type 0x82

grub> geometry (hd3)
drive 0x83: C/H/S = 14946/255/63, The number of sectors = 240121728, /dev/sdd
   Partition num: 0,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 1,  Filesystem type unknown, partition type 0x6
   Partition num: 4,  Filesystem type unknown, partition type 0x7


Good luck y'all with installing and juggling with your disks.
Freek

---

