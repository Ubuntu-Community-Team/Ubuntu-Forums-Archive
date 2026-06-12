---
title: "Ubuntu 16.04 - problem on every boot and sw updater not working"
date: 2016-11-20
forum: Installation &amp; Upgrades
---

### Post by linux.girl on 2016-11-20
Hi Everyone,

A while ago I upgraded to ubuntu 16.04. For some reason that I already discussed here in a different thread, the upgrade did not go smooth and in a way that the kernel continued to appear as the old kernel and not the new one for 16.04. This problem was solved (dont remember how, it was somewhere here in the forum), but since then, it feels like there is something wrong with the installation. The first problem is that Software Updater is no longer working. It shows me that packages that need to be updated, it appears to update and then when it is finished it is says "Package Operation Failed" and I don't know if it installed anything, or partially or what and I don't know how to fix this, can you assist? I attached the error that it shows. The second problem is that every time that I reboot the computer it says that there was a problem with ubuntu 16.04 and asks if I want report about it. I usually say no, this time I took a few screenshots of the errors it shows. I dont know if the two problems are connected and how I can fix this, will be happy if someone can assist. (I have 2 more screenshots of the reboot error but I could upload only 5 here).

Thanks in advance,

Linux.Girl
[ATTACH=CONFIG]272262[/ATTACH][ATTACH=CONFIG]272265[/ATTACH][ATTACH=CONFIG]272266[/ATTACH][ATTACH=CONFIG]272268[/ATTACH][ATTACH=CONFIG]272269[/ATTACH]

---

### Post by ian-weisser on 2016-11-20
Please open a terminal and copy-and-paste the complete session output here:
```
sudo apt update
sudo apt upgrade
```

---

### Post by linux.girl on 2016-11-20
Hi, here is the output followed by another boot error screenshot - thanks!! :

