---
title: "ASRock ION 330 Installation :/"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by MeBrains on 2009-12-22
Early last month, I decided to drop Windows in favor of Ubuntu. It has been an okay experience up to now - difficult, but getting there.

I bought one of these ASRock ION 330 machine as HTPC, print server and web server and got to installing it quite okay. I started of with Karmic server, added Apache, PHP, XBMC. Got the sound working, the video, the resolutions of the HDTV connected through HDMI. I have TF-B4RT running in the background, installed FreeNX, have XBMC logging in automatically, starting XBMC etc.

And am looking at some minor problems now... for the last 2 days and I am not able to solve ANY anymore. Turns out these "minor" problems are not as minor as I initially believed...


[LIST=1]
[*]allow the XBMC user to shutdown, reboot, suspend... I followed the tutorial and got to: sudo polkit-auth --user xbmc ... etc. Rebooted just in case. Guess what: it does not work and I am not able to find any new info on it.
[*]have usplash show the XBMC spinner logo on the plasma's screen. Although when connecting a monitor, the resolution seems to be one the plasma should know, I get Pictore format not supported on it when booting. Seems to be unsolvable for now - even with "startup-manager"
[*]USB mounts - when I installed I am pretty sure they mounted automatically. Not so anymore. Read dozens of other users' woes with it. No solutions.
[*]XBMC seems to lose its known resolution on second start. In other words: it starts up okay, but if it needs to restart without a system reboot - the resolution is bad, i.e. noticeable through overscan. I have not really searched a lot for a potential solution.
[*]Gnome overscan.
[/LIST]
Anyhows, the first three have kept me busy for the better part of two days. I seem to run across unclosed bug reports too much with it and it seems I might be better of installing the system again. I am losing a lot of time here and I am wondering if I should not go back to MS's wonderful world.

Sorry for the rant. - needed t lay it off me for now. 

Course... if you have solutions to one of the above. Feel free to post! :P

---

### Post by MeBrains on 2009-12-22
waw. after only 6h I am on page 3...

I mentioned to maybe try MS's wonderful world again. I was kidding. I do not want to and I guess I am going to reinstall Ubuntu again... I hope that by keeping things under control more than I have now - I tried, I really did - I would get to a stable installation.

I said that it has apache as well. I want to have it as a dev machine for an ezPublish website I want to build. I hope that I will be able to repeat the installation when I get to a staging environment, eventually production. It is one of the worries I have now.


question i have now: should I start from Jaunty - which is supported longer  than Karmic?

---

### Post by MeBrains on 2009-12-24
the question above was not about jaunty, but the LTS server edition.

anyhows, I have reinstalled in the mean time, starting from Ubuntu minimal. All is up and running and working as expected I (largely) followed this guide: [http://www.springydevelopment.co.uk/2009/11/08/minimal-install-of-xbmc-on-ubuntu-karmic-koala/](http://www.springydevelopment.co.uk/2009/11/08/minimal-install-of-xbmc-on-ubuntu-karmic-koala/) 

And added Apache, MySQL, PHP to it. Boot time is way fast - 15s at most. When editing .bash_profile, make sure to use ` and not '. 

Still to do is adding cups, samba, ftp and TF-B4RT.

I hope nothing gets broken doing that. 

Cheers.

---

