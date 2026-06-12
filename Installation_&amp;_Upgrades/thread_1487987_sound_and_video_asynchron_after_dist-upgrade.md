---
title: "sound and video asynchron after dist-upgrade"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by kanyi on 2010-05-19
Hi!

I've got an problem:
After the upgrade 9.10 to 10.04 the sound always faster the video. My pulse audio system send me an message under the upgrade:
[http://pastebin.ubuntu.com/436327/](http://pastebin.ubuntu.com/436327/)

Ok, I checkd it in the /etc/default/pulseaudio file is the PULSEAUDIO_SYSTEM_START=0 so it is correct. (There are another option dynamically module loading is true: DISALLOW_MODULE_LOADING=1)

After then, try to the SMplayer, VLC, flash, sound/video are not correct. Try to set up in the preferences, and now if I changed the sound output in the SMplayer and VLC pulse to alsa. This is solve the porblem in the players, but what can I do the Flash player.

Another how can I solve all of these problem?

---

