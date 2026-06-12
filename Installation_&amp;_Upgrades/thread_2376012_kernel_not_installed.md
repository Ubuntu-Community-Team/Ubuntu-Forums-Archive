---
title: "kernel not installed"
date: 2017-10-29
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2017-10-29
I guess this Lubuntu  has same kernel after update for months,
my acquaintance said that my Lubuntu will not install newer kernel, 
do you the fix?

here is output after shut down,

taro@taro-HP-Mini-110-3000:~$ sudo apt update
[sudo] password for taro:
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease
Reading package lists... Done
Building dependency tree
Reading state information... Done
All packages are up to date.
taro@taro-HP-Mini-110-3000:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
taro@taro-HP-Mini-110-3000:~$ uname -a
Linux taro-HP-Mini-110-3000 4.4.0-75-generic #96-Ubuntu SMP Thu Apr 20 09:55:15 UTC 2017 i686 i686 i686 GNU/Linux
taro@taro-HP-Mini-110-3000:~$

---

### Post by Bashing-om on 2017-10-29
Matrix01; Hello;

Is a puzzle - 

as the current 16.04 kernel:
> 
sysop@x1604:~$ uname -r
4.4.0-97-generic
sysop@x1604:~$


So, let's see what we can find out why you are not current.
Post back - Between code Tags - the outputs of terminal commands:
```

cat -n /etc/apt/sources.list
dpkg -l | grep linux-

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

as a place to start the investigation.

[INDENT][INDENT]gotta be a cause
[/INDENT][/INDENT]

---

### Post by deadflowr on 2017-10-29
uname commands only list what's currently in use.
It does not list what is installed.
look at
```
ls /boot
dpkg -l linux-image* | awk '{print $1,$2}'
```
the system won't run into a new kernel until you reboot.

Also, as a caveat the bootloader program, GRUB, needs to be updated in order for the system to see the new kernel.
If you have a dual or multi boot system you need to make sure that the system that controls the bootloader program, GRUB, has been properly updated.

---

### Post by Matrix01 on 2017-10-29
```
taro@taro-HP-Mini-110-3000:~$ cat -n /etc/apt/sources.list
     1    #deb cdrom:[Lubuntu 16.04.1 LTS _Xenial Xerus_ - Release i386 (20160720)]/ xenial main multiverse restricted universe
     2    
     3    # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
     4    # newer versions of the distribution.
     5    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
     6    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial main restricted
     7    
     8    ## Major bug fix updates produced after the final release of the
     9    ## distribution.
    10    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    11    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates main restricted
    12    
    13    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    14    ## team, and may not be under a free licence. Please satisfy yourself as to
    15    ## your rights to use the software. Also, please note that software in
    16    ## universe WILL NOT receive any review or updates from the Ubuntu security
    17    ## team.
    18    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
    19    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial universe
    20    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
    21    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates universe
    22    
    23    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    24    ## team, and may not be under a free licence. Please satisfy yourself as to 
    25    ## your rights to use the software. Also, please note that software in 
    26    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    27    ## security team.
    28    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
    29    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial multiverse
    30    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    31    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-updates multiverse
    32    
    33    ## N.B. software from this repository may not have been tested as
    34    ## extensively as that contained in the main release, although it includes
    35    ## newer versions of some applications which may provide useful features.
    36    ## Also, please note that software in backports WILL NOT receive any review
    37    ## or updates from the Ubuntu security team.
    38    deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    39    # deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) xenial-backports main restricted universe multiverse
    40    
    41    ## Uncomment the following two lines to add software from Canonical's
    42    ## 'partner' repository.
    43    ## This software is not part of Ubuntu, but is offered by Canonical and the
    44    ## respective vendors as a service to Ubuntu users.
    45    # deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    46    # deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial partner
    47    
    48    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    49    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security main restricted
    50    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    51    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security universe
    52    deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
    53    # deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security multiverse
