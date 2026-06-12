---
title: "Bionic Beaver broke Trackpad sensitivity"
date: 2018-06-06
forum: Installation &amp; Upgrades
---

### Post by paulakreuzer on 2018-06-06
I updated to Bionic Beaver yesterday and now my Trackpad reacts really slowly and inaccurately.
The settings for movement speed don't help.
It's really hard to e.g. put the pointer on the right spot in a written text to correct an error. If I just need to move the cursor a little bit I regularly overshoot the target.

I'm using a Laptop why! P775DM3 17,3''

Oh and one other thing that no longer works since the update is adjusting the backlight of the screen.

---

### Post by monkeybrain20122 on 2018-06-06
Try 
```

sudo apt install xserver-xorg-input-synaptics
```

if it says already installed then remove it.

also "upgrade" (instead of a clean install) probably accounts for half of the problems in the installation and upgrade thread; or if you must upgrade instead of a clean install for whatever reason, hold off til 18.04.1

---

### Post by paulakreuzer on 2018-06-06
Awesome. Thanks! :)

---

### Post by paulakreuzer on 2018-06-08
Does anybody have an idea how I could fix the trackpad?
It's really annoying. I keep clicking the wrong buttons.

---

### Post by paulakreuzer on 2018-06-16
The trackpad issue evolved a bit.
Additionally to being inaccurate now the pointer moves very slowly to the left and to the top-left most of the times. All other directions work as they should.

---

