---
title: "linux-image-3.19.0-51-generic Upgrade Attempt Yields Dependency Issues, &quot;Half-Install"
date: 2016-02-22
forum: Installation &amp; Upgrades
---

### Post by ectomonomorphosis on 2016-02-22
apt-get update is normal:

```
spyro@Blubot:~$ sudo apt-get update
Ign http://us.archive.ubuntu.com trusty InRelease
Get:1 http://us.archive.ubuntu.com trusty-updates InRelease [65.9 kB]        
Ign http://archive.canonical.com trusty InRelease                              
Hit http://security.ubuntu.com trusty-security InRelease                       
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Hit http://security.ubuntu.com trusty-security/main Sources           
Get:2 http://us.archive.ubuntu.com trusty-updates/main Sources [260 kB]
Hit http://archive.canonical.com trusty Release                                
Hit http://security.ubuntu.com trusty-security/main amd64 Packages             
Hit http://archive.canonical.com trusty/partner Sources                        
Hit http://security.ubuntu.com trusty-security/main i386 Packages              
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Get:3 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [710 kB] 
Hit http://security.ubuntu.com trusty-security/main Translation-en             
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Get:4 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [688 kB]
Hit http://us.archive.ubuntu.com trusty-updates/main Translation-en
Hit http://us.archive.ubuntu.com trusty Release                            
Hit http://us.archive.ubuntu.com trusty/main Sources                        
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages         
Hit http://us.archive.ubuntu.com trusty/main i386 Packages          
Hit http://us.archive.ubuntu.com trusty/main Translation-en         
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US       
Fetched 1,723 kB in 2s (590 kB/s)             
Reading package lists... Done


```


Ran autoremove so I could update:

