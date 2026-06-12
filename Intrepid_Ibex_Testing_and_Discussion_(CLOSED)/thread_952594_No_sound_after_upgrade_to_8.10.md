---
title: "No sound after upgrade to 8.10"
date: 2008-10-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Spr0k3t on 2008-10-19
So I just upgraded to Ibex last night and noticed I have absolutely no sound.  I checked through the PulseAudio guides to see if I could fix the issue as the same thing happened when I upgraded to 8.04 from 7.10.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285965](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/285965)

Any insight to this issue would be fantastic.

---

### Post by milliman on 2008-10-19
First determine if your audio controller drivers are loading and if your sound card is recognized.  Run the "lspci" and "lsmod" commands to determine if your drivers.  Executing "aplay -l" will quickly tell you if it is loaded.  

I am having a problem where my snd-intel8x0 driver is not loading.

---

### Post by marttali on 2008-10-19
i had no sound for 2 weeks, i tried several of different guides.
Seems like pulse and alsa can't handle certain cards/chips, in my case ATI Azalia SB 600.

So i recommend you to go and download suitable oss .deb from [http://www.4front-tech.com/download.cgi](http://www.4front-tech.com/download.cgi) and hopefully your problems are gone.

If you prefer to try to fix it in other ways, there are 2 threads i can recommend:
[http://ubuntuforums.org/showthread.php?t=866965](http://ubuntuforums.org/showthread.php?t=866965)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

