---
title: "configure grub menu"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by PLIACHAS PASCHALIS on 2008-02-28
i had two winxp operating systems on the first hard disk and linux on the second hard disk. i changed the motherboard and i had to reinstall the xp systems. i set the second partition hidden and i installed the first xp. i made visible the second partition and hidden the first one so i installed the second xp system. i used the live cd to enable the grub and i finally did it. the problem is that in the grub menu the second entry about the first xp system doesn't work.
below is the piece of the menu.lst file

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Pro
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda8
title		Windows NT/2000/XP (loader)
unhide (hd0,5)
hide (hd0,7)
root		(hd0,5)
savedefault
makeactive
chainloader	+1


below is the image of gparted where you can see the partitions on the first disk. xp are installed on the dev10 (working os) and on dev8 (not working)
below is the image link
[http://img218.imageshack.us/img218/6476/screenshotdevsdagpartedsj3.png](http://img218.imageshack.us/img218/6476/screenshotdevsdagpartedsj3.png)

---

### Post by dstew on 2008-02-28
I am not sure that Windows will function if booted from a logical partition, such as your /dev/sda6

---

### Post by PLIACHAS PASCHALIS on 2008-02-28
> **dstew said:**
> I am not sure that Windows will function if booted from a logical partition, such as your /dev/sda6

Sorry my working xp os is on the sda10(see image). My not working Xp Os is on the sda8 which is hidden. 
Thanks for your reply

---

### Post by zvacet on 2008-02-28
I´m not expert,but if you have windows on sda8 than root should be pointed to it.In short try with root(hd0,7).

---

### Post by Pumalite on 2008-02-28
Make sure your XP is in a primary partition.
Maybe I'm wrong, but I see 2 primaries and the a series of logicals inside an extended. According to you, your XP is not on the primaries I see.

---

### Post by PLIACHAS PASCHALIS on 2008-02-29
> **Pumalite said:**
> Make sure your XP is in a primary partition.
Maybe I'm wrong, but I see 2 primaries and the a series of logicals inside an extended. According to you, your XP is not on the primaries I see.

1.i'll try to change the root
2. yes all of them are in logical partitions

---

