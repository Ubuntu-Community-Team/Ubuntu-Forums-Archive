---
title: "Live boot from hd or unetbootin help..."
date: 2010-04-25
forum: Installation &amp; Upgrades
---

### Post by chadraytay on 2010-04-25
I have an old laptop with a dead cd drive. Managed to get a minumum install of 9.10 on it. Now I'm trying to use that to boot the live cd so I can do a full install without downloading everything.

Tried unetbootin first, but it's not writing anything to grub.cfg so there's no option to boot the files it installs.

I have a spare partition I that I have copied the entire live cd to, and just need to know how to configure grub to boot that partition with the live cd. Its my (hd0,1) if that helps...

Unless of course someone knows the grub.cfg to boot a unetbootin live cd of ubuntu 9.10...:KS

---

### Post by C.S.Cameron on 2010-04-25
UNetbootin should be able to put the Live CD on your C drive without messing anything up.
Open Unetbootin, select "Diskimage" then select "Type: Hard Disk" and then "Drive: C:\" and then OK.
You should get the option to install Ubuntu the next time you boot.

---

