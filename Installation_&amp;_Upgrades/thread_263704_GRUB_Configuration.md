---
title: "GRUB Configuration"
date: 2006-09-23
forum: Installation &amp; Upgrades
---

### Post by src2206 on 2006-09-23
Hi,
I've installed Ubuntu 6.06.01 and its beautiful. Thanks Developers.

Now the Ubuntu GRUB has Ubuntu set as its default OS. But my PC is also used by my family members who are not that tech savy and accustomed to Windows, which I have.

So how can I change the default OS to Win XP Pro in the Ubuntu GRUB menu when nothing is selected?

Please help.

---

### Post by Tomosaur on 2006-09-23
Easy. You may edit the /boot/grub/menu.lst file in any text editor, and change the line which says:

default 0

to the number of your choice. Grub counts from zero, so the first item in the grub menu is 0, second is 1 etc etc. The little 'Other Operating Systems:' dividor in Grub DOES count as a menu item too, so don't forget to include it in your count :)

You will need to use sudo or gksudo to gain root priveleges in order to edit /boot/grub/menu.lst, so you should press alt+f2 then in the box, type:
gksudo gedit /boot/grub/menu.lst

Alternatively, you can download the script in my signature, which allows you to change a whole bunch of Grub settings using a GUI :)

---

### Post by ajgreeny on 2006-09-23
Have a look at:-
[http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu](http://ubuntuguide.org/wiki/Dapper#How_to_change_default_Operating_System_boot-up_for_GRUB_menu)
This is part of a large html page with lots of useful info about ubuntu.

---

### Post by Cariboo1938 on 2006-09-23
> **src2206 said:**
> Hi,
I've installed Ubuntu 6.06.01 and its beautiful. Thanks Developers.
Now the Ubuntu GRUB has Ubuntu set as its default OS. But my PC is also used by my family members who are not that tech savy and accustomed to Windows, which I have.
So how can I change the default OS to Win XP Pro in the Ubuntu GRUB menu when nothing is selected?
Please help. Check [this]("http://users.bigpond.net.au/hermanzone/") and [ that]("http://www.ubuntuforums.org/showthread.php?t=229909&high"). I use "GAG 46" or "Super Grub Disk". The main thing to do was, to enter the following in "/boot/grub/menu.list":
> title Windows XP
root  (hd1,0)
savedefault
makeactive
map  (hd0) (hd1)
map  (hd1) (hd0)
chainloader +1. 

---

### Post by src2206 on 2006-09-24
Hi,
Problem solved- had to reinstall.
Thank you all :D

---

