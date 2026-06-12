---
title: "Synaptic/Update Manager won't complete -- kernel errors"
date: 2009-12-28
forum: Installation &amp; Upgrades
---

### Post by ray field on 2009-12-28
I'm having problems with Update Manager, as well as Synaptic, on this Asus eee PC 1000.

1) It may be unrelated, but a couple of weeks ago, I was forced to reinstall from a backup -- everything seemed to go alright once I reset some ownerships and permissions, however, there seems to be a lot of CPU usage even when the netbook is idle -- CPU temp tends to escalate rapidly, for instance, right now, having just restarted, with only gedit and Thunderbird running, it's going between 70-90% and the temp is 63 C.

2) When I try running Update Manager, or when I try to "Recover Broken Packages" after choosing the recovery kernel from Grub, I get consistent errors which I don't understand (incompletely compiled kernel?)  When I watch the processing routines, I seem to see consistent errors related to NVidia

Here is the error message generated after Update Manager fails to complete:

```
E: linux-image-2.6.27-15-generic: subprocess post-installation script returned error exit status 2
E: linux-backports-modules-2.6.27-15-generic: dependency problems - leaving unconfigured
E: linux-image-2.6.27-11-generic: subprocess post-installation script returned error exit status 2
E: linux-restricted-modules-2.6.27-15-generic: dependency problems - leaving unconfigured
E: linux-headers-2.6.27-11-generic: subprocess post-installation script returned error exit status 2
E: linux-headers-2.6.27-15-generic: subprocess post-installation script returned error exit status 2
E: nvidia-common: subprocess post-installation script returned error exit status 1

```

---

### Post by slakkie on 2009-12-28
Could you show us the full logs?

You can have a look in /var/log/apt and/or /var/log/dist-upgrade and/or /var/log/aptitude.

---

### Post by ray field on 2009-12-28
> Could you show us the full logs?

You can have a look in /var/log/apt

this has many, many entries, most of which seem identical or nearly so -- this should be a representative chunk:

```
[74G[ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 2, in <module>
    import NvidiaDetector
ImportError: No module named NvidiaDetector
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-11-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.27-11-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-headers-2.6.27-15-generic (2.6.27-15.43) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-15-generic       [80G 
 *  rt2860sta (1.8LK)...       [80G rt2860sta (1.8LK): Already installed on this kernel.

[74G[ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 2, in <module>
    import NvidiaDetector
ImportError: No module named NvidiaDetector
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-15-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.27-15-generic (--configure):
 subprocess post-installation script returned error exit status 2
Setting up linux-headers-2.6.27-16-generic (2.6.27-16.44) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.27-16-generic       [80G 
 *  rt2860sta (1.8LK)...       [80G rt2860sta (1.8LK): Already installed on this kernel.

[74G[ OK ]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 2, in <module>
    import NvidiaDetector
ImportError: No module named NvidiaDetector
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.27-16-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.27-16-generic (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.27-16-generic; however:
  Package linux-headers-2.6.27-16-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Setting up nvidia-common (0.2.4.2) ...
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 2, in <module>
    import NvidiaDetector
ImportError: No module named NvidiaDetector
dpkg: error processing nvidia-common (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.27-15-generic
 linux-backports-modules-2.6.27-15-generic
 linux-image-2.6.27-16-generic
 linux-backports-modules-2.6.27-16-generic
 linux-image-2.6.27-11-generic
 linux-restricted-modules-2.6.27-15-generic
 linux-restricted-modules-2.6.27-16-generic
 linux-backports-modules-intrepid-generic
 linux-image-generic
 linux-restricted-modules-generic
 linux-generic
 linux-headers-2.6.27-11-generic
 linux-headers-2.6.27-15-generic
 linux-headers-2.6.27-16-generic
 linux-headers-generic
 nvidia-common
Log ended: 2009-12-28  12:02:12
```


> and/or /var/log/dist-upgrade 

main.log.partial:

