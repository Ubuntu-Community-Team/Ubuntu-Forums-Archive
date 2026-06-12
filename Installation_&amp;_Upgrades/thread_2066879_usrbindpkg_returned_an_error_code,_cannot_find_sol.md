---
title: "/usr/bin/dpkg returned an error code, cannot find solution on any other forum"
date: 2012-10-05
forum: Installation &amp; Upgrades
---

### Post by numbrain2go on 2012-10-05
ok, so i'm having a problem where everything i try to update on my system(ubuntu 12.04) will not fully update or install. when i use sudo apt-get upgrade i get this: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-3.2.0-31-generic-pae (3.2.0-31.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-31-generic-pae /boot/vmlinuz-3.2.0-31-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-31-generic-pae /boot/vmlinuz-3.2.0-31-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-31-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-31-generic-pae /boot/vmlinuz-3.2.0-31-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-31-generic-pae /boot/vmlinuz-3.2.0-31-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-31-generic-pae /boot/vmlinuz-3.2.0-31-generic-pae
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-31-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-31-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-31-generic-pae; however:
  Package linux-image-3.2.0-31-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic-pae (= 3.2.0.31.34); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 3.2.0.31.34); however:
  Package linux-image is not configured yet.
dpkg: error processing linux (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up linux-image-3.2.0-31-generic (3.2.0-31.50) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
Error! Your kernel headers for kernel 3.2.0-31-generic cannot be found.
Please install the linux-headers-3.2.0-31-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.2.0-31-generic cannot be found.
Please install the linux-headers-3.2.0-31-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.2.0-31-generic cannot be found.
Please install the linux-headers-3.2.0-31-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
Error! Your kernel headers for kernel 3.2.0-31-generic cannot be found.
Please install the linux-headers-3.2.0-31-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-31-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-31-generic /boot/vmlinuz-3.2.0-31-generic
/usr/sbin/grub-mkconfig: 11: /etc/default/grub: splash: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-31-generic.postinst line 1010.
dpkg: error processing linux-image-3.2.0-31-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up grub-pc (1.99-21ubuntu3.4) ...
No apport report written because MaxReports is reached already
                                                              /var/lib/dpkg/info/grub-pc.config: 11: /etc/default/grub: splash: not found
dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-3.2.0-31-generic; however:
  Package linux-image-3.2.0-31-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 3.2.0.31.34); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-pae:
 linux-generic-pae depends on linux-image-generic-pae (= 3.2.0.31.34); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-generic-pae (--configure):
 dependency problems - leavNo apport report written because MaxReports is reached already
         No apport report written because MaxReports is reached already
                                                                       No apport report written because MaxReports is reached already
                                                     No apport report written because MaxReports is reached already
                                   ing unconfigured
Errors were encountered while processing:
 linux-image-3.2.0-31-generic-pae
 linux-image-generic-pae
 linux-image
 linux
 linux-image-3.2.0-31-generic
 grub-pc
 linux-image-generic
 linux-generic
 linux-generic-pae
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

furthermore, i have tried to find the solution on all of theese forum posts: 
[http://ubuntuforums.org/showthread.php?t=2058967](http://ubuntuforums.org/showthread.php?t=2058967)
[http://ubuntuforums.org/showthread.php?t=1735575&page=2](http://ubuntuforums.org/showthread.php?t=1735575&page=2)
[http://askubuntu.com/questions/195950/package-system-broken-e-sub-process-usr-bin-dpkg-returned-an-error-code-1](http://askubuntu.com/questions/195950/package-system-broken-e-sub-process-usr-bin-dpkg-returned-an-error-code-1)

none of theese solutions worked, and i'm out of ideas. help would be appreciated.

---

### Post by BicyclerBoy on 2012-10-05
My guess is a grub install/update problem..
Maybe you missed an earlier grub update..

Did you upgrade from 10.04 LTS ?
If so was that install completely up-to-date ? (10.04.3LTS) ?

Debug info (no action) run:
dpkg-query -l grub*

---

### Post by jerrrys on 2012-10-05
try

sudo apt-get dist-upgrade

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

