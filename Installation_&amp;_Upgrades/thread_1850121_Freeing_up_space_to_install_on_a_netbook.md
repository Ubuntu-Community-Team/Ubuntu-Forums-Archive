---
title: "Freeing up space to install on a netbook????"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by xxxBorrachoxxx on 2011-09-25
So, my sister's netbook got messed up and I'm trying to install ubuntu since I've heard good things about the os. Plus, theres no way for me to install win 7 right now. So I got it loaded up on a usb and its all fine but I need to free up 2.5 gigs of space to install it. I don't care about the previous data on the hd. Is there a way for me to format it or at least free up some space in the mean time??

Thanks.

---

### Post by OpenJacob on 2011-09-25
Use Gparted to do that, you find the drive and reformat it to ext3 or 4. Or you can install and choose to use the entire disk which should be default for netbook installs, but it's not.

---

### Post by xxxBorrachoxxx on 2011-09-25
Thanks for the quick reply. I'm on the netbook right now(don't know how people can use these things) and just using the explore ubuntu function. I downloaded the ubuntu 10.10 netbook version btw. I'm looking for the gparted program but I can't seem to find it. Would there be a way to just delete a few files from the previous partition in the mean time to free up the space?

---

### Post by Hakunka-Matata on 2011-09-25
for gparted: System>Administration>Gparted, Partition Editor
or from a terminal:
```
sudo gparted
```

---

### Post by drawkcab on 2011-09-26
You're gunna need more than 2.5 gb to install ubuntu.

---

### Post by xxxBorrachoxxx on 2011-09-26
I went to Gparted and the only drive in site was the usb. Seems like a hardware problem cause the little hd cylinder light only comes on when booting(w/o the usb stick) and the error message I got was : OPERATING SYSTEM NOT FOUND. Also my sis told me she didn't have many things on the netbook and that there should have been more than 2.5 gigs of free memory.

---

### Post by xxxBorrachoxxx on 2011-09-26
double post

---

### Post by Hakunka-Matata on 2011-09-26
```
sudo lshw -C disk
sudo fdisk -lu
sudo sfdisk -luS
```
Those three commands should show more information about the hard drive in that netbooik.

---

