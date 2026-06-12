---
title: "Shutting Down X Windows System?"
date: 2007-07-13
forum: Installation &amp; Upgrades
---

### Post by jukari on 2007-07-13
I've searched the web up and down for a quick answer to this... but there doesn't seem to be any..

How can I close the X Window system to get into a Strict Console mode.... much like DOS... I'm very new to Linux.  

I'm trying to install the 8800 GTS Drivers but it keeps telling me I can't be in the X Window system... even when in root.

Thank you.

BTW: there are many features I am starting to like about this OS... Can't wait to learn how to use it to its full potential.

---

### Post by JTux on 2007-07-13
Booting in to the recovery mode will give you a system without X. It will also automatically login as root. [SIZE="3"]Be careful[/SIZE]l

---

### Post by mikewhatever on 2007-07-13
Boot into recovery mode, the second option in the grub boot menu.

---

### Post by jukari on 2007-07-13
Thank you will give it a shot

!:guitar:

---

### Post by deanjm1963 on 2007-07-13
the easiest way is to log out to the "log in" screen and hit Ctrl+Alt+F1 which will give you "terminal mode"

log in and type

sudo /etc/init.d/gdm stop

once you've installed your drivers type

sudo /etc/init.d/gdm start

replace gdm with kdm if you're using kubuntu

---

### Post by jukari on 2007-07-13
Hey thanks for the tip... I have another question....

Nvidia is telling me that I shouldn't run the drivers in level one... I should run it in 3? umm how to I get to 3?

Also what do I need APIC for... i have to keep disabling it...

thank you

---

### Post by mikewhatever on 2007-07-13
Use this gude [http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)
or [ENVY]("http://www.albertomilone.com/nvidia_scripts1.html"), an even better option.

---

### Post by jukari on 2007-07-14
Ugh I wish I would of read your post earlier... Thank you very much... I spent 6 hours F**king with the video drivers... and eventually got them to install but when I rebooted my system crashed... Im thinking about just reinstalling linux... It would probally be easier.

Thank you though I will check out the ENVY when I attempt it again after I take some asprin.

---

