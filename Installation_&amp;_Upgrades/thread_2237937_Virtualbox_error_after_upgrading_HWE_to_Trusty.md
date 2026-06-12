---
title: "Virtualbox error after upgrading HWE to Trusty"
date: 2014-08-04
forum: Installation &amp; Upgrades
---

### Post by cscj01 on 2014-08-04
I am using 12.04.4 and have been having a message in Update Manager that a new HWE was available.  Up until today, it always failed with dependency issues.  Today I clicked Install, and lo and behold, it completed.  After rebooting, I have the following > uname -a
Linux Car-Photo-Ubuntu 3.13.0-32-generic #57~precise1-Ubuntu SMP Tue Jul 15 03:5

hwe-support-status
Your Hardware Enablement Stack (HWE) is supported until April 2017.However, I have an issue with Virtualbox.  When I try to start it, I get the following message > Failed to open a session for the virtual machine VM.

The virtual machine 'VM' has terminated unexpectedly
during startup with exit code 1.

Details

Result Code:             NS_ERROR_FAILURE ((0x80004005)
Component:              Machine
Interface:                 IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}
I then receive another message as follows > Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not
loaded or there is a permission problem with /dev/vboxdrv.
Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. If it is available in your distribution, you should install
the DKMS package first. This package keeps track of Linux
kernel changes and recompiles the vboxdrv kernel module if
necessary./etc/init.d/vboxdrv and /dev/vboxdrv are not present.  If I check Synaptic, it shows
dkms version 2.2.0.3-1ubuntu3.2
virtualbox-dkms version 4.1.12-dfsg-2ubuntu0.6
virtualbox version 4.1.12-dfsg-2ubuntu0.6
are installed and are the latest versions.

My question is how do I get the Virtualbox kernel driver created without losing my virtual machine and its configuration?

---

### Post by cscj01 on 2014-08-05
bump

---

### Post by kansasnoob on 2014-08-05
Is it related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1292118](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1292118)

I've had a lot of trouble with these HWE EOL upgrades, and release upgrades are still not being offered via update manager:

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826](https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826)

---

### Post by cscj01 on 2014-08-05
> **kansasnoob said:**
> Is it related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1292118](https://bugs.launchpad.net/ubuntu/+source/virtualbox/+bug/1292118)

I've had a lot of trouble with these HWE EOL upgrades, and release upgrades are still not being offered via update manager:

[https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826](https://bugs.launchpad.net/ubuntu-release-notes/+bug/1351826)

Yes, I actually tried the solutions they gave at the latter end of that.  I removed 4.1.12 and installed 4.3.14.  Problem is, the VM will now launch, but the desktop is messed up; it only partially shows.  I can get around that by minimizing then maximizing the desktop.  But the same thing happens with applications windows in the VM.  And some of those I cannot close, because the minimize and maximize icons are not visible.

I suppose I should show this thread as solved because I actually have gotten rid of the problem I had.  However, I may wait a while in case someone sees this and has an answer for what is now happening.

---

### Post by cezar-andrei on 2014-10-30
I had the same problem, due to the bug reported in an earlier post.

I fixed the problem by purging the 4.1.x version.
    apt-get purge virtualbox virtualbox-dkms virtualbox-source virtualbox-ose-dkms linux-headers-generic virtualbox-qt virtualbox-guest-additions-iso

And installing the latest 4.3 version:
    apt-get install virtualbox-4.3

Note: make sure you have dkms package installed already and the virtualbox ppa [http://download.virtualbox.org/virtualbox/debian](http://download.virtualbox.org/virtualbox/debian) in your Software source list.

---