```
spyro@Blubot:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-generic-lts-vivid linux-image-3.19.0-25-lowlatency
  linux-image-3.19.0-49-generic linux-image-extra-3.19.0-49-generic
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 414 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 280236 files and directories currently installed.)
Removing linux-image-3.19.0-25-lowlatency (3.19.0-25.26~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-25-lowlatency /boot/vmlinuz-3.19.0-25-lowlatency
update-initramfs: Deleting /boot/initrd.img-3.19.0-25-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-25-lowlatency /boot/vmlinuz-3.19.0-25-lowlatency
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: GRUB_TIMEOUT-STYLE=menu: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-25-lowlatency.postrm line 328.
dpkg: error processing package linux-image-3.19.0-25-lowlatency (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-3.19.0-49-generic (3.19.0-49.55~14.04.1) ...
depmod: FATAL: could not load /boot/System.map-3.19.0-49-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-49-generic /boot/vmlinuz-3.19.0-49-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-49-generic /boot/vmlinuz-3.19.0-49-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-49-generic
grep: /boot/config-3.19.0-49-generic: No such file or directory
WARNING: missing /lib/modules/3.19.0-49-generic
Device driver support needs thus be built-in linux image!
depmod: ERROR: could not open directory /lib/modules/3.19.0-49-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_C8ddmX/lib/modules/3.19.0-49-generic/modules.order: No such file or directory
depmod: WARNING: could not open /tmp/mkinitramfs_C8ddmX/lib/modules/3.19.0-49-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-49-generic /boot/vmlinuz-3.19.0-49-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-49-generic /boot/vmlinuz-3.19.0-49-generic
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: GRUB_TIMEOUT-STYLE=menu: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-3.19.0-49-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-3.19.0-49-generic (3.19.0-49.55~14.04.1) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-49-generic /boot/vmlinuz-3.19.0-49-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-49-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-49-generic /boot/vmlinuz-3.19.0-49-generic
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: GRUB_TIMEOUT-STYLE=menu: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-3.19.0-49-generic.postrm line 328.
dpkg: error processing package linux-image-3.19.0-49-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-headers-generic-lts-vivid (3.19.0.51.36) ...
Errors were encountered while processing:
 linux-image-3.19.0-25-lowlatency
 linux-image-extra-3.19.0-49-generic
 linux-image-3.19.0-49-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

apt-get dist-upgrade yields:

```
spyro@Blubot:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
9 not fully installed or removed.
Need to get 110 MB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.19.0-25-lowlatency amd64 3.19.0-25.26~14.04.1 [55.0 MB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.19.0-49-generic amd64 3.19.0-49.55~14.04.1 [16.8 MB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.19.0-49-generic amd64 3.19.0-49.55~14.04.1 [38.3 MB]
Fetched 110 MB in 2min 6s (867 kB/s)                                           
dpkg: error processing package linux-image-3.19.0-25-lowlatency (--configure):
 package linux-image-3.19.0-25-lowlatency is not ready for configuration
 cannot configure (current status `half-installed')
dpkg: error processing package linux-image-3.19.0-49-generic (--configure):
 package linux-image-3.19.0-49-generic is not ready for configuration
 cannot configure (current status `half-installed')
Setting up linux-image-3.19.0-51-generic (3.19.0-51.57~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: GRUB_TIMEOUT-STYLE=menu: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-51-generic.postinst line 1025.
dpkg: error processing package linux-image-3.19.0-51-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.19.0-51-lowlatency (3.19.0-51.57~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-51-lowlatency /boot/vmlinuz-3.19.0-51-lowlatency
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-51-lowlatency /boot/vmlinuz-3.19.0-51-lowlatency
update-initramfs: Generating /boot/initrd.img-3.19.0-51-lowlatency
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-51-lowlatency /boot/vmlinuz-3.19.0-51-lowlatency
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-51-lowlatency /boot/vmlinuz-3.19.0-51-lowlatency
/usr/sbin/grub-mkconfig: 10: /etc/default/grub: GRUB_TIMEOUT-STYLE=menu: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-51-lowlatency.postinst line 1025.
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No apport report written because MaxReports is reached already
                                                    dpkg: error processing package linux-image-3.19.0-51-lowlatency (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: error processing package linux-image-extra-3.19.0-49-generic (--configure):
 package linux-image-extra-3.19.0-49-generic is not ready for configuration
 cannot configure (current status `half-installed')
dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-51-generic:
 linux-image-extra-3.19.0-51-generic depends on linux-image-3.19.0-51-generic; however:
  Package linux-image-3.19.0-51-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.19.0-51-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-vivid:
 linux-image-generic-lts-vivid depends on linux-image-3.19.0-51-generic; however:
  Package linux-image-3.19.0-51-generic is not configured yet.
 linux-image-generic-lts-vivid depends on linux-image-extra-3.19.0-51-generic; however:
  Package linux-image-extra-3.19.0-51-generic is not configured yet.

dpkg: error processing package linux-image-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-lowlatency-lts-vivid:
 linux-image-lowlatency-lts-vivid depends on linux-image-3.19.0-51-lowlatency; however:
  Package linux-image-3.19.0-51-lowlatency is not configured yet.

dpkg: error processing package linux-image-lowlatency-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-lowlatency-lts-vivid:
 linux-lowlatency-lts-vivid depends on linux-image-lowlatency-lts-vivid (= 3.19.0.51.36); however:
  Package linux-image-lowlatency-lts-vivid is not configured yet.

dpkg: error processing package linux-lowlatency-lts-vivid (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.19.0-25-lowlatency
 linux-image-3.19.0-49-generic
 linux-image-3.19.0-51-generic
 linux-image-3.19.0-51-lowlatency
 linux-image-extra-3.19.0-49-generic
 linux-image-extra-3.19.0-51-generic
 linux-image-generic-lts-vivid
 linux-image-lowlatency-lts-vivid
 linux-lowlatency-lts-vivid
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

A list of my /boot/ directory:

```
spyro@Blubot:/boot$ ls
abi-3.19.0-49-lowlatency         memtest86+.bin
abi-3.19.0-51-generic            memtest86+.elf
abi-3.19.0-51-lowlatency         memtest86+_multiboot.bin
config-3.19.0-49-lowlatency      System.map-3.19.0-49-lowlatency
config-3.19.0-51-generic         System.map-3.19.0-51-generic
config-3.19.0-51-lowlatency      System.map-3.19.0-51-lowlatency
grub                             vmlinuz-3.19.0-49-lowlatency
initrd.img-3.19.0-51-generic     vmlinuz-3.19.0-51-generic
initrd.img-3.19.0-51-lowlatency  vmlinuz-3.19.0-51-lowlatency
lost+found


```

I should mention that my /boot/ directory has only 147.8 MB remaining, 76.7 MB used. I'm afraid to reboot now, expecting compounding issues, and so will monitor this thread for a serious, studied response as opposed "troubleshooting tips."

Here's the Support Status:

```
spyro@Blubot:~$ ubuntu-support-status
Support status summary of 'Blubot':


You have 2443 packages (100.0%) that can not/no-longer be downloaded
You have 0 packages (0.0%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details
spyro@Blubot:~$ cat /etc/dpkg/dpkg.cfg.d/multiarch
cat: /etc/dpkg/dpkg.cfg.d/multiarch: No such file or directory
spyro@Blubot:~$ dpkg --print-foreign-architectures
i386
spyro@Blubot:~$ sudo grep -R proxy /etc/apt/*
spyro@Blubot:~$ grep proxy  /etc/environment
spyro@Blubot:~$ echo $http_proxy

spyro@Blubot:~$ echo $ftp_proxy

spyro@Blubot:~$ grep proxy /etc/bash.bashrc
spyro@Blubot:~$ grep proxy ~/.bashrc
spyro@Blubot:~$ cat /etc/apt/apt.conf
cat: /etc/apt/apt.conf: No such file or directory
spyro@Blubot:~$ sudo fuser -vvv /var/lib/dpkg/lock
spyro@Blubot:~$ sudo fuser -vvv /var/cache/apt/archives/lock
spyro@Blubot:~$ cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04.4 LTS"
spyro@Blubot:~$ uname -a
Linux Blubot 3.19.0-49-lowlatency #55~14.04.1-Ubuntu SMP PREEMPT Fri Jan 22 13:21:43 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux
spyro@Blubot:~$ sudo rm /var/lib/apt/lists/lock 
rm: cannot remove '/var/lib/apt/lists/lock': No such file or directory
spyro@Blubot:~$ sudo rm  /var/cache/apt/archives/lock
spyro@Blubot:~$ sudo rm /var/lib/dpkg/lock
spyro@Blubot:~$ sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
spyro@Blubot:~$ sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
spyro@Blubot:~$ sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status  ||  sudo cp /var/backups/apt.extended_states.0 /var/lib/dpkg/status
spyro@Blubot:~$ sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-bad
spyro@Blubot:~$ sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
spyro@Blubot:~$ sudo rm -rf /var/lib/dpkg/updates/*
spyro@Blubot:~$ sudo rm -rf /var/lib/apt/lists
spyro@Blubot:~$ sudo rm /var/cache/apt/*.bin
spyro@Blubot:~$ sudo mkdir /var/lib/apt/lists
spyro@Blubot:~$ sudo mkdir /var/lib/apt/lists/partial
spyro@Blubot:~$ LANG=C;sudo apt-get clean
spyro@Blubot:~$ LANG=C;sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
spyro@Blubot:~$ sudo dpkg --configure -a
Setting up linux-image-3.19.0-51-generic (3.19.0-51.57~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-51-generic /boot/vmlinuz-3.19.0-51-generic
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: GRUB_TIMEOUT-STYLE=menu: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-51-generic.postinst line 1025.
dpkg: error processing package linux-image-3.19.0-51-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.19.0-51-lowlatency (3.19.0-51.57~14.04.1) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-51-lowlatency /boot/vmlinuz-3.19.0-51-lowlatency
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-51-lowlatency /boot/vmlinuz-3.19.0-51-lowlatency
update-initramfs: Generating /boot/initrd.img-3.19.0-51-lowlatency
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-51-lowlatency /boot/vmlinuz-3.19.0-51-lowlatency
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-51-lowlatency /boot/vmlinuz-3.19.0-51-lowlatency
/usr/sbin/grub-mkconfig: 9: /etc/default/grub: GRUB_TIMEOUT-STYLE=menu: not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.19.0-51-lowlatency.postinst line 1025.
dpkg: error processing package linux-image-3.19.0-51-lowlatency (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-lowlatency-lts-vivid:
 linux-image-lowlatency-lts-vivid depends on linux-image-3.19.0-51-lowlatency; however:
  Package linux-image-3.19.0-51-lowlatency is not configured yet.

dpkg: error processing package linux-image-lowlatency-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-generic-lts-vivid:
 linux-image-generic-lts-vivid depends on linux-image-3.19.0-51-generic; however:
  Package linux-image-3.19.0-51-generic is not configured yet.

dpkg: error processing package linux-image-generic-lts-vivid (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-3.19.0-51-generic:
 linux-image-extra-3.19.0-51-generic depends on linux-image-3.19.0-51-generic; however:
  Package linux-image-3.19.0-51-generic is not configured yet.

dpkg: error processing package linux-image-extra-3.19.0-51-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-lowlatency-lts-vivid:
 linux-lowlatency-lts-vivid depends on linux-image-lowlatency-lts-vivid (= 3.19.0.51.36); however:
  Package linux-image-lowlatency-lts-vivid is not configured yet.

dpkg: error processing package linux-lowlatency-lts-vivid (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-3.19.0-51-generic
 linux-image-3.19.0-51-lowlatency
 linux-image-lowlatency-lts-vivid
 linux-image-generic-lts-vivid
 linux-image-extra-3.19.0-51-generic
 linux-lowlatency-lts-vivid
spyro@Blubot:~$ sudo dpkg --clear-avail
spyro@Blubot:~$ LANG=C;sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.19.0-25-lowlatency linux-image-3.19.0-49-generic
  linux-image-extra-3.19.0-49-generic
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
9 not fully installed or removed.
After this operation, 414 MB disk space will be freed.
Do you want to continue? [Y/n] y
Abort.


```

---

### Post by ectomonomorphosis on 2016-02-25
I reinstalled.

---

