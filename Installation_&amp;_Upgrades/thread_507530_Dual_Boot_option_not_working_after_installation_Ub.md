---
title: "Dual Boot option not working after installation Ubuntu - Vista"
date: 2007-07-23
forum: Installation &amp; Upgrades
---

### Post by joe.kosterman@gmail.com on 2007-07-23
Hi

I recently bought a new laptop (HP Pavilion dv6386sc) AMD Turion™ 64 X2 Mobile Technology, 2048 MB, 160 GB, 15,4" og 2 GB RAM, which has a pre-installed version of Windows Vista Premium. I downloaded the lastest version from Ubuntu and then proceded to install Ubuntu, after I have left 15 GB of un-allocated space. 

The installation went fine, and I was within the uBuntu operating system. I  then after a while shutdown the laptop and rebooted in order to get to the dual boot window and test it. It however started immediately with Windows Vista, not providing me with an option to select which operating system I want to use. I have re-installed Ubuntu again, but my problem is still un-resolved.

How do I fix this? I am new to Linux and would really like to use it.
 
Look forward to some asistence and possible a solution to  fix this?

Joe

---

### Post by Arwen on 2007-07-23
You did made a /boot partition right?Otherwise you have to install grub on your own..I don't think vista have a problem,I had xp in my laptop,installed vista,deleted xp and installed ubuntu and now the bootloader has the options for ubuntu and save mode for ubuntu,memtest and windows vista/longhorn(or sth like that).

---

### Post by joe.kosterman@gmail.com on 2007-07-23
Ok

Since I am really new to Linux, how do I install the Grub application and how can I find it?

Joe

---

### Post by confused57 on 2007-07-23
You might try booting Ubuntu from the Vista bootloader:
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

To do this, you need to install grub to Ubuntu's root partition, which you can do with the Ubuntu live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

For example, to install grub to the root partition...wherever "find /boot/grub/stage1" locates your root partition this is where you will setup, i.e. "setup (hd0,3)"...if you want to try installing to the mbr, then "setup (hd0)".

I would recommend trying to boot Ubuntu from Vista...

---

