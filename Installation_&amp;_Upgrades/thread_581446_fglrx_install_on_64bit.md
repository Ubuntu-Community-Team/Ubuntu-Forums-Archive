---
title: "fglrx install on 64bit"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by vascot on 2007-10-19
I've just upgraded to gutsy, now my Xserver doesn't start:
 It complained about fglrx wants a newer xorg server version. I have deinstalled xorg-driver-fglrx and reinstall it. But it say this: xorg-driver-fglrx: Depends: libc6-i386 (>=2.6.1) but is not .... etc. I've tried to install libc6-i386, this complains : Depends: libc6 (= 2.6.1-1ubuntu9) but 2.6.1-4 is installed. How can i get my xorg working? Mayby i have to google much more, but i'm using elinks now, so searching is a hell. Please, help me....

---

### Post by jrasmussen0 on 2007-10-19
Are you sure you are entirely upgraded?  Try running aptitude from the command line and press 'u' to update the list; '+' to select all updates; 'g' to go or commit additions; 'g' again to confirm.

Otherwise you could try running off of the open source ati or radeon module (no 3D) until you get the fglrx module working.

---

### Post by vascot on 2007-10-21
I've got it working by first installing an old version of libc6:
apt-get install libc6=2.6.1-1ubuntu9

and then just install the fglrx driver

---

