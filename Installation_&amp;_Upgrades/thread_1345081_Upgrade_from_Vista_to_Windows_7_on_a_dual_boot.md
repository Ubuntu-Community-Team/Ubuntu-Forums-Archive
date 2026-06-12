---
title: "Upgrade from Vista to Windows 7 on a dual boot"
date: 2009-12-03
forum: Installation &amp; Upgrades
---

### Post by velorution9 on 2009-12-03
I just bought a laptop with Vista installed, and am receiving a free upgrade to Windows 7 in about a week. I'm planning on ending up with 7 and Ubuntu 9.10 dual booting. I have heard there are some issues with grub when installing Karmic on a Windows 7 system. 

My question is: would it make things any simpler to go ahead and divide the partitions and install Karmic now, before I upgrade from Vista to Windows 7? Or should I leave it until I can upgrade to 7, then install Karmic?

---

### Post by darkod on 2009-12-03
There are no issues with Karmic and win7. I am running them on both my desktop and netbook.
As for the other question, either way it should work fine. If you install Karmic now, during the win7 upgrade it will overwrite grub2 with its bootloader but restoring grub2 with the ubuntu cd is as simple as entering two commands. The choice is yours, either way it's fine.

---

### Post by velorution9 on 2009-12-03
So the boot issue is easy to fix, but it won't happen if I wait and install Karmic after upgrading to win7?

---

### Post by darkod on 2009-12-03
Correct. During the upgrade win7 will put its bootloader over vista's. Then when you install Karmic it put grub2 over win7's, it will detect win7 automatically and make the grub menu with options for ubuntu and win7.

---

### Post by wilee-nilee on 2009-12-03
If there is a recovery partition make sure you are able to remove it as it will be unusable for W7 it could be around 10 gigs in size.

I also wouldn't install Karmic until all of this is done. I would also get the ISO download of W7 and burn it to a DVD so that you have a install backup and a dvd to do recovery stuff if needed in the future. 

MS is supposedly going to re release the dvd/iso to thumb again soon, it had been removed due to open source code.

I was lucky that when I downloaded W7 the thumb loader was available so I have the DVD and a loaded bootable thumb. I have a net book so the thumb loader saved me some cash not having to buy a external DVD reader to install.

---

