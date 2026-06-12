---
title: "Ubuntu newb: no screen signal after install of Desktop 18.04.3"
date: 2019-10-08
forum: Installation &amp; Upgrades
---

### Post by simonkepp on 2019-10-08
[COLOR=#1A1A1B][FONT=&quot]Absolute newb here, having problems with my first install. I've made a bootable USB stick with the installer for Ubuntu Desktop 18.04.3. When I boot on the stick, I get the simple text menu, allowing me to try or install Ubuntu. If I choose Install, the signal to my screen dies. Instead, I tried the option to Try Ubuntu without installing, and it took me to the GUI without any problems.. From there, I chose the option to install Ubuntu to a local SSD, and the installation process seemed to complete without any problems. When booting on the disk I just installed to, I again loose the signal to my monitor, and have nothing but a blank screen. Any help or suggestions would be much appreciated.[/FONT][/COLOR]

---

### Post by mörgæs on 2019-10-08
Hi, welcome to the fora.

in a live boot, please copy ```
sudo lshw -sanitize > lshw.txt
``` and paste it to the command line, run it and post lshw.txt in CODE tags.

---

### Post by simonkepp on 2019-10-10
The problem went away by itself. After watching a movie on Netflix on a different PC for a couple of hours, I switched my KVM switch back to the Ubuntu machine, and now, everything worked fine. I'm guessing the issue was related to the KVM-switch, rather than the new Ubuntu install.

---

