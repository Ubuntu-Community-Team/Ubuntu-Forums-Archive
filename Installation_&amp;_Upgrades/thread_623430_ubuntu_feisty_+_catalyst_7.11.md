---
title: "ubuntu feisty + catalyst 7.11"
date: 2007-11-25
forum: Installation &amp; Upgrades
---

### Post by nzadLithium on 2007-11-25
Hey

I decided to try the latest ati driver package built packages from ati installer and installed. Im running feisty gona upgrade to gutsy at end of month if i remember :D

I have a Radeon X1300
I have gui and it seems 2D accelleration is faster now? 
However if i try to run anything that needs to use 3D accell libs it says they arent found. They're supposed to be in the ati installer so whats up??

I had a look through the xorg logs and it looked like the driver had a bit of fun with my card :S

it has an 
EE failed to find interrupts.
and a whole lot of warnings saying 
(WW) AIGLX: 3D driver claims to not support visual 
then a hex code on the end of each warning (goes up 1 value at time)

Apart from that there werent any problems in driver startup so im thinking this is the problem.
and can add agpgart to the modules blacklist? i wana try the agp thing built into the driver.

How can i get 3D accell going? do i have to wait till i gots gutsy or something? maybe somethings to outa date for driver? like the kernel maybe??

Progs i tried that needed 3D libs were catalyst RTCW (quake3 based game for any who dont no already) and glxgears

---

### Post by nzadLithium on 2007-11-26
I'm thinking it was stupid to install when my kernel wasnt supported. But it was fun though :D I guess i gots to wait till end of month then ill upgrade to gutsy. Hopefully i can get some decent game speeds then coz 5-10 fps on a first person shooter just doesnt cut it and without 3d accell? well that really doesnt work.

---

