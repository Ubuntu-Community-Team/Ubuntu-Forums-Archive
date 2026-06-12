---
title: "Gparted not working..."
date: 2007-11-15
forum: Installation &amp; Upgrades
---

### Post by MrSpiffdifilous on 2007-11-15
I just installed an old 40GB hard drive in my computer and I cant get it to work at all. I've tried Gparted and everytime I get errors. I get this one most:
> nick@nick-desktop:~$ sudo gparted /dev/sdc
======================
libparted : 1.7.1
======================
Unable to open /dev/sdc - unrecognised disk label.
Unable to open /dev/sdc - unrecognised disk label.
Unable to open /dev/sdc - unrecognised disk label.
Segmentation fault (core dumped)

I've gotten another error but I havent been able to emulate it.

I tried to fix the error in Windows but every time I tried to Initialize the disk it just stopped. I cant figure this out and its really bugging me. Any help would be appreciated.

---

### Post by Maddmaxx on 2007-11-17
Sorry Spiff, I have no answer, but maybe we have some hope if we're more specific... In my case I just added 2 brand new identical 320 GB drives, they are recognized in gparted as having an unrecognized label, and both 7.87 GB each, (going for raid for backup purposes). Well DUH! there is NO label, so how do we go about giving our drives a label?? Gparted seems to not be allowing either of us to partition our drives until we initialize and label them, what's the best way?

"Unable to open /dev/sde - unrecognised disk label."
"Segmentation fault (core dumped)"  <- error given when trying to give disk a label

Any help would be welcomed and appreciated!

---

