---
title: "Having problems freeing space in /boot"
date: 2022-07-07
forum: Installation &amp; Upgrades
---

### Post by elpidiovaldez5 on 2022-07-07
I am using Lubuntu 20.04.  For some time I have been having problems with automatic updates which seem to be due to a lack of free space in /boot.  I have been following a procedure to free space, but that does not work either.  I'd appreciate some help fixing the system.

Based on what I have read the following should explain the problem:

```
paul@clio:~$ df -i
Filesystem        Inodes   IUsed     IFree IUse% Mounted on
udev             4090392     758   4089634    1% /dev
tmpfs            4098333    1275   4097058    1% /run
/dev/nvme0n1p3  31195136 1011315  30183821    4% /
tmpfs            4098333      84   4098249    1% /dev/shm
tmpfs            4098333       7   4098326    1% /run/lock
tmpfs            4098333      18   4098315    1% /sys/fs/cgroup
tmpfs            4098333      41   4098292    1% /tmp
/dev/loop1         10849   10849         0  100% /snap/core18/2344
/dev/loop2         11789   11789         0  100% /snap/core20/1494
/dev/loop3         10857   10857         0  100% /snap/core18/2409
/dev/loop4         11789   11789         0  100% /snap/core20/1518
/dev/loop5         27806   27806         0  100% /snap/gnome-3-28-1804/161
/dev/loop0            29      29         0  100% /snap/bare/5
/dev/loop7           486     486         0  100% /snap/snapd/16010
/dev/loop6         16536   16536         0  100% /snap/libreoffice/254
/dev/loop8         17504   17504         0  100% /snap/gnome-3-38-2004/106
/dev/nvme0n1p2     34240     326     33914    1% /boot
/dev/nvme0n1p1         0       0         0     - /boot/efi
/dev/loop9           486     486         0  100% /snap/snapd/16292
/dev/loop10        76208   76208         0  100% /snap/gtk-common-themes/1535
/dev/loop11        27807   27807         0  100% /snap/gnome-3-28-1804/145
/dev/loop12        76177   76177         0  100% /snap/gtk-common-themes/1534
/dev/loop13        18120   18120         0  100% /snap/gnome-3-38-2004/112
/dev/loop14        17144   17144         0  100% /snap/libreoffice/256
tmpfs            4098333      46   4098287    1% /run/user/1000
/dev/sdb1      900416964 2700844 897716120    1% /media/paul/Seagate Backup Plus Drive
```

