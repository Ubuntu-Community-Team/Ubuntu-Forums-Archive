---
title: "Dual booting"
date: 2014-11-26
forum: Installation &amp; Upgrades
---

### Post by draigcoch2 on 2014-11-26
I have just installed Ubuntu 14 (64 bit) on a Sata drive in a new machine.  There is space to add another Sata drive - I have one with XP Pro (32 bit) already in place.  

Ideally I would like to be able to select which OS to use at boot up.

What is the best way to do this?  Is it even possible?

---

### Post by yancek on 2014-11-26
I'm not sure if I'm understanding your post clearly but if you have Ubuntu on one drive on the computer and it boots and you just want to attach the xp from a separate drive, do that and boot Ubuntu and run:  sudo update-grub.  It should find the windows install and add an entry to your boot menu.

---

### Post by oldfred on 2014-11-26
If your XP was on a different system, it probably will not work. It may want to update registration or check that hardware has changed, but there is no more XP, so it cannot update. 
All Windows are configured & licensed to install in one system only.

---

