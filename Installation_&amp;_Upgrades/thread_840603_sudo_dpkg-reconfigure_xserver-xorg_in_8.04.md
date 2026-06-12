---
title: "sudo dpkg-reconfigure xserver-xorg in 8.04???"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by nparayo on 2008-06-25
Hi the command

sudo dpkg-reconfigure xserver-xorg

doesnt seem to work in 8.04 all i get are keyboard options unless i have got it wrong?

i cant get my laptop display to work it goes blank on startup ive managed to get it to shortly display the message "you monitor display settings could not be found" by runnung recovery and go to reset xserver settings i think,

i type my user and pass in command line , for a quick screen flash i get a message something about adjusting them manually btu this message disappears its like ubuntu found the safe resolution but then changed its mind and goes blank? what can i do?

---

### Post by avtolle on 2008-06-25
Boot into "safe graphics" mode (under F6 when first booting up). This, hopefully, will load the generic driver and get you into something visible on the screen. Next, get to a terminal (Alt+Ctl+F1), and there do```
gksudo displayconfig-gtk
```and see what is displayed for your screen and graphics card. For the screen, I'd try something like generic PnP or generic LCD, select a safe display resolution for your laptop (1024x768, for example), apply, and restart to see if that helps. While there, you might check to see what is being reported for your graphics card (graphics card tab) and set it to what you have before applying the changes. HTH.

---

### Post by nparayo on 2008-06-25
at which point do i press F6 on the keyboard all throught startup i pressed F6 and it did nto affect boot sequence. Ive never been able to get into the UI of UBUNTU screen goes blank, either way i tried entering 

gksudo displayconfig-gtk

but it says 

Gtk-WARNING **: cannot open disply:

---

### Post by comthre3 on 2009-02-21
same problem here, i cant even login safe graphics mode. for some reason it gives me random colors on my scren, it worked in safe graphics mode in 8.10, but i had to downgrade to use the reconfigure xorg tool.
so i dont know what im doing wrong
it would be great if someone could actually help us, im getting cannot open display also when i giving gksudo displayconfig-gtk command 

regards

---

