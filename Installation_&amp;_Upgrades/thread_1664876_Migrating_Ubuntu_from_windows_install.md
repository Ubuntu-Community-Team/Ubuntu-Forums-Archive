---
title: "Migrating Ubuntu from windows install"
date: 2011-01-11
forum: Installation &amp; Upgrades
---

### Post by crimsonsky69 on 2011-01-11
Hi folks and thanks for looking at my post.

Problem: I installed ubuntu with the option to install it inside windows but on a different hard drive. c: drive contains windows and d: drive contains ubuntu. I'm getting a new SSD and plan on doing a new install of windows on the SSD. 

Question: my concern is will the ubuntu still be there since it's on a different hd? or will i have to modify grub and stuff. or should i just uninstall ubuntu as well and re-install.

---

### Post by Frogs Hair on 2011-01-11
Did you use Wubi or is this a traditional dual boot ?  I wondering because if you used the windows installer, Ubuntu should reside on the same drive as windows because Wubi installs Ubuntu inside the  Windows partition . 

Having used Wubi a number of times I don't remember an option for selecting a different drive , but I could be wrong . It is possible to move a Wubi installation to its own partition.

---

### Post by Frogs Hair on 2011-01-11
Double post

---

### Post by bcbc on 2011-01-11
Ubuntu will still be there, but you won't have a way of booting it. You can of course, manually add an entry to the Windows boot manager to boot it. Or some other method (involving backing up the root.disk, reinstalling, copying over etc.)

However, since you have separate hard drives, it's better to stop using Wubi and [migrate]("http://ubuntuforums.org/showthread.php?t=1519354") the install to a partition. Then you don't have to worry about getting it to boot from Windows.

---

### Post by crimsonsky69 on 2011-01-13
@frogs hair, you were right. it wasn't on a separate drive. It was only some random files, Wubi and grub that was on the separate drive. I got confused since all of it was under ubuntu directory.

But following bcbc's instructions i moved the partition to another hd and after windows install i still needed to fix grub and after hours of searching and trial and error i fixed it. Now it works perfectly.

---

### Post by Frogs Hair on 2011-01-13
Good to here ! :P

---

