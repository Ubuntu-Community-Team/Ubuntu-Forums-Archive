---
title: "grub loader not working!"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by gretarsson on 2008-11-27
Hi there. I had ubuntu UE 8.04 in my son computer and upgrade to ubuntu 8.10 but after that it want start so I tried to use live cd with ubuntu 8.10 and reinstall but nothing happen the cd can not find hdd so I took that hdd out of my son   computer and but into my computer and reintall it on that hdd, it work fine in my computer but when I put that hdd back to my son computer I got grub Erro13 so I tried use cd name super grub loader to fix that grub menu but I am not sure what to do there,  can some one explane to me how grub loader work, what does this uuid number mean, is that id number for my son hdd and hdd0,0 mean first hdd (my son computer only have one hdd)

---

### Post by confused57 on 2008-11-27
> **gretarsson said:**
> Hi there. I had ubuntu UE 8.04 in my son computer and upgrade to ubuntu 8.10 but after that it want start so I tried to use live cd with ubuntu 8.10 and reinstall but nothing happen the cd can not find hdd so I took that hdd out of my son   computer and but into my computer and reintall it on that hdd, it work fine in my computer but when I put that hdd back to my son computer I got grub Erro13 so I tried use cd name super grub loader to fix that grub menu but I am not sure what to do there,  can some one explane to me how grub loader work, what does this uuid number mean, is that id number for my son hdd and hdd0,0 mean first hdd (my son computer only have one hdd)
This should give you some idea of grub's hard drive/partitioning system:
[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

Does your son's computer show a grub boot menu when booting the computer?  If it does, you can try highlighting the first Ubuntu entry, press "e", highlight the line with root, change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot...x & y represent the numbers that your root line already shows, e.g. if root shows (hd1,0), change it to (hd0,0).
This change is temporary, but you can make it permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
You'll also need to change the line with #groot to (hd0,y).

---

### Post by gretarsson on 2008-11-28
> **confused57 said:**
> This should give you some idea of grub's hard drive/partitioning system:
[http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System](http://users.bigpond.net.au/hermanzone/p15.htm#A_Quick_Guide_to_Grubs_Numbering_System)

Does your son's computer show a grub boot menu when booting the computer?  If it does, you can try highlighting the first Ubuntu entry, press "e", highlight the line with root, change root from (hdx,y) to (hd0,y), press "enter", then "b" to boot...x & y represent the numbers that your root line already shows, e.g. if root shows (hd1,0), change it to (hd0,0).
This change is temporary, but you can make it permanent in your menu.lst:
```
gksudo gedit /boot/grub/menu.lst
```
You'll also need to change the line with #groot to (hd0,y).

Hi and Thanks
Nothing come up when I start my son computer, after bios has run it come one blinkking underline in left top line one the screen but if I but in the cd disk call super grub loader and runed then I can see  the grub karnel lines, I try your idea tonight and I let you know how it goes
Thank you for quick reply

---

### Post by confused57 on 2008-11-28
You also might try using the live cd to install grub to the hard drive's mbr:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
You should probably do this before trying what I mentioned earlier...good luck.

You can also do this with Super Grub Disk's "Fix Boot of Linux"

---

