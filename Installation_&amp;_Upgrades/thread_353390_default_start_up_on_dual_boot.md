---
title: "default start up on dual boot"
date: 2007-02-04
forum: Installation &amp; Upgrades
---

### Post by celticbhoy on 2007-02-04
I have just installed version 6.10 on a dual boot system which was already running xp. As I am a complete novice at linux, could anyone let me know how to set XP as the default startup option, as other users of the PC would feel more comfortable to just turn the PC on and get the XP logon screen.

---

### Post by thelocust on 2007-02-04
[B]
Check out [GrubEd]("http://ubuntuforums.org/showthread.php?t=228104"). It will give you what your looking for and many other options but dont forget to back up your boot folder before doing anything. :cool:

[/B]

---

### Post by celticbhoy on 2007-02-04
tanx got grubed, but how do i back up folder

---

### Post by bulldog on 2007-02-04
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_bak
```

---

