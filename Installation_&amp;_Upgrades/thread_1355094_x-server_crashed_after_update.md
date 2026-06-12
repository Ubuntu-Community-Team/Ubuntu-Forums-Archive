---
title: "x-server crashed after update"
date: 2009-12-14
forum: Installation &amp; Upgrades
---

### Post by mayankbhagya on 2009-12-14
my x-server resulted in a blinking screen after an automatic update  followed by a restart on ubuntu-karmic. 

i have a nvidia 8400m gs and was running nvidia-185 drivers smoothly until this update happened and asked restart.

while digging deeper, i found that linux-headers and linux-image are half configured packages in dpkg status files and won't let install any other packages too...

I have even tried reinstalling these after removing these packages from dpkg status file. The output of dpkg --configure -a:

$ sudo dpkg --configure -a
Setting up linux-headers-2.6.31-16-generic (2.6.31-16.53) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-16-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.31-16-generic (2.6.31-16.53) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-16-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-16-generic; however:
  Package linux-headers-2.6.31-16-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-16-generic; however:
  Package linux-image-2.6.31-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.16.29); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-2.6.31-16-generic
 linux-image-2.6.31-16-generic
 linux-headers-generic
 linux-image-generic
 linux-generic
$ 


I have also tried: 
sudo apt-get -f install

Plzz help...

---

### Post by mayankbhagya on 2009-12-15
This is what happens on 'sudo apt-get -f install':


$ sudo apt-get -f install
[sudo] password for bhagya: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 64 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.31-16-generic (2.6.31-16.53) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-16-generic
Running postinst hook script /usr/sbin/update-grub.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
run-parts: failed to exec /etc/kernel/postinst.d/dkms: Exec format error
run-parts: /etc/kernel/postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-16-generic.postinst line 1002.
dpkg: error processing linux-image-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.31-16-generic; however:
  Package linux-image-2.6.31-16-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.31.16.29); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                                           No apport report written because the error message indicates its a followup error from a previous failure.
                                                                        headers-2.6.31-16-generic (2.6.31-16.53) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
run-parts: failed to exec /etc/kernel/header_postinst.d/dkms: Exec format error
run-parts: /etc/kernel/header_postinst.d/dkms exited with return code 1
Failed to process /etc/kernel/header_postinst.d at /var/lib/dpkg/info/linux-headers-2.6.31-16-generic.postinst line 110.
dpkg: error processing linux-headers-2.6.31-16-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.31-16-generic; however:
  Package linux-headers-2.6.31-16-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            Errors were encountered while processing:
 linux-image-2.6.31-16-generic
 linux-image-generic
 linux-generic
 linux-headers-2.6.31-16-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
$

---

