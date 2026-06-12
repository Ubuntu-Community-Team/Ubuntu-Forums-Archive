---
title: "Image three installs"
date: 2019-04-01
forum: Installation &amp; Upgrades
---

### Post by tomtom447 on 2019-04-01
Hi everyone, first post here.
I have four computers, one with Ubuntu with a custom kernel to work with some equipment and a set of applications. I would like to image the drive to the other three computers so I don’t have to compile everything again. I’m kinda embarrassed to say that I have never done this before and need some advice.

Can someone direct me in how to achieve this? Thank you.

---

### Post by TheFu on 2019-04-01
dd, ddrescue, clonezilla, partimage, fsarchiver are all tools for something like this.

OTOH, this would be the perfect time to validate those backup/restore/disaster recovery procedures that every company would require.  

If the computers don't have very similar GPUs and use proprietary GPU drivers, best to remove those first.

---

### Post by joelgsus on 2019-04-01
Hey Tomtom447, it's not too difficult to clone your master hard drive these days, I just did it last week and i used clonezilla ([https://clonezilla.org/downloads.php](https://clonezilla.org/downloads.php)) 
1. download the clonezilla iso and burn into a usb
2. boot from usb into clonezilla 
3. follow menu instructions,
it's as simple as this. you may want to search youtube ([https://www.youtube.com/watch?v=41tTudaQb0I](https://www.youtube.com/watch?v=41tTudaQb0I))
good luck, 
FYI. make sure your other 3 hard drives are same size or bigger of master drive.

---

### Post by tomtom447 on 2019-04-01
Thank you both, I will get on it when I get to the lab and keep you all posted. BTW yes the systems are identical, so I shouldn’t have any issues with that.

---

