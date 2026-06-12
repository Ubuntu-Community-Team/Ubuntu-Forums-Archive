---
title: "Disconnected from system bus"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by Son Of Warmonga on 2011-10-18
I'm having trouble doing a new install of Ubuntu 11.04 on an Optiplex GX270 (it's a P4).  The installer seemed to work, but when I clicked the button to reboot, the system displayed a console screen that showed a bunch of processes getting killed, along with this text:
```

init: Disconnected from system bus
init: dbus main process (1097) killed by TERM signal
unable to connect to system bus: Failed to connect to socket  /var/run/dbus/system_bus_socket: Connection refused

```This is my second attempt at installing.  When I rebooted after the first attempt (and after seeing the same console screen), the desktop came up, but it was seriously out of whack.  Text was mostly invisible, only barely flickering, and clicking on the screen would blank out the surrounding area.

---

### Post by JazzPotato on 2011-10-18
What are you using to install? (CD, memory stick, blah blah blah)

---

### Post by Son Of Warmonga on 2011-10-18
I'm installing from a CD I burned from a downloaded ISO image.  The md5 sum on the ISO is okay, and the machine I'm installing on is not connected to the web.

---

### Post by matt_symes on 2011-10-18
Hi

Boot to the recovery console and type
```
rm /var/run/dbus/pid 
rm /var/run/dbus/system_bus_socket

```Then reboot.
Maybe that will help.

Kind regards

---

### Post by Son Of Warmonga on 2011-10-18
It seems I do not have the hardware to run Unity.  How do I change to Ubuntu Classic from a console?

---

### Post by Son Of Warmonga on 2011-10-18
Maybe I'll just switch to Xubuntu...

---

