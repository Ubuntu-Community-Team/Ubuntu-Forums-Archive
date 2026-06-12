---
title: "Need help, booting to black screen with Ubuntu 13.10."
date: 2014-02-14
forum: Installation &amp; Upgrades
---

### Post by davewhelchel on 2014-02-14
I just installed Ubuntu 13.10 on a Toshiba Satellite C55-A and after the Ubuntu logo appears the screen goes black. I've searched the forums and spent a lot of time on google searching for answers but I can't find anything that helps. I've tried installing Ubuntu 12.04, 12.10, and 13.04 also with the same results. I also tried replacing 'quiet splash' with nomodeset and several other options that I've seen in other threads. Secure boot and quick boot are disabled and UEFI mode is enabled in the BIOS. I would greatly appreciate any help.

---

### Post by skippsav on 2014-02-15
One thing I've found so far in my (unsuccessful) attempts to install Ubuntu on a new Lenovo laptop is that it suddenly sets the screen brightness to 0 so the screen goes totally black. Use the function keys to put the screen brightness up and you may find it is not a blank screen after all - maybe...

---

### Post by bc.haynes on 2014-02-15
Tell us a little more about your video card. Enter in Terminal:
```
lspci | grep VGA
```

---

### Post by davewhelchel on 2014-02-15
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8400]

I downloaded and installed Ubuntu 14.04 and everything worked great. Not sure if the problem was with the graphics card or something else but the newest version of Ubuntu didn't have any issues. Hopefully this helps someone.

---

