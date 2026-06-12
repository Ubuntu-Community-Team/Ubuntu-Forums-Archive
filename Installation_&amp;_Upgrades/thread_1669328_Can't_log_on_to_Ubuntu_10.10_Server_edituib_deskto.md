---
title: "Can't log on to Ubuntu 10.10 Server edituib desktop..."
date: 2011-01-17
forum: Installation &amp; Upgrades
---

### Post by acompay on 2011-01-17
[SIZE=3][FONT=Calibri]Hello There,[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I just installed Ubuntu 10.10 Server Edition. When I log in I only get the username and password login. I input that info I get the user@user waiting for me to enter new commands. What can I do to leave the shell and open up the desktop?[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Regards,[/FONT][/SIZE]

---

### Post by ajgreeny on 2011-01-17
The server edition doesn't have a desktop environment to boot into, so unless you add one manually with ```
sudo apt-get install <package>
``` you will have to make do with the command line.

There are many desktops to chose from, but for a server I suggest you go for one of the smaller faster ones, eg, fluxbox.  If you really want the gnome desktop you can add it, or even the full ubuntu-desktop package if you must, but if it's really just a server, you really shouldn't need a DE.

---

### Post by acompay on 2011-01-17
> **ajgreeny said:**
> The server edition doesn't have a desktop environment to boot into, so unless you add one manually with ```
sudo apt-get install <package>
``` you will have to make do with the command line.
 
There are many desktops to chose from, but for a server I suggest you go for one of the smaller faster ones, eg, fluxbox. If you really want the gnome desktop you can add it, or even the full ubuntu-desktop package if you must, but if it's really just a server, you really shouldn't need a DE.
 
Thank you for your reply. I really want the server to install Joomla using Putty from Windows 7. But I thought that might be certaing tasks that could be simpler to solve with the server desktop. Thanks!

---

