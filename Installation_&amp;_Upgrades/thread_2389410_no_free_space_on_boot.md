---
title: "no free space on boot"
date: 2018-04-16
forum: Installation &amp; Upgrades
---

### Post by Coriander Redgoat on 2018-04-16
I have my disk encrypted and apparently that causes it to not have much space. I [previously had this problem]("https://ubuntuforums.org/showthread.php?t=2355234&page=2&p=13619465#post13619465") and it was solved for the time being, but alas, no more. What can I do? I think this also caused a boot problem.

Thanks!

---

### Post by Coriander Redgoat on 2018-04-16
The boot issue was something like "end kernel panic not syncing vfs unable to mount root fs on unknown block"

---

### Post by deadflowr on 2018-04-16
This would be a different issue than before.
Step 1 would be to try booting into another older kernel.
The new  message typically means the current kernel is corrupted or something.

---

### Post by Coriander Redgoat on 2018-04-17
I booted from an older kernel and that seems to have worked

---

### Post by deadflowr on 2018-04-17
Now run those commands you did the last time
like these commands
```
df -i
df -h
dpkg -l  linux*
```
and see if there some issues with space or broken kernel installed.

---

### Post by Coriander Redgoat on 2018-04-17
Sorry for the wall of text. From those commands:

```
coriander@radish1:~$ df -iFilesystem                     Inodes  IUsed     IFree IUse% Mounted on
udev                           484828    574    484254    1% /dev
tmpfs                          491712    854    490858    1% /run
/dev/mapper/ubuntu--vg-root  29032448 541685  28490763    2% /
tmpfs                          491712    189    491523    1% /dev/shm
tmpfs                          491712      6    491706    1% /run/lock
tmpfs                          491712     19    491693    1% /sys/fs/cgroup
/dev/loop0                      12817  12817         0  100% /snap/core/4407
/dev/loop1                        242    242         0  100% /snap/okular/3
/dev/loop2                      12829  12829         0  100% /snap/core/4327
/dev/loop3                      12826  12826         0  100% /snap/core/4206
/dev/sdb1                       62248    318     61930    1% /boot
cgmfs                          491712     15    491697    1% /run/cgmanager/fs
tmpfs                          491712     45    491667    1% /run/user/1000
/home/coriander/.Private     29032448 541685  28490763    2% /home/coriander
/dev/sdc1                           0      0         0     - /media/coriander/BOB
/dev/sda1                   406325456  78724 406246732    1% /media/coriander/Seagate Expansion Drive
coriander@radish1:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        385M   11M  374M   3% /run
/dev/mapper/ubuntu--vg-root  436G  366G   49G  89% /
tmpfs                        1.9G   88M  1.8G   5% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop0                    87M   87M     0 100% /snap/core/4407
/dev/loop1                   7.4M  7.4M     0 100% /snap/okular/3
/dev/loop2                    83M   83M     0 100% /snap/core/4327
/dev/loop3                    82M   82M     0 100% /snap/core/4206
/dev/sdb1                    236M  207M   18M  93% /boot
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        385M  108K  385M   1% /run/user/1000
/home/coriander/.Private     436G  366G   49G  89% /home/coriander
/dev/sdc1                    3.8G  2.4G  1.4G  65% /media/coriander/BOB
/dev/sda1                    932G  545G  388G  59% /media/coriander/Seagate Expansion Drive
coriander@radish1:~$ dpkg -l  linux*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-aws-tool <none>       <none>       (no description available)
ii  linux-base     4.0ubuntu1   all          Linux image base package
un  linux-doc-4.4. <none>       <none>       (no description available)
ii  linux-firmware 1.157.17     all          Firmware for Linux kernel drivers
un  linux-firmware <none>       <none>       (no description available)
ii  linux-generic  4.4.0.119.12 amd64        Complete Generic Linux kernel and
iU  linux-generic- 4.13.0.38.57 amd64        Complete Generic Linux kernel and
un  linux-gke-tool <none>       <none>       (no description available)
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.13.0-37.42 all          Header files related to Linux ker
ii  linux-headers- 4.13.0-37.42 amd64        Linux kernel headers for version 
ii  linux-headers- 4.13.0-38.43 all          Header files related to Linux ker
ii  linux-headers- 4.13.0-38.43 amd64        Linux kernel headers for version 
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.4.0-119.14 all          Header files related to Linux ker
ii  linux-headers- 4.4.0-119.14 amd64        Linux kernel headers for version 
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.4.0.119.12 amd64        Generic Linux kernel headers
ii  linux-headers- 4.13.0.38.57 amd64        Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
rc  linux-image-4. 4.13.0-36.40 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.13.0-37.42 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.13.0-38.43 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-101.12 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-103.12 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-104.12 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-109.13 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-112.13 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-116.14 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.4.0-119.14 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-64.85  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-66.87  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-70.91  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-71.92  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-72.93  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-75.96  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-78.99  amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-79.100 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-81.104 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-83.106 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-87.110 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-89.112 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-92.115 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-93.116 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-96.119 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-97.120 amd64        Linux kernel image for version 4.
rc  linux-image-4. 4.4.0-98.121 amd64        Linux kernel image for version 4.
rc  linux-image-ex 4.13.0-36.40 amd64        Linux kernel extra modules for ve
iF  linux-image-ex 4.13.0-37.42 amd64        Linux kernel extra modules for ve
iF  linux-image-ex 4.13.0-38.43 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-101.12 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-103.12 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-104.12 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-109.13 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-112.13 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-116.14 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.4.0-119.14 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-64.85  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-66.87  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-70.91  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-71.92  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-72.93  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-75.96  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-78.99  amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-79.100 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-81.104 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-83.106 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-87.110 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-89.112 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-92.115 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-93.116 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-96.119 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-97.120 amd64        Linux kernel extra modules for ve
rc  linux-image-ex 4.4.0-98.121 amd64        Linux kernel extra modules for ve
ii  linux-image-ge 4.4.0.119.12 amd64        Generic Linux kernel image
iU  linux-image-ge 4.13.0.38.57 amd64        Generic Linux kernel image
un  linux-initramf <none>       <none>       (no description available)
un  linux-kernel-h <none>       <none>       (no description available)
un  linux-kernel-l <none>       <none>       (no description available)
ii  linux-libc-dev 4.4.0-119.14 amd64        Linux Kernel Headers for developm
un  linux-restrict <none>       <none>       (no description available)
ii  linux-sound-ba 1.0.25+dfsg- all          base package for ALSA and OSS sou
un  linux-source-4 <none>       <none>       (no description available)
un  linux-tools    <none>       <none>       (no description available)
ii  linux-tools-4. 4.4.0-119.14 amd64        Linux kernel version specific too
ii  linux-tools-4. 4.4.0-119.14 amd64        Linux kernel version specific too
ii  linux-tools-co 4.4.0-119.14 all          Linux kernel version specific too
ii  linux-tools-vi 4.4.0.119.12 amd64        This package will always depend o



```

