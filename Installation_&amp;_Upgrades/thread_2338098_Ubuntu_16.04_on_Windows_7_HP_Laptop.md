---
title: "Ubuntu 16.04 on Windows 7 HP Laptop"
date: 2016-09-24
forum: Installation &amp; Upgrades
---

### Post by roland-logikalsolutions on 2016-09-24
I have tried several times now, but Ubuntu 16.04 64-bit will not correctly install alongside Windows 7 Pro on this machine. It complains about UEFI and does not recognize Windows 7 UEFI. Mint 17.3 KDE installs just fine so this is a recent glitch. Has anybody successfully done this? I need to keep a sacrificial Windows 7 partition around on one machine to interface with both my Garmin and my glucose meter. Yes, there are potential work arounds for Garmin but not for my Glucose meter.

---

### Post by oldfred on 2016-09-24
Post this from terminal in live installer:
sudo parted -l
And this:
sudo fdisk -lu

---

