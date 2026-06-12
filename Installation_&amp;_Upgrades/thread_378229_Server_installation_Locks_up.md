---
title: "Server installation Locks up"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by sontek on 2007-03-07
Hey, I'm trying to convert my OpenSUSE 10.2 file server over to Ubuntu Edgy Eft Server and it locks up at 69%.  I checked the md5sums and ran "check disk" from the installation menu and its fine (and it actually installed just fine on my other server)  so the disk isn't bad. But I can't figure out why its locking up at configuring ubuntu-minimal 69%.   

The part thats broken is debootstrap: Setting up ubuntu-minimal (1.30) ...

it just doesn't get past that part.

---

### Post by tguthrie on 2007-07-07
Damn, I'm having the exact same problem on an AMD Athlon64 3200 (Socket939) system with a DFI Lanparty RDX200 motherboard. The only suggestions I've seen (in my google searches) has been to unplug any USB devices you may have, and one other guy had a few drives hooked up for a raid, when he unhooked the raid drives from the system, the installation worked.  I also have a raid hooked up, but it is 8 drives, and very inconvenient to disconnect all of them!  That will be my last ditch effort I guess.

Unfortunately, there is no information on the install debug console either, it simply stops after the following output:

debootstrap: Setting up ubuntu-minimal (0.119) ...

I've tried booting with 'install noapic nolapic', this resulted in a kernel panic (I also tried them individually).

I've tried booting with 'install pci=noacpi', this results in the same freeze at configuring ubuntu-minimal at 69% of the installation.

---

