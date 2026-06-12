---
title: "Karmic fails in Virtualbox after update"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by powel212 on 2009-10-04
After several attempts to get the Bata release of Karmic running in Virtuyalbox.

Installs correctly

Run updates, (from main US server)

Reboot

Won't boot to login. Just get a command prompt.

Anyone else experience this, and found a solution?

Powel

---

### Post by wilee-nilee on 2009-10-04
Since you have the original image and your running in a virtual environment, if it was me I would just for fun try doing a update from that command line and if it downloads more updates, do a aptitude dist-upgrade, I'm a glutton for learning though.

---

### Post by powel212 on 2009-10-04
Did ```
sudo aptitude dist-upgrade
```

reboot - Errors - boots to command line

Did ```
sudo fsck
```

reboot

Booted into system successfully

trying to install guest additions now.

Thanks for the help.

Powel

---

### Post by powel212 on 2009-10-04
Guest additions has installed correctly.

Karmic looks nice.

P.

---

### Post by wilee-nilee on 2009-10-04
Cool Man. :)

---

### Post by lkraemer on 2009-10-04
Here are some notes I had captured for future use:

Package Dependencies
If you run across a problem with dependencies (like libxercese27 which is included in the libxalan110 package), you'll have at this point to either install it first or go ahead with the installation and run "sudo apt-get -f install" to correct the problems.
Thanks Princey

Compilation of the kernel module FAILED! Error
While trying to install VirtualBox you receive an error like this:
Code:

"Compilation of the kernel module FAILED!

VirtualBox will not start until this problem is fixed. Please consult '/var/log/vbox-install.log' to find out why the kernel module does not compile. Most probably the kernel sources were not found. Install them and execute '/etc/init.d/vboxdrv' setup as root."

If there was an Ubuntu Kernel Upgrade:

Run the command "sudo /etc/init.d/vboxdrv setup"

lk

---

