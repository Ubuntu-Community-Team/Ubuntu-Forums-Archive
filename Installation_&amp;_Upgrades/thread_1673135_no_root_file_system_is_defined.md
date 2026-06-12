---
title: "no root file system is defined"
date: 2011-01-21
forum: Installation &amp; Upgrades
---

### Post by beowulfk on 2011-01-21
I'm trying to install ubuntu on d partition i deleted, which now is "free space" but its giving me that error

so im guessing i have to click on add, what do what i click on? primary? beginning? end? ext 4 im guesing and which mount point?

im installing it on d portition which i deleted and is now free space, i have windows 7 on c, \

im so confused

---

### Post by Quackers on 2011-01-21
Just to be sure, how many primary partitions are currently in use on your system? A screenshot of gparted window, or the disk management screen in Windows would clear it up, if you are unsure.

---

### Post by beowulfk on 2011-01-21
3 2 are for system restore and the third one is c, i deleted my d one

i want to know if I should add my "free space" that i got from d to c and just "install along other operating systems" on my c but is that even possible?

but how will i later add 4gb for "swap space" everything so confusing to me

primary/logical - choose logical
Beginning/end - choose beginning
file system - ext4
mount point - /

thats what i got, but then

what is boot loader? which one do i choose?

/dev/sda5 (one i just created or one of the 1-3 which is vista/7/7

there's also a dev/sda ata (500.1gb)
it also says you have no selected any partitions for use as a swap space

---

### Post by Quackers on 2011-01-22
Are you using gparted at the moment? Please post a screenshot of your /dev/sda drive. Does your pc have just one hard drive?

---

### Post by beowulfk on 2011-01-22
> **Quackers said:**
> Are you using gparted at the moment? Please post a screenshot of your /dev/sda drive. Does your pc have just one hard drive?

Yea, I just got it, thanks a lot though.

---

### Post by Quackers on 2011-01-22
Hokey cokey :-)

---

