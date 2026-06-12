---
title: "USB keyboard doesn't work on 7.10"
date: 2008-02-22
forum: Installation &amp; Upgrades
---

### Post by ForceUser on 2008-02-22
I'm using a generic Dell USB keyboard, everything works fine until I get to the install screen (GRUB?). I'm using the text based installation so there's no countdown to use the default action, the keyboard refuses to respond as soon as that screen shows up.

---

### Post by ForceUser on 2008-02-23
Er also I'm using a Live cd, and this keyboard has always worked fine and just doesn't work in this situation. I've also tried the regular installation and I still can't use the keyboard, but I have a 30 second countdown until the default option is selected. In the regular installation it freezes at 15% so I've heard use the text based alternative is a good idea.

---

### Post by nilarimogard on 2008-02-23
Try to enable usb legacy support in bios.

---

### Post by ForceUser on 2008-02-23
> **nilarimogard said:**
> Try to enable usb legacy support in bios.
Thanks for the reply, I don't see it anywhere though. Here's a picture:
[IMG]http://i26.tinypic.com/6ypou8.jpg[/IMG]

---

### Post by TransitMan on 2008-02-23
Onboard Devices -> USB Controller should be Enabled/On
Onboard Devices -> Rear Quad USB should be Enabled/On
Onboard Devices -> Rear Dual USB should be Enabled/On

That is where the settings for your USB ports are located and can be set to either be Enabled/On or Disabled/Off.

---

### Post by ForceUser on 2008-02-23
Yeah they're all on and USB for FlexBay is on "OnBoot".

---

