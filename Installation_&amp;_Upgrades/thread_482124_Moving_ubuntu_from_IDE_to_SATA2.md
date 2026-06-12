---
title: "Moving ubuntu from IDE to SATA2"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by Xmister on 2007-06-23
Hi all!
In 2 week I will buy a completely new pc, and I will want to move my ubuntu feisty installataion from this 80GB IDE to the new 320GB SATA2 drive. Is it possible to do it without any data-loosing? And if I could copy everything, how to make it bootable?

---

### Post by Xmister on 2007-07-11
Okay, I did it myself.
From live-cd:
First created the same sized partitions in fdisk on the new drive.
Then entered this command: dd if=/dev/hda1 of=/dev/sda1
This took about 3-4 hours in my 80Gb drive.
Then edited the new drive's fstab to the correct values, edited grub's devices.map, and menu.lst, and installed grub to the new drive.
So, linux "easily" moved. But I think I should reinstall XP somehow...it doesn't want to start, just BSOD :mad:

---

### Post by Xmister on 2007-07-26
When I reinstalled XP I unplugged Ubuntu's drive for safe.
Now I can't make grub to boot XP. I had to change the boot drive in BIOS.
My XP in menu.lst:
> title		Microsoft Windows XP Professional - magyar
root		(hd1,0)
savedefault
makeactive
chainloader	+1
My device.map:
> (hd0)	/dev/sda
(hd1)	/dev/hda
I think it should work but it doesn't want to.
Is there some auto configure tool for grub which finds the OS and configure grub for it, like the installer did?

---

### Post by dabl on 2007-07-26
> **Xmister said:**
> 
When I reinstalled XP I unplugged Ubuntu's drive for safe.



A lot of people seem to think that is a good approach -- it is not.  Somewhere in the installation instructions it needs to say "LEAVE ALL YOUR HARD DRIVES CONNECTED!"

OK, here's some good information on how to deal with the resulting problems:

[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

:)

---

### Post by logos34 on 2007-07-26
> A lot of people seem to think that is a good approach -- it is not. Somewhere in the installation instructions it needs to say "LEAVE ALL YOUR HARD DRIVES CONNECTED!"

I don't think that's the problem--it might be if it was Ubuntu he had reinstalled, in which case the debian installer would not detect the presence of another OS and add it to menu.lst and fstab.  But it hardly matters for windows, which refuses to acknowledge the existence of any linux fielsystems anyway.

I think it's tha fact that you are now booting to the grub menu on sda, which means windows is now on a non-first hard drive--winxp usually won't boot unless it thinks it's on the first bios drive.  You have switch the mapping of the drives.  Edit your menu.lst entry for windows:  

> title Microsoft Windows XP Professional - magyar
root (hd1,0)
[B]map (hd1) (hd0)
map (hd0) (hd1)[/B]
savedefault
makeactive
chainloader +1

Try that.

---

### Post by Xmister on 2007-07-26
Thankx, that's worked.
Could you explain what does these 2 lines doing?
The first may show for the OS hd1 as hd0, but why the second line turn it back?

---

### Post by logos34 on 2007-07-27
> Thankx, that's worked.
Could you explain what does these 2 lines doing?
The first may show for the OS hd1 as hd0, but why the second line turn it back?

It's just a way of telling windows that the drive it is on (/dev/hda) is now designated hd0 rather than hd1. (i.e. the first bios boot drive).  Windows is hard-wired to boot only in first position in the hard disk boot priority.  I'm not sure how to explain it in programming language-terms. 

Enjoy!

---

