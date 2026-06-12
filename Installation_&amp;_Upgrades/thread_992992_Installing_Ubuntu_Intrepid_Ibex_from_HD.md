---
title: "Installing Ubuntu Intrepid Ibex from HD"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Databit on 2008-11-25
Ok I couldn't stand the flashing Wifi light caused by Intrepid Ibex on my Dell Latitude D620 so I bought a new laptop.
First problem is the DVD Rom connector is bad. If the DVD Drive is inserted the system gives me the BusyBox reconciliation errors people can't seem to resolve. Guessing it's a mobo error. 
While I wait for a new laptop I still want to play with my brand spanking new laptop with a nice big 17" screen but I can't seem to get ubuntu to install. 
I put my old harddrive in which has Intrepid and it boots fine. Kinda sluggish because it wasn't installed using this hardware but I could probably manually reconfigure everything and have it going. But I'm lazy. It's still impressive that it booted perfectly just doing a hardware swap from an Intel based laptop to a AMD based. 

So I tried using live USB. Made the disk using the wizard. When I boot I get Syslinux and a boot: prompt. If I press <enter> it says it can't find kernel: linux. I type /casper/vmlinuz and it begins to boot but hangs with something to do with root filesystem vfat (typing this from work and don't have that laptop handy. Either way doesn't work. 

I resized my swap partition from 6 gigs down to 4 so I would have an extra 2 gigs which I formatted as FAT16 then extracted everything from the II 64 bit ISO and flagged as the bootable partition. Reboot grub loads then my regular ubuntu install loads. 
How do I make the 2 gig partition work as my boot? Or is there some command I can type in at grub to have it load from the files on the 2 gig partition ? 
Or am I going about this all wrong?
Any tips are appreciated

---

### Post by Databit on 2008-11-25
Another thing to note is that I don't have Windows anywhere in my house. So anything involving using wubi or ubootin won't work for me. Plus I have a working ubuntu so should be better anyway

---

