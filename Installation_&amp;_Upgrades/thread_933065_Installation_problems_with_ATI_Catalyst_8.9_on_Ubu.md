---
title: "Installation problems with ATI Catalyst 8.9 on Ubuntu 8.04"
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by Salk on 2008-09-29
Hello!

I first tried to install the drivers above using the automated installer which came with easy instructions in few steps. Unfortunately it didn't give me the hoped result as it would reboot and force me to run on low resolution for some reason. At least it was easy to restore the initial situation by running an uninstall process.

Then I had the (bad) idea of following the Method 2 Installation at:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

I followed carefully every step. All worked as supposed to (with the small exception of having to change "i386" with "amd64" in this line:

sudo dpkg -i xorg-driver-fglrx_8.532-0ubuntu1_i386.deb fglrx-kernel-source_8.532-0ubuntu1_i386.deb fglrx-amdcccle_8.532-0ubuntu1_i386.deb)

untill I reach the Finishing the Install: Configuration step:

```
sudo aticonfig --initial -f
```

When I write this, I get the following error message:

"Unable to open /etc/ati/control, please reinstall the driver.
 Uninitialised file found, configuring.
 Segmenteringsfel" <- Swedish word: Segmentation Error

Since there is no automatic uninstaller using Method 2, I find myself stuck with the low resolution desktop (just the same result I got with the automated installer!) after having rebooted.

Now I ask you if you can kindly indicate me a way to at least restore the desktop the way it was originally. The Method 2 I used is full of steps an inexperienced user like me could not really understand. I had just trusted all would go well.

I thank you for your time and interest.

Cristiano

---

### Post by Salk on 2008-09-29
UPDATE: I managed to restore the default graphic driver by simply entering recovering mode and selecting first DPKG and then XFIX.

One of the two must have done the trick as I could again boot with the restored graphic driver.

Moreover, I then start Method 1 from the link above and added Driver="fglrx" under the Device section. I run then the

```
sudo aticonfig --initial -f
```

before rebooting.

At reboot, voilà, the driver is finally working.

When I run 

```
fglrxinfo
```

I get the confirmation of the successful ATI driver installation:

```
display: :0.0 screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850 AGP
OpenGL version string: 2.1.7979 Release
```

---

