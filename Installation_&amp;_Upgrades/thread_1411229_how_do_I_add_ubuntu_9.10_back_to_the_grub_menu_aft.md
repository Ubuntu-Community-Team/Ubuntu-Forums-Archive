---
title: "how do I add ubuntu 9.10 back to the grub menu after installing ununtu studio 8.04"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by _nate on 2010-02-19
I recently installed ubuntu studio 8.04 on a new partition and now ubuntu 9.10 is no longer showing up in the grub boot menu. How can I boot into ubuntu 9.10 and how do I edit the grub menu so it shows up again?

---

### Post by hhlp on 2010-02-19
see part 13 :

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by darkod on 2010-02-19
You shouldn't have let Studio to install grub. You control that in Advanced settings in the last screen. If you already have one grub (from 9.10), that's all you need. Plus 9.10 comes with the new grub2.

I would reinstall grub2 to the mbr of your disk, and once you boot 9.10 just do

sudo update-grub

and it will detect your Studio and add it to the list.

Otherwise, if you want to keep using Studio grub, you need to add an entry in menu.lst manually for 9.10.

---

### Post by _nate on 2010-02-19
Currently /dev/sda2 has a * next to Boot.  Is this the device I should mount and install it onto? fyi sda2 is a windoze partition

---

### Post by _nate on 2010-02-19
I was able to get Grub2 installed. I can boot into windoze and ubuntu 9.10 but it didn't recognize unbuntu studio though. How do it get it to recognize the partition?  Do I have to add it manually?

---

### Post by _nate on 2010-02-19
got it!  all I need to do was run sudo update-grub in ubuntu 9.10.  thanks for pointing me in the right direction.

---

