---
title: "Not able to install anything anymore"
date: 2016-12-13
forum: Installation &amp; Upgrades
---

### Post by aroundsix on 2016-12-13
First of all, hello everyone. New to the forum and relatively new to Ubuntu. Been using it for the past 6-8 months for software development but recently I've run into the following error everytime I try to install something new. For example I tried to install the spotify client the other day and this is what I get: 

I'm using Ubuntu 16.04 in a dual-boot system with Windows 10.

```
Reading package lists... Done
    Building dependency tree       
    Reading state information... Done
    The following packages were automatically installed and are no longer required:
      linux-headers-4.4.0-36 linux-headers-4.4.0-36-generic linux-image-4.4.0-36-generic linux-image-extra-4.4.0-36-generic ubuntu-core-launcher
    Use 'sudo apt autoremove' to remove them.
    Recommended packages:
      libavcodec54 | libavcodec-extra-54 libavformat54
    The following packages will be REMOVED:
      linux-image-4.4.0-28-generic linux-image-4.4.0-31-generic linux-image-4.4.0-34-generic linux-image-extra-4.4.0-28-generic linux-image-extra-4.4.0-31-generic
      linux-image-extra-4.4.0-34-generic
    The following NEW packages will be installed:
      spotify-client
    0 upgraded, 1 newly installed, 6 to remove and 0 not upgraded.
    15 not fully installed or removed.
    Need to get 0 B/73,2 MB of archives.
    After this operation, 486 MB disk space will be freed.
    Do you want to continue? [Y/n] Y
    (Reading database ... 300801 files and directories currently installed.)
    Removing linux-image-extra-4.4.0-28-generic (4.4.0-28.47) ...
    depmod: FATAL: could not load /boot/System.map-4.4.0-28-generic: No such file or directory
    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    Error! Your kernel headers for kernel 4.4.0-28-generic cannot be found.
    Please install the linux-headers-4.4.0-28-generic package,
    or use the --kernelsourcedir option to tell DKMS where it's located
    run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    update-initramfs: Generating /boot/initrd.img-4.4.0-28-generic
    WARNING: missing /lib/modules/4.4.0-28-generic
    Ensure all necessary drivers are built into the linux image!
    depmod: ERROR: could not open directory /lib/modules/4.4.0-28-generic: No such file or directory
    depmod: FATAL: could not search modules: No such file or directory
    depmod: WARNING: could not open /var/tmp/mkinitramfs_VAlZ4z/lib/modules/4.4.0-28-generic/modules.order: No such file or directory
    depmod: WARNING: could not open /var/tmp/mkinitramfs_VAlZ4z/lib/modules/4.4.0-28-generic/modules.builtin: No such file or directory
    run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    /usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
    run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
    dpkg: error processing package linux-image-extra-4.4.0-28-generic (--remove):
     subprocess installed post-removal script returned error exit status 1
    Removing linux-image-4.4.0-28-generic (4.4.0-28.47) ...
    Examining /etc/kernel/postrm.d .
    run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    update-initramfs: Deleting /boot/initrd.img-4.4.0-28-generic
    run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    /usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
    run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
    Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-28-generic.postrm line 328.
    dpkg: error processing package linux-image-4.4.0-28-generic (--remove):
     subprocess installed post-removal script returned error exit status 1
    Removing linux-image-extra-4.4.0-31-generic (4.4.0-31.50) ...
    depmod: FATAL: could not load /boot/System.map-4.4.0-31-generic: No such file or directory
    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    Error! Your kernel headers for kernel 4.4.0-31-generic cannot be found.
    Please install the linux-headers-4.4.0-31-generic package,
    or use the --kernelsourcedir option to tell DKMS where it's located
    run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
    WARNING: missing /lib/modules/4.4.0-31-generic
    Ensure all necessary drivers are built into the linux image!
    depmod: ERROR: could not open directory /lib/modules/4.4.0-31-generic: No such file or directory
    depmod: FATAL: could not search modules: No such file or directory
    depmod: WARNING: could not open /var/tmp/mkinitramfs_abdXZQ/lib/modules/4.4.0-31-generic/modules.order: No such file or directory
    depmod: WARNING: could not open /var/tmp/mkinitramfs_abdXZQ/lib/modules/4.4.0-31-generic/modules.builtin: No such file or directory
    run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    /usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
    run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
    dpkg: error processing package linux-image-extra-4.4.0-31-generic (--remove):
     subprocess installed post-removal script returned error exit status 1
    Removing linux-image-4.4.0-31-generic (4.4.0-31.50) ...
    Examining /etc/kernel/postrm.d .
    run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    update-initramfs: Deleting /boot/initrd.img-4.4.0-31-generic
    run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    /usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
    run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
    Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-31-generic.postrm line 328.
    dpkg: error processing package linux-image-4.4.0-31-generic (--remove):
     subprocess installed post-removal script returned error exit status 1
    No apport report written because MaxReports is reached already
                                                                  Removing linux-image-extra-4.4.0-34-generic (4.4.0-34.53) ...
    depmod: FATAL: could not load /boot/System.map-4.4.0-34-generic: No such file or directory
    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    Error! Your kernel headers for kernel 4.4.0-34-generic cannot be found.
    Please install the linux-headers-4.4.0-34-generic package,
    or use the --kernelsourcedir option to tell DKMS where it's located
    run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
    WARNING: missing /lib/modules/4.4.0-34-generic
    Ensure all necessary drivers are built into the linux image!
    depmod: ERROR: could not open directory /lib/modules/4.4.0-34-generic: No such file or directory
    depmod: FATAL: could not search modules: No such file or directory
    depmod: WARNING: could not open /var/tmp/mkinitramfs_4FQUrq/lib/modules/4.4.0-34-generic/modules.order: No such file or directory
    depmod: WARNING: could not open /var/tmp/mkinitramfs_4FQUrq/lib/modules/4.4.0-34-generic/modules.builtin: No such file or directory
    run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    /usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
    run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
    dpkg: error processing package linux-image-extra-4.4.0-34-generic (--remove):
     subprocess installed post-removal script returned error exit status 1
    No apport report written because MaxReports is reached already
                                                                  Removing linux-image-4.4.0-34-generic (4.4.0-34.53) ...
    Examining /etc/kernel/postrm.d .
    run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    update-initramfs: Deleting /boot/initrd.img-4.4.0-34-generic
    run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    /usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
    run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
    Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-34-generic.postrm line 328.
    dpkg: error processing package linux-image-4.4.0-34-generic (--remove):
     subprocess installed post-removal script returned error exit status 1
    No apport report written because MaxReports is reached already
                                                                  Errors were encountered while processing:
     linux-image-extra-4.4.0-28-generic
     linux-image-4.4.0-28-generic
     linux-image-extra-4.4.0-31-generic
     linux-image-4.4.0-31-generic
     linux-image-extra-4.4.0-34-generic
     linux-image-4.4.0-34-generic
    E: Sub-process /usr/bin/dpkg returned an error code (1)
```