```
linux:~$ sudo apt update
Hit:1 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates InRelease [95.7 kB]
Get:3 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-backports InRelease [92.2 kB] 
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [94.5 kB]    
Get:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease [11.5 kB]           
Get:6 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [424 kB]
Get:7 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [418 kB]
Get:8 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [361 kB]
Get:9 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [357 kB]
Fetched 1,854 kB in 1s (994 kB/s)                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
10 packages can be upgraded. Run 'apt list --upgradable' to see them.
```
```
linux:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  gcc-5-base:i386 libasound2:i386 libasound2-plugins:i386 libasyncns0:i386 libdbus-1-3:i386 libflac8:i386 libfreetype6:i386 libice6:i386 libjack-jackd2-0:i386 libjson-c2:i386 libogg0:i386
  libpng12-0:i386 libpulse0:i386 libsamplerate0:i386 libsm6:i386 libsndfile1:i386 libspeexdsp1:i386 libstdc++6:i386 libvorbis0a:i386 libvorbisenc2:i386 libwrap0:i386 libx11-6:i386 libxau6:i386
  libxcb1:i386 libxdamage1:i386 libxdmcp6:i386 libxext6:i386 libxfixes3:i386 libxrandr2:i386 libxrender1:i386 libxtst6:i386 linux-headers-4.4.0-34 linux-headers-4.4.0-34-generic linux-headers-4.4.0-38
  linux-headers-4.4.0-38-generic linux-image-4.4.0-34-generic linux-image-4.4.0-38-generic linux-image-extra-4.4.0-34-generic linux-image-extra-4.4.0-38-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be upgraded:
  gnome-software gnome-software-common libfcitx-config4 libfcitx-gclient0 libfcitx-utils0 libprocps4 procps ubuntu-software update-notifier update-notifier-common
10 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
6 not fully installed or removed.
Need to get 3,048 kB of archives.
After this operation, 2,048 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 update-notifier amd64 3.168.2 [48.2 kB]
Get:2 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 update-notifier-common all 3.168.2 [163 kB]
Get:3 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libprocps4 amd64 2:3.3.10-4ubuntu2.2 [32.7 kB]
Get:4 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 procps amd64 2:3.3.10-4ubuntu2.2 [222 kB]
Get:5 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 ubuntu-software amd64 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1 [11.7 kB]
Get:6 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gnome-software amd64 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1 [226 kB]
Get:7 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 gnome-software-common all 3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1 [2,257 kB]
Get:8 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libfcitx-utils0 amd64 1:4.2.9.1-1ubuntu1.16.04.1 [33.8 kB]
Get:9 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libfcitx-config4 amd64 1:4.2.9.1-1ubuntu1.16.04.1 [34.0 kB]
Get:10 [http://il.archive.ubuntu.com/ubuntu](http://il.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 libfcitx-gclient0 amd64 1:4.2.9.1-1ubuntu1.16.04.1 [19.2 kB]
Fetched 3,048 kB in 2s (1,452 kB/s)           
dpkg: warning: files list file for package 'sphinx-voxforge-hmm-en' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sound-theme-freedesktop' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxfixes3:i386' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfcitx-utils0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libudisks2-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkate1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsoup-gnome2.4-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sgml-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tcpd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mobile-broadband-provider-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unity-scope-gmusicbrowser' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkdecore5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libclutter-gtk-1.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sgml-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xscreensaver-data-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sphinx-voxforge-lm-en' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-cairo' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxdmcp6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapt-pkg4.12:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'logrotate' missing; assuming package has no files currently installed
(Reading database ... 356184 files and directories currently installed.)
Preparing to unpack .../update-notifier_3.168.2_amd64.deb ...
Unpacking update-notifier (3.168.2) over (3.168.1) ...
Preparing to unpack .../update-notifier-common_3.168.2_all.deb ...
Unpacking update-notifier-common (3.168.2) over (3.168.1) ...
Preparing to unpack .../libprocps4_2%3a3.3.10-4ubuntu2.2_amd64.deb ...
Unpacking libprocps4:amd64 (2:3.3.10-4ubuntu2.2) over (2:3.3.10-4ubuntu2) ...
Preparing to unpack .../procps_2%3a3.3.10-4ubuntu2.2_amd64.deb ...
Unpacking procps (2:3.3.10-4ubuntu2.2) over (2:3.3.10-4ubuntu2) ...
Preparing to unpack .../ubuntu-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb ...
Unpacking ubuntu-software (3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1) over (3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1) ...
Preparing to unpack .../gnome-software_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_amd64.deb ...
Unpacking gnome-software (3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1) over (3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1) ...
Preparing to unpack .../gnome-software-common_3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1_all.deb ...
Unpacking gnome-software-common (3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1) over (3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1) ...
Preparing to unpack .../libfcitx-utils0_1%3a4.2.9.1-1ubuntu1.16.04.1_amd64.deb ...
Unpacking libfcitx-utils0:amd64 (1:4.2.9.1-1ubuntu1.16.04.1) over (1:4.2.9.1-1ubuntu1) ...
Preparing to unpack .../libfcitx-config4_1%3a4.2.9.1-1ubuntu1.16.04.1_amd64.deb ...
Unpacking libfcitx-config4:amd64 (1:4.2.9.1-1ubuntu1.16.04.1) over (1:4.2.9.1-1ubuntu1) ...
Preparing to unpack .../libfcitx-gclient0_1%3a4.2.9.1-1ubuntu1.16.04.1_amd64.deb ...
Unpacking libfcitx-gclient0:amd64 (1:4.2.9.1-1ubuntu1.16.04.1) over (1:4.2.9.1-1ubuntu1) ...
Processing triggers for gconf2 (3.2.6-3ubuntu6) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Processing triggers for libglib2.0-0:amd64 (2.48.1-1~ubuntu16.04.1) ...
Processing triggers for libc-bin (2.23-0ubuntu4) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (229-4ubuntu12) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for desktop-file-utils (0.22-1ubuntu5) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Setting up initramfs-tools (0.122ubuntu8.5) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-extra-4.4.0-47-generic (4.4.0-47.68) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-47-generic /boot/vmlinuz-4.4.0-47-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-47-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.4.0-47-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic:
 linux-image-generic depends on linux-image-extra-4.4.0-47-generic; however:
  Package linux-image-extra-4.4.0-47-generic is not configured yet.

dpkg: error processing package linux-image-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-image-generic (= 4.4.0.47.50); however:
  Package linux-image-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-4.4.0-42-generic (4.4.0-42.62) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
        Running depmod.
update-initramfs: deferring update (hook will be called later)
The link /initrd.img is a dangling linkto /boot/initrd.img-4.4.0-42-generic
vmlinuz(/boot/vmlinuz-4.4.0-42-generic
) points to /boot/vmlinuz-4.4.0-42-generic
 (/boot/vmlinuz-4.4.0-42-generic) -- doing nothing at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postinst line 491.
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-42-generic /boot/vmlinuz-4.4.0-42-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-42-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-42-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
Failed to process /etc/kernel/postinst.d at /var/lib/dpkg/info/linux-image-4.4.0-42-generic.postinst line 1052.
dpkg: error processing package linux-image-4.4.0-42-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of linux-image-extra-4.4.0-42-generic:
 linux-image-extra-4.4.0-42-generic depends on linux-image-4.4.0-42-generic; however:
  Package linux-image-4.4.0-42-generic is not configured yet.

dpkg: error processing package linux-image-extra-4.4.0-42-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Setting up update-notifier-common (3.168.2) ...
Setting up update-notifier (3.168.2) ...
Setting up libprocps4:amd64 (2:3.3.10-4ubuntu2.2) ...
Setting up procps (2:3.3.10-4ubuntu2.2) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up gnome-software-common (3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1) ...
Setting up gnome-software (3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1) ...
Setting up ubuntu-software (3.20.1+git20160923.2.7374bdc-0ubuntu1~xenial1) ...
Setting up libfcitx-utils0:amd64 (1:4.2.9.1-1ubuntu1.16.04.1) ...
Setting up libfcitx-config4:amd64 (1:4.2.9.1-1ubuntu1.16.04.1) ...
Setting up libfcitx-gclient0:amd64 (1:4.2.9.1-1ubuntu1.16.04.1) ...
Processing triggers for initramfs-tools (0.122ubuntu8.5) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-47-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.4.0-47-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for libc-bin (2.23-0ubuntu4) ...
Errors were encountered while processing:
 linux-image-extra-4.4.0-47-generic
 linux-image-generic
 linux-generic
 linux-image-4.4.0-42-generic
 linux-image-extra-4.4.0-42-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
linux:~$ 
```








