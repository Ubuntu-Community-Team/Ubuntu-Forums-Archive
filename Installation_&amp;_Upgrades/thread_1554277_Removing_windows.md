---
title: "Removing windows"
date: 2010-08-16
forum: Installation &amp; Upgrades
---

### Post by chris0108 on 2010-08-16
Well iv been using Ubuntu 9.10 now for six months,had a few problems getting the wireless to work properly but its all sorted now.
Iv not used windows on it for a few months so i want to remove windows off the hard drive and give the space back to unbuntu, how do i do this?
Also i want to remove the grub boot so the laptop just boots straight to ubuntu.

Thank you any help offer, Chris

---

### Post by davidmohammed on 2010-08-16
hope [this link]("https://answers.launchpad.net/ubuntu/+question/7194") helps - 

not sure about grub.  You could always just reduce the GRUB_TIMEOUT value to say 1 (or possibly zero?)

save and then run

update-grub

---

### Post by chris0108 on 2010-08-17
Thank you for that, its a very good starting point and will sort out windows no problem. Just grub now.

Many thanks

---

