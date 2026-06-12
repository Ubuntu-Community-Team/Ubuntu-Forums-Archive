---
title: "Reduced ISO size?"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by Ashboy on 2013-05-09
Hi. Due to bad timing on my behalf, I am currently unable to get my hands on a DVDR or RW to burn an installation disc. I do however have a whole stack of old CD-R's. Is it possible to obtain a smaller installation ISO size for Ubunti 13.04 (but with full network card driver support), and download all that's missing after its initial installation?

---

### Post by e-Tiggy on 2013-05-09
Hi,

there is a minimal CD for both the i386 and amd64 versions, you can dl it from here:
[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")
There is a good chance your wifi card won't work so you better get a wired connection for the install just to be on the safe side.
Or alternatively you can install an older version and update it to 13.04.
Of course the best way would be to use and usb drive but I guess that's not an option for you.

---

### Post by Ashboy on 2013-05-09
> **e-Tiggy said:**
> Hi,

there is a minimal CD for both the i386 and amd64 versions, you can dl it from here:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
There is a good chance your wifi card won't work so you better get a wired connection for the install just to be on the safe side.
Or alternatively you can install an older version and update it to 13.04.
Of course the best way would be to use and usb drive but I guess that's not an option for you.

That's too bad, as I don't have a wired connection (landlord owns router). Also no, sadly my BIOS doesn't support booting from USB or Network. I guess I'll have to find an older version that fits. Thanks for the tip!

---

### Post by Cheesemill on 2013-05-09
Try using the mini iso, I've used it successfully with a wireless connection several times.

If that doesn't work then you can burn [Plop]("http://www.plop.at/en/bootmanagers.html") boot loader to a CD and use that to boot from a USB drive.

---

### Post by oldfred on 2013-05-09
While I would prefer flash drive or a minimal, you could try Lubuntu. But in all Ubuntu versions not all wireless drivers are included and you then need a wired connection to download the wireless driver.

If system is so old as not to boot from flash, then Lubuntu may be a better choice. Or you can install full Ubuntu and uninstall lubuntu desktop if your system can support full Ubuntu.

       The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
sudo apt-get install ubuntu-desktop
#Minimal gnome fallback desktop
 sudo apt-get install gnome-panel

---

