---
title: "remove efi boot entry"
date: 2017-03-15
forum: Installation &amp; Upgrades
---

### Post by nestek on 2017-03-15
[IMG]http://i.imgur.com/Mar7HoG.png[/IMG]


I'm trying to delete the Mac OS X efi boot entry off the list.  Which number is the correct one from this image to use this command "sudo efibootmgr -b ? -B"?

---

### Post by nestek on 2017-03-15
Never mind,I got inpatient and got it delete correctly.  
sudo efibootmgr -b 80 -B

---

### Post by ubfan1 on 2017-03-15
The man pages are always a good source of such information:
man efibootmgr

---

