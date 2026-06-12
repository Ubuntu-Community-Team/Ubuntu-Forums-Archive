---
title: "Tv only works on Jaunty, not Karmic"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ToxinPowe on 2009-10-10
Hello guys, I have tv on Jaunty (Hauppage HVR-3000) with Kaffeine and this script:

"#!/bin/bash
modprobe cx8800 && modprobe cx88xx && modprobe cx8802 && modprobe cx22702 && modprobe cx88-dvb && \
mkdir /dev/dvb/adapter1 && ln /dev/dvb/adapter0/demux1 /dev/dvb/adapter1/demux0 && ln /dev/dvb/adapter0/frontend1 /dev/dvb/adapter1/frontend0 && ln /dev/dvb/adapter0/net1 /dev/dvb/adapter1/net0 && ln /dev/dvb/adapter0/dvr1 /dev/dvb/adapter1/dvr0
exit

Now in Karmic, I installed Kaffeine 1.0pre2 (Kde4), search and found my channels but I can't see or hear anything.
With o without my script.

I try w_scan -c ES -X >> ~/channels.conf
too but I get this error: ERROR: Sorry - i couldn't get any working frequency/transponder
 Nothing to scan!!

Is any problem with the new kernel/modules?

Anybody can help me plz? I'm crazy now :mad:

---

### Post by dinxter on 2009-10-10
i feel your pain :) I had exactly the same problem, kaffeine found the channels but when i tried to open one it said something like 'cannot open resource' or something. I did fix it but i cant be sure how. I think I installed phonon and phonon-backend-xine, then after a reboot it works fine

[EDIT] It may not be the same problem but with it was with a newly installed kaffeine, finds all the channels, doesnt play them when you click, so if that sounds right then give phonon-backend-xine a try

---

### Post by dinxter on 2009-10-10
maybe this
[https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/404970](https://bugs.launchpad.net/ubuntu/+source/kaffeine/+bug/404970)

---

### Post by ToxinPowe on 2009-10-10
"You need to install libxine1-ffmpeg if you want to watch DVB on any xine-based player"


YES YESSSSSSSS YESSSSSSSSSSSSSSSSSSS its works!

Thank you very much dude, I'm happy again, I can move jaunty to karmic now,all is working. thx ;)

Great forum, sry for my poor English ;)

---

### Post by dinxter on 2009-10-10
> **ToxinPowe said:**
> 
Great forum, sry for my poor English ;)
no apologies needed, your english is better than mine :)

---

