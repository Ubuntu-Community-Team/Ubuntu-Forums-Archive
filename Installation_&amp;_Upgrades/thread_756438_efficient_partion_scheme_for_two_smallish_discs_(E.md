---
title: "efficient partion scheme for two smallish discs (EEE PC 900)"
date: 2008-04-15
forum: Installation &amp; Upgrades
---

### Post by Rob Hodge on 2008-04-15
how would you setup partitions on a laptop with these specs?

 i'm going to be getting the new EEE PC 900 and installing ubuntu on it. i've never had to span two drives this small with an install and i'd like some suggestions. 

two internal drives, 
Primary 4 gig SSD
secondary 16gig SSD
2 gig ram. (max possible, not factory. relevant for suspend/hibernate support)

Cheers,
Rob Hodge

---

### Post by LeoSolaris on 2008-04-15
My suggestion would be to put /root on the 4 gig primary, and copy over your /home to the 16 gig secondary.That would give you some play room for applications, while maintaining the largest space for your docs, pics and movies. (Or what ever you put in your /home)

You will have to set your second partition to automount in your fstab, I believe, to use it immedately on start up. I am still learning that myself, and I have been toying with the idea of doing it to my hard drive to see how i like it.

Leo

---

### Post by Rob Hodge on 2008-04-15
yeah, but is 4 gig going to be enough or all the aplication space?

i'm thinking:
on 4 gig:
/boot
2 gig swap
maybe /lib?

on 16 gig
/

and /tmp and /var/tmp as tmpfs (held in ram, not stored on the disc

basically, my thought is if i put root on the larger disc and offload as much as possible to the smaller disc, i can use space more eficently and have room to grow.

any movies or media or such would probably get downconverted/imported on the full size laptop and put on a SD card or a USB stick.

any thoughts?

Rob hodge

---

### Post by The Cog on 2008-04-16
I would go for 5G root and 15G /home. I have all manner of rubbish installed here including gnome and KDE, 2 versions of openoffice, and have used 4.3G of my / partition.

---

### Post by Rob Hodge on 2008-04-19
> **The Cog said:**
> I would go for 5G root and 15G /home. I have all manner of rubbish installed here including gnome and KDE, 2 versions of openoffice, and have used 4.3G of my / partition.

i think you missed the whole post i made. 

there are two separate discs in this device. a 4 gig and a 16 gig.

i've also since found that the 4 gig is around 25% faster read time.

Rob Hodge

---

### Post by chapterthree on 2008-04-19
You could always LVM them together and then the issue resolves itself (I heard rumors that Hardy will finally support LVM at install, but you will want to double check that).

---

### Post by Rob Hodge on 2008-05-01
now i'm leaning towards:

on the 4 gig SSD drive (faster, more write cycles before sector damage)

100 mb /boot
2 gig swap
1.9gb /var

on 16 gig SSD (slightly slower drive, less write cycles before loosing sectors)
whole disc for /

how does that sound?

---

### Post by Hannu Leinonen on 2008-05-15
Could you post a tutorial how did you do it? I also have EeePC 900 and I'd like to achieve the perfect partitioning solution, but I'm quite newbie in Linux world. :)

Btw. Why are you having the swap partition on the 4gb drive? Wouldn't that be written often and it'd ruin the disk faster?

---