[ATTACH=CONFIG]272271[/ATTACH]

---

### Post by ian-weisser on 2016-11-20
Terminal output is very helpful. It often explain exactly what the problem is.
For example, here's why your package manager keeps crashing: 
> **linux.girl said:**
> gzip: stdout: **No space left on device**

Let's find out about your disk space.
Please cut-and-paste to show us the complete output of the following two commands:
```
df
df -i
```

---

### Post by linux.girl on 2016-11-20
Thanks for the quick reply! I don't understand what is filling up my disk space :-( Do you think that this is also the cause for the boot error I get every time I reboot?

linux:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                          16G     0   16G   0% /dev
tmpfs                        3.2G  9.8M  3.2G   1% /run
/dev/mapper/ubuntu--vg-root  886G  749G   92G  90% /
tmpfs                         16G  584K   16G   1% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                         16G     0   16G   0% /sys/fs/cgroup
/dev/sda1                    236M  207M   17M  93% /boot
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        3.2G   76K  3.2G   1% /run/user/1000

linux:~$ df -hi
Filesystem                  Inodes IUsed IFree IUse% Mounted on
udev                          4.0M   611  4.0M    1% /dev
tmpfs                         4.0M   937  4.0M    1% /run
/dev/mapper/ubuntu--vg-root    57M  468K   56M    1% /
tmpfs                         4.0M    11  4.0M    1% /dev/shm
tmpfs                         4.0M     8  4.0M    1% /run/lock
tmpfs                         4.0M    18  4.0M    1% /sys/fs/cgroup
/dev/sda1                      61K   321   61K    1% /boot
cgmfs                         4.0M    14  4.0M    1% /run/cgmanager/fs
tmpfs                         4.0M    35  4.0M    1% /run/user/1000

_**EDIT:**_ I found what it is - I have a vmware workstation installed and the disk is filled with snapshots that I took from one of my VMs. I am deleting them now, will run the updates again and let you know if it solves the problem. Thanks!

---

### Post by ian-weisser on 2016-11-20
Not so fast...TWO problems.

> **linux.girl said:**
> /dev/mapper/ubuntu--vg-root  886G  749G   92G  **90%** /
...
/dev/sda1                    236M  207M   17M  **93%** /boot

One problem is all those VM snapshots (good catch!)
But also take a look at your /boot partition.

You obviously use an LVM or encrypted system. During boot, the system doesn't know how to read those. So you have a tiny unencrypted partition with an unencrypted copy of the Linux kernel and a ramdisk with enough information to teach that kernel how to read LVM and decrypt the system.

