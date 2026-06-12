---
title: "Removing Old Kernels"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by Kirkx on 2014-08-21
I always do the updates with the following three commands:

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove

```
 Although <apt-get autoremove> is supposed to remove old kernels, for some reason it didn't work that way on my system and old kernels kept piling up, all the way back to v3.13.0-24.

As I wanted to have only the latest two kernels present I ran the following two commands.

1) Show all installed packages with a name that starts with "linux-" and contains a number:

```
dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -e [0-9]
```

2) Specify the names of all unwanted packages and purge them:

```

sudo apt-get -y purge  linux-headers-3.13.0-24  linux-headers-3.13.0-24-generic  linux-headers-3.13.0-29  linux-headers-3.13.0-29-generic  linux-image-3.13.0-24-generic  linux-image-3.13.0-29-generic  linux-image-extra-3.13.0-24-generic  linux-image-extra-3.13.0-29-generic

```

Here is the result:

[http://i.imgur.com/fS6RrpO.png](http://i.imgur.com/fS6RrpO.png)

I'm wondering if this is a correct method and if I didn't miss anything. The last line on the screenshot (linux-libc-dev:amd64) doesn't belong to a kernel package and must be ignored. As a Linux newbie I wanted to play safe, that's why I decided to enter all kernel names manually on the command line.

There are much more advanced commands available on the web, like the one below, which apparently removes all kernel packages except for the latest one ([http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/](http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/)) :

```

