---
title: "Gutsy Freezes on Load"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by arashiko28 on 2008-02-28
I have been using Ubuntu for quite a long time, and know the ways of my computer. But from a few days back it started to freeze on boot, in the load screen after just a little part of the first block or at the half, it flashes the caps lock led button and does nothing else. I have to hard shut down turn on again. It's random and not very often, but I don't like to shut it down like that. Any advices? Is this some sort of bug? Help.

---

### Post by Pumalite on 2008-02-28
Have you changed some part of your hardware? Do you have anything connected to USB while booting?

---

### Post by arashiko28 on 2008-02-29
I haven't changed anything since using Linux and, yes I do, I have the PCMCIA LAN card connected because otherwise, it does not recognizes it after turned on, a USB Hub with a venting fan to keep it cool, a wireless mouse and a DVD burner, but it's off all the time. Again, this is recent, I've had all of those since way long before using Ubuntu.

---

### Post by Pumalite on 2008-02-29
See if pressing 'Esc', you can see exactly where it gets stuck
You can also edit /boot/grub/menu.lst and remove 'quiet splash' at the end of the kernel line.Backup your file first.

---

### Post by arashiko28 on 2008-03-05
that of editing the boot/GRUB/menu.lts, I tried it and it says that I can't save it because I have no permission, I have no idea of how to open the file from terminal with the root permission, I do get to see file, but not to open it and modificate it.

---

### Post by Pumalite on 2008-03-06
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
gksudo gedit /boot/grub/menu.lst
Make the changes, save, exit and reboot.

---

