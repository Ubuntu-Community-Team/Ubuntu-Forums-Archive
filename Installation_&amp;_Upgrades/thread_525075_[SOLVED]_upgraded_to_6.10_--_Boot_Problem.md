---
title: "[SOLVED] upgraded to 6.10 -- Boot Problem"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by lakelovers on 2007-08-13
Just upgraded from Dapper to Edgy. Everything went smoothly except on rebooting I get an error message that stops the boot: EE No Input drive matching "wacom." My brief search suggests that this is a tablet device that I don't have. Also I think there is an xserver error. How should I fix this?

---

### Post by logos34 on 2007-08-13
Boot into recovery mode. edit X server config

**sudo nano /etc/X11/xorg.conf**

---

### Post by lakelovers on 2007-08-14
Thanks. I tried reconfiguring X11/xorg.conf without success. I was able to "#" all references to WACOM. I also changed a couple of dispaly lines to better fit my monitor (Hanns CY199D) digital monitor. Still no booting to X!!. Then I tried "dpkg-reconfigure xserver-xorg" and got the message:  "xserver-xorg is broken or not fully installed." Any ideas on where I go from here?

---

### Post by logos34 on 2007-08-14
try 
**sudo dpkg --configure -a**

---

### Post by lakelovers on 2007-08-14
I got it working, finally. I re-installed X11.xorg, then did the "dpkg-reconfigure xserver-xorg" and that did it. Thanks for your input.
Jerry

---

