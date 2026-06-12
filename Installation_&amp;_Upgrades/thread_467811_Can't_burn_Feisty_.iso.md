---
title: "Can't burn Feisty .iso"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by Edward The Bonobo on 2007-06-08
I've downloaded the .iso, but keep getting errors when I try to burn to CD-R.

My CD-RW drive usually works fine.  I'm using decent quality, 700MB disks.  I have 250+MB on my HD.

I've tried the following methods:
[LIST]
[*]Right click/ Burn .iso
[*]Gnomebaker
[*]Graveman
[/LIST]
Any ideas?  Thanks.

---

### Post by viciouslime on 2007-06-08
Go to a terminal and navigate to the folder with the iso in it then type "md5sum <iso's filename here>" you will get the md5sum of the iso. Then compare it to the list of md5sums below:

50f3655fbcbdba9746d4b05ad8705b0b *ubuntu-7.04-alternate-amd64.iso
ff0cc7c9ed5157f0ff8c0f2213973f49 *ubuntu-7.04-alternate-i386.iso
a2b159599b69cea51371eee1ec5feda6 *ubuntu-7.04-desktop-amd64.iso
e296e3468358789904097fc8df29609a *ubuntu-7.04-desktop-i386.iso
8a1099f5fa8eaf4ee295bf0087c8b03a *ubuntu-7.04-server-amd64.iso
cf462501e2dc1b82b96dfc497a0404a2 *ubuntu-7.04-server-i386.iso
e016f1e3322848af98d01eae2688568c *ubuntu-7.04-server-sparc.iso

If yours doesn't match with the correct one above for whichever iso you have downloaded, then the iso is corrupt and you will have to redownload it :)

---

### Post by Edward The Bonobo on 2007-06-08
I'll chack that - but I've just managed to burn one on a W******s machine, so my immediate problem has gone away.  I'd still like to think I can get my Ubuntu machine up to W******s standards, though.;)

---

