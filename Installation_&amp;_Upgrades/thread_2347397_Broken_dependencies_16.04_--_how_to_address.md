---
title: "Broken dependencies 16.04 -- how to address"
date: 2016-12-24
forum: Installation &amp; Upgrades
---

### Post by Haven_McClure on 2016-12-24
I am running into a problem with broken dependencies on my installation of Ubuntu Studio 16.04 that is similar to one I had solved in a thread from a year and a half ago .  The thread is [here]("https://ubuntuforums.org/showthread.php?t=2283287").  It turns out I am running into almost the exact same issue as before--I am not able to install updates because the /boot partition is completely full.  A lot of it (perhaps all of it?) has to do with several kernels being partially installed.  
-
```
liberation@liberation-Lenovo-Z40-70:~$ df -h
Filesystem                           Size  Used Avail Use% Mounted on
udev                                 3.9G     0  3.9G   0% /dev
tmpfs                                788M  9.6M  778M   2% /run
/dev/mapper/ubuntu--studio--vg-root  450G  335G   93G  79% /
tmpfs                                3.9G  224K  3.9G   1% /dev/shm
tmpfs                                5.0M  4.0K  5.0M   1% /run/lock
tmpfs                                3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/sda2                            473M  463M     0 100% /boot
/dev/sda1                            511M  3.6M  508M   1% /boot/efi
tmpfs                                788M   40K  788M   1% /run/user/1000
/home/liberation/.Private            450G  335G   93G  79% /home/liberation
liberation@liberation-Lenovo-Z40-70:~$ df -i
Filesystem                            Inodes  IUsed    IFree IUse% Mounted on
udev                                 1002672    601  1002071    1% /dev
tmpfs                                1008080    897  1007183    1% /run
/dev/mapper/ubuntu--studio--vg-root 29949952 742837 29207115    3% /
tmpfs                                1008080      7  1008073    1% /dev/shm
tmpfs                                1008080      6  1008074    1% /run/lock
tmpfs                                1008080     16  1008064    1% /sys/fs/cgroup
/dev/sda2                             124928    333   124595    1% /boot
/dev/sda1                                  0      0        0     - /boot/efi
tmpfs                                1008080     24  1008056    1% /run/user/1000
/home/liberation/.Private           29949952 742837 29207115    3% /home/liberation

liberation@liberation-Lenovo-Z40-70:~$ dpkg -l | grep linux-
ii  ladspa-sdk                                    1.13-2                                                      amd64        sample tools for linux-audio-dev plugin architecture
ii  linux-base                                    4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                                1.157.5                                                     all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-21                        4.4.0-21.37                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-lowlatency             4.4.0-21.37                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-34                        4.4.0-34.53                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-34-lowlatency             4.4.0-34.53                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-36                        4.4.0-36.55                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-lowlatency             4.4.0-36.55                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-38                        4.4.0-38.57                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-lowlatency             4.4.0-38.57                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-42                        4.4.0-42.62                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-lowlatency             4.4.0-42.62                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45                        4.4.0-45.66                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-lowlatency             4.4.0-45.66                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47                        4.4.0-47.68                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-lowlatency             4.4.0-47.68                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-51                        4.4.0-51.72                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-lowlatency             4.4.0-51.72                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53                        4.4.0-53.74                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-lowlatency             4.4.0-53.74                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-57                        4.4.0-57.78                                                 all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-57-lowlatency             4.4.0-57.78                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-lowlatency                      4.4.0.57.60                                                 amd64        lowlatency Linux kernel headers
ii  linux-image-4.4.0-21-lowlatency               4.4.0-21.37                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-34-lowlatency               4.4.0-34.53                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-lowlatency               4.4.0-36.55                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-lowlatency               4.4.0-38.57                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-lowlatency               4.4.0-42.62                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-lowlatency               4.4.0-45.66                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-lowlatency               4.4.0-47.68                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-lowlatency               4.4.0-51.72                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-lowlatency               4.4.0-53.74                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-lowlatency                        4.4.0.57.60                                                 amd64        lowlatency Linux kernel image
iU  linux-libc-dev:amd64                          4.4.0-57.78                                                 amd64        Linux Kernel Headers for development
iU  linux-lowlatency                              4.4.0.57.60                                                 amd64        Complete lowlatency Linux kernel
ii  linux-sound-base                              1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems


```