I tried to install them manually using sudo apt install linux-headers-4.4.0-28-generic but I'm greeted by the same error. Also tried to sudo apt dist-upgrade, that didn't seem to fix it either. 

Anyway I could fix this without reinstalling the OS ?

---

### Post by howefield on 2016-12-13
Can you show the output of the terminal commands..

```
df -h
```
```
df -i
```

---

### Post by aroundsix on 2016-12-13
**df-h**
```

Filesystem      Size  Used Avail Use% Mounted on
udev            2,9G     0  2,9G   0% /dev
tmpfs           592M  8,9M  583M   2% /run
/dev/sda5        71G   52G   16G  77% /
tmpfs           2,9G  330M  2,6G  12% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
tmpfs           2,9G     0  2,9G   0% /sys/fs/cgroup
tmpfs           592M   60K  592M   1% /run/user/1000
```


**df -i**

```
Filesystem      Inodes   IUsed   IFree IUse% Mounted on
udev            752273     604  751669    1% /dev
tmpfs           757103     820  756283    1% /run
/dev/sda5      4685824 1705963 2979861   37% /
tmpfs           757103     237  756866    1% /dev/shm
tmpfs           757103       5  757098    1% /run/lock
tmpfs           757103      16  757087    1% /sys/fs/cgroup
tmpfs           757103      30  757073    1% /run/user/1000



```

