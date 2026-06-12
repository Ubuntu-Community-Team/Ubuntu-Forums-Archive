---
title: "Update manager failure and ubuntu crash"
date: 2016-12-07
forum: Installation &amp; Upgrades
---

### Post by Gingalone on 2016-12-07
Yesterday after an update process I got a Software Updater crash, it looks it's something that has to do with Linux headers package... A first window says: "the package system is broken"
Then the crash report title reads: ```
"update-manager  crashed with linux-headers-generic in_show_trasaction(): Depends: linux-headers-3.13.0-105-generic but it is not installed".
```
I tried to fix the problem with Synaptic but got another error warning from it: 
```
An error occurred
E: /var/cache/apt/archives/linux-headers-3.13.0-105-generic_3.13.0-105.152_i386.deb: unable to create `/usr/src/linux-headers-3.13.0-105-generic/include/config/reed/solomon/dec16.h.dpkg-new' (while processing `./usr/src/linux-headers-3.13.0-105-generic/include/config/reed/solomon/dec16.h'): No space left on device

```
I was surprised from the "No space left on device" statement since there is plenty of space on system disks...
Any idea???

---

### Post by howefield on 2016-12-07
Could be that /boot is full hence the "No space left on device" rather than the entirety of your system disks.

What's the output of..

```
df -i
```
```
df -h /boot
```

---

### Post by Gingalone on 2016-12-07
Thank you awefield, here's the output of the commands you suggested:
```
sudo df -i
[sudo] password for ginus: 
Filesystem             Inodes   IUsed    IFree IUse% Mounted on
udev                   196206     557   195649    1% /dev
tmpfs                  202895     609   202286    1% /run
/dev/sdb1             1466368 1466364        4  100% /
none                   202895       2   202893    1% /sys/fs/cgroup
none                   202895       3   202892    1% /run/lock
none                   202895      61   202834    1% /run/shm
none                   202895      30   202865    1% /run/user
/dev/sda3            28393472  177612 28215860    1% /home
/dev/sda2             1525920   15119  1510801    1% /var
/home/ginus/.Private 28393472  177612 28215860    1% /home/ginus