```
paul@clio:~$ ls -l /boot
total 496124
-rw-r--r-- 1 root root    237942 Feb  3 18:16 config-5.4.0-100-generic
-rw-r--r-- 1 root root    237975 Mar 24 15:48 config-5.4.0-107-generic
-rw-r--r-- 1 root root    237975 Apr  8 09:44 config-5.4.0-109-generic
-rw-r--r-- 1 root root    237975 Apr 14 13:19 config-5.4.0-110-generic
-rw-r--r-- 1 root root    237975 May 18 15:07 config-5.4.0-113-generic
-rw-r--r-- 1 root root    237975 Jun 15 14:13 config-5.4.0-121-generic
-rw-r--r-- 1 root root    237940 Feb  2 16:21 config-5.4.0-99-generic
drwx------ 3 root root      4096 Jan  1  1970 efi
drwxr-xr-x 4 root root      4096 Apr 16 16:20 grub
-rw------- 1 root root  57334711 Mar 31 18:32 initrd.img-5.4.0-100-generic
-rw------- 1 root root  57335089 Mar 31 18:34 initrd.img-5.4.0-107-generic
-rw------- 1 root root 116016571 Aug 25  2021 initrd.img-5.4.0-77-generic
-rw------- 1 root root 116021855 Sep  8  2021 initrd.img-5.4.0-81-generic
-rw------- 1 root root  57331389 Mar 31 18:33 initrd.img-5.4.0-99-generic
drwx------ 2 root root     16384 Jan 22  2021 lost+found
-rw-r--r-- 1 root root    182704 Aug 18  2020 memtest86+.bin
-rw-r--r-- 1 root root    184380 Aug 18  2020 memtest86+.elf
-rw-r--r-- 1 root root    184884 Aug 18  2020 memtest86+_multiboot.bin
-rw------- 1 root root   4758018 Feb  3 18:16 System.map-5.4.0-100-generic
-rw------- 1 root root   4759409 Mar 24 15:48 System.map-5.4.0-107-generic
-rw------- 1 root root   4759493 Apr  8 09:44 System.map-5.4.0-109-generic
-rw------- 1 root root   4759819 Apr 14 13:19 System.map-5.4.0-110-generic
-rw------- 1 root root   4759899 May 18 15:07 System.map-5.4.0-113-generic
-rw------- 1 root root   4761203 Jun 15 14:13 System.map-5.4.0-121-generic
-rw------- 1 root root   4757200 Feb  2 16:21 System.map-5.4.0-99-generic
lrwxrwxrwx 1 root root        25 May 12 17:50 vmlinuz -> vmlinuz-5.4.0-110-generic
-rw------- 1 root root  13664512 Feb  4 17:04 vmlinuz-5.4.0-100-generic
-rw------- 1 root root  13664512 Mar 24 15:52 vmlinuz-5.4.0-107-generic
-rw------- 1 root root  13668608 Apr  8 09:45 vmlinuz-5.4.0-109-generic
-rw------- 1 root root  13668608 Apr 14 13:56 vmlinuz-5.4.0-110-generic
-rw------- 1 root root  13660416 Feb  2 16:23 vmlinuz-5.4.0-99-generic
lrwxrwxrwx 1 root root        25 May 12 17:50 vmlinuz.old -> vmlinuz-5.4.0-109-generic
```

```
paul@clio:~$ sudo apt --purge autoremove
[sudo] password for paul:                                                                                                                 
Reading package lists... Done                                                                                                             
Building dependency tree                                                                                                                  
Reading state information... Done                                                                                                         
You might want to run 'apt --fix-broken install' to correct these.                                                                        
The following packages have unmet dependencies.                                                                                           
 linux-image-generic : Depends: linux-image-5.4.0-121-generic but it is not installed                                                     
 linux-modules-extra-5.4.0-113-generic : Depends: linux-image-5.4.0-113-generic but it is not installed or                                
                                                  linux-image-unsigned-5.4.0-113-generic but it is not installed                          
 linux-modules-extra-5.4.0-121-generic : Depends: linux-image-5.4.0-121-generic but it is not installed or                                
                                                  linux-image-unsigned-5.4.0-121-generic but it is not installed                          
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).  
```

```
paul@clio:~$ uname -r                                                                                                                     
5.4.0-107-generic 
```

I have not tried 'apt --fix-broken install' yet, as I don't understand what it will do, and my top priority is not to break anything more ! I would appreciate some explanation and advice.

---

### Post by vanadium on 2022-07-08
You have a separate boot partition, and too many old kernels lingering around. An old kernel occupies about 500 Mb, so that counts up. Your output does not show that: for a reason unknow, you select to use the "-i" (inode) switch. I however take the freedom to assume that the root partition has no free space anymore.

The problem is that probably your `apt` will not work because it always needs some free space. I nevertheless would attempt with `sudo apt --purge autoremove` first, because that may remove old kernels. If it succeeds, you will have free space again on the /boot partition. If that does not work, you will need to proceed to removal as described in the [official Ubuntu documentation](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels).

---

### Post by elpidiovaldez5 on 2022-07-08
Many thanks for your help.  Sorry I posted output of df -i by mistake.  Here is the correct output (shows /boot is full).

