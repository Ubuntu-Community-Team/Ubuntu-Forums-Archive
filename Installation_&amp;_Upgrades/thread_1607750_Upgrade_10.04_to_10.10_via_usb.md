---
title: "Upgrade 10.04 to 10.10 via usb"
date: 2010-10-28
forum: Installation &amp; Upgrades
---

### Post by Shishant on 2010-10-28
Hello,

I have already downloaded the ISO of 10.10 and created a startup  disk(Pen drive) now I want to upgrade my current 10.04 instead of fresh install because I have installed tons of apps.

Is it possible to upgrade my system from usb pen drive which I have created using ubuntus startup disk creator.

---

### Post by alexandari on 2010-10-28
Yes it is possible,there shouldnt be any problems whatsoever. You may have some trouble with choosing the right boot device (I had that problem),depending on your BIOS,but overall it should be ok :)

---

### Post by mörgæs on 2010-10-28
You can easily do a clean install and get the same applications in the new release, as explained here:

[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

### Post by Shishant on 2010-10-28
> **alexandari said:**
> Yes it is possible,there shouldnt be any problems whatsoever. You may have some trouble with choosing the right boot device (I had that problem),depending on your BIOS,but overall it should be ok :)
I have booted through usb but there is option only for install and not upgrade

---

### Post by alexandari on 2010-10-28
oh god,sorry I didnt understand that you wanted to just upgrade the system. You can upgrade the system via the terminal,but all your installed apps will stay,or be updated

```
 sudo apt-get dist-upgrade 
```

---

### Post by Shishant on 2010-10-28
> **alexandari said:**
> oh god,sorry I didnt understand that you wanted to just upgrade the system. You can upgrade the system via the terminal,but all your installed apps will stay,or be updated

```
 sudo apt-get dist-upgrade 
```
Will it upgrade through usb or download the whole ubuntu iso again?

---

### Post by alexandari on 2010-10-28
No you dont need a USB or anything to upgrade like that,it just downloads and installs the things needed :)

---

### Post by Shishant on 2010-10-28
> **alexandari said:**
> No you dont need a USB or anything to upgrade like that,it just downloads and installs the things needed :)
ok, thank you.

---

### Post by AndyCee on 2010-10-28
Crikey people, read each other's posts.

I've had trouble upgrading from a USB in previous releases, as the upgrade process started successfully but part way through tried looking for files in the ACTUAL CDROM drive & halted. I have no idea whether this stuff is fixed.

You should have more success using just the ISO file, following [these instructions]("http://tuxtweaks.com/2009/04/upgrade-ubuntu-with-a-cd-image/").

Let us know how you go.

EDIT: Upgrading over the net is the better option, like alexandari suggested, as it will pull down the latest upgrades.

---

