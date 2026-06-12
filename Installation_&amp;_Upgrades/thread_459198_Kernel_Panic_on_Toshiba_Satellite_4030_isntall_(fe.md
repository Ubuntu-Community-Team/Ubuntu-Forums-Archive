---
title: "Kernel Panic on Toshiba Satellite 4030 isntall (feisty)"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by Sherlok on 2007-05-30
Hey guys, I figured I would try to install ubuntu on my dated Toshiba laptop. To give you an idea of what we're working with I believe it's clocked at 300 mhz.

Anyway, I've burned the feisty desktop cd 3 times so far, all giving me the same error:

Kernel Panic - not syncing: VFS: Unable to mount root FS on unkown block(104,1)
Spurious ACK on isa0060/serio0. Some Program might be trying to access the hardware directly.

and it just repeats the spurious ack errors and flashes the caps lock light until i reboot.

When booting normally it sits at the splash (I'm assuming it's having the same problem), although I've been booting as : live noapic nolapic  as per something i read on these boards, to no avail.

Was just wondering if anyone had any idea what was going on, or a possible solution.

The laptop is a Toshiba Satellite 4030CDT btw, it's listed as working (although slow) on the ubuntu website.

Thanks :)

---

### Post by Sherlok on 2007-05-30
A small bump to see if anyone knows the answer :)

sorry if it's against the rules.

---

### Post by luzius on 2007-10-09
> **Sherlok said:**
> 
The laptop is a Toshiba Satellite 4030CDT btw, it's listed as working (although slow) on the ubuntu website.

Hi Sherlok,

How much memeory is installed? I only could successfully install Xubuntu on a Satellite 4030 **after** extending it with a 128MB chip (not so easy to find nowadays!).
Hope it helps

Luzius

---

### Post by gwbennett on 2007-10-09
Definitely recommend using the alternate install CD, not the live CD, for older hardware!

---

