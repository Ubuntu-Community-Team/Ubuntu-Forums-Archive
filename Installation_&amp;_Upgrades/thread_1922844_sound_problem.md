---
title: "sound problem"
date: 2012-02-09
forum: Installation &amp; Upgrades
---

### Post by Pzdarter on 2012-02-09
Hi. I have just upgraded and now have no sound whatsoever. Any assistance appreciated.

---

### Post by ajgreeny on 2012-02-09
Upgraded from what to what?

Much more detail needed please.  Still much to brief.

---

### Post by Pzdarter on 2012-02-10
Hi,
   I upgraded yesterday from jaunty to narwhal. Previously I had correct sound in all applications, but now I have no sound at all, not even the start up jingle. I have tried a cd, no sound.
I am not familiar with computers but my troubleshooting thus far leads me to suspect that the driver has not installed. At that point I was instructed to open a terminal and type some commands which, from memory, included aplay -l and another sudo .....but I did not gain the expected results, which was a list of hardware, instead I got a page of stuff that I had no idea what I was looking at! At that point I knew I was way outa my depth and have given up from there.
I did previous to this toggle all the various options the settings for sound preferences.:(

---

### Post by ajgreeny on 2012-02-11
Run ```
alsamixer
``` in terminal and check that the levels are set where you want them.

Move from slider to slider, and raise and lower levels with the cursor keys;
Mute and unmute with the "M" key.
Tab will move you from "playback" to "capture".
Esc will save and exit.

Also install **pavucontrol** if you don't already have it, run **pulseaudio-volume-control **and play around with the control options in that.

---

### Post by Pzdarter on 2012-02-21
Hello,
      thanks for your interest and suggestions. I now have full sound again and am delighted!!

                     Regards

---

