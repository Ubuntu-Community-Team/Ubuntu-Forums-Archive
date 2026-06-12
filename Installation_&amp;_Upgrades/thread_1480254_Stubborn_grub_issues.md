---
title: "Stubborn grub issues"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by StevenSheridan on 2010-05-11
**Update: I gave up and just got rid of XP. This made room for Ubuntu on the SSD, so the problem's solved.**

I am trying to install Grub (at this point I don't care whether it's Legacy and Grub2) to a SSD that has room only for XP. For now, I only want to boot XP. I'll try to get Ubuntu back later, but first I need a working computer again.

I got into this problem by trying to dual-boot XP and Ubuntu on separate drives--XP on the SSD, Ubuntu on an SD card drive. Unfortunately, the SD card drive is not recognized until some OS boots, so when I try to boot, Grub2 says:
```
error: no such device: 9d56f73c-3038-4495-867c-42362e8bdbae.
grub rescue>
```I have tried, and failed, to learn how to manually choose to boot only XP in grub2 (removing the 10_linux file doesn't help). If you can help me out here, that might work, but I feel like there's something deeper that's confusing my computer. Here's why:

I tried to install Grub Legacy:
```
sudo aptitude purge grub2 grub-pc
sudo aptitude install grub
sudo update-grub
sudo grub-install /dev/sda
```When I enter that last line, it says "Could not find device for /boot: Not found or not a block device."

I Googled this error message, and following a couple people's advice, did
```
sudo grub
grub> find /boot/grub/stage1

Error 15: File not found

grub> root (hd0,1)
grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... no

Error 15: File not found
```Every time I try a different approach to install Grub Legacy or Grub2, I get, at some point or another, a message saying that something isn't found.

I'll expound below upon a few other approaches I've tried to see if it rings any bells.

---

### Post by dino99 on 2010-05-11
your config is quite special and i've no experience with this kind of hardware.

note: grub2 (lucid) dont like grub-legacy (issues)

need to googled around: ssd+ubuntu, ssd+lucid, "sd card"+linux, ...

---

### Post by StevenSheridan on 2010-05-11
I'm really just trying to get away from the SD card. Is the SSD really going to make things different from a hard disk?

Anyway... in case this gives any one any further hints, here are a few more things I tried:

I tried reinstalling grub2 from a LiveUSB, as described [here.]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")  I think I did it right, but I'm not sure.

Remember:
```
>sudo grub-install /dev/sda
Could not find device for /boot: Not found or not a block device
```

The LiveUSB is mounted on /cdrom, so I tried
```
>sudo grub-install --root-directory=/cdrom/ /dev/sda
mkdir: cannot create directory '/cdrom//boot': Read-only file  system
```

The SD card drive is /dev/mmcblk0; Ubuntu's partion is /dev/mmcblk0p5;  this partition is mounted on  /media/9d56f73c......................................8bdbae.
```
>sudo grub-install  --root-directory=/media/9d56f73c......................................8bdbae/  /dev/sda
Probing devices to guess BIOS drives. This may take a long time.
/dev/mmcblk0p5 does not have any corresponding BIOS drive
```


Next, after purging Grub Legacy, I tried a fresh install of Grub2
```
sudo apt-get install grub-pc
```
This downloaded some stuff, gave me a blue "configuring package" screen and an option to enter a "Linux command line." I left it blank and moved on. I had a choice of which drives to run the grub-installer for. Last time, I chose sda, sda1, and sda2; this time, I just chose sda2 (a 100mb partition which I was thinking of turning into a boot partition). Both times, it said it failed. I ran what would have been the next step:
```
> sudo update-grub
  /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).
```

How would I mount /dev?

---

### Post by oldfred on 2010-05-11
Grub cannot boot without extra files. If you want to use grub to boot sda you will have to create a grub (only) partition for either grub legacy or grub2.

Herman on separate grub partition - He has both grub & grub2 on his site:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)
Grub partition slakkie
[http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/](http://blog.opperschaap.net/2009/11/13/all-your-grub-are-belong-to-us/)
grub2 partition
[http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/](http://rxezlqu.wordpress.com/2010/04/07/separate-boot-partition-vs-dedicated-boot-partition/)
Grub2 partition discussion:
[http://ubuntuforums.org/showthread.php?t=1465772](http://ubuntuforums.org/showthread.php?t=1465772)

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

ASUS EeePC netbook PC 10.04 install - SSD info
[http://members.iinet.net/~herman546/p28.html](http://members.iinet.net/~herman546/p28.html)

---

### Post by StevenSheridan on 2010-05-11
I'm going to try to wipe XP and replace it with a clean Ubuntu boot,  but I'm not sure that'll fix my problem--and I don't want to go ahead  with this if it'll still be screwed up.

---

### Post by oldfred on 2010-05-11
I am not familiar with this but it uses a version of grub:

wingrub - The main function of GRUB is placed in a single file grldr
[http://grub4dos.sourceforge.net/wiki/index.php/Main_Page](http://grub4dos.sourceforge.net/wiki/index.php/Main_Page)

---

### Post by StevenSheridan on 2010-05-11
Gave up. I just got rid of XP. Now that Ubuntu and grub are on the same drive, everything's fine.

---

