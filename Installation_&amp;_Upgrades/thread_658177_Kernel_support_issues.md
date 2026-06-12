---
title: "Kernel support issues?"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by helix on 2008-01-04
I can currently only boot into 2.6.17, this is the latest kernel I can boot into. Other kernels boot me into "Initramfs" prompt of busybox. Custom kernels do quite the same thing. I've also downloaded the latest alpha release of ubuntu and this also has issues.

Even though I can boot into 2.6.17 it still hangs unless I do an hdb=noprobe boot parameter. I have checked out all the threads and bug reports I can find on this and nothing seems to help or be completely relevant. 


I'm currently running 7.10 but using the 2.6.17 kernel. I would like to run 7.10 with a 2.6.23.12 kernel if I can get it all working as the 2.6.17 lacks features I want.


P4 2.6ghz Overclocked to 3.0
1.5gb PC3200 
Abit IS7-G motherboard
2x 160gb IDE
1x 80gb IDE

Thanks for the help.

---

### Post by sciencewhiz on 2008-01-04
what happens when you stop overclocking?

---

### Post by helix on 2008-01-04
> **sciencewhiz said:**
> what happens when you stop overclocking?

Tried what you said and nixed the overclocking and same thing.

---

### Post by helix on 2008-01-04
Bump. Anyone?

---

### Post by helix on 2008-01-06
> **helix said:**
> Bump. Anyone?

.

---

### Post by tgalati4 on 2008-01-06
Post the output of:

>dmesg

But only post the suspicious stuff, you can leave out the normal hardware detection.

---

### Post by helix on 2008-01-07
> **tgalati4 said:**
> Post the output of:

>dmesg

But only post the suspicious stuff, you can leave out the normal hardware detection.

How can I use this for my previous boot? I can't get to gnome with anything 2.6.17+.

I booted into 2.6.23.12 to load up the report with the errors ive been getting then i booted into 2.6.17 and dmsg it just shows my latest boot into 2.6.17.


btw, sorry my post took so long, I was flying back from Germany. :)

---

### Post by helix on 2008-01-09
> **helix said:**
> How can I use this for my previous boot? I can't get to gnome with anything 2.6.17+.

I booted into 2.6.23.12 to load up the report with the errors ive been getting then i booted into 2.6.17 and dmsg it just shows my latest boot into 2.6.17.


btw, sorry my post took so long, I was flying back from Germany. :)

.

---

### Post by helix on 2008-01-10
> **helix said:**
> .

.

---

### Post by Partyboi2 on 2008-01-10
try having  a look at the kern and dmesg logs in /var/log.

---

### Post by helix on 2008-01-10
> **Partyboi2 said:**
> try having  a look at the kern and dmesg logs in /var/log.

Thanks for the reply.


My kern log and unfortunately the dmesg log still only has the info for the last boot (the one I'm currently in). This pertains the the 2.6.17 kernel which boots relatively ok for me. I'm still unable to get the logs for the 2.6.23.12 boot. 

Any further ideas? Thanks, I'm  really desperate here. :(

---

