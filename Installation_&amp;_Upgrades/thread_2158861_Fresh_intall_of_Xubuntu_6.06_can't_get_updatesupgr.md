---
title: "Fresh intall of Xubuntu 6.06 can't get updates/upgrade HELP!"
date: 2013-06-30
forum: Installation &amp; Upgrades
---

### Post by WarrenSH on 2013-06-30
I only had 1 blank CDR left and I found Xubuntu 6.06 downloaded it & instaled. The install went very fast. Everthing is working well in Xubuntu 6.06  My issuse is this.   When I go to Applications / System / Update Manager it loads but i'm unable to get the update to 6.10 is there away I can get Xubuntu 6.06 to upgrade to the latest verison of Xubuntu?   If so please explain   Thanks.

---

### Post by Iowan on 2013-06-30
Easily? No...
You can upgrade from LTS to LTS, but i don't think there is currently a one-hop upgrade.
As for updates, Those end with version End-of-Life.

---

### Post by CharlesA on 2013-06-30
You would be better off getting another dvd or a USB drive and downloading one of the newer releases: [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

The upgrade path from 6.06 to something that is actually supported would likely cause more issues than you would want to deal with. You would need to hop thru at least 12 different upgrades to get to a supported release.

---

### Post by sudodus on 2013-06-30
6.06 passed end of life several years ago, and the repositories for updating are no longer there. Please get a new version of Xubuntu by downloading an iso file. I would suggest the long time support version 12.04 LTS, which is 6 years newer than the one you tried.

If your computer is less than about 10 years old it should boot from a USB drive, and you can also make a boot USB (for example a pendrive). It can be reused many times in contrast to a standard CD.

---

### Post by Iowan on 2013-06-30
There IS a Wiki page for [EOL Upgrades]("https://help.ubuntu.com/community/EOLUpgrades").
A fresh install is usually preferred. I've had some upgrade success... but some failures, too.
 ANY failure along the upgrade path means starting over. 
You're welcome to try, but you've probably noticed that it is generally discouraged.

---

### Post by WarrenSH on 2013-06-30
how can I download & install pendrive using Xubuntu 6.06 via Terminal?

---

### Post by CharlesA on 2013-06-30
I think you can use dd to transfer the ISO to a USB drive:
[http://askubuntu.com/questions/59551/how-to-burn-iso-to-usb-device](http://askubuntu.com/questions/59551/how-to-burn-iso-to-usb-device)

Download said ISO with wget.
```
wget http://whatevertheurltotheisois
```

[http://cdimage.ubuntu.com/xubuntu/releases/precise/release/](http://cdimage.ubuntu.com/xubuntu/releases/precise/release/)

---

### Post by WarrenSH on 2013-06-30
I'm not following what you replied. Sorry I do not understand.   What is dd?

> **CharlesA said:**
> I think you can use dd to transfer the ISO to a USB drive: [http://askubuntu.com/questions/59551/how-to-burn-iso-to-usb-device](http://askubuntu.com/questions/59551/how-to-burn-iso-to-usb-device)  Download said ISO with wget. ```
wget http://whatevertheurltotheisois
```  [http://cdimage.ubuntu.com/xubuntu/releases/precise/release/](http://cdimage.ubuntu.com/xubuntu/releases/precise/release/)

---

### Post by CharlesA on 2013-06-30
It's a utility to do bit-for-bit copies. From what I have heard it works fine for transfering ISOs to USB drives.

Do you only have this Ubuntu 6.06 machine to work with or do you have another machine you can use?

---

### Post by WarrenSH on 2013-06-30
Right now I only have this one to work with.

---

### Post by CharlesA on 2013-06-30
Read this:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I don't know if this startup disc creator is included in 6.06, but I doubt it is, which is why you will more than likely need to use dd (which can be dangerous if you don't double check your commands).

---

### Post by sudodus on 2013-06-30
See this link, that describes how to use dd (and the risks if you make a typing error) [Howto make USB boot drives]("http://ubuntuforums.org/showthread.php?t=1958073")

Assuming that the input iso file is 'xubuntu-12.04.2-desktop-i386.iso' the dd command would be

```
dd if=xubuntu-12.04.2-desktop-i386.iso bs=4096 of=/dev/sdx
```

where x at the end should be replaced by the actual drive letter for the USB drive, as checked with for example

```
sudo fdisk -lu
``` or ```
sudo parted -l
``` if that command existed in 6.06

---

