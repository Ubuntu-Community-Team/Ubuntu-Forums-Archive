---
title: "Quick question: Grubs"
date: 2007-09-07
forum: Installation &amp; Upgrades
---

### Post by uposer111 on 2007-09-07
I installed Ubuntu and everything is partitioned correctly but when i go into the bootmenu of grubs, it dosnt show my windows vista. I looked at this [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

but that dosnt show my how to add vista OS to the file so it will recognize it.

Thanks

Jeff

---

### Post by Pumalite on 2007-09-07
Post:
specs
sudo fdisk -lu
cat /boot/grub/menu.lst

---

