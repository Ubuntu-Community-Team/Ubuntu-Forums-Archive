---
title: "Ubuntu does not detect the presence of cdROM"
date: 2011-06-08
forum: Installation &amp; Upgrades
---

### Post by chinc on 2011-06-08
Dear Ubuntu Users,

I have just had my Ubuntu 10.04.2 Luci installed under my Windows OS. Things seem to be fine until I find out next that my copy of Ubuntu does not detect the presence of the cdROM which installed the software itself on my desktop machine.

I have tried searching high and low for clue in this forum, tried all the recommended tricks to find out at last that there is no cdROM listed under my DISK UTILITY and when I input the following comman, 

sudo lshw -class disk -class storage I only happened to see my hard drive  and some USD drives being listed.

Also, Brasero Disc Burner does not detect the presence of a cd/ DVD rom devices.

Appreciate if someone can kindly assist me.
Many thanks in advance.

Regards,
Chinc

---

### Post by jwcalla on 2011-06-08
There was a thread about a similar problem yesterday or the day before.  If I recall, it was a driver problem with a SATA3 controller and when the poster hooked his DVD drive into a SATA 2.0 port things were fine.

1) Is this a CD or DVD drive?
2) Is it a SATA or IDE connection?

---

### Post by chinc on 2011-06-10
Your suggestion indeed works! Fantastic. Thank you very much.

---

