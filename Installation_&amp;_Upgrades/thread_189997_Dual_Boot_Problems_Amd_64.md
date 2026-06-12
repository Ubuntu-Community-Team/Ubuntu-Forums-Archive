---
title: "Dual Boot Problems/ Amd 64"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by hookooekoo on 2006-06-05
Hello All,

My computer is an Opteron Dual Core with 1 IDE and 2 SATA drives.  

On Drive sda1 I have a 30 gig partition with Windows.  I load up the live cd and install Ubuntu and it takes up partition #2, #3 for mount and swap.  Everything seems to install fine but after reboot it asks for the system disk and doesn't boot.

Now the only way I can get into windows is with a boot disk, and my ubuntu install seems hosed.  I would love any advice that can help me to fix this.

I have tons of experience with gentoo, but very little with ubuntu.

---

### Post by Travisty on 2006-06-05
When you say mount, are you referring to the root partition "/" ?

---

### Post by hookooekoo on 2006-06-06
[QUOTE=Travisty]When you say mount, are you referring to the root partition "/" ?[/QUOTE]

Yes.

After I install I get the message

Reboot and Select proper Boot device or Insert Bood Media in selectedBoot device and press a key.

Does Ubuntu install grub by default?  I tried to boot into live cd and run grub, but it didn't work.

I have

hda
sda   (This has 3 partitions.  #1- Windows, #2 /, #3 swap)
sdb 

pls help

---