```
paul@clio:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
tmpfs           3.2G  2.2M  3.2G   1% /run
/dev/nvme0n1p3  468G  137G  307G  31% /
tmpfs            16G   43M   16G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
tmpfs            16G   17M   16G   1% /tmp
/dev/loop1       56M   56M     0 100% /snap/core18/2344
/dev/loop2       62M   62M     0 100% /snap/core20/1494
/dev/loop3       56M   56M     0 100% /snap/core18/2409
/dev/loop4       62M   62M     0 100% /snap/core20/1518
/dev/loop5      165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop0      128K  128K     0 100% /snap/bare/5
/dev/loop7       47M   47M     0 100% /snap/snapd/16010
/dev/loop6      918M  918M     0 100% /snap/libreoffice/254
/dev/loop8      255M  255M     0 100% /snap/gnome-3-38-2004/106
/dev/nvme0n1p2  510M  494M     0 100% /boot
/dev/nvme0n1p1  532M  5.3M  527M   1% /boot/efi
/dev/loop9       47M   47M     0 100% /snap/snapd/16292
/dev/loop10      92M   92M     0 100% /snap/gtk-common-themes/1535
/dev/loop11     163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop12      82M   82M     0 100% /snap/gtk-common-themes/1534
/dev/loop13     401M  401M     0 100% /snap/gnome-3-38-2004/112
/dev/loop14     915M  915M     0 100% /snap/libreoffice/256
tmpfs           3.2G   16K  3.2G   1% /run/user/1000
/dev/sdb1       1.9T 1008G  856G  55% /media/paul/Seagate Backup Plus Drive
```

I have previously attempted to use *sudo apt-get autoremove --purge*. The results are shown in my previous message.  It failed.

I tried to follow the procedure in [https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels]("https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels").  This also failed.  The output is below:

```
paul@clio:~$ uname -r
5.4.0-107-generic
paul@clio:~$ dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+'
pi  linux-image-5.4.0-100-generic                 5.4.0-100.113                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-107-generic                 5.4.0-107.121                        amd64        Signed kernel image generic
iF  linux-image-5.4.0-109-generic                 5.4.0-109.123                        amd64        Signed kernel image generic
iF  linux-image-5.4.0-110-generic                 5.4.0-110.124                        amd64        Signed kernel image generic
rc  linux-image-5.4.0-96-generic                  5.4.0-96.109                         amd64        Signed kernel image generic
pi  linux-image-5.4.0-99-generic                  5.4.0-99.112                         amd64        Signed kernel image generic
paul@clio:~$ sudo update-initramfs -d -k 5.4.0-99-generic
[sudo] password for paul: 
update-initramfs: Deleting /boot/initrd.img-5.4.0-99-generic
paul@clio:~$ sudo dpkg --purge linux-image-5.4.0-99-generic
dpkg: dependency problems prevent removal of linux-image-5.4.0-99-generic:
 linux-modules-extra-5.4.0-99-generic depends on linux-image-5.4.0-99-generic | linux-image-unsigned-5.4.0-99-generic; however:
  Package linux-image-5.4.0-99-generic is to be removed.
  Package linux-image-unsigned-5.4.0-99-generic is not installed.

dpkg: error processing package linux-image-5.4.0-99-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-5.4.0-99-generic
paul@clio:~$ sudo dpkg --purge linux-image-5.4.0-99-generic linux-image-extra-5.4.0-99-generic
dpkg: dependency problems prevent removal of linux-image-5.4.0-99-generic:
 linux-modules-extra-5.4.0-99-generic depends on linux-image-5.4.0-99-generic | linux-image-unsigned-5.4.0-99-generic; however:
  Package linux-image-5.4.0-99-generic is to be removed.
  Package linux-image-unsigned-5.4.0-99-generic is not installed.

dpkg: error processing package linux-image-5.4.0-99-generic (--purge):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-image-extra-5.4.0-99-generic which isn't installed
Errors were encountered while processing:
 linux-image-5.4.0-99-generic
```

