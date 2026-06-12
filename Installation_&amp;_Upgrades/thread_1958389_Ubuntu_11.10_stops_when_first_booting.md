---
title: "Ubuntu 11.10 stops when first booting"
date: 2012-04-14
forum: Installation &amp; Upgrades
---

### Post by master66 on 2012-04-14
Hi.
this is the first time with ubuntu for this PC . After the successful installation, when first booting, the system stops after the usual "african welcome", showing only the wallpaper and nothing else. i noticed also that i can't "try ubuntu" with CD or USB. in both cases the system stops at the same place.
i used the 32-bit desktop iso.

This is the PC:
Pro: Intel Pentium Dual CPU E2140
Ram: 2GB
GPU: ATI Radeon X1550
3HD: 2 in PATA (data only) 1 in SATA (system)

hope you can help, because I tried to post the same thing in the Italian forum, without significant response. 
thanks.

---

### Post by roelforg on 2012-04-14
Try going to the freeze point, press ctrl-alt-f1 to get a terminal, log in and post the content of /var/log/Xorg.0.log

---

### Post by master66 on 2012-04-14
i entered in terminal and logged in with my accoun configured during the installation process, then tried to access at /var folder with "cd var" command, but "no such file or directory " exists. i'm not very good with the terminal so maybe i mistaked something

---

### Post by roelforg on 2012-04-14
> **master66 said:**
> i entered in terminal and logged in with my accoun configured during the installation process, then tried to access at /var folder with "cd var" command, but "no such file or directory " exists. i'm not very good with the terminal so maybe i mistaked something
 
Here's the right cmd:
```

cd /var/log

```
The / is no mistake

---

### Post by master66 on 2012-04-14
copy: permission denied. how can i put it in a usb?

---

### Post by roelforg on 2012-04-14
> **master66 said:**
> copy: permission denied. how can i put it in a usb?
 
Try running your copy with sudo
 
Assuming your usb is mounted as /media/usb
```

sudo cp /var/log/Xorg.0.log /media/usb/

```

---

### Post by master66 on 2012-04-14
ok. if it works where shall i upload the log file? is mediafire good for you?

---

