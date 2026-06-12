---
title: "Kernel Upgrade from terminal"
date: 2006-11-05
forum: Installation &amp; Upgrades
---

### Post by nprosper on 2006-11-05
Hello everyone,
I am new to this Linux stuff, and I am loving it so far. Last night I was at a friends and he was helping me install VMWare Player. I had issues and we were manually upgrading my kernel from the terminal. It required the CD to be in the cd rom of course and it was taking a very long time, and when I checked later it failed, possible because i shut the lid on the laptop.
Anyways I am looking for the command, I cant get ahold of my friend and I do remember some of it. Well one part. We ran something that had "" and -c any ideas?
Thanks!
-Nick]
(*,)

---

### Post by az on 2006-11-05
> **nprosper said:**
> Hello everyone,
I am new to this Linux stuff, and I am loving it so far. Last night I was at a friends and he was helping me install VMWare Player. I had issues and we were manually upgrading my kernel from the terminal. It required the CD to be in the cd rom of course and it was taking a very long time, and when I checked later it failed, possible because i shut the lid on the laptop.
Anyways I am looking for the command, I cant get ahold of my friend and I do remember some of it. Well one part. We ran something that had "" and -c any ideas?
Thanks!
-Nick]
(*,)

Vmware player is in the multiverse repo - you do not need to recompile the kernel.

To fix a broken package run

sudo apt-get -f install

and it may or may not tell you to run

sudo dpkg --configure -a

---

### Post by nprosper on 2006-11-05
Thanks a lot for the tip there!

I actually got ahold of my friend. Here are the commands:

gksu "update-manager -c"

gksu "sh /cdrom/cdromupgrade"

---

