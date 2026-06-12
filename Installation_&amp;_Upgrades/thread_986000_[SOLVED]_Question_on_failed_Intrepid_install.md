---
title: "[SOLVED] Question on failed Intrepid install"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by greenshirt11 on 2008-11-18
I have a construction with the primary bootloader (from partition magic via Win2k) on /dev/sda3 .
That is referring to /dev/sda6 for booting kubuntu. This worked up to now for Feisty.

Doing an install from Kubuntu 8.10 LiveDVD, grub ended with an error:
   grub_installer: /dev/sda6 does not have any corresponding BIOS   drive

Booted from the LiveCD I see my Kubuntu 8.10 partitions as:
/dev/sda6 mounted on /target/boot
/dev/sda8 mounted on /target
/dev/sdb7 mounted on /target/usr
(/dev/sda7 used for swap)

The /target/boot contains the old kernels and the new one.
The /target/boot/grub contains the old(working) information.
The device.map has: 
   (hd0) /dev/hda
   (hd1) /dev/hdb

How would I proceed from this? I tried:
   sudo chroot /target /bin/bash
   sudo grub
   find /boot/grub/stage1
   root (X,Y)
   setup (X,Y)
  (With X=hda ? and Y= the partition # returned from the find)

The 'find' fails with: Error 15: file not found

Does anyone have an idea on how to proceeed with this? Ideally from the LiveDVD session I have still running?

Thanks in advance,
Folkert

---

### Post by caljohnsmith on 2008-11-18
In order to get a better idea of your setup, how about first posting the full output of:
```
sudo fdisk -lu
```

---

### Post by greenshirt11 on 2008-11-18
Sorry for not supplying more info at first but I posted from another computer previously. 
The output of sudo fdisk -lu:

[FONT="Courier New"]ubuntu@ubuntu:/target/boot/grub$ sudo fdisk -lu

Schijf /dev/sda: 80.0 GB, 80026361856 bytes
255 koppen, 63 sectoren/spoor, 9729 cilinders, totaal 156301488 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x2a40ace4

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1          208908    73947194    36869143+  17  Verborgen HPFS/NTFS
/dev/sda2        73947195   156296384    41174595    f  W95 Uitgeb. (LBA)
/dev/sda3   *          63      208844      104391    6  FAT16
/dev/sda5        73947258    78043769     2048256    b  W95 FAT32
/dev/sda6        78043833    78252614      104391   83  Linux
/dev/sda7        78252678    80308934     1028128+  82  Linux wisselgeheugen
/dev/sda8        80308998   156296384    37993693+  83  Linux

Partitietabel-items liggen niet in schijfvolgorde.

Schijf /dev/sdb: 120.0 GB, 120034123776 bytes
255 koppen, 63 sectoren/spoor, 14593 cilinders, totaal 234441648 sectoren
Eenheid = sectoren van 1 * 512 = 512 bytes
Schijf-ID: 0x19762147

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdb1   *       16065   234436544   117210240    f  W95 Uitgeb. (LBA)
/dev/sdb5           16128   122897249    61440561    7  HPFS/NTFS
/dev/sdb6       122897313   163862999    20482843+   b  W95 FAT32
/dev/sdb7       163863063   234436544    35286741   83  Linux
ubuntu@ubuntu:/target/boot/grub$
[/FONT]

I'm sorry but the language is Dutch.

Thanks,
Folkert

---

### Post by caljohnsmith on 2008-11-18
There's been some people in the forums who've had problems with installing Intrepid when there is a USB drive present; is sdb USB by chance? Their easy solution was to disconnect their USB drive while installing, but since you want to use one of the partitions sdb7 as /usr, that's obviously not an option for you. One thing you could do is choose not to have Grub installed during the installation process, and then if the installation is successful, you could install Grub afterwards. I'll be happy to help you install Grub afterwards if you would like, just let me know if you would like a hand. :)

---

### Post by greenshirt11 on 2008-11-18
Thanks for your help sofar.
I already unplugged my USB sticks/disks before installing. These are just two internal ATA disks.
My memory (that is becoming more eroded everyday) tells me that when Feisty was installed some years ago I had to do some manual Grub exercise to get everything working. Unfortunately my notes from that event disappeared; at least I can't find them.

As for your suggestion:
What would I have to do in order to install grub afterwards?
There is definitely no way to work with grub from the LiveDVD session?

Regards,
Folkert

---

### Post by caljohnsmith on 2008-11-18
> **greenshirt11 said:**
> 
As for your suggestion:
What would I have to do in order to install grub afterwards?
There is definitely no way to work with grub from the LiveDVD session?

Regards,
Folkert
Installing Grub afterwards takes several commands, and it will be slightly more complicated for you since you have a /boot partition. And you will have to install Grub manually from the Live DVD after the installer is done, if that is what you mean. See if you can install Kubuntu successfully without Grub, and then I can type out all the commands you need. Also please post one more thing:
```
sudo blkid
```
Let me know how it goes. :)

---

