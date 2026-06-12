---
title: "Broken packages linux image"
date: 2019-05-24
forum: Installation &amp; Upgrades
---

### Post by sawyer_ipg on 2019-05-24
Hello. Can someone help me with this? I'm at my wits end. I tried to clean these broken packages. I've tried all the suggested methods that I found (copy n paste) such as:

```
sudo apt-get purge 
sudo apt-get install -f
sudo dpkg --force-all -p linux image (returned not availabe)
```
etc

 linux-image-4.15.0-43-generic
 linux-image-4.15.0-50-generic

```
sudo apt-get autoremove

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.15.0-43-generic linux-image-4.15.0-50-generic
0 upgraded, 0 newly installed, 2 to remove and 12 not upgraded.
2 not fully installed or removed.
After this operation, 16.6 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 201216 files and directories currently installed.)
Removing linux-image-4.15.0-43-generic (4.15.0-43.46) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-43-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 5: /etc/default/grub: ate-grub afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n Simple: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-4.15.0-43-generic (--remove):
 installed linux-image-4.15.0-43-generic package post-removal script subprocess returned error exit status 1
Removing linux-image-4.15.0-50-generic (4.15.0-50.54) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-50-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
/usr/sbin/grub-mkconfig: 5: /etc/default/grub: ate-grub afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n Simple: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-4.15.0-50-generic (--remove):
 installed linux-image-4.15.0-50-generic package post-removal script subprocess returned error exit status 1
Errors were encountered while processing:
 linux-image-4.15.0-43-generic
 linux-image-4.15.0-50-generic
E: Sub-process /usr/bin/dpkg returned an error code (1) 
```

The problem started after my disk was almost full during auto update in synaptic manager.

Thank you in advance.

---

### Post by sawyer_ipg on 2019-05-24
I am just a script kiddie. Hence, things I've done might not be effective for my situation. So, any help would be appreciated.

---

### Post by Bashing-om on 2019-05-24
sawyer_ipg; Hello -

Let's see what we can do. :)

For diagnostic purposes please post back - Between code tags ! -
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

the outputs of terminal commands:
```

df -h
df -i
dpkg -l | grep linux-
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/

```

we make up then a process
[INDENT]and just do it
[/INDENT]

---

### Post by sawyer_ipg on 2019-05-25
Here you go.

```
df -h

Filesystem      Size  Used Avail Use% Mounted on
udev            3.8G     0  3.8G   0% /dev
tmpfs           782M  2.0M  780M   1% /run
/dev/sda4        31G   23G  6.2G  79% /
tmpfs           3.9G   25M  3.8G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs           3.9G     0  3.9G   0% /sys/fs/cgroup
/dev/loop0      3.8M  3.8M     0 100% /snap/gnome-system-monitor/70
/dev/loop1       13M   13M     0 100% /snap/gnome-characters/139
/dev/loop2      1.0M  1.0M     0 100% /snap/gnome-logs/61
/dev/loop3      185M  185M     0 100% /snap/eclipse/40
/dev/loop5      3.8M  3.8M     0 100% /snap/gnome-system-monitor/57
/dev/loop7       90M   90M     0 100% /snap/core/6673
/dev/loop6      202M  202M     0 100% /snap/polar-bookshelf/54
/dev/loop8      141M  141M     0 100% /snap/gnome-3-26-1604/74
/dev/loop4      203M  203M     0 100% /snap/vlc/770
/dev/loop12     7.3M  7.3M     0 100% /snap/tuition-manager/9
/dev/loop10      60M   60M     0 100% /snap/notes/4
/dev/loop9      4.2M  4.2M     0 100% /snap/gnome-calculator/352
/dev/loop14      13M   13M     0 100% /snap/speed-test/31
/dev/loop11      35M   35M     0 100% /snap/gtk-common-themes/1122
/dev/loop13      35M   35M     0 100% /snap/gtk-common-themes/818
/dev/loop15     141M  141M     0 100% /snap/gnome-3-26-1604/78
/dev/loop16      54M   54M     0 100% /snap/core18/782
/dev/loop17     174M  174M     0 100% /snap/spotify/34
/dev/loop20      15M   15M     0 100% /snap/gnome-characters/254
/dev/loop23     152M  152M     0 100% /snap/gnome-3-28-1804/31
/dev/loop18      54M   54M     0 100% /snap/core18/941
/dev/loop24     1.0M  1.0M     0 100% /snap/gnome-logs/57
/dev/loop32      15M   15M     0 100% /snap/gnome-characters/206
/dev/loop25     2.3M  2.3M     0 100% /snap/gnome-calculator/260
/dev/loop28      15M   15M     0 100% /snap/gnome-logs/45
/dev/loop30     4.8M  4.8M     0 100% /snap/network-manager/379
/dev/loop19     141M  141M     0 100% /snap/gnome-3-26-1604/82
/dev/loop21     152M  152M     0 100% /snap/gnome-3-28-1804/36
/dev/loop22     3.8M  3.8M     0 100% /snap/gnome-system-monitor/77
/dev/loop29     193M  193M     0 100% /snap/eclipse/29
/dev/loop27     4.2M  4.2M     0 100% /snap/gnome-calculator/406
/dev/loop31      94M   94M     0 100% /snap/telegram-desktop/715
/dev/loop26      91M   91M     0 100% /snap/core/6405
/dev/loop33      94M   94M     0 100% /snap/telegram-desktop/663
/dev/loop34     202M  202M     0 100% /snap/polar-bookshelf/52
/dev/loop35     144M  144M     0 100% /snap/gnome-3-28-1804/23
/dev/loop36      36M   36M     0 100% /snap/gtk-common-themes/1198
/dev/loop37      92M   92M     0 100% /snap/core/6531
/dev/sda1       296M   39M  258M  13% /boot/efi
tmpfs           782M   28K  782M   1% /run/user/1000
```

