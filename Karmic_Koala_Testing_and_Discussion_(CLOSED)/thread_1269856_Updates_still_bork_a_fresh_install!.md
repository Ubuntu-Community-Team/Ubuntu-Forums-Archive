---
title: "Updates still bork a fresh install!"
date: 2009-09-18
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by kansasnoob on 2009-09-18
I just did a fresh install of Karmic Alpha 6, partly to see if some of the problems with the install gui's were fixed (they were), then I ran through a few reboots, ran update-grub, and several other things.

All was cheery until I ran updates through the Update Manager - no partial upgrade - nothing to be removed - **so beware!**

Basically still a hard hat zone :(

---

### Post by kansasnoob on 2009-09-18
> **kansasnoob said:**
> I just did a fresh install of Karmic Alpha 6, partly to see if some of the problems with the install gui's were fixed (they were), then I ran through a few reboots, ran update-grub, and several other things.

All was cheery until I ran updates through the Update Manager - no partial upgrade - nothing to be removed - **so beware!**

Basically still a hard hat zone :(

Well, even before installing any updates, I've now found that installing 'nautilus-gksu' breaks the next boot. No idea why!

Of course now I have to try and back that out (I'll use recovery mode and follow with terminal + net) and then see what happens.

It's testing so I must "rinse and repeat"!

---

### Post by Squonk07 on 2009-09-19
> **kansasnoob said:**
> 

Basically still a hard hat zone :(

Definitely. :( I did a clean install of A6 the day it came out, and all was good until the reboot, where I got a bunch of symlink errors and a stalled boot. I couldn't get to a command prompt no matter what I tried. Oddly, one time in every twenty or so it would boot, seemingly randomly.

I reinstalled from the exact same .iso, and while I got the same symlink errors (I still get them) it now boots every time.

Weird. Here's a suggestion to anybody reading: If you run multiple OSs, **remember to update GRUB** on your first bootup of A6. A6 won't list your other OSs by default, so if you end up like I did the first time and didn't update GRUB you'll be McScrewed.

---

### Post by kansasnoob on 2009-09-19
Hmmm, previous to the big crash a few days ago, I had been installing Karmic with no bootloader and then adding Karmic to an existing grub legacy on either Jaunty or Mint Gloria.

Anyhow this time I'd decided to play with Grub 2 some more just to start learning about editing the new grub menu files, etc. Well, what I discovered was that I just couldn't get Karmic to boot after I'd run update-grub to have os-prober find my Win XP, Jaunty, and Mint.

So I finally removed the entire grub folder from Karmic by mounting it from either Jaunty or Mint using nautilus-gksu to open the boot folder as administrator (a word of caution here - opening Nautilus as root can wreck things if you're not very, very sure what you're doing), and afterwards restored grub to Mint and added Karmic to Mints menu.lst:

> title		Ubuntu 9.10, kernel 2.6.31-10-generic (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-10-generic root=UUID=05aed494-04f9-43c6-abd3-de8626294e1f ro   quiet splash 
initrd		/boot/initrd.img-2.6.31-10-generic
savedefault
boot

title		Ubuntu 9.10, kernel 2.6.31-10-generic (recovery mode) (on /dev/sda3)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.31-10-generic root=UUID=05aed494-04f9-43c6-abd3-de8626294e1f ro single 
initrd		/boot/initrd.img-2.6.31-10-generic
savedefault
boot

All seems well after a dozen or so reboots!

I still plan on playing with Grub 2 more in the future though. But for now I'm having fun:)

---

