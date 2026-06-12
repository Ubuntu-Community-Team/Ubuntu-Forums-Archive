---
title: "Upgrade from Fedora Core 6"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by trogsworth on 2007-04-24
Hi,

I'm running Fedora Core 6 and I'd like to install Ubuntu over it. Having said that I'd like it to preserve the use of my nvidia fake raid (two disks mirroring each other) and preserve my lvm volumes so that I can keep all my files. I'm running an amd64 platorm. At the moment the installer doesn't recognise my nvidia hard disk controller, (it appears in /dev/ but is an invalid filesystem if I try to mount it) and it also can't read my lvm volumes (the only thing it can mount is my old boot sector).  What's the best way to try and install feisty?

Thanks,

Phil.

---

### Post by slayerboy on 2007-04-24
Hiya!  Welcome to Ubuntu!

I hate to break it to ya, but you pretty much have to wipe out Fedora to get Ubuntu installed.  Unless you can repartion and dual boot.  You'll lose EVERYTHING.  If you don't have /home on a separate partition, back up everything and reinstall Ubuntu and setup /home on a separate partition just in case you want to do a fresh install or change distros, you'll at least have your /home that's able to be saved (barring of course that you don't select it to be formatted each time :) ).

Good luck!

---

