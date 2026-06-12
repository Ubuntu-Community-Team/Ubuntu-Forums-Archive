---
title: "sudo apt-get install xorg-driver-intel"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by TerabyteUK on 2008-01-02
sudo apt-get install xorg-driver-intel

doesn't work for me.

"Couldn' find pacakge xorg-driver-intel"

I'm trying to get the intel driver so ubuntu can at least get close to being able to detect my monitor setup.

---

### Post by wolfen69 on 2008-01-02
in terminal: sudo apt-get install 915resolution xserver-xorg-video-i810 xserver-xorg-video-intel

---

### Post by TerabyteUK on 2008-01-02
for the benifit of future users...

running this command on 704:

sudo apt-get install 915resolution xserver-xorg-video-i810 xserver-xorg-video-intel

causes a "conflict" in dependancies
solution

sudo apt-get install 915resolution xserver-xorg-video-intel

on it's own :)

---

