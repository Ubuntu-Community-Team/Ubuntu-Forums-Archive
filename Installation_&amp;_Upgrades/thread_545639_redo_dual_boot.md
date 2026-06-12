---
title: "redo dual boot"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by uposer111 on 2007-09-07
Ok, i just deleted all my partitions and started fresh,  I use to have Vista and a old version of Ubuntu and now i want the new Ubuntu 7.04. i set up my partions as follows:

Sda1 Fat 32 54Mb
Sda2 Ntfs 35Gb
Sda3 ext3 25Gb
Extended
Sda5 Linux-swap 2.42Mb
Sda6 Fat32169Gb

I am using the GUI Ubuntu Live CD 7.04 and when I get to the partioning part, i go to manual install on what partition i want and this is the error i get.

[IMG]http://i74.photobucket.com/albums/i274/levidicus/Screenshot-1.png[/IMG]

I hope someone knows what this means.

Thanks
Jeff

---

### Post by banewman on 2007-09-07
A simple solution is if you know the partition that you want to make "/" or the ubuntu install then right click it - delete it - then right click the unallocated space and choose to set it up as root "/"
Hope this helps. :)

---

### Post by uposer111 on 2007-09-07
Thank you, that worked!

Jeff

---

### Post by banewman on 2007-09-08
Happy Ubuntuing!:lolflag:

---

