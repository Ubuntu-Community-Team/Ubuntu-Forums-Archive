---
title: "Reinstalled gutsy - no toolbars after login"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by tokker73 on 2007-11-08
I just reinstalled gutsy. I took an older gutsy version CD (from before the official release) and  then ran sudo apt-get update and sudo apt-get upgrade, so it took some downloading and installing, but eventually i got up to my login screen. After that I get the standard brown desktop, but there are no toolbars or menus anywhere to be seen. The system itself seems to be running, so it's hasn't crashed. Could it be a problem with my resolution so that the menu bar is there but not visible (which would be strange because in the installation process I only kept my laptop's resolution? If so how can i adjust this. Remember i don't have any menu's, the only thing i can do is press ALT-F2 and then run a command in the terminal.

Thanks in advance,
Tom

---

### Post by bulldog on 2007-11-08
Try on your desktop ALT + F2 and see if anything comes up.

---

### Post by tokker73 on 2007-11-09
I figured out that I had to run sudo dpkg-reconfigure xserver-xorg and changed my resolution. Log out and then in again and everything's OK. Still 1 problem. Everytime I start up again, I have the same problem because when I run sudo dpkg-reconfigure xserver-xorg again, it is changed back into the wong resolution. Strangely enough my changes were stored in the config file (sudo nano /etc/X11/xorg.conf). How can I make it stick? Is there a special save function that I overlooked?

---

### Post by bulldog on 2007-11-09
Set the desired resolution as the only one in the xorg.conf.
Did you install any driver for the graphics?

You save the file with CTRL+X in nano

---

### Post by tokker73 on 2007-11-09
I downloaded the official release Live CD of Gutsy (which worked with my intel 965 driver, unlike the Live CD of Feisty) and installed everything again. Now everything seems to work fine. (Except for the special effects - I don't understand all that compiz xgf gfx whatever stuff so i am waiting for a clear explanation before i start trying things out,... or I might need to start all over again. Great help this forum, but little consideration for people who have no idea of commands and stuff...)

---

