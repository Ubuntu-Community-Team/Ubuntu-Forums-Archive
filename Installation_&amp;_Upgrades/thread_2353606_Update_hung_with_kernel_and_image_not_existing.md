---
title: "Update hung with kernel and image not existing"
date: 2017-02-23
forum: Installation &amp; Upgrades
---

### Post by derekcentrico on 2017-02-23
Quite confused.  Any input on fixing this will be greatly appreciated.

```
cp: cannot stat '/usr/share/plymouth/ubuntu-logo.png': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-63-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-63-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-63-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                                                                                                            dpkg: error processing package linux-image-extra-4.4.0-63-generic (--configure):
 package linux-image-extra-4.4.0-63-generic is not ready for configuration
 cannot configure (current status 'half-installed')
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.8.0-39-generic
cp: cannot stat '/usr/share/plymouth/ubuntu-logo.png': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.8.0-39-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-4.4.0-59-generic
 linux-image-extra-4.4.0-59-generic
 linux-image-4.4.0-62-generic
 linux-image-extra-4.4.0-62-generic
 linux-image-4.4.0-63-generic
 linux-image-extra-4.4.0-63-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@homeserver:/home/derek# 

```

Then I re-ran it with new errors on top of the ones above.


```

dpkg: warning: files list file for package 'libswresample-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsamplerate0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libswresample-ffmpeg1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libavresample-ffmpeg2:amd64' missing; assuming package has no files currently installed
(Reading database ... 328999 files and directories currently installed.)
Removing linux-image-extra-4.4.0-59-generic (4.4.0-59.80) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
dkms: WARNING: Linux headers are missing, which may explain the above failures.
      please install the linux-headers-4.4.0-59-generic package to fix this.
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
cp: cannot stat '/usr/share/plymouth/ubuntu-logo.png': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-59-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 linux-image-extra-4.4.0-59-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```


I have no clue what botched.

---

### Post by Impavidus on 2017-02-23
It may help if you tell us what command you tried to run.

The first error is```
cp: cannot stat '/usr/share/plymouth/ubuntu-logo.png': No such file or directory
```

First try the simplest solution and hope it works. The missing file is part of the plymouth package, so```
sudo apt install --reinstall plymouth
```

---

### Post by derekcentrico on 2017-02-23
Yeah, an update went to total botch land.  I tried that command and it doesn't help.

APT errors out before the install can happen.

```
[COLOR=#000000]dpkg: warning: files list file for package 'libswresample-ffmpeg1:amd64' missing; assuming package has no files currently installed[/COLOR]dpkg: warning: files list file for package 'libavresample-ffmpeg2:amd64' missing; assuming package has no files currently installed
(Reading database ... 391799 files and directories currently installed.)
Removing linux-image-extra-4.4.0-59-generic (4.4.0-59.80) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-59-generic /boot/vmlinuz-4.4.0-59-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-59-generic
cp: cannot stat '/usr/share/plymouth/ubuntu-logo.png': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-59-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-59-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-62-generic (4.4.0-62.83) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-62-generic /boot/vmlinuz-4.4.0-62-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-62-generic
cp: cannot stat '/usr/share/plymouth/ubuntu-logo.png': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-62-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-62-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-63-generic (4.4.0-63.84) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic
cp: cannot stat '/usr/share/plymouth/ubuntu-logo.png': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-63-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-63-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-64-generic (4.4.0-64.85) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-64-generic /boot/vmlinuz-4.4.0-64-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-64-generic
cp: cannot stat '/usr/share/plymouth/ubuntu-logo.png': No such file or directory
E: /usr/share/initramfs-tools/hooks/plymouth failed with return 1.
update-initramfs: failed for /boot/initrd.img-4.4.0-64-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-64-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-59-generic
 linux-image-extra-4.4.0-62-generic
 linux-image-extra-4.4.0-63-generic
 linux-image-extra-4.4.0-64-generic
E: Sub-process /usr/bin/dpkg returned an error code (1) [COLOR=#000000]root@homeserver:/home/derek# [/COLOR]
```

---

### Post by tbenst on 2017-02-23
I think [my problem]("https://ubuntuforums.org/showthread.php?t=2353633") may be related. (as a well-timed c-c reveals)

```
$ sudo killall dpkg
$ sudo dpkg --configure -a
Setting up initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: deferring update (trigger activated)
Setting up base-files (9.4ubuntu4.4) ...
Installing new version of config file /etc/issue ...
Installing new version of config file /etc/issue.net ...
Installing new version of config file /etc/lsb-release ...
Setting up linux-image-4.4.0-63-generic (4.4.0-63.84) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
initrd.img(/boot/initrd.img-4.4.0-63-generic
) points to /boot/initrd.img-4.4.0-63-generic
 (/boot/initrd.img-4.4.0-63-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-63-generic.postinst line 491.
vmlinuz(/boot/vmlinuz-4.4.0-63-generic
) points to /boot/vmlinuz-4.4.0-63-generic
 (/boot/vmlinuz-4.4.0-63-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-63-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-63-generic /boot/vmlinuz-4.4.0-63-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic
^CFailed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-63-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-63-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-4.4.0-63-generic; however:
  Package linux-image-4.4.0-63-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-4.4.0-63-generic:
 linux-signed-image-4.4.0-63-generic depends on linux-image-4.4.0-63-generic (= 4.4.0-63.84); however:
  Package linux-image-4.4.0-63-generic is not configured yet.

dpkg: error processing package linux-signed-image-4.4.0-63-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-image-generic:
 linux-signed-image-generic depends on linux-signed-image-4.4.0-63-generic; however:
  Package linux-signed-image-4.4.0-63-generic is not configured yet.

dpkg: error processing package linux-signed-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-63-generic:
 linux-image-extra-4.4.0-63-generic depends on linux-image-4.4.0-63-generic; however:
  Package linux-image-4.4.0-63-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-63-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.63.67); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-signed-image-generic (= 4.4.0.63.67); however:
  Package linux-signed-image-generic is not configured yet.

dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools (0.122ubuntu8.8) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-63-generic
^Cdpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script was interrupted
Processing triggers for plymouth-theme-ubuntu-text (0.9.2-3ubuntu13.1) ...
update-initramfs: deferring update (trigger activated)
Errors were encountered while processing:
 linux-image-4.4.0-63-generic
 linux-image-generic
 linux-signed-image-4.4.0-63-generic
 linux-signed-image-generic
 linux-image-extra-4.4.0-63-generic
 linux-generic
 linux-signed-generic
 initramfs-tools

```

Edit: this is quite a severe issue as all operations involving installing or updating with apt are borked!

---

