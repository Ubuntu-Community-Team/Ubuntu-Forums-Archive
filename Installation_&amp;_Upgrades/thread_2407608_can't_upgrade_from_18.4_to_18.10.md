---
title: "can't upgrade from 18.4 to 18.10"
date: 2018-12-06
forum: Installation &amp; Upgrades
---

### Post by linux.girl on 2018-12-06
Hello,

I tried to upgrade my ubunto 18.4 to 18.10. At the end, it tells me it cannot continue because I don't have enough disk space on /boot and therefore it did only a partial update. I reboot the system and 18.10 appears, but tells me it is only a partial upgrade because not enough disk space on /boot.

I try to free disk space and get this error:

apt autoremove
E: Could not get lock /var/lib/dpkg/lock-frontend - open (11: Resource temporarily unavailable)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), is another process using it?

Tried many things, nothing helped, i.e., tried to kill the process, but the process number kept changing and reapearing every time I killed it.

Any suggestions?

Thanks!

---

### Post by ajgreeny on 2018-12-06
I assume from that error that you are either using an encrypted system or have chosen LVM when installing, both of which create a separate /boot partition.

Unfortunately the partition created is rather small (~250MB) and can quickly fill with old kernels if you do not regularly either remove those old versions manually or regularly use autoremove.

If you have accepted **unattended upgrades** that should, I believe, do all this automatically for you, but I do not use the unattended upgrades, preferring to keep control manually, so I may be wrong about that.

However we now need to remove old kernels for you but as autoremove is no longer working for you as a result of lack of headroom, so to check the current state of play please show us the output of ```
df -hT
dpkg -l linux-*
```
Please maximise the terminal before running those commands to avoid cutting off part of the output of the dpkg command.
We should then be able to show you another dpkg command to remove at least one kernel version after which the ```
sudo apt autoremove
``` command may be successful in removing others no longer needed.

---

### Post by linux.girl on 2018-12-06
Hi there, first of all, thank you so much for taking the time to answer me. I did a manual upgrade from the previous LTS to the current LTS 18.4 - it went smoothly even though it is a huge jump. But when I tried to manually upgrade from 18.4 to 18.10, then I got these problems. Just so I understand, why autoremove stopped working? Didn't understand that one. In any event, here are the results of the commands you told me to run:

 ```
df -hT
Filesystem                  Type      Size  Used Avail Use% Mounted on
udev                        devtmpfs   16G     0   16G   0% /dev
tmpfs                       tmpfs     3.2G  3.5M  3.2G   1% /run
/dev/mapper/ubuntu--vg-root ext4      886G  646G  195G  77% /
tmpfs                       tmpfs      16G   28M   16G   1% /dev/shm
tmpfs                       tmpfs     5.0M  4.0K  5.0M   1% /run/lock
tmpfs                       tmpfs      16G     0   16G   0% /sys/fs/cgroup
/dev/sda1                   ext2      236M  220M  4.2M  99% /boot
tmpfs                       tmpfs     3.2G   16K  3.2G   1% /run/user/124
tmpfs                       tmpfs     3.2G   36K  3.2G   1% /run/user/1000


dpkg -l linux-*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                          Version                     Architecture                Description
+++-=============================================-===========================-===========================-===============================================================================================
ii  linux-base                                    4.5ubuntu1                  all                         Linux image base package
un  linux-doc-3.11.0                              <none>                      <none>                      (no description available)
un  linux-doc-3.13.0                              <none>                      <none>                      (no description available)
un  linux-doc-4.15.0                              <none>                      <none>                      (no description available)
un  linux-doc-4.4.0                               <none>                      <none>                      (no description available)
ii  linux-firmware                                1.175                       all                         Firmware for Linux kernel drivers
un  linux-firmware-snapdragon                     <none>                      <none>                      (no description available)
ii  linux-generic                                 4.15.0.39.41                amd64                       Complete Generic Linux kernel and headers
un  linux-headers                                 <none>                      <none>                      (no description available)
un  linux-headers-3.0                             <none>                      <none>                      (no description available)
un  linux-headers-3.11.0-19-generic               <none>                      <none>                      (no description available)
un  linux-headers-3.11.0-20-generic               <none>                      <none>                      (no description available)
un  linux-headers-3.11.0-22-generic               <none>                      <none>                      (no description available)
un  linux-headers-3.13.0-93-generic               <none>                      <none>                      (no description available)
ii  linux-headers-4.15.0-39                       4.15.0-39.42                all                         Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-39-generic               4.15.0-39.42                amd64                       Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
un  linux-headers-4.4.0-34-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-38-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-42-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-47-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-51-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-62-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-63-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-64-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-66-generic                <none>                      <none>                      (no description available)
un  linux-headers-4.4.0-71-generic                <none>                      <none>                      (no description available)
un  linux-headers-686-pae                         <none>                      <none>                      (no description available)
un  linux-headers-amd64                           <none>                      <none>                      (no description available)
ii  linux-headers-generic                         4.15.0.39.41                amd64                       Generic Linux kernel headers
un  linux-image                                   <none>                      <none>                      (no description available)
un  linux-image-3.0                               <none>                      <none>                      (no description available)
rc  linux-image-3.11.0-19-generic                 3.11.0-19.33                amd64                       Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-20-generic                 3.11.0-20.35                amd64                       Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.11.0-22-generic                 3.11.0-22.38                amd64                       Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-93-generic                 3.13.0-93.140               amd64                       Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-4.15.0-39-generic                 4.15.0-39.42                amd64                       Signed kernel image generic
rc  linux-image-4.4.0-34-generic                  4.4.0-34.53                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                  4.4.0-38.57                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                  4.4.0-42.62                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic                  4.4.0-47.68                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-51-generic                  4.4.0-51.72                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-62-generic                  4.4.0-62.83                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-63-generic                  4.4.0-63.84                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-64-generic                  4.4.0-64.85                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic                  4.4.0-66.87                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-71-generic                  4.4.0-71.92                 amd64                       Linux kernel image for version 4.4.0 on 64 bit x86 SMP
un  linux-image-4.4.0-79-generic                  <none>                      <none>                      (no description available)
un  linux-image-4.4.0-91-generic                  <none>                      <none>                      (no description available)
rc  linux-image-extra-3.11.0-19-generic           3.11.0-19.33                amd64                       Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-20-generic           3.11.0-20.35                amd64                       Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-22-generic           3.11.0-22.38                amd64                       Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-93-generic           3.13.0-93.140               amd64                       Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic            4.4.0-34.53                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic            4.4.0-38.57                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic            4.4.0-42.62                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic            4.4.0-47.68                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-51-generic            4.4.0-51.72                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic            4.4.0-62.83                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-63-generic            4.4.0-63.84                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-generic            4.4.0-64.85                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic            4.4.0-66.87                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-71-generic            4.4.0-71.92                 amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-generic            4.4.0-79.100                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-91-generic            4.4.0-91.114                amd64                       Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                           4.15.0.39.41                amd64                       Generic Linux kernel image
un  linux-image-unsigned-4.15.0-39-generic        <none>                      <none>                      (no description available)
un  linux-initramfs-tool                          <none>                      <none>                      (no description available)
un  linux-kernel-log-daemon                       <none>                      <none>                      (no description available)
ii  linux-modules-4.15.0-39-generic               4.15.0-39.42                amd64                       Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-39-generic         4.15.0-39.42                amd64                       Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
un  linux-restricted-common                       <none>                      <none>                      (no description available)
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5        all                         base package for ALSA and OSS sound systems
un  linux-source-3.11.0                           <none>                      <none>                      (no description available)
un  linux-source-3.13.0                           <none>                      <none>                      (no description available)
un  linux-source-4.15.0                           <none>                      <none>                      (no description available)
un  linux-source-4.4.0                            <none>                      <none>                      (no description available)
un  linux-tools                                   <none>                      <none>                      (no description available)
```