So naturally, the first thing I did was to walk through that thread. 

I got to the point in the old thread where I was told to do the following;

```


*********THESE ARE INSTRUCTIONS FROM AN OLD THREAD IN JUNE 2015--NOT SOMETHING ATTEMPTED NOW************
sudo dpkg -P linux-image-extra-3.16.0-{29,33,36,37}-generic
sudo dpkg -P linux-signed-image-3.16.0-{33,36,37}-generic
sudo dpkg -P linux-image-3.16.0-{29,33}-lowlatency
sudo dpkg -P linux-headers-3.16.0-{33,36,37}-generic
sudo dpkg -P linux-headers-3.16.0-{29,33,36,37}-lowlatency
sudo dpkg -P linux-headers-3.16.0-{29,33,36,37}
```
 
But now I'm dealing with different kernels, and since I'm getting down and dirty with kernel work, I figure I should get some guidance.  

I suppose I could do a system reinstall, but I have misgiving about doing so.  Though I'm open to being persuaded. 

Haven

---

### Post by mörgæs on 2016-12-25
Is this the same install as the one in the old thread, that is a system which has been upgraded several times and repeatedly with problems?

---

### Post by ian-weisser on 2016-12-25
Basic maintenance is important, especially when you use LVM/encryption.
This maintenance is *much* easier if you do it before the /boot partition is full.

1) Run the following commands to gather the data you need, 
```
uname -r
ls -l /boot
dpkg -l | grep linux-image
dpkg -l | grep linux-headers
```

2) Sit down with a pencil and paper. Figure out which kernel packages should be removed.
- 'rc' packages are already removed
- Don't remove the currently running kernel
- Don't remove the newest kernel
- If you remove a kernel, remove the corresponding -signed, -extra, and -headers packages, too.

3) Use dpkg, like you did before, to remove the packages.

4) Test your package manager to ensure proper function:
```
sudo apt-get update           // Change all 'apt-get' to 'apt' in 16.04 and newer
sudo apt-get upgrade
```

If you wish us to look over and validate your estimate of what needs to be removed, we're happy to help.

Like brushing your teeth or changing your car's oil, this is a simple job that needs to be done by you regularly.
In your case, seems like annually.

---

### Post by Haven_McClure on 2016-12-31
It appears we're making some progress. Did get some errors when I tried to upgrade, though.  

My errors were coming off a clean install of 16.04.  I'm resisting upgrading to short-term versions nowadays. 

