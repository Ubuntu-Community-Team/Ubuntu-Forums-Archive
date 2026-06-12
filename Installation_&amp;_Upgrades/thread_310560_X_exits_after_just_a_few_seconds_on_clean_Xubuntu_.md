---
title: "X exits after just a few seconds on clean Xubuntu 6.10 Alternate install"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by jcompton on 2006-12-01
Hardware: Gateway Solo 2150 (added larger HD, using 10 gigs for Linux.)

Distro: Xubuntu 6.10 Alternate Install

Problem: Xubuntu installs fine, then appears to load fine, but anywhere between 5 and 30 seconds after the desktop comes up, the interface freezes for a few seconds and then I am silently dumped to a TTY login. (Which works fine.) The desktop looks normal up to that point--if I'm quick I can successfully log in, there's no video corruption, etc.

I have successfully run Ubuntu 4.10 and 5.04 on this machine in the past. 5.04 was noticeably slower than 4.10, though, so I figured Xubuntu would be a better choice now.

I'm happy to post whatever diagnostic logs, but am not terribly sure where to begin.

---

### Post by confused57 on 2006-12-01
Only a guess, but it could be your video card driver...if you know the kind of card you have you can check & change(if needed) the driver in your:
```
sudo nano /etc/X11/xorg.conf
```

or interactively:
```
sudo dpkg-reconfigure xserver-org
```

Since you've been using Ubuntu for awhile, you probably already know how to edit your xorg.conf file, but thought I'd include how.

---

### Post by jcompton on 2006-12-01
Yeah, I've run into fun with Ubuntu and video drivers in the past but I checked the xorg.conf and it seemed correct--plus, again, the desktop works fine up to a point, so I don't think it's an obvious video driver issue. So I'm suspecting another problem, but I guess I can tinker a bit more.

---

### Post by jcompton on 2006-12-01
Messing around in the X configuration doesn't seem to help. This is now the second machine that has failed to work out-of-the-box with Xubuntu (the other being an older G4 Mac tower.) Kind of disappointing.

---

