---
title: "system lock ups when i delete files EXT4"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by skedone on 2009-04-05
running 9.04 all updated with ext4 problem is when i try to delete stuff if i do shift delete or send to bin then delete more than about 4 files the system locks up not even the mouse moves.

anyone know when this is gonna be fixed also the new cups detects my printer and installs it but then wont print saying maybe printer not connected lol

---

### Post by lean on 2009-04-05
Do you need to reboot when EXT4 locks up?

Is your printer by any change an HP printer?

---

### Post by skedone on 2009-04-05
yes i cant do anying nothing responds not even mouse curser and no my printer is a epson sylus office bx300f to be precise

---

### Post by skedone on 2009-04-05
anyone?

---

### Post by pressureman on 2009-04-05
Yep, I'm seeing the same problem on my notebook (Pentium M, 512MB RAM). If I have a lot of stuff in the trash, it sometimes locks up when I empty trash, or if I shift-delete a big folder.

Even using "Magic SysRq" keys, I can't get to a vty to see what has caused the crash (but can reboot it with Alt-SysRq-B).

My system is fairly stretched for memory (hence why I plan to upgrade), so I wonder if this problem only appears on boxes where memory is tight. I had temporary use of another laptop (Core2 Duo, 3GB, running 64-bit) and never had any problems with ext4.

---

### Post by pressureman on 2009-04-05
You might want to take a look at [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/330824/)

Seems to be somewhat unique to Ubuntu's kernel.

---

### Post by skedone on 2009-04-06
its not a memeory thing mate im running 4 gig of corsair xms extreme

---

### Post by RaZoR1394 on 2009-04-06
Have you tried CTRL-ALT-PRTSCR/SYSRQ + SUB when the system totally locks up. It's better than just pressing the RESET button on the case.

I have had nautilus lock up when doing heavy file operations on ext4 but when the operation is finished it returns normally.

---

### Post by cl333r on 2009-04-06
Check if the ext4 partition isn't corrupted.
As to your printer this could help:
[http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Office_BX300F](http://www.openprinting.org/show_printer.cgi?recnum=Epson-Stylus_Office_BX300F)

---

### Post by Yashiro on 2009-04-06
It looks like it may be related to the backported patches applied to Jaunty. Hopefully it will be fixed.

---

### Post by skedone on 2009-04-06
well updates came thru today for cups and goshtscript i reset and magic happened my printer works and my scanner YES!!!!! have not ahd any lock ups yet either maybe it was python or xul runner or summit they updated to

---