```
```
taro@taro-HP-Mini-110-3000:~$ dpkg -l | grep linux-
ii  linux-base                            4.0ubuntu1                                 all          Linux image base package
ii  linux-firmware                        1.157.13                                   all          Firmware for Linux kernel drivers
ii  linux-headers-4.4.0-64                4.4.0-64.85                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-64-generic        4.4.0-64.85                                i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-75                4.4.0-75.96                                all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-75-generic        4.4.0-75.96                                i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-4.4.0-31-generic          4.4.0-31.50                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-4.4.0-43-generic          4.4.0-43.63                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-4.4.0-45-generic          4.4.0-45.66                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-4.4.0-47-generic          4.4.0-47.68                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-64-generic          4.4.0-64.85                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-75-generic          4.4.0-75.96                                i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-31-generic    4.4.0-31.50                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-43-generic    4.4.0-43.63                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-45-generic    4.4.0-45.66                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-47-generic    4.4.0-47.68                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-51-generic    4.4.0-51.72                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-57-generic    4.4.0-57.78                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-62-generic    4.4.0-62.83                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-64-generic    4.4.0-64.85                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-75-generic    4.4.0-75.96                                i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-sound-base                      1.0.25+dfsg-0ubuntu5                       all          base package for ALSA and OSS sound systems
ii  syslinux-common                       3:6.03+dfsg-11ubuntu1                      all          collection of bootloaders (common)
ii  syslinux-legacy                       2:3.63+dfsg-2ubuntu8                       i386         Bootloader for Linux/i386 using MS-DOS floppies
taro@taro-HP-Mini-110-3000:~$
```

this netbook has simple single boot, only Lubuntu,

```
taro@taro-HP-Mini-110-3000:~$ ls /boot
abi-4.4.0-64-generic         memtest86+.bin
abi-4.4.0-75-generic         memtest86+.elf
config-4.4.0-64-generic      memtest86+_multiboot.bin
config-4.4.0-75-generic      System.map-4.4.0-64-generic
grub                 System.map-4.4.0-75-generic
initrd.img-4.4.0-64-generic  vmlinuz-4.4.0-64-generic
initrd.img-4.4.0-75-generic  vmlinuz-4.4.0-75-generic
taro@taro-HP-Mini-110-3000:~$
``` 
```
taro@taro-HP-Mini-110-3000:~$ dpkg -l linux-image* | awk '{print $1,$2}'
Desired=Unknown/Install/Remove/Purge/Hold 
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required
||/ Name
+++-==================================-============-============-============================================================== 
un linux-image
rc linux-image-4.4.0-31-generic
rc linux-image-4.4.0-43-generic
rc linux-image-4.4.0-45-generic
rc linux-image-4.4.0-47-generic
un linux-image-4.4.0-51-generic
un linux-image-4.4.0-57-generic
un linux-image-4.4.0-62-generic
ii linux-image-4.4.0-64-generic
ii linux-image-4.4.0-75-generic
rc linux-image-extra-4.4.0-31-generic
rc linux-image-extra-4.4.0-43-generic
rc linux-image-extra-4.4.0-45-generic
rc linux-image-extra-4.4.0-47-generic
rc linux-image-extra-4.4.0-51-generic
rc linux-image-extra-4.4.0-57-generic
rc linux-image-extra-4.4.0-62-generic
ii linux-image-extra-4.4.0-64-generic
ii linux-image-extra-4.4.0-75-generic
taro@taro-HP-Mini-110-3000:~$ 
```
> **deadflowr said:**
> uname commands only list what's currently in use.
It does not list what is installed.
look at
```
ls /boot
dpkg -l linux-image* | awk '{print $1,$2}'
```
the system won't run into a new kernel until you reboot.

Also, as a caveat the bootloader program, GRUB, needs to be updated in order for the system to see the new kernel.
If you have a dual or multi boot system you need to make sure that the system that controls the bootloader program, GRUB, has been properly updated.

---

### Post by Bashing-om on 2017-10-29
Matrix01; Hey hey ...

use code tags please . what we do is difficult enough as is .

try:
```

sudo apt update
sudo apt install linux-generic
sudo apt full-upgrade

