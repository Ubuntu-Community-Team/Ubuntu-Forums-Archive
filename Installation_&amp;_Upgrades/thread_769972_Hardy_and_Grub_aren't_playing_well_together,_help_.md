---
title: "Hardy and Grub aren't playing well together, help please!"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by c00kie1000 on 2008-04-27
Let me start off by explaining my hardware situation:

1 160GB IDE HD
4 500GB SATA HDs set up as RAID5
nVidia 8500 card
2 IDE optical drives
4GB RAM

ok, so I had my box set up so that the 160GB drive was dual boot with Windows XP Pro on a 100GB partition, and the other 50someGB with Feisty (then Gutsy). Unfortunately, while fooling around on Gutsy, I did something nasty with the graphics card driver so my dual monitor setup stopped working.  The plan: do a fresh install of Hardy to clear up the mess I made with Gutsy.  Unfortunately, things went awry and when I tried rebooting after the install, GRUB told me it couldn't find the hard drive.  It was then that I realised that the IDE drive was no longer hdaXX but instead sdeXX.  So I modified the GRUB files to say hda instead of sde... and now I get GRUB ERROR 22.

Any idea how to make Hardy and GRUB play nicely?

also, to make sure that the filesystems were all OK, along with the partitions, I booted up using a Puppy Linux cd and mounted the filesystems (that's also how I got to a point where I could modify the grub device.map file).

thanks in advance!

---

### Post by fridayjones85 on 2008-04-27
I realize that this entirely sidesteps the actual question (and I apologize if you'd already thought of this), but perhaps it will suffice: 

Since you already have a working install of Windows, you could just install Hardy Heron using Wubi -- that way you wouldn't have to deal with complexities of configuring Grub for your RAID.

---

### Post by c00kie1000 on 2008-04-27
thanks! it's working now!

---

