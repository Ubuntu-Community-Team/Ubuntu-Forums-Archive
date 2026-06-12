---
title: "No Dual Monitor after update 18.04.1."
date: 2018-12-07
forum: Installation &amp; Upgrades
---

### Post by rusty.hinge on 2018-12-07
Installed Ubuntu 18.04.1 LTS update this morning.  After reboot my second monitor no longer works.

Processor: Intel Core&#8482; i7-3820 CPU @ 3.60GHz × 8 
Memory: 15.6
Graphics: GeForce GTX 650/PCIe/SSE2
Troublshooting so far:
Change video driver to X.Org X server from nvudua-driver-390 (no help)
Change video card to older card (no help)
Swapped monitors all (not monitor)
tried Nvidia Binary driver- version 340.107 from nvidia -340 (no help)
   caused crash report (Sent) Revert back to X server.
   
dmesg | grep -i fail
...
[    3.297429] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    4.729014] EDAC sbridge: Failed to register device with error -19.

Any help Appreciated. Thanks
sudo apt-get install -fThe following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
...
3 not fully installed or removed.
Need to get 0 B/29.2 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 248122 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

...

---

### Post by ununtrium on 2018-12-09
> **rusty.hinge said:**
> Installed Ubuntu 18.04.1 LTS update this morning.  After reboot my second monitor no longer works.

Processor: Intel Core™ i7-3820 CPU @ 3.60GHz × 8 
Memory: 15.6
Graphics: GeForce GTX 650/PCIe/SSE2
Troublshooting so far:
Change video driver to X.Org X server from nvudua-driver-390 (no help)
Change video card to older card (no help)
Swapped monitors all (not monitor)
tried Nvidia Binary driver- version 340.107 from nvidia -340 (no help)
   caused crash report (Sent) Revert back to X server.
   
dmesg | grep -i fail
...
[    3.297429] nvidia: module verification failed: signature and/or required key missing - tainting kernel
[    4.729014] EDAC sbridge: Failed to register device with error -19.

Any help Appreciated. Thanks
sudo apt-get install -fThe following additional packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
The following NEW packages will be installed:
  libnvidia-gl-390 libnvidia-gl-390:i386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
...
3 not fully installed or removed.
Need to get 0 B/29.2 MB of archives.
After this operation, 147 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 248122 files and directories currently installed.)
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb ...
diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/i386-linux-gnu/libGL.so.1 to /usr/lib/i386-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb (--unpack):
 new libnvidia-gl-390:i386 package pre-installation script subprocess returned error exit status 2
Preparing to unpack .../libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb ...
diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340
dpkg-divert: error: mismatch on package
  when removing 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 by libnvidia-gl-390'
  found 'diversion of /usr/lib/x86_64-linux-gnu/libGL.so.1 to /usr/lib/x86_64-linux-gnu/libGL.so.1.distrib by nvidia-340'
dpkg: error processing archive /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb (--unpack):
 new libnvidia-gl-390:amd64 package pre-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_i386.deb
 /var/cache/apt/archives/libnvidia-gl-390_390.77-0ubuntu0.18.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

...

Your GFX drivers are a mess. We can fix this no problem. 
Your card needs the 410 version as Nvidia recommends for this make and model.

First set your driver to the "X.OrgXserver" in "Software & Updates"
click reboot
code:
```

sudo apt update && apt upgrade
sudo apt --purge autoremove nvidia*
sudo apt autoclean
sudo apt autoremove
sudo apt update && apt upgrade
sudo reboot

```
code:
```

sudo apt update && apt upgrade
ubuntu-drivers list
sudo apt install nvidia-driver-410
sudo apt update && apt upgrade
sudo reboot

```
Check the "Software & Updates" if the new 410 is activated.
If not then select it (nvidia-drivers-410) and reboot

Other Nvidia driver versions will be listed there. 
Do not use them. Don't try deleting them. Just leave them there.

Hopefully that can solve it
At very least your drivers will work better.

---

