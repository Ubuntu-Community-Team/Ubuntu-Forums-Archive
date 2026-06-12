---
title: "New Install - Grub Prompt Only"
date: 2007-03-26
forum: Installation &amp; Upgrades
---

### Post by aerofoil on 2007-03-26
Hi all

I am pretty new to linux as a whole, I have had some experience with Suse, and FC, but am totally new to Ubuntu. 

I have tried to install 6.10, using the partitioning as below:

SATA Drive:
/boot   512MB Ext3
/         180GB Ext3
Swap   4GB Swap

IDE Drive:
/media/sda5 120GB

However, when booting for the first time, I am presented with a prompt saying 'grub>'. I thought it was meant to present me with a menu of what to choose, or go straight into ubuntu. I am not running dual boot. 

I am looking for some help to get it to boot into ubuntu.

Thanks for any help.

---

### Post by zvacet on 2007-03-26
```
sudo gedit boot/grub/menu.lst
```
line timeout maybe it take too much time to boot so change the time(is in seconds)
next line is about show/hide menu
see what is saying and if you don´t like it change but this is not important to you because you are not in dual boot.If you want to see grub menu you can allways press** esc**

---

### Post by aerofoil on 2007-03-26
I pressed escape, and nothing happened - the screen with the grub prompt refreshed, but that was it.

Using sudo gedit /boot/grub/menu.lst, I got an Error 27: Unrecognised command.

Thanks for your help.

---

### Post by confused57 on 2007-03-26
> **aerofoil said:**
> I pressed escape, and nothing happened - the screen with the grub prompt refreshed, but that was it.

Using sudo gedit /boot/grub/menu.lst, I got an Error 27: Unrecognised command.

Thanks for your help.
You could try reinstalling grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Here's a short description of your problem:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Returns_to_a_Grub__prompt](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Returns_to_a_Grub__prompt)

See the first link in my signature for some excellent information about grub.

---

