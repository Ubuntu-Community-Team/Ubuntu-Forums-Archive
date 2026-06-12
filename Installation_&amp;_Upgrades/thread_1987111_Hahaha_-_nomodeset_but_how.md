---
title: "Hahaha - nomodeset but how?"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by LancerNZ on 2012-05-25
After setting "nomodeset" in order to run the live CD and install 12.04 LTS onto my hard drive, when I boot into my new system, my keyboard and mouse are locked.

...let me clarify that: the live CD or USB needs "nomodeset" in grub to work. But after the hard drive install, I don't have the chance to toggle that option.

I'm pretty much 100% sure nomodeset would fix this but there appears to be no options for Grub, just a plain purple screen for a few seconds. Hitting [TAB] there does nothing and it just boots into the login screen with no mouse* or keyboard. I can get into the live CD to fix things but... where do I start?




* Well, actually the mouse does work after a while in that it moves but it can't click anything.

---

### Post by wilee-nilee on 2012-05-25
Chroot to the install from a live cd, open the                            [FONT=Verdana, sans-serif][SIZE=1]/etc/default/grub[/SIZE][/FONT]  add nomodeset in, GRUB_CMDLINE_LINUX_DEFAULT="nomodeset quiet splash"
run a update-grub and you are set.

[https://help.ubuntu.com/community/Grub2/Installing#ChRoot](https://help.ubuntu.com/community/Grub2/Installing#ChRoot)

---

### Post by LancerNZ on 2012-05-25
Ah - hold [Shift] key while it's loading up caused grub to come out of hiding.

....why oh why does Ubuntu hide mission-critical-to-install things like this? It's like they've set it up to preinstall perfectly only on their own favourite hardware.



**Edit:** Thanks for your suggestion. My next question was indeed going to be where that was located.

---

### Post by wilee-nilee on 2012-05-25
I generally use gedit to open edits so this what it would be, it is in root by that point.


```
gedit [FONT=Verdana, sans-serif][SIZE=1]/etc/default/grub[/SIZE][/FONT]
```

---

### Post by LancerNZ on 2012-05-25
Yes thanks. Once I was in at lest once I was able to sudo gedit... (said file). Dunnot why they didn't call "update-grub" "grub-update". I was hitting grub[tab] before to try and autocomple-find options before seeing it was the other way around.

---

