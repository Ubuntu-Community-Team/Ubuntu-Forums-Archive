---
title: "No sound for  ALC883"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by Krzysiaczek99 on 2011-02-12
I installed Ubuntu 10.10 Maverick on desktop system with mother board GA M61PME-S2 with the sound Realtek chip with codec ALC883 and sadly no sound.  This board has 3 jacks and SPDIF support 

Than i tried 

sudo gedit /etc/modprobe.d/alsa-base

and I added the line

options snd-hda-intel model=MODEL

with following models

3stack-dig    3-jack with SPDIF I/O 
3stack-2ch-dig    3-jack with SPDIF I/O (ALC883)
3stack-6ch    3-jack 6-channel
3stack-6ch-dig 3-jack 6-channel with SPDIF I/O 

but it didin't help. How should I proceed with this ??

Krzysztof

---

