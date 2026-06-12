---
title: "Bizarre Dual-Boot behavior"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by tudsy on 2007-10-16
I realize this may be more of a Vista issue, but GRUB plays a very important role and has a problem of its own, so  any insight would be appreciated.

I have Vista and Ubuntu 7.04 installed on the same HDD (250GB SATA, x2 3600 2GB RAM, Gigabyte 690G motherboard) with the Vista bootloader on the MBR which either boots straight into Vista or loads GRUB on the Ubuntu partition if I want to boot there.  

The problem:  every two weeks or so when I try to boot into Vista it just hangs right after I select Vista from the bootloader menu.  On a blank black screen.  

The strange part:  if I select Ubuntu from the Vista bootloader, it takes me to GRUB, which stalls for about 90 seconds on the "Loading Stage 2" phase.  Then, when I finally get the GRUB menu and select the Vista/Longhorn bootloader, it takes me back the Vista bootloader screen and if I select Vista at this point, IT GOES INTO VISTA WITH NO PROBLEMS!!!!!!!!!!!!!!!!

I'm able to fix it by repairing using the Vista DVD, but this happens way too often for that to be fun.

Any advice?

---

### Post by rsambuca on 2007-10-16
Why don't you just install grub to the mbr then if it seems to work.

---

### Post by tudsy on 2007-10-16
I don't know if GRUB 'works' to load Vista.  It successfully loads the Vista bootloader which then successfully loads Vista (but only on the second time it is run).

It's like this:

Vista BL ==> Vista FAILS
Vista BL ==> GRUB ==> Vista BL ==> Vista  SUCCESS (if you call running Vista a success ;))

---

### Post by rsambuca on 2007-10-16
Grub works perfectly on my setup.  (XP, Vista, plus 5 linux distros).

---

### Post by tudsy on 2007-10-16
would i need to install the vista bootloader on the vista partition, or can grub just load it sraight away?  i.e., i just need to write grub to the MBR and that's it...

---

### Post by rsambuca on 2007-10-16
I think it should work if you just install grub to the MBR.

---

