---
title: "Lucid not even booting"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by schmolch on 2010-03-31
It doesn't even get up to grub, just a blank screen.


****ing Bullshit.

---

### Post by VMC on 2010-03-31
More detail. what doesn't boot livecd or an installed ubuntu. Also list some of your hardware. 

since you mentioned grub, you must have installed from either live or alternate cd/usb. If livecd were you able to see the desktop or did you just install first?

---

### Post by schmolch on 2010-04-01
I upgraded my Karmic-Setup on my Desktop (AthlonX-2, Nvidia-Card).
I get a cursor (no prompt though) for a few seconds but the grub-menu never shows up and the screen goes blank. No reaction to any input.

---

### Post by dino99 on 2010-04-01
i dont understand you are asking such a question :rolleyes:

i guess grub have detected a bug into your profile: look at your avatar, that's not serious  :twisted:

As i'm in a good day, i give you some ideas:
- as you have made a dist-upgrade, can you check if grub1 is installed, if so remove/purge everything about grub-legacy
- run grub-install and verify that its correctly installed
- run grub-mkconfig then update-grub
-reboot

---

