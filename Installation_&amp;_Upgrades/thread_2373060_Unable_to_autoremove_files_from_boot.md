---
title: "Unable to autoremove files from /boot"
date: 2017-10-02
forum: Installation &amp; Upgrades
---

### Post by dossvanda on 2017-10-02
Hi,
i have an issue cleaning up /boot on a Ubuntu 14.04.4 LTS installation which is at 100% full. I suspect that someone's tried to manually delete old kernel files and now I'm unable to use autoremove:
* sudo apt-get autoremove:
   E: Unmet dependencies. Try using -f.
* sudo apt-get -f install:
   This tries to install linux-headers-3.13.0-132 but gives the following error:
   'dpkg: error processing archive /var/cache/apt/archives/linux-headers-3.13.0-132_3.13.0-132.181_all.deb (--unpack): unable to open '/usr/src/linux-headers-3.13.0-132/include/linux/amba/pl022.h.dpkg-new': Operation not permitted
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-3.13.0-132_3.13.0-132.181_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)'

Any help greatly appreciated
Thanks
Paul

---

### Post by ian-weisser on 2017-10-02
'Operation not permitted' seems different from a file-not-found problem.

---

### Post by Impavidus on 2017-10-02
'Operation not permitted' is an unexpected error. Not sure what could cause that.

Anyway, to learn a bit more about the state your system is in, try these and show us the output:```
ls /boot
dpkg -l | grep linux
uname -r
```

---

### Post by dossvanda on 2017-10-03
Thanks Impavidus - I'm pretty sure it's not a permissions issue. Here's the requested output:

ls /boot
```
abi-4.2.0-38-generic     config-4.2.0-42-generic      initrd.img-4.2.0-35-generic  lost+found                   System.map-4.2.0-30-generic  System.map-4.2.0-41-generic
abi-4.2.0-41-generic     grub                         initrd.img-4.2.0-36-generic  memtest86+.bin               System.map-4.2.0-34-generic  System.map-4.2.0-42-generic
abi-4.2.0-42-generic     initrd.img-4.2.0-27-generic  initrd.img-4.2.0-38-generic  memtest86+.elf               System.map-4.2.0-35-generic  vmlinuz-4.2.0-38-generic
config-4.2.0-38-generic  initrd.img-4.2.0-30-generic  initrd.img-4.2.0-41-generic  memtest86+_multiboot.bin     System.map-4.2.0-36-generic  vmlinuz-4.2.0-41-generic
config-4.2.0-41-generic  initrd.img-4.2.0-34-generic  initrd.img-4.2.0-42-generic  System.map-4.2.0-27-generic  System.map-4.2.0-38-generic  vmlinuz-4.2.0-42-generic
```

