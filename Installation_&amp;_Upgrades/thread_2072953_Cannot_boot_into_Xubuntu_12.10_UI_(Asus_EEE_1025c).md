---
title: "Cannot boot into Xubuntu 12.10 UI (Asus EEE 1025c)"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by SoggyPinata on 2012-10-18
Hi everyone,

I just finished downloading and installing Xubuntu 12.10 on my Asus EEE 1025c netbook and when I tried booting into the OS I am immediately faced with the linux terminal login screen and nothing else.

Once I login through the terminal, I cannot access the XFC UI or anything. Can anyone tell me what exactly is going on?

Thank you for your time.

---

### Post by twodogs on 2012-10-18
you can try 'startx' in terminal

if that doesn't work, I would re-install

---

### Post by SoggyPinata on 2012-10-18
> **twodogs said:**
> you can try 'startx' in terminal

if that doesn't work, I would re-install

Thanks for replying.

I started off with a fresh install of Xubuntu 12.10. I tried to issue "startx" but I get a following error message saying "Fatal Error: No Screens found".

Did they discontinue supporting the graphics driver for the Asus EEE 1025C pc?

---

### Post by twodogs on 2012-10-19
> **SoggyPinata said:**
> Thanks for replying.

I started off with a fresh install of Xubuntu 12.10. I tried to issue "startx" but I get a following error message saying "Fatal Error: No Screens found".

Did they discontinue supporting the graphics driver for the Asus EEE 1025C pc?

wow.  I thought that would work.  I used to have an asus eeepc and never had problems. I'm now on asus u51e and running xubuntu for first time.

to fix your problem, if it was me, I would do a re-install.  I assume you can run xubuntu in 'live' mode?  If you can that would tell me your usb is good to go.  If not, re-install xubuntu on the usb (use unetbootin).

after installation, I have never installed a graphics driver.  never had to. let me know what happens if you decide to re-install.

---

### Post by Nordicnurse on 2012-10-20
> **SoggyPinata said:**
> Thanks for replying.

I started off with a fresh install of Xubuntu 12.10. I tried to issue "startx" but I get a following error message saying "Fatal Error: No Screens found".

Did they discontinue supporting the graphics driver for the Asus EEE 1025C pc?

Could it be this? I have trouble getting X up on the device and symptoms match these... [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1069031](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/1069031)

---

### Post by twodogs on 2012-10-21
You could try one more thing...

Instead of 'startx' try this --> 'startxfce4' and see if that works. If it doesn't work then I would look into Nordicnurse's response.

Hope this helps.

---

