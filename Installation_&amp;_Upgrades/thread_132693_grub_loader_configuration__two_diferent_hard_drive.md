---
title: "grub loader configuration_ two diferent hard drives"
date: 2006-02-18
forum: Installation &amp; Upgrades
---

### Post by makende12 on 2006-02-18
hi ubuntians, i am new to  ubuntu but have been playing around with suse linux 10. i have two hard drives with the following setups

 Hard drive one -->hda - has Winxp and Suse linux
 Hard Drive two -->hdb - has  winxp1, winxp2 and ubuntu

i would like to have separate grub boot loaders for the two hard drives but with the hda loading using Suse and hdb loading using ubuntu.

the problem is when i install ubuntu, it loads onto the master boot record on hda rather than on hdb so that if i am on hard drive b (hdb) it wont load the boot loader as it has been stored on hda.

i have tried to set it up at install time in the install grub boot loader time in the ubuntu install and it wont recognise /dev/hdb3 where the reiser system is at and keeps having the messant cant find dev/hda3 fatal error

any help will be appreciated

---

