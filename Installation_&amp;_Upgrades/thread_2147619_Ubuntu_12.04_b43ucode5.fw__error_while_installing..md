---
title: "Ubuntu 12.04 b43/ucode5.fw  error while installing."
date: 2013-05-22
forum: Installation &amp; Upgrades
---

### Post by spiderlandcapt on 2013-05-22
I have never used linux before. I got it put on a flashdrive and managed to get the desktop to show up for ubuntu.

after a moment a notification pops up in the corner and says there are restricted drivers and they need to be installed, these are for broadcom wireless adapters and when I click  to install drivers it gets 3/4th of the way through and I get a long page of text and errors.

one of the first errors says "b43/ucode5.fw"

If I hit any key it takes me back to the desktop but the resolution is destroyed and I can't click or access anything and always have to do a hard shutdown.

Now I understand that this is an error caused by Broadcom wireless adapters and I've looked at the fixes needed, but have absolutely no understanding of command line in linux.

[https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/909871](https://bugs.launchpad.net/ubuntu/+source/b43-fwcutter/+bug/909871)

I tried to hold shift on install to access the menu where I get to pick my language but I have had no luck with getting that page to pop up. 

if there is any simple starter steps that would help tremendously.

---

### Post by EmmEight on 2013-05-23
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

Sounds like you need to install the drivers for b43, if you can get the computer on the internet without using wireless, the steps are pretty simple

```

sudo apt-get update
```

If you have a **b43** card use the command 

```

sudo apt-get install firmware-b43-installer
```

 or, if you need the **b43legacy** driver, use: 

```

sudo apt-get install firmware-b43legacy-installer 
```

or, if you need a **LP-PHY** version (e.g BCM4312), use: 

```

sudo apt-get install firmware-b43-lpphy-installer
```


When you are done installing, restart the computer

```

sudo reboot now

```

*Poof*

---