---

### Post by linux.girl on 2018-12-08
Help please dear community - I don't know what to do :-(

---

### Post by linux.girl on 2018-12-08
Even when I try to remove manually it doesn't work:

apt-get purge linux-image-3.11.0-19-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-3.11.0-19-generic*
0 upgraded, 0 newly installed, 1 to remove and 7 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up initramfs-tools (0.131ubuntu15) ...
update-initramfs: deferring update (trigger activated)
dpkg: warning: files list file for package 'sphinx-voxforge-hmm-en' missing; assuming package has no files currently installed
dpkg:  warning: files list file for package 'unity-scope-gmusicbrowser'  missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sgml-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sphinx-voxforge-lm-en' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapt-pkg4.12:amd64' missing; assuming package has no files currently installed
(Reading database ... 220464 files and directories currently installed.)
Purging configuration files for linux-image-3.11.0-19-generic (3.11.0-19.33) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.11.0-19-generic /boot/vmlinuz-3.11.0-19-generic
Processing triggers for initramfs-tools (0.131ubuntu15) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-39-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.15.0-39-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 installed initramfs-tools package post-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)


Then I do :dpkg -l linux-* 
And see that what I tried to remove is still there. Same if I try with rm -rf.

What do I do??

---

### Post by ajgreeny on 2018-12-09
Sorry for the delay but Christmas preparations take time away from the forum.

I am a bit confused by what I'm seeing here because what **dpkg** is showing as still installed, according to the output of that command I asked you to run, should not be sufficient to fill your /boot partition.
We need to dig a bit deeper so can you now please show us the output of command ```
ls -l /boot
df -i
``` as I am now wondering if there are some orphaned kernels in there that can no longer be seen by dpkg because you updated from a previous Ubuntu version, or if you have simply run out of inode space.

There are many configurations for old kernels remaining but at present you have apparently only one kernel to which you can boot, 4.15.0-39, so there is nothing obvious to remove with the package manager; we may even have to resort to manually deleting files from /boot, something which in most situations is not sensible nor safe, but in your position may be the only option.

Let's keep trying!  We can do it.

---

