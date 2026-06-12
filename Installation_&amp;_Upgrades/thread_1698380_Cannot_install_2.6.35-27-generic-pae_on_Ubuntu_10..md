---
title: "Cannot install 2.6.35-27-generic-pae on Ubuntu 10.10"
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by blackyhn on 2011-03-02
So this is what happens 

*******************************************************************



apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
5 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.35-27-generic (2.6.35-27.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-27-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
 * dkms: running auto installation service for kernel 2.6.35-27-generic                                                                                                                                    
 *       nvidia-current (260.19.06)...                                                                                                                                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-27-generic /boot/vmlinuz-2.6.35-27-generic
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-27-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-2.6.35-27-generic-pae (2.6.35-27.48) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-27-generic-pae                                                                                                                                        
Examining /etc/kernel/postinst.d.                                                                                                                                                                          
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-27-generic-pae /boot/vmlinuz-2.6.35-27-generic-pae                                                                                                 
 * dkms: running auto installation service for kernel 2.6.35-27-generic-pae                                                                                                                                
 *       nvidia-current (260.19.06)...                                                                                                                                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-27-generic-pae /boot/vmlinuz-2.6.35-27-generic-pae                                                                                      
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-27-generic-pae /boot/vmlinuz-2.6.35-27-generic-pae                                                                                        
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-27-generic-pae /boot/vmlinuz-2.6.35-27-generic-pae                                                                                             
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-27-generic-pae /boot/vmlinuz-2.6.35-27-generic-pae                                                                                      
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-27-generic-pae /boot/vmlinuz-2.6.35-27-generic-pae                                                                                       
/etc/default/grub: 9: splash: not found                                                                                                                                                                    
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic-pae.postinst line 1010.
dpkg: error processing linux-image-2.6.35-27-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            No apport report written because MaxReports is reached already
                                                                                                                                                                                          No apport report written because MaxReports is reached already
                                             dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-2.6.35-27-generic-pae; however:
  Package linux-image-2.6.35-27-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 2.6.35.27.35); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-27-generic; however:
  Package linux-image-2.6.35-27-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-27-generic
 linux-image-2.6.35-27-generic-pae
 linux-image-generic-pae
 linux-generic-pae
 linux-image-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



*********************************************

what's wrong ? I have installed source and headers ...:-k

---

### Post by blackyhn on 2011-03-02
PROGRESS...

*************************************
apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-2.6.35-27-generic-pae
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 108MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 331479 files and directories currently installed.)
Removing linux-image-2.6.35-27-generic-pae ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-27-generic-pae /boot/vmlinuz-2.6.35-27-generic-pae
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-27-generic-pae /boot/vmlinuz-2.6.35-27-generic-pae
/etc/default/grub: 9: splash: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-27-generic-pae.postrm line 328.
dpkg: error processing linux-image-2.6.35-27-generic-pae (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-2.6.35-27-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by blackyhn on 2011-03-02
SOLVED 
Removed "slpash" from /etc/defauls/grub
):P

---

