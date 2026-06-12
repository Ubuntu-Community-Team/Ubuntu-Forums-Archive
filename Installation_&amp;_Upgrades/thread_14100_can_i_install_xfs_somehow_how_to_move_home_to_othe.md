---
title: "can i install xfs somehow? how to move home to other partition?"
date: 2005-02-04
forum: Installation &amp; Upgrades
---

### Post by T31 on 2005-02-04
when i try to install it, it says grub doesnt work with xfs bye bye ](*,) 

anyone know how to?

and by the way i would like to know as well how to move my home directory to a different partition

thx in advance

---

### Post by friez on 2005-02-05
try making your boot partion ext2 and install grub there. leave the rest as xfs. 8)
to move your home dir boot from a livecd mount the partion the old-home dir is on the partion  for the new-home dir
example 
 ```
mkdir /mnt/old
           mount -t xfs /dev/hda1 /mnt/old
``` and
 ```
mkdir /mnt/new
           mount -t xfs /dev/hdb1 /mnt/new
``` 
then ```
mv /mnt/old/* /mnt/new
``` 
and edit fstab too tell it which pation your home dir is on
```
/dev/hb1 /   home    xfs     defaults    00
``` 
hope this helps :mrgreen:

---

### Post by T31 on 2005-02-08
im now short of space in my hd, how large should be that boot partition?
and one last thing do i have to do something to be able to write to the hd using the ubuntu live cd, i think i remember under knoppix u cant write right to ur hd booting from the livecd
thx

---

### Post by friez on 2005-02-12
about 100 mb for boot

---

### Post by T31 on 2005-02-13
\\:D/  it does work great! thx!

---

