---
title: "Problem installing Ubuntu &amp; other Os"
date: 2009-12-30
forum: Installation &amp; Upgrades
---

### Post by elaine81 on 2009-12-30
hi all , 

 need help , the scenario is like this  , i was helping my sis troubleshoot her compaq presario laptop , Original os  [Vista[IMG]http://images.intellitxt.com/ast/adTypes/mag-glass_10x10.gif[/IMG]]("http://forums.hardwarezone.com.sg/showthread.php?p=42885438#") , my sis format with Win 7 disc , everything was working fine for 1 or 2 mths , then suddenly , yesterday when she try to login window 7 , after the login screen , it stuck at a black screen with just a cursor. Today i try to format with Ubuntu , but installation only finish half way , then it say something about old hdd or watsoever , then auto boot to live cd , when i try to boot from my memory card which i hv created as a bootable usb drive for win 7 , but system will just prompt me "Remove disk & Other media , Press any key to restart" . My sister lost the win 7 disc , her vista was built in wan , last time change hdd , so lost , then my lappy also no dvd writer , therefore cannot burn win7 image to dvd , Anyone can help me think of other solution ?

---

### Post by dstew on 2009-12-30
Boot the Ubuntu Live CD, open a terminal window, enter the command```
sudo fdisk -l
```That will show what partitions are left on the hard drive. Maybe you can still boot into Windows using grub, if it is still intact.

---

### Post by elaine81 on 2009-12-31
> **dstew said:**
> Boot the Ubuntu Live CD, open a terminal window, enter the command```
sudo fdisk -l
```That will show what partitions are left on the hard drive. Maybe you can still boot into Windows using grub, if it is still intact.


Thanks for ur help , but i am newbie in ubuntu , dun realli get you . Do you  or anyone here know how to create a bootable usb stick in ubuntu , pls help ... thanks

---

### Post by dstew on 2009-12-31
Do you have an Ubuntu CD?

---

### Post by elaine81 on 2009-12-31
> **dstew said:**
> Do you have an Ubuntu CD?


yes , i do  , and   rite now  , my os id ubuntu 9.10 , but what i need is to create a bootable usb stick for my win 7 , thanks

---

### Post by dstew on 2009-12-31
What OS do you want to put on the bootable USB stick? Do you want to put an Ubuntu Live CD system on it?

---

### Post by elaine81 on 2009-12-31
> **dstew said:**
> What OS do you want to put on the bootable USB stick? Do you want to put an Ubuntu Live CD system on it?


Nope wan to put win 7

---

### Post by dstew on 2010-01-01
We can't help you with that. You might find some help in a Windows forum.

---

