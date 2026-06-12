---
title: "GRUB problem...."
date: 2004-12-07
forum: Installation &amp; Upgrades
---

### Post by innerlogic on 2004-12-07
I've been trying to install ubuntu on my computer, but after the install ends and reboots my computer, it stalls on Grub... it does not give me an error (i've left it on for over 10 minites or so to see if it would... it did not), but it would stall on "stage 1.5", I also have windows, and the only way i can get there now is to use the live CD and boot into the first partishion from there.

I've been trying for the past few hours to fix everything, anyone have any ideas?

---

### Post by Nathanael Reveal on 2004-12-08
The problem is likely that the BIOS can't read all of the GRUB files to get GRUB started.

To help sort this out I've got a few questions:

[list=1]
[*]How big is your hard drive?
[*]How big does your BIOS think you hard drive is?
[*]What disk geometry is reported by the BIOS for your drive? This is usually reported in units of Cylinders, Heads, and Sectors or CHS. There is also an additional "mode" value usually Large, LBA, or Normal.
[/list]
Did you do the default install and have Ubuntu automatically partition the drive?

---

### Post by innerlogic on 2004-12-08
[QUOTE=Nathanael Reveal]The problem is likely that the BIOS can't read all of the GRUB files to get GRUB started.

To help sort this out I've got a few questions:

[list=1]
[*]How big is your hard drive?
[*]How big does your BIOS think you hard drive is?
[*]What disk geometry is reported by the BIOS for your drive? This is usually reported in units of Cylinders, Heads, and Sectors or CHS. There is also an additional "mode" value usually Large, LBA, or Normal.
[/list]
Did you do the default install and have Ubuntu automatically partition the drive?[/QUOTE]

My HDD is 60 gig's, my BIOS's reads all 60 gigs right

I'm going to check the Geometry right now, but it should be noted that a few weeks ago i could use all distros right (with the exact same hardware) and only with the last few distros i've tried had this happen... so i have NO idea whats going on.

EDIT:
It should also be noted that my BIOS has LBA on already.

also, i've already tried LILO, only to have it hang on the "L" flashing.

---

### Post by Nathanael Reveal on 2004-12-09
I'm curious, what happens if you change the BIOS detection of the hard drive to "Normal" instead of LBA?

---

### Post by innerlogic on 2004-12-09
[QUOTE=Nathanael Reveal]I'm curious, what happens if you change the BIOS detection of the hard drive to "Normal" instead of LBA?[/QUOTE]

i get error 17, I think, i have to do it again, but i already tried it.

---

### Post by programgeek on 2005-06-24
Hi.  This thread was never solved, or at least I haven't seen it solved.

Does anyone here know a link to an Ubuntu FAQ on this?  Or is there another post that solved this?

I have the symptom of my grub doing
"Loading stage 1.5

Loading Please Wait..."

And then it just stalling.  :grin:  What mistake could I be making here?  I could go up and bring my HD geometry, but I'm a human being, my name is just a cover. ;)

Also, the person who finds the answer to my problem gets a cookie.  :razz:   Thanks!  :)

---

