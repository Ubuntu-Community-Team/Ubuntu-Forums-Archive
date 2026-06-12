---
title: "Dapper sees raid0 as individual drives!"
date: 2006-08-01
forum: Installation &amp; Upgrades
---

### Post by wr0x2 on 2006-08-01
I have a Gigabyte GA-7N400 pro2 motherboard and recently bought two 320gb sata150 drives to put in raid0. I setup the raid in my bios, and formatted it using partition magic in windows. After booting from the dapper install CD, I start the install program. It sees my drives individually! How can I fix this?

By the way, my raid chipset is made by silicon image.

---

### Post by firefly2442 on 2006-08-01
I assume this is hardware RAID that you are trying to setup?  Have you checked to see that there are Linux drivers for the hardware raid?  If not, would you consider using software raid?  I've personally used software raid a few times and haven't had any problems.  Plus, you can mix and match different hard drive types and sizes for raid zero.  Hope you get it working. :)

---

### Post by wr0x2 on 2006-08-01
Well, ubuntu *was* seeing the first of my 320GB drives as a single volume around 600GB in size... However, after partitioning and installing it, I think it treats it as one drive, and the system does not boot to ubuntu, so here I am again in liveCD. This means that ubuntu has support for my raid. If anyone has a tutorial on how to manage raid 0 in ubuntu, please post it, because I'm getting confused here.

---

### Post by coln_panic on 2006-11-26
did you (anyone) ever get your ga-7n400 to boot a sata drive?  if so, how?!?  all the information i have seen online has basically said that it won't boot a sata drive, but it should since it has all the bios options and it only makes sense to be able to.  also, i installed to an external usb drive, and it can boot from that and then mount the sata (two drives in software raid 0) and it works fine, just in the POST and in grub the sata drives don't show up.

jay

---

