---
title: "Blank Terminal After Update"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by amtur_poet on 2013-01-21
I recently installed some updates to my laptop running Ubuntu 12.10, as well as installed a proprietary driver for the Nvidia Geforce GTX 560M 3D graphics card I have in my Toshiba Qosmio X775-3DV78 laptop. I did so via the Restricted Drivers application that used to come with Ubuntu. But, after installing these updates, after selecting Ubuntu from the Grub menu on boot (I have it dual-booted with Win8), all I see is a blinking text prompt that never leaves. My keyboard does nothing, and neither does any other button on my machine, save for the power button, which does run the standard shutdown text. What can I do to fix this?

---

### Post by gordintoronto on 2013-01-21
Additional Drivers is now part of "software sources".

If you boot into recovery mode and run this command, it might get you going again:
sudo apt-get autoremove nvidia-current

---

### Post by amtur_poet on 2013-01-25
> **gordintoronto said:**
> Additional Drivers is now part of "software sources".

If you boot into recovery mode and run this command, it might get you going again:
sudo apt-get autoremove nvidia-current
When I try that, it tells me it cannot write to /var/cache/apt.

---

### Post by raja.genupula on 2013-01-25
There you have to remove the lock file.but proper and complete solution we can give you if you give us the full details.

---

### Post by amtur_poet on 2013-01-25
> **raja.genupula said:**
> There you have to remove the lock file.but proper and complete solution we can give you if you give us the full details.
Sure; what do you need to know?

---

### Post by sandyd on 2013-01-25
**moved to installations and upgrades**

---

### Post by amtur_poet on 2013-01-25
So, what do I need to do?

---

### Post by amtur_poet on 2013-01-25
Oh dear God, help me! I tried to reinstall Ubuntu over the old partition, but when I try to boot my laptop, it says this:
[http://i.imgur.com/mDCC4yi.jpg](http://i.imgur.com/mDCC4yi.jpg)

---

### Post by raja.genupula on 2013-01-28
Ok its your GRUB . put the primary boot partition as your bootable device.

---

