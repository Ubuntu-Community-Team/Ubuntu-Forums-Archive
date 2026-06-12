---
title: "Any Post Bcm43xx-fwcutter gives post script error"
date: 2007-09-05
forum: Installation &amp; Upgrades
---

### Post by Bin23 on 2007-09-05
Hello again all,
I have been able to use the Bcm43xx-fwcutter. There was an error in the install script but I found th e drivers for my Dell 8500's broadcom wireless. It installed, the wireless card seems to work, but I get this error message : 


E: bcm43xx-fwcutter: subprocess post-installation script returned error exit status 1

with every install, update, upgrade. It has also completely stopped me from using the IR port on the machine as I can not complete the install.

Thanks for any help..

Bin

---

### Post by Jota1234 on 2007-09-21
I'm having the exact same problem and am considering just wiping the partition and doing a clean install from the Feisty Fawn CD unless someone else has any ideas.

---

### Post by Jota1234 on 2007-09-21
I guess Feisty tries to install the native Broadcom crap.  Just use ndiswrapper for now until you figure out how to make the Broadcom stuff work.  The following worked for me:

sudo apt-get remove --purge bcm43xx-fwcutter

---

### Post by Bin23 on 2007-09-23
Jota1234 I finally just uninstalled Bcm43xx-fwcutter and used ndiswrapper instead and it is working now.

Bin

---