But that partition is tiny --it can usually hold only three kernels-- so you must occasionally perform maintenance to clean out obsolete kernels.
Accumulation of obsolete kernels was actually fixed in 16.04, so this seems rather unusual.

Let's look into it. Please copy-and paste the complete output of the following commands.
NEW: Please contain within ```
 tags, so it formats properly.
[code]ls -l /boot
dpkg -l | grep linux-image
```

---

### Post by linux.girl on 2016-11-20
Hi!

Thanks for all the help! LVM or encrypted system? No idea why I would have either. I had the last Ubuntu LTS version (I think 12?) which I installed AGES ago and then I just did an upgrade to the new ubuntu 16.04 using the software upgrade (i.e., I didn't re-install the whole thing). So I am guessing ubuntu is now using LVM as default and that would explain why the LVM? And the encryption? No idea - but I don't want to have an encryption. I did notice that since the upgrade the boot process takes much longer than it used to with the late 12 LTS. 

I want my system to be tidy, no weird stuff around - if there is an encryption, can you teach me how I spot it and how I cancel it? Regarding the LVM, I am guessing not much one can do about it?

Here is the output you asked for:

ls -l /boot

total 202229
[-rw-r--r-- 1 root root  1166336 Jul 19 03:19 abi-3.13.0-93-generic
-rw-r--r-- 1 root root  1241623 Jul 28 00:28 abi-4.4.0-34-generic
-rw-r--r-- 1 root root  1242262 Sep  6 21:52 abi-4.4.0-38-generic
-rw-r--r-- 1 root root  1242701 Oct  8 05:15 abi-4.4.0-42-generic
-rw-r--r-- 1 root root  1243086 Oct 27 01:27 abi-4.4.0-47-generic
-rw-r--r-- 1 root root   165966 Jul 19 03:19 config-3.13.0-93-generic
-rw-r--r-- 1 root root   189676 Jul 28 00:28 config-4.4.0-34-generic
-rw-r--r-- 1 root root   189732 Sep  6 21:52 config-4.4.0-38-generic
-rw-r--r-- 1 root root   189760 Oct  8 05:15 config-4.4.0-42-generic
-rw-r--r-- 1 root root   189809 Oct 27 01:27 config-4.4.0-47-generic
drwxr-xr-x 5 root root     1024 Nov 20 22:51 grub
-rw-r--r-- 1 root root 31250369 Aug 21 11:58 initrd.img-3.13.0-93-generic
-rw-r--r-- 1 root root 37145456 Aug 21 22:16 initrd.img-4.4.0-34-generic
-rw-r--r-- 1 root root 38424540 Oct 10 18:57 initrd.img-4.4.0-38-generic
-rw-r--r-- 1 root root 38865116 Nov 14 21:48 initrd.img-4.4.0-47-generic
drwx------ 2 root root    12288 Dec 25  2013 lost+found
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  3394259 Jul 19 03:19 System.map-3.13.0-93-generic
-rw------- 1 root root  3866644 Jul 28 00:28 System.map-4.4.0-34-generic
-rw------- 1 root root  3869329 Sep  6 21:52 System.map-4.4.0-38-generic
-rw------- 1 root root  3869895 Oct  8 05:15 System.map-4.4.0-42-generic
-rw------- 1 root root  3873447 Oct 27 01:27 System.map-4.4.0-47-generic
-rw------- 1 root root  5835888 Jul 19 03:19 vmlinuz-3.13.0-93-generic
-rw------- 1 root root  7046160 Jul 28 00:28 vmlinuz-4.4.0-34-generic
-rw------- 1 root root  7051680 Sep  6 21:52 vmlinuz-4.4.0-38-generic
-rw------- 1 root root  7053472 Oct  8 05:15 vmlinuz-4.4.0-42-generic
-rw------- 1 root root  7060896 Oct 27 01:27 vmlinuz-4.4.0-47-generic]

dpkg -l | grep linux-image

[rc  linux-image-3.11.0-19-generic                 3.11.0-19.33                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-20-generic                 3.11.0-20.35                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-22-generic                 3.11.0-22.38                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-93-generic                 3.13.0-93.140                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-34-generic                  4.4.0-34.53                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic                  4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-42-generic                  4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                  4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-19-generic           3.11.0-19.33                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-20-generic           3.11.0-20.35                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-22-generic           3.11.0-22.38                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic           3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-34-generic            4.4.0-34.53                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic            4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-42-generic            4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-47-generic            4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                           4.4.0.47.50                                   amd64        Generic Linux kernel image]

---

### Post by ian-weisser on 2016-11-20
> **linux.girl said:**
> So I am guessing ubuntu is now using LVM as default and that would explain why the LVM?

If your system were encrypted, you would know - you would need to enter your passphrase to decrypt the system at each boot.
So your system seems to be LVM.
LVM is _not_ Ubuntu's default. Ever. Admins must choose it, often during installation.
I'm not an expert on how to remove LVM without reinstalling (since it involves repartitioning), so I'll let other communit members work that angle.


Here are your four (mostly) installed kernels:
> **linux.girl said:**
> 
```
-rw------- 1 root root  5835888 Jul 19 03:19 vmlinuz-3.13.0-93-generic
-rw------- 1 root root  7046160 Jul 28 00:28 vmlinuz-4.4.0-34-generic
-rw------- 1 root root  7051680 Sep  6 21:52 vmlinuz-4.4.0-38-generic
-rw------- 1 root root  7053472 Oct  8 05:15 vmlinuz-4.4.0-42-generic
-rw------- 1 root root  7060896 Oct 27 01:27 vmlinuz-4.4.0-47-generic
```

And here are the relevant kernel packages. Note they are (mostly) tagged 'ii' for 'installed'. Anything 'iU' or 'iF' must be repaired or removed.:
> **linux.girl said:**
> 
```
ii  linux-image-3.13.0-93-generic                 3.13.0-93.140                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-34-generic                  4.4.0-34.53                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-generic                  4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-42-generic                  4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                  4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-93-generic           3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-34-generic            4.4.0-34.53                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-38-generic            4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-42-generic            4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-47-generic            4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                           4.4.0.47.50                                   amd64        Generic Linux kernel image
```

1) The 4.4.0-47 kernel is the current kernel for 16.04. Keep it.