```
2009-12-28 11:53:46,279 INFO release-upgrader version '0.93.34' started
2009-12-28 11:53:46,282 DEBUG Using 'DistUpgradeViewText' view
2009-12-28 11:53:46,422 DEBUG enable dpkg --force-overwrite
2009-12-28 11:53:46,572 DEBUG lsb-release: 'intrepid'
2009-12-28 11:53:46,572 DEBUG _pythonSymlinkCheck run
2009-12-28 11:53:46,574 DEBUG openCache()
2009-12-28 11:53:48,982 DEBUG /openCache()
2009-12-28 11:53:48,983 DEBUG needServerMode(): run in 'desktop' mode, (because of pkg 'ubuntu-desktop')
2009-12-28 11:53:48,983 DEBUG checkViewDepends()
2009-12-28 11:53:48,984 DEBUG doPostInitialUpdate
2009-12-28 11:53:48,984 DEBUG quirks: running intrepidPostInitialUpdate
2009-12-28 11:53:48,985 DEBUG running intrepidPostInitialUpdate
2009-12-28 11:53:55,822 DEBUG Foreign: cairo-dock-plug-ins-integration linux-restricted-modules-eeepc linux-eeepc cairo-dock-data cairo-dock-core google-chrome-unstable linux-image-eeepc cairo-dock-plug-ins cairo-dock-plug-ins-data linux-image-2.6.27-8-eeepc wicd eeepc-config cairo-dock
2009-12-28 11:53:55,822 DEBUG Obsolete: adobe-flashplugin rt2860sta-dkms opera skychart webmin skype mucommander
2009-12-28 11:53:56,830 DEBUG Installing 'python2.4-minimal' (priority in required set 'required' but not scheduled for install)
2009-12-28 11:53:57,641 DEBUG Installing 'ash' (priority in required set 'required' but not scheduled for install)
2009-12-28 11:53:58,957 DEBUG Running KeepInstalledSection rules
2009-12-28 11:53:59,220 DEBUG Kernel uname: '2.6.27-16-generic' 
2009-12-28 11:53:59,232 DEBUG nvidiaUpdate()
2009-12-28 11:53:59,233 ERROR NvidiaDetector can not be imported No module named NvidiaDetector.nvidiadetector
2009-12-28 11:53:59,234 DEBUG Removing 'libflashsupport' (Distro PostUpgradeRemove rule)
2009-12-28 11:53:59,235 DEBUG Removing 'xscreensaver' (ubuntu-desktop PostUpgradeRemove rule)
2009-12-28 11:53:59,680 DEBUG Removing 'gnome-cups-manager' (ubuntu-desktop PostUpgradeRemove rule)
2009-12-28 11:53:59,681 DEBUG Purging 'xorg-common' (Distro PostUpgradePurge rule)
2009-12-28 11:53:59,681 DEBUG Purging 'libgl1-mesa' (Distro PostUpgradePurge rule)
2009-12-28 11:53:59,682 DEBUG Purging 'ltsp-client' (Distro PostUpgradePurge rule)
2009-12-28 11:54:00,128 DEBUG Purging 'ltspfsd' (Distro PostUpgradePurge rule)
2009-12-28 11:54:00,575 DEBUG Purging 'python2.3' (Distro PostUpgradePurge rule)
2009-12-28 11:54:00,576 DEBUG quirks: running intrepidPostDistUpgradeCache
2009-12-28 11:54:00,576 DEBUG running intrepidPostDistUpgradeCache
2009-12-28 11:54:01,732 DEBUG Marking 'ubuntu-desktop' for upgrade
2009-12-28 11:54:03,371 ERROR Unauthenticated packages found: 'ash blt python2.4 python2.4-minimal'
```

from most recent entry in apt.log

```
Log time: 2009-12-28 11:53:48.561775
Starting
Starting 2
Done
Installing python2.4 as dep of python2.4-minimal
Installing blt as dep of python2.4
MarkUpgrade() called on a non-upgrable pkg: 'ubuntu-desktop'

Error authenticating some packages 

It was not possible to authenticate some packages. This may be a 
transient network problem. You may want to try again later. See below 
for a list of unauthenticated packages. 

ash 
blt 
python2.4 
python2.4-minimal 
```

happy to provide more if need be.

---

### Post by ray field on 2009-12-30
[bump]

---

### Post by ray field on 2010-01-13
[ bump ]

---

### Post by earthtux on 2010-01-21
bump
I have the same issue
I saw from another google result saying it's cause the /boot is full
how to resize /boot?
thank you all!

---

