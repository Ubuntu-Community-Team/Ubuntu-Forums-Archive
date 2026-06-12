---
title: "hard drive inaccessible"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by rajeev1204 on 2006-11-11
hi
when i run ubuntu live desktop cd amd 64 it shows my 2 partitions but doesnt show details like used or free space.and says drive inaccessible and no available free space.i have windows installed on it and i want to dual boot.

what seems to be the problem]

i have 80 gb sata drive
amd 64 MSI K8NGM V  mobo

---

### Post by ReaderRat on 2006-11-11
If you alraedy have Windoze on the entire disc, you will need to download [**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php) and use it (A bootable CD) to resize your Windblows partition first, to make room for Ubuntu.
First off, how much RAM do you have? This determines what version of (K)(X)Ubuntu you can install.

---

### Post by rajeev1204 on 2006-11-12
hi 

thanks for replying
i have 512 MB RAM .why do i need to get gparted when i already have it on the ubuntu live cd 6.06 LTS?! isnt it supposed to complete the dual boot process automatically?

---

### Post by ReaderRat on 2006-11-12
I don't believe you can **[COLOR="Red"]resize[/COLOR] a partition** with the copy on the LiveCD. You can with the more recent version.

---

### Post by rajeev1204 on 2006-11-17
hi
thanks a lot for the reply
anyways i manually partitioned my windows d partition and formatted it for ubuntu. installation was easy and last step was getting display drivers for nvidia which i got from repository.so things went smooth. 

now iam stuck with the obvious problem of 64 bit - no real player ,no flash - but i downloaded firefox 2 and it seems to run flash sites just ok.also got latest java.

anyway i guess this topic has to be in another heading

thanks and bye 
:)

---

