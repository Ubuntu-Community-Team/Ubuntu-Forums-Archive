---
title: "Restore partimaged image (Solved)"
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by MistaED on 2005-12-02
Hello, 
I made a ubuntu partition on one machine about 4.5 gb and have imaged it with partimage. Now on my laptop I made a 35gb ext3 format with 1.5gb swap, then restored ths 4.5gb image on top of the 35gb partition. The problem I have now is that it still thinks it's only 4.5gb and has only 1.8gb free. How do I make ubuntu recognise the more space? The partition table is correct, 35gb primary ext3, 1.5gb swap primary as well.

Thanks
-MistaED

---

### Post by KermitJr on 2005-12-02
Aha... one a I KNOW how to answer....

Use a live CD with qtparted  (Knoppix has it). Run qtparted as root, select your drive, "Shrink" the 35GB partition to the minimum it will go and when that is done... resize it to the full size.  This will reset the geometry and recognize it properly.

I have a small 1GB image of another OS I do this for for others all the time.  Takes 20-30 minute to have everthing done.

KermitJr

---

### Post by MistaED on 2005-12-02
Cheers mate, but I already found another answer :)

The resize2fs command did what I wanted, but thanks for the suggestion anyway.

-MistaED

---

### Post by KermitJr on 2005-12-02
Glad you found a solution.  I'm pretty sure that the qtparted is just the gui version of resize2fs for ext2 partitions.

---

