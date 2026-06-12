---
title: "Change to Xserver Xorg won't allow me to boot into Ubuntu Edgy"
date: 2006-12-19
forum: Installation &amp; Upgrades
---

### Post by DapperMe17 on 2006-12-19
Hello, 


I recently uninstalled my Nvidia Legacy GlX drivers from Synaptic. 

I forgot to change the Xorg file back to "NV". It is currently "Nvidia".


Unfortunately, when I boot into Ubuntu, I get the dreaded Xserver-Xorg error screen, which I can't get past, in order to get into Ubuntu.


I have a copy of Damn Small Linux on hand as a LiveCD. 


How can I get into Xserver-Xorg, in order to change the file back to "nv".....and get back into Ubuntu???


Thanks!

---

### Post by scxtt on 2006-12-19
reboot into recovery mode from the grub menu ... (you might have to hit escape to see more options) ... you'll be dropped to a root shell and can **vi /etc/X11/xorg.conf** ...

---

### Post by DapperMe17 on 2006-12-19
I ran that command in Recovery mode....unfortunately, I was presnted an empty screen....except for what looks to be sideways-looking "s" characters on about every other line. In other words, it resembles the xorg file, but doesn't contain any data.


What next?

---

### Post by DapperMe17 on 2006-12-19
Update!


Ok, I made it into xorg from Recovery mode. (vi /etc/X11/xorg.conf)


After I update the file, what do I need to do in order to save the new file???

---

### Post by scxtt on 2006-12-19
type

:wq

that will "write" and "quit"

or use **nano /etc/X11/xorg.conf**

---

### Post by DapperMe17 on 2006-12-19
Thanks all...solved!


I used sudo nano, then Ctrl-o & Ctrl-n...rebooted & all works fine:)

---

