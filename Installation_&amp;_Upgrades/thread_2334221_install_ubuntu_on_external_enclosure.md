---
title: "install ubuntu on external enclosure"
date: 2016-08-17
forum: Installation &amp; Upgrades
---

### Post by sparks0335 on 2016-08-17
Hi, I am new to this forum, I have a 2.5 laptop hdd from my grandson's computer. I want to install ubuntu to that hdd in an external enclosure (usb) Do I download the os and put that on a dvd? I have never done this before.
Thanks John

---

### Post by sudodus on 2016-08-17
Welcome to the Ubuntu Forums :-)

The short answer is yes, you can download an iso file, check it with md5sum and install it into a DVD disk or USB drive. See the following link,

[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

At the bottom of that page there are links to instruction pages how to create a boot DVD/USB drive.

-o-

With more information, we will be able to give relevant help for your particular case.

In principle you install Ubuntu into an external drive like you would install it into an internal drive. But there are some differences, particularly if your computer is running in UEFI mode.

So please tell us about your computer,

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

- Are you running Windows or MacOS in your computer?
- Are are booting in BIOS mode or UEFI mode?
- Are you already running Ubuntu in a computer, or is Ubuntu new for you?

---

### Post by sparks0335 on 2016-08-17
Thanks for the replay, The computer I am using to send this is a dell d630 with windows 10,duo core,2gb ram. My grandson's is an Asus, i5, 8gb ram. Sorry I don't know what UEFI is.
Thanks John

---

### Post by sudodus on 2016-08-17
Are the following specs correct (except that you have 2 GB RAM)?

[http://www.cnet.com/products/dell-latitude-d630/specs/](http://www.cnet.com/products/dell-latitude-d630/specs/)

[In that case] I think that your computer is running in BIOS mode (too old for UEFI). I think your computer is powerful enough for all flavours of Ubuntu, but I think you should try not only standard Ubuntu, but also the medium light 'flavours' Xubuntu and Ubuntu MATE or the ultra light Lubuntu, particularly if you want to play high definition video. I suggest that you start with the current release 16.04.1 LTS. With only 2 GB RAM, I suggest that you install the 32-bit version, because it needs less RAM for the same tasks, even though it is possible to run a 64-bit version.

See this link: [Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

I see from the link with the specs, that there are only USB 2 ports (no USB 3 ports). This makes the connection much slower than with an internal drive, but I think it will work fairly well anyway.

Do you know already how to boot from a USB drive? There are some tips in the following link (and links from it). Dell computers let you select boot drive after pressing an F (function) key, try F12 (it works in my old Dell desktop computer).

If you want it to always boot from USB (as the default first choice) you must change the boot order in a BIOS menu. The following link might help: [Booting the Computer from USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by sparks0335 on 2016-08-18
Thanks for all the links and your help, I downloaded ubuntu, made a DVD then loaded it the the hdd. everything good. Again thanks for your help.
John

---

### Post by sudodus on 2016-08-18
Congratulations :KS

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

(and start a new thread, if you have a new problem or question)

---

