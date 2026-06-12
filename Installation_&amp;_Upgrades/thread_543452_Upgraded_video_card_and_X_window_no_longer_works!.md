---
title: "Upgraded video card and X window no longer works!"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by bnajbert on 2007-09-05
I Upgraded the video card and the X window no longer works!The card that was in there was a SIS and I upgraded it to a NV 6200 and i'm assuming there's no video driver and thats why X window is nolonger working. So my solution is to enable the NV restricted driver from the command line..... unfortunately I have no idea how to do this. Any help here is appreciated

System:
Feisty 7.04
AMD 64 3000+
1 GB dual channel
40GB ata
SIS video card  -----> nvidia 6200

---

### Post by sharke on 2007-09-05
> **bnajbert said:**
> I Upgraded the video card and the X window no longer works!The card that was in there was a SIS and I upgraded it to a NV 6200 and i'm assuming there's no video driver and thats why X window is nolonger working. So my solution is to enable the NV restricted driver from the command line..... unfortunately I have no idea how to do this. Any help here is appreciated

System:
Feisty 7.04
AMD 64 3000+
1 GB dual channel
40GB ata
SIS video card  -----> nvidia 6200


sudo dpkg-reconfigure  xserver-xorg if you want to select settings or sudo dpkg-reconfigure -phigh xserver-xorg for auto select
Regards
Sharke

---

### Post by doublearon on 2007-09-05
I swear I just did this exact card no longer than 20 minutes ago. I used envy. I'm a big nooblet so this might not be the right way, or even necessary. Someone hopefully will tell you if I'm wrong.

I logged in as root (was not in xwindows)

made a directory to store the envy .deb file - mkdir envy

i downloaded envy - wget [http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/envy_0.9.7-0ubuntu8_all.deb)

then I followed this howto [http://www.albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu](http://www.albertomilone.com/pmwiki/pmwiki.php?n=Main.Envy-InstructionsForUbuntu) (with a few hiccups for missing dependencies which I have no idea why I didn't have) 

i had to apt-get install what ever program it said envy depended on but I didn't have.

---

### Post by sharke on 2007-09-05
> **sharke said:**
> sudo dpkg-reconfigure  xserver-xorg if you want to select settings or sudo dpkg-reconfigure -phigh xserver-xorg for auto select
Regards
Sharke

sorry for error now correct
Sharke

---

### Post by bnajbert on 2007-09-05
Thanks I'll try this out

---

