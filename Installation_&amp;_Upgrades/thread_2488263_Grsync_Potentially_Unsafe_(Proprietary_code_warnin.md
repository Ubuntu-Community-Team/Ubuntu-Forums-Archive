---
title: "Grsync Potentially Unsafe (Proprietary code warning)"
date: 2023-06-29
forum: Installation &amp; Upgrades
---

### Post by john2210 on 2023-06-29
Hi,

I'm looking at some file sync tools and came across Grsync (GUI for rsync).

In Ubuntu Software Centre it has warning as being "Potentially Unsafe" being it Proprietary code which is clearly not true as the entire source code is published here: [http://www.opbyte.it/grsync/download.html](http://www.opbyte.it/grsync/download.html)

Looking at this how to report it as wrong: [https://gitlab.gnome.org/GNOME/gnome-software/-/wikis/software-metadata#user-content-how-to-fix-incorrect-licensing-information](https://gitlab.gnome.org/GNOME/gnome-software/-/wikis/software-metadata#user-content-how-to-fix-incorrect-licensing-information)
But there doesn't seem to be any report link or anything.

Am I wrong and it actually is proprietary (how?) or how do I actually report it as mislabeled?

Thank you all.

---

### Post by MAFoElffen on 2023-06-29
This is in the Universe repo... 
```

mafoelffen@Mikes-B460M:~$ apt-cache show grsync
Package: grsync
Architecture: amd64
Version: 1.3.0-1
Priority: optional
Section: universe/x11
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Martijn van Brummelen <mvb@debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 660
Depends: libc6 (>= 2.4), libglib2.0-0 (>= 2.35.9), libgtk-3-0 (>= 3.0.0), libpango-1.0-0 (>= 1.14.0), rsync
Recommends: ssh-askpass
Filename: pool/universe/g/grsync/grsync_1.3.0-1_amd64.deb
Size: 144892
MD5sum: a584fd1060edccb8cc6c764ffa26c934
SHA1: afd14c7836a4836d94d8079212283f9284edbd46
SHA256: 57fe6de3ed450131fe42469026d265054d0590959e196ded604783a97fa6f0be
SHA512: 6d77beba65328d3c542500c577dc99dfff0b1bbb3e22309971b36462a44a4108cc158ee5ab8c1b623f913c6cd1dec6159d0ffb75af2a2d6e198136b3e970063b
Homepage: http://www.opbyte.it/grsync/
Description-en: GTK+ frontend for rsync
 grsync is a simple graphical interface using GTK2 for the rsync command line
 program. It currently supports only a limited set of the most important rsync
 features, but can be used effectively for local directory synchronization.
Description-md5: 0ac8f84c8fd587a0895d4e8eb0faba34

```
Have you just tried to install the package through apt?
```

sudo apt install grsync

```

---

### Post by The Cog on 2023-06-29
Read the description for the Universe repo here: [https://www.howtogeek.com/194247/whats-the-difference-between-main-restricted-universe-and-multiverse-on-ubuntu/](https://www.howtogeek.com/194247/whats-the-difference-between-main-restricted-universe-and-multiverse-on-ubuntu/)
Then you can decide whether to trust it. In general, I do, because I don't have the resources to separately vet and check for updates every package I use from Universe.

---

