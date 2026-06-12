---
title: "Tried to upgrade Kernel, failed to make initrd image"
date: 2010-10-26
forum: Installation &amp; Upgrades
---

### Post by Maahes on 2010-10-26
See here:
> Setting up linux-image-2.6.32-25-generic (2.6.32-25.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
gzip: /initrd.img.gz: No such file or directory
cp: cannot stat `/vmlinuz': No such file or directory
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-25-generic; however:
  Package linux-image-2.6.32-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.25.27); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 linux-image-2.6.32-25-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up linux-image-2.6.32-25-generic (2.6.32-25.45) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.32-25-generic
gzip: /initrd.img.gz: No such file or directory
cp: cannot stat `/vmlinuz': No such file or directory
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-25-generic; however:
  Package linux-image-2.6.32-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.25.27); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.32-25-generic
 linux-image-generic
 linux-generic

---

### Post by Maahes on 2010-10-26
If anyone does have any expertise with this, I could really use it, I've been quietly asking for help on #ubuntu few days and no one has been able to help me. This is after doing some extensive googling as well.

---

### Post by ArgentStar on 2010-10-29
I'm having a similar problem upgrading.  I enter the usual: 

sudo apt-get dist-upgrade

But what I get is...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.32-25-generic (2.6.32-25.45) ...
Running depmod.
Cannot create version 2.6.32-25-generic: already exists
Failed to create initrd image.
dpkg: error processing linux-image-2.6.32-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.32-25-generic; however:
  Package linux-image-2.6.32-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.32.25.27); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-headers-2.6.32-25-generic (2.6.32-25.45) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                            No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                        Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.32-25-generic /boot/vmlinuz-2.6.32-25-generic
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.32-25-generic /boot/vmlinuz-2.6.32-25-generic
Traceback (most recent call last):
  File "/usr/bin/nvidia-detector", line 8, in <module>
    a = NvidiaDetection(printonly=True)
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 85, in __init__
    self.printSelection()
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 408, in printSelection
    driver = self.selectDriver()
  File "/usr/lib/python2.6/dist-packages/NvidiaDetector/nvidiadetector.py", line 328, in selectDriver
    choice = self.driversForCards[self.driversForCards.keys()[0]][0]
IndexError: list index out of range
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.32-25-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.32-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-25-generic; however:
  Package linux-headers-2.6.32-25-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 linux-image-2.6.32-25-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.32-25-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

...and when I boot the new image is available in the GRUB2 menu, but selecting it just gives me a scrambled looking screen with some blue garbage at the top.  Booting from the old image works fine.

Any assistance would be much appreciated. Many thanks. :)

---

