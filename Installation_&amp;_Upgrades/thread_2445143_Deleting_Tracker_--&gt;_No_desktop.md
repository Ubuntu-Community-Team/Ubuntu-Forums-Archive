---
title: "Deleting Tracker --&gt; No desktop"
date: 2020-06-09
forum: Installation &amp; Upgrades
---

### Post by oguzhancakir on 2020-06-09
Hello everyone,

 I am a freshman in ubuntu.

After the upgrade from 19.10 to 20.04, I sometimes got warnings like low memory on your disk. When I checked the disk usage analyzer, I found it was due to Tracker. It was using ~350 GB from my memory!! !  and I checked on the web. I tried to disable several time by writing their .desktop files "Hidden=True" etc. But it did not work.  And I deleted it from synaptic and now I can not install ubuntu-desktop, nautilus.

I do not know what to do :(

I would be really appreciated, if you could help me. Thank you in advance!

---

### Post by Bashing-om on 2020-06-09
oguzhancakir; Welcome to the forum :)

As a place to start; what is the state of the package manager ?
Post back - between code tags - the outputs of terminal commands:
```

sudo apt update
sudo apt upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

See where we go from here/

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by oguzhancakir on 2020-06-09
[COLOR=#000000]Dear Bashing-om, 

Firstly, thank you for welcoming :)

When I run those two commands, output is below;

[/COLOR]```

sudo apt update

