---
title: "How do I go about installing Feisty on my apparently not-so-normal PC? sil3112a..."
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by Buchardt on 2007-04-22
Hi

I just downloaded Feisty yesterday, and spent all day yesterday trying to get it onto my PC.
I have an Asus A7N8X Deluxe motherboard with a sil3112a raid controller. My setup is:

2 SATA disk on the sil3112a raid controller
1 IDE disk attached normally (extra disk, i'd prefer not to install on it)

I downloaded the alternate install CD so I can install with LVM for my SATA disks. I want to install on the SATA disks because the IDE disk is like an old extra disk I have.
First I installed with LVM and used GRUB. The installation went fairly fine, and the IDE disk was unused. When I then wanted to boot my system, GRUB gave me an error 17: cannot mount selected partition
So, after installation, my system was useless. But I remembered that GRUB could have problems with the sil3112a controller, so I tried to install LILO instead. But the installer halts when at 50% trying to install LILO, so that ain't successfull. It seems buggy, but I'm not sure?!? Maybe I'm doing something wrong here.

Can you guys help me, telling me how to get my system up and running on the SATA disks? Or am I forced to install the main system on the IDE disk?

---

