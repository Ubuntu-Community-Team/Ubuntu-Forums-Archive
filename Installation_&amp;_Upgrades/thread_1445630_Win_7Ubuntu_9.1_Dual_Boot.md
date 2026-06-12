---
title: "Win 7/Ubuntu 9.1 Dual Boot"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by spike53 on 2010-04-02
Hey,
Now what I have a spare drive, I've decided to take a dip into Linux. I tried installing it, it works, on its own though. However, I can't figure out how to get it to dual boot. I have 2 drives (not partitions but physical drives), one is dedicated Windows 7, the other one is dedicated for Ubuntu. 7 is my primary and is the only one that works from the boot menu I created. I used Easy BCD to create the MBR. When I use any other bootmanager other than GRUB, I get a message saying that Ubuntu can't boot from its hard drive. When I use GRUB, it comes up with some DOS looking GUI which I don't know what to do with. I'm a Linux beginner so I don't know many codes. 
I want to know what I need to do in order to get my 7 and Ubuntu discs to cooperate together so I can successfully make a dual boot.
Thanks for the help,
Spike

---

### Post by Arand on 2010-04-02
What I would do is (re-)install GRUB to the mbr of the Ubuntu disk, and then setup EasyBCD to chainload GRUB from that disk.

Reinstalling GRUB via a liveCD should take care of getting past the GRUB rescue screen (which is due to grub not being able to load the GRUB configuration file):

[LIST=1]
[*]Boot a liveCD
[*]Start a terminal from [menu]Applications>Accessories>Terminal
[*]Find out what partition is the Ubuntu root:```
sudo fdisk -l
```The Ubuntu root should be the one designated Linux (not Linux swap) e.g.```
/dev/sdb1   *           1    15504256   488384032+   83  Linux
```I will thus use sdb1 for the Ubuntu root, if yours is ootherwise, change all following commands accordingly.
.
If you have a separate /boot partition these instruction does NOT apply (it needs to be mounted to /mnt/boot in addition)
.
[*]Mount current ubuntu root partition :```
sudo mount /dev/sdb1 /mnt
```[*]Reinstall GRUB:```
sudo grub-install --root-directory=/mnt /dev/sdb
```
[/LIST]
Now GRUB should be setup to load if the mbr of the second harddisk is initiated.
Then make BCD load the mbr of the second disk, using EasyBCD or otherwise.

- Arand

---

### Post by spike53 on 2010-04-04
Thanks for the help Arand!
I tried what you said and it gave me a confirmation that GRUB was installed. However I didn't know about the way BCD wants it to be done so it never really worked until I came across the documentation on how to do it.
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu) is the link to the steps I followed and they worked like a charm. Apparently I didn't do many things right the first time.
Regards!
Spike

---