Hit:1 http://dl.google.com/linux/chrome/deb stable InReleaseHit:2 http://archive.canonical.com/ubuntu focal InRelease                  
Hit:3 http://archive.ubuntu.com/ubuntu focal InRelease                     
Get:4 http://archive.ubuntu.com/ubuntu focal-updates InRelease [107 kB]
Get:5 http://archive.ubuntu.com/ubuntu focal-backports InRelease [98,3 kB]
Get:6 http://archive.ubuntu.com/ubuntu focal-security InRelease [107 kB]
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main i386 Packages [97,1 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages [186 kB]
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/main Translation-en [72,2 kB]
Get:10 http://archive.ubuntu.com/ubuntu focal-updates/restricted amd64 Packages [10,9 kB]
Get:11 http://archive.ubuntu.com/ubuntu focal-updates/restricted Translation-en [2.972 B]
Fetched 681 kB in 1s (480 kB/s)                                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
4 packages can be upgraded. Run 'apt list --upgradable' to see them.
 

```[COLOR=#000000]

[/COLOR]```

sudo apt upgrade

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-5.4.0-37 linux-headers-5.4.0-37-generic linux-image-5.4.0-37-generic linux-modules-5.4.0-37-generic
  linux-modules-extra-5.4.0-37-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic linux-libc-dev
4 upgraded, 5 newly installed, 0 to remove and 0 not upgraded.
Need to get 75,1 MB of archives.
After this operation, 359 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-5.4.0-37-generic amd64 5.4.0-37.41 [14,4 MB]
Get:2 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-5.4.0-37-generic amd64 5.4.0-37.41 [8.877 kB]
Get:3 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-modules-extra-5.4.0-37-generic amd64 5.4.0-37.41 [38,5 MB]
Get:4 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-generic amd64 5.4.0.37.40 [1.900 B]              
Get:5 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-image-generic amd64 5.4.0.37.40 [2.612 B]        
Get:6 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-5.4.0-37 all 5.4.0-37.41 [10,9 MB]       
Get:7 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-5.4.0-37-generic amd64 5.4.0-37.41 [1.218 kB]
Get:8 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-headers-generic amd64 5.4.0.37.40 [2.496 B]      
Get:9 http://archive.ubuntu.com/ubuntu focal-updates/main amd64 linux-libc-dev amd64 5.4.0-37.41 [1.103 kB]            
Fetched 75,1 MB in 46s (1.628 kB/s)                                                                                    
Selecting previously unselected package linux-modules-5.4.0-37-generic.
(Reading database ... 386498 files and directories currently installed.)
Preparing to unpack .../0-linux-modules-5.4.0-37-generic_5.4.0-37.41_amd64.deb ...
Unpacking linux-modules-5.4.0-37-generic (5.4.0-37.41) ...
Selecting previously unselected package linux-image-5.4.0-37-generic.
Preparing to unpack .../1-linux-image-5.4.0-37-generic_5.4.0-37.41_amd64.deb ...
Unpacking linux-image-5.4.0-37-generic (5.4.0-37.41) ...
Selecting previously unselected package linux-modules-extra-5.4.0-37-generic.
Preparing to unpack .../2-linux-modules-extra-5.4.0-37-generic_5.4.0-37.41_amd64.deb ...
Unpacking linux-modules-extra-5.4.0-37-generic (5.4.0-37.41) ...
Preparing to unpack .../3-linux-generic_5.4.0.37.40_amd64.deb ...
Unpacking linux-generic (5.4.0.37.40) over (5.4.0.33.38) ...
Preparing to unpack .../4-linux-image-generic_5.4.0.37.40_amd64.deb ...
Unpacking linux-image-generic (5.4.0.37.40) over (5.4.0.33.38) ...
Selecting previously unselected package linux-headers-5.4.0-37.
Preparing to unpack .../5-linux-headers-5.4.0-37_5.4.0-37.41_all.deb ...
Unpacking linux-headers-5.4.0-37 (5.4.0-37.41) ...
Selecting previously unselected package linux-headers-5.4.0-37-generic.
Preparing to unpack .../6-linux-headers-5.4.0-37-generic_5.4.0-37.41_amd64.deb ...
Unpacking linux-headers-5.4.0-37-generic (5.4.0-37.41) ...
Preparing to unpack .../7-linux-headers-generic_5.4.0.37.40_amd64.deb ...
Unpacking linux-headers-generic (5.4.0.37.40) over (5.4.0.33.38) ...
Preparing to unpack .../8-linux-libc-dev_5.4.0-37.41_amd64.deb ...
Unpacking linux-libc-dev:amd64 (5.4.0-37.41) over (5.4.0-33.37) ...
Setting up linux-libc-dev:amd64 (5.4.0-37.41) ...
Setting up linux-headers-5.4.0-37 (5.4.0-37.41) ...
Setting up linux-modules-5.4.0-37-generic (5.4.0-37.41) ...
Setting up linux-headers-5.4.0-37-generic (5.4.0-37.41) ...
/etc/kernel/header_postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-37-generic


Kernel preparation unnecessary for this kernel.  Skipping...
applying patch 0002-Makefile.patch...patching file Makefile
Hunk #1 succeeded at 113 with fuzz 1.
Hunk #2 succeeded at 132 with fuzz 2 (offset 1 line).


applying patch 0003-Make-up-for-missing-init_MUTEX.patch...patching file src/wl/sys/wl_linux.c
Hunk #1 succeeded at 111 with fuzz 2 (offset 12 lines).


applying patch 0010-change-the-network-interface-name-from-eth-to-wlan.patch...patching file src/wl/sys/wl_linux.c
Hunk #1 succeeded at 221 (offset -14 lines).


applying patch 0013-gcc.patch...patching file Makefile


applying patch 0019-broadcom-sta-6.30.223.248-3.18-null-pointer-fix.patch...patching file src/wl/sys/wl_linux.c
Hunk #1 succeeded at 2169 (offset 12 lines).


applying patch 0020-add-support-for-linux-4.3.patch...patching file src/shared/linux_osl.c


applying patch 0021-add-support-for-Linux-4.7.patch...patching file src/wl/sys/wl_cfg80211_hybrid.c


applying patch 0022-add-support-for-Linux-4.8.patch...patching file src/wl/sys/wl_cfg80211_hybrid.c
Hunk #1 succeeded at 2391 (offset 3 lines).
Hunk #2 succeeded at 2501 (offset 3 lines).
Hunk #3 succeeded at 2933 (offset 9 lines).


applying patch 0023-add-support-for-Linux-4.11.patch...patching file src/include/linuxver.h
patching file src/wl/sys/wl_linux.c
Hunk #1 succeeded at 2919 (offset 4 lines).


applying patch 0024-add-support-for-Linux-4.12.patch...patching file src/wl/sys/wl_cfg80211_hybrid.c
Hunk #1 succeeded at 55 (offset 5 lines).
Hunk #2 succeeded at 472 (offset 5 lines).
Hunk #3 succeeded at 2371 (offset 5 lines).
Hunk #4 succeeded at 2388 (offset 5 lines).


applying patch 0025-add-support-for-Linux-4.14.patch...patching file src/shared/linux_osl.c
Hunk #1 succeeded at 1080 (offset 4 lines).


applying patch 0026-add-support-for-Linux-4.15.patch...patching file src/wl/sys/wl_linux.c
Hunk #2 succeeded at 2306 (offset 4 lines).
Hunk #3 succeeded at 2368 (offset 4 lines).


applying patch 0027-add-support-for-linux-5.1.patch...patching file src/include/linuxver.h
Hunk #1 succeeded at 595 (offset 4 lines).




Building module:
cleaning build area...
make -j8 KERNELRELEASE=5.4.0-37-generic -C /lib/modules/5.4.0-37-generic/build M=/var/lib/dkms/bcmwl/6.30.223.271+bdcom/
build...
cleaning build area...


DKMS: build completed.


wl.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-37-generic/updates/dkms/


depmod...


DKMS: install completed.


Kernel preparation unnecessary for this kernel.  Skipping...
applying patch disable_fstack-clash-protection_fcf-protection.patch...patching file Kbuild
Hunk #1 succeeded at 79 (offset 8 lines).


applying patch buildfix_kernel_5.6.patch...patching file common/inc/nv-procfs.h
patching file common/inc/nv-time.h
patching file conftest.sh
Hunk #1 succeeded at 1267 (offset -3 lines).
Hunk #2 succeeded at 2936 (offset -3 lines).
patching file nvidia-modeset/nvidia-modeset.Kbuild
patching file nvidia-uvm/nvidia-uvm.Kbuild
patching file nvidia/linux_nvswitch.c
patching file nvidia/nv-procfs.c
patching file nvidia/nvidia.Kbuild
patching file nvidia/nvlink_linux.c




Building module:
cleaning build area...
unset ARCH; [ ! -h /usr/bin/cc ] && export CC=/usr/bin/gcc; env NV_VERBOSE=1 'make' -j8 NV_EXCLUDE_BUILD_MODULES='' KERN
EL_UNAME=5.4.0-37-generic IGNORE_XEN_PRESENCE=1 IGNORE_CC_MISMATCH=1 SYSSRC=/lib/modules/5.4.0-37-generic/build LD=/usr/
bin/ld.bfd modules............
cleaning build area...


DKMS: build completed.


nvidia.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-37-generic/updates/dkms/


nvidia-modeset.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-37-generic/updates/dkms/


nvidia-drm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-37-generic/updates/dkms/


nvidia-uvm.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/5.4.0-37-generic/updates/dkms/


depmod...


DKMS: install completed.
   ...done.
Setting up linux-headers-generic (5.4.0.37.40) ...
Setting up linux-image-5.4.0-37-generic (5.4.0-37.41) ...
I: /boot/vmlinuz.old is now a symlink to vmlinuz-5.4.0-33-generic
I: /boot/initrd.img.old is now a symlink to initrd.img-5.4.0-33-generic
I: /boot/vmlinuz is now a symlink to vmlinuz-5.4.0-37-generic
I: /boot/initrd.img is now a symlink to initrd.img-5.4.0-37-generic
Setting up linux-modules-extra-5.4.0-37-generic (5.4.0-37.41) ...
Setting up linux-image-generic (5.4.0.37.40) ...
Setting up linux-generic (5.4.0.37.40) ...
Processing triggers for linux-image-5.4.0-37-generic (5.4.0-37.41) ...
/etc/kernel/postinst.d/dkms:
 * dkms: running auto installation service for kernel 5.4.0-37-generic
   ...done.
/etc/kernel/postinst.d/initramfs-tools:
update-initramfs: Generating /boot/initrd.img-5.4.0-37-generic
I: The initramfs will attempt to resume from /dev/sda5
I: (UUID=c0050141-f1fd-4566-8d99-24ce8ef30057)
I: Set the RESUME variable to override this.
/etc/kernel/postinst.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-5.4.0-37-generic
Found initrd image: /boot/initrd.img-5.4.0-37-generic
Found linux image: /boot/vmlinuz-5.4.0-33-generic
Found initrd image: /boot/initrd.img-5.4.0-33-generic
Found linux image: /boot/vmlinuz-5.4.0-31-generic
Found initrd image: /boot/initrd.img-5.4.0-31-generic
Found linux image: /boot/vmlinuz-5.3.0-18-generic
Found initrd image: /boot/initrd.img-5.3.0-18-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done



```[COLOR=#000000]

Beside, in synaptic, sometimes it gives me a warning fix the broken packages (I think it is related to this issue). Therefore, I clicked the "Edit", then click the "Fix the broken packages", but it does not matter.[/COLOR]

---

### Post by Bashing-om on 2020-06-09
oguzhancakir; Well -

So far so good -
But where did you come up with that linux-image-5.4.0-37-generic kernel ?
as the latest supported is;
> 
 Package linux-image-generic
focal (20.04LTS) (kernel): Generic Linux kernel image
5.4.0.33.38 [security]: amd64
5.4.0.26.32 [ports]: arm64 armhf ppc64el s390x


so what kernel are you booting:
```

uname -r

```

are all kernels fully installed:
```

dpkg -l | grep linux-

```
And with the number of kernels that are installed; what is the disk space usage:
```

df -h
df -i

```

Broken packages advisory ?
what shows:
```

sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT]maybe all is well ?
[/INDENT][/INDENT]

