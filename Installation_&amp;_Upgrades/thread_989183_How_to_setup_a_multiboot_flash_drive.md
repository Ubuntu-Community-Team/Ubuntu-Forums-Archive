---
title: "How to setup a multiboot flash drive"
date: 2008-11-21
forum: Installation &amp; Upgrades
---

### Post by a412on on 2008-11-21
Hey everyone, I just got a 16 gig kingston data traveler flash drive, and my goal is to have it be able to boot up many different distro live cds. My overall plan is to have 8 gigs in windows for data storage, and split the other 8 gigs up between an ubuntu live cd, backtrack 3, DSL, and samurai. The first thing I have done is partition off the two 8 gigs, one labled DATA, and the other Live. From reading around, I tried to use Unetbootin to install the bootable live os'es on my drive. It works fine with one OS, for example ubuntu. What I read was to install one using that app, then put it all in a folder, and install another, and link them together in syslinux.cfg. The thing is that I can always get one to boot, but not the other. Does anyone know of a straighforward way of doing this? I am surely not the first person to try and make it happen.

---

### Post by lemming465 on 2008-11-22
You are going to have much better luck if you install each Linux distribution to a separate disk partition.  If you want Windows, Ubuntu, Backtrack, DSL, and Samurai on the same disk make 6 partitions (the linux variants can share a single swap partition).

---

### Post by xenolalia on 2008-12-30
Hi!

I am also trying to put together a multiboot flash drive (Patriot XT 16 GB), and I was wondering if anyone could give me any pointers as to how to use grub (or any other bootloader for that matter) to put ubuntu, super grub disk, dban, and . . . :? . . . maybe winpe/bartpe on my flash drive.  A quick disclaimer: I'm not a total linux-newbie, but I don't know much more than the very basics when it comes to booting or bootloaders.  :)

Thanks very much in advance!
Xenolalia

P.S. So far, I've tried both installing ubuntu to my flash drive and using the utility included in intrepid ibex to create a persistent live usb drive; both seem to work fine with my flash drive.

---

