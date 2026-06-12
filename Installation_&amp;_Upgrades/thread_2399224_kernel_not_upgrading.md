---
title: "kernel not upgrading"
date: 2018-08-23
forum: Installation &amp; Upgrades
---

### Post by Zolcsi on 2018-08-23
Hi folks,

I just upgraded my server to 18.04 and it displayed some information about the L1TF vulnerability, so I checked it out and I read that new a new kernel would fix that.
But I realised that I am still on 3.13 kernel Linux aragorn 3.13.0-63-generic.
apt doesn't show any upgrades, but I thought that 18.04 would bring the 4 series kernel. I don't really mind staying on 3.13 because everything is working fine, I was just wondering what might cause this.

Thanks!

---

### Post by Impavidus on 2018-08-23
3.13.0-64 is a really old kernel for Ubuntu 14.04. 16.04 should have given you 4.4, 18.04 should give you 4.15. Maybe some metapackages to pull in new kernels are missing (and have been missing for years). What do you get from```
dpkg --list 'linux-*'
```(First make your terminal big enough to prevent truncated output, or redirect to a text file.)

---

### Post by Zolcsi on 2018-08-23
This is the output of the command:

```

zolcsi@aragorn:~$ sudo dpkg --list 'linux-*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Név                                                                       Verzió                                    Architecture                              Leírás
+++-=========================================================================-=========================================-=========================================-========================================================================================================================================================
ii  linux-base                                                                4.5ubuntu1                                all                                       Linux image base package
un  linux-doc-3.13.0                                                          <none>                                    <none>                                    (nincs leírás)
ii  linux-firmware                                                            1.173.1                                   all                                       Firmware for Linux kernel drivers
un  linux-firmware-snapdragon                                                 <none>                                    <none>                                    (nincs leírás)
un  linux-headers                                                             <none>                                    <none>                                    (nincs leírás)
un  linux-headers-3.0                                                         <none>                                    <none>                                    (nincs leírás)
ii  linux-headers-3.13.0-46                                                   3.13.0-46.79                              all                                       Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                                           3.13.0-46.79                              amd64                                     Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48                                                   3.13.0-48.80                              all                                       Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                                           3.13.0-48.80                              amd64                                     Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                                                   3.13.0-49.83                              all                                       Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                                           3.13.0-49.83                              amd64                                     Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
un  linux-headers-3.13.0-51-generic                                           <none>                                    <none>                                    (nincs leírás)
un  linux-headers-3.13.0-62-generic                                           <none>                                    <none>                                    (nincs leírás)
ii  linux-headers-3.13.0-63                                                   3.13.0-63.104~precise1                    all                                       Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                                           3.13.0-63.104~precise1                    amd64                                     Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-32                                                   4.15.0-32.35                              all                                       Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32-generic                                           4.15.0-32.35                              amd64                                     Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                                                     4.15.0.32.34                              amd64                                     Generic Linux kernel headers
un  linux-image                                                               <none>                                    <none>                                    (nincs leírás)
un  linux-image-3.0                                                           <none>                                    <none>                                    (nincs leírás)
ii  linux-image-3.13.0-46-generic                                             3.13.0-46.79                              amd64                                     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                                             3.13.0-48.80                              amd64                                     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                                             3.13.0-49.83                              amd64                                     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-51-generic                                             3.13.0-51.84                              amd64                                     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic                                             3.13.0-62.102                             amd64                                     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                                             3.13.0-63.104~precise1                    amd64                                     Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                                       3.13.0-46.79                              amd64                                     Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                                       3.13.0-48.80                              amd64                                     Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                                       3.13.0-49.83                              amd64                                     Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-51-generic                                       3.13.0-51.84                              amd64                                     Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic                                       3.13.0-62.102                             amd64                                     Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
in  linux-image-extra-3.13.0-63-generic                                       <none>                                    amd64                                     (nincs leírás)
un  linux-initramfs-tool                                                      <none>                                    <none>                                    (nincs leírás)
un  linux-kernel-headers                                                      <none>                                    <none>                                    (nincs leírás)
un  linux-kernel-log-daemon                                                   <none>                                    <none>                                    (nincs leírás)
ii  linux-libc-dev:amd64                                                      4.15.0-32.35                              amd64                                     Linux Kernel Headers for development
un  linux-lts-trusty-doc-3.13.0                                               <none>                                    <none>                                    (nincs leírás)
un  linux-lts-trusty-source-3.13.0                                            <none>                                    <none>                                    (nincs leírás)
un  linux-lts-trusty-tools                                                    <none>                                    <none>                                    (nincs leírás)
un  linux-restricted-common                                                   <none>                                    <none>                                    (nincs leírás)
un  linux-source-3.13.0                                                       <none>                                    <none>                                    (nincs leírás)
un  linux-tools                                                               <none>                                    <none>                                    (nincs leírás)

```

---

### Post by jeremy31 on 2018-08-23
What is the result for ```
sudo parted -l
```
I think you might need to install grub again so that it updates the kernel version correctly once again

---

### Post by Zolcsi on 2018-08-23
The output of parted is:

