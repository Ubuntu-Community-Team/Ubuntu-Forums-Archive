---
title: "Error while installing STA driver"
date: 2010-06-14
forum: Installation &amp; Upgrades
---

### Post by emjot on 2010-06-14
Synaptic Package Manager:
"E: bcmwl-kernel-source: subprocess installed post-installation script returned error exit status 6"
 
run bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb:
"/usr/sbin/dkms: line 35: patch: command not found
Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--install):
subprocess installed post_installation script returned error exit status 6
Errors were encountered while processing: bcmwl-kernel-source"
 
On launchpad I found info that a new package is available (...0ubuntu4...) but I was not able to find it.

---

### Post by emjot on 2010-06-15
Found packages. Tried:
bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb
bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb
bcmwl-kernel-source_5.10.91.9+bdcom-0ubuntu4_i386.deb
 
Same error. I must be doing something wrong. 
For STA driver installation I found an instruction that calls to first run:
dkms_2.1.0.1-0ubuntu1_all.deb
from pool>restricted>b>bcmwl
On LiveUSB I have dkms as this:
dkms_2.1.1.2-2fakesync1_all.deb
 
This is current ubuntu run from a partition with Win7 on the other partition. It was installed from ISO converted to LiveUSB. No problem during installation. Hardware is Dell Inspiron 1525. The task was to get WiFi to work thus STA attempt to install.

---

### Post by JustinR on 2010-06-15
Do this:

```

sudo apt-get remove patch
sudo apt-get remove fakeroot
sudo apt-get remove bcmwl-kernel-source

```

After that reboot, then reinstall those removed packages, then reboot again. If that doesn't work, backup your data.

```

sudo apt-get remove patch
sudo apt-get remove fakeroot
sudo apt-get remove dkms
sudo apt-get remove bcmwl-kernel-source

```

Then reboot, reinstall those removed packages. If this doesn't work we can continue from there.

PS.

This removes bcmwl-kernel-source and its dependencies - which seems to be your problem.

---

### Post by emjot on 2010-06-15
It's late. I will try it tomorrow and post here.

---

### Post by emjot on 2010-06-15
sudo apt-get remove patch.....
Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
 
sudo apt-get remove fakeroot...
Error! Application of patch 0001-MODULE_LICENSE.patch failed.
Check /var/lib/dkms/bcmwl/5.60.48.36+bdcom/build/ for more information.
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 6
Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)

sudo apt-get remove bcmwl-kernel-source...
...successfull...
 
I don't have anything on this system yet. Maybe I should reinstall the whole thing?
(I have to confess that this is my first attempt to conquer Unix-type os.)

---

### Post by frogotronic on 2010-06-15
Go to SYSTEM>ADMINISTRATION>SOFTWARE SOURCES

Make sure your proprietary drivers are checked and the enable the proposed and backports repos.

Close Software Sources, update if you have to, upgrade if you have to (& reboot if necessary)

Open a terminal and

```
sudo apt-get install build-essential cdbs fakeroot dh-make debhelper debconf libstdc++5 dkms
```

Install the linux headers and source
```

sudo apt-get install linux-headers-`uname -r`

sudo apt-get install linux-source
```

Close terminal & Now try it.

- CH

---

### Post by cneha on 2010-06-15
just go to system>administration>hardware drivers
and check the status of your STA driver.if it is not active then activate it and restart your system.

---

### Post by emjot on 2010-06-15
I had STA and b43 drivers when I was using  LiveUSB to boot Ubuntu.
After installing on HD I don’t have any driver in “Admin>Hardware Drivers”. That is why I tried to follow instruction in post 1368699 and run into an initial problem reported on top of this thread. 
I will try cement_head code and report back.

---

### Post by frogotronic on 2010-06-15
> **emjot said:**
> I had STA and b43 drivers when I was using  LiveUSB to boot Ubuntu.
After installing on HD I don’t have any driver in “Admin>Hardware Drivers”. That is why I tried to follow instruction in post 1368699 and run into an initial problem reported on top of this thread. 
I will try cement_head code and report back.

I was thinking that your drivers are not being build against your kernel (bw-kernel-source errors)

- CH

---

### Post by emjot on 2010-06-15
Thank you all for good direction.
I solved my problem after modifying original procedure from post 1368699. I think that 10.04 LTS is different that when original post was created.
I went to Synaptic Package Manager and tried install bcmwl from there even I did not have CD. But Synaptic told me I need to install four packages. I did this with LiveUSB:

Proc_install:
{Right click on package file.
Select Open with GDebi Package Installer.
Disregard advisory about package available on Software Channel.
Click Install Package.}

1. Navigate to pool/main/p/patch and find (the only one) patch_2.6-2ubuntu1_i386.deb. Execute Proc_install.
2. Navigate to pool/main/f/fakeroot and find  fakeroot_1.14.4-1ubuntu1_i386.deb. Execute Proc_install.
3. Navigate to pool/main/d/dkms and find dkms_2.1.1.2-2fakesync1_all.deb. Execute Proc_install.
4. Navigate to pool/restricted/b/bcmwl and find bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb. ExecuteProc_install.
6. Reboot.
7. System>Admin>Hardware Driver and select Broadcom STA Wireless Driver.
8. Right click on Network Manager, looking like miniature radio waves, and check Enable Wireless.
9. Left click on Network Manager and add your network SSI and encryption. 
10. Reboot and enjoy.
Package bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb might report install errors after this. I don't understand this but it works. Brave souls may try newest package ...0ubuntu5...

---

### Post by frogotronic on 2010-06-16
> **emjot said:**
> Thank you all for good direction.
I solved my problem after modifying original procedure from post 1368699. I think that 10.04 LTS is different that when original post was created.
I went to Synaptic Package Manager and tried install bcmwl from there even I did not have CD. But Synaptic told me I need to install four packages. I did this with LiveUSB:

Proc_install:
{Right click on package file.
Select Open with GDebi Package Installer.
Disregard advisory about package available on Software Channel.
Click Install Package.}

1. Navigate to pool/main/p/patch and find (the only one) patch_2.6-2ubuntu1_i386.deb. Execute Proc_install.
2. Navigate to pool/main/f/fakeroot and find  fakeroot_1.14.4-1ubuntu1_i386.deb. Execute Proc_install.
3. Navigate to pool/main/d/dkms and find dkms_2.1.1.2-2fakesync1_all.deb. Execute Proc_install.
4. Navigate to pool/restricted/b/bcmwl and find bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb. ExecuteProc_install.
6. Reboot.
7. System>Admin>Hardware Driver and select Broadcom STA Wireless Driver.
8. Right click on Network Manager, looking like miniature radio waves, and check Enable Wireless.
9. Left click on Network Manager and add your network SSI and encryption. 
10. Reboot and enjoy.
Package bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb might report install errors after this. I don't understand this but it works. Brave souls may try newest package ...0ubuntu5...

Hi,

  Glad it worked out - maybe you could fill a bug at launchpad?

- CH

---

