---
title: "Boot Order--Dual Boot"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by Taranis on 2006-06-01
I am dual booting.

How do I change which OS is default to boot after restart or cold boot?
As it is...I have 10 seconds to choose a different OS before Ubuntu boots.

Thanks

---

### Post by doobit on 2006-06-01
You edit /boot/grub/menu.lst as root. 

1. Open a terminal
2. Type sudo nano /boot/grub/menu.lst
3. Arrow down to the line with the number 0 and change it to 4 or whatever the line your other OS is on minus 1 (grub lines start with 0).
4. ctrl X
5. Y
6. Enter
7. type exit to get out of the terminal.
reboot

---

### Post by aysiu on 2006-06-01
[https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS](https://wiki.ubuntu.com/GrubHowto/ChangeDefaultOS)

---

### Post by Richard_at_home on 2007-09-29
> **Taranis said:**
> I am dual booting.

How do I change which OS is default to boot after restart or cold boot?
As it is...I have 10 seconds to choose a different OS before Ubuntu boots.

Thanks

The Link to the grub documentation is very helpful, but for the ones not interested in all the details here in short what I did. I think it's a bit more Windows-User friendly than the first reply.

The file /boot/grub/menu.lst contains the settings for the boot menu. To edit it, open a terminal ( In German language Version you find that in Anwendungen/Zubehör, I guess it's Applications/Accessories in English). There you type:

sudo gedit /boot/grub/menu.lst

to open an editor. You must have root privileges to edit the file, so you cant open it from the editor and have to do it with the sudo. In this file you find a line almost at the top:

default		0

For my computer (Win XP with additional Ubuntu) I need a 4 as default that Windows starts as default. At the end of the file you find the boot options listed. The counting starts with 0 and every entry starting with "title" is counted (that makes "Other operating systems:" index 3 which would not boot at all)

At last save the file.

Hope that helps.

---