```
df -i

Filesystem      Inodes  IUsed   IFree IUse% Mounted on
udev            995527    641  994886    1% /dev
tmpfs          1000735   1249  999486    1% /run
/dev/sda4      2028000 468222 1559778   24% /
tmpfs          1000735     41 1000694    1% /dev/shm
tmpfs          1000735      5 1000730    1% /run/lock
tmpfs          1000735     18 1000717    1% /sys/fs/cgroup
/dev/loop0         734    734       0  100% /snap/gnome-system-monitor/70
/dev/loop1        1598   1598       0  100% /snap/gnome-characters/139
/dev/loop2         354    354       0  100% /snap/gnome-logs/61
/dev/loop3        1578   1578       0  100% /snap/eclipse/40
/dev/loop5         747    747       0  100% /snap/gnome-system-monitor/57
/dev/loop7       12819  12819       0  100% /snap/core/6673
/dev/loop6       10131  10131       0  100% /snap/polar-bookshelf/54
/dev/loop8       27631  27631       0  100% /snap/gnome-3-26-1604/74
/dev/loop4       44811  44811       0  100% /snap/vlc/770
/dev/loop12       1062   1062       0  100% /snap/tuition-manager/9
/dev/loop10      15913  15913       0  100% /snap/notes/4
/dev/loop9        1549   1549       0  100% /snap/gnome-calculator/352
/dev/loop14       4553   4553       0  100% /snap/speed-test/31
/dev/loop11      24092  24092       0  100% /snap/gtk-common-themes/1122
/dev/loop13      27345  27345       0  100% /snap/gtk-common-themes/818
/dev/loop15      27631  27631       0  100% /snap/gnome-3-26-1604/78
/dev/loop16       9862   9862       0  100% /snap/core18/782
/dev/loop17      23723  23723       0  100% /snap/spotify/34
/dev/loop20        271    271       0  100% /snap/gnome-characters/254
/dev/loop23      27705  27705       0  100% /snap/gnome-3-28-1804/31
/dev/loop18       9883   9883       0  100% /snap/core18/941
/dev/loop24        354    354       0  100% /snap/gnome-logs/57
/dev/loop32        271    271       0  100% /snap/gnome-characters/206
/dev/loop25       1269   1269       0  100% /snap/gnome-calculator/260
/dev/loop28       1720   1720       0  100% /snap/gnome-logs/45
/dev/loop30        122    122       0  100% /snap/network-manager/379
/dev/loop19      27631  27631       0  100% /snap/gnome-3-26-1604/82
/dev/loop21      27705  27705       0  100% /snap/gnome-3-28-1804/36
/dev/loop22        734    734       0  100% /snap/gnome-system-monitor/77
/dev/loop29       1650   1650       0  100% /snap/eclipse/29
/dev/loop27       1550   1550       0  100% /snap/gnome-calculator/406
/dev/loop31       9859   9859       0  100% /snap/telegram-desktop/715
/dev/loop26      12816  12816       0  100% /snap/core/6405
/dev/loop33       9859   9859       0  100% /snap/telegram-desktop/663
/dev/loop34      10131  10131       0  100% /snap/polar-bookshelf/52
/dev/loop35      27707  27707       0  100% /snap/gnome-3-28-1804/23
/dev/loop36      25385  25385       0  100% /snap/gtk-common-themes/1198
/dev/loop37      12815  12815       0  100% /snap/core/6531
/dev/sda1            0      0       0     - /boot/efi
tmpfs          1000735     32 1000703    1% /run/user/1000
```

