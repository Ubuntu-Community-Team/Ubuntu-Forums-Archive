---
title: "Install without CDROM and GRUB Error 17"
date: 2006-06-14
forum: Installation &amp; Upgrades
---

### Post by GameGod on 2006-06-14
Hi guys,

I've been trying to install Ubuntu 6.06 on a network file server I have at work. The machine has no CDROM and no floppy drive.

I was able to get Ubuntu 6.06 installed on it by installing GRUB on my USB key, and then copying the Ubuntu netinstall files over to my key and setting up a GRUB entry to boot the netinstall image.
(Yeah, it was confusing, but it worked.)

Unfortunately, when the Ubuntu installer set up GRUB on the hard-disk, it screwed up pretty badly. When I boot the machine, I get a GRUB Error 17. I'm pretty sure the problem is that my "hd(#,#)" entries are wrong in the "/boot/grub/menu.lst" file.

However, I can't just boot into a LiveCD to fix that problem. (Normally I'd just boot into a LiveCD, mount the hard-disk, and then edit that file...)

Since I don't have a CDROM, I can't boot into a LiveCD. However, I still have my handy USB key, and I managed to get Feather Linux installed (and booting) off of it.
Here's my big problem right now: When I try to mount the partition that the menu.lst file is on (/dev/hda3 for me), I get the usual "Bad FS type or bad superblock" error...
I have no idea why I can't mount that drive...

The partitioning is as follows:
1. Windows XP Embedded
2. Ubuntu EXT3 "/share1"
3. Ubuntu EXT3 "/"
4. Ubuntu EXT3 "/swap"

If anyone has any tips for me, they'd be greatly appreciated!

Alternatively, maybe someone can suggest another way that I can fix my GRUB...?

Thanks!

GameGod

---

### Post by GameGod on 2006-06-14
Ok, well, I'm trying another approach....

I'm going to try installing Ubuntu on the first drive (/dev/hda) instead... The reason I didn't do this in the first place is because I wanted to have Windows XP embedded still installed. I've backed up the partition XP embedded was on though, so I'm just going to overwrite it now.

(So I'm going to do a netboot install off my USB key again...)

---

### Post by catlett on 2006-06-14
If you have a problem again there are 2 suggestions I'l make . First try and get Puppy Linux installed on your usb key. It has a grub configurator application that you can select from the menu to instal grub. So if you can boot to it you can use that tool to install grub.
If you get in with feather again try this in a root terminal.```
grub
``` this should get you a grub< prompt ```
find /boot/grub/stage1
``` what ever the response is to that i.e. hdo,0 or hd1,2 use in the next command ```
root (hd?,?) 
``` and```
  setup (hd,?,?)
```and finally```
 quit
``` Hopefully you won't need any of this.

---

### Post by GameGod on 2006-06-15
Damnit, I wish I had read that earlier! lol

Feather Linux doesn't have grub installed on it... I should have tried Puppy Linux, dang...
Anyways, I imaged the first drive over to the second drive (ie. I backed up the WinXP Embedded partition) and I'm installing Ubuntu to the first drive as we speak...
If this doesn't work though, I'll give the Puppy/grub thing a go... :)

Thanks anyways! :)

---

