---
title: "package fglrx 2:8.723.1-0ubuntu3 failed to install/upgrade: fglrx kernel module faile"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by aviramof on 2010-04-22
i have just installed updates and fglrx failed to update and now he's not working what can i do about it?
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568790](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/568790)

thanks in advance.

---

### Post by cubeist on 2010-04-23
looked at the bug report, it should build, I have similar hardware, actually the exact same graphics card.

I also had problems upgrading.  Before upgrading I had the latest ati fglrx driver installed from the ati website on 9.04 (64bit).  I had to first remove this driver before fglrx could be installed from synaptic, it took me a while to figure out, first boot into recovery mode, now you have two choices, either reconfigure the (open source) radeon driver so you can boot in and uninstall your fglrx module via synaptic, OR, boot into a terminal and purge the fglrx module
```
sudo apt-get purge fglrx
```then reboot (again into a terminal or using vesa graphics) and type
```
sudo apt-get install fglrx
``` then, this is very important!, type
```
sudo aticonfig --initial -f
```
reboot, cross your fingers, clench your cheeks, whatever...hopefully you will have working fglrx graphics...

unless I am totally wrong and you have a weird bug unique to your system, in which case use the radeon driver (sudo apt-get install xserver-xorg-video-ati)

goodluck...I'll check back tmorrow, I can't stay awake longer today

---

### Post by aviramof on 2010-04-23
Thanks for the help but it's not working i booted to recovery mode run ubuntu in low configuration mode purged fglrx i also had to use sudo rm -rf /usr/lib/fglrx/ to completly 
delete this folder because the purge process did not remove it because she was no empty

but i still get this:
```
Error! Bad return status for module build on kernel: 2.6.33-020633-generic (i686)
Consult the make.log in the build directory
/var/lib/dkms/fglrx/8.723.1/build/ for more information.
dpkg: error processing fglrx (--configure):
 subprocess installed post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of fglrx-amdcccle:
 fglrx-amdcccle depends on fglrx; however:
  Package fglrx is not configured yet.
dpkg: error processing fglrx-amdcccle (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.he_IL.utf8.cache...
Processing triggers for python-support ...
Errors were encountered while processing:
 fglrx
 fglrx-amdcccle
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

i don't understand why does my 2.6.33 kernel is causing problems when i'm installing from 2.6.32-21 and i can't remove 2.6.33 because the risk is too high for this 2.6.32-21 kernel would crash because of this fglrx problems and i have no intention of reinstalling linux today so i'm hopping that the problem would be fix via an update of the fglrx driver.

---

### Post by jfernyhough on 2010-04-23
fglrx won't yet build correctly for .33 or .34 kernels. It will build for the .32. If you want fglrx you will have to remove .33.

---

### Post by aviramof on 2010-04-23
i did it and installed fglrx now it's working fine but this fglrx driver is not perfect it still asks 
me to restart when i choose one of the multi display options in catalyst.

in any case i am going to try and reinstall 2.6.33 just in case 2.6.32 would ever crash for any reason in the future.

Update:
it seem to be that i can't do it right now if i try i already start getting errors with the fglrx from apport so let's hope nothing would crash my current kernel till the problem is solved.

---

