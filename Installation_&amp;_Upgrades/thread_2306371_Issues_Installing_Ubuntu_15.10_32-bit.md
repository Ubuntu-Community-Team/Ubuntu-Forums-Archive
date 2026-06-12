---
title: "Issues Installing Ubuntu 15.10 32-bit"
date: 2015-12-15
forum: Installation &amp; Upgrades
---

### Post by Parker_Harless on 2015-12-15
Hello!

I am new to the Ubuntu world, and I'm trying to install Ubuntu 15.10 32-bit on an Acer Aspire One Netbook. I am booting off of USB, and whenever I change the boot order, it flashes and shows a continuously blinking underscore at the top left of the screen. I know pretty much nothing about Ubuntu except for it being an open-source operating system.

Any help getting this installed would be greatly appreciated. Is there anything I'm doing wrong here, or am I just being impatient?

Thanks in advance. :)

---

### Post by sudodus on 2015-12-15
Welcome to the Ubuntu Forums :-)

How did you make the USB drive bootable?

How much RAM is there in the computer (1 GB or more)? Maybe it would work better with an Ubuntu flavour with a lighter desktop environment, Lubuntu or Xubuntu.

And it might be a good idea to install version 14.04.1 LTS, which has longer support (until April 2017) than 15.10 (only until July 2016).

See the following links,

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](http://ubuntuforums.org/showthread.php?t=2230389)

[Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Parker_Harless on 2015-12-19
Hello!

There is only a gig of RAM in the computer, so I'll try a lighter weight system.

I followed these instructions for making the USB stick: [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows)

Thanks for the reply, and apologies for being a little late to reply.

---

### Post by sudodus on 2015-12-19
That method should work. If not, you find other methods/tools via the links in post #2.

Good luck with the lighter flavour(s) of Ubuntu, and please come back if/when you have any questions :-)

---

### Post by roler2 on 2015-12-22
Stick with 14.04 with the default kernel. Don't utilize the HWE upgrade and stay away from 15.10 if you have a very old computer such as a P4. Appears to be updated kernel issues poorly interacting with old computer graphics cards. I was able to install 15.10 with a Flash Drive however everything that happened after that I just got Desktop freeze issues, bad, fuzzy unclear graphics and extremely poor font rendering. 14.04 with the default kernel works very well. No freezes, good graphics, terrific font rendering.

I am now concerned about 16.04 as it will have a major upgraded kernel. If it is going to be the same scenario as 15.10 then I cannot utilize Lubuntu any longer.

---

### Post by gordintoronto on 2015-12-23
Just to combat the naysayers, I am running Xubuntu 15.10 on an Acer Aspire One (1 GB) with no issues at all. I mostly use the computer for downloading and playing podcasts, but it's also a tiny file server, and I have used it as a remote camera.

---

### Post by MAFoElffen on 2015-12-23
One issue not mentioned-- there were many versions of the Acer Aspire One. Early ones have a bug booting from an SD card. Acer had a BIOS firmware update that corrected that...

And if you have an issue with boot order, press <F12> on bootup to bring up the boot menu.

---