---

### Post by rbmorse on 2020-06-09
5.4.0-37 was pushed today.  Just showed up in my update queue.

---

### Post by oguzhancakir on 2020-06-10
Actually I do not know about linux image generic kernel :(

```

uname -r


5.4.0-37-generic

```

```

dpkg -l | grep linux


ii  binutils-x86-64-linux-gnu                         2.34-6ubuntu1                       amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  console-setup-linux                               1.194ubuntu3                        all          Linux specific part of console-setup
rc  extlinux                                          3:6.04~git20190206.bf6db5b4+dfsg1-2 amd64        collection of bootloaders (Linux ext2/ext3/ext4, btrfs, and xfs bootloader)
ii  fonts-linuxlibertine                              5.3.0-4                             all          Linux Libertine family of fonts
ii  libselinux1:amd64                                 3.0-1build2                         amd64        SELinux runtime shared libraries
ii  libselinux1:i386                                  3.0-1build2                         i386         SELinux runtime shared libraries
ii  libv4l-0:amd64                                    1.18.0-2build1                      amd64        Collection of video4linux support libraries
ii  libv4l-0:i386                                     1.18.0-2build1                      i386         Collection of video4linux support libraries
ii  libv4lconvert0:amd64                              1.18.0-2build1                      amd64        Video4linux frame format conversion library
ii  libv4lconvert0:i386                               1.18.0-2build1                      i386         Video4linux frame format conversion library
ii  linux-base                                        4.5ubuntu3                          all          Linux image base package
ii  linux-firmware                                    1.187                               all          Firmware for Linux kernel drivers
ii  linux-generic                                     5.4.0.37.40                         amd64        Complete Generic Linux kernel and headers
ii  linux-headers-5.3.0-18                            5.3.0-18.19                         all          Header files related to Linux kernel version 5.3.0
ii  linux-headers-5.3.0-18-generic                    5.3.0-18.19                         amd64        Linux kernel headers for version 5.3.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-31                            5.4.0-31.35                         all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-31-generic                    5.4.0-31.35                         amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-33                            5.4.0-33.37                         all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-33-generic                    5.4.0-33.37                         amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-5.4.0-37                            5.4.0-37.41                         all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-37-generic                    5.4.0-37.41                         amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                             5.4.0.37.40                         amd64        Generic Linux kernel headers
ii  linux-image-5.3.0-18-generic                      5.3.0-18.19+1                       amd64        Signed kernel image generic
rc  linux-image-5.3.0-29-generic                      5.3.0-29.31                         amd64        Signed kernel image generic
rc  linux-image-5.3.0-40-generic                      5.3.0-40.32                         amd64        Signed kernel image generic
rc  linux-image-5.3.0-42-generic                      5.3.0-42.34                         amd64        Signed kernel image generic
rc  linux-image-5.3.0-45-generic                      5.3.0-45.37                         amd64        Signed kernel image generic
rc  linux-image-5.3.0-46-generic                      5.3.0-46.38                         amd64        Signed kernel image generic
rc  linux-image-5.3.0-51-generic                      5.3.0-51.44                         amd64        Signed kernel image generic
rc  linux-image-5.4.0-29-generic                      5.4.0-29.33                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-31-generic                      5.4.0-31.35                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-33-generic                      5.4.0-33.37                         amd64        Signed kernel image generic
ii  linux-image-5.4.0-37-generic                      5.4.0-37.41                         amd64        Signed kernel image generic
ii  linux-image-generic                               5.4.0.37.40                         amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                              5.4.0-37.41                         amd64        Linux Kernel Headers for development
ii  linux-modules-5.3.0-18-generic                    5.3.0-18.19                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-29-generic                    5.3.0-29.31                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-40-generic                    5.3.0-40.32                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-42-generic                    5.3.0-42.34                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-45-generic                    5.3.0-45.37                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-46-generic                    5.3.0-46.38                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.3.0-51-generic                    5.3.0-51.44                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-5.4.0-29-generic                    5.4.0-29.33                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-31-generic                    5.4.0-31.35                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-33-generic                    5.4.0-33.37                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-5.4.0-37-generic                    5.4.0-37.41                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-18-generic              5.3.0-18.19                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-29-generic              5.3.0-29.31                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-40-generic              5.3.0-40.32                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-42-generic              5.3.0-42.34                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-45-generic              5.3.0-45.37                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-46-generic              5.3.0-46.38                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.3.0-51-generic              5.3.0-51.44                         amd64        Linux kernel extra modules for version 5.3.0 on 64 bit x86 SMP
rc  linux-modules-extra-5.4.0-29-generic              5.4.0-29.33                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-31-generic              5.4.0-31.35                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-33-generic              5.4.0-33.37                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-37-generic              5.4.0-37.41                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-sound-base                                  1.0.25+dfsg-0ubuntu5                all          base package for ALSA and OSS sound systems
ii  pptp-linux                                        1.10.0-1build1                      amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  skypeforlinux                                     8.59.0.77                           amd64        Skype keeps the world talking, for free.
ii  syslinux                                          3:6.04~git20190206.bf6db5b4+dfsg1-2 amd64        collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                                   3:6.04~git20190206.bf6db5b4+dfsg1-2 all          collection of bootloaders (common)
ii  syslinux-legacy                                   2:3.63+dfsg-2ubuntu9                amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                        2.34-0.1ubuntu9                     amd64        miscellaneous system utilities

```

```

df -h 


Filesystem      Size  Used Avail Use% Mounted on
udev            7,8G     0  7,8G   0% /dev
tmpfs           1,6G  2,2M  1,6G   1% /run
/dev/sda1        32G   23G  7,6G  75% /
tmpfs           7,8G  257M  7,6G   4% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           7,8G     0  7,8G   0% /sys/fs/cgroup
/dev/loop0      106M  106M     0 100% /snap/audacity/648
/dev/loop2      114M  114M     0 100% /snap/audacity/666
/dev/loop3      157M  157M     0 100% /snap/chromium/1165
/dev/loop4       94M   94M     0 100% /snap/core/9066
/dev/loop1      157M  157M     0 100% /snap/chromium/1182
/dev/loop5       55M   55M     0 100% /snap/core18/1705
/dev/loop6       55M   55M     0 100% /snap/core18/1754
/dev/loop8       98M   98M     0 100% /snap/core/9289
/dev/loop7      256M  256M     0 100% /snap/gnome-3-34-1804/33
/dev/loop9      256M  256M     0 100% /snap/gnome-3-34-1804/36
/dev/loop11     182M  182M     0 100% /snap/spotify/36
/dev/loop10     194M  194M     0 100% /snap/mailspring/482
/dev/loop12      50M   50M     0 100% /snap/snap-store/433
/dev/loop13     194M  194M     0 100% /snap/mailspring/488
/dev/loop14      55M   55M     0 100% /snap/gtk-common-themes/1502
/dev/loop15     203M  203M     0 100% /snap/vlc/1397
/dev/loop16     213M  213M     0 100% /snap/tuxguitar-vs/10
/dev/loop17     256K  256K     0 100% /snap/gtk2-common-themes/9
/dev/loop18      50M   50M     0 100% /snap/snap-store/454
/dev/loop19     291M  291M     0 100% /snap/vlc/1620
/dev/loop20     145M  145M     0 100% /snap/zoom-client/84
/dev/loop21      63M   63M     0 100% /snap/gtk-common-themes/1506
/dev/loop22     164M  164M     0 100% /snap/spotify/41
/dev/loop23      68M   68M     0 100% /snap/sublime-text/85
/dev/sda6       394G   51G  323G  14% /home
tmpfs           1,6G   16K  1,6G   1% /run/user/124
tmpfs           1,6G   44K  1,6G   1% /run/user/1000

```

```

df -i


Filesystem       Inodes  IUsed    IFree IUse% Mounted on
udev            2031967    599  2031368    1% /dev
tmpfs           2039006   1195  2037811    1% /run
/dev/sda1       2084880 492078  1592802   24% /
tmpfs           2039006    947  2038059    1% /dev/shm
tmpfs           2039006      5  2039001    1% /run/lock
tmpfs           2039006     18  2038988    1% /sys/fs/cgroup
/dev/loop0        12747  12747        0  100% /snap/audacity/648
/dev/loop2        14227  14227        0  100% /snap/audacity/666
/dev/loop3        10769  10769        0  100% /snap/chromium/1165
/dev/loop4        12857  12857        0  100% /snap/core/9066
/dev/loop1        10769  10769        0  100% /snap/chromium/1182
/dev/loop5        10765  10765        0  100% /snap/core18/1705
/dev/loop6        10764  10764        0  100% /snap/core18/1754
/dev/loop8        12860  12860        0  100% /snap/core/9289
/dev/loop7        24339  24339        0  100% /snap/gnome-3-34-1804/33
/dev/loop9        24339  24339        0  100% /snap/gnome-3-34-1804/36
/dev/loop11       23725  23725        0  100% /snap/spotify/36
/dev/loop10       24692  24692        0  100% /snap/mailspring/482
/dev/loop12       15827  15827        0  100% /snap/snap-store/433
/dev/loop13       24692  24692        0  100% /snap/mailspring/488
/dev/loop14       47984  47984        0  100% /snap/gtk-common-themes/1502
/dev/loop15       44807  44807        0  100% /snap/vlc/1397
/dev/loop16       31628  31628        0  100% /snap/tuxguitar-vs/10
/dev/loop17          14     14        0  100% /snap/gtk2-common-themes/9
/dev/loop18       15827  15827        0  100% /snap/snap-store/454
/dev/loop19       51065  51065        0  100% /snap/vlc/1620
/dev/loop20       13531  13531        0  100% /snap/zoom-client/84
/dev/loop21       62342  62342        0  100% /snap/gtk-common-themes/1506
/dev/loop22       24012  24012        0  100% /snap/spotify/41
/dev/loop23       14689  14689        0  100% /snap/sublime-text/85
/dev/sda6      26247168 187571 26059597    1% /home
tmpfs           2039006     60  2038946    1% /run/user/124
tmpfs           2039006    108  2038898    1% /run/user/1000

```

```

sudo apt -f install
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-5.4.0-31 linux-headers-5.4.0-31-generic linux-image-5.4.0-31-generic linux-modules-5.4.0-31-generic
  linux-modules-extra-5.4.0-31-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


```

sudo dpkg -C

```

When I try to install ubuntu-desktop

```

sudo apt-get install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 ubuntu-desktop : Depends: gnome-shell-extension-desktop-icons but it is not going to be installed
                  Depends: nautilus but it is not going to be installed
                  Depends: ubuntu-desktop-minimal but it is not going to be installed
                  Recommends: nautilus-share but it is not installable
E: Unable to correct problems, you have held broken packages.

```

---

### Post by ActionParsnip on 2020-06-10
Try:
```

sudo apt-get clean
sudo apt-get --purge autoremove

```

I'm not seeing any issues in the outputs about low disk space bit these are good to run. Your post says about memory. What is the output of:
```

free -m

```

Thanks

---

