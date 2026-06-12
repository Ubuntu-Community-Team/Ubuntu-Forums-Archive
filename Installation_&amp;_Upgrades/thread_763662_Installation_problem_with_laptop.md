---
title: "Installation problem with laptop"
date: 2008-04-23
forum: Installation &amp; Upgrades
---

### Post by owend on 2008-04-23
I recently changed computers; this one has Vista HP. I used to be able to use Ubuntu 7.10 on the old, desktop, XP-based computer, but the new one won't let me install. It locks up after at most 90 seconds into the install routine.

I've tried all sorts of boot options (at F6), having scoured the forums: best result from pnpbios=off; with the quiet splash deleted, I generally get as far as USB configuration messages. Once, with irqpoll as well, it got as far as the black screen with the Gnome timer in the middle then locked up. 

The disk worked before, so that's not it; I think it's hardware but what? Any clues welcome!

Acer Travelmate 7510, AMD Turion, NVIDIA GeForce Go 6100 chipset, 1Mb RAM, 50Mb+ spare on hard drive.  

Thanks in advance for ANY ideas! :confused:

---

### Post by Partyboi2 on 2008-04-23
Have you tried  the alternate cd?
[http://releases.ubuntu.com/7.10/](http://releases.ubuntu.com/7.10/)

---

### Post by Pumalite on 2008-04-23
Have you tried the Alternate CD?

---

### Post by owend on 2008-04-24
Thanks for suggestions: now downloaded alternate, burned to CD, same problem!

---

### Post by Ayuthia on 2008-04-24
Have you tried booting with noapic?

---

### Post by tachuela on 2008-04-24
Have you tried all_generic_ide at the boot line?

---

### Post by beta.tester on 2008-04-24
> **owend said:**
> I recently changed computers; this one has Vista HP. I used to be able to use Ubuntu 7.10 on the old, desktop, XP-based computer, but the new one won't let me install. It locks up after at most 90 seconds into the install routine.

I've tried all sorts of boot options (at F6), having scoured the forums: best result from pnpbios=off; with the quiet splash deleted, I generally get as far as USB configuration messages. Once, with irqpoll as well, it got as far as the black screen with the Gnome timer in the middle then locked up. 

The disk worked before, so that's not it; I think it's hardware but what? Any clues welcome!

Acer Travelmate 7510, AMD Turion, NVIDIA GeForce Go 6100 chipset, 1Mb RAM, 50Mb+ spare on hard drive.  

Thanks in advance for ANY ideas! :confused:

Have you tried with the option:

/noapic /nolapic

kind regards

---

### Post by owend on 2008-05-06
Thanks for all your suggestions: all tried in vain!

BUT I'm writing this with a Ubuntu boot!!!

Secret: Heron 8.04 (Amd64 version) downloaded a treat, live disk perfect, installed cleanly and first time. It dualboots with Vista (in case!). Only hitch so far is a Canon scanner which needs a driver I think.

So, if you've got an AMD processor, try Heron 8.04 - no biosbug problems.

Good luck.

---

### Post by Disker on 2008-05-07
Hi Owend,

I'm having the same problem with my laptop.  I have the AMD processor and I've tried both the x386 and AMD64 versions to no avail.  I still get a long list of errors after the initial boot screen and language prompt.  

Is there more than one AMD version of Ubuntu?  i could only find the one for AMD64.  My chip is the AMD mobile.  Not a great chip but I thought it might be a nice laptop with Ubuntu on it.  

Any suggestions appreciated at this point because I'm dead in the water at this point.

Bob

---

### Post by Pumalite on 2008-05-07
Post your complete specs.

---

### Post by owend on 2008-05-08
Hi, Disker: I used the download named ubuntu-8.04-desktop-amd64.iso, burned to DVD as iso. It worked live and as install disk. Good luck!

---

### Post by owend on 2008-05-08
Disker etc: sorry, should have said details. I've an Acer Travelmate 7510 laptop, AMD Turion 64 processor, 1GB RAM, 80GB HD; set 13GB unallocate space in Vista before installing. NVidia GeForce Go 6100 chipset. I burned to DVD, but iso is 680MB, so might go on a CD, I was just trying to avoid ANY problems!

---

