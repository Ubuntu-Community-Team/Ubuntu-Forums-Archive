---
title: "Kernel + Ramdisk Installer cannot read CD Rom"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Gruelius on 2007-05-28
Hey guys.
I tried to make the title relevant but its kinda hard considering what im trying to do.

Basically i have a lappy that refuses to boot from the PCMCIA drive which  is understandable. The specs are as follows.
533mhz Transmetta Crusoe CPU
128mb SD Ram 133mhz
40gb drive 
Et.c.

Anyway i setup the partitions like this
hda1 = 64mb boot
hda2 = 512mb swap (i plan to get 256mb ram for this lappy)
hda3 = 8gb root (For gentoo
Extended
hda5 = 6gb win98
hda6 = rest of space data partion.

Anyway ive gotten tired of trying to fix gentoo and the horrendusly slow compile times so ive decided i will install ubuntu fesity. Ive gotten the vmlinuz and initrd.gz files from [http://ftp.iinet.net.au/pub/ubuntu/dists/feisty/main/installer-i386/current/images/cdrom/](http://ftp.iinet.net.au/pub/ubuntu/dists/feisty/main/installer-i386/current/images/cdrom/) and i set grub to boot them from hda1 so that all the other patitions are free.

The installer loads perfectly however it tells me that there was a problem reading data from the cd rom, which is ovbious because the pccard icon on the laptops mainbar is off . What makes it worse is that when i tell it to check cd rom integrity it switches on the pcmcia card logo and can read the disk and verify its contents. 

When i go into the console i can see that it has found my drive correctly, i am now wondering as to how i can install it from the console maybe?

Any ideas would be appriciated.

Thanks
Julius

**Edit** Am i asking a bit much for 128mb of ram? i can run 98 lite for sure but id rather use an up to date OS that doesnt need a virus scanner :P i am prepared to use very lightweight apps like abiword e.t.c.

---

