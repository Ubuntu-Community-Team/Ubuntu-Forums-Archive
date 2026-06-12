---
title: "Error installing LILO"
date: 2006-03-31
forum: Installation &amp; Upgrades
---

### Post by krakan on 2006-03-31
Hi Guys,

I've been playing around with using software RAID 0 to add a little bit more speed to my system. As it's just for learning to use Linux a bit more on, the insane lack of data security isn't a problem. 

I am installing Kubuntu 5.10 afresh on a PC I have acquired recently after doing an upgrade for someone. It's a fairly standard desktop PC with Intel motherboard, onboard everything and 2 x 40GB Seagate PATA Hard Disks.

I have (I think) correctly created my RAID partitions and used the multi disk module to define volumes for both the root filesystem and a swap area. I've formatted them and installed stuff on but at the (almost) last stage of the installation, when the time comes to install a boot loader, I can't get either LILO or GRUB to install! LILO fails 'with error 1' and GRUB also fails (I'm aiming to load LILO for no particular reason so I'm focussing on that right now..

Does anyone have a quick checklist I can use to make sure I'm doing everything right?

Two 40GB disks, each with a 35GB root (ext2) and a 5GB swap partition. Used md editor during installation to create two arrays, both RAID 0, therefore the system one is ~70GB and the swap ~10GB

I obviously don't know something fundamental about partitioning my disks/volumes for install Linux on, but I'm buggered if I know what it is, so could someone give me a clue?

Many thanks to anyone who can help!

---