Forgot to mention I have a dual-boot system with Windows 10.

---

### Post by howefield on 2016-12-13
Thanks for that, I meant to add /boot to the df -h command, could you oblige with the output of..

```
df -h /boot
```

---

### Post by aroundsix on 2016-12-13
**df -h /boot**
```
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5        71G   52G   16G  77% /



```

---

### Post by ian-weisser on 2016-12-13
> **aroundsix said:**
> 
```
    Removing linux-image-extra-4.4.0-28-generic (4.4.0-**28**.47) ...
    depmod: FATAL: could not load /boot/System.map-4.4.0-**28**-generic: No such file or directory
    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
    Error! Your kernel headers for kernel 4.4.0-28-generic cannot be found.
    Please install the linux-headers-4.4.0-28-generic package,
    or use the --kernelsourcedir option to tell DKMS where it's located
[...]
    Removing linux-image-extra-4.4.0-31-generic (4.4.0-**31**.50) ...
    depmod: FATAL: could not load /boot/System.map-4.4.0-**31**-generic: No such file or directory
    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
    Error! Your kernel headers for kernel 4.4.0-31-generic cannot be found.
    Please install the linux-headers-4.4.0-31-generic package,
    or use the --kernelsourcedir option to tell DKMS where it's located
[...]
    Removing linux-image-extra-4.4.0-34-generic (4.4.0-**34**.53) ...
    depmod: FATAL: could not load /boot/System.map-4.4.0-**34**-generic: No such file or directory
    run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
    Error! Your kernel headers for kernel 4.4.0-34-generic cannot be found.
    Please install the linux-headers-4.4.0-34-generic package,
    or use the --kernelsourcedir option to tell DKMS where it's located

```
I tried to install them manually using sudo apt install linux-headers-4.4.0-28-generic but I'm greeted by the same error. Also tried to sudo apt dist-upgrade, that didn't seem to fix it either. 

Seems like the system is complaining about three sets of headers. Try installing all three.
```
sudo apt install linux-headers-4.4.0-28-generic linux-headers-4.4.0-31-generic linux-headers-4.4.0-34-generic
```

If that fails, there are a couple directions to go.

---

### Post by aroundsix on 2016-12-13
Seemed to be doing something for a second but after fetching each one it started showing the same error.

---

### Post by ian-weisser on 2016-12-13
if it succeeded fetching each one, then you can use dpkg.
```
ls -l /var/cache/apt/archives/ | grep linux-headers                    \\ learn the exact file names
cd /var/cache/apt/archives                                             \\ change dirs to make the next step easier
sudo dpkg --install <package_1.deb> <package_2.deb> <package_3.deb>    \\ use FILEname.deb, not package name
cd ~                                                                   \\ return to your home dir
```

If all three install properly, then you can remove those kernel packages. Afterward, double-check that the headers were also removed.

---

### Post by aroundsix on 2016-12-13
Looks like it didn't actually got them. 

