---
title: "Move Ubuntu to another drive"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by bendilts on 2011-03-11
I have a laptop with an 80GB SSD and 500GB HDD. I currently have Windows installed on the SSD, and a 400GB data partition for Windows on the HDD. I set aside 100GB on the HDD to try out Ubuntu, and I'd like to make it my primary OS and switch it over to the (much) faster SSD.

How could I go about getting my Ubuntu setup moved over to the SSD? I have a 120GB USB hard drive I can use if necessary for getting through it.  I'm not worried about saving the contents of that 80GB drive, as it has no meaningful data on it, but I do not want to have to reinstall and reconfigure Ubuntu if possible.

---

### Post by oracle2b on 2011-03-11
It could be as easy as using gparted to copy your existing Ubuntu install from the 100gb to the SSD assuming of course you're using less than the 80GB of sorage on the 100GB partition.

---

### Post by Hedgehog1 on 2011-03-12
bendilts,

If you can shrink the 100 gig Ubuntu partition down to **under 80 gigs** (resize in gparted), you could then copy the partition to the SSD using any of these:

* dd
* ddrescue
* clonezila
* gparted (partition copy)

In any case you will need to do an update of grub afterward, but that part is simple.

You can ***later*** make the 500 gig drive an ext4 drive, and then make it your '/home' directory, giving you what would appear to be a single 580 gig drive.

***The Hedge***

:KS

---

