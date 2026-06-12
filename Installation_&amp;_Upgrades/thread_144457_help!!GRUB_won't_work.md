---
title: "help!!GRUB won't work"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by emmaclose on 2006-03-14
i've just tried to install Kubuntu but when i start up i get 

GRUB loading please wait....
error 21

then nothing. i've set it up with a partition to keep XP. what's going on! can i uninstall it?

em

---

### Post by otake-tux on 2006-03-14
get a live cd, like knnopix or the ubuntu-livecd.  Boot from that.

once you are in the live cd youll be able to mount your partitions.  Mount the partition with linux installed.

example: say your linux partion is hda1, type in a terminal:
```
sudo mount /dev/hda1 /media/folder 
```
folder is any directory you want.

open a terminal and type
```
 sudo nano /media/folder/boot/grub/menu.lst 
```

then post whats in that file.  Once we can see whats in there well be able to help more.

---

### Post by jgregory on 2006-03-14
Let me first say that I'm no expert.

I found a little info about error 21 on the internet...

21 : Selected disk does not exist
     This error is returned if the device part of a device- or full file
     name refers to a disk or BIOS device that is not present or not
     recognized by the BIOS in the system. 

Google "GRUB error 21". There's lot's of info.

I just installed Edubuntu a couple days ago and had a similar error message from GRUB, except it was error 18, I think. It was related to a BIOS problem. I upgraded my BIOS and it still didn't work. I swapped my (too big) 250GB hard drive for a 20GB drive, then it booted. I don't have a dual boot system with XP on it though.

Help it helps... good luck.

John

---

