---
title: "Vista missing from grub after install"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by Unlimbo on 2008-06-24
Complete ubuntu newbie here. I had three partitions on my laptop, one with xp, one with vista and a third data partition. I deleted the xp partition in the ubuntu setup and used the remaining free space for the ubuntu install. All went well. After exiting ubuntu and rebooting there is no entry for vista in the boot options, but looking at device input in QGRUBEditor I have:

  ¦mountpoint        ¦partition ¦GRUB Part ¦Device ¦GRUB Device¦

0/                   /dev/sda7  (hd0,6)    /dev/sda (hd0)
1/media/DATA         /dev/sda6  (hd0,5)    /dev/sda (hd0)
2/media/Vista\040x64 /dev/sda5  (hd0,4)    /dev/sda (hd0)


Also, when I look in main menu > places both my Vista & Data partitions are intact. How do I get GRUB to allow me to boot Vista? :confused:

Many thanks in advance.

---

### Post by overdrank on 2008-06-24
> **Unlimbo said:**
> Complete ubuntu newbie here. I had three partitions on my laptop, one with xp, one with vista and a third data partition. I deleted the xp partition in the ubuntu setup and used the remaining free space for the ubuntu install. All went well. After exiting ubuntu and rebooting there is no entry for vista in the boot options, but looking at device input in QGRUBEditor I have:

  ¦mountpoint        ¦partition ¦GRUB Part ¦Device ¦GRUB Device¦

0/                   /dev/sda7  (hd0,6)    /dev/sda (hd0)
1/media/DATA         /dev/sda6  (hd0,5)    /dev/sda (hd0)
2/media/Vista\040x64 /dev/sda5  (hd0,4)    /dev/sda (hd0)


Also, when I look in main menu > places both my Vista & Data partitions are intact. How do I get GRUB to allow me to boot Vista? :confused:

Many thanks in advance.

Hi and welcome, I am no grub expert but is it listed in the  grub menu?
You can use the command ```
gksu gedit /boot/grub/menu.lst
```
Also this link may help to add vista to the menu 
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by meierfra. on 2008-06-24
You will have to edit "menu.lst" via 

```
gksu gedit /boot/grub/menu.lst
```

and add this to the end of the file:

title Vista
rootnoverify (hd0,4)
chainloader +1

(It is important that you do NOT use "makeactive. Otherwise you will get Grub Error 12)

But editing menu.lst by itself will not solve your problem:


>  I deleted the xp partition in the ubuntu setup 

The XP partition contained all the boot files for Vista. So grub will not be able to boot Vista.

Give this a try:

[http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD")

But since Vista is on a logical partition, I'm not sure that it will work.

---

