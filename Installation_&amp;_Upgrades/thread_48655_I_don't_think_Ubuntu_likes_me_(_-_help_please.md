---
title: "I don't think Ubuntu likes me :( - help please?"
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by Morcas on 2005-07-13
Hi, having recently received my CD's I set about installing Ubuntu. 

First up was the 'Live CD' using 'expert' mode as I have a copy of XP Pro running on my C: partition. Apart from being incredibly slow (2 plus hours and it's still trying!!) all seems to progress well. It recognises my video card and monitor, but then fails to load a GDI at the end with a xorg message telling me it 'could not find any screens' it also continually displays a message 'Disabling IRQ #18'  

I then tried to perform a full install, again using expert mode. This too is fantastically (after 1 hour only 13% copied!!) slow but it does progress. I am able to partition ok and it starts to install the base system but after several attempts and several different CD's the installation fails during the copy, not I might add, at the same point.

So right now I cannot get Ubuntu installed, neither can I run the Live CD :(

Any help please?

My Specs:

P4 2.4
MSI 865 PE-Neo 2 LS
MSI FX5600
512Mb RAM
Segate 120 SATA
WD 120 IDE
Sony DVD/CD
Plexstor CD-RW


The linux partitions have 40Gb for the installation.
Soundblaster Live Plat.

---

### Post by voidvoidpointer on 2005-11-27
You're screwed because the problem is caused by Debian's inability to correctly load data from CD-ROM in Plexstor drives.  The problem has been beaten to death in the forums, and the thick headed first responders suggest cleaning a brand new drive.

You're out of luck for now, or at least until there is a new release of Ubuntu that is based on a release of Debian that works correctly with Plexstor drives.

---

### Post by Leif on 2005-11-27
don't despair just yet. there are other methods of intalling ubuntu : [https://wiki.ubuntu.com/Installation](https://wiki.ubuntu.com/Installation)

---