I have been wrestling with the problem of freeing space in /boot for some time.  I think many failed attempts have caused damage to the package structures - I presume pi means 'partially installed'.

---

### Post by TheFu on 2022-07-08
Well, then you should manually remove/purge each specific kernel package that is old.  Leave the last 2 working kernels.

Kernels packages typically have modules and header packages that are matched. When the kernel is removed, the match modules and headers can/should be removed too.

There are many different ways to accomplish this.  For most people, using Synaptic (a GUI package manager) will be the easiest.  But if you didn't pre-install that already, you are sorta screwed.

Start with
```
$ sudo apt purge linux-image-5.4.0-9*
$ sudo apt purge linux-image-5.4.0-10[0-6]*  linux-image-5.4.0-109-generic linux-image-5.4.0-110-generic
$ sudo apt autoremove purge
```
DO NOT REBOOT!  It could go bad.  That should leave just the linux-image-5.4.0-107-generic kernel, which appears to be what you are booted into.  You can verify that with uname -r

```
$ sudo apt update
```
should install 1 new kernel, cleanly.  If it doesn't, don't reboot and post back here the errors.

---

### Post by Impavidus on 2022-07-08
You have to remove the linux-image-..., the linux-modules-... and linux-modules-extra-... packages. Not the linux-image-extra-... package, which isn't installed. The way how kernels are packaged changed some time ago, so there may still be old guides around telling you to remove linux-image-extra-...

linux-image-... cannot be removed before linux-modules-extra-... (because the latter depends on the former) and linux-modules-... cannot be removed before linux-image-..., so if you want to remove all three of them separately, the order is linux-modules-extra-..., linux-image-..., linux-modules-..., but you can tell dpkg to remove all of them at the same time.

You currently run kernel 5.4.0-107, so I suggest you remove 5.4.0-99, -100 and -109, then use apt to fix things (which will fully install -110). And then a regular upgrade should also install -121. After rebooting, remove -107, but that should work the normal way. And remove the header packages.

```
sudo apt update
sudo dpkg --purge linux-modules-extra-5.4.0-99-generic linux-image-5.4.0-99-generic linux-modules-5.4.0-99-generic
# The same for -100 and -109
sudo apt install -f
sudo apt upgrade
```

---

### Post by elpidiovaldez5 on 2022-07-08
Many thanks for your advice.  I tried the purge and update ideas.  There were a few hiccups, but I did free some space and manage to update the system.  Now my system will boot 5.4.0-121-generic, but only in recovery mode.  I kind of expected this, since some of the hiccups wer complaining about nvidia packages.

The current state of my system is:

```
paul@clio:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
udev             16G     0   16G   0% /dev
tmpfs           3.2G  2.1M  3.2G   1% /run
/dev/nvme0n1p3  468G  136G  309G  31% /
tmpfs            16G   48M   16G   1% /dev/shm
tmpfs           5.0M  4.0K  5.0M   1% /run/lock
tmpfs            16G     0   16G   0% /sys/fs/cgroup
tmpfs            16G  620K   16G   1% /tmp
/dev/nvme0n1p2  510M  449M   25M  95% /boot
/dev/nvme0n1p1  532M  5.3M  527M   1% /boot/efi
/dev/loop0      128K  128K     0 100% /snap/bare/5
/dev/loop2      163M  163M     0 100% /snap/gnome-3-28-1804/145
/dev/loop1       56M   56M     0 100% /snap/core18/2409
/dev/loop5       62M   62M     0 100% /snap/core20/1494
/dev/loop4      401M  401M     0 100% /snap/gnome-3-38-2004/112
/dev/loop3      165M  165M     0 100% /snap/gnome-3-28-1804/161
/dev/loop7      915M  915M     0 100% /snap/libreoffice/256
/dev/loop6       92M   92M     0 100% /snap/gtk-common-themes/1535
/dev/loop8       56M   56M     0 100% /snap/core18/2344
/dev/loop9       62M   62M     0 100% /snap/core20/1518
/dev/loop10      82M   82M     0 100% /snap/gtk-common-themes/1534
/dev/loop11     255M  255M     0 100% /snap/gnome-3-38-2004/106
/dev/loop12      47M   47M     0 100% /snap/snapd/16292
/dev/loop13     918M  918M     0 100% /snap/libreoffice/254
/dev/loop14      47M   47M     0 100% /snap/snapd/16010
tmpfs           3.2G   12K  3.2G   1% /run/user/1000
/dev/sdb1       1.9T 1008G  856G  55% /media/paul/Seagate Backup Plus Drive
```

