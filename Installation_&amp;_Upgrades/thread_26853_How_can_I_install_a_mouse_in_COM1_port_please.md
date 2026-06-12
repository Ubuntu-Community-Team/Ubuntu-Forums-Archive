---
title: "How can I install a mouse in COM1 port please?"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by chantal on 2005-04-14
I have just installed ubuntu "warty" onto an old Pentium133 with 128 ram. However, to get my old 14" monitor to work and XServer to load, I ran xf86config from the command line at /usr/X11R6 and stored the new file in /etc/X11 , changing the name of the generic config file (which wouldn't load) to XF86Config-4save. So I got to the desktop and can navigate with just the kb. The mouse pointer is there but does not react at all.
The config for my mouse is:

Identifier            "Mouse1"
Driver                 "mouse"
Option "Protocol" "Auto"
Option "Device"   "/dev/input/mice"

My motherboard (a P5HX-B) doesn't have a PS/2 socket, so I plugged the mouse in COM1. It worked fine under W98, but I think under Ubuntu I need to configure something otherwise.
Any help please?

---

### Post by heimo on 2005-04-14
Try changing this
Option "Device" "/dev/input/mice"
to this
Option "Device" "/dev/ttyS0"

ttyS0 = COM1 (first serial port)
ttyS1 = COM2 (second serial port)
 
Unless *ls -l /dev/input/mice *shows that it's already symbolic link to the correct device

---

### Post by chantal on 2005-04-14
Thanks a lot Heimo - that did it. My mouse is working now.

---