dpkg -l | grep
```
ii  libselinux1:amd64                  2.2.2-1ubuntu0.1                           amd64        SELinux runtime shared libraries
ii  linux-firmware                     1.127.23                                   all          Firmware for Linux kernel drivers
ii  linux-generic-lts-wily             4.2.0.42.34                                amd64        Complete Generic Linux kernel and headers
iU  linux-headers-3.13.0-132-generic   3.13.0-132.181                             amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-79            3.13.0-79.123                              all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic    3.13.0-79.123                              amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-83            3.13.0-83.127                              all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic    3.13.0-83.127                              amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-85            3.13.0-85.129                              all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic    3.13.0-85.129                              amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-86            3.13.0-86.131                              all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic    3.13.0-86.131                              amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-87            3.13.0-87.133                              all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-87-generic    3.13.0-87.133                              amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-88            3.13.0-88.135                              all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic    3.13.0-88.135                              amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-91            3.13.0-91.138                              all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-91-generic    3.13.0-91.138                              amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-92            3.13.0-92.139                              all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic    3.13.0-92.139                              amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-27             4.2.0-27.32~14.04.1                        all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-27-generic     4.2.0-27.32~14.04.1                        amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-30             4.2.0-30.36~14.04.1                        all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-30-generic     4.2.0-30.36~14.04.1                        amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-34             4.2.0-34.39~14.04.1                        all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-34-generic     4.2.0-34.39~14.04.1                        amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-35             4.2.0-35.40~14.04.1                        all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-35-generic     4.2.0-35.40~14.04.1                        amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-36             4.2.0-36.42~14.04.1                        all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-36-generic     4.2.0-36.42~14.04.1                        amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-38             4.2.0-38.45~14.04.1                        all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-38-generic     4.2.0-38.45~14.04.1                        amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-41             4.2.0-41.48~14.04.1                        all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-41-generic     4.2.0-41.48~14.04.1                        amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
ii  linux-headers-4.2.0-42             4.2.0-42.49~14.04.1                        all          Header files related to Linux kernel version 4.2.0
ii  linux-headers-4.2.0-42-generic     4.2.0-42.49~14.04.1                        amd64        Linux kernel headers for version 4.2.0 on 64 bit x86 SMP
iU  linux-headers-generic              3.13.0.132.141                             amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-wily     4.2.0.42.34                                amd64        Generic Linux kernel headers
iU  linux-headers-server               3.13.0.132.141                             amd64        Transitional package.
ii  linux-image-4.2.0-27-generic       4.2.0-27.32~14.04.1                        amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-30-generic       4.2.0-30.36~14.04.1                        amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-34-generic       4.2.0-34.39~14.04.1                        amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-35-generic       4.2.0-35.40~14.04.1                        amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-36-generic       4.2.0-36.42~14.04.1                        amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-38-generic       4.2.0-38.45~14.04.1                        amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-41-generic       4.2.0-41.48~14.04.1                        amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-4.2.0-42-generic       4.2.0-42.49~14.04.1                        amd64        Linux kernel image for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-27-generic 4.2.0-27.32~14.04.1                        amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-30-generic 4.2.0-30.36~14.04.1                        amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-34-generic 4.2.0-34.39~14.04.1                        amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-35-generic 4.2.0-35.40~14.04.1                        amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-36-generic 4.2.0-36.42~14.04.1                        amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-38-generic 4.2.0-38.45~14.04.1                        amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-41-generic 4.2.0-41.48~14.04.1                        amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-extra-4.2.0-42-generic 4.2.0-42.49~14.04.1                        amd64        Linux kernel extra modules for version 4.2.0 on 64 bit x86 SMP
ii  linux-image-generic-lts-wily       4.2.0.42.34                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64               3.13.0-132.181                             amd64        Linux Kernel Headers for development
ii  util-linux                         2.20.1-5.1ubuntu20.7                       amd64        Miscellaneous system utilities
```


```

uname -r:
4.2.0-42-generic
```

Thanks for your help

---

### Post by ian-weisser on 2017-10-03
What you see in /boot seems to match dpkg's reckoning. Nobody appears to have cleaned out /boot the wrong way.

All those linux-headers-* packages are stored in /usr/src, not in /boot. and /usr/src is where you seem to be encountering the error.

Can you use dpkg (not apt) to remove some of those old header packages?
What are the permissions of the offending file: [COLOR=#000000]/usr/src/linux-headers-3.13.0-132/include/linux/amba/pl022.h.dpkg-new
[/COLOR]Do you have enough inodes? (df -i)

---

### Post by Impavidus on 2017-10-04
> **ian-weisser said:**
> What you see in /boot seems to match dpkg's reckoning. Nobody appears to have cleaned out /boot the wrong way.

Not entirely. Although the System.map-* and initrd.img-* files of all old versions are present, the abi-* and config-* files are not.

Try removing old versions of header packages and kernel packages with dpkg.```
sudo dpkg -P linux-headers-4.2.0-27 linux-headers-4.2.0-27-generic
sudo dpkg -P linux-image-4.2.0-27-generic linux-image-extra-4.2.0-27-generic
```And the same for the other old versions, including the 3.13 header packages. Keep 4.2.0-41 and 4.2.0-42 for a while.

Kernel 4.2.0 for Ubuntu 14.04 is no longer supported. You should upgrade to kernel 4.4.
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

---

### Post by dossvanda on 2017-10-04
Ian-Weisser/Impavidus,
Thanks so much for your help. Getting rid of the old kernels using dpkg seems to have done the trick and I'm now updating OK again.
Hats off to you guys.
Regards
Paul

---

### Post by oldos2er on 2017-10-04
Would you please mark your thread 'Solved' under Thread Tools at the top of the page? It will help others who may be having the same problem.

Thanks.

---

