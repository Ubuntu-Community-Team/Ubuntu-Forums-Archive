---
title: "No display after upgrade 9.10-&gt;10"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by Humbugs on 2010-05-08
I upgraded ubuntu 9.10 from the update manager- it had a couple of problems, and now when I boot there's no display- I'm pretty sure it's just the graphics driver since it loads up and plays the login sound.

I'm currently running off a CD version of 9.10 and when I chroot the drive with 10 and
sudo apt-get upgrade
it says there's some stuff that depend on fglrx, and that it's not there.

There were proprietary drivers installed before the upgrade- Is there an easy way to just run with non-proprietary drivers? Or to install non-proprietary drivers to another drive?

(I don't really know what I'm doing, if I need to boot to recovery mode and do stuff could someone please tell me how to do that? The only info I can find is maybe possibly press Esc during the os boot and that doesn't seem to work for me)


Edit: /etc/X11/xorg.conf was not missing

---

### Post by Catharsis on 2010-05-09
Try:
1) Hold down Shift while booting to get the grub menu.
2) Hit 'e' to edit. Add "nomodeset" after "quiet splash".
3) Ctrl+x to boot.

---

### Post by PopsTX on 2010-06-06
Worked perfectly on my older home-built system w/Nvidia graphics-card.

---

