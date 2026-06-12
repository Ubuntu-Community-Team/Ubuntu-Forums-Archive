---
title: "Reusing a user from a previous install"
date: 2005-05-22
forum: Installation &amp; Upgrades
---

### Post by lyp on 2005-05-22
I've just installed Ubuntu over an old Knoppix install.  Previously I had my 40G hdd partitioned into a 5G / and a 35G /home which had all the user files.  I've changed fstab to mount /home and my slave hdd, and I've chaged the user and group id's to the match those of the new user.  But I can't login.  I get an error stating my session has only lasted 10 seconds then I'm kicked out to the login again. 

What do I need to do bring my old files and config into my new install?

---

### Post by tonym on 2005-05-23
Have you tried logging in at a console session rather than X?  Sometimes you get clearer error messages at a console when this sort of thing happens.

If you can get logged in at a console,  try stopping gdm/kdm and then typing startx.  Again this can give you some diagnostics.

---

### Post by XDevHald on 2005-05-23
[QUOTE=tonym]Have you tried logging in at a console session rather than X?  Sometimes you get clearer error messages at a console when this sort of thing happens.

If you can get logged in at a console,  try stopping gdm/kdm and then typing startx.  Again this can give you some diagnostics.[/QUOTE]
 I've had this SAME exact problem before. Reboot, then try to login, if it doesn't then press ctrl+alt+backspace and use X to kill gnome-session then reboot and try again. It could be a wide variety of things, maybe you installed something before you logged out, or one of your files are corrupted and are bashing against the login.

---

