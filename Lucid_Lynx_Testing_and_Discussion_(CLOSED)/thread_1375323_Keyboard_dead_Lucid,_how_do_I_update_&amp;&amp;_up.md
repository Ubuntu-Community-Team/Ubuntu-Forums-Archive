---
title: "Keyboard dead Lucid, how do I update &amp;&amp; upgrade?"
date: 2010-01-07
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by garvinrick4 on 2010-01-07
Have HP G71-34 Laptop with keyboard dead cannot update && upgrade can someone tell me how to accomplish this.   Cannot enter password in GUI and of course with out keyboard cannot use Terminal. Thanks.

---

### Post by nanog on 2010-01-07
Check to make sure your keyboard or xorg driver is not broken with a stable release live cd. 

If not, then open terminal in the live cd.

Mount your drive using commands similar to:

[PHP]sudo mkdir /media/lucid
sudo mount /dev/sda2 /media/lucid[/PHP]

(replace /dev/sda2 with name of drive, e.g. hda1 etc.)


Chroot into your mounted hard drive:

[PHP]sudo chroot /media/lucid[/PHP]


Update your install:

[PHP]sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade[/PHP]

---

### Post by garvinrick4 on 2010-01-08
Thank You Sir.

---

### Post by putxi on 2010-02-12
> **nanog said:**
> 
If not, then open terminal in the live cd.

Mount your drive using commands similar to:

[PHP]sudo mkdir /media/lucid
sudo mount /dev/sda2 /media/lucid[/PHP]

(replace /dev/sda2 with name of drive, e.g. hda1 etc.)



**nanog**, just to make sure and don't make things worse ...

I don't know if i have to do this step too? ... 'cos ...

Is it possible that running live cd 9.10, partitions from hd automatically get mounted on the FS?

If i go to PLACES on GNOME, and then COMPUTER, i see and access correctly the data of hd ... (maybe gnome has done it for me ...)

THEN, i shoud jump to directly try to chroot from my partition, isn't it?
I suppose have to choose the root partition, and not the one with all the data ..., isn't it?

Thanks in advance !!!

Regards,
jordi

---

### Post by ranch hand on 2010-02-12
Yes you need to chroot your / partition.

I just learned to do that in the last testing cycle.  It is nerve racking the first couple times.

Also handier than a pocket in a shirt.  Done correctly, you can run apt or aptitude and update/upgrade your system very nicely.

Had one install of 9.10-testing that didn't boot for 8 days.  An upgrade finally sorted it out.

---

