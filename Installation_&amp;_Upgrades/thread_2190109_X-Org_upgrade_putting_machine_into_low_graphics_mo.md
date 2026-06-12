---
title: "X-Org upgrade putting machine into low graphics mode."
date: 2013-11-25
forum: Installation &amp; Upgrades
---

### Post by aaronschillings on 2013-11-25
Every time I do a sudo-apt get upgrade and allow X-org to update, my computer is put into low graphics mode and I have to do a complete re-installation of my back up that I do before hand.  When I click the notification for system updates in the bottom right hand of my toolbar, and un-click X-org, I'm able to continue operating just fine.  Does any one have any suggestions on how to fix this problem? I would like to be able to not have to worry about getting kicked into low graphics mode after a full system upgrade!

---

### Post by QIII on 2013-11-25
Hello!

Which version of Ubuntu are you running, what is your GPU and what driver are you using?

---

### Post by aaronschillings on 2013-11-25
13.04.  I'm not sure what GPU stands for, and my driver is a Radeon 8210

---

### Post by QIII on 2013-11-25
GPU = Graphics Processing Unit -- your graphics "card".  In this case, it looks like you probably have an E1 or A4 APU (Accelerated Processing Unit, which is both the CPU and GPU combined on one die) since those are generally what the HD 8210 (your graphics "card") is associated with.

A driver is the software that tells the hardware how to run.  Do you remember installing a driver from "Additional Drivers" or were you just running Ubuntu as installed in the previous version?

---

### Post by aaronschillings on 2013-11-25
Ah yes, it's an E1.  And I remember having to download amd-driver-installer-catalyst-13-6-beta-x86.x86_64.run to get my machine to run properly after installation.  I am a new usuer of Linux, and this is the first distro of Ubuntu I've run.

---

### Post by QIII on 2013-11-26
When you install the driver from the repository, it uses the package management system, which keeps track of all the bits and pieces of things and is "smart" enough to make sure everything is updated and in the proper place.

Because you used the .run file directly from ATI, you circumvented the package management system.  Not a big deal, but it means that when there are updates to X Org and the kernel, you first need to uninstall the driver, reboot, do your upgrades, reboot, reinstall the driver, reboot.

The following should get you back to the default open source Radeon driver that was installed when you first installed Ubuntu.  If, as you say, this did not work well, then just reinstall the proprietary driver.

However, this time I would recommend installing from the repository.  

So, let's uninstall the driver

```
sudo amdconfig --uninstall
```

and change the name of the xorg.conf if there is one

```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Reboot.

Install fglrx (that is the ATI driver) and the Catalyst Control Center from the repo:

```
sudo apt-get install fglrx-updates fglrx-amdcccle-updates
```

```
sudo amdconfig --initial
```

Reboot.

Now you should be running the proprietary driver that exists in the repo (which may not be the very most recent one) and your package management system will be able to keep track of it and allow you to upgrade your system as usual.  Then you can use CCC to make any adjustments you want.

Let us know how that goes.

---

