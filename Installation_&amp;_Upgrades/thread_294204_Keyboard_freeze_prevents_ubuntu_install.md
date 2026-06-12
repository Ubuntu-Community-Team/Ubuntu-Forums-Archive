---
title: "Keyboard freeze prevents ubuntu install"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by phildacey on 2006-11-06
hello, I am trying to install ubuntu on my friends computer and am  experiencing a very frustrating problem. I boot from CD, choose the type of installation (with the keyboard) and the os loads, except that my ps2 keyboard is frozen and I can't input any text. 

I have tried three different keyboards, the same happens every time. 

I have tried ubuntu live installer, ubuntu CLI installer, debian sarge, zenwalk and the knoppix live CD. the same happens every time, ps2 keyboard freezes after the os loads, even though it was working before the os loaded.

The same happens to the ps2 mouse. my usb mouse is not affected.

the keyboard and mouse work fine in windows (did work fine, windows has gone now).

any ideas? its hard to debug this problem without being able to type anything in! oh, and I tried to get the onscreen keyboard working on the ubuntu live CD and failed.

---

### Post by phildacey on 2006-11-06
okay, so this is the solution. If your keyboard isn't working when you try to install linux you might be suffering from this [bug]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/54836") (Bug #54836)

the workaround is to clatter the keyboard when the system is booting up. seriously.

thanks to the kind people at the #ubuntuforums irc channel on freenode who worked through this with me : )

---

