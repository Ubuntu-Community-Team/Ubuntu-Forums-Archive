---
title: "Problem with ATI graphic card driver installation. Help~~"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by sinogermany on 2008-11-03
Hi everyone,

I'm new here and am not sure whether I chose the right category.
I got a problem with ATI driver installation.
[COLOR="Red"]OS: Ubuntu 8.10 desktop version, x86(32 bit)
Graphic card: ATI Radeon 2600Pro[/COLOR]

The OS installation process was pretty smooth.
It's a pure Linux system without Bill's products.
The first thing I did, after istalling the OS, 
is installing ATI driver.

I downloaded the driver from AMD official site:
[COLOR="Red"]ati-driver-installer-8-10-x86.x86_64.run[/COLOR]
Then I copied it on to the desktop.

Here's what I did in the Terminal:
[COLOR="red"]sudo apt-get update
sudo sh ati-driver-installer-8-10-x86.x86_64.run[/COLOR]


Then I recieved the information below:
[COLOR="red"]Created directory fglrx-install.IU9747
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.542...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.27-7-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.IU9747[/COLOR]



Anyone who encountered the similar problem?
Or could anyone give me some useful hints?

I can't accept the 800*600 resolution on any OS.

Thanks a lot for your help!

Daniel

---

### Post by sinogermany on 2008-11-04
Could anyone give me some suggestions?

---

### Post by bvtd092 on 2008-11-04
After downloading the ati driver installer version 8.10 from the website [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html) and trying to install under ubuntu 8.10 i've got also the following error:

sh ./ati-driver-installer-8-10-x86.x86_64.run 
Created directory fglrx-install.M17050
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.542...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.27-7-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.M17050
bvtd092@ubuntu810:~/Desktop$

Video card: ati radeon hd3870.

Bug description from ubuntu:
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/264462](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/264462)

When I try starting from the 8.10 livecd after the splash screen i've got a black screen. The only thing i can do is CNTRL ALT F1.

Is there a solution for that problem?

Greetings,

---

### Post by ristretto_dreams on 2008-11-04
I had the same problem, for whatever reason this fixed it:
```

chmod a+x ./ati-driver-installer-8-10-x86.x86_64.run 
./ati-driver-installer-8-10-x86.x86_64.run 

```

---

### Post by bvtd092 on 2008-11-05
After testing your suggestion i've had the same problem.

See output:
root@ubuntu810:/home/bvtd092/Desktop# chmod a+x ./ati-driver-installer-8-10-x86.x86_64.run 
root@ubuntu810:/home/bvtd092/Desktop# ./ati-driver-installer-8-10-x86.x86_64.run 
Created directory fglrx-install.l10694
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.542...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.27-7-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.l10694
root@ubuntu810:/home/bvtd092/Desktop# 


Are you sure you test it with Ubuntu 8.10, because with Ubuntu 8.04 that driver is working!

Greetings,

---

### Post by torgrot on 2008-11-05
That driver is not compatible with the version of X-org installed in Ubunut 8.10.  Until AMD/ATI updates the driver to work with X-org 7.4 you are SOL.

torgrot

---

### Post by bvtd092 on 2008-11-05
Torgrot,

Thank you for the necessary information.
Indeed the driver you can download from the ati site is only compatible for the following x-org versions:

Automated installer and Display Drivers for X.Org 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3

Hopefully, they develop asap the new drivers!

Regards,

---

### Post by sbooder on 2008-11-24
I am a bit of a Linux novice, but is it possible to roll back the X,org version in Ubuntu 8.10?

---