```
liberation@liberation-Lenovo-Z40-70:~$ uname -r
4.4.0-53-lowlatency
liberation@liberation-Lenovo-Z40-70:~$ ls -l /boot
total 463723
-rw-r--r-- 1 root root  1240262 Apr 18  2016 abi-4.4.0-21-lowlatency
-rw-r--r-- 1 root root  1242308 Jul 27 17:57 abi-4.4.0-34-lowlatency
-rw-r--r-- 1 root root  1242645 Aug 11 15:57 abi-4.4.0-36-lowlatency
-rw-r--r-- 1 root root  1242947 Sep  6 15:12 abi-4.4.0-38-lowlatency
-rw-r--r-- 1 root root  1243386 Oct  7 22:49 abi-4.4.0-42-lowlatency
-rw-r--r-- 1 root root  1243386 Oct 19 12:42 abi-4.4.0-45-lowlatency
-rw-r--r-- 1 root root  1243771 Oct 26 18:17 abi-4.4.0-47-lowlatency
-rw-r--r-- 1 root root  1244164 Nov 24 16:03 abi-4.4.0-51-lowlatency
-rw-r--r-- 1 root root  1244164 Dec  2 14:30 abi-4.4.0-53-lowlatency
-rw-r--r-- 1 root root   189342 Apr 18  2016 config-4.4.0-21-lowlatency
-rw-r--r-- 1 root root   189606 Jul 27 17:57 config-4.4.0-34-lowlatency
-rw-r--r-- 1 root root   189626 Aug 11 15:57 config-4.4.0-36-lowlatency
-rw-r--r-- 1 root root   189662 Sep  6 15:12 config-4.4.0-38-lowlatency
-rw-r--r-- 1 root root   189690 Oct  7 22:49 config-4.4.0-42-lowlatency
-rw-r--r-- 1 root root   189690 Oct 19 12:42 config-4.4.0-45-lowlatency
-rw-r--r-- 1 root root   189739 Oct 26 18:17 config-4.4.0-47-lowlatency
-rw-r--r-- 1 root root   189807 Nov 24 16:03 config-4.4.0-51-lowlatency
-rw-r--r-- 1 root root   189807 Dec  2 14:30 config-4.4.0-53-lowlatency
drwx------ 3 root root     4096 Dec 31  1969 efi
drwxr-xr-x 5 root root     1024 Dec  6 02:58 grub
-rw-r--r-- 1 root root 39126382 Aug 15 16:08 initrd.img-4.4.0-21-lowlatency
-rw-r--r-- 1 root root 39136389 Aug 15 16:15 initrd.img-4.4.0-34-lowlatency
-rw-r--r-- 1 root root 39139941 Aug 31 02:24 initrd.img-4.4.0-36-lowlatency
-rw-r--r-- 1 root root 39142551 Sep 29 21:09 initrd.img-4.4.0-38-lowlatency
-rw-r--r-- 1 root root 40817403 Oct 10 19:26 initrd.img-4.4.0-42-lowlatency
-rw-r--r-- 1 root root 40821678 Nov 10 21:17 initrd.img-4.4.0-45-lowlatency
-rw-r--r-- 1 root root 40862324 Nov 12 16:21 initrd.img-4.4.0-47-lowlatency
-rw-r--r-- 1 root root 40915503 Nov 30 10:11 initrd.img-4.4.0-51-lowlatency
-rw-r--r-- 1 root root 40913369 Dec  6 02:58 initrd.img-4.4.0-53-lowlatency
drwx------ 2 root root    12288 Aug 15 10:04 lost+found
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  3855144 Apr 18  2016 System.map-4.4.0-21-lowlatency
-rw------- 1 root root  3868069 Jul 27 17:57 System.map-4.4.0-34-lowlatency
-rw------- 1 root root  3869254 Aug 11 15:57 System.map-4.4.0-36-lowlatency
-rw------- 1 root root  3870754 Sep  6 15:12 System.map-4.4.0-38-lowlatency
-rw------- 1 root root  3871320 Oct  7 22:49 System.map-4.4.0-42-lowlatency
-rw------- 1 root root  3871320 Oct 19 12:42 System.map-4.4.0-45-lowlatency
-rw------- 1 root root  3874899 Oct 26 18:17 System.map-4.4.0-47-lowlatency
-rw------- 1 root root  3875828 Nov 24 16:03 System.map-4.4.0-51-lowlatency
-rw------- 1 root root  3875828 Dec  2 14:30 System.map-4.4.0-53-lowlatency
-rw-r--r-- 1 root root  7046944 Jul  2 07:01 vmlinuz-4.4.0-21-lowlatency
-rw------- 1 root root  7079136 Jul 27 17:57 vmlinuz-4.4.0-34-lowlatency
-rw------- 1 root root  7081536 Aug 11 15:57 vmlinuz-4.4.0-36-lowlatency
-rw------- 1 root root  7083008 Sep  6 15:12 vmlinuz-4.4.0-38-lowlatency
-rw------- 1 root root  7085088 Oct  7 22:49 vmlinuz-4.4.0-42-lowlatency
-rw------- 1 root root  7085408 Oct 19 12:42 vmlinuz-4.4.0-45-lowlatency
-rw------- 1 root root  7095936 Oct 26 18:17 vmlinuz-4.4.0-47-lowlatency
-rw------- 1 root root  7097968 Nov 24 16:03 vmlinuz-4.4.0-51-lowlatency
-rw------- 1 root root  7097456 Dec  2 14:30 vmlinuz-4.4.0-53-lowlatency
liberation@liberation-Lenovo-Z40-70:~$ dpkg -l | grep linux-image
ii  linux-image-4.4.0-21-lowlatency               4.4.0-21.37                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-34-lowlatency               4.4.0-34.53                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-36-lowlatency               4.4.0-36.55                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-38-lowlatency               4.4.0-38.57                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-42-lowlatency               4.4.0-42.62                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-45-lowlatency               4.4.0-45.66                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-47-lowlatency               4.4.0-47.68                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-51-lowlatency               4.4.0-51.72                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-53-lowlatency               4.4.0-53.74                                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
iU  linux-image-lowlatency                        4.4.0.57.60                                                 amd64        lowlatency Linux kernel image
liberation@liberation-Lenovo-Z40-70:~$ dpkg -l | grep linux-headers
ii  linux-headers-4.4.0-21                        4.4.0-21.37                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-21-lowlatency             4.4.0-21.37                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-34                        4.4.0-34.53                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-34-lowlatency             4.4.0-34.53                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-36                        4.4.0-36.55                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-36-lowlatency             4.4.0-36.55                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-38                        4.4.0-38.57                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-38-lowlatency             4.4.0-38.57                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-42                        4.4.0-42.62                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-42-lowlatency             4.4.0-42.62                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-45                        4.4.0-45.66                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-45-lowlatency             4.4.0-45.66                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-47                        4.4.0-47.68                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-47-lowlatency             4.4.0-47.68                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-51                        4.4.0-51.72                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-51-lowlatency             4.4.0-51.72                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-53                        4.4.0-53.74                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-53-lowlatency             4.4.0-53.74                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-4.4.0-57                        4.4.0-57.78                                                 all          Header files related to Linux kernel version 4.4.0
iU  linux-headers-4.4.0-57-lowlatency             4.4.0-57.78                                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
iU  linux-headers-lowlatency                      4.4.0.57.60                                                 amd64        lowlatency Linux kernel headers
liberation@liberation-Lenovo-Z40-70:~$ sudo dpkg _P linux-image 4.4.0-{21,34,36,38,42,45,47,51,53}-generic
[sudo] password for liberation: 
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
liberation@liberation-Lenovo-Z40-70:~$ sudo dpkg _P linux-image 4.4.0-{21,34,36,38,42,45,47,51,53}-generic
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
liberation@liberation-Lenovo-Z40-70:~$ sudo dpkg _P linux-image 4.4.0-{21,34,36,38,42,45,47,51,53}-generic
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
liberation@liberation-Lenovo-Z40-70:~$ sudo dpkg -P linux-image-4.4.0-{21,34,36,38,42,45,47,51}-generic
dpkg: warning: ignoring request to remove linux-image-4.4.0-21-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.4.0-34-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.4.0-36-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.4.0-38-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.4.0-42-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.4.0-45-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.4.0-47-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-4.4.0-51-generic which isn't installed
liberation@liberation-Lenovo-Z40-70:~$ sudo dpkg -P linux-image-4.4.0-{21,34,36,42,45,47,51}-lowlatency
(Reading database ... 565812 files and directories currently installed.)
Removing linux-image-4.4.0-21-lowlatency (4.4.0-21.37) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-21-lowlatency /boot/vmlinuz-4.4.0-21-lowlatency
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-21-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-21-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-21-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod......

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-21-lowlatency /boot/vmlinuz-4.4.0-21-lowlatency
update-initramfs: Deleting /boot/initrd.img-4.4.0-21-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-21-lowlatency /boot/vmlinuz-4.4.0-21-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-51-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-51-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-47-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-47-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-45-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-45-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-42-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-42-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-38-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-38-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-36-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-36-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-34-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-34-lowlatency
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-4.4.0-21-lowlatency (4.4.0-21.37) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-21-lowlatency /boot/vmlinuz-4.4.0-21-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-21-lowlatency /boot/vmlinuz-4.4.0-21-lowlatency
Removing linux-image-4.4.0-34-lowlatency (4.4.0-34.53) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-34-lowlatency /boot/vmlinuz-4.4.0-34-lowlatency
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-34-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-34-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-34-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod.........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-34-lowlatency /boot/vmlinuz-4.4.0-34-lowlatency
update-initramfs: Deleting /boot/initrd.img-4.4.0-34-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-34-lowlatency /boot/vmlinuz-4.4.0-34-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-51-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-51-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-47-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-47-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-45-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-45-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-42-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-42-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-38-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-38-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-36-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-36-lowlatency
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-4.4.0-34-lowlatency (4.4.0-34.53) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-34-lowlatency /boot/vmlinuz-4.4.0-34-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-34-lowlatency /boot/vmlinuz-4.4.0-34-lowlatency
Removing linux-image-4.4.0-36-lowlatency (4.4.0-36.55) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-36-lowlatency /boot/vmlinuz-4.4.0-36-lowlatency
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-36-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-36-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-36-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-lowlatency /boot/vmlinuz-4.4.0-36-lowlatency
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-lowlatency /boot/vmlinuz-4.4.0-36-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-51-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-51-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-47-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-47-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-45-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-45-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-42-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-42-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-38-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-38-lowlatency
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-4.4.0-36-lowlatency (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-lowlatency /boot/vmlinuz-4.4.0-36-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-lowlatency /boot/vmlinuz-4.4.0-36-lowlatency
Removing linux-image-4.4.0-42-lowlatency (4.4.0-42.62) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-42-lowlatency /boot/vmlinuz-4.4.0-42-lowlatency
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-42-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-42-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-42-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-lowlatency /boot/vmlinuz-4.4.0-42-lowlatency
update-initramfs: Deleting /boot/initrd.img-4.4.0-42-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-lowlatency /boot/vmlinuz-4.4.0-42-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-51-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-51-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-47-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-47-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-45-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-45-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-38-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-38-lowlatency
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-4.4.0-42-lowlatency (4.4.0-42.62) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-42-lowlatency /boot/vmlinuz-4.4.0-42-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-42-lowlatency /boot/vmlinuz-4.4.0-42-lowlatency
Removing linux-image-4.4.0-45-lowlatency (4.4.0-45.66) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-45-lowlatency /boot/vmlinuz-4.4.0-45-lowlatency
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-45-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-45-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-45-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-lowlatency /boot/vmlinuz-4.4.0-45-lowlatency
update-initramfs: Deleting /boot/initrd.img-4.4.0-45-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-lowlatency /boot/vmlinuz-4.4.0-45-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-51-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-51-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-47-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-47-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-38-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-38-lowlatency
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-4.4.0-45-lowlatency (4.4.0-45.66) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-45-lowlatency /boot/vmlinuz-4.4.0-45-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-45-lowlatency /boot/vmlinuz-4.4.0-45-lowlatency
Removing linux-image-4.4.0-47-lowlatency (4.4.0-47.68) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-47-lowlatency /boot/vmlinuz-4.4.0-47-lowlatency
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-47-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-47-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-47-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-47-lowlatency /boot/vmlinuz-4.4.0-47-lowlatency
update-initramfs: Deleting /boot/initrd.img-4.4.0-47-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-47-lowlatency /boot/vmlinuz-4.4.0-47-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-51-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-51-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-38-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-38-lowlatency
Adding boot menu entry for EFI firmware configuration
done
Purging configuration files for linux-image-4.4.0-47-lowlatency (4.4.0-47.68) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-47-lowlatency /boot/vmlinuz-4.4.0-47-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-47-lowlatency /boot/vmlinuz-4.4.0-47-lowlatency
Removing linux-image-4.4.0-51-lowlatency (4.4.0-51.72) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 4.4.0-51-lowlatency /boot/vmlinuz-4.4.0-51-lowlatency
dkms: removing: bcmwl 6.30.223.248+bdcom (4.4.0-51-lowlatency) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  4.4.0-51-lowlatency (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/4.4.0-51-lowlatency/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod........

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-51-lowlatency /boot/vmlinuz-4.4.0-51-lowlatency
update-initramfs: Deleting /boot/initrd.img-4.4.0-51-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-51-lowlatency /boot/vmlinuz-4.4.0-51-lowlatency
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-53-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-53-lowlatency
Found linux image: /boot/vmlinuz-4.4.0-38-lowlatency
Found initrd image: /boot/initrd.img-4.4.0-38-lowlatency
Adding boot menu entry for EFI firmware configuration
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-4.4.0-51-lowlatency (4.4.0-51.72) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-51-lowlatency /boot/vmlinuz-4.4.0-51-lowlatency
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-51-lowlatency /boot/vmlinuz-4.4.0-51-lowlatency
liberation@liberation-Lenovo-Z40-70:~$ sudo dpkg _P linux-headers-4.4.0-{21,34,36,38,42,45,47,51}-lowlatency
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
liberation@liberation-Lenovo-Z40-70:~$ sudo dpkg -P linux-headers-4.4.0-{21,34,35,38,42,45,47,51}-lowlatency
(Reading database ... 526701 files and directories currently installed.)
Removing linux-headers-4.4.0-21-lowlatency (4.4.0-21.37) ...
Removing linux-headers-4.4.0-34-lowlatency (4.4.0-34.53) ...
dpkg: warning: ignoring request to remove linux-headers-4.4.0-35-lowlatency which isn't installed
Removing linux-headers-4.4.0-38-lowlatency (4.4.0-38.57) ...
Removing linux-headers-4.4.0-42-lowlatency (4.4.0-42.62) ...
Removing linux-headers-4.4.0-45-lowlatency (4.4.0-45.66) ...
Removing linux-headers-4.4.0-47-lowlatency (4.4.0-47.68) ...
Removing linux-headers-4.4.0-51-lowlatency (4.4.0-51.72) ...
liberation@liberation-Lenovo-Z40-70:~$ sudo dpkg -P linux-headers-4.4.0-{21,34,36,38,42,45,47,51}
(Reading database ... 458482 files and directories currently installed.)
Removing linux-headers-4.4.0-21 (4.4.0-21.37) ...
Removing linux-headers-4.4.0-34 (4.4.0-34.53) ...
dpkg: dependency problems prevent removal of linux-headers-4.4.0-36:
 linux-headers-4.4.0-36-lowlatency depends on linux-headers-4.4.0-36.

dpkg: error processing package linux-headers-4.4.0-36 (--purge):
 dependency problems - not removing
Removing linux-headers-4.4.0-38 (4.4.0-38.57) ...
Removing linux-headers-4.4.0-42 (4.4.0-42.62) ...
Removing linux-headers-4.4.0-45 (4.4.0-45.66) ...
Removing linux-headers-4.4.0-47 (4.4.0-47.68) ...
Removing linux-headers-4.4.0-51 (4.4.0-51.72) ...
Errors were encountered while processing:
 linux-headers-4.4.0-36
liberation@liberation-Lenovo-Z40-70:~$ sudo dpkg -P linux-image 4.4.0-{21,34,36,38,42,45,47,51}
dpkg: warning: ignoring request to remove linux-image which isn't installed
dpkg: warning: ignoring request to remove 4.4.0-21 which isn't installed
dpkg: warning: ignoring request to remove 4.4.0-34 which isn't installed
dpkg: warning: ignoring request to remove 4.4.0-36 which isn't installed
dpkg: warning: ignoring request to remove 4.4.0-38 which isn't installed
dpkg: warning: ignoring request to remove 4.4.0-42 which isn't installed
dpkg: warning: ignoring request to remove 4.4.0-45 which isn't installed
dpkg: warning: ignoring request to remove 4.4.0-47 which isn't installed
dpkg: warning: ignoring request to remove 4.4.0-51 which isn't installed
liberation@liberation-Lenovo-Z40-70:~$ sudo apt update
Hit:1 http://us.archive.ubuntu.com/ubuntu xenial InRelease
Get:2 http://us.archive.ubuntu.com/ubuntu xenial-updates InRelease [102 kB]    
Get:3 http://security.ubuntu.com/ubuntu xenial-security InRelease [102 kB]     
Hit:4 http://ppa.launchpad.net/anonbeat/guayadeque/ubuntu xenial InRelease     
Hit:5 http://ppa.launchpad.net/eugenesan/ppa/ubuntu xenial InRelease           
Get:6 http://us.archive.ubuntu.com/ubuntu xenial-backports InRelease [102 kB]  
Get:7 http://us.archive.ubuntu.com/ubuntu xenial-updates/main amd64 DEP-11 Metadata [303 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu xenial-updates/main DEP-11 64x64 Icons [190 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe amd64 DEP-11 Metadata [121 kB]
Get:10 http://security.ubuntu.com/ubuntu xenial-security/main amd64 DEP-11 Metadata [68.2 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu xenial-updates/universe DEP-11 64x64 Icons [145 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu xenial-updates/multiverse amd64 DEP-11 Metadata [2,516 B]
Get:13 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 Packages [4,404 B]
Get:14 http://us.archive.ubuntu.com/ubuntu xenial-backports/main i386 Packages [4,404 B]
Get:15 http://us.archive.ubuntu.com/ubuntu xenial-backports/main Translation-en [3,124 B]
Get:16 http://us.archive.ubuntu.com/ubuntu xenial-backports/main amd64 DEP-11 Metadata [208 B]
Get:17 http://us.archive.ubuntu.com/ubuntu xenial-backports/universe amd64 DEP-11 Metadata [212 B]
Get:18 http://us.archive.ubuntu.com/ubuntu xenial-backports/multiverse amd64 DEP-11 Metadata [216 B]
Get:19 http://security.ubuntu.com/ubuntu xenial-security/main DEP-11 64x64 Icons [43.1 kB]
Get:20 http://security.ubuntu.com/ubuntu xenial-security/universe amd64 DEP-11 Metadata [19.4 kB]
Get:21 http://security.ubuntu.com/ubuntu xenial-security/multiverse amd64 DEP-11 Metadata [212 B]
Fetched 1,211 kB in 1s (981 kB/s)   
AppStream cache update completed, but some metadata was ignored due to errors.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
45 packages can be upgraded. Run 'apt list --upgradable' to see them.
liberation@liberation-Lenovo-Z40-70:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-lowlatency : Depends: linux-image-4.4.0-57-lowlatency but it is not installed
E: Unmet dependencies. Try using -f.
liberation@liberation-Lenovo-Z40-70:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-lowlatency : Depends: linux-image-4.4.0-57-lowlatency but it is not installed
E: Unmet dependencies. Try using -f.
liberation@liberation-Lenovo-Z40-70:~$ 


```


