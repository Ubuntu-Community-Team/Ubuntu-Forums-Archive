---
title: "Hanging while setting xserver-xorg"
date: 2005-06-03
forum: Installation &amp; Upgrades
---

### Post by jerrybme on 2005-06-03
I'm trying to install Hoary 5.04 on my desktop:
AMD64 3000
LanParty Motherboard
ATI 9800 pro
Hauppage 150 TV card

All goes well until it installs & configures the packages after the first reboot. It hangs at
```

setting up xserver-xorg
```
If I reboot it locks up in the app that comes up to trouble shoot unfinished installation, safe mode same problem.

I tried removing the tv card thinking that the installer couldn't handle the extra video options, but same result.

I tried reburning the iso at slower speed to make sure it wasn't a faulty iso burn but same result (m5dsum is ok). Have had the result with the DVD version of Hoary and also tried Breezy with same result.

Live CD works fine. Any suggestions?

---

### Post by jerrybme on 2005-06-06
Turns out it was a setting in my bios that was hanging the system. Unfortunately, I'm not sure what setting was causing the problem. I saw a post with a similar problem that was resolved with a bios change. I went into bios and changed the way IRQs are handled, but when I tried to save the changes & exit bios something happened and it wouldn't even post. So I cleared the CMOS, and Ubuntu installed fine with default bios settings :roll:

---

