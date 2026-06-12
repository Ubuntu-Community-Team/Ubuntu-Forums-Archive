---
title: "dpkg: dependency problems prevent configuration of initramfs-tools:"
date: 2014-02-02
forum: Installation &amp; Upgrades
---

### Post by Umang_Agrawal on 2014-02-02
```
umang@umang-samsung-NP300-V5A-S0GIN:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  initramfs-tools
The following packages will be upgraded:
  initramfs-tools
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
Need to get 0 B/49.2 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of initramfs-tools:
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.3.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.4.
dpkg: error processing initramfs-tools (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-3.2.0-58-generic:
 linux-image-3.2.0-58-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                            Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-3.2.0-58-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of dmsetup:
 dmsetup depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
dpkg: error processing dmsetup (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-58-generic; however:
  Package linux-image-3.2.0-58-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                  No apport report written because MaxReports is reached already
                                                                                                                                dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.58.69); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdevmapper1.02.1:
 libdevmapper1.02.1 depends on dmsetup (>= 2:1.02.48-4ubuntu7.4); however:
  Package dmsetup is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing libdevmapper1.02.1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of grub-common:
 grub-common depends on libdevmapper1.02.1 (>= 2:1.02.36); however:
  Package libdevmapper1.02.1 is not configured yet.
dpkg: error processing grub-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub2-common:
 grub2-common depends on grub-common (= 1.99-21ubuntu3.14); however:
  Package grub-common is not configured yet.
dpkg: error processing grub2-common (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-pc-bin:
 grub-pc-bin depends on libdevmapper1.02.1 (>= 2:1.02.36); however:
  Package libdevmapper1.02.1 is not configured yet.
 grub-pc-bin depends on grub-common (= 1.99-21ubuntu3.14); however:
  Package grub-common is not configured yet.
dpkg: error processing grub-pc-bin (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of grub-pc:
 grub-pc depends on grub-common; however:
  Package grub-common is not configured yet.
 grub-pc depends on grub2-common (= 1.99-21ubuntu3.14); however:
  Package grub2-common is not configured yet.
 grub-pc depends on grub-pc-bin (= 1.99-21ubuntu3.14); however:
  Package grub-pc-bin is not configured yet.
dpkg: error processing grub-pc (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libdevmapper-event1.02.1:
 libdevmapper-event1.02.1 depends on libdevmapper1.02.1 (>= 2:1.02.36); however:
No apport report written because MaxReports is reached already
                                                                Package libdevmapper1.02.1 is not configured yet.
dpkg: error processing libdevmapper-event1.02.1 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of liblvm2app2.2:
 liblvm2app2.2 depends on libdevmapper-event1.02.1 (>= 2:1.02.20); however:
  Package libdevmapper-event1.02.1 is not configured yet.
 liblvm2app2.2 depends on libdevmapper1.02.1 (>= 2:1.02.44); however:
  Package libdevmapper1.02.1 is not configured yet.
dpkg: error processing liblvm2app2.2 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 initramfs-tools
 linux-image-3.2.0-58-generic
 dmsetup
 linux-image-generic
 linux-generic
 libdevmapper1.02.1
 grub-common
 grub2-common
 grub-pc-bin
 grub-pc
 libdevmapper-event1.02.1
 liblvm2app2.2
E: Sub-process /usr/bin/dpkg returned an error code (1)


```


Please help

---

### Post by varunendra on 2014-02-03
Welcome to the forums Umang!

> **Umang_Agrawal said:**
> ```
 initramfs-tools depends on initramfs-tools-bin (<< 0.99ubuntu13.3.1~); however:
  Version of initramfs-tools-bin on system is 0.99ubuntu13.4.
```
The version that dpkg expects is no longer there in the repositories. So let's try manually installing the updated package so it gets over its confusion..

Download the updated package : [http://archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/i/initramfs-tools/initramfs-tools_0.99ubuntu13.4_all.deb)
Assuming the above package is downloaded in your "Downloads" directory, install it with -
```
sudo dpkg -i Downloads/initramfs-tools_0.99ubuntu13.4_all.deb
```
Any errors? Post back if there are. If not, try -
```
sudo apt-get install -f
```
..again and let us know if the problem got fixed.

---

### Post by Umang_Agrawal on 2014-02-04
```
umang@umang-samsung-NP300-V5A-S0GIN:~$ sudo dpkg -i Downloads/initramfs-tools_0.99ubuntu13.4_all.deb
[sudo] password for umang: 
(Reading database ... 225005 files and directories currently installed.)
Preparing to replace initramfs-tools 0.99ubuntu13.3 (using .../initramfs-tools_0.99ubuntu13.4_all.deb) ...
Unpacking replacement initramfs-tools ...
Setting up initramfs-tools (0.99ubuntu13.4) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for man-db ...
Processing triggers for doc-base ...
Processing 1 changed doc-base file...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-55-generic
/usr/sbin/update-initramfs: 173: /usr/sbin/update-initramfs: mv: not found
dpkg: error processing initramfs-tools (--install):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 initramfs-tools
umang@umang-samsung-NP300-V5A-S0GIN:~$ 

```

---

### Post by varunendra on 2014-02-05
How much disk space you have left? Please show us the output of -
```
df -h
```

Also, the output of -
```
dpkg -l | grep linux-image
```

---

