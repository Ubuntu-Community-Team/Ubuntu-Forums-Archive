---
title: "Grub screen split in half"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by Morvie on 2010-05-24
Hello,

I am running Ubuntu 10.04 on my Samsung NC20 Netbook.

I have one annoying Problem i cannt fix.
My Grub Screen is split into half.
What i have already tryed is to set diffrent resolutions
and to reinstall grub.

Does someone else have an idea how i can fix this?

Regards Morvie

---

### Post by dino99 on 2010-05-24
finally can you select a boot line ?

if not , try to add [COLOR="Blue"]video=vesa[/COLOR] on the boot line

seems to be a video driver issue

[http://ubuntuforums.org/showthread.php?t=1079314&page=44](http://ubuntuforums.org/showthread.php?t=1079314&page=44)

you might add this ppa to your synaptic repo:
[https://launchpad.net/~xorg-edgers/+archive/drivers-only](https://launchpad.net/~xorg-edgers/+archive/drivers-only)

---

### Post by Morvie on 2010-05-24
I can select a boot line and as soon as linux is started the interface works just fine at the right resolution.

So its just a beauty error, but an annoying one.

---

### Post by dino99 on 2010-05-24
sudo apt-get update
sudo apt-get install -f
sudo dpkg --configure -a

into: system admin startup-manager, set a resolution not too wide

sudo dpkg-reconfigure grub-pc
sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure plymouth

---

