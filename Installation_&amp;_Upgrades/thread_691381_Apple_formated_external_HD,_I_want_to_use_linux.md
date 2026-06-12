---
title: "Apple formated external HD, I want to use linux"
date: 2008-02-08
forum: Installation &amp; Upgrades
---

### Post by Cyfr on 2008-02-08
I have a 1TB external HD with quite a lot of stuff on. Its LaCie one and formated in hf+ journaled or whatever its called. 

I want to use linux and store the majority of my large files on the external HD. I wish to keep all the stuff I already have, is this possible?

ps. I'm doing it from a macbook so the harddrive isnt big to copy things over to, and at University I only have my macbook with me so can't copy it anywhere else..

---

### Post by Rocket2DMn on 2008-02-08
If the drive doesn't automount when you plug it in, you can mount it with something like this:
```
sudo mount -t hfsplus /dev/sdb1 /media/usbdisk
```
The first time you will have to make the directory before mounting with
```
sudo mkdir /media/usbdisk
```
Of course, substitute the correct device for sdb1 (see "sudo fdisk -l").

---

