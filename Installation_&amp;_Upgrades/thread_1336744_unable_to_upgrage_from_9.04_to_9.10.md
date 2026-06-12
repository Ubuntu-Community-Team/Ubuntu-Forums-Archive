---
title: "unable to upgrage from 9.04 to 9.10"
date: 2009-11-24
forum: Installation &amp; Upgrades
---

### Post by Forbees on 2009-11-24
when 9.10 first came out i saw the option to upgrade with my update manager, but i didn't have the time so i ignored it, thinking i'd just get back to it later

but now it's gone

even tried upgrading through terminal
```
forbees@forbees-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

i'm still running 9.04, want to get to 9.10, but i don't want to download the image and flash a drive to reinstall

suggestions? or am i stuck to the long method of flashing a usb drive

---

### Post by raymondh on 2009-11-24
> **Forbees said:**
> when 9.10 first came out i saw the option to upgrade with my update manager, but i didn't have the time so i ignored it, thinking i'd just get back to it later

but now it's gone

even tried upgrading through terminal
```
forbees@forbees-laptop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

i'm still running 9.04, want to get to 9.10, but i don't want to download the image and flash a drive to reinstall

suggestions? or am i stuck to the long method of flashing a usb drive

Check your software sources and make sure (under the update tab) that the box for "check updates" is checked and that release upgrade shows "normal releases".

From there, do your usual

sudo apt-get update
sudo apt-get upgrade

Here is the release notes.  Also, make sure your are updated in Jaunty before upgrading to Karmic.

[https://help.ubuntu.com/community/KarmicUpgrades](https://help.ubuntu.com/community/KarmicUpgrades)

Have a working back-up of your files.  happy ubuntu-ing.

---

### Post by Forbees on 2009-11-30
yeah it's set for normal releases. . .

---