```
where I have the hope that linux-image-generic and linux-headers-generic will also be pulled in as dependencies .

Still a bit of clean up to remove some cruft .

Maybe yes
-could be not so yes-

---

### Post by Matrix01 on 2017-10-30
```
taro@taro-HP-Mini-110-3000:~$ sudo apt update
[sudo] password for taro: 
Get:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease [102 kB]
Hit:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial InRelease
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates InRelease [102 kB]    
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-backports InRelease [102 kB]  
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [611 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [516 kB]
Fetched 1,433 kB in 1min 5s (22.0 kB/s)                                        
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
taro@taro-HP-Mini-110-3000:~$ sudo apt install linux-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  linux-headers-4.4.0-97 linux-headers-4.4.0-97-generic linux-headers-generic
  linux-image-4.4.0-97-generic linux-image-extra-4.4.0-97-generic
  linux-image-generic thermald
Suggested packages:
  fdutils linux-doc-4.4.0 | linux-source-4.4.0 linux-tools
The following NEW packages will be installed:
  linux-generic linux-headers-4.4.0-97 linux-headers-4.4.0-97-generic
  linux-headers-generic linux-image-4.4.0-97-generic
  linux-image-extra-4.4.0-97-generic linux-image-generic thermald
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 67.1 MB of archives.
After this operation, 240 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-image-4.4.0-97-generic i386 4.4.0-97.120 [20.6 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-image-extra-4.4.0-97-generic i386 4.4.0-97.120 [35.7 MB]
Get:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-image-generic i386 4.4.0.97.102 [2,284 B]
Get:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-headers-4.4.0-97 all 4.4.0-97.120 [9,921 kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-headers-4.4.0-97-generic i386 4.4.0-97.120 [770 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-headers-generic i386 4.4.0.97.102 [2,264 B]
Get:7 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 linux-generic i386 4.4.0.97.102 [1,790 B]
Get:8 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial-updates/main i386 thermald i386 1.5-2ubuntu4 [193 kB]
Fetched 67.1 MB in 6min 27s (173 kB/s)                                         
Selecting previously unselected package linux-image-4.4.0-97-generic.
(Reading database ... 162674 files and directories currently installed.)
Preparing to unpack .../linux-image-4.4.0-97-generic_4.4.0-97.120_i386.deb ...
Done.
Unpacking linux-image-4.4.0-97-generic (4.4.0-97.120) ...
Selecting previously unselected package linux-image-extra-4.4.0-97-generic.
Preparing to unpack .../linux-image-extra-4.4.0-97-generic_4.4.0-97.120_i386.deb ...
Unpacking linux-image-extra-4.4.0-97-generic (4.4.0-97.120) ...
Selecting previously unselected package linux-image-generic.
Preparing to unpack .../linux-image-generic_4.4.0.97.102_i386.deb ...
Unpacking linux-image-generic (4.4.0.97.102) ...
Selecting previously unselected package linux-headers-4.4.0-97.
Preparing to unpack .../linux-headers-4.4.0-97_4.4.0-97.120_all.deb ...
Unpacking linux-headers-4.4.0-97 (4.4.0-97.120) ...
Selecting previously unselected package linux-headers-4.4.0-97-generic.
Preparing to unpack .../linux-headers-4.4.0-97-generic_4.4.0-97.120_i386.deb ...
Unpacking linux-headers-4.4.0-97-generic (4.4.0-97.120) ...
Selecting previously unselected package linux-headers-generic.
Preparing to unpack .../linux-headers-generic_4.4.0.97.102_i386.deb ...
Unpacking linux-headers-generic (4.4.0.97.102) ...
Selecting previously unselected package linux-generic.
Preparing to unpack .../linux-generic_4.4.0.97.102_i386.deb ...
Unpacking linux-generic (4.4.0.97.102) ...
Selecting previously unselected package thermald.
Preparing to unpack .../thermald_1.5-2ubuntu4_i386.deb ...
Unpacking thermald (1.5-2ubuntu4) ...
Processing triggers for man-db (2.7.5-1) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for ureadahead (0.100.0-19) ...
ureadahead will be reprofiled on next reboot
Processing triggers for systemd (229-4ubuntu21) ...
Setting up linux-image-4.4.0-97-generic (4.4.0-97.120) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-extra-4.4.0-97-generic (4.4.0-97.120) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-97-generic /boot/vmlinuz-4.4.0-97-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-97-generic
Found initrd image: /boot/initrd.img-4.4.0-97-generic
Found linux image: /boot/vmlinuz-4.4.0-75-generic
Found initrd image: /boot/initrd.img-4.4.0-75-generic
Found linux image: /boot/vmlinuz-4.4.0-64-generic
Found initrd image: /boot/initrd.img-4.4.0-64-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up linux-image-generic (4.4.0.97.102) ...
Setting up linux-headers-4.4.0-97 (4.4.0-97.120) ...
Setting up linux-headers-4.4.0-97-generic (4.4.0-97.120) ...
Setting up linux-headers-generic (4.4.0.97.102) ...
Setting up linux-generic (4.4.0.97.102) ...
Setting up thermald (1.5-2ubuntu4) ...
Processing triggers for dbus (1.10.6-1ubuntu3.3) ...
Processing triggers for systemd (229-4ubuntu21) ...
Processing triggers for ureadahead (0.100.0-19) ...
taro@taro-HP-Mini-110-3000:~$ sudo apt full-upgrade
[sudo] password for taro: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-64 linux-headers-4.4.0-64-generic
  linux-image-4.4.0-64-generic linux-image-extra-4.4.0-64-generic
Use 'sudo apt autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
taro@taro-HP-Mini-110-3000:~$
```

---

### Post by Bashing-om on 2017-10-30
Matrix01; Ho Kay :)

Looks good to me ..

Reboot and see that you now boot the -97 kernel:
```

uname -r

```

[INDENT][INDENT]were nothing but a thing[/INDENT][/INDENT]

---

### Post by Matrix01 on 2017-10-30
4.4.0-97-generic

thanks bunch!

---

### Post by Bashing-om on 2017-10-30
Matrix01;

Help is what we do :)

If this matter is now concluded to your satisfaction -
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]'buntu
[INDENT][INDENT][INDENT]all for 1
one for all[/INDENT][/INDENT][/INDENT][/INDENT]

---

