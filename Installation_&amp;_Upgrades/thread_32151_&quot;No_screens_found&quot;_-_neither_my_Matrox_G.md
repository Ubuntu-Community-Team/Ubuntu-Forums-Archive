---
title: "&quot;No screens found&quot; - neither my Matrox G550 graphic card"
date: 2005-05-06
forum: Installation &amp; Upgrades
---

### Post by rainer on 2005-05-06
Hello to all,

I can´t get my graphic card working. All I got is an "No screens found" in the log.

1.) I own an old P-III 900 Mhz on a board with integrated SIS graphics. The resolution is poor.

2.) I installed a Matrox G550 and switched to it by changing the BIOS, Off course, I changed the connection cable to the MATROX plug.

3.) The whole (console based) installation prozess worked well. But, the hardware recognition found only the BIOS disabled SIS onbord graphics. From the moment ubuntu switches from console to X11/Gnome, I get a blue screen.

4.) I inststalled the LINUX driver for the Matrox G550, which is properly recognized (LOG).

5.) I reconfigured XORG by running "dpkg-reconfigure xserver-xorg". No errors occured.

6.) After rebooting I get the blue screen. "No screens found"! In the xorg.conf there is a sreen section with al lot of subsections, related to different color depth and resolutions. 

===> What went wrong? Thanks for your hints!

Rainer

---

