---
title: "MPV with raspberry pi on Ubuntu 18"
date: 2018-05-15
forum: Installation &amp; Upgrades
---

### Post by linux-tiger1 on 2018-05-15
Hi,

I am using MPV package to display video and images together on Raspberry pi on ubuntu 18 classic. I have installed lubuntu-desktop to get the desktop environment. I am able to run everything fine using MPV but MPV is dropping frames while running high resolution video and quality is really choppy.

Is there a way I can use MPV with the hardware acceleration or is there another packge which can be used to perform the same application?

Thanks.

---

### Post by TheFu on 2018-05-15
OSMC for r-pi v2-v3 assuming the video is h.264 encoded. Any other encoding won't work except mpeg2 with the purchased mpeg2 HW license.
Trying to run a full desktop on a r-pi is just being cruel.

---

### Post by linux-tiger1 on 2018-05-16
Thanks for the reply, but changing OS is not the option. Need to use Ubuntu, but can use different package if available.

---

### Post by QIII on 2018-05-16
I hope someone can help you with the package of your choice.  Wait a bit and we'll see.

If  you have to go with an alternative, I have found Kodi to run passably on my Pi 3.  

There is a command line application called omxplayer, which I am currently using on a large format electronic picture frame I built on a Pi.  I'm using it to play slideshows in 1920x1080, complete with panning and fading.  Unfortunately, there is no GUI like most media players.

[ATTACH=CONFIG]279722[/ATTACH]

(The power cord is now hidden inside the wall.  If you want the frame, you can use my woodworking shop.  :)  This is also an older version at 1680x1050)

---

### Post by TheFu on 2018-05-16
> **linux-tiger1 said:**
> Thanks for the reply, but changing OS is not the option. Need to use Ubuntu, but can use different package if available.

**Is the video h.264 encoded so you can use the built-in HW decoder?** Any other sort of video encoding just won't work well at hi-def resolutions.

OSMC is a debian stretch-based distro running kodi that has been optimized for media playback on raspberry pi devices and to be kind to SDHC storage.  You can load debian packges using APT. Debian feels a little different than Ubuntu, but it is almost the same.   Not sure if this is helpful or not. 

I use OSMC on r-pi v2 and v3 devices.  

For fun, I did an *apt install mpv* ... 111 packages to be installed. Seems like a huge amount of overhead for a CLI media player.  It wanted Wayland.  Kodi doesn't need X/Windows, which is part of the reason osmc works so well. Minimal overhead.

I have seen Ubuntu-Mate running on a r-pi v3+ (newest board) ... it ran and The Gimp mostly worked, but it wasn't fast.

BTW, I love mpv on my Ubuntu desktop systems.

I'll go away now.

---

