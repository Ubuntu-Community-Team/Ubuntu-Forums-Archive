---
title: "Shut off computer during installation-now I only have a black screen during boot"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by teekay13 on 2010-12-07
Okay, I installed Ubuntu Server 10.10 32-bit to my Gateway Solo 5300 using Unetbootin. After it asked me what to do with my hard drive I selected to use entire disk, hence deleting all that was on it. 

The problem is, it was taking a while, it was late at night and I had to get up early the next morning so I decided to shut off the laptop when it had asked me to select other software to install. At this point it said only the core components were installed and when I turned on the laptop the next day it only came to a black screen with a flashing underscore in the top left corner.

How can I fix this?

---

### Post by oldfred on 2010-12-07
IF you are installing with the alternate installer, you do not have  a liveCD. You need to download a liveCD. 

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] paste here [ /code] tags.

Or you can just reinstall. The issue may be where it installed grub or how it installed it.

---

### Post by teekay13 on 2010-12-07
Okay, I installed Ubuntu Server 10.10 32-bit to my Gateway Solo 5300 using Unetbootin. After it asked me what to do with my hard drive I selected to use entire disk, hence deleting all that was on it. 

The problem is, it was taking a while, it was late at night and I had to get up early the next morning so I decided to shut off the laptop when it had asked me to select other software to install. At this point it said only the core components were installed and when I turned on the laptop the next day it only came to a black screen with a flashing underscore in the top left corner.

How can I fix this?

---

### Post by teekay13 on 2010-12-07
Thanks for your quick replies, but I have already tried to reinstall the OS from my USB but it does not recognize it during boot. I have changed the boot preferences/settings so that removable devices was first but it still goes to the same screen.

(Also, the cd drive does not work)

---

### Post by MooPi on 2010-12-07
Your going to have to start from scratch. Shoulda just let it finish. Nothing lost so the reinstall is best option.

---

### Post by drs305 on 2010-12-07
Duplicate threads merged. Please do not create multiple threads on the same issue.

---

### Post by restorator on 2010-12-07
> **teekay13 said:**
> Okay, I installed Ubuntu Server 10.10 32-bit ......
..came to a black screen with a flashing underscore in the top left corner.


The server version has no GUI so you should only have a blinking cursor in the top left corner. This is normal. But you should have a command propmt not just an underscore. 
I would do a fresh install anyway just to make sure everything is right.

---

### Post by teekay13 on 2010-12-07
The only problem is that I originally installed it within windows and now that it has been removed, I can't. The usb or cd drive is not recognized during boot and I have changed the boot preferences so that either were first in order. 
Why is this and how can I fix it?

---

### Post by Dyamalos on 2010-12-07
That sounds more like a BIOS issue. Does the BIOS still run as it had before? If I remember the right key for gateway, does anything happen when you hit F2 on power-on before the BIOS starts loading from disks?

Even if you had powered off during the install copying files, that would have just given you a non working (or half working) install that would need to be redone. Odds are if it's not the BIOS, the boot loader wasn't installed correctly.

---

### Post by teekay13 on 2010-12-07
Might I be able to do a network boot?

---