2) Use the command 'uname -r' to determine your currently running kernel. Maybe it's -47, maybe not. If not, keep it too.

3) Delete the rest of the kernel packages using dpkg. Not apt. Apt won't work in an out-of-space situation.
    Example: sudo dpkg --remove linux-image-3.13.0-93-generic linux-image-extra-3.13.0-93-generic    // See the two packages in that command?

4) Run a normal 'sudo apt update' and 'sudo apt upgrade' to test if apt works again. If there are ANY error messages, stop and post the output here.

5) Any remaining packages tagged 'iU' or 'iF' should be reinstalled using apt, now that apt is working again. 
    The metapackage linux-image-generic should be reinstalled (not removed).

It's hard to say why Ubuntu 16.04's unattended-upgrades application didn't autoremove those older kernels already. Perhaps because some were not fully installed, perhaps not. Nevertheless, you will want to watch that /boot partition space for a month or two to ensure unattended-upgrades is doing the job.

---

### Post by linux.girl on 2016-11-21
Thank you so much! My kernel is really 47, so I am deleting all the rest as you suggested. What is the meaning of the ones that begin with rc, for example, rc  linux-image-3.11.0-19-generic - should those be deleted too?

_***EDIT:***_

I tried to delete those with rc and this is what I got:

dpkg -l | grep linux-image
rc  linux-image-3.11.0-19-generic                 3.11.0-19.33                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-20-generic                 3.11.0-20.35                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-22-generic                 3.11.0-22.38                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-93-generic                 3.13.0-93.140                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic                  4.4.0-34.53                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                  4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-42-generic                  4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                  4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-19-generic           3.11.0-19.33                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-20-generic           3.11.0-20.35                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-22-generic           3.11.0-22.38                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-93-generic           3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic            4.4.0-34.53                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic            4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-42-generic            4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-47-generic            4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                           4.4.0.47.50                                   amd64        Generic Linux kernel image

linux:~$ sudo  dpkg --remove linux-image-4.4.0-42-generic linux-image-4.4.0-38-generic linux-image-4.4.0-34-generic linux-image-3.13.0-93-generic linux-image-3.11.0-22-generic linux-image-3.11.0-20-generic linux-image-3.11.0-19-generic

