---
title: "moving GRUB boot loader"
date: 2014-06-21
forum: Installation &amp; Upgrades
---

### Post by louis.nel on 2014-06-21
Hello I am quite new to Ubuntu and have made a mistake when i was installing 13.10 and the I think the boot loader is in the wrong place so that when i boot my pc I get no option to boot into ubuntu? Really annoyed :mad:

Any help greatly appreciated

---

### Post by Dreamer Fithp Apprentice on 2014-06-21
You could just install it again.

---

### Post by ajgreeny on 2014-06-21
Where do you think you installed grub?
If you used the default system for installation and did not use the "Something Else" option, you will not have seen any choice of a grub installation; it will automatically have gone to the correct place on the machine.

Have a look at Boot-Repair in my signature at the bottom of my post; it may help you out.

PS:
Why 13.10 and not 14.04?  13.10 will lose support very soon and 14.04 still has nearly 5 years support remaining.

---

### Post by grahammechanical on 2014-06-21
The installer defaults to installing Grub into the MBR of the first hard disk. Which is the correct place for most users.

You should tell us more about your system, the hardware specifications, other operating systems. Due to the lack of information we might give advice that will make matters worse. Do you want to be even more annoyed? Messing up your machine is within the realm of possibilities. :)

---

### Post by louis.nel on 2014-06-22
hi guys

[COLOR=#000000]ajgreeny: I have go a live disk for 13.10 so i used that for the install and GRUB is installed in the third partition on the hard disk. I did use the something else option when i installed Ubuntu and put the GRUB in the wrong place by accident.
 
grahammechanical: I have an HP Compaq witha 80 gig HDD with three partitions the other os is win XP.

Hope that helps 

[/COLOR]

---

### Post by ajgreeny on 2014-06-22
Grub should **not** be installed in a partition but in the first sectors of the disk itself, ie, in your case /dev/sda, not /dev/sda3, which I think is where you put it.

You can either reinstall the whole system, which should not take long, or you can try installing grub to the proper place with Boot-Repair from my signature link.

Good luck.

---

### Post by louis.nel on 2014-06-22
thanks will do that

---

### Post by louis.nel on 2014-06-26
Hello there

Ive tried the boot repair from ajgreeny's signature but my ubuntu live dvd is to slow does anyone else have some ideas???

Please help 

thanks

---

### Post by oldfred on 2014-06-26
How much RAM and what video?
Full Ubuntu with Unity needs more RAM and newer video card/chip to work well. Otherwise fallback or gnome-panel, Xubuntu or Lubuntu work much better.
The Boot-Repair liveCD is based on Lubuntu.

---

