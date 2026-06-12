---
title: "Install Ubuntu on Power Macintosh G3"
date: 2013-10-04
forum: Installation &amp; Upgrades
---

### Post by Rnw6WCJ on 2013-10-04
I have a Power Macintosh G3 (green/white) that I would like to use with Ubuntu Server. Could someone direct me to a step by step install process. I tried to follow wiki.ubuntu.com/PowerPCFAQ but I cannot get past finding my USB drive in OpenFirmware.

---

### Post by Lars Noodén on 2013-10-04
I usually boot from CD but from my notes you should be able to boot from USB using OpenFirmware (cmnd-opt-o-f) with something like this:

```

boot usb1/disk@1:2,\\yaboot

```

Sometimes it is usb1 other times it is usb0.

Other than that, if you are going for PPC, I would recommend to [use Lubuntu](https://help.ubuntu.com/community/Lubuntu/GetLubuntu) instead.  And since you are wanting to install a server, I would recomend using the [Alternate Install](https://help.ubuntu.com/community/Lubuntu/Alternate_ISO) CD and choosing to choose "Install a command-line system" installation. It's there in the initial text menu available under the F4 key.

---

### Post by Rnw6WCJ on 2013-10-04
Thanks for the response Lars. I couldn't figure out the USB so I used a CD instead (using base Ubuntu server not Lubuntu as you suggested). The install seems to freeze on "returning from prom_init" on a white screen. Any idea why?

---

### Post by Lars Noodén on 2013-10-04
I've only ever used Lubuntu with a G4, I'm not sure what the differences will be with G3 or with Ubuntu.  Going with Lubuntu Alternate and choosing "Command-line" will give you about the same as the Server disc, that has worked for me.  Just add the package openssh-server and you're all set.

---

### Post by Rnw6WCJ on 2013-10-04
Thanks again Lars for your input. While downloading the Lubuntu image I decided to read the options for install. The default install option is marked as "install" where I saw another option labeled "install-powerpc" so, on trying that option, everything went off without a hitch. I feel so stupid. Lol. Thanks again for your help and suggestions.

---

