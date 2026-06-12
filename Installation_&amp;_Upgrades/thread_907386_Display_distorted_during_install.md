---
title: "Display distorted during install"
date: 2008-09-01
forum: Installation &amp; Upgrades
---

### Post by BlueTesla on 2008-09-01
I am trying to install Ubuntu on my computer.

Initially everything is fine. I get the language selection, and then a list of options. I select either "Install" or "Try Ubuntu...", and then it loads normally. However, after it is done loading, my monitor displays an out of range error. I can press ctrl+alt+[+] to change the resolution, but all I get is a garbled mess. I can make out the colours and the mouse moving, but it is far too distorted to do anything.

I have tried using Safe Graphics mode to no avail, and everything I've found on Google seems to be used after installation.

I am new to Linux so this may be something simple I am overlooking.

Thanks for any help you can give :).

ATI 9600 AIW, AMD Athlon64 3200+, Asus K8V-X Motherboard, 1.5 Gigs RAM, 2 hard drives IDE.

---

### Post by overdrank on 2008-09-01
> **BlueTesla said:**
> I am trying to install Ubuntu on my computer.

Initially everything is fine. I get the language selection, and then a list of options. I select either "Install" or "Try Ubuntu...", and then it loads normally. However, after it is done loading, my monitor displays an out of range error. I can press ctrl+alt+[+] to change the resolution, but all I get is a garbled mess. I can make out the colours and the mouse moving, but it is far too distorted to do anything.

I have tried using Safe Graphics mode to no avail, and everything I've found on Google seems to be used after installation.

I am new to Linux so this may be something simple I am overlooking.

Thanks for any help you can give :).

ATI 9600 AIW, AMD Athlon64 3200+, Asus K8V-X Motherboard, 1.5 Gigs RAM, 2 hard drives IDE.

HI and welcome, I have the ATI 9600 with no issues, You may try and check the cd for errors and how fast did you burn the ISO? Also may do a checksum on the ISO
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by BlueTesla on 2008-09-01
Thank you for your relpy.

I have done the MD5 check and it seems to check out. I should mention that I have tried several burns of the iso with the same results. I burned iso using every speed available to me. Good thing cd are cheap :).

I have also tried to install it through Windows using WUBI, which results in a successful install but the same distortion when it boots.

---

### Post by overdrank on 2008-09-01
> **BlueTesla said:**
> Thank you for your relpy.

I have done the MD5 check and it seems to check out. I should mention that I have tried several burns of the iso with the same results. I burned iso using every speed available to me. Good thing cd are cheap :).

I have also tried to install it through Windows using WUBI, which results in a successful install but the same distortion when it boots.

Ok then this idea has helped others so lets try it here. You can try and boot into recovery mode which is usually the second option from the grub and use the xfix option and hopefully this will correct your graphics.

---

### Post by BlueTesla on 2008-09-01
I am now posting from inside Ubuntu!

Turns out that my monitor was having problems with the initial resolution ubuntu starts in and couldn't display it properly.

Everything is peachy now!

Thank you so much for your time and help! It is much appreciated!

---