Installed kernels are:

```
paul@clio:~$ dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+'
ii  linux-image-5.4.0-107-generic                 5.4.0-107.121                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-110-generic                 5.4.0-110.124                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-121-generic                 5.4.0-121.137                        amd64        Signed kernel image generic

```

kernel 107 no longer boots.

kernel 121 will boot using nouveau drivers, but all the nvidia drivers complain of dependency errors.

```
pk-client-error-quark: The following packages have unmet dependencies:
  nvidia-driver-515: Depends: libnvidia-gl-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-extra-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-decode-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-encode-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: xserver-xorg-video-nvidia-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-cfg1-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-fbc1-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Recommends: libnvidia-compute-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
                     Recommends: libnvidia-decode-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
                     Recommends: libnvidia-encode-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
                     Recommends: libnvidia-fbc1-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
                     Recommends: libnvidia-gl-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
 (268)

```

I have minimal space left in /boot, and need to be really careful not to destroy the system now that kernel 107 no longer works.

What do you think I should do now ?

---

### Post by elpidiovaldez5 on 2022-07-08
I also tried installing the nvidia package and got the following output:

```
paul@clio:~$ sudo apt install nvidia-driver-515
[sudo] password for paul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 nvidia-driver-515 : Depends: libnvidia-gl-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-extra-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-decode-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-encode-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: xserver-xorg-video-nvidia-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-cfg1-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Depends: libnvidia-fbc1-515 (= 515.48.07-0ubuntu0.20.04.2) but it is not going to be installed
                     Recommends: libnvidia-compute-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
                     Recommends: libnvidia-decode-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
                     Recommends: libnvidia-encode-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
                     Recommends: libnvidia-fbc1-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
                     Recommends: libnvidia-gl-515:i386 (= 515.48.07-0ubuntu0.20.04.2)
E: Unable to correct problems, you have held broken packages.

```


However no held packages are found by *dpkg --get-selections | grep hold*

---

### Post by Impavidus on 2022-07-09
If kernel -107 no longer works, you can just as well remove it. The linux-modules-extra-..., linux-image-... and linux-modules-... packages. You can also remove the linux-headers-... packages for -107, but those don't take any space in /boot.

Does the -110 kernel work properly? And the -121 kernel only using the nouveau driver?

I've got no experience with nvidia drivers, so I'll leave this to people who have (unless none appear).

---

### Post by TheFu on 2022-07-09
If the nvidia dkms isn't working, the quick fix is usually to let the ubuntu-drivers tool handle it.

```
sudo ubuntu-drivers autoinstall
```

For each new kernel, this might be necessary, until either the nvidia dkms is fixed or you fix it.  I'm lazy.  On my nvidia system, if my patch script sees that a new kernel was installed, then it just re-runs the command above. I haven't bothered looking into the "correct" solution and it has been over 2 yrs that this has been working.

BTW, you might want to remove all the old nvidia driver packages. If you are using nouveau, now is the perfect time.