[COLOR=#3366ff][B]dpkg -l 'linux-*' | sed  '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]*  [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
[/B][/COLOR]
```

Following blindly a command like that without understanding what all its parts are actually doing might be a bit risky. I'm aware that you can also delete kernels using Ubuntu Tweak or Synaptic (not a very practical option).

---

### Post by ian-weisser on 2014-08-21
> **Kirkx said:**
> I'm wondering if this is a correct method and if I didn't miss anything.

Correct? Yes.
Miss anything? I don't think so.
I think you did a great job of troubleshooting and resolving the issue.
Your solution is very close to what we have been recommending to other users bitten by a kernel-not-autoremoved bug.

The only additional protection we usually recommend is to ensure you are not accidentally removing the current running kernel.

---

### Post by vasa1 on 2015-03-11
I'm seeing something similar to what Kirkx reported. *sudo apt-get autoremove* (even when run a week after *sudo apt-get update* and *sudo apt-get dist-upgrade*) hasn't been removing older kernel-related files for quite some time. It used to work previously and I can't remember when it stopped working for me.

To give a broad picture of what I have, I ran *dpkg -l linux** instead of Kirkx's specific command. Here's the output:
```
08:12 AM ~ $ dpkg -l linux*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                                 Version                 Architecture            Description
+++-====================================-=======================-=======================-=============================================================================
un  linux-doc-3.13.0                     <none>                  <none>                  (no description available)
ii  linux-firmware                       1.127.11                all                     Firmware for Linux kernel drivers
ii  linux-generic                        3.13.0.46.53            amd64                   Complete Generic Linux kernel and headers
un  linux-headers                        <none>                  <none>                  (no description available)
un  linux-headers-3.0                    <none>                  <none>                  (no description available)
un  linux-headers-3.13.0-32-generic      <none>                  <none>                  (no description available)
ii  linux-headers-3.13.0-39              3.13.0-39.66            all                     Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic      3.13.0-39.66            amd64                   Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
un  linux-headers-3.13.0-40-generic      <none>                  <none>                  (no description available)
un  linux-headers-3.13.0-41-generic      <none>                  <none>                  (no description available)
un  linux-headers-3.13.0-43-generic      <none>                  <none>                  (no description available)
un  linux-headers-3.13.0-44-generic      <none>                  <none>                  (no description available)
ii  linux-headers-3.13.0-45              3.13.0-45.74            all                     Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic      3.13.0-45.74            amd64                   Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-46              3.13.0-46.79            all                     Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic      3.13.0-46.79            amd64                   Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-generic                3.13.0.46.53            amd64                   Generic Linux kernel headers
un  linux-image                          <none>                  <none>                  (no description available)
un  linux-image-3.0                      <none>                  <none>                  (no description available)
rc  linux-image-3.13.0-32-generic        3.13.0-32.57            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic        3.13.0-39.66            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-40-generic        3.13.0-40.69            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-41-generic        3.13.0-41.70            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-43-generic        3.13.0-43.72            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic        3.13.0-44.73            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-45-generic        3.13.0-45.74            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-46-generic        3.13.0-46.79            amd64                   Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic  3.13.0-32.57            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic  3.13.0-39.66            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-40-generic  3.13.0-40.69            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-41-generic  3.13.0-41.70            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-43-generic  3.13.0-43.72            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic  3.13.0-44.73            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-45-generic  3.13.0-45.74            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic  3.13.0-46.79            amd64                   Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                  3.13.0.46.53            amd64                   Generic Linux kernel image
un  linux-initramfs-tool                 <none>                  <none>                  (no description available)
un  linux-kernel-log-daemon              <none>                  <none>                  (no description available)
un  linux-restricted-common              <none>                  <none>                  (no description available)
ii  linux-sound-base                     1.0.25+dfsg-0ubuntu4    all                     base package for ALSA and OSS sound systems
un  linux-source-3.13.0                  <none>                  <none>                  (no description available)
un  linux-tools                          <none>                  <none>                  (no description available)
un  linux32                              <none>                  <none>                  (no description available)
08:14 AM ~ $ 

``` 

I know this thread is several months old and I've read something more recent (although I don't (yet) have a disk space problem): [Updater can't update kernel due to disk space]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2015-January/015284.html").

Also, here's part of the dist-upgrade output I got today:
```
The following packages will be upgraded:
  libpwquality-common libpwquality1 linux-headers-3.13.0-46
  linux-headers-3.13.0-46-generic linux-image-3.13.0-46-generic
  linux-image-extra-3.13.0-46-generic
6 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 61.5 MB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue? [Y/n] 
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libpwquality-common all 1.2.3-1ubuntu1.1 [5,400 B]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libpwquality1 amd64 1.2.3-1ubuntu1.1 [11.7 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-46-generic amd64 3.13.0-46.79 [15.1 MB]
Get:4 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-46 all 3.13.0-46.79 [8,877 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-46-generic amd64 3.13.0-46.79 [707 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.13.0-46-generic amd64 3.13.0-46.79 [36.8 MB]
Fetched 61.5 MB in 15min 10s (67.5 kB/s)                                       
(Reading database ... 177024 files and directories currently installed.)
Preparing to unpack .../libpwquality-common_1.2.3-1ubuntu1.1_all.deb ...
Unpacking libpwquality-common (1.2.3-1ubuntu1.1) over (1.2.3-1ubuntu1) ...
Preparing to unpack .../libpwquality1_1.2.3-1ubuntu1.1_amd64.deb ...
Unpacking libpwquality1:amd64 (1.2.3-1ubuntu1.1) over (1.2.3-1ubuntu1) ...
Preparing to unpack .../linux-image-3.13.0-46-generic_3.13.0-46.79_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-46-generic (3.13.0-46.79) over (3.13.0-46.77) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Preparing to unpack .../linux-headers-3.13.0-46_3.13.0-46.79_all.deb ...
Unpacking linux-headers-3.13.0-46 (3.13.0-46.79) over (3.13.0-46.77) ...
Preparing to unpack .../linux-headers-3.13.0-46-generic_3.13.0-46.79_amd64.deb ...
Unpacking linux-headers-3.13.0-46-generic (3.13.0-46.79) over (3.13.0-46.77) ...
Preparing to unpack .../linux-image-extra-3.13.0-46-generic_3.13.0-46.79_amd64.deb ...
Unpacking linux-image-extra-3.13.0-46-generic (3.13.0-46.79) over (3.13.0-46.77) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Setting up libpwquality-common (1.2.3-1ubuntu1.1) ...
Setting up libpwquality1:amd64 (1.2.3-1ubuntu1.1) ...
Setting up linux-image-3.13.0-46-generic (3.13.0-46.79) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-46.77 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-46.77 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Setting up linux-headers-3.13.0-46 (3.13.0-46.79) ...
Setting up linux-headers-3.13.0-46-generic (3.13.0-46.79) ...
Setting up linux-image-extra-3.13.0-46-generic (3.13.0-46.79) ...
**run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic**
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
07:14 AM ~ $ 
```

Could someone please explain what ```
run-parts: executing /etc/kernel/postinst.d/**apt-auto-removal** 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
```
means? And is it now normal, in 14.04, for *sudo-apt-get autoremove* to no longer remove kernel-related files older than the latest two versions?

Because the code above references **/etc/kernel**, here's what I have: ```
08:26 AM /etc/kernel $ ls -l
total 8
drwxr-xr-x 2 root root 4096 Nov 14 18:06 postinst.d
drwxr-xr-x 2 root root 4096 Jul 23  2014 postrm.d
08:26 AM /etc/kernel $ ls -lR
.:
total 8
drwxr-xr-x 2 root root 4096 Nov 14 18:06 postinst.d
drwxr-xr-x 2 root root 4096 Jul 23  2014 postrm.d

./postinst.d:
total 16
-rwxr-xr-x 1 root root 2824 Apr 10  2014 apt-auto-removal
-rwxr-xr-x 1 root root  858 Jun  1  2012 initramfs-tools
-rwxr-xr-x 1 root root  196 Jul 15  2014 pm-utils
lrwxrwxrwx 1 root root   49 Oct  7 07:49 update-notifier -> /usr/share/update-notifier/notify-reboot-required
-rwxr-xr-x 1 root root  641 May  8  2014 zz-update-grub

./postrm.d:
total 8
-rwxr-xr-x 1 root root 814 Jun  1  2012 initramfs-tools
-rwxr-xr-x 1 root root 641 May  8  2014 zz-update-grub
08:27 AM /etc/kernel $ 
```

---

### Post by BazBear on 2015-03-24
I've been having the same issue vasa1. I'm not sure when this started either, but it seems like several months and several kernel updates. I noticed it some time ago, and have been manually removing the older kernels, but I'm sort of glad to hear it's not just me. For what it's worth, I'm on a 32 bit system, whereas you're on a 64 bit one, so it's apparently not architecturally specific.

---

### Post by ian-weisser on 2015-03-24
> **vasa1 said:**
> Could someone please explain what
```
run-parts: executing /etc/kernel/postinst.d/**apt-auto-removal** 3.13.0-46-generic /boot/vmlinuz-3.13.0-46-generic
```
means? And is it now normal, in 14.04, for *sudo-apt-get autoremove* to no longer remove kernel-related files older than the latest two versions?

/etc/kernel/postinst.d/apt-auto-removal is the script that makes older kenels eligible for autoremoval.
The comments within the script are helpful - minimum of two retained kernels: Current and newly-downloaded. More under certain circumstances. Has not changed.

If your older kernels are not being autoremoved (are ineligible for autoremoval), perhaps a possible apt-marking issue?

---

### Post by Fritz_T_Cat on 2015-07-30
```

[COLOR=#3366ff][B]dpkg -l 'linux-*' | sed  '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]*  [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
[/B][/COLOR]
```

Following blindly a command like that without understanding what all its parts are actually doing might be a bit risky. I'm aware that you can also delete kernels using Ubuntu Tweak or Synaptic (not a very practical option).[/QUOTE]

Exactly. The above script deletes the g++ compiler, among others, since ' linux-libc-dev:amd64' will be included into the purge list

---

### Post by vasa1 on 2015-07-30
> **ian-weisser said:**
> /etc/kernel/postinst.d/apt-auto-removal is the script that makes older kenels eligible for autoremoval.
The comments within the script are helpful - minimum of two retained kernels: Current and newly-downloaded. More under certain circumstances. Has not changed.

If your older kernels are not being autoremoved (are ineligible for autoremoval), perhaps a possible apt-marking issue?
@ian-weisser, thanks! I'm sorry I missed your response. Yes, I now understand the "More under certain circumstances" part.

The default provided works just fine in the light of those comments!

---

### Post by drjoeross on 2015-12-20
> **Kirkx said:**
> I always do the updates with the following three commands:

```

sudo apt-get update
sudo apt-get dist-upgrade
sudo apt-get autoremove

```
 Although <apt-get autoremove> is supposed to remove old kernels, for some reason it didn't work that way on my system and old kernels kept piling up, all the way back to v3.13.0-24.

As I wanted to have only the latest two kernels present I ran the following two commands.

1) Show all installed packages with a name that starts with "linux-" and contains a number:

```
dpkg -l linux-* | awk '/^ii/{ print $2 }' | grep -e [0-9]
```

2) Specify the names of all unwanted packages and purge them:

```

sudo apt-get -y purge  linux-headers-3.13.0-24  linux-headers-3.13.0-24-generic  linux-headers-3.13.0-29  linux-headers-3.13.0-29-generic  linux-image-3.13.0-24-generic  linux-image-3.13.0-29-generic  linux-image-extra-3.13.0-24-generic  linux-image-extra-3.13.0-29-generic

```

Here is the result:

[http://i.imgur.com/fS6RrpO.png](http://i.imgur.com/fS6RrpO.png)

I'm wondering if this is a correct method and if I didn't miss anything. The last line on the screenshot (linux-libc-dev:amd64) doesn't belong to a kernel package and must be ignored. As a Linux newbie I wanted to play safe, that's why I decided to enter all kernel names manually on the command line.

There are much more advanced commands available on the web, like the one below, which apparently removes all kernel packages except for the latest one ([http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/](http://ubuntugenius.wordpress.com/2011/01/08/ubuntu-cleanup-how-to-remove-all-unused-linux-kernel-headers-images-and-modules/)) :

```

[COLOR=#3366ff][B]dpkg -l 'linux-*' | sed  '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]*  [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purge
[/B][/COLOR]
```

Following blindly a command like that without understanding what all its parts are actually doing might be a bit risky. I'm aware that you can also delete kernels using Ubuntu Tweak or Synaptic (not a very practical option).

I tried this after verifing that it did not list my current OS for deletion.  It still destroyed my os and I had to reinstall.  UBUNTU Really needs to fix this stupid issue with the boot partition being full!  
Joe

---

### Post by ian-weisser on 2015-12-20
If you have been affected by this issue, then see [LP #1357093]("https://bugs.launchpad.net/bugs/1357093") and click the 'affects me too' link at the top of the bug report.
Destroying your system using shell voodoo is not neccessary.

---

### Post by yoshii on 2015-12-21
there's a manual way of removing old kernels using synaptic, but i forget how.  it involves using the search command to list all entries with a certain text.  sorry i dont remember any more than that.

---

