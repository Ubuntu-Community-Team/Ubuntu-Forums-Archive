---
title: "Kernal wont update"
date: 2011-03-09
forum: Installation &amp; Upgrades
---

### Post by ve3tru on 2011-03-09
Cant update anything till I fix this kernal  linux-image-2.6.32-24-generic package
I need help 



peter@peter-laptop:~$ sudo apt-get install linux-image-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-generic linux-image-2.6.35-28-generic
Suggested packages:
  fdutils linux-doc-2.6.35 linux-source-2.6.35 linux-tools
The following packages will be REMOVED:
  linux-image-2.6.32-24-generic linux-image-2.6.35-19-generic
  linux-image-2.6.35-20-generic linux-image-2.6.35-21-generic
The following NEW packages will be installed:
  linux-image-2.6.35-28-generic
The following packages will be upgraded:
  linux-generic linux-image-generic
2 upgraded, 1 newly installed, 4 to remove and 98 not upgraded.
12 not fully installed or removed.
Need to get 0B/34.2MB of archives.
After this operation, 405MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 200729 files and directories currently installed.)
Removing linux-image-2.6.32-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-19-generic /boot/vmlinuz-2.6.35-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-19-generic /boot/vmlinuz-2.6.35-19-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-19-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-20-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-20-generic /boot/vmlinuz-2.6.35-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-20-generic /boot/vmlinuz-2.6.35-20-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-20-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-20-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-21-generic /boot/vmlinuz-2.6.35-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-21-generic /boot/vmlinuz-2.6.35-21-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-21-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-21-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 linux-image-2.6.35-19-generic
 linux-image-2.6.35-20-generic
 linux-image-2.6.35-21-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@peter-laptop:~$

---

### Post by zvacet on 2011-03-11
```
sudo dpkg --configure -a
```

---

### Post by ve3tru on 2011-03-11
Sorry no go I get, dkms: WARNING: linux headers are missing, which may explain the above failures. please install the linux-headers-2.6.35-25-generic package to fix this. That wont install either.
Tnx

peter@peter-laptop:~$ sudo apt-get install linux-headers-2.6.35-25-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-headers-2.6.35-25
The following packages will be REMOVED:
  linux-image-2.6.32-24-generic linux-image-2.6.35-19-generic
  linux-image-2.6.35-20-generic linux-image-2.6.35-21-generic
The following NEW packages will be installed:
  linux-headers-2.6.35-25 linux-headers-2.6.35-25-generic
0 upgraded, 2 newly installed, 4 to remove and 102 not upgraded.
12 not fully installed or removed.
Need to get 11.1MB of archives.
After this operation, 454MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-headers-2.6.35-25 all 2.6.35-25.44 [10.3MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main linux-headers-2.6.35-25-generic amd64 2.6.35-25.44 [807kB]
Fetched 11.1MB in 9min 12s (20.1kB/s)                                          
(Reading database ... 200729 files and directories currently installed.)
Removing linux-image-2.6.32-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.32-24-generic /boot/vmlinuz-2.6.32-24-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.32-24-generic.postrm line 321.
dpkg: error processing linux-image-2.6.32-24-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-19-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-19-generic /boot/vmlinuz-2.6.35-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-19-generic /boot/vmlinuz-2.6.35-19-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-19-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-19-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-20-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-20-generic /boot/vmlinuz-2.6.35-20-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-20-generic /boot/vmlinuz-2.6.35-20-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-20-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-20-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-2.6.35-21-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-21-generic /boot/vmlinuz-2.6.35-21-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-21-generic /boot/vmlinuz-2.6.35-21-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-2.6.35-21-generic.postrm line 328.
dpkg: error processing linux-image-2.6.35-21-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-2.6.32-24-generic
 linux-image-2.6.35-19-generic
 linux-image-2.6.35-20-generic
 linux-image-2.6.35-21-generic
localepurge: Disk space freed in /usr/share/locale: 0 KiB
localepurge: Disk space freed in /usr/share/man: 0 KiB
localepurge: Disk space freed in /usr/share/gnome/help: 0 KiB
localepurge: Disk space freed in /usr/share/omf: 0 KiB
localepurge: Disk space freed in /usr/share/doc/kde/HTML: 0 KiB

Total disk space freed by localepurge: 0 KiB

E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@peter-laptop:~$

---

### Post by ve3tru on 2011-03-11
Is it because I'm running Ubuntu 11.04, I'm not sure but I think its not even supposed to be released till next month. It's been running so great I forgot its still a baby.

---

### Post by zvacet on 2011-03-12
```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
sudo dpkg --configure -a
```

---

### Post by ve3tru on 2011-03-12
Thanks but I still getting the same errors
like

linux-image-generic depends on linux-image-2.6.35-26-generic; however:
  Package linux-image-2.6.35-26-generic is not configured yet.
or

Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-26-generic; however:
  Package linux-image-2.6.35-26-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.26.33); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.35-23-generic
 linux-image-2.6.35-22-generic
 linux-image-2.6.35-26-generic
 grub-pc
 linux-image-2.6.35-24-generic
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
peter@peter-laptop:~$ 

The frustrating part, is I cant update anything until this all gets fixed.
thnx

---

### Post by zvacet on 2011-03-12
```
sudo dpkg --configure  linux-image-2.6.35-25-generic && sudo apt-get install linux-image-generic
```

---

### Post by ve3tru on 2011-03-12
Nice try but no.

peter@peter-laptop:~$ sudo dpkg --configure  linux-image-2.6.35-25-generic && sudo apt-get install linux-image-generic
[sudo] password for peter: 
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       virtualbox-ose (3.2.8)...                                       [ OK ] 
 *       dahdi (2.2.1+dfsg-1ubuntu3)...                                  [ OK ] 
dkms: WARNING: linux headers are missing, which may explain the above failures.
      please install the linux-headers-2.6.35-25-generic package to fix this.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
/etc/default/grub: 9: quiet: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.35-25-generic
peter@peter-laptop:~$ 


P.S.
Thanks 4 the help
Peter

---

