---
title: "Upgraded to Ubuntu 16.04 from 15.10 Now can only boot into Windows"
date: 2016-06-06
forum: Installation &amp; Upgrades
---

### Post by hsinas on 2016-06-06
Hi I had dual boot Windows 10 and Ubuntu 15.10

I upgraded to Ubuntu 16.04 using the software updater and now the PC only boots into Windows 10.

I ran the boot repair tool from a flash drive but It made no difference 

The report is here

[http://paste.ubuntu.com/17058583/](http://paste.ubuntu.com/17058583/)

---

### Post by hsinas on 2016-06-06
OK I can now boot into both now, I ran boot-repair with secureboot ticked however now I have all these entries that were not there before in the GRUB Menu shown below (the ones that start with "EFI/")

[http://i.imgur.com/qRqBrpy.jpg](http://i.imgur.com/qRqBrpy.jpg)

The latest boot info report is here :

[http://paste.ubuntu.com/17058992/](http://paste.ubuntu.com/17058992/)

---

### Post by hsinas on 2016-06-06
OK, I removed the entries from /etc/grub.d and now its ok :)

---

### Post by oldfred on 2016-06-06
Boot-Repair sees all the HP .efi files and assumes you may want those as bootable choices in menu.
So it adds 25_custom with all those entries. 

You normally can edit out most or turn off execute bit so none are added. 
Not sure if when you need HP repairs if you can or need to boot any of those from grub or not.

---

