---
title: "Updating Kernel Config Error"
date: 2011-01-31
forum: Installation &amp; Upgrades
---

### Post by Peter7K on 2011-01-31
Hi, I've been trying to upgrade my kernel with the kxstudio ppa (need realtime for audio), and I keep getting the following message:

```
E: linux-image-2.6.35-25-generic: subprocess installed post-installation script returned error exit status 2
E: linux-image-generic: dependency problems - leaving unconfigured
E: linux-generic: dependency problems - leaving unconfigured
E: linux-image-2.6.31-12-realtime: subprocess installed post-installation script returned error exit status 2

```

What to do?  Thanks.

---

### Post by zvacet on 2011-02-01
```
sudo apt-get -f install
```

---

### Post by Peter7K on 2011-02-03
```
sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up linux-image-2.6.31-12-realtime (2.6.31-12.21+all1~maverick1) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-12-realtime
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
 * dkms: running auto installation service for kernel 2.6.31-12-realtime        
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-12-realtime.postinst line 1002.
dpkg: error processing linux-image-2.6.31-12-realtime (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-2.6.31-12-realtime
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
peter@peter-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libreoffice-filter-binfilter samplerate-programs jackd1-firewire
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.31-12-realtime (2.6.31-12.21+all1~maverick1) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-12-realtime
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
 * dkms: running auto installation service for kernel 2.6.31-12-realtime        
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-12-realtime.postinst line 1002.
dpkg: error processing linux-image-2.6.31-12-realtime (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Errors were encountered while processing:
 linux-image-2.6.31-12-realtime
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

It appeared the hdjmod had been giving an error earlier when it was trying to configure the kernel, so I uninstalled the package (it was a driver for my Hercules DJ controller).  It uninstalled, however with errors.  Now what I pasted above occurs.

---

### Post by zvacet on 2011-02-03
```
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by Peter7K on 2011-02-03
```
$ sudo dpkg --configure -a
[sudo] password for peter: 
Setting up linux-image-2.6.31-12-realtime (2.6.31-12.21+all1~maverick1) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-12-realtime
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
 * dkms: running auto installation service for kernel 2.6.31-12-realtime        
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-12-realtime.postinst line 1002.
dpkg: error processing linux-image-2.6.31-12-realtime (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-12-realtime
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic

```

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libreoffice-filter-binfilter samplerate-programs jackd1-firewire
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-image-2.6.31-12-realtime (2.6.31-12.21+all1~maverick1) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-12-realtime
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
 * dkms: running auto installation service for kernel 2.6.31-12-realtime        
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-12-realtime.postinst line 1002.
dpkg: error processing linux-image-2.6.31-12-realtime (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-image-2.6.31-12-realtime
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Same error!

---

### Post by fortguy on 2011-02-04
First, make sure that you are not currently running either of the versions causing the problem. In a terminal, type:

```
uname -r
```

If you are currently running the a problem version, reboot and pick a safe version from grub before proceeding. Otherwise, open Nautilus and go to the following directory:

```
/var/lib/dpkg/info
```

Find all files that begin with linux-image-2.6.35-25-generic. There should be maybe six in all ending with .list, .md5sums, .postinst, .postrm, .preinst, and .prerm and removed them.

```
cd /var/lib/dpkg/info
sudo rm linux-image-2.6.35-25-generic.list
```

Repeat the process for each file. Then completely remove the package:

```
sudo apt-get remove --purge linux-image-2.6.35-25-generic
sudo apt-get clean
sudo apt-get update
```

Then reinstall:

```
sudo apt-get install linux-image-2.6.35-25-generic
```

Then repeat the process for linux-image-2.6.31-12-realtime

---

### Post by Peter7K on 2011-02-10
Not sure why, but when I try to do as you have said, it merely says "Abort" after I confirm that I wish to continue:

```
peter@peter-laptop:/var/lib/dpkg/info$ sudo apt-get remove --purge linux-image-2.6.35-25-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-generic* linux-image-2.6.35-25-generic* linux-image-generic*
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
4 not fully installed or removed.
After this operation, 107MB disk space will be freed.
Do you want to continue [Y/n]? Y
Abort.
peter@peter-laptop:/var/lib/dpkg/info$ uname -r
2.6.35-23-generic
peter@peter-laptop:/var/lib/dpkg/info$ 

```

---

### Post by dino99 on 2011-02-10
check your repo list, use only genuine and trusted ubuntu repo. Be sure that dkms is installed. 
Then clean the sources:

sudo rm /var/cache/apt/archives/*

then update, upgrade

---

### Post by Peter7K on 2011-02-10
I have removed the culprit ppa (Abogani's realtime kernels), however, when I try to remove the /var/cache/apt/archives/* it says it cannot remove it due to it being a directory.  The only thing inside was a folder named partial which was empty (I removed it anyway).

It still seems to be that there are the 4 packages that were downloaded before the ppa was removed (and it wants to install them):

```
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  docky docky-dbg
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 934kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main docky all 2.1.0~bzr1780-0ubuntu1~10.10~dockycore1 [777kB]
Get:2 http://ppa.launchpad.net/docky-core/ppa/ubuntu/ maverick/main docky-dbg all 2.1.0~bzr1780-0ubuntu1~10.10~dockycore1 [157kB]
Fetched 934kB in 1s (613kB/s)    
(Reading database ... 
dpkg: warning: files list file for package `linux-image-2.6.35-25-generic' missing, assuming package has no files currently installed.
(Reading database ... 331807 files and directories currently installed.)
Preparing to replace docky 2.1.0~bzr1775-0ubuntu1~10.10~dockycore1 (using .../docky_2.1.0~bzr1780-0ubuntu1~10.10~dockycore1_all.deb) ...
Unpacking replacement docky ...
Replaced by files in installed package stacks ...
Preparing to replace docky-dbg 2.1.0~bzr1775-0ubuntu1~10.10~dockycore1 (using .../docky-dbg_2.1.0~bzr1780-0ubuntu1~10.10~dockycore1_all.deb) ...
Unpacking replacement docky-dbg ...
Processing triggers for man-db ...
Processing triggers for gconf2 ...
Processing triggers for hicolor-icon-theme ...
gtk-update-icon-cache: The generated cache was invalid.
WARNING: icon cache generation failed
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for desktop-file-utils ...
Processing triggers for python-support ...
Setting up linux-image-2.6.31-12-realtime (2.6.31-12.21+all1~maverick1) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.31-12-realtime
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
 * dkms: running auto installation service for kernel 2.6.31-12-realtime        
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.31-12-realtime /boot/vmlinuz-2.6.31-12-realtime
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.31-12-realtime.postinst line 1002.
dpkg: error processing linux-image-2.6.31-12-realtime (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-2.6.35-25-generic (2.6.35-25.44) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-25-generic
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
 * dkms: running auto installation service for kernel 2.6.35-25-generic         
 *       bcmwl (5.60.48.36+bdcom)...                                     [ OK ] 
 *       nvidia-current (260.19.06)...                                   [ OK ] 
 *       vhba (20100822)...                                              [ OK ] 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: executing /etc/kernel/postinst.d/update-nvidia 2.6.35-25-generic /boot/vmlinuz-2.6.35-25-generic
run-parts: failed to exec /etc/kernel/postinst.d/update-nvidia: No such file or directory
run-parts: /etc/kernel/postinst.d/update-nvidia exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-25-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-25-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-2.6.35-25-generic; however:
  Package linux-image-2.6.35-25-generic is not configured yet.
dpkg: error processing linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 2.6.35.25.32); however:
  Package linux-image-generic is not configured yet.
dpkg: error processing linux-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because MaxReports is reached already
        Setting up docky (2.1.0~bzr1780-0ubuntu1~10.10~dockycore1) ...
Setting up docky-dbg (2.1.0~bzr1780-0ubuntu1~10.10~dockycore1) ...
Errors were encountered while processing:
 linux-image-2.6.31-12-realtime
 linux-image-2.6.35-25-generic
 linux-image-generic
 linux-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

