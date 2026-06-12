---
title: "ubuntu-12.04-alternate-amd64.iso totally screwed"
date: 2012-04-26
forum: Installation &amp; Upgrades
---

### Post by Nekomata3 on 2012-04-26
The .iso has several files with incomplete names like "xserver-xorg-video-ati_6.14.99~git20111219.aacbd629-0ubuntu2_.deb" and several others that fail the checksum and broke the installation.... please fix this.

---

### Post by jadtech on 2012-04-26
you can re burn the iso some say USB  stick is best if your computer will boot from USB  though CD or DVD will do make sure you burn the iso at the slowest speed ...

---

### Post by Nekomata3 on 2012-04-26
... the original file name is **xserver-xorg-video-ati_6.14.99~git20111219.aacbd629-0ubuntu2_amd64.deb** as [http://packages.ubuntu.com/precise/amd64/xserver-xorg-video-ati/download](http://packages.ubuntu.com/precise/amd64/xserver-xorg-video-ati/download)

the trunked file in xserver-xorg-video-ati folder matches the md5 of another unrelated file: xserver-xorg-input-evdev/xserver-xorg-input-evdev_2.7.0-0ubuntu1_amd64.deb

WTF!!

---

### Post by Nekomata3 on 2012-04-26
> **jadtech said:**
> you can re burn the iso some say USB  stick is best if your computer will boot from USB  though CD or DVD will do make sure you burn the iso at the slowest speed ...

no... im already trying to install via usb, you can check those mismatches in the .iso file downloaded from ubuntu website.

:lolflag:

---

### Post by techsupport on 2012-04-26
> **Nekomata3 said:**
> no... im already trying to install via usb, you can check those mismatches in the .iso file downloaded from ubuntu website.

:lolflag:

Someone should let them know. 

In the meantime, you can just install Ubuntu instead and then add the Xubuntu PPA to install Xubuntu desktop to achieve the same result you want. 

[https://launchpad.net/~xubuntu-team/+archive/ppa]("https://launchpad.net/%7Exubuntu-team/+archive/ppa")

---

### Post by Nekomata3 on 2012-04-26
> **techsupport said:**
> Someone should let them know. 

In the meantime, you can just install Ubuntu instead and then add the Xubuntu PPA to install Xubuntu desktop to achieve the same result you want. 

[https://launchpad.net/~xubuntu-team/+archive/ppa]("https://launchpad.net/%7Exubuntu-team/+archive/ppa")

I'm not trying to install xubuntu, I need the alternate install iso because of encryption and LVM options... where can I report this bug?

---

### Post by techsupport on 2012-04-26
> **Nekomata3 said:**
> I'm not trying to install xubuntu, I need the alternate install iso because of encryption and LVM options... where can I report this bug?

Oh I though you were trying to install xubuntu. My bad. :) 

Report the bug here:

[https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

