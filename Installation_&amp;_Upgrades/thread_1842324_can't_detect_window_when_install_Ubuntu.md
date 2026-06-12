---
title: "can't detect window when install Ubuntu"
date: 2011-09-11
forum: Installation &amp; Upgrades
---

### Post by Renoald on 2011-09-11
Hai , i already install window xp in Laptop. when I install ubuntu ( using boot from discs ) , the ubuntu set up can't find the operating system of XP.
 I also install the ubuntu inside window but also can't not because at some process , the setup say can't find the root file for ubuntu!
any one have solution about this ?
Thank

---

### Post by mue.de on 2011-09-11
Hello and welcome as a new ubuntu-user!

I've installed sometimes (K)ubuntu from CD, but before that i assured, that i had made a copy of the MBR and the boot records from the other partitions. It's just one 512Byte File, that helps you to get back to the point where you were before.
So, be sure to save your sytem (Image-Backup).
Then you can easy install GRUB2 into the MBR of your harddsik, GRUB2 will find the Windows-Partition and lists it in the Bootmenue as the last entry (Windows Recovery mode ?)

Good luck

mue.de

---

### Post by donpeter06 on 2011-09-11
If during installation this problem occurs , then i seriously doubt the integrity of the CD you have. Either use a different CD or boot from USB drive and install Ubuntu.

---

### Post by ashickur.noor on 2011-09-11
After install update your grub and check that weather grub finds windows or not. If it finds then no thing to worry.

---

### Post by donpeter06 on 2011-09-11
whats the ubuntu version you are using?

---

### Post by Renoald on 2011-09-13
> **donpeter06 said:**
> whats the ubuntu version you are using?
Ubuntu 9.04

---

### Post by Renoald on 2011-09-13
If I just install it , then ubuntu will delete my operating system(window) in C  drive or not ?

---

### Post by Renoald on 2011-09-13
> **mue.de said:**
> Hello and welcome as a new ubuntu-user!

I've installed sometimes (K)ubuntu from CD, but before that i assured, that i had made a copy of the MBR and the boot records from the other partitions. It's just one 512Byte File, that helps you to get back to the point where you were before.
So, be sure to save your sytem (Image-Backup).
Then you can easy install GRUB2 into the MBR of your harddsik, GRUB2 will find the Windows-Partition and lists it in the Bootmenue as the last entry (Windows Recovery mode ?)

Good luck

mue.de
Thank for reply ....... 
but how can i do it because i only can boot ubuntu from disk but can't  install ? if i directly install using boot method i think ubuntu will delete the operating system window

---

### Post by Renoald on 2011-09-13
> **donpeter06 said:**
> If during installation this problem occurs , then i seriously doubt the integrity of the CD you have. Either use a different CD or boot from USB drive and install Ubuntu.

i think the disc not have problem because when install inside window , the error "can't find the root" happen when the  system boot into ubuntu loading page ( the disc already remove) 
i also try USB drive , some error happen .........
the problem of hardware will effect this or not ? 
because every time i start my window , i need to press F2 to load window .....i already format window , but still can't resolve ...
every new startup of window , the system time and date need to reset .....

---

### Post by donpeter06 on 2011-09-13
Let us make this clear
You have Windows in your machine and wants to install ubuntu 9.04? Right?
Now all you have to do is go to windows and make a partition fat32.
they restart and boot from ubuntu dvd and install it(not inside windows) .
During installation when asked for partitions do select custom and then select the partition that has free space then under the menu you will have an option to select the boot loader choose windows bootloader and continue with the istallation.
PS: Using an ubuntu 10.10 or 11.04 is advisable.)
Now if you have any more queries free feel to post it Am here to help.

---

