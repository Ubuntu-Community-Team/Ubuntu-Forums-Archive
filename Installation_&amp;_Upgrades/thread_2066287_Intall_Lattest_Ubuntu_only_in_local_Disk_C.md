---
title: "Intall Lattest Ubuntu only in local Disk C"
date: 2012-10-04
forum: Installation &amp; Upgrades
---

### Post by MrBledi on 2012-10-04
Hello everyone... i want to format my notebook again with the ubuntu... i want to format only Local Disk C not formating  Local Disk D cos there i got all my multimedia downloads... is there a tuto to help me with this please?
Thanks allot!

---

### Post by darkod on 2012-10-04
First of all, C and D is what windows calls partitions. If you have windows and you format C you will lose it. Is that what you want to do?

Install ubuntu on its own partition with its own linux filesystem?

Or only install wubi inside windows?

---

### Post by MrBledi on 2012-10-04
> **darkod said:**
> First of all, C and D is what windows calls partitions. If you have windows and you format C you will lose it. Is that what you want to do?

Install ubuntu on its own partition with its own linux filesystem?

Or only install wubi inside windows?

 i wanna format C 
and keep the D as it is!  
it doesn't metter if the C is formatted... i only wanna save the D 
P.S: inside i got only one HDD but serperated it in two parts

---

### Post by darkod on 2012-10-04
Boot the ubuntu cd in live mode (Try Ubuntu) and open Gparted. Delete the partition you want to delete. Don't forget to click the green button in Gparted so it can execute the changes.

After that start the install process and either use the manual partitioning option (called Something Else) where you can create your own partitions, or use the auto method to install which will use the unallocated space left by deleting the partition.

---

### Post by MrBledi on 2012-10-04
thank you very much... an lattest question, it's inculed linux kernel 3.4 on this Ubuntu?

---

### Post by QIII on 2012-10-04
Before you do anything at all, back up your important files.

Don't do anything until you have done that.

Sorry for the intrusion, Darkod.  ;)

For you and me that goes without saying.

---

