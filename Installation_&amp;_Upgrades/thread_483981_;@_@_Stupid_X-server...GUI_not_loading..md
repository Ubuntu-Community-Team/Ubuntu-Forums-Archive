---
title: ";@_@ Stupid X-server...GUI not loading."
date: 2007-06-25
forum: Installation &amp; Upgrades
---

### Post by ARandomKid on 2007-06-25
I recently upgraded to Ubuntu 6.10. When restarting, everything looked normal until I get to this screen.

"X-server has encountered an error. Would you like to see a report?" or something like that was displayed. When pressing "Yes", I get a screen with some labels and explanations, and at the bottom this is displayed:

> (EE) Failed to load /usr/lib/vorg/modules/extensions/libGLcore.so
(EE) Failed to load module "GLcore" (loader failed, 7)
(EE) module ABI major version (0) doesn't match the server's version
(1)
(EE) Failed to load module "neomagic" (module requirement mismatch, 0)
(EE) Failed to load module "synaptics" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

---

### Post by eapache on 2007-06-25
It should then give you a terminal (command line). If not, press Ctrl-Alt-F6 and login. When you have a terminal run:

```
sudo dpkg-reconfigure xserver-xorg
```

and follow the instructions. Then run:

```
startx
```

---

### Post by ARandomKid on 2007-06-25
When I try to reconfigure it, I get this:

"/usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed."

---

### Post by Pumalite on 2007-06-25
Interrupted installation.

---

### Post by ARandomKid on 2007-06-25
> **Pumalite said:**
> Interrupted installation.

...really? It looked complete before I restarted it...

...how would I go about reinstalling this without a CD? The only way I'm able to update is through the terminal...can't burn the iso or order a disk...

---

### Post by Pumalite on 2007-06-25
There is a way to install through the Internet. Can't remember off the top of my head. Look in Ubuntu.com/Documents. Another thing you should do before reinstall is check your CD or iso. Do checksum. If corrupted; may a friend download an iso for you? If so: torrent is better than HTTP or FTP. Burn at 1x.

---

