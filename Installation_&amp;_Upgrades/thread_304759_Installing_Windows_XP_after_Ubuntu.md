---
title: "Installing Windows XP after Ubuntu"
date: 2006-11-22
forum: Installation &amp; Upgrades
---

### Post by kampsuniahv on 2006-11-22
I need to install Windows XP on my 40GB hdd besides Ubuntu. My current partitons are:
10GB - /
32MB - boot
512MB - swap
other space - /home

I would like to make another partionon (10GB) from my /home partion and install XP on that and i thin i need somesort of "trading post" for those to OSes.  What's the best way to do that.

Thanks

Hendrik

---

### Post by renzokuken on 2006-11-22
it will involve editing your grub file, but try searching the forums or wiki, ive seen a few threads/howtos about this

---

### Post by ssalman on 2006-11-22
Two points:

1- windows expect to be on the first primary partition of your HD, it will be simpler if you grant it what it expects!

2- windows will overwrite your HD MBR which will disable grub and you won't be able to boot ubuntu, but you can easily fix that using [this]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") wiki page.


good luck

---

