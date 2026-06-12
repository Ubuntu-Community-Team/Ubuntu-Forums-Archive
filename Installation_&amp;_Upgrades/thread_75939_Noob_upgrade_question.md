---
title: "Noob upgrade question"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by MLX on 2005-10-14
I am about to upgrade to Breezy and was going to change my /etc/apt/sources.list as shown in the BreesyUpgradeNotes post to this:

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main universe multiverse restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

Do I need to do anything with this first line from my current sources list?

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

---

### Post by macgyver2 on 2005-10-14
[QUOTE=MLX]Do I need to do anything with this first line from my current sources list?

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted[/QUOTE]
You can just get rid of that line...as you can probably tell, it tells apt to look for the Hoary install CD.  You won't need that anymore since you're upgrading to Breezy.  :)

---

### Post by MLX on 2005-10-14
Thanks macgyver2
I figured that was the case but figured it was better to ask first.

---

