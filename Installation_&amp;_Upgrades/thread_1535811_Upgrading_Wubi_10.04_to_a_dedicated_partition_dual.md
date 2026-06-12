---
title: "Upgrading Wubi 10.04 to a dedicated partition dual boot (keeping windows 7)"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by Shadowstep33 on 2010-07-21
Hi,

So I'm completely new to pretty much anything ubuntu/linux related. I recently installed wubi 10.04 and I really enjoy it and am considering upgrading to a dedicated dual boot (so if windows goes down it won't drag down ubuntu with it). I've been searching the internet for answers (and was led to a few posts here) but they weren't much help to me (i don't want to mess anything up so want to make sure I understand the instructions before I do them). 

Basically, I want to upgrade wubi 10.04 to a dedicated partition (dual boot) without having to uninstall windows or wubi if at all possible. On this computer I've been through 3-5 fresh installs of OSs on this machine and would rather not have to go through the process of collecting programs and making new preferences/settings and what not. 

If I can't upgrade that's fine, i'll just uninstall wubi and do a dual boot linux installation from scratch or something but I'd prefer that to be the last resort option.

Thanks,
Gabe

---

### Post by bumanie on 2010-07-21
There is a program called LVPM that transfers wubi installs to a dedicated partition, but I have just read that LVPM is not working in 10.04 - you will probably have to do a removal of wubi from win 7 and then a regular live/alternate cd or unetbootin installation of 10.04 to a dedicated partition.

---

### Post by Shadowstep33 on 2010-07-21
Thank you, I guess I'll just get around to fresh installing Ubuntu when I have the chance. It makes me sad to have to erase all my Ubuntu setting but oh well, it probably won't take that long. It's not like I got very far or have had Ubuntu for very long.

---

### Post by oldfred on 2010-07-21
You can copy /home if you have made a lot of settings. And you can export a list of installed programs if you have installed a lot of apps and want to reinstall.

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

HOWTO: migrate wubi install to partition 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Old conversion LVPM, see Alternative Instructions 
[http://ubuntuforums.org/showthread.php?t=438591](http://ubuntuforums.org/showthread.php?t=438591)

---

