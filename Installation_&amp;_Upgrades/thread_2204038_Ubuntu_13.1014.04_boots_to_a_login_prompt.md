---
title: "Ubuntu 13.10/14.04 boots to a login prompt"
date: 2014-02-06
forum: Installation &amp; Upgrades
---

### Post by EmyrB on 2014-02-06
Hi Guys,

I've had this issue with 13.10 and now with 14.04 which is driving me nuts and I can't seem to figure out what is the cause. I have a Nvidia GeForce GT630 card in my ubuntu box and when I first install either 13.10 or 14.04 everything is fine. Once I install the nvidia drivers my PC boots to a command prompt login, then sits there for about a couple of minutes, then Ubuntu greeter displays and once I log in, it then goes to a black screen for a further minute before the desktop appears. It got so bad that I went back to 13.04 and that booted fine using the same gfx card. As the support has ended for 13.04 I needed to upgrade. Is there an issue with the nvidia drivers? I've searched and searched the internet and I can't find any solution.

Cheers in advance.

---

### Post by grahammechanical on 2014-02-06
> [COLOR=#000000]Once I install the nvidia drivers my PC boots to a command prompt login, then sits there for about a couple of minutes, then Ubuntu greeter displays and once I log in, it then goes to a black screen for a further minute before the desktop appears. [/COLOR]

That says it all, really. "Once I install the Nvidia drivers." I am using Trusty Tahr with the Nouveau open source video driver and I also see a lot of black screen between the purple Ubuntu screen that comes after the Grub menu and the login screen. And then there is a worrying delay until the desktop loads.

This is all part and parcel of running a development release. I would not be be surprised if there were issues with the Nvidia drivers. Use the Additional Drivers tab to experiment. That is the best I can offer.

The differences between 13.04 and 13.10 and onwards include Linux kernels, Xserver, and proprietary video drivers. They all have to work together and Ubuntu developers cannot patch proprietary video drivers.

Regards.

---

