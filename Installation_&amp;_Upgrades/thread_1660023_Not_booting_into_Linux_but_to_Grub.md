---
title: "Not booting into Linux but to Grub"
date: 2011-01-04
forum: Installation &amp; Upgrades
---

### Post by SkinnyMedic on 2011-01-04
After I installed 10.10 to my desktop it will only boot to a grub screen. Any ideas. It appears that it did not install a kernel. I have tried it twice and both times the same thing. I am just clicking on standard install. I formatted entire HD. So I am not trying to dual boot.

---

### Post by garvinrick4 on 2011-01-04
# Did you install grub to sda at install? 
# In live Cd (Ubuntu install cd and use try ubuntu)
# Open a terminal:
```
sudo fdisk -l
``` (lower case L)
Now find which sda# is yours.
# I will use sda1 for this:
```
sudo mount /dev/sda1 /mnt
``````
sudo grub-install --recheck --root-directory=/mnt /dev/sda
``````
sudo umount /mnt
```reboot to HDD

---

### Post by SkinnyMedic on 2011-01-04
Same thing. I have no idea what is wrong. I have install it on my laptop with no problems.

---

### Post by Bucky Ball on 2011-01-04
Installed from the same CD? Maybe give 10.04 LTS a go and see if you have the same problem.

---

### Post by SkinnyMedic on 2011-01-04
Tried that too  very confused :-)

---

### Post by wilee-nilee on 2011-01-04
So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags paste all the text in between.

---

### Post by garvinrick4 on 2011-01-06
Give post #6 wilee-nilee his boot script only takes a minute and he will give you the
correct procedure to fix boot problems.

---

