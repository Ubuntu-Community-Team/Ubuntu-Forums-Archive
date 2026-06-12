---
title: "USB problems - stalls at preparing to install stage"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by chicTragic on 2010-11-17
I've been trying Ubuntu out for the past few months with Wubi, and decided to install it properly.

I downloaded 10.10 32bit via torrent, then used the '[Installation From USB Stick Quick]("https://help.ubuntu.com/community/Installation/FromUSBStickQuick")' guide. Doing everything on Windows, not Wubi. I tried a number of different combinations in the BIOS to try and get it to boot from the USB, without any success. Thinking that Wubi might be interfering I removed it and tried again, but nothing. I then tried different usb creators (usb creator and UNetBootin), and BIOS combinations, again without success.So I installed plop.

I booted the USB without problems, and started the install. Selected language, forward to preparing to install, it showed all green ticks, I selected the other two boxes, hit forward ... and nothing happened. I waited a good 20 to 30 minutes. I quit the install, tried again, but this time without selecting the additional boxes. Still nothing. I tried the other creators again. I then left it sitting their for six hours, and it still hadn't moved past the preparing to install screen. I tried using UNetBootin and letting it download a new ico. I then tried it by downloading another ico from the site directly. No success.

There's no error messages, it simply doesn't do anything once I click forward from the preparing to install screen.

Any help would be greatly appreciated.

---

### Post by C.S.Cameron on 2010-11-17
Ubuntu needs at least 256MB RAM if not more.
If you don't have this much RAM there are a few other distros that are good.

I would think that if WUBI was working a Full install should also work.

---

### Post by chicTragic on 2010-11-17
I am so sorry, how foolish of me *facepalm*

I'm attempting to install to a NEC Versa L2200 laptop with 2gig RAM, currently has Vista. The optical drive is dead, which is why I've been attempting the USB install.

---

### Post by chicTragic on 2010-11-18
I've managed to install Ubuntu. I reinstalled Wubi to see if making a USB on that would have any difference. It didn't. But I then went back to the Windows side and made another USB copy with the universal, and ran it with Wubi still installed, and it worked. No sure why, can only assume it was some combination of things.

---

