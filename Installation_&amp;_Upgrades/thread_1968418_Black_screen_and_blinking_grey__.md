---
title: "Black screen and blinking grey _"
date: 2012-04-29
forum: Installation &amp; Upgrades
---

### Post by LolxD on 2012-04-29
I made Ubuntu 12.04 USB stick with unetbootin. Now when i try to boot up from it, i get black screen and blinking grey _ sign. What causes this, is it my GPU, which is connected to a screen with HDMI?

---

### Post by darkod on 2012-04-29
It can be a video driver issue. Not sure how unetbootin changes the main menu of ubuntu.

Otherwise you can hit Esc when the cd/usb starts loading and that will show a main menu. With F6 you can open advanced options, select nomodeset parameter, and then use Try Ubuntu from the main menu to boot into live mode.

That is the most common parameter for video issues.

---

