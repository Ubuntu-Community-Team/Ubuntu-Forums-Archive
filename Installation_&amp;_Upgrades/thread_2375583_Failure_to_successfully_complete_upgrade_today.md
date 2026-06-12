---
title: "Failure to successfully complete upgrade today"
date: 2017-10-25
forum: Installation &amp; Upgrades
---

### Post by harfin on 2017-10-25
Hello,

On being advised of an upgrade for my HP-255-G1-Notebook-PC today, I proceeded to instigate the upgrade.
It finished with:
```
WARNING: missing /lib/modules/4.4.0-81-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-81-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_3WhayW/lib/modules/4.4.0-81-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_3WhayW/lib/modules/4.4.0-81-generic/modules.builtin: No such file or directory



```

```
The full text from the attempt today is as follows:
Harfin@harfin-HP-255-G1-Notebook-PC:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-extra
  distro-info-data linux-firmware
5 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 107 MB of archives.
After this operation, 40.2 MB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 chromium-browser-l10n all 62.0.3202.62-0ubuntu0.16.04.1308 [2,701 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 chromium-browser amd64 62.0.3202.62-0ubuntu0.16.04.1308 [59.2 MB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 chromium-codecs-ffmpeg-extra amd64 62.0.3202.62-0ubuntu0.16.04.1308 [1,000 kB]
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 distro-info-data all 0.28ubuntu0.4 [4,130 B]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 linux-firmware all 1.157.13 [44.4 MB]
Fetched 107 MB in 53s (2,005 kB/s)                                             
(Reading database ... 266892 files and directories currently installed.)
Preparing to unpack .../chromium-browser-l10n_62.0.3202.62-0ubuntu0.16.04.1308_all.deb ...
Unpacking chromium-browser-l10n (62.0.3202.62-0ubuntu0.16.04.1308) over (61.0.3163.100-0ubuntu0.16.04.1306) ...
Preparing to unpack .../chromium-browser_62.0.3202.62-0ubuntu0.16.04.1308_amd64.deb ...
Unpacking chromium-browser (62.0.3202.62-0ubuntu0.16.04.1308) over (61.0.3163.100-0ubuntu0.16.04.1306) ...
Preparing to unpack .../chromium-codecs-ffmpeg-extra_62.0.3202.62-0ubuntu0.16.04.1308_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (62.0.3202.62-0ubuntu0.16.04.1308) over (61.0.3163.100-0ubuntu0.16.04.1306) ...
Preparing to unpack .../distro-info-data_0.28ubuntu0.4_all.deb ...
Unpacking distro-info-data (0.28ubuntu0.4) over (0.28ubuntu0.3) ...
Preparing to unpack .../linux-firmware_1.157.13_all.deb ...
Unpacking linux-firmware (1.157.13) over (1.157.12) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu5.1) ...
Processing triggers for bamfdaemon (0.5.3~bzr0+16.04.20160824-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.13.3-6ubuntu3.1) ...
Processing triggers for mime-support (3.59ubuntu1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for hicolor-icon-theme (0.15-0ubuntu1) ...
Setting up chromium-codecs-ffmpeg-extra (62.0.3202.62-0ubuntu0.16.04.1308) ...
Setting up chromium-browser (62.0.3202.62-0ubuntu0.16.04.1308) ...
Setting up chromium-browser-l10n (62.0.3202.62-0ubuntu0.16.04.1308) ...
Setting up distro-info-data (0.28ubuntu0.4) ...
Setting up linux-firmware (1.157.13) ...
update-initramfs: Generating /boot/initrd.img-4.4.0-97-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-96-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-81-generic
WARNING: missing /lib/modules/4.4.0-81-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-81-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_3WhayW/lib/modules/4.4.0-81-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_3WhayW/lib/modules/4.4.0-81-generic/modules.builtin: No such file or directory

```

Could some please help by advising me as to what I should do now.

Alan 
(Senior novice)

---

### Post by ian-weisser on 2017-10-25
Did you ever manually move or remove any kernel files?
Have you had any kernel-related problems before?

---

### Post by harfin on 2017-10-26
Hiya