sudo df -h /boot
[sudo] password for ginus: 
Filesystem      Size  Used Avail Use% Mounted on
/dev/sdb1        22G   20G  1,8G  92% /
```
It looks your diagnose correct and that I should free (how?) some space in sdb1 (which is a SSD disk) I never save files in that disk and so don't know how it went full of stuff...

---

### Post by howefield on 2016-12-07
Try to free up some inodes to allow you to properly update and upgrade.

Header packages use up thousands of inodes, so find and remove some of them..

```
dpkg -l | grep linux-headers
```

to list all installed headers packages and remove the oldest ones, do not remove the currently running ones. If you are not sure post back with the results of the dpkg command and also the output of..

```
uname -r
```

---

### Post by Gingalone on 2016-12-08
Thank you Howefield, in the attached file there is the output of the dpkg command you suggested (a lot of stuff there, 86 lines!) and the other: ```
uname -r
3.13.0-103-generic
``` I need some hint on the inodes to delete (I'm not that ubuntu expert!)

---

### Post by ian-weisser on 2016-12-08
It's better to paste than to attach.

```
ii  linux-headers-3.13.0-100                              3.13.0-100.147                                      all          Header files related to Linux kernel version 3.13.0ii  linux-headers-3.13.0-100-generic                      3.13.0-100.147                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-101                              3.13.0-101.148                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-101-generic                      3.13.0-101.148                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-103                              3.13.0-103.150                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-103-generic                      3.13.0-103.150                                      i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-105                              3.13.0-105.152                                      all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-44                               3.13.0-44.73                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-44-generic                       3.13.0-44.73                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-45                               3.13.0-45.74                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-45-generic                       3.13.0-45.74                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-46                               3.13.0-46.79                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-46-generic                       3.13.0-46.79                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-48                               3.13.0-48.80                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-48-generic                       3.13.0-48.80                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-49                               3.13.0-49.83                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-49-generic                       3.13.0-49.83                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-51                               3.13.0-51.84                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-51-generic                       3.13.0-51.84                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-52                               3.13.0-52.86                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-52-generic                       3.13.0-52.86                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-53                               3.13.0-53.89                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-53-generic                       3.13.0-53.89                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-55                               3.13.0-55.94                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-55-generic                       3.13.0-55.94                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-57                               3.13.0-57.95                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-57-generic                       3.13.0-57.95                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-58                               3.13.0-58.97                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-58-generic                       3.13.0-58.97                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-59                               3.13.0-59.98                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-59-generic                       3.13.0-59.98                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-61                               3.13.0-61.100                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-61-generic                       3.13.0-61.100                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-62                               3.13.0-62.102                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-62-generic                       3.13.0-62.102                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-63                               3.13.0-63.103                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-63-generic                       3.13.0-63.103                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-65                               3.13.0-65.106                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-65-generic                       3.13.0-65.106                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-66                               3.13.0-66.108                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-66-generic                       3.13.0-66.108                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-67                               3.13.0-67.110                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-67-generic                       3.13.0-67.110                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-68                               3.13.0-68.111                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-68-generic                       3.13.0-68.111                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-71                               3.13.0-71.114                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-71-generic                       3.13.0-71.114                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-73                               3.13.0-73.116                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-73-generic                       3.13.0-73.116                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-74                               3.13.0-74.118                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic                       3.13.0-74.118                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-76                               3.13.0-76.120                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-76-generic                       3.13.0-76.120                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-77                               3.13.0-77.121                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-77-generic                       3.13.0-77.121                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-79                               3.13.0-79.123                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-79-generic                       3.13.0-79.123                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-83                               3.13.0-83.127                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-83-generic                       3.13.0-83.127                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-85                               3.13.0-85.129                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-85-generic                       3.13.0-85.129                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-86                               3.13.0-86.131                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-86-generic                       3.13.0-86.131                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-87                               3.13.0-87.133                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-87-generic                       3.13.0-87.133                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-88                               3.13.0-88.135                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-88-generic                       3.13.0-88.135                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-91                               3.13.0-91.138                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-91-generic                       3.13.0-91.138                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-92                               3.13.0-92.139                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-92-generic                       3.13.0-92.139                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-93                               3.13.0-93.140                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-93-generic                       3.13.0-93.140                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-95                               3.13.0-95.142                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-95-generic                       3.13.0-95.142                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-96                               3.13.0-96.143                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-96-generic                       3.13.0-96.143                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-98                               3.13.0-98.145                                       all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-98-generic                       3.13.0-98.145                                       i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
iU  linux-headers-generic                                 3.13.0.105.113                                      i386         Generic Linux kernel headers
```

Here is an example of how to remove the oldest set of kernel headers:
```
sudo dpkg --remove linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
```

Repeat for the -44, -45, -46, -48, etc headers.

After the first or second, you should have enough free space to use apt again.
Once apt is working, run the following to clear more additional space by removing orphaned packages and cached packages:
```
sudo apt autoremove
sudo apt autoclean
```

In addition to looking at linux-header package, look for obsolete linux-image packages, too.
DO NOT remove your currently-running kernel. That would be very very bad.
Best practice is to retain one older kernel in case of breakage.
Remove the rest exactly the same way you uninstalled the kernel-header packages. (apt autoremove should have dome most of this work for you)

Finally, survey the results of your effort.
Run 'df' again and see how much space you have freed.

---

### Post by Gingalone on 2016-12-09
Thank you ian-weisser, i did
```
sudo dpkg --remove linux-headers-3.13.0-32 linux-headers-3.13.0-32-generic
``` removing a lot of headers (up to 79)
then I rebooted, but afterwords the apt commands were unsuccessful```
sudo apt autoremove
[sudo] password for ginus: 
E: Invalid operation autoremove
sudo apt autoclean
E: Invalid operation autoclean
``` and the problem is just there: broken system pakage...

---

### Post by ian-weisser on 2016-12-09
Ah, you are using an older release of Ubuntu.
Use 'apt-get' instead of 'apt' for autoremove and autoclean.

Please show us an entire apt-get output showing the 'broken system package' error and you you got the error.

---

### Post by Gingalone on 2016-12-10
> **ian-weisser said:**
> Please show us an entire apt-get output showing the 'broken system package' error and you you got the error.here we go:```
sudo apt-get autoremove
[sudo] password for ginus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-headers-generic : Depends: linux-headers-3.13.0-105-generic but it is not installed
E: Unmet dependencies. Try using -f.

sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del gstreamer1.0-pulseaudio 1.2.4-1~ubuntu1.1 [48,9 kB]
Del linux-image-generic 3.13.0.101.109 [2.324 B]
Del linux-tools-virtual-lts-vivid 3.19.0.74.56 [2.342 B]
Del libmagickcore5-extra 8:6.7.7.10-6ubuntu3.2 [55,0 kB]
Del libgstreamer-plugins-good1.0-0 1.2.4-1~ubuntu1.1 [30,9 kB]
Del linux-image-generic 3.13.0.103.111 [2.322 B]
Del linux-generic 3.13.0.101.109 [1.786 B]
Del gstreamer0.10-pulseaudio 0.10.31-3+nmu1ubuntu5.1 [98,8 kB]
Del libmagickwand5 8:6.7.7.10-6ubuntu3.2 [235 kB]
Del libmagickcore5 8:6.7.7.10-6ubuntu3.2 [1.386 kB]
Del ghostscript 9.10~dfsg-0ubuntu10.5 [40,8 kB]
Del firefox 50.0+build2-0ubuntu0.14.04.2 [45,2 MB]
Del libgstreamer-plugins-bad0.10-0 0.10.23-7.2ubuntu1.2 [132 kB]
Del linux-headers-generic 3.13.0.103.111 [2.302 B]
Del linux-headers-generic 3.13.0.101.109 [2.320 B]
Del linux-libc-dev 3.13.0-101.148 [770 kB]
Del linux-libc-dev 3.13.0-103.150 [771 kB]
Del gstreamer0.10-gconf 0.10.31-3+nmu1ubuntu5.1 [68,0 kB]
Del gstreamer0.10-plugins-good 0.10.31-3+nmu1ubuntu5.1 [1.344 kB]
Del firefox-locale-en 50.0+build2-0ubuntu0.14.04.2 [646 kB]
Del gstreamer0.10-plugins-bad 0.10.23-7.2ubuntu1.2 [1.137 kB]
Del imagemagick-common 8:6.7.7.10-6ubuntu3.2 [37,8 kB]
Del gstreamer1.0-plugins-good 1.2.4-1~ubuntu1.1 [1.260 kB]
Del ghostscript-x 9.10~dfsg-0ubuntu10.5 [33,2 kB]
Del libgs9-common 9.10~dfsg-0ubuntu10.5 [2.066 kB]
Del linux-tools-virtual-lts-vivid 3.19.0.75.57 [2.328 B]
Del linux-generic 3.13.0.103.111 [1.782 B]
Del imagemagick 8:6.7.7.10-6ubuntu3.2 [188 kB]
Del libgs9 9.10~dfsg-0ubuntu10.5 [1.892 kB]
Del samba 2:4.1.6+dfsg-1ubuntu2.14.04.13 [999 B]
Del libwbclient0 2:4.1.6+dfsg-1ubuntu2.14.04.13 [999 B]
Del thunderbird-locale-en-us 1:38.6.0+build1-0ubuntu0.14.04.1 [999 B]
Del libsmbclient 2:4.1.6+dfsg-1ubuntu2.14.04.13 [999 B]
Del thunderbird-gnome-support 1:38.6.0+build1-0ubuntu0.14.04.1 [999 B]
Del thunderbird-locale-en 1:38.6.0+build1-0ubuntu0.14.04.1 [999 B]
Del thunderbird 1:38.6.0+build1-0ubuntu0.14.04.1 [999 B]
Del samba-vfs-modules 2:4.1.6+dfsg-1ubuntu2.14.04.13 [999 B]
Del samba-dsdb-modules 2:4.1.6+dfsg-1ubuntu2.14.04.13 [999 B]
Del python-samba 2:4.1.6+dfsg-1ubuntu2.14.04.13 [999 B]
Del samba-common 2:4.1.6+dfsg-1ubuntu2.14.04.13 [999 B]
Del samba-libs 2:4.1.6+dfsg-1ubuntu2.14.04.13 [999 B]

```
Then, as suggested by apt-get, I did```
sudo apt-get -f install
```
Then I made run the update manager and got no "Broken system package" warning!
Solved, thank you!

---

