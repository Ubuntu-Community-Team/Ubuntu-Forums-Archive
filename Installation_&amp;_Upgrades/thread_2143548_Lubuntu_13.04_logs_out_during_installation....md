---
title: "Lubuntu 13.04 logs out during installation..."
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by Matteo Iervasi on 2013-05-09
Hi everybody! I'm new to UbuntuForums and so I hope this is the right place for my question (I'm also italian, so please tell me if I make mistakes).
I have been using ubuntu for 2 years and I have never got any problems during installation.

Four months ago I installed Lubuntu 12.10 on an old HP compaq nx6110, and it works.
Yesterday I downloaded lubuntu 13.04 because I wanted to upgrade it.
So I deleted from windows the lubuntu partition, and then I plugged in the usb stick with lubuntu on it.
I chose "Install Lubuntu" directly from the startup menu. It runs ubiquity but after a while it logs out and it show me the log in menu.
I tried also to install it from a live session, but I got the same result.

I can't understand why...
Is there someone who can help me!

Thanks..

---

### Post by dino99 on 2013-05-09
Check:
- the bios : deactivate everything that can disturb during installation (suspend/hibernate/powersave/...)
- deactivate the other processes that can also disturb : screensaver, app in the background (sound/radio/...)
- if you only have windows installed, then also clean it (chkdsk/defrag/ccleaner)
- about the hardware: stop the overclocking if it exist, and be sure it can grab some fresh air (clean it if required)

So, are you reinstalling via wubi ? or doing a real install ?
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

---

### Post by Matteo Iervasi on 2013-05-10
Thanks for the answer! I solved using the alternate cd!

---

