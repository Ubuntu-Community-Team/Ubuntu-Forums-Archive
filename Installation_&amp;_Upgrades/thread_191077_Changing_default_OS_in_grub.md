---
title: "Changing default OS in grub?"
date: 2006-06-07
forum: Installation &amp; Upgrades
---

### Post by E1000 on 2006-06-07
Ubuntu is fun to tinker arround with but there are still too many windows essentials that I cannot give up. What I would like to do is change the order in GRUB so that windows is the default choice and I have to select ubuntu if I want it.

does anybody how know how to change the default OS in GRUB? maybe if I could shorten my selection time to 5 seconds also, that would be good.

your help is always appreciated
-Evan

---

### Post by confused57 on 2006-06-07
I did a search and this looks like a good thread to explain it:

[http://www.ubuntuforums.org/showthread.php?t=134393&highlight=default+OS](http://www.ubuntuforums.org/showthread.php?t=134393&highlight=default+OS)

Change the "timeout" to however many seconds you want.

Also, you may want to a backup before you edit your menu.lst:

```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
sudo gedit menu.lst
```

If you need to restore:
```
cd /boot/grub
sudo cp menu.lst_backup menu.lst
```

---

