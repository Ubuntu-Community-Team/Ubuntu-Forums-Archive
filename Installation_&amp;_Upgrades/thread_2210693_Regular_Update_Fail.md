---
title: "Regular Update Fail"
date: 2014-03-12
forum: Installation &amp; Upgrades
---

### Post by NYxkCsy on 2014-03-12
Was doing my weekly update, largely an update to the kernel but it seems to have hung up telling me that the installation or remeval of a software package has failed. Posting the log to see if there are any ideas out there.

```
"installArchives() failed: Setting up linux-image-3.2.0-60-generic-pae (3.2.0-60.91) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-60-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-60-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-59-generic-pae (3.2.0-59.90) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-59-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-59-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up extlinux (2:4.05+dfsg-2) ... 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
dpkg: error processing extlinux (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-image-generic-pae: 
 linux-image-generic-pae depends on linux-image-3.2.0-59-generic-pae; however: 
  Package linux-image-3.2.0-59-generic-pae is not configured yet. 
dpkg: error processing linux-image-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image: 
 linux-image depends on linux-image-generic-pae (= 3.2.0.59.70); however: 
  Package linux-image-generic-pae is not configured yet. 
dpkg: error processing linux-image (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux: 
 linux depends on linux-image (= 3.2.0.59.70); however: 
  Package linux-image is not configured yet. 
dpkg: error processing linux (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 linux-image-3.2.0-60-generic-pae 
 linux-image-3.2.0-59-generic-pae 
 extlinux 
 linux-image-generic-pae 
 linux-image 
 linux 
Error in function:  
Setting up extlinux (2:4.05+dfsg-2) ... 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
dpkg: error processing extlinux (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up linux-image-3.2.0-60-generic-pae (3.2.0-60.91) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-60-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-60-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-59-generic-pae (3.2.0-59.90) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-59-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-59-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic-pae: 
 linux-image-generic-pae depends on linux-image-3.2.0-59-generic-pae; however: 
  Package linux-image-3.2.0-59-generic-pae is not configured yet. 
dpkg: error processing linux-image-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image: 
 linux-image depends on linux-image-generic-pae (= 3.2.0.59.70); however: 
  Package linux-image-generic-pae is not configured yet. 
dpkg: error processing linux-image (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux: 
 linux depends on linux-image (= 3.2.0.59.70); however: 
  Package linux-image is not configured yet. 
dpkg: error processing linux (--configure): 
 dependency problems - leaving unconfigured 

installArchives() failed: Setting up linux-image-3.2.0-60-generic-pae (3.2.0-60.91) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-60-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-60-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-59-generic-pae (3.2.0-59.90) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-59-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-59-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up extlinux (2:4.05+dfsg-2) ... 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
dpkg: error processing extlinux (--configure): 
 subprocess installed post-installation script returned error exit status 1 
dpkg: dependency problems prevent configuration of linux-image-generic-pae: 
 linux-image-generic-pae depends on linux-image-3.2.0-59-generic-pae; however: 
  Package linux-image-3.2.0-59-generic-pae is not configured yet. 
dpkg: error processing linux-image-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image: 
 linux-image depends on linux-image-generic-pae (= 3.2.0.59.70); however: 
  Package linux-image-generic-pae is not configured yet. 
dpkg: error processing linux-image (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux: 
 linux depends on linux-image (= 3.2.0.59.70); however: 
  Package linux-image is not configured yet. 
dpkg: error processing linux (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 linux-image-3.2.0-60-generic-pae 
 linux-image-3.2.0-59-generic-pae 
 extlinux 
 linux-image-generic-pae 
 linux-image 
 linux 
Error in function:  
Setting up extlinux (2:4.05+dfsg-2) ... 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
dpkg: error processing extlinux (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Setting up linux-image-3.2.0-60-generic-pae (3.2.0-60.91) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-60-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-60-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-59-generic-pae (3.2.0-59.90) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
update-initramfs: Generating /boot/initrd.img-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae 
P: Checking for EXTLINUX directory... found. 
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae... 
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae... 
P: Installing debian theme...cp: cannot stat `/usr/share/syslinux/themes/debian-squeeze/extlinux/memtest.bin': No such file or directory 
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-59-generic-pae.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-59-generic-pae (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic-pae: 
 linux-image-generic-pae depends on linux-image-3.2.0-59-generic-pae; however: 
  Package linux-image-3.2.0-59-generic-pae is not configured yet. 
dpkg: error processing linux-image-generic-pae (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-image: 
 linux-image depends on linux-image-generic-pae (= 3.2.0.59.70); however: 
  Package linux-image-generic-pae is not configured yet. 
dpkg: error processing linux-image (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux: 
 linux depends on linux-image (= 3.2.0.59.70); however: 
  Package linux-image is not configured yet. 
dpkg: error processing linux (--configure): 
 dependency problems - leaving unconfigured"
```

---

### Post by ibjsb4 on 2014-03-12
Please edit your post and use code tags or this thread will end up a mile long :)

[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168)

Lets have a look at your kernels from terminal:
```
ls /boot
```

[https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal](https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal)

---

### Post by ian-weisser on 2014-03-12
Your weekly update hasn't been working for a *long* time.
You seem to have the package *syslinux-themes-debian-squeeze* installed. Why? It's not compatible with Ubuntu. Uninstall it.

---

### Post by NYxkCsy on 2014-03-13
ls /boot returns
```

"abi-3.2.0-57-generic-pae         initrd.img-3.2.0-59-generic-pae
abi-3.2.0-58-generic-pae         initrd.img-3.2.0-60-generic-pae
abi-3.2.0-59-generic-pae         lost+found
abi-3.2.0-60-generic-pae         System.map-3.2.0-57-generic-pae
config-3.2.0-57-generic-pae      System.map-3.2.0-58-generic-pae
config-3.2.0-58-generic-pae      System.map-3.2.0-59-generic-pae
config-3.2.0-59-generic-pae      System.map-3.2.0-60-generic-pae
config-3.2.0-60-generic-pae      vmlinuz-3.2.0-57-generic-pae
extlinux                         vmlinuz-3.2.0-58-generic-pae
grub                             vmlinuz-3.2.0-59-generic-pae
initrd.img-3.2.0-57-generic-pae  vmlinuz-3.2.0-60-generic-pae
initrd.img-3.2.0-58-generic-pae"

```

---

### Post by chkneater on 2014-03-13
Have you tried:

dpkg--configure or dpkg--reconfigure 

 I noticed a lot errors were dpkg errors.  Maybe look in that direction?....

---

### Post by ibjsb4 on 2014-03-13
> **ian-weisser said:**
> Your weekly update hasn't been working for a *long* time.
You seem to have the package *syslinux-themes-debian-squeeze* installed. Why? It's not compatible with Ubuntu. Uninstall it.

> **chkneater said:**
> Have you tried:

dpkg--configure or dpkg--reconfigure 

 I noticed a lot errors were dpkg errors.  Maybe look in that direction?....

Yes and yes :)

You need to remove that debian-suqeeze theme.  Open software sources>Other Software and just uncheck it.

[https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu#Removing_.26_Disabling_Repositories)

Then open a terminal and enter:

```
sudo dpkg --configure -a

```
Then update

```
sudo apt-get update

```
And post back.

---

### Post by NYxkCsy on 2014-03-14
Did the configure aand the update and got the following

```

:~$ sudo dpkg --configure -a
Setting up extlinux (2:4.05+dfsg-2) ...
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae...
E: /usr/share/syslinux/themes/debian/extlinux: No such file or directory
dpkg: error processing extlinux (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up linux-image-3.2.0-60-generic-pae (3.2.0-60.91) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-60-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-60-generic-pae /boot/vmlinuz-3.2.0-60-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae...
E: /usr/share/syslinux/themes/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-60-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-60-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up linux-image-3.2.0-59-generic-pae (3.2.0-59.90) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
update-initramfs: Generating /boot/initrd.img-3.2.0-59-generic-pae
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
run-parts: executing /etc/kernel/postinst.d/zz-extlinux 3.2.0-59-generic-pae /boot/vmlinuz-3.2.0-59-generic-pae
P: Checking for EXTLINUX directory... found.
P: Writing config for /boot/vmlinuz-3.2.0-60-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-59-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-58-generic-pae...
P: Writing config for /boot/vmlinuz-3.2.0-57-generic-pae...
E: /usr/share/syslinux/themes/debian/extlinux: No such file or directory
run-parts: /etc/kernel/postinst.d/zz-extlinux exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-59-generic-pae.postinst line 1010.
dpkg: error processing linux-image-3.2.0-59-generic-pae (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic-pae:
 linux-image-generic-pae depends on linux-image-3.2.0-59-generic-pae; however:
  Package linux-image-3.2.0-59-generic-pae is not configured yet.
dpkg: error processing linux-image-generic-pae (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image:
 linux-image depends on linux-image-generic-pae (= 3.2.0.59.70); however:
  Package linux-image-generic-pae is not configured yet.
dpkg: error processing linux-image (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux:
 linux depends on linux-image (= 3.2.0.59.70); however:
  Package linux-image is not configured yet.
dpkg: error processing linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 extlinux
 linux-image-3.2.0-60-generic-pae
 linux-image-3.2.0-59-generic-pae
 linux-image-generic-pae
 linux-image
 linux
:~$ sudo apt-get update
Get:1 http://dl.google.com stable Release.gpg [198 B]
Hit http://dl.google.com stable Release.gpg                                    
Hit http://archive.ubuntu.com precise Release.gpg                              
Get:2 http://archive.ubuntu.com precise-updates Release.gpg [198 B]            
Hit http://archive.ubuntu.com precise-backports Release.gpg                    
Get:3 http://archive.ubuntu.com precise-security Release.gpg [198 B]           
Get:4 http://dl.google.com stable Release [1,351 B]                            
Hit http://archive.ubuntu.com precise Release                                  
Get:5 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Get:6 http://archive.canonical.com precise Release.gpg [198 B]                 
Get:7 http://extras.ubuntu.com precise Release.gpg [72 B]                      
Get:8 http://linux.dropbox.com precise Release.gpg [489 B]                     
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://ppa.launchpad.net precise Release.gpg                               
Hit http://dl.google.com stable Release                                        
Get:9 http://linux.dropbox.com precise Release [2,603 B]                       
Get:10 http://archive.canonical.com precise Release [7,078 B]                  
Hit http://extras.ubuntu.com precise Release                                   
Get:11 http://dl.google.com stable/main i386 Packages [1,252 B]                
Hit http://archive.ubuntu.com precise-backports Release                        
Get:12 http://archive.ubuntu.com precise-security Release [49.6 kB]            
Hit http://ppa.launchpad.net precise Release                                   
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://dl.google.com stable/main i386 Packages                             
Get:13 http://linux.dropbox.com precise/main i386 Packages [1,142 B]           
Hit http://archive.ubuntu.com precise/main Sources                             
Hit http://archive.ubuntu.com precise/restricted Sources                       
Hit http://archive.ubuntu.com precise/universe Sources                         
Hit http://archive.ubuntu.com precise/multiverse Sources                       
Ign http://dl.google.com stable/main TranslationIndex                          
Hit http://archive.ubuntu.com precise/main i386 Packages                       
Hit http://archive.ubuntu.com precise/restricted i386 Packages                 
Hit http://archive.ubuntu.com precise/universe i386 Packages                   
Hit http://archive.ubuntu.com precise/multiverse i386 Packages                 
Hit http://extras.ubuntu.com precise/main Sources                              
Hit http://ppa.launchpad.net precise Release                                   
Hit http://ppa.launchpad.net precise Release                                   
Hit http://archive.ubuntu.com precise/main TranslationIndex                    
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex              
Hit http://archive.ubuntu.com precise/restricted TranslationIndex              
Hit http://archive.ubuntu.com precise/universe TranslationIndex                
Get:14 http://archive.ubuntu.com precise-updates/main Sources [452 kB]         
Ign http://linux.dropbox.com precise/main TranslationIndex                     
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Get:15 http://archive.canonical.com precise/partner Sources [4,867 B]          
Hit http://ppa.launchpad.net precise Release                                   
Get:16 http://archive.canonical.com precise/partner i386 Packages [8,932 B]    
Ign http://archive.canonical.com precise/partner TranslationIndex              
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:17 http://archive.ubuntu.com precise-updates/restricted Sources [8,028 B]  
Get:18 http://archive.ubuntu.com precise-updates/universe Sources [105 kB]     
Hit http://ppa.launchpad.net precise/main Sources                              
Hit http://ppa.launchpad.net precise/main i386 Packages                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                     
Get:19 http://archive.ubuntu.com precise-updates/multiverse Sources [8,900 B]  
Get:20 http://archive.ubuntu.com precise-updates/main i386 Packages [782 kB]   
Ign http://dl.google.com stable/main Translation-en_CA                         
Ign http://dl.google.com stable/main Translation-en                            
Ign http://dl.google.com stable/main Translation-en_CA                         
Get:21 http://archive.ubuntu.com precise-updates/restricted i386 Packages [12.2 kB]
Get:22 http://archive.ubuntu.com precise-updates/universe i386 Packages [242 kB]
Ign http://dl.google.com stable/main Translation-en                            
Ign http://linux.dropbox.com precise/main Translation-en_CA                    
Get:23 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
Get:24 http://archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]
Get:25 http://archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]
Get:26 http://archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]
Get:27 http://archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]
Hit http://archive.ubuntu.com precise-backports/main Sources                   
Hit http://archive.ubuntu.com precise-backports/restricted Sources             
Hit http://archive.ubuntu.com precise-backports/universe Sources               
Hit http://archive.ubuntu.com precise-backports/multiverse Sources             
Ign http://linux.dropbox.com precise/main Translation-en                       
Hit http://archive.ubuntu.com precise-backports/main i386 Packages             
Hit http://archive.ubuntu.com precise-backports/restricted i386 Packages       
Hit http://archive.ubuntu.com precise-backports/universe i386 Packages         
Hit http://archive.ubuntu.com precise-backports/multiverse i386 Packages       
Hit http://archive.ubuntu.com precise-backports/main TranslationIndex          
Hit http://archive.ubuntu.com precise-backports/multiverse TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/restricted TranslationIndex    
Hit http://archive.ubuntu.com precise-backports/universe TranslationIndex      
Get:28 http://archive.ubuntu.com precise-security/main Sources [99.2 kB]       
Get:29 http://archive.ubuntu.com precise-security/restricted Sources [2,494 B] 
Get:30 http://archive.ubuntu.com precise-security/universe Sources [30.9 kB]   
Get:31 http://archive.ubuntu.com precise-security/multiverse Sources [1,789 B] 
Get:32 http://archive.ubuntu.com precise-security/main i386 Packages [396 kB]  
Ign http://archive.canonical.com precise/partner Translation-en_CA             
Ign http://archive.canonical.com precise/partner Translation-en                
Ign http://extras.ubuntu.com precise/main Translation-en_CA                    
Get:33 http://archive.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:34 http://archive.ubuntu.com precise-security/universe i386 Packages [96.1 kB]
Ign http://extras.ubuntu.com precise/main Translation-en                       
Get:35 http://archive.ubuntu.com precise-security/multiverse i386 Packages [2,646 B]
Get:36 http://archive.ubuntu.com precise-security/main TranslationIndex [74 B] 
Get:37 http://archive.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:38 http://archive.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:39 http://archive.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://archive.ubuntu.com precise/main Translation-en_CA            
Hit http://archive.ubuntu.com precise/main Translation-en
Hit http://archive.ubuntu.com precise/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted Translation-en         
Ign http://ppa.launchpad.net precise/main Translation-en_CA             
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_CA
Ign http://ppa.launchpad.net precise/main Translation-en
Ign http://ppa.launchpad.net precise/main Translation-en_CA
Hit http://archive.ubuntu.com precise/universe Translation-en_CA
Hit http://archive.ubuntu.com precise/universe Translation-en
Hit http://archive.ubuntu.com precise-updates/main Translation-en_CA    
Get:40 http://archive.ubuntu.com precise-updates/main Translation-en [339 kB]
Ign http://ppa.launchpad.net precise/main Translation-en                       
Ign http://ppa.launchpad.net precise/main Translation-en_CA                    
Ign http://ppa.launchpad.net precise/main Translation-en          
Get:41 http://archive.ubuntu.com precise-updates/multiverse Translation-en [9,010 B]
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://archive.ubuntu.com precise-updates/universe Translation-en_CA
Get:42 http://archive.ubuntu.com precise-updates/universe Translation-en [138 kB]
Hit http://archive.ubuntu.com precise-backports/main Translation-en
Hit http://archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://archive.ubuntu.com precise-backports/universe Translation-en
Get:43 http://archive.ubuntu.com precise-security/main Translation-en [173 kB]
Hit http://archive.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise-security/restricted Translation-en
Get:44 http://archive.ubuntu.com precise-security/universe Translation-en [56.6 kB]
Fetched 3,115 kB in 4s (777 kB/s)                                     
Reading package lists... Done

```

---

