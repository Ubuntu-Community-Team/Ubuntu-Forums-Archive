---
title: "Laptop 800mb, 32mb.  Floppy and PCMCIA net installation?"
date: 2005-07-17
forum: Installation &amp; Upgrades
---

### Post by chris_andrew on 2005-07-17
Hi,

I would like to install Ubuntu on an old laptop.  I don't mind it running slowly, but would really like to install it on an 820mb hdd, with 32 megs of RAM.  Unfortunately I only have a floppy disk drive and a PCMCIA networ card.  Is an installation possible?

Thanks,

Chris.

---

### Post by damonw5 on 2005-07-17
[QUOTE=chris_andrew]Hi,

I would like to install Ubuntu on an old laptop.  I don't mind it running slowly, but would really like to install it on an 820mb hdd, with 32 megs of RAM.  Unfortunately I only have a floppy disk drive and a PCMCIA networ card.  Is an installation possible?

Thanks,

Chris.[/QUOTE]
 If you can, try to get another 32 megs of ram to bring it up to 64. That will make a huge difference.

820mb? That might be the one limiting factor.

You can try this, though: [http://ubuntuforums.org/showthread.php?t=29358](http://ubuntuforums.org/showthread.php?t=29358)

And there's a project for computers like yours. Nothing has been released yet, but here it is:
[http://www.ubuntulite.org/](http://www.ubuntulite.org/)

If I were you, I'd get some more RAM and run Damn Small Linux using a net-install like the one described here: [http://www.damnsmalllinux.org/network-install.html](http://www.damnsmalllinux.org/network-install.html)

Ubuntu is probably just too big for that machine :)

Good luck,
Damon

---

### Post by chris_andrew on 2005-07-17
Hi,

I tried DSL, but Tomsrtbt did not recognise my PCMCIA card.  I'll have a look at the link you posted, even if it is experimental.  Will let you know how I get on.

BTW, another 32megs is prohibitivly expensive.  Laptop cost me GBP12, mmory is GBP90!!!!!

Thanks,

Chris.

---

### Post by chris_andrew on 2005-07-17
Hmmm,

They need CDROM's :-(

---

### Post by mingus on 2005-07-18
[QUOTE=chris_andrew]Hi,

I would like to install Ubuntu on an old laptop.  I don't mind it running slowly, but would really like to install it on an 820mb hdd, with 32 megs of RAM.  Unfortunately I only have a floppy disk drive and a PCMCIA networ card.  Is an installation possible?

Thanks,

Chris.[/QUOTE]

Have a look at:

[http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge/talkback/1113587843](http://www.ubuntulinux.org/support/documentation/faq/upgrade-sarge/talkback/1113587843)
[http://www.ubuntuforums.org/showpost.php?p=120024&postcount=3](http://www.ubuntuforums.org/showpost.php?p=120024&postcount=3)

As already mentioned, the HDD and RAM are challenges.  But you may just be able to squeak by if you:
* install the server version and then add only what you need to get X and a lightweight windowing system like flux-box or windowmaker.  The technique is simlar to what is described at [http://www.ubuntuforums.org/showthread.php?t=49675](http://www.ubuntuforums.org/showthread.php?t=49675) but you cannot use xfce, so you'll have to use diff packages.
* pre-partition the disk with Knoppix or similar.  Create a 20MB ext2 partition, followed by a 64MB swap partition.  The former will get you around the 1024 issue and the latter should give enough to the installer to work.

Good luck.

---

