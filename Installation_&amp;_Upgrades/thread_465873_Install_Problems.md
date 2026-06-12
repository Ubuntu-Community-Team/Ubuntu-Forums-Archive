---
title: "Install Problems"
date: 2007-06-06
forum: Installation &amp; Upgrades
---

### Post by brunny on 2007-06-06
After 3 failed attempts (and one successful) to make a partition and reinstalling windows 3 times, I feel that i might need some help installing Ubuntu.

ok so i am running Vista on a brand new Sony Vaio laptop. i have got a partition of ~40GB for the program (D: drive)

so what the hell do i do.


cheers

gareth


P.s.Please be basic, as i have tried it already and it just failed.

---

### Post by celticbhoy on 2007-06-06
Is the 40G partition only for Ubuntu

---

### Post by brunny on 2007-06-06
> **celticbhoy said:**
> Is the 40G partition only for Ubuntu

Yeah

---

### Post by celticbhoy on 2007-06-06
Just double click install after you have booted from live cd, then follow on screen prompts until you come to the part where you are asked about partitions, then you have to make sure you are installing to your 40G Partition and the installer will take care of the rest. Grub should find and install for both systems plus any recovery partitions but on mine vista showed as longhorn.
After that is just setting up drivers and the forums should help with any specific problems

---

### Post by brunny on 2007-06-06
this seems to come up when i try

[[img]http://xs116.xs.to/xs116/07233/06062007089.jpg[/img]](http://xs.to)

[[img]http://xs116.xs.to/xs116/07233/06062007091.jpg[/img]](http://xs.to)

[[img]http://xs116.xs.to/xs116/07233/06062007092.jpg[/img]](http://xs.to)

---

### Post by celticbhoy on 2007-06-06
If you select 'manual', you will be able to select the 40G partition, and set the boot and swap partitions for Ubuntu

---

### Post by brunny on 2007-06-06
> **celticbhoy said:**
> If you select 'manual', you will be able to select the 40G partition, and set the boot and swap partitions for Ubuntu

sorry if being really stupid, but how do you set the boot and swap partitions for Ubuntu. i clicked on the 40 GB partistion and clicked next but the root error came up

cheers

---

### Post by brunny on 2007-06-08
> **brunny said:**
> sorry if being really stupid, but how do you set the boot and swap partitions for Ubuntu. i clicked on the 40 GB partistion and clicked next but the root error came up

cheers

Can anyone explain??

---

### Post by merlinus on 2007-06-08
Try clicking on your 40G partition and select edit.  This should give you a choice of mountpoint.  Select / 

You may have to reduce the size a bit so a swap partition can also be created.  It should be about 1.5 times RAM.

-merlin

---