A few other tidbits.  When it comes to storage use, all the loop devices are useless. They aren't taking up any storage that isn't accounted for elsewhere. Same for all the tmpfs and devfs stuff.  We never need to see those things. They just add cruft to your posts and confuse any real storage issue.  This alias (add to your normal alias lists in your dotfiles).  I've added another handy alias for storage stuff:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
alias lsblkt='lsblk -e 7 -o name,size,type,fstype,mountpoint'
```

Clean, useful, information.

---

### Post by ajgreeny on 2022-07-09
> BTW, you might want to remove all the old nvidia driver packages. If you are using nouveau, now is the perfect time.
I am fairly sure that it is essential to remove an older, non-working nvidia driver before attempting to install another so follow TheFu's idea and you may get things going again.

---

### Post by TheFu on 2022-07-09
> **ajgreeny said:**
> I am fairly sure that it is essential to remove an older, non-working nvidia driver before attempting to install another so follow TheFu's idea and you may get things going again.

I haven't been removing older nvidia driver versions, but I did remove 3 older versions today.  I'm on a GT 1030, so high-end GPUs might be completely different.  My other physical machine with a GPU has an AMD and it "just works", once the kernel with support for that iGPU version was installed (which wasn't the normal kernel for my hardware and OS release).

---

### Post by elpidiovaldez5 on 2022-07-09
I managed to get the machine to boot with nvidia-driver-470

```
NVIDIA-SMI 470.129.06   Driver Version: 470.129.06   CUDA Version: 11.4 

```

```
paul@clio:~$ ubuntu-drivers devices
== /sys/devices/pci0000:00/0000:00:1c.7/0000:09:00.0/0000:0a:07.0/0000:0e:00.0 ==
modalias : pci:v000014E4d000043A0sv00001043sd00008659bc02sc80i00
vendor   : Broadcom Inc. and subsidiaries
model    : BCM4360 802.11ac Wireless Network Adapter
driver   : bcmwl-kernel-source - distro non-free

== /sys/devices/pci0000:00/0000:00:03.0/0000:01:00.0 ==
modalias : pci:v000010DEd00001B06sv00003842sd00006696bc03sc00i00
vendor   : NVIDIA Corporation
model    : GP102 [GeForce GTX 1080 Ti]
manual_install: True
driver   : nvidia-driver-515 - distro non-free recommended
driver   : nvidia-driver-510 - distro non-free
driver   : nvidia-driver-510-server - distro non-free                                                                                                                   
driver   : nvidia-driver-515-server - distro non-free                                                                                                                   
driver   : xserver-xorg-video-nouveau - distro free builtin                                                                                                             

== /sys/devices/pci0000:00/0000:00:02.0/0000:02:00.0 ==
modalias : pci:v000010DEd0000128Bsv00001462sd00008C93bc03sc00i00
vendor   : NVIDIA Corporation
model    : GK208B [GeForce GT 710]
driver   : nvidia-driver-418-server - distro non-free
driver   : nvidia-driver-470 - distro non-free
driver   : nvidia-driver-450-server - distro non-free
driver   : nvidia-driver-390 - distro non-free
driver   : nvidia-driver-470-server - distro non-free
driver   : xserver-xorg-video-nouveau - distro free builtin

```

It is showing as manually installed, which I imagine means that it won't be automatically updated.  That is not a problem for now.

I really want to make sure /boot is now cleaned and consistent. The following commands show the situation:

```
paul@clio:~$ uname -r
5.4.0-121-generic

