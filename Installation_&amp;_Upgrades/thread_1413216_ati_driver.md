---
title: "ati driver"
date: 2010-02-22
forum: Installation &amp; Upgrades
---

### Post by vazovskiiii on 2010-02-22
lasha@lasha-desktop:~$ cd ~/Downloads
lasha@lasha-desktop:~/Downloads$ chmod +x ati-driver-installer-9-3-x86.x86_64.run
lasha@lasha-desktop:~/Downloads$ ./ati-driver-installer-9-3-x86.x86_64.run
Created directory fglrx-install.VIPA7G
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
ATI Technologies Linux Driver Installer/Packager 
==================================================
Warning: /etc/ati/custom-package/ati-packager.sh is missing or not a script.
 
Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.31-19-generic; make sure that the version is being
correctly set by --iscurrentdistro
 
Removing temporary directory: fglrx-install.VIPA7G
 
 
need help what is it can't install ati driver

---

### Post by khelben1979 on 2010-02-22
Why not install the ATi driver which is provided by the Ubuntu distribution? (search for it in [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager"))

Otherwise, have you checked that you got the correct driver version for your graphics card/chip? Also, I would recommend to use sudo to execute that script.

---

### Post by Mark Phelps on 2010-02-22
Typically, the "does not support version" error message indicates that there is a conflict between the version of the driver you are trying to install and something else already installed, typically, the X-server.

What model video card/chip do you have?

If it's not one of the newer HD 3x/4x/5x cards, there is no ATI driver for it and forcing such an install will only trash your display.

---

### Post by quadproc on 2010-02-22
Having just installed the fglrx driver (again) on this system, I have looked into the install script and found that the script is only designed to support a few versions of Ubuntu, the latest being 9.04.

Are you perhaps trying to install with version 9.10?

If you run the .run script with the option --keep then the install will leave behind the files that it used during the installation, and one of these is a log file.  You might find something useful in it.

Good luck.

quadproc

---

