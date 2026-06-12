---
title: "Moving an installation from RAID to single drive"
date: 2021-11-13
forum: Installation &amp; Upgrades
---

### Post by Hex on 2021-11-13
Hey guys,

I've had nothing but problems with two SSDs that used to work fine for the last year, but now one of them keeps failing all the time, degrading the RAID 1. Since this is my third reinstall of my server and I'm facing the same problem (smart control says both drives are fine), I decided to buy a new SSD and if possible, move the working OS (from the degraded RAID) to the new SSD. Is this possible, or do I have to reinstall everything again...?

---

### Post by ActionParsnip on 2021-11-13
I'd suggest doing a clean install to the new drive, then restore your user data from your backups.

---

### Post by Hex on 2021-11-13
> **ActionParsnip said:**
> I'd suggest doing a clean install to the new drive, then restore your user data from your backups.

I know that's the best thing, I just didn't feel like reconfiguring a ton of software on the server one more time. OK then, are there any tools to migrate data from one installation to another or is doing it from scratch, again, the best option? :)

---

### Post by ActionParsnip on 2021-11-13
You can use disk mirroring tools but with the array being flakey you might get a bad copy. Something like dd in a terminal will do it or something like this
[https://www.tecmint.com/linux-disk-cloning-tools/amp/](https://www.tecmint.com/linux-disk-cloning-tools/amp/)

---

### Post by Hex on 2021-11-13
> **ActionParsnip said:**
> You can use disk mirroring tools but with the array being flakey you might get a bad copy. Something like dd in a terminal will do it or something like this
[https://www.tecmint.com/linux-disk-cloning-tools/amp/](https://www.tecmint.com/linux-disk-cloning-tools/amp/)

But essentially I will be creating a single drive system, which will be running in a degraded state all the time. Thank you, I appreciate the help - just wanted to check if there is an easier way!

---

