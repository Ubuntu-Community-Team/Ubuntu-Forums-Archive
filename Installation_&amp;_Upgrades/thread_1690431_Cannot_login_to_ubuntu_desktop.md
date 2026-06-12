---
title: "Cannot login to ubuntu desktop"
date: 2011-02-18
forum: Installation &amp; Upgrades
---

### Post by tenmoi on 2011-02-18
Hi all,

I am in big trouble now:

First I was remotely controlling my lucid box from windowsxp through teamviewer6. I installed kernel 2.6.38-rc3, uninstalled ati 11.1, then set lucid to automatic login. I also put teaviewer to the startup application list then I wrote a script and put it to /etc/init.d
then run: update-rc.d myscript defaults

myscript:
 #!/bin/bash
/usr/bin/teamviewer

I restarted and could not login. I chose safegraphics mode and was brought to standby. 
Steps I have taken to try to solve the problem:

-Boot to recovery mode
-Uninstall kernel 2.6.38, ati 11.1 and teamviewer.
-Install ati 11.2
-Inside the console, set automatic login to false. Remove myscript
-Reboot normally but cannot login. 

-Boot to recovery mode again and startx and I can get to the graphical desktop.

I have also resorted to removing .gconf .gconfd .metacity ... to no avail.

Please help and thank you.

---

### Post by angryfirelord on 2011-02-19
Sounds like an ATI driver issue, but it's hard to tell unless I can see some log files. What I would do is uninstall the catalyst driver (don't install it again) and try to login normally. Ubuntu will use the default driver (radeon or radeonhd) for your videocard.

---

### Post by Hippytaff on 2011-02-19
If Angryfirelord's suggestion doesn't work out, it might be worth trying nomodeset.
When you get to the grub menu highlight ubuntu and press e. Then change 'quite splash' to 'nomodeset' and press CTRL+X to boot. Then install the necessary drivers

---