[dpkg: dependency problems prevent removal of linux-image-4.4.0-42-generic:
 linux-image-extra-4.4.0-42-generic depends on linux-image-4.4.0-42-generic.
dpkg: error processing package linux-image-4.4.0-42-generic (--remove):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-image-4.4.0-38-generic, only the config
 files of which are on the system; use --purge to remove them too
dpkg: warning: ignoring request to remove linux-image-4.4.0-34-generic, only the config
 files of which are on the system; use --purge to remove them too
dpkg: warning: ignoring request to remove linux-image-3.13.0-93-generic, only the config
 files of which are on the system; use --purge to remove them too
dpkg: warning: ignoring request to remove linux-image-3.11.0-22-generic, only the config
 files of which are on the system; use --purge to remove them too
dpkg: warning: ignoring request to remove linux-image-3.11.0-20-generic, only the config
 files of which are on the system; use --purge to remove them too
dpkg: warning: ignoring request to remove linux-image-3.11.0-19-generic, only the config
 files of which are on the system; use --purge to remove them too
Errors were encountered while processing:
 linux-image-4.4.0-42-generic]

Should I use purge instead? Can you tell me which ones from the list below I should delete and how (purge or remove)?

[dpkg -l | grep linux-image
rc   linux-image-3.11.0-19-generic                  3.11.0-19.33                                  amd64        Linux kernel  image for version 3.11.0 on 64 bit x86 SMP
rc   linux-image-3.11.0-20-generic                  3.11.0-20.35                                  amd64        Linux kernel  image for version 3.11.0 on 64 bit x86 SMP
rc   linux-image-3.11.0-22-generic                  3.11.0-22.38                                  amd64        Linux kernel  image for version 3.11.0 on 64 bit x86 SMP
rc   linux-image-3.13.0-93-generic                  3.13.0-93.140                                 amd64        Linux kernel  image for version 3.13.0 on 64 bit x86 SMP
rc   linux-image-4.4.0-34-generic                   4.4.0-34.53                                   amd64        Linux kernel  image for version 4.4.0 on 64 bit x86 SMP
rc   linux-image-4.4.0-38-generic                   4.4.0-38.57                                   amd64        Linux kernel  image for version 4.4.0 on 64 bit x86 SMP
iF   linux-image-4.4.0-42-generic                   4.4.0-42.62                                   amd64        Linux kernel  image for version 4.4.0 on 64 bit x86 SMP
ii   linux-image-4.4.0-47-generic                   4.4.0-47.68                                   amd64        Linux kernel  image for version 4.4.0 on 64 bit x86 SMP
rc   linux-image-extra-3.11.0-19-generic            3.11.0-19.33                                  amd64        Linux kernel  extra modules for version 3.11.0 on 64 bit x86 SMP
rc   linux-image-extra-3.11.0-20-generic            3.11.0-20.35                                  amd64        Linux kernel  extra modules for version 3.11.0 on 64 bit x86 SMP
rc   linux-image-extra-3.11.0-22-generic            3.11.0-22.38                                  amd64        Linux kernel  extra modules for version 3.11.0 on 64 bit x86 SMP
rc   linux-image-extra-3.13.0-93-generic            3.13.0-93.140                                 amd64        Linux kernel  extra modules for version 3.13.0 on 64 bit x86 SMP
rc   linux-image-extra-4.4.0-34-generic             4.4.0-34.53                                   amd64        Linux kernel  extra modules for version 4.4.0 on 64 bit x86 SMP
rc   linux-image-extra-4.4.0-38-generic             4.4.0-38.57                                   amd64        Linux kernel  extra modules for version 4.4.0 on 64 bit x86 SMP
iU   linux-image-extra-4.4.0-42-generic             4.4.0-42.62                                   amd64        Linux kernel  extra modules for version 4.4.0 on 64 bit x86 SMP
iF   linux-image-extra-4.4.0-47-generic             4.4.0-47.68                                   amd64        Linux kernel  extra modules for version 4.4.0 on 64 bit x86 SMP
iU   linux-image-generic                            4.4.0.47.50                                   amd64        Generic Linux  kernel image]

---

### Post by ian-weisser on 2016-11-21
> **linux.girl said:**
> Thank you so much! My kernel is really 47, so I am deleting all the rest as you suggested. What is the meaning of the ones that begin with rc, for example, rc  linux-image-3.11.0-19-generic - should those be deleted too?

'rc' means the package is already deleted.  Yes, the package database remembers deleted packages too.
'ii' means the package is properly installed
'iF' means the package is marked for installation, but only half installed. Fix it with 'sudo dpkg --configure --pending'
'iU' means the package is marked for installation, but only unpacked. Fix it with 'sudo dpkg --configure --pending'

