---
title: "I cant use my cd-rom"
date: 2005-01-02
forum: Installation &amp; Upgrades
---

### Post by Matt00 on 2005-01-02
Yes root denies me to use my cd-rom. What should i do :confused: 
I have tried logging as a root but it didnt work.


Help me :sad:

---

### Post by nemin on 2005-01-02
[QUOTE=Matt00]Yes root denies me to use my cd-rom.[/QUOTE]
I think you have to clear up a few things before someone can help you. What do you want exaclty? What do you try? What error do you get?
If you simply want to mount your CD-drive, `mount /dev/cdrom`. When that doesn't work as user, try `sudo mount /dev/cdrom` and post you /etc/fstab here.

Hope this helps.

---

