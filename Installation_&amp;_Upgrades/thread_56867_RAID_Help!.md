---
title: "RAID Help!"
date: 2005-08-14
forum: Installation &amp; Upgrades
---

### Post by Sam0r on 2005-08-14
Im setting up a fileserver, for home use (To store all my music, movies etc.. also going to use it to host my website which will be nfs mounted to a different machine).

I've got 4 hdd's in there, all 40gb (same make/model etc). 
I want to set it up so theyre all in RAID-0 so i have a virtual 160gb hdd.

I know i can set up raid on install, but the problem is, i cant install from the CD and have all 4 hdd's in there at the same time!

So how would i go about setting this up?

---

### Post by nad on 2005-08-14
This is silly. Failure of any one drive would mean an end to your filesystem. And as a raid0 needs to be built with all drives present, there is no way to do this.

Why would you possibly wish to do this? If anything, you should build a raid1 for your website as this will give you redundancy protection.

There is very little perfomance penalty from having four separate filesystems, and certainly they may be configured to be transparent and seemless in operation.

---

### Post by Sam0r on 2005-08-14
I'm not really botheerd about if i lose any data, Its just really somthing to play with. My website will never get finnished (and anyway its just a testing setup).

I want raid0 so i get the max attainable space from the hard drive setup.

I was thinking i could boot from a floppy disk set and install via the web? Like suse does?

---

### Post by nad on 2005-08-14
Point taken. Play away!

As far as maximum usage, there is overhead in setting up the raid0. Whether it is more or less than separate filesystems I don't know. You can certainly tweak filesystems to your specs.

Yes, you can install from floppy sets. Search for several threads here regarding this.

---

