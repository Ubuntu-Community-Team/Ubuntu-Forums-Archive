---
title: "Ubuntu 14.10 doesn't boot into 3.16 kernel but boots into 3.14"
date: 2014-10-31
forum: Installation &amp; Upgrades
---

### Post by sp40140 on 2014-10-31
I was running 14.04 64 before 14.10 was released. And the latest in the update channel was 3.13. I had manually installed 3.14 kernel which I picked up from ubuntu stable kernel site. I had to test couple of things. not relevent at this point. I was booting 3.14 without issues. and grub had entries for previous 3.13 kernles as well.
Then 14.10 was released. Few days later it popped up in my update channel. I upgraded to 14.10. No errors during upgrade. 
But now my machine boots into 3.14 instead of 3.16 which came with 14.10.
I know it's installed as I can see the 3.16 version as installed in synaptic. 
But grub has entries fro just 3.14 and 3.14 recovery. 

How do I make grub scan for new versions of kernel and boot into latest by default?

If it matters: I am running HP elitebook core i7 6 gigs ram. 64 bit 14.10 Ubuntu.

I have run update-grub2. But it doesn't locate new kernel. Here is the output from update-grub2
sudo update-grub2
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.14.0-031400-generic
Found initrd image: /boot/initrd.img-3.14.0-031400-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1 ---- This is dual boot windows on partition on my main HD.
Found Windows 7 (loader) on /dev/sdb1 ---- This is dual boot windows on partition on my secondary HD. Have very specific user case and install.
Found Ubuntu 14.04 LTS (14.04) on /dev/sdb6 ---- This is second Ubuntu install on partition on my secondary HD. Have very specific user case and install.
done


The reason I would like to move to 3.16 is that some applications are giving me trouble with 3.14 kernel and 14.10 Ubuntu. Example : VMWare player. It loactes the windows install. launches it but when I try to capture mouse / keyboard.. my system becomes almost unresponsive. I am almost certain that it's caused by this unusual kernel which I installed manually.
So, I need to sort this out.

---

### Post by sp40140 on 2014-11-03
Bump.. Please help

---

### Post by phidia on 2014-11-03
Having used grub for a long time I'm not as versed in grub2 so I'm including a link to the [man pages]("http://www.gnu.org/software/grub/manual/grub.html"). 
I think you might want to try booting from the grub2 cl and also commenting out the 3.14 kernel. That's my best guess anyway.
Hope that helps

---

### Post by Bucky Ball on 2014-11-04
> **sp40140 said:**
> Bump.. Please help

Be aware that we are all volunteers here. If someone is around that can help you, they would be helping you. A simple 'bump' will suffice and that will take your thread to the top of the new posts search list. Good luck. ;)

---

