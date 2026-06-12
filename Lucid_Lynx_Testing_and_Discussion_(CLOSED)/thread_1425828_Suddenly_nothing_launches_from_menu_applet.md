---
title: "Suddenly nothing launches from menu applet"
date: 2010-03-09
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by macstevejb on 2010-03-09
Click on menu applet inside gnome-panel and no programs can be opened...if it is attempted, the gnome panel behaves like the autohide feature and fails to open selected program.

This behaviour seems to be particular to the main menu applet...if it is removed and replaced with the alternative menu bar applet then normal behaviour resumes.

The recent batch of updates has somehow affected the way the gnome-panel interacts with the menu applet with regard to the launching of programs.

Can anybody else throw new light on this please?

regards

---

### Post by Didius Falco on 2010-03-09
I'm getting the same problem.

I've filed a bug report on that here: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535327](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535327)

Regards,

Didius

---

### Post by kansasnoob on 2010-03-09
I notice with apps like Firefox that I have in the panel they launch from the panel but not from the menu. Other apps, eg: synaptic, gcalctool, gparted, will not launch from the menu but launch fine from CLI.

I like it:D

That's what I expect in development.

Oh and the panel momentarily disappears while trying to launch an app from the menu.

---

### Post by soapytheclown on 2010-03-09
mine work fine on menus panelsand via cli !!

---

### Post by lonniehenry on 2010-03-09
I have noticed this occurring kansasnoob.  I am noticing it and wonder what updates caused it.  I suspect the gnomepanel updates today. Will look at logs if i can.

edit: I am showing segfaults in gnomepanel as such

Mar  9 18:56:47 lucid-laptop kernel: [ 1266.277813] gnome-panel[3657]: segfault at 3a ip 00007f6a48e57ae4 sp 00007fff862d41b0 error 4 in libgtk-x11-2.0.so.0.1906.0[7f6a48dbf000+461000]
Mar  9 18:58:21 lucid-laptop kernel: [ 1359.990233] #
Mar  9 18:58:21 lucid-laptop kernel: [ 1360.450134] #
Mar  9 18:58:22 lucid-laptop kernel: [ 1361.200128] #
Mar  9 18:58:22 lucid-laptop kernel: [ 1361.500102] #
Mar  9 18:58:22 lucid-laptop kernel: [ 1361.950128] #
Mar  9 18:58:26 lucid-laptop kernel: [ 1364.978085] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 144
Mar  9 19:00:21 lucid-laptop kernel: [ 1480.130132] #
Mar  9 19:00:21 lucid-laptop kernel: [ 1480.430103] #
Mar  9 19:00:22 lucid-laptop kernel: [ 1481.180233] #
Mar  9 19:00:22 lucid-laptop kernel: [ 1481.630126] #
Mar  9 19:00:22 lucid-laptop kernel: [ 1481.930221] #
Mar  9 19:00:26 lucid-laptop kernel: [ 1484.972494] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 144
Mar  9 19:00:54 lucid-laptop kernel: [ 1513.578657] gnome-panel[3715]: segfault at 3a ip 00007f9e7e5b8ae4 sp 00007fffc0a133b0 error 4 in libgtk-x11-2.0.so.0.1906.0[7f9e7e520000+461000]

---

### Post by cyberkilla on 2010-03-09
Just started happening for me after updating a few minutes ago...

There WAS a gnome-panel update too.

---

### Post by lonniehenry on 2010-03-09
I can use the menu to add launcher to the panel that work. Just can't launch from menus. Off to look at Launchpad for bugs.

---

### Post by Dilutu on 2010-03-09
Just noticed that with the last update. Going back to alt+t.

---

### Post by tekstr1der on 2010-03-09
already a thread on this:

[http://ubuntuforums.org/showthread.php?t=1425777](http://ubuntuforums.org/showthread.php?t=1425777)

and a bug filed:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535326](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535326)

---

### Post by lonniehenry on 2010-03-09
Affects me also.  Subscribed to the bug.

---

### Post by cyberkilla on 2010-03-09
> **tekstr1der said:**
> already a thread on this:

[http://ubuntuforums.org/showthread.php?t=1425777](http://ubuntuforums.org/showthread.php?t=1425777)

and a bug filed:

[https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535326](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/535326)

Thanks, I had assumed that /this/ thread was the main one, with it being at the top of the forum list.:p

---

### Post by Trespasser on 2010-03-09
Did a fresh install of daily 3-8-10, updated via synaptic, only to be faced with this after a reboot. I had a nice day. ;).

Later...

---

