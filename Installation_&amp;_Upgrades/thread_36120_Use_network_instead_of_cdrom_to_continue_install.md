---
title: "Use network instead of cdrom to continue install"
date: 2005-05-21
forum: Installation &amp; Upgrades
---

### Post by kentsin on 2005-05-21
I got some problem installing base system with my installation disk. It report a file is missing and fail to perform the installation of the base system.

Can I change to use network instead of the cdrom to continue the installation process?

---

### Post by dekoi on 2005-05-21
I believe you need to have *some* version of (K)Ubuntu to completely install/update from the 'net. Presuming you DL'ed the .iso, did you check the md5sum? Rare though it is, your .iso could be incomplete.

---

### Post by derrick1985 on 2005-05-22
Should be able to.

sudo nano /etc/apt/sources.list

the first line will be a cdrom entry, you can either delete it, or like me, just comment it out

ex.
##deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

then, do sudo apt-get update and no more cd useage!

---

### Post by KLineD on 2005-05-22
If the install got to the point where you have a minimal but usable ubuntu, you can switch to a console (ctrl + F2 or ctrl + F7) and from there, edit the file sources.list as derrick1985 said and then
sudo apt-get update
sudo apt-get dist-upgrade

I *THINK* that should work, but since we don't know how much of the packages where not installed, it's probably easier to re-download the iso and verify it with the MD5sum

---

