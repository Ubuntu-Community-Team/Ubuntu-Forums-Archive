---
title: "yet another grub 22 error thread"
date: 2008-10-07
forum: Installation &amp; Upgrades
---

### Post by jijin on 2008-10-07
Ok here is the thing, In recently did a complete wipe of my HDD and installed ubuntu formatting the whole drive.

However, when I reboot I get error 22. I had at one time Vista installed on this but I installed ubuntu over the whole drive, so it shouldn't even have installed grub.

please help

I have tried doing

```
sudo grub
find /boot/grub/stage1
```

But I get in return:

```
Error 15: File not found
```

thanks

---

### Post by WWSmith36 on 2008-10-07
Check to see whats in your /boot/grub/ directory.  I have a feeling its empty, if it can´t find stage1.

If this is the case, let me know.  You will have to mount the hard drive, change root, install grub, and update grub to get a menu.lst generated.

---

### Post by jijin on 2008-10-08
```
ubuntu@ubuntu:/boot$ cd grub
bash: cd: grub: No such file or directory
```

:/

EDIT:

I realize now that that is only the live CD install. In the HDD under places there is no folder "/boot/grub" either

---

### Post by WWSmith36 on 2008-10-08
You are in the LiveCD file system not your installed ubuntu file system.

Please provide output of 

```
sudo fdisk -l
```

for better help.

---

### Post by jijin on 2008-10-08
```
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95744b99

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

```

---

### Post by WWSmith36 on 2008-10-08
From the LiveCD mount your hard drive and change root

```
sudo mkdir /mnt/root
mount -t ext3 /dev/sda1 /mnt/root
sudo mount -t proc none /mnt/root/proc
sudo mount -o bind /dev /mnt/root/dev
sudo chroot /mnt/root bin/bash
```

The command prompt should now look like this

root@ubuntu:/#

Now reinstall and update grub (make sure you regenerate menu.lst)

sudo grub-install /dev/sda1
sudo update-grub
ls /boot/grub

This will provide you with a grub folder with all the required files including regenerating menu.lst file.

---

### Post by jijin on 2008-10-08
Ok I'm not sure if the commands you give below "Now reinstall and update grub (make sure you regenerate menu.lst)" do that but not aptitude is no longer working either.

Note: It might say unable to resolve ubuntu, but my internet is working. I am posting this from the live CD.

```
root@ubuntu:/# sudo grub-install /dev/sda1
sudo: unable to resolve host ubuntu
sudo: grub-install: command not found
root@ubuntu:/# sudo apt-get remove grub
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

I can and don't mind reinstalling from scratch, but I want to make sure I don't have the same issue all over again.

EDIT: I'm going to reinstall it from scratch

---

### Post by amgalitz on 2008-10-08
Pardon me if you already checked this, but I fixed a Grub error 22 by correcting my drive cabling. My Sata drive motherboard sockets were populated (clue was from from start up bios report):
[INDENT]Sata1: empty
Sata2: empty
Sata3: master 1
Sata4: master 2[/INDENT]

Grub was happy after this:
[INDENT]Sata1: master 1
Sata2: master 2
Sata3: empty
Sata4: empty[/INDENT]

When I first built the system I did not think it mattered to plug the cables in strict order (or my old eyes misread the small print). Apparently, the later versions of Ubuntu are picky at load about cabling. This can happen from plugging the IDE in reversed (drive header into motherboard socket) also. The install CDROM worked fine, as did XP, but not the Grub loader from the actual installation. Even with the first two Motherboard Sata sockets empty, the CDROM Kubuntu numbered them sda and sdb.

Hope this helps, cheers

"We sleep soundly in our beds because rough men stand ready in the night to visit violence on those who would do us harm." - Winston Churchill

---

### Post by WWSmith36 on 2008-10-08
This might be a problem with the CD you are using. Here is some general tips regarding the CD

Download the standard Ubuntu 8.04.1 32 bits iso image, torrent is recommended
[http://releases.ubuntu.com/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso](http://releases.ubuntu.com/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso)
[http://releases.ubuntu.com/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso.torrent](http://releases.ubuntu.com/releases/8.04.1/ubuntu-8.04.1-desktop-i386.iso.torrent)

Check the md5sum of your downloaded Ubuntu .iso image file [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
and compare with [http://releases.ubuntu.com/8.04.1/MD5SUMS](http://releases.ubuntu.com/8.04.1/MD5SUMS)

Burn it on a CD rom with low speed 4X and then check the md5sum of the burnt CD

Try to perform the "Memory test" and the "Check CD for defects" to be sure the CD is read without errors by the destination PC CD rom driver

Then reinstall your Ubuntu

Hope this helps

---