### Post by Doug S on 2014-11-04
Please provide the output for these commands:```
ls -l /boot
dpkg -l | grep linux-
```For example:```
doug@s15:~/temp$ [COLOR=#ff0000]ls -l /boot[/COLOR]
total 174071
-rw-r--r-- 1 root root  1164489 Sep 22 15:24 abi-3.13.0-37-generic
-rw-r--r-- 1 root root  1164547 Oct 28 07:25 abi-3.13.0-39-generic
-rw-r--r-- 1 root root  1216834 Oct 19 18:54 abi-3.18.0-031800rc1-generic
-rw-r--r-- 1 root root  1220875 Nov  2 15:47 abi-3.18.0-031800rc3-generic
-rw-r--r-- 1 root root   165712 Sep 22 15:24 config-3.13.0-37-generic
-rw-r--r-- 1 root root   165712 Oct 28 07:25 config-3.13.0-39-generic
-rw-r--r-- 1 root root   174733 Oct 19 18:54 config-3.18.0-031800rc1-generic
-rw-r--r-- 1 root root   174679 Nov  2 15:47 config-3.18.0-031800rc3-generic
-rw-r--r-- 1 root root   174581 Nov  2 17:42 config-3.18.0-rc3-250
drwxr-xr-x 5 root root     5120 Nov  3 12:12 grub
-rw-r--r-- 1 root root 24886043 Oct  8 16:16 initrd.img-3.13.0-37-generic
-rw-r--r-- 1 root root 24887782 Nov  3 12:12 initrd.img-3.13.0-39-generic
-rw-r--r-- 1 root root 24335418 Oct 20 07:48 initrd.img-3.18.0-031800rc1-generic
-rw-r--r-- 1 root root 24411061 Nov  2 17:12 initrd.img-3.18.0-031800rc3-generic
-rw-r--r-- 1 root root 24147299 Nov  2 21:00 initrd.img-3.18.0-rc3-250
drwxr-xr-x 2 root root    12288 Mar 14  2012 lost+found
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3386945 Sep 22 15:24 System.map-3.13.0-37-generic
-rw------- 1 root root  3386936 Oct 28 07:25 System.map-3.13.0-39-generic
-rw------- 1 root root  3689618 Oct 19 18:54 System.map-3.18.0-031800rc1-generic
-rw------- 1 root root  3676096 Nov  2 15:47 System.map-3.18.0-031800rc3-generic
-rw-r--r-- 1 root root  3524260 Nov  2 17:42 System.map-3.18.0-rc3-250
-rw------- 1 root root  5808832 Sep 22 15:24 vmlinuz-3.13.0-37-generic
-rw------- 1 root root  5808544 Oct 28 07:25 vmlinuz-3.13.0-39-generic
-rw------- 1 root root  6507792 Oct 19 18:54 vmlinuz-3.18.0-031800rc1-generic
-rw------- 1 root root  6491024 Nov  2 15:47 vmlinuz-3.18.0-031800rc3-generic
-rw-r--r-- 1 root root  6391536 Nov  2 17:42 vmlinuz-3.18.0-rc3-250
doug@s15:~/temp$ [COLOR=#ff0000]dpkg -l | grep linux-[/COLOR]
ii  linux-firmware                         1.127.7                              all          Firmware for Linux kernel drivers
ii  linux-firmware-image                   3.11.0-rc6-31                        amd64        Linux kernel firmware, version 3.11.0-rc6
ii  linux-generic                          3.13.0.39.46                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-37                3.13.0-37.64                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-37-generic        3.13.0-37.64                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-39                3.13.0-39.66                         all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-39-generic        3.13.0-39.66                         amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.18.0-031800rc1         3.18.0-031800rc1.201410192135        all          Header files related to Linux kernel version 3.18.0
ii  linux-headers-3.18.0-031800rc1-generic 3.18.0-031800rc1.201410192135        amd64        Linux kernel headers for version 3.18.0 on 64 bit x86 SMP
ii  linux-headers-3.18.0-031800rc3         3.18.0-031800rc3.201411022335        all          Header files related to Linux kernel version 3.18.0
ii  linux-headers-3.18.0-031800rc3-generic 3.18.0-031800rc3.201411022335        amd64        Linux kernel headers for version 3.18.0 on 64 bit x86 SMP
ii  linux-headers-3.18.0-rc3-250           3.18.0-rc3-250-171                   amd64        Linux kernel headers for 3.18.0-rc3-250 on amd64
ii  linux-headers-generic                  3.13.0.39.46                         amd64        Generic Linux kernel headers
ii  linux-headers-server                   3.13.0.39.46                         amd64        Transitional package.
ii  linux-image-3.13.0-37-generic          3.13.0-37.64                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-39-generic          3.13.0-39.66                         amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.18.0-031800rc1-generic   3.18.0-031800rc1.201410192135        amd64        Linux kernel image for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-3.18.0-031800rc3-generic   3.18.0-031800rc3.201411022335        amd64        Linux kernel image for version 3.18.0 on 64 bit x86 SMP
ii  linux-image-3.18.0-rc3-250             3.18.0-rc3-250-171                   amd64        Linux kernel, version 3.18.0-rc3-250
ii  linux-image-extra-3.13.0-37-generic    3.13.0-37.64                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-39-generic    3.13.0-39.66                         amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-generic                    3.13.0.39.46                         amd64        Generic Linux kernel image
ii  linux-image-server                     3.13.0.39.46                         amd64        Transitional package.
ii  linux-libc-dev:amd64                   3.13.0-39.66                         amd64        Linux Kernel Headers for development
ii  linux-server                           3.13.0.39.46                         amd64        Transitional package.
doug@s15:~/temp$
```

---

