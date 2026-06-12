---
title: "ubuntu-minimal: Depends: memtest86+ but it is not going to be installed"
date: 2005-10-23
forum: Installation &amp; Upgrades
---

### Post by Morgrog on 2005-10-23
I get the following message when the ubuntu install CD installs the base package

ubuntu-minimal: Depends: memtest86+ but it is not going to be installed


Since everything is automated at that point (just booted with the CD and everything was automated to that point), what can I do?
Tried looking for the apt-get but being the clueless newbie that I am, can't find it

(this is an install from scratch, not an upgrade)

Any help will be appreciated :)

Thanks

edit: nm, I am a complete idiot... that'll teach me to have an undersized /boot partition...

dpkg: error processing var/cache/apt/archives/memtest86+_1.60-1_i386.deb (--unpack):
 failed in buffer_write(fd) (15, ret=-1): backend dpkg-deb during `./boot/memtest86+.bin': No space left on device

eh

---

