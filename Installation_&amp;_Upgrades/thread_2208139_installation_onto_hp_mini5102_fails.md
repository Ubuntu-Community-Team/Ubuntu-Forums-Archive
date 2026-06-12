---
title: "installation onto hp mini5102 fails"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2014-02-26
I am just after long time again in progress of an installation of 12.04.4 on my HP mini 5102.

I can start Ubuntu live, but then when I go to the installation, I can just select language, then the installation preparing dialog comes up. All is ticked, internet connection is OK (via LAN cable) but from there on simply nothing happends.
Busy sign is circling for hours, no evidence of something happening, there is no other activity of the computer.

I have 2Mb ram and enough space on drive.

Any idea how to get ubuntu to that machine?

I strated the live system from usb stick (unetbootin)

---

### Post by ajgreeny on 2014-02-26
Was the .iso file you used for unetbootin good; did you check the md5sum of the image from those listed at [UbuntuHashes - MD5sum]("https://help.ubuntu.com/community/UbuntuHashes")?

---

### Post by ottosykora on 2014-02-26
yes have checked that, and downloaded twice, no luck.

Have now taken the 13.10 and this does behave as expected, I was abel to install it somehow.

Have just now problems to find the classic desktop for it, this seems to not exist any more??
Sorry, I have not been around Ubuntu for long time, my all other machines had 12.04 with classic, so now I am struggling

Does somebody have a link for installation of classic desktop on 13.10?

---

### Post by ajgreeny on 2014-02-27
I think there is a classic desktop that can be added to 13.10, and I believe you need to install **gnome-panel** to get it, along with all the dependencies, just as was needed for 12.04, but things may have moved on from that time so see if it works, and if not follow my thoughts on other DEs below.  

EDIT:
A quick search has just suggested that you need the ubuntu-gnome version rather than standard unity ubuntu to get the gnome-classic desktop, so the above may not work as I thought originally.

You would probably have done a lot better on that hardware with Xubuntu or Lubuntu instead of Ubuntu with the unity desktop.  You could either reinstall using another .iso of (XL)ubuntu or even try adding xfce4 or lxde to your current Ubuntu.

The latter can add some over-complication to the menu content to the system, but if you try xfce4 and lxde rather than xubuntu-desktop or lubuntu-desktop packages it is probably worth trying, as they will pull in less cruft than the full *ubuntu-desktop metapackages.

---

