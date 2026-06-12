---
title: "Package operation failed"
date: 2012-08-20
forum: Installation &amp; Upgrades
---

### Post by krkonnet on 2012-08-20
Hello,

Auto package upgrade gave following error:

```
installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Setting up initramfs-tools (0.99ubuntu13) ... 
update-initramfs: deferring update (trigger activated) 
Setting up linux-image-3.2.0-24-generic (3.2.0-24.39) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
dkms: WARNING: Linux headers are missing, which may explain the above failures. 
      please install the linux-headers-3.2.0-24-generic package to fix this. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-25-generic (3.2.0-25.40) ...No apport report written because MaxReports is reached already
 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-25-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-25-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-26-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Setting up linux-image-3.2.0-27-generic (3.2.0-27.43) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-27-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-27-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ... 
No apport report written because MaxReports is reached already
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-29-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.2.0-24-generic; however: 
  Package linux-image-3.2.0-24-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 3.2.0.24.26); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Processing triggers for initramfs-tools ... 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1 
dpkg: error processing initramfs-tools (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 linux-image-3.2.0-24-generic 
 linux-image-3.2.0-25-generic 
 linux-image-3.2.0-26-generic 
 linux-image-3.2.0-27-generic 
 linux-image-3.2.0-29-generic 
 linux-image-generic 
 linux-generic 
 initramfs-tools 
Error in function:  
Setting up initramfs-tools (0.99ubuntu13) ... 
update-initramfs: deferring update (trigger activated) 
Setting up linux-image-3.2.0-29-generic (3.2.0-29.46) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-29-generic /boot/vmlinuz-3.2.0-29-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-29-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-29-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-24-generic (3.2.0-24.39) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
dkms: WARNING: Linux headers are missing, which may explain the above failures. 
      please install the linux-headers-3.2.0-24-generic package to fix this. 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-24-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-24-generic /boot/vmlinuz-3.2.0-24-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-24-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-24-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-25-generic (3.2.0-25.40) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-25-generic /boot/vmlinuz-3.2.0-25-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-25-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-25-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Setting up linux-image-3.2.0-26-generic (3.2.0-26.41) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-26-generic /boot/vmlinuz-3.2.0-26-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-26-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-26-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
dpkg: dependency problems prevent configuration of linux-image-generic: 
 linux-image-generic depends on linux-image-3.2.0-24-generic; however: 
  Package linux-image-3.2.0-24-generic is not configured yet. 
dpkg: error processing linux-image-generic (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of linux-generic: 
 linux-generic depends on linux-image-generic (= 3.2.0.24.26); however: 
  Package linux-image-generic is not configured yet. 
dpkg: error processing linux-generic (--configure): 
 dependency problems - leaving unconfigured 
Setting up linux-image-3.2.0-27-generic (3.2.0-27.43) ... 
Running depmod. 
update-initramfs: deferring update (hook will be called later) 
Examining /etc/kernel/postinst.d. 
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
update-initramfs: Generating /boot/initrd.img-3.2.0-27-generic 
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
run-parts: executing /etc/kernel/postinst.d/zz-runlilo 3.2.0-27-generic /boot/vmlinuz-3.2.0-27-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/kernel/postinst.d/zz-runlilo exited with return code 1 
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-3.2.0-27-generic.postinst line 1010. 
dpkg: error processing linux-image-3.2.0-27-generic (--configure): 
 subprocess installed post-installation script returned error exit status 2 
Processing triggers for initramfs-tools ... 
update-initramfs: Generating /boot/initrd.img-3.2.0-29-generic 
Added Linux  + 
Added Linux_Old  + 
Fatal: Default image doesn't exist. 
run-parts: /etc/initramfs/post-update.d//runlilo exited with return code 1 
dpkg: error processing initramfs-tools (--configure): 
 subprocess installed post-installation script returned error exit status 1 
```


Can somebody help me to rectify this problem?

I have tried following bit did not work:

sudo apt-get autoclean
sudo apt-get clean
sudo rm -r /var/log/apt/lists/*
sudo apt-get uggrade

Thank you.


Kishore

---

### Post by wojox on 2012-08-20
[Remove lilo]("http://askubuntu.com/a/130292/2973")

---

