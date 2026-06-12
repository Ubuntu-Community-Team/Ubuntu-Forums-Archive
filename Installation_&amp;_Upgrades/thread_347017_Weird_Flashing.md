---
title: "Weird Flashing?"
date: 2007-01-26
forum: Installation &amp; Upgrades
---

### Post by Opeth115 on 2007-01-26
I just installed ubuntu and when i go to do a reboot it gets to the ubuntu logo and loads through that but then it just flashes a lot and dosn't continue to anything.  I have left it on over night even.  any body have any suggestions on what to do?

---

### Post by dannyboy79 on 2007-01-26
bootup into recovery mode and reconfigure your xserver. sounds like a classic graphics card issue. you'll have to gogle how to do these things as I forget off hand. oh yeah, booting into recovery mode is easy, when grub starts, hit esc, then chose the recovery mode. as far as reconfiguring your xserver. type in sudo dpkg-reconfigure xserver-xorg in a terminal. go thru each thing and if you know the answer than enter itm when in doubt and you don't know the answer, just accept the default. this should do it for ya. have you tried to install any graphics drivers? if so, that probably screwed up your xserver config.

---