```
dpkg -l | grep linux-

ii  binutils-x86-64-linux-gnu                  2.30-21ubuntu1~18.04.1                       amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                 4.5ubuntu1                                   all          Linux image base package
ii  linux-firmware                             1.173.6                                      all          Firmware for Linux kernel drivers
ii  linux-headers-4.15.0-47                    4.15.0-47.50                                 all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-47-generic            4.15.0-47.50                                 amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-50                    4.15.0-50.54                                 all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-50-generic            4.15.0-50.54                                 amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                      4.15.0.50.52                                 amd64        Generic Linux kernel headers
ic  linux-image-4.15.0-42-generic              4.15.0-42.45                                 amd64        Signed kernel image generic
iH  linux-image-4.15.0-43-generic              4.15.0-43.46                                 amd64        Signed kernel image generic
ii  linux-image-4.15.0-47-generic              4.15.0-47.50                                 amd64        Signed kernel image generic
iH  linux-image-4.15.0-50-generic              4.15.0-50.54                                 amd64        Signed kernel image generic
ii  linux-libc-dev:amd64                       4.15.0-50.54                                 amd64        Linux Kernel Headers for development
rc  linux-modules-4.15.0-29-generic            4.15.0-29.31                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-42-generic            4.15.0-42.45                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-43-generic            4.15.0-43.46                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-47-generic            4.15.0-47.50                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-50-generic            4.15.0-50.54                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-29-generic      4.15.0-29.31                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-42-generic      4.15.0-42.45                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-43-generic      4.15.0-43.46                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-47-generic      4.15.0-47.50                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ic  linux-modules-extra-4.15.0-50-generic      4.15.0-50.54                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                            3:6.03+dfsg1-2                               all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu9                         amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

```
ls -al /usr/src/

total 28
drwxr-xr-x  7 root root 4096 Mei  22 14:10 .
drwxr-xr-x 10 root root 4096 Jul  25  2018 ..
drwxr-xr-x 27 root root 4096 Apr  16 15:46 linux-headers-4.15.0-47
drwxr-xr-x  8 root root 4096 Apr  16 15:46 linux-headers-4.15.0-47-generic
drwxr-xr-x 27 root root 4096 Mei  22 07:00 linux-headers-4.15.0-50
drwxr-xr-x  8 root root 4096 Mei  22 07:00 linux-headers-4.15.0-50-generic
drwxr-xr-x  8 root root 4096 Mac  23 13:44 nvidia-390.116
```

```
ls -al /lib/modules/

total 24
drwxr-xr-x  6 root root 4096 Mei  24 20:44 .
drwxr-xr-x 22 root root 4096 Dis  11 20:06 ..
drwxr-xr-x  2 root root 4096 Apr  17 06:27 4.15.0-42-generic
drwxr-xr-x  5 root root 4096 Mei  24 20:45 4.15.0-43-generic
drwxr-xr-x  6 root root 4096 Apr  16 15:47 4.15.0-47-generic
drwxr-xr-x  5 root root 4096 Mei  24 20:47 4.15.0-50-generic
```

```
ls -al /boot/

total 56528
drwxr-xr-x  4 root root     4096 Mei  24 20:54 .
drwxr-xr-x 24 root root     4096 Mei  24 21:04 ..
-rw-r--r--  1 root root   217018 Dis   6 21:52 config-4.15.0-43-generic
-rw-r--r--  1 root root   216996 Mac  13 12:37 config-4.15.0-47-generic
-rw-r--r--  1 root root   217278 Mei   7 00:59 config-4.15.0-50-generic
drwxr-xr-x  6 root root     4096 Jan   1  1970 efi
drwxr-xr-x  5 root root     4096 Mei  23 23:36 grub
-rw-r--r--  1 root root 36201006 Mei  24 20:54 initrd.img-4.15.0-47-generic
-rw-r--r--  1 root root   182704 Jan  28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan  28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan  28  2016 memtest86+_multiboot.bin
-rw-------  1 root root  4048162 Dis   6 21:52 System.map-4.15.0-43-generic
-rw-------  1 root root  4050630 Mac  13 12:37 System.map-4.15.0-47-generic
-rw-------  1 root root  4053204 Mei   7 00:59 System.map-4.15.0-50-generic
-rw-------  1 root root  8290040 Mac  13 12:43 vmlinuz-4.15.0-47-generic
```

It do look clean!

---

### Post by dino99 on 2019-05-25
As a 'script kiddie' you might have disturbed the whole system.
Myself i avoid the 'snap' install; its a work in progress and really too instable.
I'm a synaptic fan to manage the system update/upgrade, and nowadays apt deals very well with dupes (kernels in your case).
Maybe you will be able to downgrade to a genuine install; i suppose you have already used 'sudo rm -f ...' from a path to get ride of all these dupes.

Start with the usuel clean/autoclean/autoremove/gtkorphan to clean the system, then run 'sudo dpkg --configure -a'

---

### Post by Impavidus on 2019-05-25
It doesn't look too bad, but I see two problems:> **sawyer_ipg said:**
> 

```
sudo apt-get autoremove

