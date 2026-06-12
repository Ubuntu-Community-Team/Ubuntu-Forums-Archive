---
title: "Graphical interface failed to load from LiveCD"
date: 2011-02-28
forum: Installation &amp; Upgrades
---

### Post by Dediggefedde on 2011-02-28
Hi^^

I've got some Problems with installing/using Ubuntu and hope you could help me^^

I tried to install Ubuntu on my Desktop-PC (beside WinXP) and on my Laptop.
I have burned a Live-DVD (CheckSum OK) with the Maverick Meerkat and it loads fine untill you can decide whether to run from CD or install Ubuntu...
When I try to install, there is the Desktop-Background, but no window (sometimes a white window that does'nt load anything)...

I found a way to install lucy lynx: I just installed jaunty jackalope and upgraded^^ there isn't any problem... but it is very uncomfortable... and I had to reinstall the graphic-driver two times...

I use a nVidia-Card that is maybe 1-2y old...

however, trying to upgrade to Maverick Meerkat gives me an Error that there could be halted Packages or some invalid third-party-packages... but I checked the package-administrations...

There is also the Problem since Lucy lynx that my hard-drive is about 128 TB and my battery (Laptop) is always full.

There is also an error occurring while playing DXL-Ball (something like Arkanoid) that the Computer is frozing, actualizes the screen particularly and after some time, the Computer shut down.


Is there something I missed somewhere while installing Ubuntu?^^
Or do you need some more specific Error-Messages?^^

---

### Post by sikander3786 on 2011-03-01
Welcome to the forums :-)

I think you mis-typed something here.

> my hard-drive is about [COLOR="Red"]128[/COLOR] TB

We need to know the full hardware specs of machine in question including Processor, RAM and Graphics Card Model.

You might also need to check your Lucid downloaded image's health.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

And also check the disc for defects.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

### Post by Dediggefedde on 2011-03-01
ah, ok...
Well, i didn't mistyped something there^^
mybe I didn't tell it right, but ubuntuy is saying my hard-drive is about 128 TB big^^

Processor Intel Core 2 Duo T5870 @2gHz
Harddrive: Hitachi HTS5... 160GB SATA300 2.5'' 5400rpm 7MB Cache
Graphic-card: NVIDIA Geforce 8200M G
2 GB Ram DIMM DDR2

The downloads have the right checksum and there are no burning-errors...

---

### Post by sikander3786 on 2011-03-01
Did you try booting a Lucid disk? Does it encounter the same problem?

---

### Post by Dediggefedde on 2011-03-01
Well, I've got some disks here from previous versions...
I tried MM, LL and KK, so there was always the same error...
but using JJ is working alright...
(btw. the option "safe-graphic-mode" is only visible in the JJ-Version...)

---

### Post by sikander3786 on 2011-03-02
Safe graphics on Lucid and Maverick is achieved by 'nomodeset' parameter. See here.

[http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html](http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html)

---

### Post by Dediggefedde on 2011-03-02
So your advice is to uninstall Ubuntu and try to reinstall it with this guide?

---

### Post by sikander3786 on 2011-03-03
I mean you can retry with Ubuntu Lucid and use the nomodeset parameter if needed.

Or you can try the Ubuntu alternate (text-based) installer. It is not that much difficult.

[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

---

