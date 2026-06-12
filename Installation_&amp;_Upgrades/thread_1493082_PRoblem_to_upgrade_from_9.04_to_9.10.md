---
title: "PRoblem to upgrade from 9.04 to 9.10"
date: 2010-05-25
forum: Installation &amp; Upgrades
---

### Post by mjsomn on 2010-05-25
hello to ubuntu forum
last month i had ubuntu 9.04 on my pc but i formated and i install 9.10 then i formated again with windows xp and now i want to install again the 9.10..
but when i try to install at the boot ubuntu dosent boot up =/
also fedora(12),opensuse and ubuntu 9.10 but with ubuntu 9.04 everything is ok..
i try to upgrade from 9.04 to 9.10 using update manager but when i restart my pc ubuntu doesnt boot up
what happen?

sry for my bad for english :(

---

### Post by dino99 on 2010-05-25
grub2 dont work if grub1 and menu.lst still installed: only grub-pc and grub-common have to be installed, then:

sudo grub-mkconfig
sudo update-grub

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by mjsomn on 2010-05-25
thanks but can i find greek how to or something else with picture because i cant understand

---

### Post by mjsomn on 2010-05-25
with only that "sudo update-grub" i am ok?

---