[...]

Removing linux-image-4.15.0-43-generic (4.15.0-43.46) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-4.15.0-43-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
**/usr/sbin/grub-mkconfig: 5: /etc/default/grub: ate-grub afterwards to update**
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n Simple: not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
```
That looks like a damaged **/etc/default/grub**. Show the contents of that file and it may be easy to fix:```
cat /etc/default/grub
```
This problem has to be fixed first, because as long as it persists, every attempt to install or remove a kernel will fail.

> **sawyer_ipg said:**
> 
```
dpkg -l | grep linux-

ii  binutils-x86-64-linux-gnu                  2.30-21ubuntu1~18.04.1                       amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                 4.5ubuntu1                                   all          Linux image base package
ii  linux-firmware                             1.173.6                                      all          Firmware for Linux kernel drivers
ii  linux-headers-4.15.0-47                    4.15.0-47.50                                 all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-47-generic            4.15.0-47.50                                 amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-50                    4.15.0-50.54                                 all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-50-generic            4.15.0-50.54                                 amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                      4.15.0.50.52                                 amd64        Generic Linux kernel headers
ic  linux-image-4.15.0-42-generic              4.15.0-42.45                                 amd64        Signed kernel image generic
iH  linux-image-4.15.0-43-generic              4.15.0-43.46                                 amd64        Signed kernel image generic
ii  linux-image-4.15.0-47-generic              4.15.0-47.50                                 amd64        Signed kernel image generic
iH  linux-image-4.15.0-50-generic              4.15.0-50.54                                 amd64        Signed kernel image generic
ii  linux-libc-dev:amd64                       4.15.0-50.54                                 amd64        Linux Kernel Headers for development
rc  linux-modules-4.15.0-29-generic            4.15.0-29.31                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-42-generic            4.15.0-42.45                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-43-generic            4.15.0-43.46                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-47-generic            4.15.0-47.50                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-50-generic            4.15.0-50.54                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-29-generic      4.15.0-29.31                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-42-generic      4.15.0-42.45                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-43-generic      4.15.0-43.46                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-47-generic      4.15.0-47.50                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ic  linux-modules-extra-4.15.0-50-generic      4.15.0-50.54                                 amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5                         all          base package for ALSA and OSS sound systems
ii  syslinux-common                            3:6.03+dfsg1-2                               all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu9                         amd64        Bootloader for Linux/i386 using MS-DOS floppies
```

It do look clean!
Two packages are half installed (set to be installed) and two packages only have config files (set to be installed). Also, the linux-generic and linux-image-generic metapackages are missing, probably removed during an attempt to remove the kernel on which they depended. This should be trivial to fix.

---

### Post by sawyer_ipg on 2019-05-25
Thanks.

Got problems after Windows 10 and Ubuntu update. Did Ubuntu first, then Windows. Since, then couldn't load grub unless I use the advance restart on WIndows. It just went straight to Windows during booting. Secure and fast boot are disabled did not work too.

```
cat /etc/default/grub

# If you change this file, run 'upd
ate-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=10
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX="nouveau.modeset=0"

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
```

I'd modified this section since it caused black screen the after the installation of Ubuntu:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=force"
GRUB_CMDLINE_LINUX="nouveau.modeset=0"
```

I wonder why is it hard to remove these broken packages since I do not even use it.

---

### Post by sawyer_ipg on 2019-05-25
Solved it. Damn naughty GRUB. Thanks everyone.

---

### Post by Impavidus on 2019-05-26
There's a stray newline character in your /etc/default/grub. Edit the first lines to make them read:```

# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

```
That should fix it. Then install the package **linux-generic**. That will pull in kernel updates.

---

### Post by sawyer_ipg on 2019-05-29
That solved it. Thanks.

---

