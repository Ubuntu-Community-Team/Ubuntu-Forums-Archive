---
title: "No bars or menus"
date: 2009-04-12
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nyto on 2009-04-12
Hi,

I installed 9.04 beta today, upgrading from 8.10.

After I log in, I get an entirely black screen, the only way I can bring anything up, is by using the hotkey to open my terminal, and then open things like firefox from the terminal window.

I have no top bar with the menus like applications/places/system and the clock, nor do i have the bottom bar which has the windows open.

Also, I can't change between windows using alt+tab.

Anyone got any ideas on how I can get those back, or revert back to 8.10 (I have the live CD), without doing a full wipe.

(I also submitted a bug on Launchpad, [https://bugs.launchpad.net/ubuntu/+bug/360186](https://bugs.launchpad.net/ubuntu/+bug/360186))

Thanks.
// Nyto

---

### Post by miegiel on 2009-04-12
You can't downgrade, if you want to go back to intrepid you'll need to reinstall. However if you make a separate /home partition, you can move your homedir there and during reinstallation use the manual partition option to select that partition to be mounted as /home. This way you'll at least save your documents and configuration. 

Next time you want to try a beta it's safer to make a dual boot ;) You can also use the same /home and swap partitions for both linuxes. And, in most circumstances, you'll only need a 20GB root partition if you have a separate /home partition. So you won't loose to much disk space having 2 linuxes on your disk.

A safe way to repartition or resize partitions is using gParted when you booted from the live-CD. Alternatively you can use the [_gParted live-CD_]("http://gparted.sourceforge.net/livecd.php")

As for your jaunty problem. I can't think of anything better then :
```
sudo apt-get remove ubuntu-desktop
sudo apt-get install ubuntu-desktop
```

---

### Post by nyto on 2009-04-12
Thanks for the quick reply miegel.

I've solved my problem now by choosing GNOME session at login.

// Nyto

---

### Post by miegiel on 2009-04-12
great :)

---

