---
title: "Is these possible????"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by ignacioguevara on 2010-12-01
I´m new on linux and I use a Live USB with persistency file. Every time I create the USB I update the OS with java, flash and other soft, like MP3 libraries etc. But when I install Ubuntu into a HD fron the USB I install it without all those soft that I update.
Is there a way that alows me to install the system already updated?

Thanks

Ignacio

---

### Post by Rubi1200 on 2010-12-03
I am not exactly clear on what you want to do, but I thought this might interest you:
[http://psychocats.net/ubuntu/remastersys](http://psychocats.net/ubuntu/remastersys)

---

### Post by ignacioguevara on 2010-12-04
Thanks for your answer. I would chekit.
What i want to do is install ubuntu on a PC from a live USB that I already update with new soft and libraries, that were't installed in the original USB install

---

### Post by efflandt on 2010-12-04
The live iso only installs its set list of programs.  If you have a network connection there is a checkbox to download some additional files during install (mostly language packs I think) and another checkbox for some restricted files for multimedia.  But the only things it really carries over from persistent data on the live iso is some settings like timezone and network settings (like wireless keys).

Some of the programs that are active on the iso (like gparted) are not installed by default.  And it does not automatically install other programs you installed in persistent data.

There may be a way to install or copy over the .deb files for packages by loop mounting the casper-rw persistent data file from the USB without having to download them again.  After connecting the USB iso:
```
ls /media
**6136-C97B**  (substitute what shows up here in loop mount below)

sudo mkdir /media/vdisk  (if you have not done that once before, as a mount point)

sudo mount -o loop /media/**6136-C97B**/casper-rw /media/vdisk

cd /media/vdisk/var/cache/apt/archives/

ls -l  (should show .deb files for persistent packages installed)
```I am not a dpkg expert, but I think you can use **Places** to go to /media/vdisk/var/cache/apt/archives and double click or right click to use the package manager to install any of the ones you want.  Maybe someone else will suggest another method.

Before removing the USB device, do not forget to:
```
cd  (out of vdisk)

sudo umount /media/vdisk  (no n after the u)
```

---

### Post by ignacioguevara on 2010-12-17
Thanks for your answer!!!

---

