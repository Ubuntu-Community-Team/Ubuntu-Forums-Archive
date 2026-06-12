---
title: "Is this a standard Linux partition setup?"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by jonelnz on 2007-12-15
Hi everyone, I´m new to Ubuntu but I wheelie wheelie love it.
Bought a new system at the beginning of the month which had Win doze Vista Ultimate installed plus the dreaded recovery partition.
Two days later (after creating rescue DVD&#347;) I installed Ubuntu as a dual boot option. Actually Vista was the option, Ubuntu is mandatory.

I have since removed Vista and the recovery partition. Ubuntu now has the whole drive.(500 GB)
My partitions are as follows:

/	primary
/home	primary
/usr	primary
swap	logical

Is this the way to set up a Linux system?
Sorry if I´m covering an old topic but if I reinstall will my /home and /usr partitions stay as are?

Thanks for any advice in advance
Oh and by the way, I love this place.

---

### Post by khurrum1990 on 2007-12-15
I never made a /usr partition. I only made:
"/"-root
"/home"
"swap"

---

### Post by SunnyRabbiera on 2007-12-15
there should be a main partition and a swap, yours looks just about right but if you can give us a screen shot of your partitions

---

### Post by rsambuca on 2007-12-15
It won't mess things up the way you have it, but there is really no need for a separate /usr partition for regular desktop use.

---

### Post by jonelnz on 2007-12-15
Thanks for the rapid replies guy´s, thought the compulsory waiting period was at least 2 days! :)

SunnyRabbiera
What´s the easiest way of taking a screen shot of my partition info?

---

### Post by logos34 on 2007-12-15
> **jonelnz said:**
> SunnyRabbiera
What´s the easiest way of taking a screen shot of my partition info?

sudo gparted

>Print Scrn key

---

