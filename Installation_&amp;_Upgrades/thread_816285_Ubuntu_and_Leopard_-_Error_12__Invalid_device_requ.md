---
title: "Ubuntu and Leopard - Error 12 : Invalid device requested"
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by theumang on 2008-06-02
Hi All!

Leopard worked fine when that was the only operating system on the computer..
after I installed the Ubuntu, leopard was not being recognized by the grub.

I have edited the grub (source - [http://www.howtoforge.com/working_with_the_grub_menu](http://www.howtoforge.com/working_with_the_grub_menu)) and managed to change the background too, however when I choose Leopard to boot from, it comes up with the error - Error 12 : Invalid device requested.

This is the sudo fdisk -l result..

umang@umang:~$ sudo fdisk -l
[sudo] password for umang: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00074fb8

Device Boot Start End Blocks Id System
/dev/sda1 1 2188 17575078+ 83 Linux
/dev/sda2 2189 26511 195374497+ 5 Extended
/dev/sda5 * 2189 26511 195374466 af Unknown

How do I go about fixing this error ?

Thanks
Umang

PS: do not have / want windows on my computer.

---

### Post by theumang on 2008-06-04
Bump

---

### Post by demonzrulaz on 2008-12-07
Bump. Sorry for bumping an old thread but I have the exact same problem

---

### Post by lovecrime on 2009-04-03
I've the same problem too 
I tried all the possible entry to add mac to menu.lst none of them works

---

### Post by theumang on 2009-04-03
Bump!

am Bumping may own thread, seems like no one (ofcourse apart from demonzrulaz, lovecrime & ??, i guess.. me) with a Mac likes Ubuntu & Vice-a-versa..

---