### Post by greenshirt11 on 2008-11-18
[FONT="Courier New"]ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="62B42C42B42C1B55" TYPE="ntfs"
/dev/sda3: SEC_TYPE="msdos" LABEL="BOOTMAGIC" UUID="4072-BA8F" TYPE="vfat"
/dev/sda5: LABEL="DATA" UUID="80BC-59CA" TYPE="vfat"
/dev/sda6: UUID="4d0662ce-7852-4902-b3d6-abead7e50faa" TYPE="ext3"
/dev/sda7: UUID="9e042901-2dd2-4d07-8ffe-012692b45586" TYPE="swap"
/dev/sda8: UUID="1e3d53cb-fae5-4049-a45f-d31116b7ce81" TYPE="ext3"
/dev/sdb5: UUID="4E80734B80733913" LABEL="video" TYPE="ntfs"
/dev/sdb6: LABEL="DATA" UUID="405E-2CE1" TYPE="vfat"
/dev/sdb7: UUID="7713c260-69b0-45c9-9fcc-7cb798cd3e3e" TYPE="ext3"
/dev/loop0: TYPE="squashfs"
[/FONT]

Ok, I will install without grub and come back on this.

---

### Post by greenshirt11 on 2008-11-18
> **caljohnsmith said:**
> Installing Grub afterwards takes several commands, and it will be slightly more complicated for you since you have a /boot partition. And you will have to install Grub manually from the Live DVD after the installer is done, if that is what you mean. See if you can install Kubuntu successfully without Grub, and then I can type out all the commands you need. Also please post one more thing:
```
sudo blkid
```
Let me know how it goes. :)

Ok, I reinstalled without installing GRUB.
Rebooted from the LiveDVD; where do I go from here?

Thanks in advance.

---

### Post by caljohnsmith on 2008-11-18
OK, from the terminal:
```
sudo mount /dev/sda6 /mnt
sudo mkdir /mnt/grub
sudo cp /usr/lib/grub/[COLOR="Blue"]i386-pc[/COLOR]/* /mnt/grub
```
Note if you are using 64-bit Kubuntu, for that last command instead use:
```
sudo cp /usr/lib/grub/[COLOR="Blue"]x86_64-pc[/COLOR]/* /mnt/grub
```
Next, download the attached "menu.lst.txt" to your Desktop, and do:
```
sudo mv ~/Desktop/menu.lst.txt /mnt/grub/menu.lst
```
And finish with installing Grub to the boot sector of sda6:
Then continue with:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0,5)
grub> quit
```
And hopefully all that should work. Let me know how it goes or if you run into problems. :)

---

### Post by greenshirt11 on 2008-11-18
Replaced the UUID for /dev/sda6 in menu.lst as blkid now gives other result.

Mounted on /target/boot gives:
```
ubuntu@ubuntu:~$ ls -l /target/boot
totaal 11933
-rw-r--r-- 1 root root  507665 2008-10-24 08:29 abi-2.6.27-7-generic
-rw-r--r-- 1 root root   91364 2008-10-24 08:29 config-2.6.27-7-generic
drwxr-xr-x 2 root root    1024 2008-11-18 19:48 grub
-rw-r--r-- 1 root root 8149680 2008-11-18 18:24 initrd.img-2.6.27-7-generic
drwx------ 2 root root   12288 2008-11-18 17:58 lost+found
-rw-r--r-- 1 root root  124152 2008-09-11 20:11 memtest86+.bin
-rw-r--r-- 1 root root 1029585 2008-10-24 08:29 System.map-2.6.27-7-generic
-rw-r--r-- 1 root root    1073 2008-10-24 08:31 vmcoreinfo-2.6.27-7-generic
-rw-r--r-- 1 root root 2244272 2008-10-24 08:29 vmlinuz-2.6.27-7-generic
ubuntu@ubuntu:~$ ls -l /target/boot/grub
totaal 299
-rw-r--r-- 1 root   root     8108 2008-11-18 19:39 e2fs_stage1_5
-rw-r--r-- 1 root   root     7856 2008-11-18 19:39 fat_stage1_5
-rw-r--r-- 1 root   root     8712 2008-11-18 19:39 jfs_stage1_5
-rw-r--r-- 1 ubuntu ubuntu   4291 2008-11-18 19:47 menu.lst
-rw-r--r-- 1 root   root     7352 2008-11-18 19:39 minix_stage1_5
-rw-r--r-- 1 root   root     9756 2008-11-18 19:39 reiserfs_stage1_5
-rw-r--r-- 1 root   root      512 2008-11-18 19:39 stage1
-rw-r--r-- 1 root   root   121460 2008-11-18 19:39 stage2
-rw-r--r-- 1 root   root   121460 2008-11-18 19:39 stage2_eltorito
-rw-r--r-- 1 root   root     9556 2008-11-18 19:39 xfs_stage1_5

```

Now I will reboot and see what happens.
...

---

### Post by greenshirt11 on 2008-11-18
... and it works :)

Even better; the sessions from my Feisty account are restored when I login.
So big thanks for your help; how can I upgrade your Thanks count?

Now up to get my wireless connection working.

---

### Post by caljohnsmith on 2008-11-18
> **greenshirt11 said:**
> ... and it works :)

Even better; the sessions from my Feisty account are restored when I login.
So big thanks for your help; how can I upgrade your Thanks count?

Now up to get my wireless connection working.
That's great news, glad you have it working. If you have the time, I think it would be good to file a bug at bugs.launchpad.net to let them know about the error you got during installation. And about the "thanks" count, you can just press the little "red and gold medal" icon in the lower right corner of any message you want to thank. Cheers and have fun with your new Kubuntu install. :)

---