---

### Post by deadflowr on 2018-04-17
It looks like a slight space issue is involved. (only 18mb of pace on the boot partition)
You are having some issue with the 4.13.0-38 kernel.
Perhaps they are related.

Firstly you might want to run the command Bashing-om provided in the last thread to clear all those rc'd packages.
Just to make things easier to read.
(This one
```
dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P
```
then maybe post which kernel is the one you are booting into:
```
uname -r
```
This will help provide what direction to move forward with.
(and prevent us from giving undesirable advice, like advice that would try to remove the kernel you are using)

There is probably more, but let's start with some baby steps.

---

### Post by Coriander Redgoat on 2018-04-17
```
coriander@radish1:~$ uname -r
4.13.0-38-generic

```

---

### Post by deadflowr on 2018-04-17
A quick skim of the output shows you have both the linux-image\headers-generic packages and the linux-image\headers-generic-hwe-16.04 packages
The linux-image\headers-generic packages are providing the 4.4 kernels.
the linux-image\header-generic-hwe-16.04 packages are providing the 4.13 kernels.
You only need one of those.
Since you are currently running the 4.13.0-38 kernel, you might consider removing the linux-image\header-generic packages.
And then remove the subsequent kernels related to those packages.
Something like
```
sudo apt purge linux-image-generic linux-headers-generic
```
will remove those.
Then you can run an autoremove to remove the leftover kernel packages for those.
```
sudo apt autoremove --purge
```
That should hopefully clear up space and allow you to run
```
sudo apt update
sudo apt install --reinstall linux-image-generic-hwe-16.04 linux-headers-generic-hwe-16.04
```

That should help clean things up some.

Hope it helps
Hope it make sense

---

### Post by Coriander Redgoat on 2018-04-17
On running that first command, some errors:

```
 sudo apt purge linux-image-generic linux-headers-generic[sudo] password for coriander: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-119 linux-headers-4.4.0-119-generic
  linux-image-4.4.0-119-generic linux-image-extra-4.4.0-119-generic
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-generic* linux-headers-generic* linux-image-generic*
0 upgraded, 0 newly installed, 3 to remove and 3 not upgraded.
5 not fully installed or removed.
After this operation, 43.0 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 326441 files and directories currently installed.)
Removing linux-generic (4.4.0.119.125) ...
Removing linux-headers-generic (4.4.0.119.125) ...
Removing linux-image-generic (4.4.0.119.125) ...
Setting up initramfs-tools (0.122ubuntu8.11) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-image-extra-4.13.0-38-generic (4.13.0-38.43~16.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-38-generic /boot/vmlinuz-4.13.0-38-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-38-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-38-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-38-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of linux-image-generic-hwe-16.04:
 linux-image-generic-hwe-16.04 depends on linux-image-extra-4.13.0-38-generic; however:
  Package linux-image-extra-4.13.0-38-generic is not configured yet.


dpkg: error processing package linux-image-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic-hwe-16.04:
 linux-generic-hwe-16.04 depends on linux-image-generic-hwe-16.04 (= 4.13.0.38.57); however:
  Package linux-image-generic-hwe-16.04 is not configured yet.


dpkg: error processing package linux-generic-hwe-16.04 (--configure):
 dependency problems - leaving unconfigured
Setting up linux-image-extra-4.13.0-37-generic (4.13.0-37.42~16.04.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.13.0-37-generic /boot/vmlinuz-4.13.0-37-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.13.0-37-generic /boot/vmlinuz-4.13.0-37-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.13.0-37-generic /boot/vmlinuz-4.13.0-37-generic
update-initramfs: Generating /boot/initrd.img-4.13.0-37-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-37-generic with 1.
run-parts: /etc/kernel/postinst.d/initramfs-tools exited with return code 1
dpkg: error processing package linux-image-extra-4.13.0-37-generic (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Processing triggers for initramfs-tools (0.122ubuntu8.11) ...
update-initramfs: Generating /boot/initrd.img-4.13.0-38-generic


gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-4.13.0-38-generic with 1.
dpkg: error processing package initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.13.0-38-generic
 linux-image-generic-hwe-16.04
 linux-generic-hwe-16.04
 linux-image-extra-4.13.0-37-generic
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)



```

What's that about?

---

### Post by deadflowr on 2018-04-17
Try the autoremove command now.
and then if still getting those messages
Try
```
sudo apt-get install -f
```
and see what happens there.

With hope, removing the leftover 4.4 kernels should gain some needed space.

---

### Post by Coriander Redgoat on 2018-04-17
looks like boot has 30% free now

---

### Post by Coriander Redgoat on 2018-04-17
Autoremove seems to have gone off without a hitch

---

### Post by Coriander Redgoat on 2018-04-24
Not enough space on boot again :(

---

### Post by Coriander Redgoat on 2018-04-24
```
coriander@radish1:~$ df -i
Filesystem                     Inodes  IUsed     IFree IUse% Mounted on
udev                           484828    583    484245    1% /dev
tmpfs                          491712    878    490834    1% /run
/dev/mapper/ubuntu--vg-root  29032448 509338  28523110    2% /
tmpfs                          491712    219    491493    1% /dev/shm
tmpfs                          491712      6    491706    1% /run/lock
tmpfs                          491712     19    491693    1% /sys/fs/cgroup
/dev/loop0                      12817  12817         0  100% /snap/core/4407
/dev/loop1                        242    242         0  100% /snap/okular/3
/dev/loop3                      12826  12826         0  100% /snap/core/4206
/dev/sdb1                       62248    312     61936    1% /boot
cgmfs                          491712     15    491697    1% /run/cgmanager/fs
tmpfs                          491712     54    491658    1% /run/user/1000
/home/coriander/.Private     29032448 509338  28523110    2% /home/coriander
/dev/sdc1                           0      0         0     - /media/coriander/BOB
/dev/sda1                   406294940  78746 406216194    1% /media/coriander/Seagate Expansion Drive
/dev/loop4                      12819  12819         0  100% /snap/core/4486



```

```
coriander@radish1:~$ df -h
Filesystem                   Size  Used Avail Use% Mounted on
udev                         1.9G     0  1.9G   0% /dev
tmpfs                        385M   40M  345M  11% /run
/dev/mapper/ubuntu--vg-root  436G  370G   45G  90% /
tmpfs                        1.9G   62M  1.9G   4% /dev/shm
tmpfs                        5.0M  4.0K  5.0M   1% /run/lock
tmpfs                        1.9G     0  1.9G   0% /sys/fs/cgroup
/dev/loop0                    87M   87M     0 100% /snap/core/4407
/dev/loop1                   7.4M  7.4M     0 100% /snap/okular/3
/dev/loop3                    82M   82M     0 100% /snap/core/4206
/dev/sdb1                    236M  156M   69M  70% /boot
cgmfs                        100K     0  100K   0% /run/cgmanager/fs
tmpfs                        385M  144K  385M   1% /run/user/1000
/home/coriander/.Private     436G  370G   45G  90% /home/coriander
/dev/sdc1                    3.8G  2.4G  1.4G  65% /media/coriander/BOB
/dev/sda1                    932G  545G  388G  59% /media/coriander/Seagate Expansion Drive
/dev/loop4                    87M   87M     0 100% /snap/core/4486



```

```
coriander@radish1:~$ dpkg -l  linux*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  linux-aws-tool <none>       <none>       (no description available)
ii  linux-base     4.0ubuntu1   all          Linux image base package
ii  linux-firmware 1.157.17     all          Firmware for Linux kernel drivers
un  linux-firmware <none>       <none>       (no description available)
iU  linux-generic- 4.13.0.39.58 amd64        Complete Generic Linux kernel and
un  linux-gke-tool <none>       <none>       (no description available)
un  linux-headers  <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
un  linux-headers- <none>       <none>       (no description available)
ii  linux-headers- 4.13.0-38.43 all          Header files related to Linux ker
ii  linux-headers- 4.13.0-38.43 amd64        Linux kernel headers for version 
ii  linux-headers- 4.13.0-39.44 all          Header files related to Linux ker
ii  linux-headers- 4.13.0-39.44 amd64        Linux kernel headers for version 
ii  linux-headers- 4.13.0.39.58 amd64        Generic Linux kernel headers
un  linux-image    <none>       <none>       (no description available)
rc  linux-image-4. 4.13.0-37.42 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.13.0-38.43 amd64        Linux kernel image for version 4.
ii  linux-image-4. 4.13.0-39.44 amd64        Linux kernel image for version 4.
rH  linux-image-ex 4.13.0-37.42 amd64        Linux kernel extra modules for ve
ii  linux-image-ex 4.13.0-38.43 amd64        Linux kernel extra modules for ve
iF  linux-image-ex 4.13.0-39.44 amd64        Linux kernel extra modules for ve
iU  linux-image-ge 4.13.0.39.58 amd64        Generic Linux kernel image
un  linux-initramf <none>       <none>       (no description available)
un  linux-kernel-h <none>       <none>       (no description available)
un  linux-kernel-l <none>       <none>       (no description available)
ii  linux-libc-dev 4.4.0-121.14 amd64        Linux Kernel Headers for developm
un  linux-restrict <none>       <none>       (no description available)
ii  linux-sound-ba 1.0.25+dfsg- all          base package for ALSA and OSS sou
un  linux-tools    <none>       <none>       (no description available)
ii  linux-tools-4. 4.4.0-121.14 amd64        Linux kernel version specific too
ii  linux-tools-4. 4.4.0-121.14 amd64        Linux kernel version specific too
ii  linux-tools-co 4.4.0-121.14 all          Linux kernel version specific too
ii  linux-tools-vi 4.4.0.121.12 amd64        This package will always depend o



```

---

### Post by oldfred on 2018-04-24
What brand/model system?

I still think there are more kernels you can houseclean. But that is just /boot.

Some have issues of run away log files.
 Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[https://ubuntuforums.org/showthread.php?t=2327103&page=3](https://ubuntuforums.org/showthread.php?t=2327103&page=3) 

      
 cd / or cd /home
sudo du -hc --max-depth=1
Shows just /
sudo du -hx --max-depth=1 / 2> /dev/null

---

### Post by deadflowr on 2018-04-24
I'd run 
```
 ls /boot
```
and see if there might be an unwanted initrd.img file or two.
Sometimes, rarely, but sometimes you might find package removal misses an initrd from an older kernel series.
So see if any initrd.img for the 4.4 kernels is there.
If you do, you can remove that manually.

It's a shot in the dark.

---

### Post by Coriander Redgoat on 2018-04-24
Its a system 76 Lemu4. The boot partition is small because I did full disk encryption and there's a bug apparently

---

### Post by Coriander Redgoat on 2018-04-24
```
coriander@radish1:~$ ls /boot
abi-4.13.0-38-generic         memtest86+.bin
abi-4.13.0-39-generic         memtest86+.elf
config-4.13.0-38-generic      memtest86+_multiboot.bin
config-4.13.0-39-generic      retpoline-4.13.0-38-generic
grub                          retpoline-4.13.0-39-generic
initrd.img-4.13.0-36-generic  System.map-4.13.0-38-generic
initrd.img-4.13.0-38-generic  System.map-4.13.0-39-generic
initrd.img-4.13.0-39-generic  vmlinuz-4.13.0-38-generic
initrd.img-4.4.0-104-generic  vmlinuz-4.13.0-39-generic
lost+found



```

---

### Post by Coriander Redgoat on 2018-04-24
```
coriander@radish1:~$ sudo du -hc --max-depth=1[sudo] password for coriander: 
1.7G	./.local
4.0K	./StarCraft II
119M	./.mozilla
150M	./.dropbox-dist
948K	./.dropbox
20K	./.gnome2
8.0K	./.vscode
2.3M	./lib
20K	./.dbus
768K	./.compiz
9.3M	./.dnx
1.3M	./.macromedia
^C
coriander@radish1:~$ sudo du -hx --max-depth=1 / 2> /dev/null
4.0K	/srv
12K	/media
776K	/tmp
3.9M	/lib32
20K	/snap
15M	/sbin
^C



```

---

### Post by ubfan1 on 2018-04-24
So you did have two old initrd files, initrd.img-4.13.0-36-generic and initrd.img-4.4.0-104-generic which I don't see in the package list.  Delete them and you'll free up 90M or so.  Rerun the du command and let it finish, of interest is /var where the log files get written.

---

### Post by Coriander Redgoat on 2018-04-25
Deleted those 2 files.

Here's the du commands:
```
coriander@radish1:/boot$ sudo du -hx --max-depth=1 / 2> /dev/null

4.0K	/srv
12K	/media
1.2M	/tmp
3.9M	/lib32
20K	/snap
15M	/sbin
6.9G	/usr
369M	/opt
361G	/home
4.0K	/lib64
4.0K	/mnt
188K	/root
732M	/lib
18M	/etc
3.6G	/var
16K	/lost+found
24K	/.Trash
13M	/bin
4.0K	/cdrom
4.6M	/libx32
372G	/


coriander@radish1:/boot$ sudo du -hc --max-depth=1


6.9M	./grub
12K	./lost+found
143M	.
143M	total



```

---

