---
title: "Error updating linux-image-2.6.38-10-generic (2.6.38-10.46) in Ubuntu 11.04"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by AeroRich on 2011-08-04
Hello Ubuntu-ers,

Let me preface this post by claiming a certain level of ignorance. I most likely know enough about Linux to get myself into deep do-do, but not enough to dig myself out of it.  I am a long-time forum reader, but first-time forum poster.

I recently (~2 wks) installed Ubuntu 11.04 onto a rather old Intel machine. I honestly did nothing special with the installation.  Everything was default (except for my username and host name ^_^). Since the installation, there are certain pieces of software that I can't seem to install.  Most notably, XBMC, Opera, and Spotify.  I also cannot seem to do an apt-get upgrade. They all seem to throw the same error associated with the linux-image. Much googling and forum searches have not found anything that seems to be pertinent.

My apt-get upgrade results are listed below.  I'm happy to provide what ever other information anyone identifies as relevant to debugging this.  Many thanks in advance,

~Rich

```

rich@argos:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.38-10-generic (2.6.38-10.46) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-10-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic                                                                     
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-10-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.38-8-generic (2.6.38-8.42) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.38-8-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.38-8.42 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.38-8.42 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
 * dkms: running auto installation service for kernel 2.6.38-8-generic                                                                      
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.38-8-generic /boot/vmlinuz-2.6.38-8-generic
run-parts: /etc/kernel/postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.38-8-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.38-8-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.38-10-generic; however:
  Package linux-image-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.38.10.25); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up linux-headers-2.6.38-10-generic (2.6.38-10.46) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
 * dkms: running auto installation service for kernel 2.6.38-10-generic                                                                     
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.38-10-generic /boot/vmlinuz-2.6.38-10-generic
run-parts: /etc/kernel/header_postinst.d/nvidia-common exited with return code 10
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.38-10-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.38-10-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.38-10-generic; however:
  Package linux-headers-2.6.38-10-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.38-10-generic
 linux-image-2.6.38-8-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.38-10-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by YannBuntu on 2011-08-04
Hi

Via Synaptic, try uninstalling linux-image-2.6.38-10-generic , the reinstall it.

---

### Post by AeroRich on 2011-08-04
Hello YannBuntu,

I seem to recall trying to do just as you suggested with a similar result.  This morning, I tried to refresh the OS from a new install CD. When that finished, I noticed my keyboard and mouse no longer work so it will be tough to try absolutely anything :)

I'll be sure to see what I can do when I get home tonight.  Thanks for the response.

~Rich

---

