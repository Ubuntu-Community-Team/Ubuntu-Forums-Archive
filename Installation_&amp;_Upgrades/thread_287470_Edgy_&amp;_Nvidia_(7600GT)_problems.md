---
title: "Edgy &amp; Nvidia (7600GT) problems"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by mageus on 2006-10-28
First time Ubuntu user, installed fresh 6.10 Edgy install, worked fine.  Trying to install NVidia drivers without success.  I've read through the forums and found many possible solutions, none of which have worked for me.  Wonder if there are any other ideas.

System:
- Biostar TForce 6100 (NV 6100 chipset)
- Athlon 64
- 1GB RAM
- eVGA 7600GT
- Ubuntu Edgy 6.10 AMD64
- onboard video disabled in BIOS (6100 chipset)

The intial install works fine with the original (I presume) VESA drivers.  X works fine.

Made sure to update all SW with apt-get.
I tried installing using the standard repository via apt-get (nvidia-glx).
Tried the NV drivers from the NV website (8776) and the beryl repository.
Tried manually configuring xorg using dpkg-reconfigure.
Tried using both 'NV' and 'nvidia' in the device section of xorg.conf.

Basically, I always get the error
"Fatal server error - no screens found"

Any help is appreciated, and I can post logs if needed.

Fortunately I can drop back to the native video driver by just copying back my old xorg.conf, so I know this is an NV driver or xorg.conf config issue.

TIA.

---

### Post by adam.skinner on 2006-10-29
Post your xorg.conf

---

### Post by mageus on 2006-10-31
Attached is my xorg.conf file (I can't attach the log file since it's too big).

2 ideas

- The log states that the NV kernel is at 1.0-8774 and that the x module is 1.0-8776.  I used the standard install repos using apt-get nvidia-glx, so I assumed the NV driver would be compiled for Edgy, but is this not the case?

- My onboard video is disabled, and the 7600GT is in the PCI-e slot.  Could it be looking for the onboard video, thus saying 'no screens found'?

---

### Post by angkor on 2006-10-31
This usually works for me:

```
sudo aptitude install linux-restricted-modules-`uname -r` nvidia-glx

```

After that change the driver to nvidia in stead of nv and you should be good to go after restarting X.

---

### Post by mageus on 2006-10-31
<sudo aptitude install linux-restricted-modules-`uname -r` nvidia-glx>

Already tried that, doesn't help.

---

### Post by g8m on 2006-11-01
I have the same card. dpkg-reconfigure xserver-xorg did the trick for me.

---

### Post by mageus on 2006-11-01
g8m:

I tried dpkg-reconfigure, didn't work.  What settings did you use for the reconfig?  Also, do you have onboard video on your motherboard?  If possible, could you post (or send me) your xorg.conf?

To anyone:
I suspect this is a problem with a conflict with on-board video.  Anyone have ideas?

---

### Post by g8m on 2006-11-02
i made a mistake, my card is an agp GeForce 7600GS card. I got the same error though, but after dpkg-reconfigure x started. After that  I installed beryl. And that messed up my configuration completely so i removed everything. Now I have it running with the nvidia beta drivers. (9625)

---

### Post by stealth17 on 2006-11-02
> **angkor said:**
> This usually works for me:

```
sudo aptitude install linux-restricted-modules-`uname -r` nvidia-glx

```After that change the driver to nvidia in stead of nv and you should be good to go after restarting X.

Thanks! That worked for me for my 7800gtx!

---

