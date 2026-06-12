---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by Ibanezz on 2011-07-26
When I did an upgrade i got
E: Sub-process /usr/bin/dpkg returned an error code (1)
than I did the command below but still look at the output :S
Can anyone help me please ?

ubuntu@ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
8 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up initramfs-tools (0.98.8ubuntu3.1) ...
update-initramfs: deferring update (trigger activated)
/usr/sbin/update-initramfs: 20: lzma: not found
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 127
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-2.6.38-10-generic:
 linux-image-2.6.38-10-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
  Package initramfs-tools is not configured yet.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth:
 plymouth depends on initramfs-tools; however:
  Package initramfs-tools is not configured yet.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
            No apport report written because MaxReports is reached already
                                                                          dpkg: error processing plymouth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
 plymouth-theme-ubuntu-text depends on plymouth; however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-theme-ubuntu-text (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems preveNo apport report written because MaxReports is reached already
                                                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                                                                                                         nt configuration of plymouth-label:
 plymouth-label depends on plymouth (= 0.8.2-2ubuntu23); however:
  Package plymouth is not configured yet.
dpkg: error processing plymouth-label (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of plymouth-theme-kubuntu-text:
 plymouth-theme-kubuntu-text depends on plymouth; however:
  Package plymouth is not configured yet.
 plymouth-theme-kubuntu-text depends on plymouth-theme-ubuntu-text; however:
  Package plymouth-theme-ubuntu-text is not configured yet.
dpkg: error processing plymouth-theme-kubuntu-text (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 initramfs-tools
 linux-image-2.6.38-10-generic
 plymouth
 plymouth-theme-ubuntu-text
 linux-image-generic
 linux-generic
 plymouth-label
 plymouth-theme-kubuntu-text
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by thefasterblueone on 2011-07-26
```
sudo dpkg --configure -a
```

[**Bug Report**](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/790794)

---

### Post by Ibanezz on 2011-07-26
Thats not working too..

---

### Post by Ibanezz on 2011-07-27
Here is the output of the command



[LIST=1]
[*]sudo dpkg --configure -a
[*]Setting up initramfs-tools (0.98.8ubuntu3.1) ...
[*]update-initramfs: deferring update (trigger activated)
[*]lzma: Encoder error: -2147467259
[*]dpkg: error processing initramfs-tools (--configure):
[*] subprocess installed post-installation script returned error exit status 1
[*]dpkg: dependency problems prevent configuration of casper:
[*] casper depends on initramfs-tools (>= 0.92bubuntu55); however:
[*]  Package initramfs-tools is not configured yet.
[*]dpkg: error processing casper (--configure):
[*] dependency problems - leaving unconfigured
[*]dpkg: dependency problems prevent configuration of linux-image-2.6.38-10-generic:
[*] linux-image-2.6.38-10-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
[*]  Package initramfs-tools is not configured yet.
[*]dpkg: error processing linux-image-2.6.38-10-generic (--configure):
[*] dependency problems - leaving unconfigured
[*]dpkg: dependency problems prevent configuration of linux-image-2.6.38-11-generic:
[*] linux-image-2.6.38-11-generic depends on initramfs-tools (>= 0.36ubuntu6); however:
[*]  Package initramfs-tools is not configured yet.
[*]dpkg: error processing linux-image-2.6.38-11-generic (--configure):
[*] dependency problems - leaving unconfigured
[*]dpkg: dependency problems prevent configuration of plymouth:
[*] plymouth depends on initramfs-tools; however:
[*]  Package initramfs-tools is not configured yet.
[*]dpkg: error processing plymouth (--configure):
[*] dependency problems - leaving unconfigured
[*]dpkg: dependency problems prevent configuration of linux-image-generic:
[*] linux-image-generic depends on linux-image-2.6.38-11-generic; however:
[*]  Package linux-image-2.6.38-11-generic is not configured yet.
[*]dpkg: error processing linux-image-generic (--configure):
[*] dependency problems - leaving unconfigured
[*]dpkg: dependency problems prevent configuration of linux-generic:
[*] linux-generic depends on linux-image-generic (= 2.6.38.11.26); however:
[*]  Package linux-image-generic is not configured yet.
[*]dpkg: error processing linux-generic (--configure):
[*] dependency problems - leaving unconfigured
[*]dpkg: dependency problems prevent configuration of plymouth-theme-kubuntu-text:
[*] plymouth-theme-kubuntu-text depends on plymouth; however:
[*]  Package plymouth is not configured yet.
[*]dpkg: error processing plymouth-theme-kubuntu-text (--configure):
[*] dependency problems - leaving unconfigured
[*]dpkg: dependency problems prevent configuration of plymouth-theme-ubuntu-text:
[*] plymouth-theme-ubuntu-text depends on plymouth; however:
[*]  Package plymouth is not configured yet.
[*]dpkg: error processing plymouth-theme-ubuntu-text (--configure):
[*] dependency problems - leaving unconfigured
[*]dpkg: dependency problems prevent configuration of plymouth-label:
[*] plymouth-label depends on plymouth (= 0.8.2-2ubuntu23); however:
[*]  Package plymouth is not configured yet.
[*]dpkg: error processing plymouth-label (--configure):
[*] dependency problems - leaving unconfigured
[*]Errors were encountered while processing:
[*] initramfs-tools
[*] casper
[*] linux-image-2.6.38-10-generic
[*] linux-image-2.6.38-11-generic
[*] plymouth
[*] linux-image-generic
[*] linux-generic
[*] plymouth-theme-kubuntu-text
[*] plymouth-theme-ubuntu-text
[*] plymouth-label
[*]Re: E: Sub-process /usr/bin/dpkg returned an error code (1)
[/LIST]

---

### Post by thefasterblueone on 2011-07-27
You are getting a lzma error '/usr/sbin/update-initramfs: 20: lzma: not found' , so let's install it.

```
sudo apt-get install lzma
```

then:

```
sudo apt-get update
```

then try your upgrade.

---

### Post by spearsem on 2011-08-01
I have a similar issue, minus the lzma not found. It seems to be a larger problem with the kernel, but I cannot figure it out.

```
ely@zaffpants:~/Desktop$ sudo dpkg --configure -a
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic               
 *       nvidia-current (270.41.06)...                                         [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-headers-2.6.38-10-generic (2.6.38-10.46) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic               
 *       nvidia-current (270.41.06)...                                         [ OK ] 
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.38-10-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.38-10-generic; however:
  Package linux-headers-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.38-10-generic
 linux-headers-2.6.38-10-generic
 linux-image-generic
 linux-generic
 linux-headers-generic
```

---

### Post by spearsem on 2011-08-01
I don't know if this will work for the above error, but I was able to fix this by first

```

sudo apt-get purge nvidia-common 
sudo aptitude safe-upgrade

```

Followed by dpkg --configure, apt-get install -f, etc., and then after getting everything sorted out I re-installed nvidia-common. For me, CUPS was the main error, and this would hang every time I tried a system upgrade. Removing nvidia-common allowed the upgrade (and associated CUPS issues) to get sorted out.

---

