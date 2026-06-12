---
title: "/[ubuntu]'graphical' grub breaks on win7/winxp/ubuntu10.04"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by _bb_ on 2011-01-06
early tl;dr: The fancy grub breaks on my wubi 10.04 install, can I force it to use the old grub?

When I rebuild grub.cfg (last time was yesterday for kernel update to .37), and shut down / reboot, grub breaks because it can't 'loadfont' and a few other errors which are related to the 'graphical' grub boot menu.

To fix this I have to boot into a live CD (also Ubuntu 10.04) and run the following:
*Taken from [http://neosmart.net/forums/showthread.php?t=5004](http://neosmart.net/forums/showthread.php?t=5004)*
```
sudo fdisk -l
sudo mkdir /win
sudo mount /dev/sda1 /win
sudo mkdir /vdisk
sudo mount -o loop /win/ubuntu/disks/root.disk /vdisk
```That gets my wubi install mounted to /vdisk. From there I run the command:
```
gksu gedit /vdisk/boot/grub/grub.cfg
```and delete everything before the first 'menuentry'. This fixes it every time - but booting into the live CD to do the above is time-consuming: Is there a way for me deny grub from using the 'graphics' version?

Additional information:

[LIST]
[*]The wubi install is Ubuntu 10.04 LTS
[/LIST]

[LIST]
[*]Wubi is mounted inside a broken Windows XP pro. 32bit install
[*]I am therefore Dual-booting with just Windows 7 64 bit
[*]The order of the bootloaders goes Windows 7 -> Grub, so I can still access Windows 7 when Ubuntu breaks
[*]Switching to a full linux installation is not an option, sorry.
[*]??? I know how to fix it but is there a way to skip having to do this on upgrades
[*](If I edit the grub.cfg before shutting down then this doesn't happen, obviously, but sometimes I forget and this is the result. I'd rather stop the problem at it's source than fight against the updater).
[/LIST]

---

### Post by bcbc on 2011-01-07
see Permanent Fix under Problem #2 in the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198")

---

