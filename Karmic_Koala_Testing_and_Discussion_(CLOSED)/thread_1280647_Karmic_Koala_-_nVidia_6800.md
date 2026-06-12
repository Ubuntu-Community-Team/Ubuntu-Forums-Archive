---
title: "Karmic Koala - nVidia 6800"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dasunsrule32 on 2009-10-02
I have tried installing Karmic with both the Alternate install CD and the Desktop ISO 32-bit, and I get the same result. I am a bit miffed at this point.

When GDM starts, the PC freezes, screen garbles and I cannot ctrl+alt+1-6 to access a console. Any ideas on how I can get this installed?

Dell Dimension 9150, with Pentium D 3ghz, 2gb RAM, nVidia 6800. Thank you in advance. :P

---

### Post by dasunsrule32 on 2009-10-02
I have now tried the 64-bit release and it hangs just after * checking battery state...   [Ok] ...done.

---

### Post by jbicha on 2009-10-03
Just after the bios screen, hold down Shift to get to the Grub menu.
Select recovery mode
Once the system boots into the recovery menu, select netroot
sudo aptitude update
sudo aptitude install nvidia-glx-185
sudo nvidia-xconfig
sudo reboot

---

### Post by dasunsrule32 on 2009-10-23
> **jbicha said:**
> Just after the bios screen, hold down Shift to get to the Grub menu.
Select recovery mode
Once the system boots into the recovery menu, select netroot
sudo aptitude update
sudo aptitude install nvidia-glx-185
sudo nvidia-xconfig
sudo reboot

Ok, I will give this a try and see how it works. I will have to do the alt install first, otherwise it just will not work. Thanks!

---