ls -l /var/cache/apt/archives/ | grep linux-headers ```
-rw-r--r-- 1 9933982 mai   16  2016 linux-headers-4.4.0-22_4.4.0-22.40_all.deb
-rw-r--r-- 1 783104 mai   16  2016 linux-headers-4.4.0-22-generic_4.4.0-22.40_amd64.deb
-rw-r--r-- 1 9944462 juin  25 13:13 linux-headers-4.4.0-28_4.4.0-28.47_all.deb
-rw-r--r-- 1 789766 juin  25 13:13 linux-headers-4.4.0-28-generic_4.4.0-28.47_amd64.deb
-rw-r--r-- 1 9935316 juil. 13 13:57 linux-headers-4.4.0-31_4.4.0-31.50_all.deb
-rw-r--r-- 1 781610 juil. 13 13:58 linux-headers-4.4.0-31-generic_4.4.0-31.50_amd64.deb
-rw-r--r-- 1 9938660 juil. 28 10:40 linux-headers-4.4.0-34_4.4.0-34.53_all.deb
-rw-r--r-- 1 784474 juil. 28 10:40 linux-headers-4.4.0-34-generic_4.4.0-34.53_amd64.deb
-rw-r--r-- 1 9953102 déc.   5 16:40 linux-headers-4.4.0-53_4.4.0-53.74_all.deb
-rw-r--r-- 1 781760 déc.   5 16:40 linux-headers-4.4.0-53-generic_4.4.0-53.74_amd64.deb
-rw-r--r-- 1 2274 déc.   5 16:39 linux-headers-generic_4.4.0.53.56_amd64.deb

```

I then ran 
```
sudo dpkg --install linux-headers-4.4.0-28-generic_4.4.0-28.47_amd64.deb linux-headers-4.4.0-31-generic_4.4.0-31.50_amd64.deb linux-headers-4.4.0-34-generic_4.4.0-34.53_amd64.deb 
```[FONT=Verdana]

and got this: 

[/FONT]```
(Reading database ... 310551 files and directories currently installed.)Preparing to unpack linux-headers-4.4.0-28-generic_4.4.0-28.47_amd64.deb ...
Unpacking linux-headers-4.4.0-28-generic (4.4.0-28.47) over (4.4.0-28.47) ...
Selecting previously unselected package linux-headers-4.4.0-31-generic.
Preparing to unpack linux-headers-4.4.0-31-generic_4.4.0-31.50_amd64.deb ...
Unpacking linux-headers-4.4.0-31-generic (4.4.0-31.50) ...
Selecting previously unselected package linux-headers-4.4.0-34-generic.
Preparing to unpack linux-headers-4.4.0-34-generic_4.4.0-34.53_amd64.deb ...
Unpacking linux-headers-4.4.0-34-generic (4.4.0-34.53) ...
dpkg: dependency problems prevent configuration of linux-headers-4.4.0-28-generic:
 linux-headers-4.4.0-28-generic depends on linux-headers-4.4.0-28; however:
  Package linux-headers-4.4.0-28 is not installed.


dpkg: error processing package linux-headers-4.4.0-28-generic (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-4.4.0-31-generic:
 linux-headers-4.4.0-31-generic depends on linux-headers-4.4.0-31; however:
  Package linux-headers-4.4.0-31 is not installed.


dpkg: error processing package linux-headers-4.4.0-31-generic (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-headers-4.4.0-34-generic:
 linux-headers-4.4.0-34-generic depends on linux-headers-4.4.0-34; however:
  Package linux-headers-4.4.0-34 is not installed.


dpkg: error processing package linux-headers-4.4.0-34-generic (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-4.4.0-28-generic
 linux-headers-4.4.0-31-generic
 linux-headers-4.4.0-34-generic





```

---

### Post by ian-weisser on 2016-12-13
It got them.
There's just another another additional set of packages to get: 

linux-headers-4.4.0-34-generic
linux-headers-4.4.0-34

See the difference? They look similar to a human, but they are two different packages.
 Instead of three packages, you must obtain and install six.

---

### Post by aroundsix on 2016-12-13
Ah, I see, thank you, will give that a go now.

---

### Post by aroundsix on 2016-12-13
Looks like they installed but I still can't install anything else without getting the same error: 


