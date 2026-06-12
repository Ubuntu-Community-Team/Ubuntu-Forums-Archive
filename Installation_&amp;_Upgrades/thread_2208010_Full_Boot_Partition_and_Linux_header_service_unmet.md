---
title: "Full Boot Partition and Linux header service unmet dependencies"
date: 2014-02-26
forum: Installation &amp; Upgrades
---

### Post by atrh on 2014-02-26
I know how to solve one problem at at time. Now, both of these problems happening to my Ubuntu server 12.04 and giving me headache.

Boot partition is full and I can't autoremove or manual purge the old kernel image. I can't also solve the dependency problem by installing new required packages. Any ideas? 

```

$uname -r
3.2.0-56-generic

```
```

$ sudo dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name                 Version              Description
+++-====================-====================-========================================================
un  linux-image          <none>               (no description available)
un  linux-image-3.0      <none>               (no description available)
ii  linux-image-3.2.0-23 3.2.0-23.36          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-34 3.2.0-34.53          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35 3.2.0-35.55          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-36 3.2.0-36.57          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-37 3.2.0-37.58          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-38 3.2.0-38.61          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-39 3.2.0-39.62          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-40 3.2.0-40.64          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-41 3.2.0-41.66          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-43 3.2.0-43.68          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-44 3.2.0-44.69          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
in  linux-image-3.2.0-52 <none>               (no description available)
in  linux-image-3.2.0-53 <none>               (no description available)
ii  linux-image-3.2.0-55 3.2.0-55.85          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-56 3.2.0-56.86          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-57 3.2.0-57.87          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
iF  linux-image-3.2.0-58 3.2.0-58.88          Linux kernel image for version 3.2.0 on 64 bit x86 SMP
in  linux-image-3.2.0-59 <none>               (no description available)
iU  linux-image-generic  3.2.0.57.68          Generic Linux kernel image
iU  linux-image-server   3.2.0.57.68          Linux kernel image on Server Equipment.


```

```

$sudo apt-get autoremove

Reading package lists... Done
Building dependency tree... 50%
Building dependency tree
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 linux-server : Depends: linux-headers-server (= 3.2.0.57.68) but 3.2.0.59.70 is installed
E: Unmet dependencies. Try using -f.


```

```

$df -l

Filesystem              1K-blocks     Used Available Use% Mounted on
/dev/mapper/CENTEX-root 147341808 80607744  59249444  58% /
udev                      3563752        8   3563744   1% /dev
tmpfs                     1429136      276   1428860   1% /run
none                         5120        0      5120   0% /run/lock
none                      3572832        0   3572832   0% /run/shm
/dev/sda1                  233191   229887         0 100% /boot

```

---

### Post by oldfred on 2014-02-26
If a server with out a desktop then you have to use command line to purge older kernels.

 Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)
cd /boot
ls vmlinuz*
sudo apt-get purge  linux-image-[version]-generic linux-image-[version]-generic
Multiples, just be sure not to delete your current kernel:
sudo apt-get purge linux-image-3.5.0-{XX,XX,XX,XX,XX,XX}-generic
Example:
sudo apt-get purge linux-image-3.5.0-{17,18,19,21,22,23,24}-generic

And then you have to empty trash.

 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

If old kernels not still in dpkg, then you have to delete each file manually and empty root trash.

---

