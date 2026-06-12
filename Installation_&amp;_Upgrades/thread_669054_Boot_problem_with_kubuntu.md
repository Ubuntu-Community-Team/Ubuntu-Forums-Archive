---
title: "Boot problem with kubuntu"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by Strike_105x on 2008-01-16
Hi i have tried to install kubuntu 7.10 amd64 but after i install it and restart i get the folowing error system boot failure does anybody know how to fix this pls ?
My PC specs are AMD Sempron X64 3000+ socket 754, motherboard asrock nforce 3, 1GB DDR400, Maxtor 80 GB HDD SATA, seagate 40 gb hdd, ATI 9600XT.
 (scaned my hdd with 2 utilities from hiren boot CD forgot the names, and my ram with memtest86 so i dont have no problems) 
 
 I installed ubuntu on the SATA drive i made of partition of 14GB for root, 1 gb partition for swap, and the rest of the hdd i used for /home (i made them (except for swap ofcourse) ext3)
 I dont have dual boot i dont intend on using windows anymore (but i did left the 40 gb hdd in ntfs because i tend to go to friends to get some data (music movies etc) using that hdd)

---

### Post by jeffus_il on 2008-01-16
Do you get as far as the Grub menu?

---

### Post by Strike_105x on 2008-01-16
yes i get to the grub he is the one its saying system boot error

---

### Post by jeffus_il on 2008-01-16
can you post the line that is executed,
while the boot line is highlighted, type e to edit, then you will see the text.

---

### Post by Strike_105x on 2008-01-16
I seem to resolve the problem partitioned my hdd with a difrent software (partition magic) and didnt put /home on the other partition now it seem to work

---

