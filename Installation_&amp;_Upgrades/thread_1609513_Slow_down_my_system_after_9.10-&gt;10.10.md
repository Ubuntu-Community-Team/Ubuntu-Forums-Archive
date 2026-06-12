---
title: "Slow down my system after 9.10-&gt;10.10"
date: 2010-10-30
forum: Installation &amp; Upgrades
---

### Post by ilghiz on 2010-10-30
Hi,

I have a problem with slow down the system (probably disk access, but I am not sure).

Hardware is: AMD 6 cores 2.8 + ASRock M3A785GXH/128M, 16GB main memory, WD SATA Hard disk with 2TB + ATI 5830.

Recent stable Ubuntu was 9.10 (everything was flying with 9.10 on this system).

In may 2010, I tried to upgrade 9.10->10.4, but the system was too slow, and I switched back to 9.10.

Today I tried to upgrade to 10.10 (indeed I reinstall everything on new partition) and it seems that if one application make disk access, then all other applications are blocked for a large period (about seconds!!!), hence it is hardly possible to work on this computer.

However, hdparm shows pretty good results at the idle system: 109MB/s with "-t" option and 3500MB/s with "-T" option.

I had similar behavior in my laptop Acer Aspire 5740G (i5 with 8Gb main memory and 460 sata WD disk) with 10.4 Ubuntu, and I did downgrade to 9.10, but on the Laptop everything is ok with new 10.10.

Completely the same upgrades 8.10->10.10 on my old Ferrari laptop and 9.04->10.10 on Dell Quad Core was successful without such a troubles. 

Everywhere after the installation I mark the same list of packages by Synaptic and install them in the system.

Please, advice me what I can try to figure out the reason of this slow down!

PS: I am using different Linux systems since 1995 and mostly on Ubuntu since 2006, but I am mainly the user and was happy that on Ubuntu I do not need to spend much time for system installation and maintenance.

Sincerely,

Ilghiz

---