### Post by sp40140 on 2014-11-04
Doug
ls -l /boot | grep linux- doesn't return anthing as nothing in that folder starting with linux-..
Here is the output of ls -l /boot
```

total 30080
-rw-r--r-- 1 root root  1160927 Mar 31  2014 abi-3.14.0-031400-generic
-rw-r--r-- 1 root root   166001 Mar 31  2014 config-3.14.0-031400-generic
drwxr-xr-x 6 root root     4096 Oct 31 10:54 grub
-rw-r--r-- 1 root root 19461864 Oct 25 14:06 initrd.img-3.14.0-031400-generic
-rw-r--r-- 1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r-- 1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r-- 1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw------- 1 root root  3531914 Mar 31  2014 System.map-3.14.0-031400-generic
-rw------- 1 root root  5926256 Mar 31  2014 vmlinuz-3.14.0-031400-generic

```
dpkg -l | grep linux-
```

ii  linux-firmware                                       1.138                                    all          Firmware for Linux kernel drivers
ii  linux-headers-3.14.0-031400                          3.14.0-031400.201403310035               all          Header files related to Linux kernel version 3.14.0
ii  linux-headers-3.14.0-031400-generic                  3.14.0-031400.201403310035               amd64        Linux kernel headers for version 3.14.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-23                              3.16.0-23.31                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-23-generic                      3.16.0-23.31                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-3.16.0-24                              3.16.0-24.32                             all          Header files related to Linux kernel version 3.16.0
ii  linux-headers-3.16.0-24-generic                      3.16.0-24.32                             amd64        Linux kernel headers for version 3.16.0 on 64 bit x86 SMP
ii  linux-headers-generic                                3.16.0.24.25                             amd64        Generic Linux kernel headers
rc  linux-image-3.11.0-12-generic                        3.11.0-12.19                             amd64        Linux kernel image for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-27-generic                        3.13.0-27.50                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-29-generic                        3.13.0-29.53                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-30-generic                        3.13.0-30.55                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-32-generic                        3.13.0-32.57                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-34-generic                        3.13.0-34.60                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-35-generic                        3.13.0-35.62                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-36-generic                        3.13.0-36.63                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-37-generic                        3.13.0-37.64                             amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.14.0-031400-generic                    3.14.0-031400.201403310035               amd64        Linux kernel image for version 3.14.0 on 64 bit x86 SMP
rc  linux-image-3.16.0-23-generic                        3.16.0-23.31                             amd64        Linux kernel image for version 3.16.0 on 64 bit x86 SMP
rc  linux-image-extra-3.11.0-12-generic                  3.11.0-12.19                             amd64        Linux kernel extra modules for version 3.11.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-27-generic                  3.13.0-27.50                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-29-generic                  3.13.0-29.53                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-30-generic                  3.13.0-30.55                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-32-generic                  3.13.0-32.57                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-34-generic                  3.13.0-34.60                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-35-generic                  3.13.0-35.62                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-36-generic                  3.13.0-36.63                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-37-generic                  3.13.0-37.64                             amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.16.0-23-generic                  3.16.0-23.31                             amd64        Linux kernel extra modules for version 3.16.0 on 64 bit x86 SMP
ii  linux-libc-dev:amd64                                 3.16.0-24.32                             amd64        Linux Kernel Headers for development
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu4                     all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03~pre18+dfsg-1ubuntu1               all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu5                     amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

Also, this is where I picked up the 3.14 version and followed the steps to install.
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)

---

### Post by sp40140 on 2014-11-04
@Phidia Thank you for the link to man page.. I will go through it.. might take me bit of time.

---

### Post by Doug S on 2014-11-04
Well, you seem to have a bit of a mess going on. All your kernels, except for 3.14 have been deleted. However, and for whatever reason, you still have the headers installed for 3.16.0.24 and 3.16.0.23.
You should be able to re-install the kernels. See if the .debs are still there. Example:```
doug@s15:~/temp-k-git-3.10rc4$ [COLOR=#ff0000]ls -l /var/cache/apt/archives/linux-*[/COLOR]
-rw-r--r-- 1 root root     1780 Sep 25 14:44 /var/cache/apt/archives/linux-generic_3.13.0.37.44_amd64.deb
-rw-r--r-- 1 root root     1784 Oct 28 18:19 /var/cache/apt/archives/linux-generic_3.13.0.39.46_amd64.deb
-rw-r--r-- 1 root root  8893218 Sep 25 14:44 /var/cache/apt/archives/linux-headers-3.13.0-37_3.13.0-37.64_all.deb
-rw-r--r-- 1 root root   721854 Sep 25 14:44 /var/cache/apt/archives/linux-headers-3.13.0-37-generic_3.13.0-37.64_amd64.deb
-rw-r--r-- 1 root root  8892478 Oct 28 18:19 /var/cache/apt/archives/linux-headers-3.13.0-39_3.13.0-39.66_all.deb
-rw-r--r-- 1 root root   727892 Oct 28 18:19 /var/cache/apt/archives/linux-headers-3.13.0-39-generic_3.13.0-39.66_amd64.deb
-rw-r--r-- 1 root root     2336 Sep 25 14:44 /var/cache/apt/archives/linux-headers-generic_3.13.0.37.44_amd64.deb
-rw-r--r-- 1 root root     2404 Oct 28 18:18 /var/cache/apt/archives/linux-headers-generic_3.13.0.39.46_amd64.deb
-rw-r--r-- 1 root root     1756 Sep 25 14:44 /var/cache/apt/archives/linux-headers-server_3.13.0.37.44_amd64.deb
-rw-r--r-- 1 root root     1756 Oct 28 18:18 /var/cache/apt/archives/linux-headers-server_3.13.0.39.46_amd64.deb
-rw-r--r-- 1 root root 15106714 Sep 25 14:44 /var/cache/apt/archives/linux-image-3.13.0-37-generic_3.13.0-37.64_amd64.deb
-rw-r--r-- 1 root root 15167746 Oct 28 18:19 /var/cache/apt/archives/linux-image-3.13.0-39-generic_3.13.0-39.66_amd64.deb
-rw-r--r-- 1 root root 36744178 Sep 25 14:44 /var/cache/apt/archives/linux-image-extra-3.13.0-37-generic_3.13.0-37.64_amd64.deb
-rw-r--r-- 1 root root 36686346 Oct 28 18:19 /var/cache/apt/archives/linux-image-extra-3.13.0-39-generic_3.13.0-39.66_amd64.deb
-rw-r--r-- 1 root root     2354 Sep 25 14:44 /var/cache/apt/archives/linux-image-generic_3.13.0.37.44_amd64.deb
-rw-r--r-- 1 root root     2418 Oct 28 18:19 /var/cache/apt/archives/linux-image-generic_3.13.0.39.46_amd64.deb
-rw-r--r-- 1 root root     1750 Sep 25 14:44 /var/cache/apt/archives/linux-image-server_3.13.0.37.44_amd64.deb
-rw-r--r-- 1 root root     1754 Oct 28 18:19 /var/cache/apt/archives/linux-image-server_3.13.0.39.46_amd64.deb
-rw-r--r-- 1 root root   800814 Sep 25 14:44 /var/cache/apt/archives/linux-libc-dev_3.13.0-37.64_amd64.deb
-rw-r--r-- 1 root root   797936 Oct 28 18:19 /var/cache/apt/archives/linux-libc-dev_3.13.0-39.66_amd64.deb
-rw-r--r-- 1 root root     1746 Sep 25 14:44 /var/cache/apt/archives/linux-server_3.13.0.37.44_amd64.deb
-rw-r--r-- 1 root root     1754 Oct 28 18:18 /var/cache/apt/archives/linux-server_3.13.0.39.46_amd64.deb
```if they are then re-install from there (using the same method as on the link you gave).

Otherwise someone else might have a better method using other tools (I only use dpkg to mess with kernels).

---

### Post by Bucky Ball on 2014-11-05
Can you do:

```
sudo apt-get autoremove #agree if there are things to autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

and post any and all errors. Thanks.

---

### Post by sp40140 on 2014-11-05
Doug 
My archive for apt has mixedup files as well...
```

@EliteBook:/var/cache/apt/archives$ ls -l linux-*
-rw-r--r-- 1 root root 21142888 Oct 22 10:03 linux-firmware_1.138_all.deb
-rw-r--r-- 1 root root  9075946 Oct 21 16:30 linux-headers-3.16.0-23_3.16.0-23.31_all.deb
-rw-r--r-- 1 root root   705146 Oct 21 17:04 linux-headers-3.16.0-23-generic_3.16.0-23.31_amd64.deb
-rw-r--r-- 1 root root  9087582 Oct 28 21:23 linux-headers-3.16.0-24_3.16.0-24.32_all.deb
-rw-r--r-- 1 root root   705068 Oct 28 21:23 linux-headers-3.16.0-24-generic_3.16.0-24.32_amd64.deb
-rw-r--r-- 1 root root     2390 Oct 16 09:54 linux-headers-generic_3.16.0.23.24_amd64.deb
-rw-r--r-- 1 root root     2408 Oct 28 21:23 linux-headers-generic_3.16.0.24.25_amd64.deb
-rw-r--r-- 1 root root 16192782 Oct 21 17:05 linux-image-3.16.0-23-generic_3.16.0-23.31_amd64.deb
-rw-r--r-- 1 root root 37983864 Oct 21 17:05 linux-image-extra-3.16.0-23-generic_3.16.0-23.31_amd64.deb
-rw-r--r-- 1 root root     2412 Oct 16 09:54 linux-image-generic_3.16.0.23.24_amd64.deb
-rw-r--r-- 1 root root   765180 Oct 21 17:04 linux-libc-dev_3.16.0-23.31_amd64.deb
-rw-r--r-- 1 root root   764326 Oct 28 21:23 linux-libc-dev_3.16.0-24.32_amd64.deb

```

I will try to upgrade again as Bucky suggested and report back here.
Thank you for your help

---

### Post by sp40140 on 2014-11-05
Bucky Ball
no errors when executing the commands..

```

@EliteBook:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libboost-system1.54.0
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 84.0 kB disk space will be freed.
Do you want to continue? [Y/n] Y

@EliteBook:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
@EliteBook:~$ 
@EliteBook:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
@EliteBook:~$ 


```
The output from "update" command is too long.. so not posting it. but everything was fine.

---

### Post by Bucky Ball on 2014-11-05
ALWAYS do an update first. 

sudo apt-get update

... then upgrade/dist-upgrade.

Still, no errors is a good start, but perhaps try again using the update commands first, please.

---

### Post by sp40140 on 2014-11-05
Bucky Ball 
I ran that apt-get update..
before doing upgrade and dist-upgrade. it's just that I didn't copy output in the post as it was too long.

---

### Post by Doug S on 2014-11-05
O.K. What do you get for this:```
doug@desk-dev:~$ [COLOR=#ff0000]lsb_release -a[/COLOR]
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 14.10
Release:        14.10
Codename:       utopic
```

---

### Post by sp40140 on 2014-11-05
Hello Doug
I get 14.10..

```

@EliteBook:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic
@EliteBook:~$ 

```

I think everything else has been updated to 14.10. But only the kernel is stuck at 3.14. And that is causing the issues with my system. Ex. Nvidia drivers they want the kernel to be 3.16. And keep crashing as I am stuck with 3.14. And I think all other libs are upgraded (and so complied for 3.16). This also is causing the problems with VMWare (win7 client). I can't run it. 
But I am almost sure that these issues will be fixed once I get my kernel sorted out.

Nuking and re-installing would be a hassle. but more than that, I want to learn and know how to fix these things.

---

### Post by Doug S on 2014-11-05
I sure would like to know how your system got so messed up. Anyway, the archive of your 3.16.0.23 kernel seems to be O.K., but first try these commands:```
sudo apt-get install --reinstall linux-headers-3.16.0-24
sudo apt-get install --reinstall linux-headers-3.16.0-24-generic
sudo apt-get install --reinstall linux-image-3.16.0-24-generic
sudo apt-get install --reinstall linux-image-extra-3.16.0-24-generic
```If that doesn't work (it did work on my VM just now while I was running a different kernel), then try substituting "23" for 24".

---

### Post by sp40140 on 2014-11-06
Doug
YDM. reinstalling worked. uname shows I am running 3.16 now. There were no errors when re-installing either. Once that was done, I re-installed the Nvidia drivers and now VMWare is working fine as well.

One more question:
I can (and have in the past) removed older kernels from system. However, can I boot into previous (lower) version and remove the latest one? Will it cause any problems?
I have a second machine running 14.04 and 3.14 kernel. I haven't upgraded that to 14.10 yet. But I am afraid it will run into same issue as this one we just fixed.

As to How this could have gotten messed up:
The 3.12 kernel version had some issues with hdmi audio. There were supposed to be fixed in 3.14. So, to make my hdmi audio work, I installed the 3.14 from mainline. My hdmi didn't work with 3.14. But everything else was fine. I didn't poke it anymore. Regular updates kept getting installed. Then came the 14.10 upgrade. It installed without any issues (But I guess I was wrong as re-installing worked!). I figured something was wrong when Nvidia kept crashing and VMWare wouldn't work. So, I investigated and turned out it was still running 3.14 instead of 3.16. Started trying to fix it and got here.

---

### Post by Bucky Ball on 2014-11-06
Good news. Please mark the thread as solved using the second link in my signature. Thanks and good luck. ;)

---

### Post by Doug S on 2014-11-06
O.K. glad you got it working. Your system might still think that kernel 3.16.0.23 is also installed and it actually isn't. You might want to take care of that.

> **sp40140 said:**
> One more question:
I can (and have in the past) removed older kernels from system. However, can I boot into previous (lower) version and remove the latest one? Will it cause any problems?
I have a second machine running 14.04 and 3.14 kernel. I haven't upgraded that to 14.10 yet. But I am afraid it will run into same issue as this one we just fixed. The answer is both yes and that is exactly what you should do. I never run "apt-get update" and "apt-get dist-upgrade" unless I am running the stock kernel for the distribution.

---

### Post by sp40140 on 2014-11-06
Great. 
Thank you guys for all your help.

Doug
Here is the uname output:
```

@EliteBook:~$ uname -r
3.16.0-24-generic
@EliteBook:~$ 

```
So, I think I it's fine now. 
I will look to remove the 3.14 from this machine after I get couple more kernel updates, just to be safe.

All Good now,

Beers & Cheers

---

