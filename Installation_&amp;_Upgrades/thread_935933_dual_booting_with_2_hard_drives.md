---
title: "dual booting with 2 hard drives"
date: 2008-10-02
forum: Installation &amp; Upgrades
---

### Post by ajlinzey on 2008-10-02
I have 2 SATA hard drives. I have XP on one and would like to put Ubuntu  8.04 on the other.  With the BIOS I can easily switch which I boot from. I did have Ubuntu  6.10 on the second drive and I remember during the install I had the option of putting grub on the windows drive or the Ubuntu drive. I put in on the ubuntu drive so my windows drive would be untouched by the ubuntu install.. Unfortunately menu.list for grub didn’t have the drives designated correctly and I had to manually fix it anytime I did an update. Was this because I had grub installed on the ubuntu drive and not the widows drive?if it matters the ubuntu drive is hd0 and the windows as  hd1.
-Andy

---

### Post by caljohnsmith on 2008-10-02
> **ajlinzey said:**
> I have 2 SATA hard drives. I have XP on one and would like to put Ubuntu  8.04 on the other.  With the BIOS I can easily switch which I boot from. I did have Ubuntu  6.10 on the second drive and I remember during the install I had the option of putting grub on the windows drive or the Ubuntu drive. I put in on the ubuntu drive so my windows drive would be untouched by the ubuntu install.. Unfortunately menu.list for grub didn’t have the drives designated correctly and I had to manually fix it anytime I did an update. Was this because I had grub installed on the ubuntu drive and not the widows drive?if it matters the ubuntu drive is hd0 and the windows as  hd1.
-Andy
Probably all you needed to do to fix your menu.lst problem was to change the line:
```
#groot=(hdX,Y)

```
That line should give your Ubuntu partition as (hd0,Y) since Ubuntu is on the boot drive. That is the line used to determine the Ubuntu partition when menu.lst is automatically updated with new kernels, so if it is incorrect, you will get incorrect menu entries for Ubuntu. But unless you post your menu.lst, I can't be sure that was the problem. :)

---

### Post by ajlinzey on 2008-10-03
I think this is the part of my menu.lst I need to change:

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)


to: 
#groot (hd0,0)

if the  ubuntu boot partition is the the first partition on the first hard drive that the bios sees.

---

### Post by artsci2 on 2008-10-04
Since most bios allow you to choose the boot device I avoid multiboot problems by disconnecting the Ubuntu drive to install windows and then disconnect the windows drive to install Ubuntu. Then I connect both drives and use the bios options.  As the system starts up I can choose the boot drive by pressing F12 when the bios promts me to. It's a hackey way to do things but it works.

---

### Post by ajlinzey on 2008-10-06
When I install 8.04 I wasn't give the option of where to put grub so Its on the windows disk but it all works fine now.
-Andy

---

