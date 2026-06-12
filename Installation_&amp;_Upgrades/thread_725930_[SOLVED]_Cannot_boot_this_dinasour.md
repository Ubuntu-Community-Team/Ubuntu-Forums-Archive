---
title: "[SOLVED] Cannot boot this dinasour"
date: 2008-03-16
forum: Installation &amp; Upgrades
---

### Post by sameera on 2008-03-16
Hi,
First of all, appologies for this not being a Ubuntu question persay.

I have a dinasour of a PC (P3, 733MHz, 196MB SD RAM) which I've been using as a media center using Geexbox (geexbox.org).  Well, today after watching a movie on it, I shut it down and left it for a while. Then came back and booted it again. It was at a pretty lousy place, so would have gotten moved around a bit by ppl walking about :)

Anyway, now the Geexbox hangs halfway down the load up. Thinking that my CD had gotten corrupt, i put in my old Ubuntu Live CD (5.10) and tried booting with it. I have an old PS2 keyboard on it, and when the Live CD runs, it hangs at the line
"input: AT translated set 2 beybord on isa0060/serio0"

I plugged in a USB keyboard and then, it hangs at the line before that:
"RAMDISK: compressed image found at block 0"

Now the PC has no hard disks. It ran geexbox completely from RAM and my DVD rom is only 1week old. I tried switching the sound card, vga and ram. but no luck. Anybody have any idea wt's wrong?

thanks.

---

### Post by Pumalite on 2008-03-16
I'd do a memtest. (several hours worth)

---

### Post by banewman on 2008-03-16
The pent3 is a few years old - pull the mem sticks out and then put them back in - it could just be a bad connection - I had that prob on my pent3 file server.
:)

---

### Post by Pumalite on 2008-03-16
Or dust them off.

---

### Post by sameera on 2008-03-16
> **banewman said:**
> The pent3 is a few years old - pull the mem sticks out and then put them back in - it could just be a bad connection - I had that prob on my pent3 file server.
:)

> **Pumalite said:**
> Or dust them off.

Hmm.. tried it but didn't work.
Could it be a memory issue? Cos' BIOS doesn't complain about it. And I have 2 sticks (64+128MB). Doesn't work with just one connected either.

---

### Post by tangibleorange on 2008-03-16
Well did you try the memtest as suggested above? It checks your RAM for errors, and can be accessed via the startup menu of the Live CD.

---

### Post by sameera on 2008-03-16
> **tangibleorange said:**
> Well did you try the memtest as suggested above? It checks your RAM for errors, and can be accessed via the startup menu of the Live CD.

Sorry, my bad. Didn't know how to run it. Thanks. It was the RAM. The 64MB has gone totally bust. And the 128MB is now showing up as 20MB. Guess there's no way to fix that.

Time to kiss this sucker good bye then.. No point trying to find RAM to work with this one. 
Thanks guys!

---

### Post by LifeInfusion on 2008-03-16
The BIOS usually doesn't do a comprehensive memory test, especially if there is a fast boot feature that shortens the boot test sequence. 

I'd double-check for card creep like banewman suggested as well (by reseating the memory firmly).

---

### Post by sameera on 2008-03-16
Yeah, will try thoroughly cleaning the slots etc. It's a 8 year old pc. It has served me well enough to warrent retiring :)
So no big heart breaks there.

Thanks for all the help!

---

