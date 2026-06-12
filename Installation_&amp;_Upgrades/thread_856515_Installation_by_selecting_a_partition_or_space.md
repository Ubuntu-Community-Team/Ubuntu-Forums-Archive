---
title: "Installation by selecting a partition or space"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by BetaByte on 2008-07-11
I'm once more installing Ubuntu due to earlier problems and yet again I faced the installer that asks me to choose where I'ld like to install Ubuntu. The thing is that the options it presents are not realy all the options I could get, so it forces me to go and use the manual partitioner prety much each time.  That why I'm actually wondering why that fase couldn't just be worked out like this :


[SIZE="3"]Where would you like me to install Ubuntu?[/SIZE]

**1) Displaying all the devices that can be used for it.**
a) HD 1 (IDE1,hda,Earth,500GB)
b) HD 2 (IDE2,hdb,Venus,320GB)
c) HD 3 (sATA,sda,Mars,1,5TB)
d) HD 4 (USB key,sdb1,Pluto,8GB)
e) ...


**2)** After having selected a previously mentioned letter (a-e). 
It displays the **current usage of that device (partitions, unallocated free space, etc.)**. 
By selecting either a part of the device of the whole thing (like in gParted) it prompts you with ...

**2.1 a whole device**
a) use the whole drive
b) liberate [dropdown options] of the free space
c) use [dropdown options] of that device

**2.2 a part of a device**
a) use that part
b) liberate [dropdown options] of the free space
c) use [dropdown options] of that device


**3) Display the selected way and press next to agree.**


[dropdown options]
* remove the partition and return to the devices
* use xxx % of that device/space
* use xxx GB of that device/space
* use it all


Instead of giving you just some options.
I'm not so sure that this is the right place to post this, so if I'm mistaken please forward me to the right area.

---

### Post by Pumalite on 2008-07-11
Maybe you have a bad burn. Manual always gives you all the options you want. Even better is to get Gparted Live CD and prepare your partitions ahead of time. Ubuntu is remarkably easy to install.

---

### Post by Rallg on 2008-07-11
Pumalite is correct. It is a good idea to pre-partition (for example, by using Gparted from the live CD). Then, when you install, the manual choice lets you do what you need to do. Of course, you need to know how to use the manual installation options.

---

