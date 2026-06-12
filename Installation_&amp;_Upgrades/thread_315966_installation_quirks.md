---
title: "installation quirks"
date: 2006-12-10
forum: Installation &amp; Upgrades
---

### Post by krelverehan on 2006-12-10
Hi, I wish to install ubuntu on my machine. I have used it at a friend's house, and was sold.

I am using a hand-me-down computer I got from a friend. It is currently running GenToo, and I am comfortable using it (I have been using it for a year now), but I is way too complicated for its own good. I need something a little more user-friendly.

One problem I am having with GenToo is that I can't properly mount my CD drive, thus I can't burn the iso onto a disk. I have downloaded it, and I was wondering if there is a way to install it without burning it onto a disk (I am sure there is a way, but my google results only tell me how to do it from a Windows machine).

Also, just to clarify, I wish get rid of gentoo and exclusively use ubuntu. And I have a few folders with all my music and such I would like to have saved when I do the switch (I have them all backed up on my ipod, so it is not really a big deal).

Thanks for your time, and if there is another thread you could redirect me to or any tips pointing me into the right direction, I would love to hear them.

-Kiel

---

### Post by lha on 2006-12-10
[http://marc.herbert.free.fr/linux/win2linstall.html]("http://marc.herbert.free.fr/linux/win2linstall.html")
It's quite long, but you are interested in a small portion of it. (Mostly under heading Ubuntu.) Basically, get the network installer kernel (linux) and ramdisk image (initrd.gz) from [http://za.archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/]("http://za.archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/ubuntu-installer/i386/") and use grub or lilo to boot them. (You can change the za part into something else, check [https://wiki.ubuntu.com/Archive/OfficialMirrors]("https://wiki.ubuntu.com/Archive/OfficialMirrors") for a mirror close to you.) I don't remember if you can install to the same partition where you have the installer files, so it might be a good idea to investigate this beforehand.

---

