---
title: "Installing Ubuntu on a compaq presario 6000"
date: 2006-08-07
forum: Installation &amp; Upgrades
---

### Post by underworld288 on 2006-08-07
I am trying to help someone install Ubuntu on a compaq presario 6000 but when I go to install my resolution of the screen wont let me see the buttons in the bottom right of the screen. Please help I have tried changing the resolution but it's only option is the resolution that its on, which is like 640 by something.

thanks

---

### Post by afilonov on 2006-08-07
Try alternative CD. It uses character-based installer.

---

### Post by underworld288 on 2006-08-08
ok but after I install it how would I change the resoution so the I can see everything on the screen?

---

### Post by afilonov on 2006-08-08
Try to run this from command line:
sudo dpkg-reconfigure xserver-xorg
If you still don't have correct resolutions, you need to set them manually in xorg.conf file. These two links might help:

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

---

### Post by yizuman on 2008-02-11
I have the same system and the sounds from my speaker sucks because it's using the nVidea Riva 128 sound device drivers for the sound card.

I remember when I installed the SoundMax Integrated drivers on Windows XP, the speakers was boomin' awesome! I am wondering if the SoundMax Integrated driver or equivelant to it is available for Ubuntu?

I'm hearing-impaired by the way and I happen to like the boomin' vibration it makes when using the SoundMax driver, epecially when the speakers are sitting near the floor level where I can feel the floor vibrate :)

Any help on this? Please?

Thanks

---

### Post by yizuman on 2008-02-11
double post

---

