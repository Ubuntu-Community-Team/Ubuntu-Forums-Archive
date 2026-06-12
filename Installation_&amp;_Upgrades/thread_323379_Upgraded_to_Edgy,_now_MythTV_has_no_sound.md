---
title: "Upgraded to Edgy, now MythTV has no sound"
date: 2006-12-22
forum: Installation &amp; Upgrades
---

### Post by AusIV4 on 2006-12-22
I've been toying with edgy for a while now. My first attempts failed due to a lack of LVM and RAID support. Finally, I decided to create a separate partition for an Edgy install and keep my old Dapper install. In trying to set everything up, I installed MythTV, set up my video card in /etc/modprobe.conf, and rebooted. When I came back later, I found that recordings since the upgrade had no sound, and I was getting the following error:

```
NVR: Only read -1 bytes of 4096 bytes from '/dev/dsp
read audio: Input/output error
```

My immediate thought was that I had not setup the mixer properly. I enabled audio capture, enabled capture on the Line in, and turned up the sound, then ran "aplay /dev/dsp". After several seconds, I got the following error: 

```
play: playback:2021: read error
```

I rebooted to my dapper install, and it plays everything fine. I have no idea what may have changed between installations.

Any ideas?

[EDIT]
I might add that if i unmute the line in, I get sound coming from my tv card.

---

### Post by AusIV4 on 2006-12-23
Since my Edgy install was fresh, I decided to wipe it and reinstall. I ran aplay /dev/dsp, and it worked fine.

Then I ran Adept updater. After updating everything, I got the same error as the above post. I'm trying to find out what might be updating, and I'll see if I can resolve it.
[EDIT]
I wiped everything again, did another install, I was trying to pay close attention to what package installed before aplay quit working, but it never failed. Now MythTV is up and running properly, and I never ran into the problem. It took three reinstalls, but I don't know what the fix was.

---

### Post by AusIV4 on 2006-12-25
I got a Plextor ConvertX TV Tuner for christmas, and when I installed the drivers, I started having trouble with this again. /dev/dsp has the same problems as before, however /dev/dsp1 (the ConvertX). As things are now, I cannot record sound on my integrated sound card, so only my external tuner does me any good. Once again, I believe Dapper works fine (I haven't tested it with the new tuner).

---

