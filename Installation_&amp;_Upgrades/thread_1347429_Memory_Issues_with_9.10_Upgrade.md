---
title: "Memory Issues with 9.10 Upgrade"
date: 2009-12-06
forum: Installation &amp; Upgrades
---

### Post by shug0131 on 2009-12-06
Hi

I'm trying to upgrade from 9.4 to 9.10

It tells me that I need at least 2000MB of space on / .

Now I have set up separate partitions for /boot (45MB) /home (around 200GB) and / (5.5GB). The / partition is 91% full so there is no spare room.

How best to proceed? 

Do I have to repartition to give some space from /home to / ?  I tried to use gparted but it told me I couldn't unmount either partition. Do I have to create a boot-up disk with gparted on it to do this externally to running Ubuntu? If so where's a reliable place to get such an image?

What would be recommended as a better choice of partition sizes for the future?


Thanks Simon

---

### Post by phillw on 2009-12-06
> **shug0131 said:**
> Hi

I'm trying to upgrade from 9.4 to 9.10

It tells me that I need at least 2000MB of space on / .

Now I have set up separate partitions for /boot (45MB) /home (around 200GB) and / (5.5GB). The / partition is 91% full so there is no spare room.

How best to proceed? 

Do I have to repartition to give some space from /home to / ?  I tried to use gparted but it told me I couldn't unmount either partition. Do I have to create a boot-up disk with gparted on it to do this externally to running Ubuntu? If so where's a reliable place to get such an image?

What would be recommended as a better choice of partition sizes for the future?


Thanks Simon

Hi

5.5 GB for Ubuntu is pretty tight.

As a minimum I'd say 10GB for a Ubuntu install MINIMUM, that'd give you 9GB for Ubuntu & 1GB for swap.

To work out your swap area - as a rule of thumb... it is 1GB or the amount of RAM you have, which ever is the GREATER (512MB RAM = 1GB swap, 2GB RAM = 2GB SWAP)

Obvioulsly, if you can afford more room, then let the Ubuntu area have it - you don't, however need any more swap - regardless of your disk size !

Gparted is available as a boot CD from here --> [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

Choose CD or USB (If you have a usb & can boot from usb on your machine)

The details of GParted are here --> [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

No, you don't have to learn it all !! - Read the Intro to get an idea of it & have a look at any areas you want to.

As always, when partitioning disks - take a backup !!

So, shrink your /home by 5GB and grow your / area by the same amount - you'll have a happy little bunny after that :-)

Regards,

Phill.

---