```
sudo dpkg --install linux-headers-4.4.0-28_4.4.0-28.47_all.deb linux-headers-4.4.0-28-generic_4.4.0-28.47_amd64.deb linux-headers-4.4.0-31_4.4.0-31.50_all.deb linux-headers-4.4.0-31-generic_4.4.0-31.50_amd64.deb linux-headers-4.4.0-34_4.4.0-34.53_all.deb linux-headers-4.4.0-34-generic_4.4.0-34.53_amd64.deb

Selecting previously unselected package linux-headers-4.4.0-28.
(Reading database ... 330054 files and directories currently installed.)
Preparing to unpack linux-headers-4.4.0-28_4.4.0-28.47_all.deb ...
Unpacking linux-headers-4.4.0-28 (4.4.0-28.47) ...
Preparing to unpack linux-headers-4.4.0-28-generic_4.4.0-28.47_amd64.deb ...
Unpacking linux-headers-4.4.0-28-generic (4.4.0-28.47) over (4.4.0-28.47) ...
Selecting previously unselected package linux-headers-4.4.0-31.
Preparing to unpack linux-headers-4.4.0-31_4.4.0-31.50_all.deb ...
Unpacking linux-headers-4.4.0-31 (4.4.0-31.50) ...
Preparing to unpack linux-headers-4.4.0-31-generic_4.4.0-31.50_amd64.deb ...
Unpacking linux-headers-4.4.0-31-generic (4.4.0-31.50) over (4.4.0-31.50) ...
Selecting previously unselected package linux-headers-4.4.0-34.
Preparing to unpack linux-headers-4.4.0-34_4.4.0-34.53_all.deb ...
Unpacking linux-headers-4.4.0-34 (4.4.0-34.53) ...
Preparing to unpack linux-headers-4.4.0-34-generic_4.4.0-34.53_amd64.deb ...
Unpacking linux-headers-4.4.0-34-generic (4.4.0-34.53) over (4.4.0-34.53) ...
Setting up linux-headers-4.4.0-28 (4.4.0-28.47) ...
Setting up linux-headers-4.4.0-28-generic (4.4.0-28.47) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
Setting up linux-headers-4.4.0-31 (4.4.0-31.50) ...
Setting up linux-headers-4.4.0-31-generic (4.4.0-31.50) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
Setting up linux-headers-4.4.0-34 (4.4.0-34.53) ...
Setting up linux-headers-4.4.0-34-generic (4.4.0-34.53) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
```


I then tried to install the spotify client, still get the same error i used to get before.

---

### Post by ian-weisser on 2016-12-13
Installing Spotify is premature - you must still remove the old kernels first.
Failure to remove those kernels was the original error. Any install (Spotify, cowsay, whatever) will fail until those kernels are properly removed.

Try removing one complete set of kernel-image and kernel-header packages:
```
sudo apt remove linux-image-extra-4.4.0-28-generic linux-image-4.4.0-28-generic linux-headers-4.4.0-28 linux-headers-4.4.0-28-generic
```

If it fails, please show us the complete output.
If it succeeds, repeat for the -31 and -34 kernels. Then run an apt update and apt upgrade to test proper functioning of apt. If that succeeds, then you're ready to install Spotify.

---

### Post by aroundsix on 2016-12-13
Looks like it failed:

