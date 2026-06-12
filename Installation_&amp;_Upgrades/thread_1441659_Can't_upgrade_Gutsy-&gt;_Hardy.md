---
title: "Can't upgrade Gutsy-&gt; Hardy"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by awacs on 2010-03-29
# do-release-upgrade 
Checking for a new ubuntu release
Failed Upgrade tool signature
Failed Upgrade tool
Done downloading            
extracting '/tmp/tmpDtqG4L/hardy.tar.gz'
Failed to extract
Extracting the upgrade failed. There may be a problem with the network or with the server. 

# cat $HOME/.update-manager-core/meta-release

[...]
Dist: hardy
Name: Hardy Heron
Version: 8.04 LTS
Date: Thu, 24 Apr 2008 12:00:00 UTC
Supported: 1
Description: This is the 8.04 LTS release
Release-File: [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)
ReleaseNotes: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.30/ReleaseAnnouncement](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.30/ReleaseAnnouncement)
UpgradeTool: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.30/hardy.tar.gz](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.30/hardy.tar.gz)
UpgradeToolSignature: [http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.30/hardy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy-proposed/main/dist-upgrader-all/0.87.30/hardy.tar.gz.gpg)
[...]

changing this to ...old-releases.ubuntu.com didn't help, either.

What am I missing?

Thanks!

---

### Post by Sef on 2010-03-29
Since Gutsy is no longer supported, you need to do a clean install, i.e., install from a cd.

---

### Post by awacs on 2010-03-31
Are *any* in-place upgrades available? Machine doesn't have a CD drive ...

---

### Post by takisan on 2010-03-31
You could put it onto a flash drive using the flash maker utility that I think is in Karmic.
Then boot and install.

---

### Post by Dayofswords on 2010-03-31
> **takisan said:**
> You could put it onto a flash drive using the flash maker utility that I think is in Karmic.
Then boot and install.
if he doesnt have a cd drive(and using gusty)
i doubt he can boot from usb

i found this to boot a usb via a floppy
just put ubuntu on the usb stick instad of pendrive linux
[http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/](http://www.pendrivelinux.com/use-a-floppy-to-boot-usb-pendrive-linux/)

---

### Post by awacs on 2010-04-08
> **takisan said:**
> You could put it onto a flash drive using the flash maker utility that I think is in Karmic.
Then boot and install.


Hmmm.

My experience in using CD/Flash drive boot installs is that they always (20 out of 20 or so) require me to wipe the root partition (otherwise, the install is hopelessly riddled with errors) which is inconvenient. In-place upgrades, OTOH, seem to work well. 

So, to repeat, can I do an in-place upgrade (i.e., from running the existing system) to *any* version?

---

### Post by gletob on 2010-04-08
Correct me if I'm wrong guys (I probably am) but couldn't he download a hardy alternate cd mount it virtually and upgrade the packages in place?  As a last ditch effort could he change his sources.list file to hardy (obviously not a good thing to do, but as a last resort maybe?)

---

### Post by Slim Odds on 2010-04-08
I have forgotten the name of the program, but it makes a USB bootable drive from the Live CD. It boots from USB, but run just like the Live CD. I'll try to find it.

Also, I've mentioned this many times, don't wait forever to upgrade. Gutsy has been unsupported for quite some time and Hardy was released **2 years ago**.

---

