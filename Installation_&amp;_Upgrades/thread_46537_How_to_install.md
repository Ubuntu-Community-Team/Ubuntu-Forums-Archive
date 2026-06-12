---
title: "How to install"
date: 2005-07-05
forum: Installation &amp; Upgrades
---

### Post by godsownman on 2005-07-05
I received my Ubuntu CD package today. I tried installing the OS on to my computer .

I faced a problem.

I have two Hard disk drives  (HDD) they are ,

1.    8.1    GB   Hard disk drive 
2.    20.1  GB   Hard disk drive.

I have Windows XP PRO  loaded on the smaller one which is 8 GB in size.

Now what I want to do is to load the Linux OS on the 20 GB hard disk drive after manually partitioning it in DOS.

I tried doing so.

I made 2 partitions one of  6 GB and the other of 14 GB.

I tried loading the Ubuntu CD on the 6GB partiton but I could not succeed. I repeatedly got errors .

Then I tried the auto partition method where I could load it  successfully .

But in this method I have to sacrifice the 14 gb which I dont think I will ever use in the Linux OS.

So can Anybody please tell me how to load the OS onto the smaller partition on 6 GB using the manual partition method.

I would be gratefull if you could please tell me the exact steps.

Also was I correct when I made 2 partitions of 6gb and 14 gb .

Thanking you for your time.

---

### Post by Lunde on 2005-07-05
You just have to delete the 6gb partition and leave it as empty space. Then let Ubuntu auto partition that 6gb

---

### Post by scoon on 2005-07-05
Hey there, 

Search the forums, there is plenty of info on how to do what you want. 

regards, 

scoon

---

### Post by mingus on 2005-07-05
*Now what I want to do is to load the Linux OS on the 20 GB hard disk drive after manually partitioning it in DOS.*

It is *not* a good idea to partition with DOS.  As Lunde indicates, you can delete that partition and let Ubuntu take the free space.  If you don't have anything on the 14GB, and you want to use that space for a partition shared between W$ and Linux, then delete it and create it new and format it as FAT32 from inside the Ubuntu install partitioner.

---

### Post by WildTangent on 2005-07-05
use the auto-partitioner, its MUCH easier than figuring it out yourself.

-Wild

---

### Post by Lunde on 2005-07-05
[QUOTE=mingus]It is *not* a good idea to partition with DOS.  As Lunde indicates, you can delete that partition and let Ubuntu take the free space.[/QUOTE]

Is'nt that what I wrote?
But you have a point about being better to use the Ubuntu partitioner

---

### Post by mingus on 2005-07-05
[QUOTE=Lunde]Is'nt that what I wrote?
But you have a point about being better to use the Ubuntu partitioner[/QUOTE]

Yes, I was emphasizing your suggestion *plus* doing it in the Ubuntu partitioner.  DOS (except for FDISK in a patched XP system) writes the table differently which can cause problems with other OS's and partitioners.

---

### Post by godsownman on 2005-07-06
Have understood what you all trying to say,

I should make 2 partitions .

I am comfortable with fdisk.  OR  when you say use auto partition how should i tell it to make 2 partitions of 6 Gb and 14 GB .

I make 2 partitions of  6GB and 14 GB and then when I start installing the OS I select AUTO PARTITION and then  let it do the rest right,

Please correct me if I am wrong .

Also  how do I configure the Internet. I have a Rockwell 56k External modem. 

Please help me .

Thanks/

---

### Post by Lunde on 2005-07-06
[QUOTE=godsownman]Have understood what you all trying to say,

I should make 2 partitions .

I am comfortable with fdisk.  OR  when you say use auto partition how should i tell it to make 2 partitions of 6 Gb and 14 GB .

I make 2 partitions of  6GB and 14 GB and then when I start installing the OS I select AUTO PARTITION and then  let it do the rest right,

Please correct me if I am wrong .

Also  how do I configure the Internet. I have a Rockwell 56k External modem. 

Please help me .

Thanks/[/QUOTE]
 If the disk is empty, create 1 fat32 with the ubuntu partitioner in the installation for sharing with windows, then let the Ubuntu installer auto create the partitions it needs on the remaining empty space of your drive

---

### Post by mingus on 2005-07-06
*Also  how do I configure the Internet. I have a Rockwell 56k External modem*

It would be a good idea to search the Forums for suggestions.  You first need to verify what chipset is in the modem, then find a driver, install the driver, and then configure the dial-up:

[https://wiki.ubuntu.com/forum/hardware/modem](https://wiki.ubuntu.com/forum/hardware/modem)
the scanmodem utility here will tell you what driver to use if it knows it, otherwise take a look at the following.  It is possible that the chipset is actually conextant.

[http://linmodems.technion.ac.il/resources.html#conexant](http://linmodems.technion.ac.il/resources.html#conexant)

and

[http://www.linuxant.com/drivers/](http://www.linuxant.com/drivers/)

and for configuring it after it is installed:

[https://wiki.ubuntu.com/DialupModemHowto](https://wiki.ubuntu.com/DialupModemHowto)

---

### Post by godsownman on 2005-07-07
Thanks everybody I shall try it out

---

### Post by godsownman on 2005-07-10
I was successfull at that.
Thanks everybody.

---