See man dpkg-query for the complete list of database codes.
See man dpkg for the --configure options.


> **linux.girl said:**
> Should I use purge instead?

'remove' deletes all files, except setting files in /etc and personal files in /home.
'purge' deletes all files, including setting files in /etc, except personal files in /home.
Since kernel image packages don't place any files in /etc, 'remove' and 'purge' will do exactly the same thing.
See for yourself by listing all the files provided by a kernel image package: dpkg -L [COLOR=#000000]linux-image-4.4.0-47-generic[/COLOR]

Some users mistakenly believe that 'purge' is some kind of 'force remove' or 'super remove' command. It's not. Now you know more than they do.

---

### Post by linux.girl on 2016-11-21
Thank you Ian! Both problems solved - software updater is now working and I don't get any more errors after reboot!

I guess I will have to keep a close eye on the boot partition and make sure it doesnt get too full.

Regarding the LVM, I probably chose it and forgot, I installed it a long time ago :-)

---

### Post by ian-weisser on 2016-11-21
> **linux.girl said:**
> I guess I will have to keep a close eye on the boot partition and make sure it doesn't get too full.
In 16.04 and newer, when a new kernel is installed, two things are supposed to happen. Look for these:

When a new kernel is installed, a hook at /etc/kernel/postinst.d/apt-auto-removal will keep the two newest kernel packages and mark older kernel packages as eligible for autoremoval.
Just eligible (apt-mark 'auto'). The hook doesn't actually do anything further.
You can check the apt-marking with the command 'apt-mark showremove | grep linux-image' (This will show you all the 'rc' packages, too)

The next time apt does it's daily update (usually about 24 hours later), it will automatically remove the marked packages, including kernel packages.
This is logged in /var/log/unattended-upgrades.

I suspect your original problem was those half-configured packages. Half-configured packages can occur from a lot of possible causes, so it may not be worthwhile guessing beyond that.
If you have those half-configured packages fixed, then I expect apt to remove old kernels properly.

---

### Post by linux.girl on 2016-11-22
Thank you so so much! Very informative and detailed, I learned a lot from you!

All the best!

---

### Post by pradtf2 on 2017-01-12
me too ian! appreciate all the info!

this thread help straighten out a situation on our ubuntu server where /lib/modules kept old items eventually resulting in disk full ... couldn't even autocomplete!

i followed your directions to linux.girl and cleaned it up: i have versions 31,38,42,45,47,51,53,57,59 all sitting around.
uname -r gave version 53.

after a final apt update/upgrade and apt autoremove, i'm left with 59 as the running version, but 53,57,59 still left in the modules directory. all earlier versions have rc on them and are gone.

i don't really understand how this happened through auto updates, but i guess it's what you said earlier about the arrangement not removing older items. i also don't understand why there are two older versions left behind - is it so that in some emergency you can run the older kernel to keep the server going?

in friendship,
prad

---

### Post by linux.girl on 2017-03-02
Ian, you are going to kill me, but the issue happened again and I did everything we discussed here and it did not help - perhaps I am senile and forgot something??

```

dpkg -l | grep linux-image
rc  linux-image-3.11.0-19-generic                 3.11.0-19.33                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-20-generic                 3.11.0-20.35                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-22-generic                 3.11.0-22.38                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-93-generic                 3.13.0-93.140                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic                  4.4.0-34.53                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                  4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                  4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-generic                  4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-generic                  4.4.0-51.72                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                  4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-4.4.0-63-generic                  4.4.0-63.84                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-generic                  4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-19-generic           3.11.0-19.33                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-20-generic           3.11.0-20.35                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-22-generic           3.11.0-22.38                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-93-generic           3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic            4.4.0-34.53                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic            4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic            4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-47-generic            4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-51-generic            4.4.0-51.72                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic            4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-extra-4.4.0-63-generic            4.4.0-63.84                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iF  linux-image-extra-4.4.0-64-generic            4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-generic                           4.4.0.64.68                                   amd64        Generic Linux kernel image


uname -r
4.4.0-62-generic

```

