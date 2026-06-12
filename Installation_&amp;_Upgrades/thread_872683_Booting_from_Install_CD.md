---
title: "Booting from Install CD"
date: 2008-07-28
forum: Installation &amp; Upgrades
---

### Post by jnewkirk on 2008-07-28
Want to migrate on my old PC to linux to sort out my learning before making a complete shift. So do not want a dual boot set-up - all backed up and moved to my new PC with files etc so ready to re-format the drives and have a linux box. 

I 'feel' like I am booting from my install CD, but I always end up at Step 3 - Prepare partitions with no prompt for 'erase entire disk'. 

Have tried to change my boot order - think I am doing it right - but always end up in the same place.

---

### Post by Pumalite on 2008-07-28
You probably have the Alternate CD. Download the Live CD from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
(Desktop Edition)

---

### Post by jnewkirk on 2008-07-28
And I cannot do it from the alternate CD?

---

### Post by Pumalite on 2008-07-28
The Alternate CD is a text based installer only. What you want is the Live CD, I think. If you are ready to install, then you can use the Alternate CD. If it's not functioning well; burn a new CD after doing md5sum on the iso. Burn at 4x or less. Do not use CD-RW

---

### Post by snowpine on 2008-07-28
You should choose "guided installation--use entire disk" if the option appears; if not, you can use a partition editor to delete your old partitions and prepare the way. Since you say it is an old PC, which install method you should use is a function of how much ram you have. If you have at least 384mb, you can use the Live CD, which includes the Partition Editor. The Alternate CD (for which I would recommend 256mb of ram) does not have a partition editor, so if necessary, you should burn a separate GParted (PARTition EDitor) live cd. Hope that is helpful info.

---

### Post by zvacet on 2008-07-28
@ **jnewkirk**

> And I cannot do it from the alternate CD?

Of cource you can.When you come to the partition stage select manual way and you will see option to erase entire disc.After that make your partitions :

1. root = 10GB             mountpoint /
2. swap = 2xram
3. home = rest of free space  mountpoint /home

---

### Post by jnewkirk on 2008-08-04
Ok, here's the deal. I boot with the install CD and get the install screen. Step 1 I choose English. Step 2 I choose my timezone. Step 3 I choose my keyboard. Step 4 I get a box that says 'starting up the partitioner' and the a Prepare Partitions page with Device Type Mount point Format? Size Used and then a box for, I assume, my drives. Below the box are buttons for New partition table new partition edit partition delete partition and undo changes to partition.

Thing is, I cannot access any of these operations, and no drive data appears in the box. 

There is no place to manually erase and format. 

My first thought is that I have not booted from the CD, but to the best of my knowledge I have done as required when booting to boot from the CD. But ... ??

---

### Post by jnewkirk on 2008-08-04
By the way, it is a celeron 2.88gHz with 1gig of RAM.

The whole point of this is to learn, so I can subsequently only run linux, so this is all great feedback. 

Cheers

---

### Post by Pumalite on 2008-08-04
[https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD](https://help.ubuntu.com/community/Installation#Installation%20using%20the%20Alternate%20CD)

---

### Post by Sef on 2008-08-04
> 1. root = 10GB mountpoint /
2. swap = 2xram
3. home = rest of free space mountpoint /home

Number 2 is not necessarily correct.  If you have 1 GB of ram or more, then 1 GB swap is the most that is needed.  If you have 2 GB ram or more, then swap is optional.

---

### Post by Sangdrax on 2008-08-04
I had the same problem installimg from the Live USB stick, I didn't see the hard drives. When you start the LiveCD, in the end, before clicking install, open a terminal. 

#sudo passwd (to set the root password)
#sudo -s (to become root permanently)

#modprobe ide-generic

Now, I think you will be able to see the other install drives (at least it worked for me). 

Now you can start the install clicking the Install program.

---