```

zolcsi@aragorn:~$ sudo parted -l
[sudo] password for zolcsi: 
Model: Dell Virtual Disk (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type      File system     Flags
 2      1049kB  1992GB  1992GB  primary   ext4            boot
 1      1992GB  2000GB  7999MB  extended
 5      1992GB  2000GB  7999MB  logical   linux-swap(v1)
```

---

### Post by Zolcsi on 2018-08-24
Something has happened, because this morning after logging in I saw that there are new updates. The following packages were installed or upgraded:

  ffmpeg grub-common grub-pc grub-pc-bin grub2-common libavcodec57 libavdevice57 libavfilter6 libavformat57 libavresample3 libavutil55 libpostproc54 libswresample2 libswscale4 linux-headers-generic linux-libc-dev

These were listed as obsolete, Ubuntu suggested to remove them using apt autoremove:
libopts25 linux-headers-4.15.0-32 linux-headers-4.15.0-32-generic sntp

After the upgrade I got the following list from dpkg:

```

root@aragorn:/home/zolcsi# dpkg --list 'linux-*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Név                                                   Verzió                          Architecture                    Leírás
+++-=====================================================-===============================-===============================-================================================================================================================
ii  linux-base                                            4.5ubuntu1                      all                             Linux image base package
un  linux-doc-3.13.0                                      <none>                          <none>                          (nincs leírás)
ii  linux-firmware                                        1.173.1                         all                             Firmware for Linux kernel drivers
un  linux-firmware-snapdragon                             <none>                          <none>                          (nincs leírás)
un  linux-headers                                         <none>                          <none>                          (nincs leírás)
un  linux-headers-3.0                                     <none>                          <none>                          (nincs leírás)
ii  linux-headers-3.13.0-46                               3.13.0-46.79                    all                             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                    amd64                           Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                    all                             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                    amd64                           Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                    all                             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                    amd64                           Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
un  linux-headers-3.13.0-51-generic                       <none>                          <none>                          (nincs leírás)
un  linux-headers-3.13.0-62-generic                       <none>                          <none>                          (nincs leírás)
ii  linux-headers-3.13.0-63                               3.13.0-63.104~precise1          all                             Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.104~precise1          amd64                           Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-32                               4.15.0-32.35                    all                             Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-32-generic                       4.15.0-32.35                    amd64                           Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-33                               4.15.0-33.36                    all                             Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-33-generic                       4.15.0-33.36                    amd64                           Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                                 4.15.0.33.35                    amd64                           Generic Linux kernel headers
un  linux-image                                           <none>                          <none>                          (nincs leírás)
un  linux-image-3.0                                       <none>                          <none>                          (nincs leírás)
ii  linux-image-3.13.0-46-generic                         3.13.0-46.79                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-48-generic                         3.13.0-48.80                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-49-generic                         3.13.0-49.83                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-51-generic                         3.13.0-51.84                    amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic                         3.13.0-62.102                   amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-63-generic                         3.13.0-63.104~precise1          amd64                           Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-46-generic                   3.13.0-46.79                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-48-generic                   3.13.0-48.80                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-49-generic                   3.13.0-49.83                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-51-generic                   3.13.0-51.84                    amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic                   3.13.0-62.102                   amd64                           Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
in  linux-image-extra-3.13.0-63-generic                   <none>                          amd64                           (nincs leírás)
un  linux-initramfs-tool                                  <none>                          <none>                          (nincs leírás)
un  linux-kernel-headers                                  <none>                          <none>                          (nincs leírás)
un  linux-kernel-log-daemon                               <none>                          <none>                          (nincs leírás)
ii  linux-libc-dev:amd64                                  4.15.0-33.36                    amd64                           Linux Kernel Headers for development
un  linux-lts-trusty-doc-3.13.0                           <none>                          <none>                          (nincs leírás)
un  linux-lts-trusty-source-3.13.0                        <none>                          <none>                          (nincs leírás)
un  linux-lts-trusty-tools                                <none>                          <none>                          (nincs leírás)
un  linux-restricted-common                               <none>                          <none>                          (nincs leírás)
un  linux-source-3.13.0                                   <none>                          <none>                          (nincs leírás)
un  linux-tools                                           <none>                          <none>                          (nincs leírás)

```

However, at the end of the upgrade the script showed the following message:
```

Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

```

So my guess is that the initrd images are not generated, therefore grub cannot install them.

---

### Post by Impavidus on 2018-08-24
You've a missing meta-package: linux-image-generic. For whatever reason it was uninstalled a long time ago. Try```
sudo apt update
sudo apt install linux-image-generic
```That should pull in the latest kernel for Ubuntu 18.04 (4.15.0-33), install it and update grub so you can boot it. Then reboot and clean up some old stuff.

---

### Post by Zolcsi on 2018-08-24
That's great, the new packages are installed. I am going to schedule the reboot to Sunday morning, hopefully everything will be fine with this scale of a kernel upgrade.
Thanks a lot!

---

### Post by Zolcsi on 2018-08-26
The reboot was successful, now my server is booted into 4.15.0-33-generic. Thanks again for the help!

---

