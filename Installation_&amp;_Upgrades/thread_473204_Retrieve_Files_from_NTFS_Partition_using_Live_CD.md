---
title: "Retrieve Files from NTFS Partition using Live CD"
date: 2007-06-13
forum: Installation &amp; Upgrades
---

### Post by textguru on 2007-06-13
I have Windows 2000 Disk and I wanted to restore the content using a live cd of Ubuntu. I have tried it but it seems that I cannot access the partition due to no permission assigned to ubuntu. Is there a way that I can restore it using the live cd?

---

### Post by confused57 on 2007-06-13
I'm not sure what you're wanting to do, but maybe something here will help:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

see the mounting section and the restore & backup section.

---

### Post by textguru on 2007-06-13
cant follow your guide. here is the scenario:

I have booted to Ubuntu 6.06 live cd. From the Desktop, l click on System > Administration > Disks. From the Disk Manager, I click on the Hard Disk that I wanted to backup click on Partitions tab. From that, the access path of my disk s on **/tmp/disks-conf-sda1**  and the Status is set to Accessible but I cannot access the disk. Is there a way to access the content of the disk?

Btw, the partition is NTFS. I am planning to copy the content to a USB thumb drive, hope you might help.

---

### Post by confused57 on 2007-06-14
Open a terminal in the live cd, then mount your sda1:
```
sudo mkdir /media/windows
sudo mount /dev/sda1 /media/windows -t ntfs -o nls=utf8,umask=0222
```

Now navigate to Disks, and change the mountpoint to /media/windows...then you should be able to browse your sda1.

```
sudo umount /media/windows
```
unmounts your sda1

---

### Post by textguru on 2007-06-14
there is error on the mount command:

mount: wrong fs type, bad option, bad superblock on /dev/sda1, missing codepage or other error ...

I just copy your command

---

### Post by confused57 on 2007-06-14
From the live cd, post the output of:
```
sudo fdisk -l
```
the -l is a lowercase "L"

---

