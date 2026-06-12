---
title: "Garbled display in live cd"
date: 2010-04-29
forum: Installation &amp; Upgrades
---

### Post by ukyo_rulz on 2010-04-29
I downloaded the iso today and burned it onto a CD, but the display keep going haywire on me and I don't know what's wrong. Basically I see a purple screen where I may or may not press a key to choose a language and start the live environment. Whether I press a key or not, I get an "ubuntu" screen with five dots lighting up to signal processing. Then suddenly everything goes crazy and the display turns into a sort of garbled, striped mess. If I chose to press a key above and try to boot into a live environment I can even hear the ubuntu startup sound, but the display is still whacked and the controls are unresponsive as far as I can tell.

Laptop Specifications:
Asus K40IN
Duo T6600
4G Memory
Nvidia GeForce G102M, 512 MB VRam (could this be the root of my problems?)

---

### Post by neuroscientist on 2010-04-29
I am experiencing the same thing. Hopefully someone will come along with an answer.

---

### Post by cuberts on 2010-04-29
> **ukyo_rulz said:**
> I downloaded the iso today and burned it onto a CD, but the display keep going haywire on me and I don't know what's wrong. Basically I see a purple screen where I may or may not press a key to choose a language and start the live environment. Whether I press a key or not, I get an "ubuntu" screen with five dots lighting up to signal processing. Then suddenly everything goes crazy and the display turns into a sort of garbled, striped mess. If I chose to press a key above and try to boot into a live environment I can even hear the ubuntu startup sound, but the display is still whacked and the controls are unresponsive as far as I can tell.

Laptop Specifications:
Asus K40IN
Duo T6600
4G Memory
Nvidia GeForce G102M, 512 MB VRam (could this be the root of my problems?)are you sure that you mounted the iso image correctly?

---

### Post by ukyo_rulz on 2010-04-29
I'm pretty sure I'm doing it right. Done the same thing many times before.

---

### Post by ukyo_rulz on 2010-04-29
I think this is my problem:
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/567579]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/567579")

---

