---
title: "Install 10.04 on CD from the DOS prompt?"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by livingdog on 2011-01-12
I was given an old DELL GX50, 800 MHz clock, and bought 512 (2x256) SDRAM DIMMs. I believe the HD was wiped b/c when I finally figured out to put in a Windows bootup disk in the A: drive it said that it didn't recognize the configuration of the C: drive.

Ok, so I ran FDISK from the A: and it created a partition. The floppy ran ATAPI so I have CD support. However, when I put the Ubuntu 9.04 (I have 10.04 working on a 450 MHz machine - beautiful, but slow) nothing happens.

I can see the CD, do a directory command, but it won't autorun.

What file will run the installation from DOS so that I can have a faster machine with 10 on it.

*thx in advance!*

---

### Post by mikewhatever on 2011-01-13
Not quite sure why you want the installer launched from dos. Have you tried booting from the cd yet?

---

### Post by ronnielsen1 on 2011-01-13
> Your computer's BIOS must be set to boot from CD first; otherwise, Windows will just load up again. To get into the BIOS settings, you usually have to press one of these keys during boot-up: Escape, F1, F2, F12, or Delete. Usually your computer will tell you which key to use.[B]

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[/B]

---

### Post by Mark Phelps on 2011-01-13
> **livingdog said:**
> 
I can see the CD, do a directory command, but it won't autorun.

What file will run the installation from DOS so that I can have a faster machine with 10 on it.

*thx in advance!*
It simply will NOT autorun from inside DOS because it needs a graphical environment to run -- which you don't have in DOS.

Besides, you don't want it to autorun from inside Windows either, because then, it will prompt you to install INSIDE Windows -- which you probably also don't want.

The only option that will be useful is to boot from the CD and install that way.

---

