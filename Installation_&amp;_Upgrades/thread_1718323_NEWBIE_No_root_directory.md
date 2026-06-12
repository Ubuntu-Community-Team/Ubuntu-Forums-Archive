---
title: "NEWBIE: No root directory"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by jakefish on 2011-03-31
Hello folks, I am brand new to Ubuntu and I love it !!!

I am currently running it from a usb pendrive, However when i try and install it to my harddrive, it says 'no root file system is defined, Please correct this from the partitioning menu'

So I have been in Gparted and formatted the hard drive to EXT3, but cant seem to mount it or indeed 'define a root file'

Please help, I will forever be in your debt


Jakefish

---

### Post by Sean Moran on 2011-03-31
> **jakefish said:**
> Hello folks, I am brand new to Ubuntu and I love it !!!

I am currently running it from a usb pendrive, However when i try and install it to my harddrive, it says 'no root file system is defined, Please correct this from the partitioning menu'

So I have been in Gparted and formatted the hard drive to EXT3, but cant seem to mount it or indeed 'define a root file'

Please help, I will forever be in your debt


Jakefish
If you can, try and start out with a plain old Live-CD.  That makes it so much easier.

If not, please explain exactly how you created a Live-USB on your pen-drive, and there maybe someway to tackle the problems, however a working Live-CD makes everything so much easier to work out, if you can do it.

--o0o---

First and foremost, is your Live-USB booting into a GUI and the "root file-system" problem encountered on the Installation part?  I reckon not, but just to check.  I assume the problem pertains to a badly built USB distro, but could be wrong.

---

### Post by jakefish on 2011-03-31
Thanks for your prompt reply, 

I have the same problem when i run from cd too.

I made the usb, with the online builder.

---

### Post by jakefish on 2011-03-31
First and foremost, is your Live-USB booting into a GUI and the "root  file-system" problem encountered on the Installation part?  I reckon  not, but just to check.  I assume the problem pertains to a badly built  USB distro, but could be wrong.


I am not completely sure where it is booting into, but my pendrive appears in Gparted as /dev/sdb

My hard drive appears as /dev/sda

It is not mounted either ??

John

---

### Post by Sean Moran on 2011-03-31
> **jakefish said:**
> First and foremost, is your Live-USB booting into a GUI and the "root  file-system" problem encountered on the Installation part?  I reckon  not, but just to check.  I assume the problem pertains to a badly built  USB distro, but could be wrong.


I am not completely sure where it is booting into, but my pendrive appears in Gparted as /dev/sdb

My hard drive appears as /dev/sda

It is not mounted either ??

John
I am jumping to conclusions here, but something reminds me that the "no root filesystem defined" happened to me just once before when I was part-way through the installation, and at the disk partitioning stage, and forgot to set one partition as my root (/) partition, and probably the same might happen if I'd not had a SWAP partition.

If this is the part where the problem happens, make sure to have two partitions available.  One needs to be around 8Gb for your Linux root (/) partition and the other needs to be around double your computer's RAM, but 2GB is plenty unless you're some kind of mad scientist on the graphic design side of things.

Not enough information to know for sure, but it seems you're at the part of the installation where you go to manual disk partitioning, and just need to setup a couple of partitions for root (/) and SWAP to let the installer know where to finish the installation.

Please let me know if I'm wrong.  It's rather a guess, but that error message is what set me onto this posibility.

---

### Post by jakefish on 2011-03-31
Thanks again for your help,
I used the create partition directory option in Gparted, then it installed fine.......until I rebooted and for some reason it had disconnected my drive from the raid, I just reconnected, careful not to erase the MBR and it is all working fine.

Now to explore, any essential apps i should have ??

---