```

```
paul@clio:~$ dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+'
rc  linux-image-5.4.0-107-generic                 5.4.0-107.121                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-110-generic                 5.4.0-110.124                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-121-generic                 5.4.0-121.137                        amd64        Signed kernel image generic
```

```
paul@clio:~$ ls -lh /boot
total 368M
-rw-r--r-- 1 root root 233K Apr 14 13:19 config-5.4.0-110-generic
-rw-r--r-- 1 root root 233K Jun 15 14:13 config-5.4.0-121-generic
drwx------ 3 root root 4.0K Jan  1  1970 efi
drwxr-xr-x 4 root root 4.0K Jul  9 03:51 grub
lrwxrwxrwx 1 root root   28 Jul  9 03:51 initrd.img -> initrd.img-5.4.0-121-generic
-rw------- 1 root root  55M Jul  9 01:02 initrd.img-5.4.0-110-generic
-rw------- 1 root root  56M Jul 10 02:54 initrd.img-5.4.0-121-generic
-rw------- 1 root root 111M Aug 25  2021 initrd.img-5.4.0-77-generic
-rw------- 1 root root 111M Sep  8  2021 initrd.img-5.4.0-81-generic
lrwxrwxrwx 1 root root   28 Jul  9 01:05 initrd.img.old -> initrd.img-5.4.0-110-generic
drwx------ 2 root root  16K Jan 22  2021 lost+found
-rw-r--r-- 1 root root 179K Aug 18  2020 memtest86+.bin
-rw-r--r-- 1 root root 181K Aug 18  2020 memtest86+.elf
-rw-r--r-- 1 root root 181K Aug 18  2020 memtest86+_multiboot.bin
-rw------- 1 root root 4.6M Apr 14 13:19 System.map-5.4.0-110-generic
-rw------- 1 root root 4.6M Jun 15 14:13 System.map-5.4.0-121-generic
lrwxrwxrwx 1 root root   25 Jul  9 01:01 vmlinuz -> vmlinuz-5.4.0-121-generic
-rw------- 1 root root  14M Apr 14 13:56 vmlinuz-5.4.0-110-generic
-rw------- 1 root root  14M Jun 15 14:18 vmlinuz-5.4.0-121-generic
lrwxrwxrwx 1 root root   25 Jul  9 01:05 vmlinuz.old -> vmlinuz-5.4.0-110-generic
```

There seem to be some left over images taking a lot of space: 
initrd.img-5.4.0-77-generic
initrd.img-5.4.0-81-generic

Can I just delete these files ?  Are there any other places where bits of these old kernels might be lieing around ?  I don't know how the system got into such a state, but it has persisted for a long time as all attempts to fix it failed.  Finally, thanks to help on this forum, things seem to be getting better.

---

### Post by oldfred on 2022-07-09
You may want to also check /lib/modules & /usr/src.

Sometimes best way to fix it to reinstall, so all the bits are there. Then the uninstall works. When you have some files, but not others, you have to manually house clean everything.

I also like synaptic but sometimes use command line.

ls /var/cache/apt/archives/linux-image*
ls -al /usr/src/
ls -al /lib/modules/
ls -al /boot/
dpkg -l | grep linux-
[FONT=monospace][COLOR=#000000]ls -al /boot/vmlinuz* /boot/initrd.img* [/COLOR]


[/FONT]

---

### Post by ActionParsnip on 2022-07-10
If the kernel is removed, then you can clean up with:
```

sudo dpkg -P linux-image-5.4.0-107-generic

```

---

### Post by TheFu on 2022-07-10
There is an overriding rule about packages and files.

Never manually delete a file from the system areas that was installed with a package and expected to be part of the package removal, except through the package manager.  This is because when it is time for the package management system to remove a package, it is going to try to remove all the files it installed and expect to still be there. If 1 of those file doesn't exist, the removal will fail. That's a hassle.

So, those specific files that you believe are extra in /boot/ ... which package are they part?  There are apt and dpkg commands that accept the absolute path to a file and will return the package to which they belong.  Some examples:
```
dpkg -l {part-of-package-name}*

#  list package names based on specific file location
dpkg -S /usr/bin/passwd
dpkg-query --search '/path/to/file'
apt-file search vim

#  list of files in a known package:
dpkg-query -L {pkg-name}

