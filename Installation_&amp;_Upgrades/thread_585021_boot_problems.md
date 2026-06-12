---
title: "boot problems"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by scytale1980 on 2007-10-21
hi!

after intsalling ubuntu dapper drake 6.06 on a friends laptop (asus pro 80 series) there was a mysterious error: the grub loader only offered ubuntu for booting although there was still windows 
vista on the machine. after booting ubuntu we were able to change the grub loader manually 
(we added the windows vista boot option). it seemed to work quiet good. but this option only exists 
for one boot of ubuntu or vista. after a second restart there is only the ubuntu-option again.

is there a chance for a permanent change of teh grub loader?

many thanks!

---

### Post by Pumalite on 2007-10-21
Post:
sudo fdisk -lu
cat /boot/grub/menu.lst

---

### Post by scytale1980 on 2007-10-21
i will try ;)
thanks :)

---

