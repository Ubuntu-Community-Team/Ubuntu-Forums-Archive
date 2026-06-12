---
title: "Purple Screen After Fresh Install"
date: 2019-07-09
forum: Installation &amp; Upgrades
---

### Post by Rayaldi on 2019-07-09
Hi there, I tried installing Ubuntu 18.04.2 to my laptop that already has Win10 x64 on it.

Here's my laptop Spec (Lenovo G405s)
CPU: AMD A8-5550M
GPU: Radeon HD 8550G (Integrated) + Radeon HD 8570M
RAM: 8 GB
HDD: 500 GB with the current partition:

/sda1 FAT32 1GB boot (FreeDOS)
/sda2 PBR_DRV NTFS 1GB (Windows Recovery)
/sda3 NTFS 250GB (Windows System)
/sda4 Extended
- /sda5 NTFS 187GB
- /sda6 EXT4 25GB < the one I choose to Install

I flash the ISO to FlashDisk from my Win10 using Rufus, and can use the Live/Demo Mode from the FlashDisk normally. Although it took a long time to scan the drive (I believe it's because of my old HDD), the installation went successful.
The option I choose from installation is Minimal Installation, not ticking the install hardware driver or whatever it is and not connected to any network.
When I tried to boot to Ubuntu from Grub, it went purple screen, I decided to Shut Down after 15 minutes of purple Screen. [s]I can boot to windows normally by choosing the FreeDOS option.[/s]

I already tried using *nomodeset* option, but it still result the same. I also tried using the recovery option but it's still the same purple screen.
What should I do to fix this problem? Thx in advance.

Edit: after I tried to reinstall ubuntu again, it seems everything I choose from grub will result in purple screen.

---