Not knowingly!  I have in the past battled with the automated update process (I seem to recall that you helped me at that time) so since that time, I update using the commands that I was then given to update, i.e. sudo apt upgrade, sudo apt update and sudo apt autoremove. I have used those now for at least a year. (Thread [https://ubuntuforums.org/showthread.php?t=2337880](https://ubuntuforums.org/showthread.php?t=2337880)) was the previous post regarding updating I think)

One update didn't complete a few months ago - it stopped half way through and I was advised by the system to insert an Ubuntu DVD and and restore and then subsequently run update/upgrade again.

Regards, Alan

---

### Post by Bashing-om on 2017-10-26
harfin; Hello;

Maybe best take a look:
> 
ERROR: could not open directory /lib/modules/4.4.0-81-generic: No such file or directory

And see what the state of the installed kernels are.

What shows:
```

ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
uname -r

```
then we see what it is going to take to satisfy the package manager.

[INDENT][INDENT]we can do that
[/INDENT][/INDENT]

---

### Post by harfin on 2017-10-26
ls -al /usr/src/

```
harfin@harfin-HP-255-G1-Notebook-PC:~$ ls -al /usr/src/
total 24
drwxr-xr-x  6 root root 4096 Oct 11 21:19 .
drwxr-xr-x 12 root root 4096 Aug  8  2016 ..
drwxr-xr-x 27 root root 4096 Sep 18 13:58 linux-headers-4.4.0-96
drwxr-xr-x  7 root root 4096 Sep 18 13:58 linux-headers-4.4.0-96-generic
drwxr-xr-x 27 root root 4096 Oct 11 21:13 linux-headers-4.4.0-97
drwxr-xr-x  7 root root 4096 Oct 11 21:13 linux-headers-4.4.0-97-generic
harfin@harfin-HP-255-G1-Notebook-PC:~$ ls -al /lib/modules/
total 16
drwxr-xr-x  4 root root 4096 Oct 11 21:20 .
drwxr-xr-x 25 root root 4096 Jun 26 10:02 ..
drwxr-xr-x  5 root root 4096 Sep 18 13:59 4.4.0-96-generic
drwxr-xr-x  5 root root 4096 Oct 11 21:17 4.4.0-97-generic
harfin@harfin-HP-255-G1-Notebook-PC:~$ ls -al /boot/
total 129148
drwxr-xr-x  5 root root     3072 Oct 25 20:03 .
drwxr-xr-x 25 root root     4096 Oct 11 21:16 ..
-rw-r--r--  1 root root  1249161 Sep 12 18:59 abi-4.4.0-96-generic
-rw-r--r--  1 root root  1249112 Sep 19 21:29 abi-4.4.0-97-generic
-rw-r--r--  1 root root   190517 Sep 12 18:59 config-4.4.0-96-generic
-rw-r--r--  1 root root   190517 Sep 19 21:29 config-4.4.0-97-generic
drwxr-xr-x  3 root root     4096 Jan  1  1970 efi
drwxr-xr-x  5 root root     1024 Oct 11 21:20 grub
-rw-r--r--  1 root root 10955110 Oct 25 20:03 initrd.img-4.4.0-81-generic
-rw-r--r--  1 root root 40551635 Oct 25 20:03 initrd.img-4.4.0-96-generic
-rw-r--r--  1 root root 40555778 Oct 25 20:02 initrd.img-4.4.0-97-generic
drwx------  2 root root    12288 Jan 28  2015 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3886723 Sep 12 18:59 System.map-4.4.0-96-generic
-rw-------  1 root root  3886693 Sep 19 21:29 System.map-4.4.0-97-generic
-rw-------  1 root root  7101968 Sep 12 18:59 vmlinuz-4.4.0-96-generic
-rw-------  1 root root  7103896 Sep 18 14:00 vmlinuz-4.4.0-96-generic.efi.signed
-rw-------  1 root root  7102864 Sep 19 21:29 vmlinuz-4.4.0-97-generic
-rw-------  1 root root  7104792 Oct 11 21:18 vmlinuz-4.4.0-97-generic.efi.signed
```

---

### Post by harfin on 2017-10-26
ls -al /lib/modules/
```
harfin@harfin-HP-255-G1-Notebook-PC:~$ ls -al /lib/modules/total 16
drwxr-xr-x  4 root root 4096 Oct 11 21:20 .
drwxr-xr-x 25 root root 4096 Jun 26 10:02 ..
drwxr-xr-x  5 root root 4096 Sep 18 13:59 4.4.0-96-generic
drwxr-xr-x  5 root root 4096 Oct 11 21:17 4.4.0-97-generic
```
ls -al /boot/
```
harfin@harfin-HP-255-G1-Notebook-PC:~$ ls -al /boot/total 129148
drwxr-xr-x  5 root root     3072 Oct 25 20:03 .
drwxr-xr-x 25 root root     4096 Oct 11 21:16 ..
-rw-r--r--  1 root root  1249161 Sep 12 18:59 abi-4.4.0-96-generic
-rw-r--r--  1 root root  1249112 Sep 19 21:29 abi-4.4.0-97-generic
-rw-r--r--  1 root root   190517 Sep 12 18:59 config-4.4.0-96-generic
-rw-r--r--  1 root root   190517 Sep 19 21:29 config-4.4.0-97-generic
drwxr-xr-x  3 root root     4096 Jan  1  1970 efi
drwxr-xr-x  5 root root     1024 Oct 11 21:20 grub
-rw-r--r--  1 root root 10955110 Oct 25 20:03 initrd.img-4.4.0-81-generic
-rw-r--r--  1 root root 40551635 Oct 25 20:03 initrd.img-4.4.0-96-generic
-rw-r--r--  1 root root 40555778 Oct 25 20:02 initrd.img-4.4.0-97-generic
drwx------  2 root root    12288 Jan 28  2015 lost+found
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  3886723 Sep 12 18:59 System.map-4.4.0-96-generic
-rw-------  1 root root  3886693 Sep 19 21:29 System.map-4.4.0-97-generic
-rw-------  1 root root  7101968 Sep 12 18:59 vmlinuz-4.4.0-96-generic
-rw-------  1 root root  7103896 Sep 18 14:00 vmlinuz-4.4.0-96-generic.efi.signed
-rw-------  1 root root  7102864 Sep 19 21:29 vmlinuz-4.4.0-97-generic
-rw-------  1 root root  7104792 Oct 11 21:18 vmlinuz-4.4.0-97-generic.efi.signed
```
dpkg -l | grep linux-
```
harfin@harfin-HP-255-G1-Notebook-PC:~$ dpkg -l | grep linux-ii  linux-base                                           4.0ubuntu1                                   all          Linux image base package
ii  linux-firmware                                       1.157.13                                     all          Firmware for Linux kernel drivers
ii  linux-generic                                        4.4.0.97.102                                 amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.4.0-96                               4.4.0-96.119                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-96-generic                       4.4.0-96.119                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-4.4.0-97                               4.4.0-97.120                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-97-generic                       4.4.0-97.120                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
ii  linux-headers-generic                                4.4.0.97.102                                 amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-24-generic                        3.13.0-24.47                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-44-generic                        3.13.0-44.73                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-45-generic                        3.13.0-45.74                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-46-generic                        3.13.0-46.79                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-48-generic                        3.13.0-48.80                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-49-generic                        3.13.0-49.83                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-51-generic                        3.13.0-51.84                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-52-generic                        3.13.0-52.86                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-53-generic                        3.13.0-53.89                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-54-generic                        3.13.0-54.91                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-55-generic                        3.13.0-55.94                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-57-generic                        3.13.0-57.95                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-58-generic                        3.13.0-58.97                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-61-generic                        3.13.0-61.100                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-62-generic                        3.13.0-62.102                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-63-generic                        3.13.0-63.103                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-65-generic                        3.13.0-65.106                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-66-generic                        3.13.0-66.108                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-67-generic                        3.13.0-67.110                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-68-generic                        3.13.0-68.111                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-71-generic                        3.13.0-71.114                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-73-generic                        3.13.0-73.116                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-74-generic                        3.13.0-74.118                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-76-generic                        3.13.0-76.120                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-77-generic                        3.13.0-77.121                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-79-generic                        3.13.0-79.123                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-83-generic                        3.13.0-83.127                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-85-generic                        3.13.0-85.129                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-86-generic                        3.13.0-86.131                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-87-generic                        3.13.0-87.133                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-88-generic                        3.13.0-88.135                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-91-generic                        3.13.0-91.138                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-92-generic                        3.13.0-92.139                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-31-generic                         4.4.0-31.50                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-34-generic                         4.4.0-34.53                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-36-generic                         4.4.0-36.55                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-38-generic                         4.4.0-38.57                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-42-generic                         4.4.0-42.62                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-45-generic                         4.4.0-45.66                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-47-generic                         4.4.0-47.68                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-53-generic                         4.4.0-53.74                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-57-generic                         4.4.0-57.78                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-59-generic                         4.4.0-59.80                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-62-generic                         4.4.0-62.83                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-64-generic                         4.4.0-64.85                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-66-generic                         4.4.0-66.87                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-70-generic                         4.4.0-70.91                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-72-generic                         4.4.0-72.93                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-75-generic                         4.4.0-75.96                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-77-generic                         4.4.0-77.98                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-79-generic                         4.4.0-79.100                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-81-generic                         4.4.0-81.104                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-87-generic                         4.4.0-87.110                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-89-generic                         4.4.0-89.112                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-91-generic                         4.4.0-91.114                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-92-generic                         4.4.0-92.115                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-4.4.0-93-generic                         4.4.0-93.116                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-96-generic                         4.4.0-96.119                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-4.4.0-97-generic                         4.4.0-97.120                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-24-generic                  3.13.0-24.47                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-44-generic                  3.13.0-44.73                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-45-generic                  3.13.0-45.74                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-46-generic                  3.13.0-46.79                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-48-generic                  3.13.0-48.80                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-51-generic                  3.13.0-51.84                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-52-generic                  3.13.0-52.86                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-53-generic                  3.13.0-53.89                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-54-generic                  3.13.0-54.91                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-55-generic                  3.13.0-55.94                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-57-generic                  3.13.0-57.95                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-58-generic                  3.13.0-58.97                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-61-generic                  3.13.0-61.100                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-62-generic                  3.13.0-62.102                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-63-generic                  3.13.0-63.103                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-65-generic                  3.13.0-65.106                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-66-generic                  3.13.0-66.108                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-67-generic                  3.13.0-67.110                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-68-generic                  3.13.0-68.111                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-71-generic                  3.13.0-71.114                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-73-generic                  3.13.0-73.116                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-74-generic                  3.13.0-74.118                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-76-generic                  3.13.0-76.120                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-77-generic                  3.13.0-77.121                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-79-generic                  3.13.0-79.123                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-83-generic                  3.13.0-83.127                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-85-generic                  3.13.0-85.129                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-86-generic                  3.13.0-86.131                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-87-generic                  3.13.0-87.133                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-88-generic                  3.13.0-88.135                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-91-generic                  3.13.0-91.138                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-92-generic                  3.13.0-92.139                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic                   4.4.0-31.50                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-34-generic                   4.4.0-34.53                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-36-generic                   4.4.0-36.55                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-38-generic                   4.4.0-38.57                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-42-generic                   4.4.0-42.62                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic                   4.4.0-45.66                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic                   4.4.0-47.68                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-53-generic                   4.4.0-53.74                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-57-generic                   4.4.0-57.78                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-59-generic                   4.4.0-59.80                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic                   4.4.0-62.83                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-64-generic                   4.4.0-64.85                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-66-generic                   4.4.0-66.87                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-70-generic                   4.4.0-70.91                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-72-generic                   4.4.0-72.93                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-75-generic                   4.4.0-75.96                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-77-generic                   4.4.0-77.98                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-79-generic                   4.4.0-79.100                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-81-generic                   4.4.0-81.104                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-87-generic                   4.4.0-87.110                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-89-generic                   4.4.0-89.112                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-91-generic                   4.4.0-91.114                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-92-generic                   4.4.0-92.115                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
rc  linux-image-extra-4.4.0-93-generic                   4.4.0-93.116                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-96-generic                   4.4.0-96.119                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-extra-4.4.0-97-generic                   4.4.0-97.120                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ii  linux-image-generic                                  4.4.0.97.102                                 amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                                 4.4.0-97.120                                 amd64        Linux Kernel Headers for development
ii  linux-signed-generic                                 4.4.0.97.102                                 amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.13.0-44-generic                 3.13.0-44.73                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-45-generic                 3.13.0-45.74                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-46-generic                 3.13.0-46.79                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-48-generic                 3.13.0-48.80                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-49-generic                 3.13.0-49.83                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-51-generic                 3.13.0-51.84                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-52-generic                 3.13.0-52.86                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-53-generic                 3.13.0-53.89                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-54-generic                 3.13.0-54.91                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-55-generic                 3.13.0-55.94                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-57-generic                 3.13.0-57.95                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-58-generic                 3.13.0-58.97                                 amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-61-generic                 3.13.0-61.100                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-62-generic                 3.13.0-62.102                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-63-generic                 3.13.0-63.103                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-65-generic                 3.13.0-65.106                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-66-generic                 3.13.0-66.108                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-67-generic                 3.13.0-67.110                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-68-generic                 3.13.0-68.111                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-71-generic                 3.13.0-71.114                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-73-generic                 3.13.0-73.116                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-74-generic                 3.13.0-74.118                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-76-generic                 3.13.0-76.120                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-77-generic                 3.13.0-77.121                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-79-generic                 3.13.0-79.123                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-83-generic                 3.13.0-83.127                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-85-generic                 3.13.0-85.129                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-86-generic                 3.13.0-86.131                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-87-generic                 3.13.0-87.133                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-88-generic                 3.13.0-88.135                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-91-generic                 3.13.0-91.138                                amd64        Signed kernel image generic
rc  linux-signed-image-3.13.0-92-generic                 3.13.0-92.139                                amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-31-generic                  4.4.0-31.50                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-34-generic                  4.4.0-34.53                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-36-generic                  4.4.0-36.55                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-38-generic                  4.4.0-38.57                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-42-generic                  4.4.0-42.62                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-45-generic                  4.4.0-45.66                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-47-generic                  4.4.0-47.68                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-53-generic                  4.4.0-53.74                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-57-generic                  4.4.0-57.78                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-59-generic                  4.4.0-59.80                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-62-generic                  4.4.0-62.83                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-64-generic                  4.4.0-64.85                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-66-generic                  4.4.0-66.87                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-70-generic                  4.4.0-70.91                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-72-generic                  4.4.0-72.93                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-75-generic                  4.4.0-75.96                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-77-generic                  4.4.0-77.98                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-78-generic                  4.4.0-78.99                                  amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-79-generic                  4.4.0-79.100                                 amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-81-generic                  4.4.0-81.104                                 amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-87-generic                  4.4.0-87.110                                 amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-89-generic                  4.4.0-89.112                                 amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-91-generic                  4.4.0-91.114                                 amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-92-generic                  4.4.0-92.115                                 amd64        Signed kernel image generic
rc  linux-signed-image-4.4.0-93-generic                  4.4.0-93.116                                 amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-96-generic                  4.4.0-96.119                                 amd64        Signed kernel image generic
ii  linux-signed-image-4.4.0-97-generic                  4.4.0-97.120                                 amd64        Signed kernel image generic
ii  linux-signed-image-generic                           4.4.0.97.102                                 amd64        Signed Generic Linux kernel image
ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                                      3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

---

### Post by harfin on 2017-10-26
uname -r

```
harfin@harfin-HP-255-G1-Notebook-PC:~$ uname -rB^Charfin@harfin-HP-255-G1-Notebook-PC:~$ ^C
harfin@harfin-HP-255-G1-Notebook-PC:~$ harfin@harfin-HP-255-G1-Notebook-PC:~$ dpkg -l | grep linux-
harfin@harfin-HP-255-G1-Notebook-PC:~$: command not found
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-base                                           4.0ubuntu1                                   all          Linux image base package
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-firmware                                       1.157.13                                     all          Firmware for Linux kernel drivers
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-generic                                        4.4.0.97.102                                 amd64        Complete Generic Linux kernel and headers
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-headers-4.4.0-96                               4.4.0-96.119                                 all          Header files related to Linux kernel version 4.4.0
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-headers-4.4.0-96-generic                       4.4.0-96.119                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-headers-4.4.0-97                               4.4.0-97.120                                 all          Header files related to Linux kernel version 4.4.0
-image-3The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-headers-4.4.0-97-generic                       4.4.0-97.120                                 amd64        Linux kernel headers for version 4.4.0 on 64 bit x86 SMP
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-headers-generic                                4.4.0.97.102                                 amd64        Generic Linux kernel headers
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-24-generic                        3.13.0-24.47                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
tThe program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-44-generic                        3.13.0-44.73                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-45-generic                        3.13.0-45.74                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-46-generic                        3.13.0-46.79                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-48-generic                        3.13.0-48.80                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-49-generic                        3.13.0-49.83                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-51-generic                        3.13.0-51.84                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-52-generic                        3.13.0-52.86                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-53-generic                        3.13.0-53.89                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-54-generic                        3.13.0-54.91                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-55-generic                        3.13.0-55.94                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-57-generic                        3.13.0-57.95                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-58-generic                        3.13.0-58.97                                 amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-61-generic                        3.13.0-61.100                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-62-generic                        3.13.0-62.102                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-63-generic                        3.13.0-63.103                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
MThe program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-65-generic                        3.13.0-65.106                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-66-generic                        3.13.0-66.108                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-67-generic                        3.13.0-67.110                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-68-generic                        3.13.0-68.111                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-71-generic                        3.13.0-71.114                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-73-generic                        3.13.0-73.116                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
      amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
rc  The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-74-generic                        3.13.0-74.118                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
lThe program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-76-generic                        3.13.0-76.120                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
c  liThe program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-77-generic                        3.13.0-77.121                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-79-generic                        3.13.0-79.123                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-83-generic                        3.13.0-83.127                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-85-generic                        3.13.0-85.129                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-86-generic                        3.13.0-86.131                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-87-generic                        3.13.0-87.133                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-88-generic                        3.13.0-88.135                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-91-generic                        3.13.0-91.138                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-3.13.0-92-generic                        3.13.0-92.139                                amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-31-generic                         4.4.0-31.50                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-34-generic                         4.4.0-34.53                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-36-generic                         4.4.0-36.55                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-38-generic                         4.4.0-38.57                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-42-generic                         4.4.0-42.62                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-45-generic                         4.4.0-45.66                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-47-generic                         4.4.0-47.68                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-53-generic                         4.4.0-53.74                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
oduleThe program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-57-generic                         4.4.0-57.78                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-59-generic                         4.4.0-59.80                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
              3.13.0-53.89                                 amd64        Linux kThe program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-62-generic                         4.4.0-62.83                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-64-generic                         4.4.0-64.85                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-66-generic                         4.4.0-66.87                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-70-generic                         4.4.0-70.91                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-72-generic                         4.4.0-72.93                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-75-generic                         4.4.0-75.96                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-77-generic                         4.4.0-77.98                                  amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-79-generic                         4.4.0-79.100                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-81-generic                         4.4.0-81.104                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-87-generic                         4.4.0-87.110                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-89-generic                         4.4.0-89.112                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-91-generic                         4.4.0-91.114                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-92-generic                         4.4.0-92.115                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-4.4.0-93-generic                         4.4.0-93.116                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-image-4.4.0-96-generic                         4.4.0-96.119                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
 64The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-image-4.4.0-97-generic                         4.4.0-97.120                                 amd64        Linux kernel image for version 4.4.0 on 64 bit x86 SMP
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-24-generic                  3.13.0-24.47                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-44-generic                  3.13.0-44.73                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-45-generic                  3.13.0-45.74                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
1The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-46-generic                  3.13.0-46.79                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-48-generic                  3.13.0-48.80                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
            amd64        Linux kernel extra modules for version 3.1The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-51-generic                  3.13.0-51.84                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-52-generic                  3.13.0-52.86                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
sion 3.1The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-53-generic                  3.13.0-53.89                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-54-generic                  3.13.0-54.91                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
sion 3.1The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-55-generic                  3.13.0-55.94                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-57-generic                  3.13.0-57.95                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-58-generic                  3.13.0-58.97                                 amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-61-generic                  3.13.0-61.100                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-62-generic                  3.13.0-62.102                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-63-generic                  3.13.0-63.103                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-65-generic                  3.13.0-65.106                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-66-generic                  3.13.0-66.108                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-67-generic                  3.13.0-67.110                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-68-generic                  3.13.0-68.111                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-71-generic                  3.13.0-71.114                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-73-generic                  3.13.0-73.116                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-74-generic                  3.13.0-74.118                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-76-generic                  3.13.0-76.120                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-77-generic                  3.13.0-77.121                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-79-generic                  3.13.0-79.123                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
nux kernel extra modules for version 4.4.0 on 64 bit x8The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-83-generic                  3.13.0-83.127                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
6The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-85-generic                  3.13.0-85.129                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-86-generic                  3.13.0-86.131                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-87-generic                  3.13.0-87.133                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-88-generic                  3.13.0-88.135                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-91-generic                  3.13.0-91.138                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-3.13.0-92-generic                  3.13.0-92.139                                amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rThe program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-31-generic                   4.4.0-31.50                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-34-generic                   4.4.0-34.53                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
modules for version 4.4.0 on 64 bit x86 SMP
iThe program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-36-generic                   4.4.0-36.55                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-38-generic                   4.4.0-38.57                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-42-generic                   4.4.0-42.62                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
.The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-45-generic                   4.4.0-45.66                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
 The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-47-generic                   4.4.0-47.68                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-53-generic                   4.4.0-53.74                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-57-generic                   4.4.0-57.78                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-59-generic                   4.4.0-59.80                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-62-generic                   4.4.0-62.83                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-64-generic                   4.4.0-64.85                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-66-generic                   4.4.0-66.87                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
nThe program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-70-generic                   4.4.0-70.91                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-72-generic                   4.4.0-72.93                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-75-generic                   4.4.0-75.96                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-77-generic                   4.4.0-77.98                                  amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-79-generic                   4.4.0-79.100                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-81-generic                   4.4.0-81.104                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-87-generic                   4.4.0-87.110                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-89-generic                   4.4.0-89.112                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-91-generic                   4.4.0-91.114                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-92-generic                   4.4.0-92.115                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
 The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-image-extra-4.4.0-93-generic                   4.4.0-93.116                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-image-extra-4.4.0-96-generic                   4.4.0-96.119                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-image-extra-4.4.0-97-generic                   4.4.0-97.120                                 amd64        Linux kernel extra modules for version 4.4.0 on 64 bit x86 SMP
ernel image generic
rc  linux-signed-image-3.13.0-83-generic                 3.13.The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-image-generic                                  4.4.0.97.102                                 amd64        Generic Linux kernel image
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-libc-dev:amd64                                 4.4.0-97.120                                 amd64        Linux Kernel Headers for development
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-signed-generic                                 4.4.0.97.102                                 amd64        Complete Signed Generic Linux kernel and headers
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-44-generic                 3.13.0-44.73                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-45-generic                 3.13.0-45.74                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-46-generic                 3.13.0-46.79                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-48-generic                 3.13.0-48.80                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-49-generic                 3.13.0-49.83                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-51-generic                 3.13.0-51.84                                 amd64        Signed kernel image generic
    4.4.0-36.55                       The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-52-generic                 3.13.0-52.86                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-53-generic                 3.13.0-53.89                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-54-generic                 3.13.0-54.91                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-55-generic                 3.13.0-55.94                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-57-generic                 3.13.0-57.95                                 amd64        Signed kernel image generic
eneric                  4.4.0-53.74                       The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-58-generic                 3.13.0-58.97                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-61-generic                 3.13.0-61.100                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-62-generic                 3.13.0-62.102                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-63-generic                 3.13.0-63.103                                amd64        Signed kernel image generic
-64.85                       The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-65-generic                 3.13.0-65.106                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-66-generic                 3.13.0-66.108                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-67-generic                 3.13.0-67.110                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-68-generic                 3.13.0-68.111                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-71-generic                 3.13.0-71.114                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-73-generic                 3.13.0-73.116                                amd64        Signed kernel image generic
        4.4.0-78.99                       The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-74-generic                 3.13.0-74.118                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-76-generic                 3.13.0-76.120                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-77-generic                 3.13.0-77.121                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-79-generic                 3.13.0-79.123                                amd64        Signed kernel image generic
        The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-83-generic                 3.13.0-83.127                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-85-generic                 3.13.0-85.129                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-86-generic                 3.13.0-86.131                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-87-generic                 3.13.0-87.133                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-88-generic                 3.13.0-88.135                                amd64        Signed kernel image generic
       The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-91-generic                 3.13.0-91.138                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-3.13.0-92-generic                 3.13.0-92.139                                amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-31-generic                  4.4.0-31.50                                  amd64        Signed kernel image generic
    3:6.03+dfsg-The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-34-generic                  4.4.0-34.53                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-36-generic                  4.4.0-36.55                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-38-generic                  4.4.0-38.57                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-42-generic                  4.4.0-42.62                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-45-generic                  4.4.0-45.66                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-47-generic                  4.4.0-47.68                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-53-generic                  4.4.0-53.74                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-57-generic                  4.4.0-57.78                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-59-generic                  4.4.0-59.80                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-62-generic                  4.4.0-62.83                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-64-generic                  4.4.0-64.85                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-66-generic                  4.4.0-66.87                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-70-generic                  4.4.0-70.91                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-72-generic                  4.4.0-72.93                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-75-generic                  4.4.0-75.96                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-77-generic                  4.4.0-77.98                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-78-generic                  4.4.0-78.99                                  amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-79-generic                  4.4.0-79.100                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-81-generic                  4.4.0-81.104                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-87-generic                  4.4.0-87.110                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-89-generic                  4.4.0-89.112                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-91-generic                  4.4.0-91.114                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-92-generic                  4.4.0-92.115                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ rc  linux-signed-image-4.4.0-93-generic                  4.4.0-93.116                                 amd64        Signed kernel image generic
The program 'rc' is currently not installed. You can install it by typing:
sudo apt install rc
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-signed-image-4.4.0-96-generic                  4.4.0-96.119                                 amd64        Signed kernel image generic
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-signed-image-4.4.0-97-generic                  4.4.0-97.120                                 amd64        Signed kernel image generic
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-signed-image-generic                           4.4.0.97.102                                 amd64        Signed Generic Linux kernel image
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  linux-sound-base                                     1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  syslinux-common                                      3:6.03+dfsg-11ubuntu1                        all          collection of bootloaders (common)
bash: syntax error near unexpected token `('
harfin@harfin-HP-255-G1-Notebook-PC:~$ ii  syslinux-legacy                                      2:3.63+dfsg-2ubuntu8                         amd64        Bootloader for Linux/i386 using MS-DOS floppies
The program 'ii' is currently not installed. You can install it by typing:
sudo apt install ii



```

---

### Post by harfin on 2017-10-26
I think that's all you asked for!
Alan

---

### Post by Bashing-om on 2017-10-26
harfin; Humm ..

No idea of how that straggler got left behind ; but:
try:
```

sudo rm /boot/initrd.img-4.4.0-81-generic

```

Not a good idea to go behind the package manager's back with a 'rm'. But, in this state the action is warranted .

Now see if the package manager will heal it's self:
```

sudo apt -f install
sudo apt update
sudo apt full-upgrade

```


Maybe Yes
[INDENT][INDENT]could be not so yes[/INDENT][/INDENT]

---

### Post by harfin on 2017-10-26
sudo rm /boot/initrd.img-4.4.0-81-generic harfin@harfin-HP-255-G1-Notebook-PC:~$ sudo rm /boot/initrd.img-4.4.0-81-genericrm: cannot remove '/boot/initrd.img-4.4.0-81-generic': No such file or directory

---

### Post by harfin on 2017-10-26
After the failure of the "[COLOR=#000000]sudo rm /boot/initrd.img-4.4.0-81-generic" I ran the other items and this is the result:
```
 [/COLOR]Reading package lists... DoneBuilding dependency tree       
Reading state information... Done
0 to upgrade, 0 to newly install, 0 to remove and 2 not to upgrade.
harfin@harfin-HP-255-G1-Notebook-PC:~$ sudo apt update
Hit:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease                 
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]     
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main Sources [279 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [644 kB]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [611 kB]
Get:9 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 DEP-11 Metadata [305 kB]
Get:10 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main DEP-11 64x64 Icons [214 kB]
Get:11 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [541 kB]
Get:12 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [516 kB]
Get:13 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 DEP-11 Metadata [173 kB]
Get:14 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe DEP-11 64x64 Icons [240 kB]
Get:15 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 DEP-11 Metadata [5,892 B]
Get:16 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/main amd64 DEP-11 Metadata [3,324 B]
Get:17 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports/universe amd64 DEP-11 Metadata [4,588 B]
Get:18 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main Sources [99.0 kB]
Get:19 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 Packages [374 kB]
Get:20 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main i386 Packages [348 kB]
Get:21 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 DEP-11 Metadata [60.4 kB]
Get:22 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main DEP-11 64x64 Icons [57.6 kB]
Get:23 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe amd64 DEP-11 Metadata [49.7 kB]
Get:24 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/universe DEP-11 64x64 Icons [80.0 kB]
Fetched 4,911 kB in 4s (1,193 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
8 packages can be upgraded. Run 'apt list --upgradable' to see them.
harfin@harfin-HP-255-G1-Notebook-PC:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  distro-info-data flashplugin-installer grub-common grub-efi-amd64
  grub-efi-amd64-bin grub-efi-amd64-signed grub2-common wget
8 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
Need to get 3,550 kB of archives.
After this operation, 7,168 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-efi-amd64-signed amd64 1.66.14+2.02~beta2-36ubuntu3.14 [296 kB]
Get:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-efi-amd64 amd64 2.02~beta2-36ubuntu3.14 [65.9 kB]
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-efi-amd64-bin amd64 2.02~beta2-36ubuntu3.14 [661 kB]
Get:4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security/main amd64 wget amd64 1.17.1-1ubuntu1.3 [299 kB]
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub2-common amd64 2.02~beta2-36ubuntu3.14 [511 kB]
Get:6 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 grub-common amd64 2.02~beta2-36ubuntu3.14 [1,705 kB]
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 distro-info-data all 0.28ubuntu0.5 [4,224 B]
Get:8 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/multiverse amd64 flashplugin-installer amd64 27.0.0.183ubuntu0.16.04.1 [6,806 B]
Fetched 3,550 kB in 1s (3,418 kB/s)         
Preconfiguring packages ...
(Reading database ... 267075 files and directories currently installed.)
Preparing to unpack .../grub-efi-amd64-signed_1.66.14+2.02~beta2-36ubuntu3.14_amd64.deb ...
Unpacking grub-efi-amd64-signed (1.66.14+2.02~beta2-36ubuntu3.14) over (1.66.12+2.02~beta2-36ubuntu3.12) ...
Preparing to unpack .../grub-efi-amd64_2.02~beta2-36ubuntu3.14_amd64.deb ...
Unpacking grub-efi-amd64 (2.02~beta2-36ubuntu3.14) over (2.02~beta2-36ubuntu3.12) ...
Preparing to unpack .../grub-efi-amd64-bin_2.02~beta2-36ubuntu3.14_amd64.deb ...
Unpacking grub-efi-amd64-bin (2.02~beta2-36ubuntu3.14) over (2.02~beta2-36ubuntu3.12) ...
Preparing to unpack .../grub2-common_2.02~beta2-36ubuntu3.14_amd64.deb ...
Unpacking grub2-common (2.02~beta2-36ubuntu3.14) over (2.02~beta2-36ubuntu3.12) ...
Preparing to unpack .../grub-common_2.02~beta2-36ubuntu3.14_amd64.deb ...
Unpacking grub-common (2.02~beta2-36ubuntu3.14) over (2.02~beta2-36ubuntu3.12) ...
Preparing to unpack .../distro-info-data_0.28ubuntu0.5_all.deb ...
Unpacking distro-info-data (0.28ubuntu0.5) over (0.28ubuntu0.4) ...
Preparing to unpack .../wget_1.17.1-1ubuntu1.3_amd64.deb ...
Unpacking wget (1.17.1-1ubuntu1.3) over (1.17.1-1ubuntu1.2) ...
Preparing to unpack .../flashplugin-installer_27.0.0.183ubuntu0.16.04.1_amd64.deb ...
Unpacking flashplugin-installer (27.0.0.183ubuntu0.16.04.1) over (27.0.0.170ubuntu0.16.04.1) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for install-info (6.1.0.dfsg.1-5) ...
Processing triggers for systemd (229-4ubuntu20) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for update-notifier-common (3.168.5) ...
flashplugin-installer: processing...
flashplugin-installer: downloading [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20171025.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20171025.1.orig.tar.gz)
Get:1 [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20171025.1.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_20171025.1.orig.tar.gz) [30.4 MB]
Fetched 30.4 MB in 9s (3,173 kB/s)                                             
W: Can't drop privileges for downloading as file '/var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20171025.1.orig.tar.gz' couldn't be accessed by user '_apt'. - pkgAcquire::Run (13: Permission denied)
Installing from local file /var/lib/update-notifier/package-data-downloads/partial/adobe-flashplugin_20171025.1.orig.tar.gz
Flash Plugin installed.
Setting up grub-common (2.02~beta2-36ubuntu3.14) ...
update-rc.d: warning: start and stop actions are no longer supported; falling back to defaults
Setting up grub2-common (2.02~beta2-36ubuntu3.14) ...
Setting up grub-efi-amd64-bin (2.02~beta2-36ubuntu3.14) ...
Setting up grub-efi-amd64 (2.02~beta2-36ubuntu3.14) ...
Installing for x86_64-efi platform.
Installation finished. No error reported.
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-96-generic
Found initrd image: /boot/initrd.img-4.4.0-96-generic
Adding boot menu entry for EFI firmware configuration
done
Setting up grub-efi-amd64-signed (1.66.14+2.02~beta2-36ubuntu3.14) ...
Installing for x86_64-efi platform.
Installation finished. No error reported.
Setting up distro-info-data (0.28ubuntu0.5) ...
Setting up wget (1.17.1-1ubuntu1.3) ...
Setting up flashplugin-installer (27.0.0.183ubuntu0.16.04.1) ...
Processing triggers for shim-signed (1.32~16.04.1+0.9+1474479173.6c180c6-1ubuntu1) ...
No DKMS packages installed: not changing Secure Boot validation state.



[COLOR=#000000] 
```
[/COLOR]

---

### Post by ian-weisser on 2017-10-26
The command only failed the second time. It worked the first time - that's why there was no feedback.
Your original problem looks fixed.

---

### Post by Bashing-om on 2017-10-26
@harfin; :)

The only other thing I can suggest is to clean up all that residual cruft:

While there is no built in way to remove all of your configuration information from your removed packages you can remove all configuration data from every removed package. To purge all removed but not yet purged packages, where The state is rc, the package is removed, but the config files are not removed....with the following command.

```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

@ian-weisser: Where would I be without you ! Hope you do not mind me taking care of the light work :)

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by deadflowr on 2017-10-26
Please use code tags when posting the output from any command.
(Click on Reply to Thread and then use the # symbol to use code tags.
Code tags retains proper formatting, quote tags does not)

---

### Post by harfin on 2017-10-26
? 

I am lost!

Should I run that command now?  (i.e. [COLOR=#000000][FONT=&quot]dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P")?

Alan[/FONT][/COLOR]

---

### Post by Bashing-om on 2017-10-26
harfin; Well.

'rc' files are not a problem . just cruft.
But I do like to keep it all clean and remove this cruft.
to see the results of the command run in terminal"
```

dpkg -l | grep linux- 

```

now run the dpkg command:
```

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

And re-run " dpkg -l | grep linux-" . 

[INDENT][INDENT]see the difference
[/INDENT][/INDENT]

---

### Post by harfin on 2017-10-26
Ahah!
I am very grateful for all of your guidance!
Regards
Alan

---

### Post by Bashing-om on 2017-10-26
harfin; Hey

> 
I am very grateful for all of your guidance!


Glad to help as help is what we do.

If this matter is concluded to your satisfaction ->
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]see, ain't nothing but a thing
[/INDENT][/INDENT]

---

