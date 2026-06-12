---
title: "Trying to Install alsa driver 1.0.24"
date: 2011-02-19
forum: Installation &amp; Upgrades
---

### Post by rzzzz on 2011-02-19
Hello,

First time linux user, so please be patient. Installed ubuntu 10.10 a couple nights ago. After getting graphics card to work (don't ask how - well you guys helped), now trying to get sound to work. Thought this was supposed to be easier/better than windows. Oh well.

Anyway, not that I know what alsa or anything of this stuff is, how do I install alsa driver 1.0.24 (I read it is supposed to get my sound working). I downloaded it, and extracted to desktop...and now no clue what to do, i.e. how to actually install it.

INFO: ubuntu 10.10, GNOME, sound card: Intel Corporation 5 Series/3400 Series Chipset High Definition, current driver: snd-hda-intel (I read that this is pre-installed).

To the best of my knowledge, nothing is muted. I some installed pulseaudio and all that, and unmuted etc...

Really close to giving up, funny, with Windows all I have to do is unmute and increase volume...

Any help would be appreciated!!

---

### Post by redradish on 2011-03-13
Hey,

Bleak about all your issues, sucks when hardware isn't supported. Are you still trying to fix your problems? I'm in a similar position, I'm trying to get a microphone working, and the new 1.0.24 alsa drivers have a fix specifically for my audio card input. Are you certain that upgrading to 1.0.24 will solve your problem? If you're unsure a good idea would be to head over to the alsa-driver launchpad site, and pose a question there: There's a script you can run that let's people know what's potting with your sound settings and they may be able to help you. 

If you *do* want to install the latest alsa driver, you can either install from source (found a nice guide here: [http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html](http://duopetalflower.blogspot.com/2011/02/alsa-1024-in-ubuntu-1010.html)), or you can upgrade to natty (Ubuntu 11.04), which has the new drivers built in (run "update-manager -d"). Please note though, that natty is in alpha and so don't be surprised if your system crashes and you lose data etc. Perhaps do a backup and give installing alsa from source a try. 

Don't give up though, having a running ubuntu system is so worth it! :D

---

