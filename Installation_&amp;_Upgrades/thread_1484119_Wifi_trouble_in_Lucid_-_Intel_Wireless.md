---
title: "Wifi trouble in Lucid - Intel Wireless"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by Loge on 2010-05-15
Hello everyone,

I installed Lucid yesterday and was extremely pleased with it. I only had one problem: The wifi driver had trouble connecting to my router. It took a very long time to connect and, occasionally, asked me for the WPA-code several times, after which it sometimes worked.
I tried to fix this issue by installing ndiswrapper and lenovo's driver for my laptop, a Thinkpad X60 tablet. It said the driver was OK; I restarted, and my wifi connection was gone. So, I deleted the driver in the configuration tool (the ndiswrapper frontend) as well as the tool itself, but still, my wifi does not work.
What's even worse, it seems to have jeopardised my Trackpoint settings as well: I can't adjust speed and sensitivity via this command:
sudo sh -c "echo -n 350 > /sys/devices/platform/i8042/serio1/speed"
any more.
Please help me! I was so happy with Lucid, and now I'm stuck with a terribly slow cursor and no wifi...

Thanks a lot in advance,

Martin

---

### Post by dino99 on 2010-05-15
[http://luke.no-ip.org/x60tablet/](http://luke.no-ip.org/x60tablet/)

[http://hydtechblog.com/2009/09/14/cracking-wep-wpa-with-ibm-lenovo-x60-basics/](http://hydtechblog.com/2009/09/14/cracking-wep-wpa-with-ibm-lenovo-x60-basics/)

---

### Post by Loge on 2010-05-15
Thanks, but those didn't really help! The first link especially is interesting since it talks about rotation, but the author mentions that wifi worked out of the box. It did for me, too, but now, after my tinkering, it doesn't any more.

---

### Post by dino99 on 2010-05-15
[http://ubuntuforums.org/showthread.php?t=1438175](http://ubuntuforums.org/showthread.php?t=1438175)

as there is lot of troubles with lucid+wifi, i suggest you add this ppa to synaptic repo and install the latest kernel 34 to see if that make differences:

[https://launchpad.net/~ricotz/+archive/unstable](https://launchpad.net/~ricotz/+archive/unstable)

i dont know what chipset is giving you these issues, but into synaptic there are: wifi-radar and some ralink packages

---

