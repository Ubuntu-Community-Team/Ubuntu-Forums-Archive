---
title: "Could not create ext3 partition during install"
date: 2007-06-16
forum: Installation &amp; Upgrades
---

### Post by LondoMollari on 2007-06-16
hi.  i've been desperately trying to install ubuntu 7.04 for five to six hours now, but there seems to be a problem during the partitioning process.

I have a brand new Samsung SpinPoint 500GB drive that i am trying to install to, but i get the message "could not create ext3 partition". At first i thought maybe there is some conflict with my other drives, so i disconnected all of them... still doesn't work..

by the way, i tried to partition to fat32 using gparted.. and i worked right away, so there seems to be a specific problem with creating ext3 partition (ntfs also works)

my system is MSI K9N SLI Premium motherboard with an AMD Athlon 64 X2 Dual 4200+ w. 1024MB RAM and a Nvida 7950 graphics card

any help is much appreciated :-)

---

### Post by bigken on 2007-06-16
have you tried the gparted live cd to create your partitions

---

### Post by bulldog on 2007-06-16
Download the gparted live cd version,it's much easier to use,
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)
Burn it to a disk and boot from it.

---

### Post by LondoMollari on 2007-06-16
wow! quick response!  ..no i have'nt tried that, but i was able to create an ext3 partition using partition magic under winXP. only problem is, even if i have an ext3 partition ready before I start the installer, the installer wants to re-format the drive..and that is where the problem starts... also i could mention that the swap partition is always successfully created)

i am starting to think that maybe the new drive is faulty... do you think maybe this could be the case?

---

### Post by bigken on 2007-06-16
the installer should give the option to manually partition your drive

---

### Post by bulldog on 2007-06-16
> **LondoMollari said:**
> wow! quick response!  ..no i have'nt tried that, but i was able to create an ext3 partition using partition magic under winXP. only problem is, even if i have an ext3 partition ready before I start the installer, the installer wants to re-format the drive..and that is where the problem starts... also i could mention that the swap partition is always successfully created)

i am starting to think that maybe the new drive is faulty... do you think maybe this could be the case?

And better not use PM to create your ext3 partitions,it's seems not the best program to use for Linux partitions.

---

### Post by floke on 2007-06-16
IMO the feisty partitioner is crap. The problem you might have is that the partitioner mounts the drive in the middle of the process and can't then complete the process because the drive is mounted (clever eh?). I would use the alternative installer - its foolproof (famous last words) in this respect, since it doesn't mount the drive. If you want to make the partitions first then use the live cd of gparted or the version on rescue disk ([www.sysresccd.org](www.sysresccd.org)) - or use the liveCD of edgy, since the gparted on there works fine. But personally i would use the alternative installer - I've given up on the Feisty LiveCD.

---

### Post by LondoMollari on 2007-06-16
thanks stevie k .. that sounds like a good explenation. I just started downloading the alternate cd... I'll report back to tell if it works!

---

### Post by floke on 2007-06-16
I'm sure it will.

---

### Post by bigken on 2007-06-16
I would try the  gparted liveCD 1st its a two minute download and also a very handy disc to have ;)

---

### Post by LondoMollari on 2007-06-16
yep... alternate cd worked like a charm

---

### Post by bigken on 2007-06-16
cool :p

---