```

 sudo apt remove linux-image-extra-4.4.0-28-generic linux-image-4.4.0-28-generic linux-headers-4.4.0-28 linux-headers-4.4.0-28-generic


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-36 linux-headers-4.4.0-36-generic linux-image-4.4.0-36-generic linux-image-extra-4.4.0-36-generic ubuntu-core-launcher
Use 'sudo apt autoremove' to remove them.
The following packages will be REMOVED:
  linux-headers-4.4.0-28 linux-headers-4.4.0-28-generic linux-image-4.4.0-28-generic linux-image-4.4.0-31-generic linux-image-4.4.0-34-generic
  linux-image-extra-4.4.0-28-generic linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-34-generic
0 upgraded, 0 newly installed, 8 to remove and 4 not upgraded.
15 not fully installed or removed.
After this operation, 730 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 380675 files and directories currently installed.)
Removing linux-image-extra-4.4.0-28-generic (4.4.0-28.47) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-28-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-28-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_gKmtiT/lib/modules/4.4.0-28-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_gKmtiT/lib/modules/4.4.0-28-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-28-generic (4.4.0-28.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-28-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-31-generic (4.4.0-31.50) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-31-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_ZCdXbV/lib/modules/4.4.0-31-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ZCdXbV/lib/modules/4.4.0-31-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-31-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-31-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-31-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-34-generic (4.4.0-34.53) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-34-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_sr2XwG/lib/modules/4.4.0-34-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_sr2XwG/lib/modules/4.4.0-34-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-34-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-34-generic (4.4.0-34.53) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-34-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-34-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-headers-4.4.0-28-generic (4.4.0-28.47) ...
dpkg: warning: while removing linux-headers-4.4.0-28-generic, directory '/lib/modules/4.4.0-28-generic' not empty so not removed
Removing linux-headers-4.4.0-28 (4.4.0-28.47) ...
Errors were encountered while processing:
 linux-image-extra-4.4.0-28-generic
 linux-image-4.4.0-28-generic
 linux-image-extra-4.4.0-31-generic
 linux-image-4.4.0-31-generic
 linux-image-extra-4.4.0-34-generic
 linux-image-4.4.0-34-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)



```


Btw, I really appreciate the help.

---

### Post by ian-weisser on 2016-12-13
Let's look at the first error:

> **aroundsix said:**
> 
```
depmod: FATAL: could not load /boot/System.map-4.4.0-28-generic: No such file or directory
```


Does the file actually exist?
```
ls -l /boot/
```

If so, that sends us in one direction (create a tempfile for the script to happily remove)
If not, that sends us in another direction (force-removal)

---

### Post by aroundsix on 2016-12-13
```
total 145132
-rw-r--r-- 1 1239577 avril 18  2016 abi-4.4.0-21-generic
-rw-r--r-- 1 1242262 sept.  6 19:52 abi-4.4.0-38-generic
-rw-r--r-- 1 1243479 déc.   2 19:11 abi-4.4.0-53-generic
-rw-r--r-- 1  189412 avril 18  2016 config-4.4.0-21-generic
-rw-r--r-- 1  189732 sept.  6 19:52 config-4.4.0-38-generic
-rw-r--r-- 1  189877 déc.   2 19:11 config-4.4.0-53-generic
drwxr-xr-x 5    4096 mai   26  2016 grub
-rw-r--r-- 1 5958850 nov.  24 16:15 initrd.img-4.4.0-21-generic
-rw-r--r-- 1 7290745 déc.  12 14:36 initrd.img-4.4.0-38-generic
-rw-r--r-- 1 7742099 déc.  12 14:36 initrd.img-4.4.0-53-generic
-rw-r--r-- 1  182704 janv. 28  2016 memtest86+.bin
-rw-r--r-- 1  184380 janv. 28  2016 memtest86+.elf
-rw-r--r-- 1  184840 janv. 28  2016 memtest86+_multiboot.bin
-rw------- 1 3853719 avril 18  2016 System.map-4.4.0-21-generic
-rw------- 1 3869329 sept.  6 19:52 System.map-4.4.0-38-generic
-rw------- 1 3874377 déc.   2 19:11 System.map-4.4.0-53-generic
-rw-r--r-- 1 7013984 mai   26  2016 vmlinuz-4.4.0-21-generic
-rw------- 1 7051680 sept.  6 19:52 vmlinuz-4.4.0-38-generic
-rw------- 1 7065648 déc.   2 19:11 vmlinuz-4.4.0-53-generic




```

Doesn't look like it exists.

---

### Post by ian-weisser on 2016-12-13
How strange. I wonder why it's not there.

Nevertheless, let's try creating a dummy file for the uninstaller to remove. That may defeat the FATAL error.

