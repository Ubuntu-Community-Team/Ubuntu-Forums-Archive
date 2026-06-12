---
title: "Is there a way to clone my Desktop Xubuntu to my Laptop?"
date: 2014-09-11
forum: Installation &amp; Upgrades
---

### Post by ryanpantano on 2014-09-11
I have Xubuntu 14.04 installation on my desktop pc and i already changed the files, installed the programs, setup and configured everything to my needs. 

And now i want to have Xubuntu on my laptop also but i don't want to sit down by the laptop for next 5 days and setup everything again.

I know that i might wont be able to basically clone whole installation or partition because my laptop have different components in it.

But all the programs and setups, it takes a long time to do all over again.

Is there a way that i can somehow clone everything on my laptop?

---

### Post by Bucky Ball on 2014-09-11
Yes, there certainly is. [Clonezilla]("http://clonezilla.org/"):

Create image:
[http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/](http://rbgeek.wordpress.com/2013/04/14/how-to-use-clonezilla-to-backup-hard-drive-and-create-recovery-iso-image/)

Create recovery ISO:
[https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/](https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/)

Partition cloning step by step:
[http://cdonner.com/partition-cloning-with-clonezilla.htm](http://cdonner.com/partition-cloning-with-clonezilla.htm)

Create Live media (with pics):
[http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc](http://clonezilla.org/fine-print-live-doc.php?path=./clonezilla-live/doc/04_Create_Recovery_Clonezilla/01-clonezilla-boot-menu.doc#01-clonezilla-boot-menu.doc)

Clone the partition(s) you want to use (or the whole disk) to a partition on an external drive (or another internal one) and then clone the image to your laptop. TAKE NOTE: The partition you're cloning to must be the same size or larger than the original, cloned partition, regardless of if the image itself is smaller than it was.

I cloned the partitions on a hard drive to an SSD drive about ten months ago and it worked great.

Don't worry about the different components; when you boot Ubuntu on the laptop it should load the appropriate drivers, if it has them, and it will have plenty to get the machine up and running. It doesn't work like Windows. Most the drivers required are already in the Ubuntu kernel. ;)

---

### Post by fidelis2 on 2014-09-11
> **Bucky Ball said:**
> TAKE NOTE: The partition you're cloning to must be the same size or larger than the original, cloned partition, regardless of if the image itself is smaller than it was.
Yes, that's an important note.
If the destination PC has got a smaller hard drive than the source PC, I suggest to temporarily shrink the source PC's main partition (with gparted for example), so that it will fit on the destination PC.
(And at the end, enlarge the source PC's main partition again. This worked fine for me many times.)

P.S. to the original poster: in case you find Clonezilla difficult to use (which I do) and have a large enough external drive to move the copied drive image around, you can also use the GUI tool "gnome-disks" (inside the package "gnome-disk-utilities" I think) and create a 1:1 copy of your source PC's main drive with a few mouse clicks, and copy that back on the destination drive with the same tool. Please note then, however: gnome-disks doesn't do any compression, so the resulting image file will be the same size like your source PC's drive.

---

### Post by John F on 2014-09-11
It wouldn't help in your case, but I have three Macs running Ubuntu in Fusion VM's.  If there is a version upgrade I just do it on one and copy the VM to the others.

---

### Post by anika200 on 2014-09-11
not a helpful post, sorry.

---

