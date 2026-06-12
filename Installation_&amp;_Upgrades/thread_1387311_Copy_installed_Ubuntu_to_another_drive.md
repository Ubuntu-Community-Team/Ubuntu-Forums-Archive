---
title: "Copy installed Ubuntu to another drive"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by neamhaol on 2010-01-21
My ubuntu will not read my sata hds. Is it possible to copy an installed ubuntu onto a differant drive?

If so, what is the best steps to take?

---

### Post by mörgæs on 2010-01-21
I will not say that it is impossible, but the fast and safe approach is simply to install Ubuntu on the new drive.

---

### Post by kansasnoob on 2010-01-22
> **neamhaol said:**
> My ubuntu will not read my sata hds. Is it possible to copy an installed ubuntu onto a differant drive?

If so, what is the best steps to take?

What do you mean by "it won't read your SATA drives"? That surprises me.

But the simple answer is yes. I've copied Ubuntu from one drive to another using nothing but Gparted but there are many things to sort out afterwards, like UUID's, grub, etc. Even drive designations can totally throw you!

I learned practicing on test machines and I made a lot of mistakes and had to wipe things and start over a lot. It's not something I'd recommend for a novice and the odds for data loss are always present even under ideal circumstances.

---

### Post by C.S.Cameron on 2010-01-22
sudo dd if=/dev/sda2 of=/dev/sdb2

Will copy the second partition of sda to the second partition of sdb.

I've used this a few times without problem.

You should run this from a Live USB or Live CD. I use gparted to know which partition is which

sudo dd if=/dev/sda of=/dev/sdb will write all of disk sda to sdb.
Sdb should have at least as much capacity as sda.

You can use gparted to adjust partition size as required.

---

### Post by amac777 on 2010-01-22
You can also just copy all the files over onto the new drive and then install grub on that drive so it will boot by itself. That way you won't be limited to the same size partition. Perfect for moving your installed system to a bigger hard drive etc. Let me know if you need more detailed instructions.

---

### Post by C.S.Cameron on 2010-01-22
"The essence of dd is you get an exact byte-for byte copy, including any fragmentation or other errors that exist on the original partition. But if it works as /dev/sda2, it should work after being exactly copied to /dev/sda1.

The essence of cp is that you get all the correct files, but re-written without fragmentation in a new filesystem. The new filesystem should be a copy of the old filesystem.
dd copies bytes, cp copies files."
--SilverBear

If you use cp do not forget the -a switch so that hidden files are copied.
Both should be run from a Live CD or Live USB.

---