I get an error on everything I try to delete and the boot partition is full :-(

You also said before that:

"In 16.04 and newer, when a new kernel is installed, two things are supposed to happen. Look for these:

When a new kernel is installed, a hook at  /etc/kernel/postinst.d/apt-auto-removal will keep the two newest kernel  packages and mark older kernel packages as eligible for autoremoval.
Just eligible (apt-mark 'auto'). The hook doesn't actually do anything further.
You can check the apt-marking with the command 'apt-mark showremove |  grep linux-image' (This will show you all the 'rc' packages, too)

The next time apt does it's daily update (usually about 24 hours later),  it will automatically remove the marked packages, including kernel  packages.
This is logged in /var/log/unattended-upgrades.

I suspect your original problem was those half-configured packages.  Half-configured packages can occur from a lot of possible causes, so it  may not be worthwhile guessing beyond that.
If you have those half-configured packages fixed, then I expect apt to remove old kernels properly."

It doesn't automatically remove any kernel packages, as you can see from the command above they are all there :-(

What do I do?

---

### Post by dajavex71 on 2017-03-02
Give this a go:
> sudo apt-get autoremove


---

### Post by linux.girl on 2017-03-03
Hi dejavex71, I did what you suggested, and it seems to have worked, but here are a few weird things.

1 - After the command finished working, the computer rebooted and opened my browser in this webpage: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/798414](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/798414) - meaning it things I still have a shortage of space in my disk?

2 - The result of uname -r is now 4.4.0-64-generic

3 - But the result of dpkg -l | grep linux-image still shows all the old kernels - I know rc means it has been removed, but given item 1 in the list of questions, maybe they are still there?
rc  linux-image-3.11.0-19-generic                 3.11.0-19.33                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-20-generic                 3.11.0-20.35                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-22-generic                 3.11.0-22.38                                  amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-93-generic                 3.13.0-93.140                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic                  4.4.0-34.53                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                  4.4.0-38.57                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                  4.4.0-42.62                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic                  4.4.0-47.68                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-51-generic                  4.4.0-51.72                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-62-generic                  4.4.0-62.83                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ri  linux-image-4.4.0-63-generic                  4.4.0-63.84                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-64-generic                  4.4.0-64.85                                   amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-19-generic           3.11.0-19.33                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-20-generic           3.11.0-20.35                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-22-generic           3.11.0-22.38                                  amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-93-generic           3.13.0-93.140                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic            4.4.0-34.53                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic            4.4.0-38.57                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic            4.4.0-42.62                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic            4.4.0-47.68                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-51-generic            4.4.0-51.72                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-62-generic            4.4.0-62.83                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-63-generic            4.4.0-63.84                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic            4.4.0-64.85                                   amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.4.0.64.68                                   amd64        Generic Linux kernel image

Meaning it didn't really clean enough space in my boot partition and the next kernel update will get me to the same problem again. Which leads me to my question. How do I avoid this from happening? Ian said previously:

"When a new kernel is installed, a hook at  /etc/kernel/postinst.d/apt-auto-removal will keep the two newest kernel  packages and mark older kernel packages as eligible for autoremoval.
Just eligible (apt-mark 'auto'). The hook doesn't actually do anything further.
You can check the apt-marking with the command 'apt-mark showremove |  grep linux-image' (This will show you all the 'rc' packages, too)

The next time apt does it's daily update (usually about 24 hours later),  it will automatically remove the marked packages, including kernel  packages.
This is logged in /var/log/unattended-upgrades."

But I obviously didn't edit the file correctly because it still doesn't leave me with only the last two kernels - so can someone help me see what do I have to edit on /etc/kernel/postinst.d/apt-auto-removal to make sure that everything that has to be removed is indeed removed and not only marked?

Thank you so much!

---

### Post by linux.girl on 2017-06-04
Hi,

I was searching some old threads of mine and came across something very useful posted by [**[COLOR=#000000]ibjsb4[/COLOR]**]("https://ubuntuforums.org/member.php?u=1729120") at [https://ubuntuforums.org/showthread.php?t=2247076](https://ubuntuforums.org/showthread.php?t=2247076) - a very good way to remove old linux kernels and install the latest +keep a previous one for backup. Since this thread is about this issue and is newer, I thought it was worth posting here to help people who are looking at this newer thread and not the old one.

 	Code:
 	dpkg -l 'linux-*' | sed '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]* [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge 
[https://help.ubuntu.com/community/Lu...Advanced_users]("https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveOldKernels#Advanced_users")
This will remove all old kernels, then ..
 	Code:
 	sudo apt-get update && sudo apt-get dist-upgrade && sudo reboot 
This will install the latest kernel (xxxxxx) and leave the current kernel (xxxxxx) for backup.

Cheers,

linux.girl

---

