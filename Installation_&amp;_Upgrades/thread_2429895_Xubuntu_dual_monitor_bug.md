---
title: "Xubuntu dual monitor bug"
date: 2019-10-24
forum: Installation &amp; Upgrades
---

### Post by Keith_Helms on 2019-10-24
I was trying to install Xubuntu 18.04 on a system that has 16.04 installed and leave that system intact.  I booted the install from a thumb drive, went throught the first couple of prompts and then selected "something else" for the install type.  The partition screen came up and I highlighted the empty partition I wanted to install into and when I clicked on "change" the install just seemed to freeze.

After googling install freeze and UEFI for hours, trying 2 different service packs (18.04.3 and 18.04.2), and messing with BIOS settings for UEFI, I finally figured out that Xubuntu had decided to display the prompt for setting up that partition on a TV that I had attached by HDMI and that was turned off instead of on the DVI monitor where all the other install activity had been shown.  Why the heck would it do that???

---

### Post by uRock on 2019-10-24
Every installer I've used ends up using the largest screen as the primary. I am surprised it showed you any of the installer on the monitor you're using.

---

### Post by Keith_Helms on 2019-10-24
Since both the monitor and the TV were 1080P screens, neither was larger.

---

### Post by uRock on 2019-10-24
They're also the same physical size? When I look in Display Settings, the system sees the resolution and the physical size. I do find it odd that the installer would show on one screen and open child windows on another monitor. I've only seen it do that with Gnome, whether Debian or Ubuntu.

---

### Post by Keith_Helms on 2019-10-24
Well, it's a 32" TV and a 23" monitor, so the TV is somewhat larger.  If the install consistently used one or the other, that would be understandable.  It was the bit where it started on the monitor and then tossed a configuration window up on the TV (which was turned off!) that caused me to waste hours.

---

