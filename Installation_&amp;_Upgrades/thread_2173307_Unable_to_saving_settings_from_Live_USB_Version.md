---
title: "Unable to saving settings from Live USB Version"
date: 2013-09-09
forum: Installation &amp; Upgrades
---

### Post by kenetik on 2013-09-09
I put Xubuntu 13.04 64-bit on a jumpdrive using "Universal USB Installer" from ubuntu, using persistence. 

I successfully launched it from a computer at work with no hard drive, and configured everything to preference, then logged out and shutdown. 

When I came home and trying to run it, I was unable to boot into the settings that I created, it only gave me the options to Install or Try Xubuntu. Even when running 'Try' it was brand new settings with xubuntu-session-user as opposed to the users I created. 

Is there any other information that I can provide that would be of benefit? I would appreciate any feedback. 

Thanks.

---

### Post by Bucky Ball on 2013-09-09
Sounds like you have created regular install media rather than a persistent install to USB. 

What instructions did you use to create the media? Maybe have a look here:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by kenetik on 2013-09-09
Bucky,

Thank you kindly for your quick response. Unfortunately I do not remember which tutorial I followed. Although I will look into that tutorial and see if that helps. Thanks again!

---

### Post by Bucky Ball on 2013-09-09
All good. You might want to check this bit specifically:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing_Ubuntu_on_the_USB_drive](https://wiki.ubuntu.com/LiveUsbPendrivePersistent#Installing_Ubuntu_on_the_USB_drive)

You'd need to change '11.04' for the release you are using, naturally. This could also be of some assistance and easier, although a new approach so handle with care:

[http://ubuntuforums.org/showthread.php?t=2172971](http://ubuntuforums.org/showthread.php?t=2172971)

What you are trying to do is listed under the heading 'Typical cases for the One Button Installer' and you should find more info on how to do it from the link on that page here:

[http://ubuntuone.com/4Py84gLbZrk8z12ZzSb8SW](http://ubuntuone.com/4Py84gLbZrk8z12ZzSb8SW)

---

### Post by ubfan1 on 2013-09-09
Note bug 1159016, where persistence is broken on UEFI machines.  Solution, edit the /boot/grub/grub.cfg file and add the word persistent to the linux boot line.

---

### Post by kenetik on 2013-09-09
ubfan1, Thank you for that!

I was also able to find some useful information in #xubuntu on freenode, thanks to XRS1 / I pastebin'ed our conversation for anyone else to be able to use this information as well!

[http://pastebin.com/raw.php?i=vCZB8ALz](http://pastebin.com/raw.php?i=vCZB8ALz)

Thanks again to everyone.

I will report on my results upon completion!

---

