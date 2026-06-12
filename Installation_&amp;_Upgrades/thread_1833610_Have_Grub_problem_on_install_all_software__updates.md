---
title: "Have Grub problem on install all software / updates"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by kelmark2180 on 2011-08-26
Anything I update or install has a grub error. This is 10.10 Maverick and I really don't know where to go to fix. This example is one of many, since I receive the same errors on any updates.

Any help is appreciated.
Don

```
donald@donald-mitx:~$ uname -a
Linux donald-mitx 2.6.35-30-generic #56-Ubuntu SMP Mon Jul 11 20:00:22 UTC 2011 i686 GNU/Linux
donald@donald-mitx:~$ sudo apt-get check
[sudo] password for donald: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
donald@donald-mitx:~$ sudo apt-get clean
donald@donald-mitx:~$ grub-install -v
grub-install (GRUB) 1.98+20100804-5ubuntu3.3
donald@donald-mitx:~$ 

```
Errors:
```

installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
(Reading database ... 
(Reading database ... 5%
(Reading database ... 100%
(Reading database ... 228941 files and directories currently installed.)
Preparing to replace flashplugin-installer 10.3.183.4ubuntu0.10.10.1 (using .../flashplugin-installer_10.3.183.7ubuntu0.10.10.1_i386.deb) ...
Unpacking replacement flashplugin-installer ...
Setting up linux-image-2.6.35-30-generic (2.6.35-30.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-30-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-30.54 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-30.54 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
**/usr/sbin/grub-probe: error: /boot/grub/device.map:2: No open parenthesis found.**
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-30-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up flashplugin-installer (10.3.183.7ubuntu0.10.10.1) ...
Downloading...
--2011-08-26 07:33:06--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.3.183.7.orig.tar.gz
Resolving archive.canonical.com... 91.189.88.33
Connecting to archive.canonical.com|91.189.88.33|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 5433328 (5.2M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.3.183.7.orig.tar.gz'

  5300K .....                                                 100%  201K=34s

2011-08-26 07:33:41 (156 KB/s) - `./adobe-flashplugin_10.3.183.7.orig.tar.gz' saved [5433328/5433328]

Download done.
Flash Plugin installed.
Errors were encountered while processing:
 linux-image-2.6.35-30-generic
Setting up linux-image-2.6.35-30-generic (2.6.35-30.56) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.35-30-generic
Not updating initrd symbolic links since we are being updated/reinstalled 
(2.6.35-30.54 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(2.6.35-30.54 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/nvidia-common 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 2.6.35-30-generic /boot/vmlinuz-2.6.35-30-generic
/usr/sbin/grub-probe: error: /boot/grub/device.map:2: No open parenthesis found.
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-2.6.35-30-generic.postinst line 1010.
dpkg: error processing linux-image-2.6.35-30-generic (--configure):
 subprocess installed post-installation script returned error exit status 2


```

---

### Post by dino99 on 2011-08-26
open synaptic to remove/purge then reinstall grub-pc

---

### Post by kelmark2180 on 2011-08-26
Wow, Thanks for the solution to my problems!

Thanks, So very Much;
Don

---

### Post by egrpioneer on 2011-08-27
> **dino99 said:**
> open synaptic to remove/purge then reinstall grub-pc

Sir, I have same issue, and research led me to your solution. Before I remove & reinstall grub-pc, please answer the following question: I have 2, hdds running Windows 7 Pro., and 10.10. Grub works great! Will the "solution" create issues?

Thank you in advance!!

---

### Post by kelmark2180 on 2011-08-28
I'm not clear on your question.  If grub gives you no errors and works great, why mess with it?  

I had grub errors when applying updates or new installs and completely removing grub-pc using Synaptic Package Manager then installing it again fixed my problems. This fix suggested by dino99 worked for Me. Whether this solution will work for you is undefined.  You should have backups and recovery of all systems before you try-dis and try-dat. 
Don

---

