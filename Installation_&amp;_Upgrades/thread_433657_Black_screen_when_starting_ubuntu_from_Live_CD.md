---
title: "Black screen when starting ubuntu from Live CD"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by Kivamaki on 2007-05-05
Well I restart my computer, insert the CD and it loads up the ubuntu screen with options. I choose "Start or Install ubuntu". Then it will go to the loading screen with a progress bar a while, then it just goes to a black screen. And it stays like that. Nothing else happens. The very first time I did it, it gave me a loooong list of text errors, but it hasn't done that again.

Anyone know how to continue?

---

### Post by rizza on 2007-05-06
I had a similar issue with a laptop that had a very new video chipset. I believe your problem might be happening when the kernel booting ends and transfers to start X for your windowing environment. If there isn't a valid driver or incomplete driver for your chipset it won't work. My problem was with via/s3 openchrome video chipset. Anyway... If this is true then you should be able to switch to another terminal using ctrl-alt-f2(f3..etc.) and type: After logging in if you need to
sudo su
cd /etc/X11
nano ./xorg.conf
scroll down to were it talks about "Device" and "Identifier" with your chip set
comment out your "Driver" line and do a new one right below it like this:
Driver "vesa"

hit ctrl-o to save then ctrl-x to exit nano
hit ctrl-alt-f7 it should be blank or something then hit ctrl-alt-backspace this should kill and restart X11/GDM
hopefully you see a desktop or login.
If this is the case then the driver for you chipset isn't going to work right now. Sorry. 
In my case I had to compile the latest developer driver for my chipset to make it work correctly until they started to include it in updates of X11 drivers.

You may also have another issue but this sounds just like my problem. GOOD LUCK!

---

