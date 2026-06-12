---
title: "Customization of 10.04 Livecd - Going directly to desktop"
date: 2010-05-20
forum: Installation &amp; Upgrades
---

### Post by jakv on 2010-05-20
The new 10.04 livecd diverts to a dialog asking if you want to go to livecd or install, which makes sense (shifting the choice away from grub, etc). However, I want to go directly to desktop: does anyone know exactly where in the boot process this diversion happens? I have a suspicion that it happens before the autologin, or somewhere thereabouts, but I haven't found anything after poking around initrd.lz. Does anyone have any ideas about where to find the script that invokes the dialog?

EDIT: I'm sorry if this is the wrong place to post this question. Move as you wish.

---

### Post by JustinR on 2010-05-20
I'm not sure if this is what your talking about but when you start the Ubuntu live CD, during the purple screen with the keyboard and language icons press any button and it will go from there.

---

### Post by jakv on 2010-05-20
That gives me the right behavior, but not quite good enough: I now think that it's running ubiquity when not given input in the first screen: however, I'm aiming for 'pop in the cd and walk away while getting to the desktop', so now my question is how to disable ubiquity. I'll be working on the problem.

---

### Post by jakv on 2010-05-20
Okay, I just purged ubiquity: not the best solution, but good enough.

---

