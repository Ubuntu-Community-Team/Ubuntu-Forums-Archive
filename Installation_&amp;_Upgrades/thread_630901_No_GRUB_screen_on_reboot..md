---
title: "No GRUB screen on reboot."
date: 2007-12-03
forum: Installation &amp; Upgrades
---

### Post by user481516 on 2007-12-03
To my surprise I was FINALLY able to install Ubuntu on my computer using the UNetbootin.  I have windows installed on my C: drive and Ubuntu on a separate 60 GB hard drive.  I restart my computer and there is no GRUB screen to choose UBUNTU.  I am SO close.  Is there an easy fix?  Could it have to do with Ubuntu being on a separate HD?

---

### Post by jjalocha on 2007-12-03
Honestly, I'm not quite clear about your problem, but you might get your GRUB menu to display with the following:

Open the '/boot/grub/menu.lst' file with a text editor, and comment out the 'hiddenmeu' entry. It should look like:

```

#hiddenmenu

```

From the command line, under Xubuntu, you could use the 'mousepad' application to accomplish this:

```

$ sudo mousepad /boot/grub/menu.lst

```

I don't know what application is used under (K)Ubuntu.

Hope this helps!

---

### Post by mozkill on 2007-12-03
the bootsplash framebuffer is not visible in the 64-bit versions of gutsy.  the screen goes blank for 30 or more seconds until X starts.  if you need to see the boot messages, type "dmesg" in a console after the system is started.

---

