---
title: "Install Freezes at 46% Complete"
date: 2007-12-05
forum: Installation &amp; Upgrades
---

### Post by fornews on 2007-12-05
I've tried two different CDs: one with Edgy and one with 7.10.

I was able to install Edgy initially but then wiped out the drive to install XP.

After installing XP with C and D partitions I wanted to also install Ubuntu in dual boot fashion.

I define 3 partitions (1 Gig swap, about 10 Gig for / and about 5 Gig for /home).
I proceed to install and it simply freezes the PC at 46% complete. 
I can move the mouse around but can't click on any icons to do anything so basically frozen.

I've tried deleting and re-creating the EXT3 partitions a few times with out success.

I'm hoping to avoid re-installing XP if possible, but if that is the only solution I can do that.

Any suggestions appreciated 

Jon

---

### Post by rexxxlo on 2007-12-05
sounds like bad memory try memtest i had a computer do that before and it was ecc or non ecc memory in a mobo that did not accept that type 

might be a bad stick ?  im just guessing though 

or a bad cd did you check the cd for defects i think that option is one of the choices when you boot from the live cd

try those and tell us what happens

---

### Post by fornews on 2007-12-06
Thank you rexxlo...

I ran the CD checker and it did fail checksum which surprises me a bit since I've used this same CD to install on a laptop some months ago and it did install a few days ago on the same PC that is hanging at 46% now.  

Assuming it is just the CD which version would you suggest i use to create a new CD ?

I'm currently running the memory test and so far after about 8+ hours no errors so I suspect that wont turn up any problems.

Again thank you !!

---

### Post by fornews on 2007-12-06
I've created a new CD using 7.10 desktop.

Ran the CD check with no errors.

Now the problem is different... saying I/O error saying either a CD problem or disk problem.


I'm thinking my problem has to do with the way it is formatted.

Circling back...

This PC has had Ubuntu installed at one point but I wiped it out while installing XP.
The XP install consumed the entire drive broken into two partitions C and D
I then used the partitioner in Ubuntu CD to break into a swap, / and /home.
I'm thinking this is my problem. More specifically how XP formatted the drive for C and D

I'm hoping for some confirmation on that idea before wiping out the XP install and starting over
or perhaps some other ideas on how to fix it.

---

