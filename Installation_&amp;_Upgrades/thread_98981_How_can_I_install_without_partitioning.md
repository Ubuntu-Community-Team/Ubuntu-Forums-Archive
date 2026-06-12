---
title: "How can I install without partitioning?"
date: 2005-12-04
forum: Installation &amp; Upgrades
---

### Post by boedeker on 2005-12-04
A few weeks ago I was positing about the installer hanging at 52% when it was doing the install, over and over. So i used Gentoo to do the partitioning now I'm ready to instal ubuntu but I want to skip the partititioning stuff any ideas how?

---

### Post by az on 2005-12-04
[QUOTE=boedeker]A few weeks ago I was positing about the installer hanging at 52% when it was doing the install, over and over. So i used Gentoo to do the partitioning now I'm ready to instal ubuntu but I want to skip the partititioning stuff any ideas how?[/QUOTE]

If it stalled at 52 percent doing the install, your partitoining was already done and it was installing packages.  

Unless you mean the partitioning step borked at 52 percent.

Anyway, you can scroll down when you get to the partitoiner to the manual partitioning option and just set your root (/) and swap partition and make it go.

---

### Post by boedeker on 2005-12-05
yes it locked at 52% of the partitioner portion. It didn't give me any options, it just started the partitioner automatically.

---

### Post by bwog on 2005-12-05
[QUOTE=boedeker]yes it locked at 52% of the partitioner portion. It didn't give me any options, it just started the partitioner automatically.[/QUOTE]

That should not happen.

Try to install again, when you arrive at partitioning, you select the partitions one at a time. You have made these partitions before, and now you have to mount them.

root partition; use as Ext3, format yes, mount point /, mount options default, bootable flag on, size x GB.

Swap partition; use as swap, bootable flag off, size (less than 2 GB). It doesnt matter when swap gets formatted.

home partition; use as ext3, mount point /home, etc.

If you cant figure it out, break of installation and come back here to ask questions.

---

### Post by az on 2005-12-05
Try again and do CTRL-ALT-F3 to see error mesages.  Try CTRL-ALT-F2 to get to a shell ans see if your machine is locked up or if it is the partitoiner which is in an infinite loop.

---

### Post by figo2476 on 2005-12-06
I tried the root partition method. It failed.... Can't figure out

[QUOTE=bwog]That should not happen.

Try to install again, when you arrive at partitioning, you select the partitions one at a time. You have made these partitions before, and now you have to mount them.

root partition; use as Ext3, format yes, mount point /, mount options default, bootable flag on, size x GB.

Swap partition; use as swap, bootable flag off, size (less than 2 GB). It doesnt matter when swap gets formatted.

home partition; use as ext3, mount point /home, etc.

If you cant figure it out, break of installation and come back here to ask questions.[/QUOTE]

---

### Post by aysiu on 2005-12-06
Sounds like maybe a bum CD.

---

### Post by figo2476 on 2005-12-06
Not really, since my friend can install it without a problem.
Is the hardware problem?

Gary
[QUOTE=aysiu]Sounds like maybe a bum CD.[/QUOTE]

---

### Post by bwog on 2005-12-06
You said you tried the root partition method. Tell us more please. Do you have a / and a swap partition. Which partitions do you have haw large are they, how are they formatted? What exactly ist what you couldnt figure out?

The forum doesnt know anything abpout your hardware and therefore cannot tell if it is a hardware problem.

---