```

If those files you believe are extra aren't part of any installed package on the system, then you can delete them manually.  If it turns out you made a mistake, you can create a zero-length (empty) file with the exact name, and use the normal APT methods to remove the package and it will remove those empty files.  I suppose there's a -f (force) option, but sometimes it is just easier and safer to avoid that during removals.

BTW, 
```
$ df -Th /boot
```
is a more helpful command to see about space in /boot.

---

### Post by elpidiovaldez5 on 2022-07-10
I checked */usr/src* and it looks good.  However */lib/modules* looks wrong.  There are a lot of folders for kernels that are no longer installed.

```
paul@clio:~$ dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+'
rc  linux-image-5.4.0-107-generic                 5.4.0-107.121                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-110-generic                 5.4.0-110.124                        amd64        Signed kernel image generic
ii  linux-image-5.4.0-121-generic                 5.4.0-121.137                        amd64        Signed kernel image generic

```

```
paul@clio:~$ ls -l /lib/modules
total 60
drwxr-xr-x 3 root root 4096 Jul  9 03:51 5.4.0-100-generic
drwxr-xr-x 3 root root 4096 Jul  9 03:51 5.4.0-107-generic
drwxr-xr-x 6 root root 4096 Jul  9 01:21 5.4.0-110-generic
drwxr-xr-x 6 root root 4096 Jul 10 02:54 5.4.0-121-generic
drwxr-xr-x 3 root root 4096 Jun  3  2021 5.4.0-65-generic
drwxr-xr-x 3 root root 4096 Jun  3  2021 5.4.0-66-generic
drwxr-xr-x 3 root root 4096 Jun  3  2021 5.4.0-67-generic
drwxr-xr-x 3 root root 4096 Jun  3  2021 5.4.0-70-generic
drwxr-xr-x 3 root root 4096 Jun  3  2021 5.4.0-71-generic
drwxr-xr-x 3 root root 4096 Jun  3  2021 5.4.0-72-generic
drwxr-xr-x 3 root root 4096 Jan 23 15:19 5.4.0-73-generic
drwxr-xr-x 3 root root 4096 Jan 23 15:20 5.4.0-74-generic
drwxr-xr-x 3 root root 4096 Jan 23 15:20 5.4.0-77-generic
drwxr-xr-x 3 root root 4096 Jan 23 15:32 5.4.0-81-generic
drwxr-xr-x 3 root root 4096 Jan 23 15:34 5.4.0-88-generic
```

These old kernels are not found by the package manager, and I believe are the result of many failed attempts to clean up the kernels.  Is it safe to just delete everything except modules for packages 107, 110 and 121 ?

---

### Post by TheFu on 2022-07-10
/lib/modules  is for kernel module packages. You should remove those that aren't matched to one of the kernels still installed.  Remove the PACKAGES, not the files. Let the package manager deal with the files.

Here's mine:
```
$ ls -F /lib/modules
5.4.0-120-generic/  5.4.0-121-generic/  5.4.0-89-generic/

```
I haven't manually removed any module packages, so on a properly working system, apt should be addressing those as needed. Just run autoremove and autoclean every few weeks.

---

### Post by Impavidus on 2022-07-11
Look for the packages providing these modules directories. For example (on my system):```
dpkg --search /lib/modules/5.15.0-40-generic/
linux-headers-5.15.0-40-generic, linux-modules-extra-5.15.0-40-generic, linux-modules-5.15.0-40-generic: /lib/modules/5.15.0-40-generic
```This tells me that this directory in modules is provided by the linux-headers-..., the linux-modules-extra-... and the linux-modules-... packages, not by the linux-image-... package. Then remove those packages.

---

### Post by elpidiovaldez5 on 2022-07-11
The packages appear to have already been removed.  Somehow the system got itself into a horribly inconsistent state.  However things seem to be better now - I have freed space on /boot and my graphics driver is working.

```
dpkg --search /lib/modules/5.4.0-{65,66,67,70,71,72,73,74,77,81,88}-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-65-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-66-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-67-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-70-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-71-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-72-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-73-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-74-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-77-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-81-generic/
dpkg-query: no path found matching pattern /lib/modules/5.4.0-88-generic/
```

I am going to remove the superfluous files manually.

---