Try:
```
sudo touch /boot/System.map-4.4.0-28-generic
sudo apt remove linux-image-extra-4.4.0-28-generic linux-image-4.4.0-28-generic linux-headers-4.4.0-28 linux-headers-4.4.0-28-generic
```

There will probably be more errors, and more workarounds. We follow the chain. Eventually, we will discover and resolve the underlying problem(s).

---

### Post by aroundsix on 2016-12-13
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'linux-headers-4.4.0-28' is not installed, so not removed
Package 'linux-headers-4.4.0-28-generic' is not installed, so not removed
The following packages will be REMOVED:
  linux-image-4.4.0-28-generic linux-image-4.4.0-31-generic linux-image-4.4.0-34-generic linux-image-4.4.0-36-generic linux-image-extra-4.4.0-28-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-34-generic linux-image-extra-4.4.0-36-generic
0 upgraded, 0 newly installed, 8 to remove and 4 not upgraded.
15 not fully installed or removed.
After this operation, 871 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 295205 files and directories currently installed.)
Removing linux-image-extra-4.4.0-28-generic (4.4.0-28.47) ...
depmod: WARNING: could not open /lib/modules/4.4.0-28-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/4.4.0-28-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-28-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_Le9Qgp/lib/modules/4.4.0-28-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_Le9Qgp/lib/modules/4.4.0-28-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-28-generic (4.4.0-28.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-28-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-31-generic (4.4.0-31.50) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-31-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_nAGNoe/lib/modules/4.4.0-31-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_nAGNoe/lib/modules/4.4.0-31-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-31-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-31-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-31-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-34-generic (4.4.0-34.53) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-34-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_e4jcHi/lib/modules/4.4.0-34-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_e4jcHi/lib/modules/4.4.0-34-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-34-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-34-generic (4.4.0-34.53) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-34-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-34-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_U9Z37a/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_U9Z37a/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-28-generic
 linux-image-4.4.0-28-generic
 linux-image-extra-4.4.0-31-generic
 linux-image-4.4.0-31-generic
 linux-image-extra-4.4.0-34-generic
 linux-image-4.4.0-34-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Looks like it got rid of the first FATAL error. I;m assuming we should to the same for the other 2 ? 31 and 34 ?

---

### Post by ian-weisser on 2016-12-13
Well, now we are at:
> run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
The workaround silenced the first fatal error, but this one is tougher. Code 127 is usually a catch-all - an error so weird and unusual that the developers didn't run across it enough to give it it's own code. Could be a corrupted typo in a config file, could be a lot of things.

Try the following. It may generate a lot of output. Or not.
```
sudo apt -f install
```

---

### Post by aroundsix on 2016-12-13
```
sudo apt -f install


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-image-4.4.0-28-generic linux-image-4.4.0-31-generic linux-image-4.4.0-34-generic linux-image-4.4.0-36-generic linux-image-extra-4.4.0-28-generic
  linux-image-extra-4.4.0-31-generic linux-image-extra-4.4.0-34-generic linux-image-extra-4.4.0-36-generic
0 upgraded, 0 newly installed, 8 to remove and 4 not upgraded.
15 not fully installed or removed.
After this operation, 871 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 295205 files and directories currently installed.)
Removing linux-image-extra-4.4.0-28-generic (4.4.0-28.47) ...
depmod: WARNING: could not open /lib/modules/4.4.0-28-generic/modules.order: No such file or directory
depmod: WARNING: could not open /lib/modules/4.4.0-28-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-28-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_MUUd3s/lib/modules/4.4.0-28-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_MUUd3s/lib/modules/4.4.0-28-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-28-generic (4.4.0-28.47) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-28-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-28-generic /boot/vmlinuz-4.4.0-28-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-28-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-28-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-extra-4.4.0-31-generic (4.4.0-31.50) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-31-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-31-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_yXwJ2u/lib/modules/4.4.0-31-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_yXwJ2u/lib/modules/4.4.0-31-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-31-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
Removing linux-image-4.4.0-31-generic (4.4.0-31.50) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-31-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-31-generic /boot/vmlinuz-4.4.0-31-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-31-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-31-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-34-generic (4.4.0-34.53) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-34-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-34-generic
depmod: WARNING: could not open /var/tmp/mkinitramfs_XKFCVQ/lib/modules/4.4.0-34-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_XKFCVQ/lib/modules/4.4.0-34-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-34-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-34-generic (4.4.0-34.53) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-34-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-34-generic /boot/vmlinuz-4.4.0-34-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-34-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-34-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-extra-4.4.0-36-generic (4.4.0-36.55) ...
depmod: FATAL: could not load /boot/System.map-4.4.0-36-generic: No such file or directory
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/dkms 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
Error! Your kernel headers for kernel 4.4.0-36-generic cannot be found.
Please install the linux-headers-4.4.0-36-generic package,
or use the --kernelsourcedir option to tell DKMS where it's located
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-36-generic
WARNING: missing /lib/modules/4.4.0-36-generic
Ensure all necessary drivers are built into the linux image!
depmod: ERROR: could not open directory /lib/modules/4.4.0-36-generic: No such file or directory
depmod: FATAL: could not search modules: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ZPgtWc/lib/modules/4.4.0-36-generic/modules.order: No such file or directory
depmod: WARNING: could not open /var/tmp/mkinitramfs_ZPgtWc/lib/modules/4.4.0-36-generic/modules.builtin: No such file or directory
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postinst.d/zz-update-grub exited with return code 127
dpkg: error processing package linux-image-extra-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Removing linux-image-4.4.0-36-generic (4.4.0-36.55) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-36-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-36-generic /boot/vmlinuz-4.4.0-36-generic
/usr/sbin/grub-mkconfig: 6: /etc/default/grub: Windows 10 (loader) (on /dev/sda1): not found
run-parts: /etc/kernel/postrm.d/zz-update-grub exited with return code 127
Failed to process /etc/kernel/postrm.d at /var/lib/dpkg/info/linux-image-4.4.0-36-generic.postrm line 328.
dpkg: error processing package linux-image-4.4.0-36-generic (--remove):
 subprocess installed post-removal script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-image-extra-4.4.0-28-generic
 linux-image-4.4.0-28-generic
 linux-image-extra-4.4.0-31-generic
 linux-image-4.4.0-31-generic
 linux-image-extra-4.4.0-34-generic
 linux-image-4.4.0-34-generic
 linux-image-extra-4.4.0-36-generic
 linux-image-4.4.0-36-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by ian-weisser on 2016-12-13
It this a dual-boot system? Is Windows or another distro installed alongside?

---

### Post by aroundsix on 2016-12-13
Yes, a dual-boot system with Windows 10.

---

### Post by ian-weisser on 2016-12-13
Hmmm. Unfortunately, I must return to work for a few hours.

I do not understand why your kernel-image packages are not fully installing...but also not throwing an error.
I do not understand why your update-grub cannot locate the Windows loader.
I do not understand why your kernel postinst script is throwing a 127 error.

Each of those problems might be quite a can of worms. 

What's you goal? Do you simply want it fixed as quickly as possible (force-uninstall or reinstall)? Or do you want to slowly dig and learn more about your system (troubleshoot)?
We can do either...but this is a decision point for you.

---

### Post by aroundsix on 2016-12-13
First of all, thank you very much for taking the time to help me. 

I would like to understand more about the system, troubleshoot. I love this sort of thing. I can't; really afford yet to do a reinstall tho since I'm working on a project for work on this system. Everything is nicely saved on Github but still, it would be a pain in the ass to reinstall now. However, come Christmas holiday if I still haven't fixed the issue I'll reinstall it and be done with it. 

It's not a MAJOR inconvenience, luckily the current mongoDB version is sufficient enough for the project but I'd like to update to the latest version and that's simply not possible with the current state of my linux os.

If you're up for going through all of this to fix it, then yeah, if not don't worry, I'll just reinstall over Christmas.

---