> **ian-weisser said:**
> Basic maintenance is important, especially when you use LVM/encryption.
This maintenance is *much* easier if you do it before the /boot partition is full.

1) Run the following commands to gather the data you need, 
```
uname -r
ls -l /boot
dpkg -l | grep linux-image
dpkg -l | grep linux-headers
```

2) Sit down with a pencil and paper. Figure out which kernel packages should be removed.
- 'rc' packages are already removed
- Don't remove the currently running kernel
- Don't remove the newest kernel
- If you remove a kernel, remove the corresponding -signed, -extra, and -headers packages, too.

3) Use dpkg, like you did before, to remove the packages.

4) Test your package manager to ensure proper function:
```
sudo apt-get update           // Change all 'apt-get' to 'apt' in 16.04 and newer
sudo apt-get upgrade
```

If you wish us to look over and validate your estimate of what needs to be removed, we're happy to help.

Like brushing your teeth or changing your car's oil, this is a simple job that needs to be done by you regularly.
In your case, seems like annually.

---

### Post by ian-weisser on 2016-12-31
Remember to check your df -h and df -i and ls -l /boot again.

> dpkg: dependency problems prevent removal of linux-headers-4.4.0-36:
 linux-headers-4.4.0-36-lowlatency depends on linux-headers-4.4.0-36.

Remove _both_ packages using either apt or dpkg.



> You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-image-lowlatency : Depends: linux-image-4.4.0-57-lowlatency but it is not installed

Follow the system's advice: sudo apt -f install

---

### Post by Haven_McClure on 2017-01-02
That cleared it up.  The "Do Not Enter" sign alerting me of broken dependencies has also disappeared.  Thanks everyone!  I'm marking this as solved.

---

