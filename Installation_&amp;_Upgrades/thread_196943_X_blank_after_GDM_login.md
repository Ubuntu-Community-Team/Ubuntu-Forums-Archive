---
title: "X blank after GDM login"
date: 2006-06-15
forum: Installation &amp; Upgrades
---

### Post by Gerr on 2006-06-15
Howdy. I've been converting my machines to Ubuntu for the last month. I bought a new machine to replace an older one at home with some nice new hardware. After installing Ubuntu (6.06), I ran into several problems. At first, it wasn't booting because it couldn't mount the root filesystem (this is on a SATA II disk, so I had to mount the disk via the live CD, chroot to the new install, download the kernel and compile in SATA support for my SATA II controller). Now that the system is able to boot, it displays X just fine, but after logging in (with any combination of sessions), the screen simply goes blank.

This appears to be vastly different then what other people have reported when they haven't been able to see the login screen at all. I can still see and move the mouse cursor around, but everything else appears to be blank.  I never see the gnome splash screen or any panel/background changes.

On a related note, is there a script that ubuntu runs after the first boot up? I'm wondering if it's possible that some of the packages haven't been installed yet... 

Many pre-emptive thanks.

---

### Post by Gerr on 2006-06-16
Answering my own problem in the hopes that this might help someone else down the line...

Killing all of the esd programs from the console got me into X (gnome-session). for the newbs, that's sudo killall esd. ESD is running now that I'm logged in, but everything seems to be OK regardless. I hope this proves useful to someone.

---

