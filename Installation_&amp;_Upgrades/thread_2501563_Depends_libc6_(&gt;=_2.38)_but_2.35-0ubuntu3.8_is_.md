---
title: "Depends: libc6 (&gt;= 2.38) but 2.35-0ubuntu3.8 is installed"
date: 2024-10-12
forum: Installation &amp; Upgrades
---

### Post by tengerye on 2024-10-12
Similar error has been posted on this forum, unfortunately, the solutions to them could not help me.

The version of my OS is (lsb_release -a):

```
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.5 LTS
Release:	22.04
Codename:	jammy

```

When I execute (sudo apt upgrade), I got the following:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-headers-6.5.0-060500-generic : Depends: libc6 (>= 2.38) but 2.35-0ubuntu3.8 is installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

I also tried to execute: (sudo apt install -f libc6=2.35-0ubuntu3.8 libc-bin=2.35-0ubuntu3.8), but still got:
```
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
libc-bin is already the newest version (2.35-0ubuntu3.8).
libc-bin set to manually installed.
libc6 is already the newest version (2.35-0ubuntu3.8).
libc6 set to manually installed.
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-headers-6.5.0-060500-generic : Depends: libc6 (>= 2.38) but 2.35-0ubuntu3.8 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).

```

Thank you in advance.

---

### Post by Bashing-om on 2024-10-13
Hello tengerye - Welcome to the forum.

That kernel/header is old; current is:
> 
6.8.0.44.44.1~22.04.1 


Which leads to the question of what kernel you are presently booting and the headers that are installed.
Please show us the outputs of terminal commands - between code tags:
```

uname -r
ls -al /usr/src/

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
and let us consider removing 6.5.0-060500-generic.

-One way forward-

---

### Post by tengerye on 2024-10-14
Thank you so much.

The output of command: (uname -r) is:

```

6.5.0-41-generic

```


The output command of (ls -al /usr/src/) is:

```

drwxr-xr-x  8 root root 4096 10&#26376; 11 20:58 .
drwxr-xr-x 14 root root 4096  2&#26376; 21  2024 ..
drwxr-xr-x 25 root root 4096 10&#26376; 11 20:58 linux-headers-6.5.0-060500
drwxr-xr-x  7 root root 4096 10&#26376; 11 20:58 linux-headers-6.5.0-060500-generic
drwxr-xr-x  7 root root 4096  7&#26376;  7 10:21 linux-headers-6.5.0-41-generic
drwxr-xr-x  7 root root 4096 10&#26376; 10 11:13 linux-headers-6.8.0-45-generic
drwxr-xr-x 26 root root 4096  7&#26376;  7 10:21 linux-hwe-6.5-headers-6.5.0-41
drwxr-xr-x 26 root root 4096 10&#26376; 10 11:13 linux-hwe-6.8-headers-6.8.0-45


```



My ultimate goal is to install NVIDIA CUDA on my Ubuntu. According to their lates instruction ([https://docs.nvidia.com/cuda/cuda-installation-guide-linux/](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/)), they support the version [COLOR=#1A1A1A][FONT=NVIDIA]5.15.0-102.

[/FONT][/COLOR]May I ask what is next please?

---

### Post by Bashing-om on 2024-10-14
tengerye hummm -

> 
My ultimate goal is to install NVIDIA CUDA on my Ubuntu. According to their lates instruction ([https://docs.nvidia.com/cuda/cuda-in...n-guide-linux/](https://docs.nvidia.com/cuda/cuda-in...n-guide-linux/)), they support the version 5.15.0-102.


Now that is something I have no experience with and know nothing about -
However
As you do say -  version 5.15.0-102 -
then you would, if that is the case, install Focal - release 20.04 !
see:
[https://packages.ubuntu.com/search?keywords=linux-image-generic&searchon=names&suite=focal-updates&section=all](https://packages.ubuntu.com/search?keywords=linux-image-generic&searchon=names&suite=focal-updates&section=all)

Depending on what you find out and what you want to do is what is to be done next.

[INDENT]which way did he go, George[/INDENT]

---

### Post by tengerye on 2024-10-15
Thank you for your help.

May I ask, if I would like to keep kernel 6.8.0. Should I delete everything except kernel [COLOR=#000000][FONT=&quot]linux-headers-6.8.0-45-generic [/FONT][/COLOR]and  [COLOR=#000000][FONT=&quot]linux-hwe-6.8-headers-6.8.0-45[/FONT][/COLOR]?

---

### Post by Bashing-om on 2024-10-15
tengerye

If you desire to remain on this current install we need to find out why you are not booting the latest kernel - and of course fix that old header dependency issue. Generally speaking we want to keep the latest kernel and one other as a fall back.
If one keeps latest and the one under it --- then "autoremove" will do the housecleaning for us.

-here to help-

---

### Post by tengerye on 2024-10-15
I tried to switch to 6.8.0, but still can install nothing.
My command (uname -r) is:
[COLOR=#000000]```
[/COLOR]
6.8.0-45-generic
[COLOR=#000000]
```
[/COLOR]
And I tried this command: sudo apt install make, but I got:
[COLOR=#000000]```
[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
make is already the newest version (4.3-4.1build1).
make set to manually installed.
You might want to run 'apt --fix-broken install' to correct these.
The following packages have unmet dependencies:
 linux-headers-6.5.0-060500-generic : Depends: libc6 (>= 2.38) but 2.35-0ubuntu3.8 is to be installed
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
[COLOR=#000000]
```

Then I tried: [/COLOR]sudo apt --fix-broken install
but I got:
[COLOR=#000000]```
[/COLOR]
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Correcting dependencies... failed.
The following packages have unmet dependencies:
 linux-headers-6.5.0-060500-generic : Depends: libc6 (>= 2.38) but 2.35-0ubuntu3.8 is installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.
E: Unable to correct dependencies
[COLOR=#000000]
```[/COLOR]

---

### Post by Bashing-om on 2024-10-16
tengerye; Good -

in that you are booting the 6.8.0-45 HWE kernel.
Next we need to know what is going on with the libc6 package in order to purge no longer wanted kernels.

show us:
```

apt policy libc6
ls -al /boot/

```
libc6 should be version 2.35-0ubuntu3.8 in jammy:
[https://packages.ubuntu.com/search?keywords=libc6&searchon=names&suite=jammy-updates&section=all](https://packages.ubuntu.com/search?keywords=libc6&searchon=names&suite=jammy-updates&section=all)

[INDENT]see what we are going to do here
[/INDENT]

---

### Post by deadflowr on 2024-10-16
Try
```
sudo dpkg --purge --force-all linux-headers-6.5.0-060500-generic
```

---

### Post by tengerye on 2024-10-16
Thank you so much.

My command: apt policy libc6
```

libc6:
  Installed: 2.35-0ubuntu3.8
  Candidate: 2.35-0ubuntu3.8
  Version table:
 *** 2.35-0ubuntu3.8 100
        100 /var/lib/dpkg/status

```

My command: ls -al /boot/
```

drwxr-xr-x  5 root root     4096 10&#26376; 11 20:58 .
drwxr-xr-x 20 root root     4096  5&#26376; 18 08:50 ..
-rw-r--r--  1 root root   278502  8&#26376; 28  2023 config-6.5.0-060500-generic
-rw-r--r--  1 root root   280657  6&#26376;  3 18:09 config-6.5.0-41-generic
-rw-r--r--  1 root root   287058  9&#26376; 11 21:33 config-6.8.0-45-generic
drwx------  4 root root     4096  1&#26376;  1  1970 efi
drwxr-xr-x  5 root root     4096 10&#26376; 11 22:42 grub
lrwxrwxrwx  1 root root       31 10&#26376; 11 20:58 initrd.img -> initrd.img-6.5.0-060500-generic
-rw-r--r--  1 root root 70920863 10&#26376; 11 20:58 initrd.img-6.5.0-060500-generic
-rw-r--r--  1 root root 71014197 10&#26376; 10 11:15 initrd.img-6.5.0-41-generic
-rw-r--r--  1 root root 72026141 10&#26376; 10 11:15 initrd.img-6.8.0-45-generic
lrwxrwxrwx  1 root root       27 10&#26376; 11 20:58 initrd.img.old -> initrd.img-6.8.0-45-generic
drwx------  2 root root    16384  5&#26376; 18 08:48 lost+found
-rw-r--r--  1 root root   182800  2&#26376;  7  2022 memtest86+.bin
-rw-r--r--  1 root root   184476  2&#26376;  7  2022 memtest86+.elf
-rw-r--r--  1 root root   184980  2&#26376;  7  2022 memtest86+_multiboot.bin
-rw-------  1 root root  8221682  8&#26376; 28  2023 System.map-6.5.0-060500-generic
-rw-------  1 root root  8268513  6&#26376;  3 18:09 System.map-6.5.0-41-generic
-rw-------  1 root root  8657806  9&#26376; 11 21:33 System.map-6.8.0-45-generic
lrwxrwxrwx  1 root root       28 10&#26376; 11 20:58 vmlinuz -> vmlinuz-6.5.0-060500-generic
-rw-------  1 root root 14088704  8&#26376; 28  2023 vmlinuz-6.5.0-060500-generic
-rw-------  1 root root 14271496  6&#26376;  3 18:10 vmlinuz-6.5.0-41-generic
-rw-------  1 root root 14911880  9&#26376; 11 21:59 vmlinuz-6.8.0-45-generic
lrwxrwxrwx  1 root root       24 10&#26376; 11 20:58 vmlinuz.old -> vmlinuz-6.8.0-45-generic

```

---

### Post by deadflowr on 2024-10-16
> My command: apt policy libc6
```
libc6:
  Installed: 2.35-0ubuntu3.8
  Candidate: 2.35-0ubuntu3.8
  Version table:
 *** 2.35-0ubuntu3.8 100
        100 /var/lib/dpkg/status
```
Well that's not right.
Should look mostly like this
```
libc6:
  Installed: 2.35-0ubuntu3.8
  Candidate: 2.35-0ubuntu3.8
  Version table:
 *** 2.35-0ubuntu3.8 500
        500 http://us.archive.ubuntu.com/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.35-0ubuntu3 500
        500 http://us.archive.ubuntu.com/ubuntu jammy/main amd64 Packages
```
(Note the archive.ubuntu mirror may differ for you.
the security repository wold be the same, as it's the same for all.)

Did you disable the repositories?
Or did you delete the lines from the posted output?

---

### Post by Bashing-om on 2024-10-16
tengerye - deadflowr; UnWell

We have a number of issues to work out.

Kernel 6.5.0-060500-generic is set to boot and that is the kernel needing removal!
In my mind is How* can a later version kernel be "vmlinuz.old" ?
And lastly is libc6 packing listing - how to fix that ?

Boot  6.8.0-45 and dpkg --purge the offending 6.5 out of tree kernel ?
then see what results:
```

sudo apt update
sudo apt full-upgrade

``` ??

Where I can foresee we will have to re-establish the vmlinuz symbolic links.

even so >
-making forward progress-

---

### Post by tengerye on 2024-10-16
The posted output is complete.

I have no idea of what went wrong. If possible, could you guide me what to do please?

---

### Post by tengerye on 2024-10-16
It seems to work so far.
I executed:
```

sudo dpkg --purge --force-all linux-headers-6.5.0-41-generic

```

Then I used this command (ls -al /usr/src/) to list all kernels:
```

drwxr-xr-x  6 root root 4096 10&#26376; 17 09:33 .
drwxr-xr-x 14 root root 4096  2&#26376; 21  2024 ..
drwxr-xr-x 25 root root 4096 10&#26376; 11 20:58 linux-headers-6.5.0-060500
drwxr-xr-x  7 root root 4096 10&#26376; 10 11:13 linux-headers-6.8.0-45-generic
drwxr-xr-x 26 root root 4096  7&#26376;  7 10:21 linux-hwe-6.5-headers-6.5.0-41
drwxr-xr-x 26 root root 4096 10&#26376; 10 11:13 linux-hwe-6.8-headers-6.8.0-45

```

Then I executed the following two commands:
```

sudo apt update
sudo apt full-upgrade
```
which went well.

---

### Post by Bashing-om on 2024-10-16
tengerye Great

So far so good.
But !
Look back at post #9 - it is the out-of-tree kernel that requires attention.

sym links ?
what shows now
```

ls -al /boot/

```

we need to tweak the merge lists ?
```

apt policy libc6

```

[INDENT]progress in small steps
[/INDENT]

---

### Post by tengerye on 2024-10-16
The command (ls -al /boot/), gives the following output:

```

total 277176
drwxr-xr-x  5 root root     4096 10&#26376; 17 09:47 .
drwxr-xr-x 20 root root     4096  5&#26376; 18 08:50 ..
-rw-r--r--  1 root root   278502  8&#26376; 28  2023 config-6.5.0-060500-generic
-rw-r--r--  1 root root   280657  6&#26376;  3 18:09 config-6.5.0-41-generic
-rw-r--r--  1 root root   287058  9&#26376; 11 21:33 config-6.8.0-45-generic
drwx------  4 root root     4096  1&#26376;  1  1970 efi
drwxr-xr-x  5 root root     4096 10&#26376; 11 22:42 grub
lrwxrwxrwx  1 root root       31 10&#26376; 11 20:58 initrd.img -> initrd.img-6.5.0-060500-generic
-rw-r--r--  1 root root 70920863 10&#26376; 11 20:58 initrd.img-6.5.0-060500-generic
-rw-r--r--  1 root root 71014197 10&#26376; 10 11:15 initrd.img-6.5.0-41-generic
-rw-r--r--  1 root root 72011006 10&#26376; 17 09:47 initrd.img-6.8.0-45-generic
lrwxrwxrwx  1 root root       27 10&#26376; 11 20:58 initrd.img.old -> initrd.img-6.8.0-45-generic
drwx------  2 root root    16384  5&#26376; 18 08:48 lost+found
-rw-r--r--  1 root root   182800  2&#26376;  7  2022 memtest86+.bin
-rw-r--r--  1 root root   184476  2&#26376;  7  2022 memtest86+.elf
-rw-r--r--  1 root root   184980  2&#26376;  7  2022 memtest86+_multiboot.bin
-rw-------  1 root root  8221682  8&#26376; 28  2023 System.map-6.5.0-060500-generic
-rw-------  1 root root  8268513  6&#26376;  3 18:09 System.map-6.5.0-41-generic
-rw-------  1 root root  8657806  9&#26376; 11 21:33 System.map-6.8.0-45-generic
lrwxrwxrwx  1 root root       28 10&#26376; 11 20:58 vmlinuz -> vmlinuz-6.5.0-060500-generic
-rw-------  1 root root 14088704  8&#26376; 28  2023 vmlinuz-6.5.0-060500-generic
-rw-------  1 root root 14271496  6&#26376;  3 18:10 vmlinuz-6.5.0-41-generic
-rw-------  1 root root 14911880  9&#26376; 11 21:59 vmlinuz-6.8.0-45-generic
lrwxrwxrwx  1 root root       24 10&#26376; 11 20:58 vmlinuz.old -> vmlinuz-6.8.0-45-generic

```

The command (apt policy lib6) gives the following output:

```

N: Unable to locate package lib6

```

---

### Post by Bashing-om on 2024-10-16
tengerye -

lib6 is my bad - should have been libc6 - error on my part.

Let's finish up removing that problematic kernel. 
```

sudo dpkg -P linux-image-6.5.0-060500-generic linux-modules{,-extra}-6.5.0-060500-generic
sudo apt update
sudo apt upgrade
sudo apt -f install

```

That is currently set as the booting kernel.
Reboot to grub's boot menu and choose to boot the 6.8 kernel.
Now what shows:
```

ls -al /boot/
apt policy libc6
dpkg -C

```

-small steps-

---

### Post by tengerye on 2024-10-17
> **Bashing-om said:**
> tengerye -

lib6 is my bad - should have been libc6 - error on my part.

Let's finish up removing that problematic kernel. 
```

sudo dpkg -P linux-image-6.5.0-060500-generic linux-modules{,-extra}-6.5.0-060500-generic
sudi apt update
sudo apt upgrade
sudo apt -f install

```

That is currently set as the booting kernel.
Reboot to grub's boot menu and choose to boot the 6.8 kernel.
Now what shows:
```

ls -al /boot/
apt policy libc6
dpkg -C

```

-small steps-


The command (ls -al /boot/) gives:
```

total 277176
drwxr-xr-x  5 root root     4096 10&#26376; 17 09:47 .
drwxr-xr-x 20 root root     4096  5&#26376; 18 08:50 ..
-rw-r--r--  1 root root   278502  8&#26376; 28  2023 config-6.5.0-060500-generic
-rw-r--r--  1 root root   280657  6&#26376;  3 18:09 config-6.5.0-41-generic
-rw-r--r--  1 root root   287058  9&#26376; 11 21:33 config-6.8.0-45-generic
drwx------  4 root root     4096  1&#26376;  1  1970 efi
drwxr-xr-x  5 root root     4096 10&#26376; 11 22:42 grub
lrwxrwxrwx  1 root root       31 10&#26376; 11 20:58 initrd.img -> initrd.img-6.5.0-060500-generic
-rw-r--r--  1 root root 70920863 10&#26376; 11 20:58 initrd.img-6.5.0-060500-generic
-rw-r--r--  1 root root 71014197 10&#26376; 10 11:15 initrd.img-6.5.0-41-generic
-rw-r--r--  1 root root 72011006 10&#26376; 17 09:47 initrd.img-6.8.0-45-generic
lrwxrwxrwx  1 root root       27 10&#26376; 11 20:58 initrd.img.old -> initrd.img-6.8.0-45-generic
drwx------  2 root root    16384  5&#26376; 18 08:48 lost+found
-rw-r--r--  1 root root   182800  2&#26376;  7  2022 memtest86+.bin
-rw-r--r--  1 root root   184476  2&#26376;  7  2022 memtest86+.elf
-rw-r--r--  1 root root   184980  2&#26376;  7  2022 memtest86+_multiboot.bin
-rw-------  1 root root  8221682  8&#26376; 28  2023 System.map-6.5.0-060500-generic
-rw-------  1 root root  8268513  6&#26376;  3 18:09 System.map-6.5.0-41-generic
-rw-------  1 root root  8657806  9&#26376; 11 21:33 System.map-6.8.0-45-generic
lrwxrwxrwx  1 root root       28 10&#26376; 11 20:58 vmlinuz -> vmlinuz-6.5.0-060500-generic
-rw-------  1 root root 14088704  8&#26376; 28  2023 vmlinuz-6.5.0-060500-generic
-rw-------  1 root root 14271496  6&#26376;  3 18:10 vmlinuz-6.5.0-41-generic
-rw-------  1 root root 14911880  9&#26376; 11 21:59 vmlinuz-6.8.0-45-generic
lrwxrwxrwx  1 root root       24 10&#26376; 11 20:58 vmlinuz.old -> vmlinuz-6.8.0-45-generic

```

The command (apt policy libc6) gives:
```

libc6:
  Installed: 2.35-0ubuntu3.8
  Candidate: 2.35-0ubuntu3.8
  Version table:
 *** 2.35-0ubuntu3.8 500
        500 https://mirrors.tuna.tsinghua.edu.cn/ubuntu jammy-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu jammy-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.35-0ubuntu3 500
        500 https://mirrors.tuna.tsinghua.edu.cn/ubuntu jammy/main amd64 Packages

```

The command (dpkg -C) gives nothing.

By the way, although I have removed all 6.5.0 kernels, I still need to choose which kernel to start when I boot Ubuntu. May I ask how can I purge them from the boot option and keeps only the 6.8.0 please?

---

### Post by Bashing-om on 2024-10-17
tengerye Huh ?

I am sorta floundering here;
If you ran:sudo dpkg -P linux-image-6.5.0-060500-generic linux-modules{,-extra}-6.5.0-060500-generic
why then does /boot still contain 6.5.0-060500 files ?

I can not continue this until we have /boot under control - nor do I support not having a fall back kernel installed in the event of future issues with the 6.8 kernel.

In order to remove the repo 6.5 we forego the Generally Available 6.5 kernels henceforth - we can do that when /boot is sane AND the system installs a new 6.8 kernel release. Providing all is stable on your system running the 6.8 series kernels.

HWE: The Ubuntu LTS enablement stacks provide newer kernel and X support for existing LTS releases, see 
               [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

[INDENT]sometimes to wonder; other times I just do not know
[/INDENT]

---

### Post by tengerye on 2024-10-17
Instead of ([COLOR=#000000]sudo dpkg -P linux-image-6.5.0-060500-generic linux-modules{,-extra}-6.5.0-060500-generic)[/COLOR]

I actually ran: ([COLOR=#000000][FONT=&amp]sudo dpkg --purge --force-all linux-headers-6.5.0-060500-generic)

Could that be the reason?

If I run ([/FONT][/COLOR][COLOR=#000000]sudo dpkg -P linux-image-6.5.0-060500-generic linux-modules{,-extra}-6.5.0-060500-generic[/COLOR][COLOR=#000000][FONT=&amp]) now, I got the following:
[/FONT][/COLOR]```
dpkg: warning: ignoring request to remove linux-image-6.5.0-060500-generic which isn't installed
dpkg: dependency problems prevent removal of linux-modules-6.5.0-060500-generic:
 linux-image-unsigned-6.5.0-060500-generic depends on linux-modules-6.5.0-060500-generic.


dpkg: error processing package linux-modules-6.5.0-060500-generic (--purge):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-modules-extra-6.5.0-060500-generic which isn't installed
Errors were encountered while processing:
 linux-modules-6.5.0-060500-generic

```

---

### Post by Bashing-om on 2024-10-17
tengerye; Yup

linux-headers-6.5.0-060500-generic > removes that problematic header file that fixed the libc6 versioning.

Next then is to remove the actual image and associated files.

-Moving on along-

---

### Post by tengerye on 2024-10-17
I am the newbie. If possible, could you give me more detail of how to do that please? For example, which specific images and associate files that I need to remove?

---

### Post by Bashing-om on 2024-10-17
tengerye - :D

Oh I did provide detail to complete the kernel removal - please refer back to my post #17.

-it's all in the process-

---

### Post by deadflowr on 2024-10-17
Look at what linux-image package is installed
```
dpkg -l | grep linux-image
```

My guess is you have the unsigned kernel.
So try to purge that.

---

### Post by tengerye on 2024-10-18
Hi, thank you all for your kind help. Here is what I did most recently.
I executed (dpkg -l | grep linux-image) and I got:
```

hc  linux-image-6.5.0-18-generic               6.5.0-18.18~22.04.1                             amd64        Signed kernel image generic
hc  linux-image-6.5.0-35-generic               6.5.0-35.35~22.04.1                             amd64        Signed kernel image generic
hi  linux-image-6.5.0-41-generic               6.5.0-41.41~22.04.2                             amd64        Signed kernel image generic
hi  linux-image-6.8.0-45-generic               6.8.0-45.45~22.04.1                             amd64        Signed kernel image generic
hi  linux-image-generic-hwe-22.04              6.8.0-45.45~22.04.1                             amd64        Generic Linux kernel image
hi  linux-image-unsigned-6.5.0-060500-generic  6.5.0-060500.202308271831                       amd64        Linux kernel image for version 6.5.0 on 64 bit x86 SMP

```

Then I executed the following two successfully:
```

sudo dpkg -P linux-image-6.5.0-18-generic
sudo dpkg -P linux-image-6.5.0-35-generic

```

Then I executed (sudo dpkg -P linux-image-6.5.0-41-generic), and I got the following:
```

(Reading database ... 180554 files and directories currently installed.)
Removing linux-image-6.5.0-41-generic (6.5.0-41.41~22.04.2) ...
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.5.0-41-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-45-generic
Found initrd image: /boot/initrd.img-6.8.0-45-generic
Found linux image: /boot/vmlinuz-6.5.0-060500-generic
Found initrd image: /boot/initrd.img-6.5.0-060500-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sdc2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Purging configuration files for linux-image-6.5.0-41-generic (6.5.0-41.41~22.04.2) ...
rmdir: failed to remove '/lib/modules/6.5.0-41-generic': Directory not empty

```

Then I executed (sudo dpkg -P linux-image-unsigned-6.5.0-060500-generic), and I got
```

(Reading database ... 180550 files and directories currently installed.)
Removing linux-image-unsigned-6.5.0-060500-generic (6.5.0-060500.202308271831) ...
I: /boot/vmlinuz is now a symlink to vmlinuz-6.8.0-45-generic
I: /boot/initrd.img is now a symlink to initrd.img-6.8.0-45-generic
/etc/kernel/postrm.d/initramfs-tools:
update-initramfs: Deleting /boot/initrd.img-6.5.0-060500-generic
/etc/kernel/postrm.d/zz-update-grub:
Sourcing file `/etc/default/grub'
Sourcing file `/etc/default/grub.d/init-select.cfg'
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-6.8.0-45-generic
Found initrd image: /boot/initrd.img-6.8.0-45-generic
Memtest86+ needs a 16-bit boot, that is not available on EFI, exiting
Warning: os-prober will be executed to detect other bootable partitions.
Its output will be used to detect bootable binaries on them and create new boot entries.
Found Windows Boot Manager on /dev/sdc2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for UEFI Firmware Settings ...
done
Purging configuration files for linux-image-unsigned-6.5.0-060500-generic (6.5.0-060500.202308271831) ...
rmdir: failed to remove '/lib/modules/6.5.0-060500-generic': Directory not empty

```

---

### Post by tengerye on 2024-10-18
After all the operations above, I execute (dpkg -l | grep linux-image) and I got:
```

hi  linux-image-6.8.0-45-generic               6.8.0-45.45~22.04.1                             amd64        Signed kernel image generic
hi  linux-image-generic-hwe-22.04              6.8.0-45.45~22.04.1                             amd64        Generic Linux kernel image

```

---

### Post by Bashing-om on 2024-10-18
tengerye - verry well; mostly

> 
[color=red]hi[/color]  linux-image-6.8.0-45-generic
[color=red]hi[/color]  linux-image-generic-hwe-22.04

can you explain why these are in Held status ? (we do want to see as staus "ii")

At his time what shows for /boot's symbolic links:
```

ls -al /boot/

```

[INDENT]moving right on along
[/INDENT]

---

### Post by tengerye on 2024-10-18
My command ([COLOR=#000000][FONT=&quot]ls -al /boot/[/FONT][/COLOR]) gives the following:
```

total 110864
drwxr-xr-x  5 root root     4096 10&#26376; 18 23:51 .
drwxr-xr-x 20 root root     4096  5&#26376; 18 08:50 ..
-rw-r--r--  1 root root   278502  8&#26376; 28  2023 config-6.5.0-060500-generic
-rw-r--r--  1 root root   280657  6&#26376;  3 18:09 config-6.5.0-41-generic
-rw-r--r--  1 root root   287058  9&#26376; 11 21:33 config-6.8.0-45-generic
drwx------  4 root root     4096  1&#26376;  1  1970 efi
drwxr-xr-x  5 root root     4096 10&#26376; 18 23:51 grub
lrwxrwxrwx  1 root root       27 10&#26376; 18 23:51 initrd.img -> initrd.img-6.8.0-45-generic
-rw-r--r--  1 root root 72011006 10&#26376; 17 09:47 initrd.img-6.8.0-45-generic
lrwxrwxrwx  1 root root       27 10&#26376; 11 20:58 initrd.img.old -> initrd.img-6.8.0-45-generic
drwx------  2 root root    16384  5&#26376; 18 08:48 lost+found
-rw-r--r--  1 root root   182800  2&#26376;  7  2022 memtest86+.bin
-rw-r--r--  1 root root   184476  2&#26376;  7  2022 memtest86+.elf
-rw-r--r--  1 root root   184980  2&#26376;  7  2022 memtest86+_multiboot.bin
-rw-------  1 root root  8221682  8&#26376; 28  2023 System.map-6.5.0-060500-generic
-rw-------  1 root root  8268513  6&#26376;  3 18:09 System.map-6.5.0-41-generic
-rw-------  1 root root  8657806  9&#26376; 11 21:33 System.map-6.8.0-45-generic
lrwxrwxrwx  1 root root       24 10&#26376; 18 23:51 vmlinuz -> vmlinuz-6.8.0-45-generic
-rw-------  1 root root 14911880  9&#26376; 11 21:59 vmlinuz-6.8.0-45-generic
lrwxrwxrwx  1 root root       24 10&#26376; 11 20:58 vmlinuz.old -> vmlinuz-6.8.0-45-generic

```

For the question,
> 
[COLOR=#000000]can you explain why these are in Held status ? (we do want to see as staus "ii")[/COLOR]

I am sorry that I do not know. But after the above operations, I have not reboot yet. Do I need to?

---

### Post by Bashing-om on 2024-10-18
tengerye - hummmmm --
> 
But after the above operations, I have not reboot yet. Do I need to?

There is no hurry or rush to reboot.

However, is there more cleanup yet to do ?
Show:
```

dpkg -l | grep linux-
apt-mark showholds

```

-Maybe - our work is done ?-

---

### Post by tengerye on 2024-10-18
The command ([COLOR=#000000][FONT=&quot]dpkg -l | grep linux-[/FONT][/COLOR]) gives the following:
```

ii  binutils-x86-64-linux-gnu                  2.38-4ubuntu2.6                                 amd64        GNU binary utilities, for x86-64-linux-gnu target
hi  linux-base                                 4.5ubuntu9                                      all          Linux image base package
hi  linux-firmware                             20220329.git681281e4-0ubuntu3.34                all          Firmware for Linux kernel drivers
hi  linux-generic-hwe-22.04                    6.8.0-45.45~22.04.1                             amd64        Complete Generic Linux kernel and headers
hi  linux-headers-6.8.0-45-generic             6.8.0-45.45~22.04.1                             amd64        Linux kernel headers for version 6.8.0 on 64 bit x86 SMP
hi  linux-headers-generic-hwe-22.04            6.8.0-45.45~22.04.1                             amd64        Generic Linux kernel headers
hi  linux-hwe-6.8-headers-6.8.0-45             6.8.0-45.45~22.04.1                             all          Header files related to Linux kernel version 6.8.0
hi  linux-hwe-6.8-tools-6.8.0-45               6.8.0-45.45~22.04.1                             amd64        Linux kernel version specific tools for version 6.8.0-45
hi  linux-image-6.8.0-45-generic               6.8.0-45.45~22.04.1                             amd64        Signed kernel image generic
hi  linux-image-generic-hwe-22.04              6.8.0-45.45~22.04.1                             amd64        Generic Linux kernel image
hi  linux-libc-dev:amd64                       5.15.0-122.132                                  amd64        Linux Kernel Headers for development
pi  linux-modules-6.5.0-060500-generic         6.5.0-060500.202308271831                       amd64        Linux kernel extra modules for version 6.5.0 on 64 bit x86 SMP
hc  linux-modules-6.5.0-18-generic             6.5.0-18.18~22.04.1                             amd64        Linux kernel extra modules for version 6.5.0 on 64 bit x86 SMP
hc  linux-modules-6.5.0-35-generic             6.5.0-35.35~22.04.1                             amd64        Linux kernel extra modules for version 6.5.0 on 64 bit x86 SMP
hi  linux-modules-6.5.0-41-generic             6.5.0-41.41~22.04.2                             amd64        Linux kernel extra modules for version 6.5.0 on 64 bit x86 SMP
hi  linux-modules-6.8.0-45-generic             6.8.0-45.45~22.04.1                             amd64        Linux kernel extra modules for version 6.8.0 on 64 bit x86 SMP
hc  linux-modules-extra-6.5.0-18-generic       6.5.0-18.18~22.04.1                             amd64        Linux kernel extra modules for version 6.5.0 on 64 bit x86 SMP
hc  linux-modules-extra-6.5.0-35-generic       6.5.0-35.35~22.04.1                             amd64        Linux kernel extra modules for version 6.5.0 on 64 bit x86 SMP
hi  linux-modules-extra-6.5.0-41-generic       6.5.0-41.41~22.04.2                             amd64        Linux kernel extra modules for version 6.5.0 on 64 bit x86 SMP
hi  linux-modules-extra-6.8.0-45-generic       6.8.0-45.45~22.04.1                             amd64        Linux kernel extra modules for version 6.8.0 on 64 bit x86 SMP
hi  linux-sound-base                           1.0.25+dfsg-0ubuntu7                            all          base package for ALSA and OSS sound systems
hi  linux-tools-6.8.0-45-generic               6.8.0-45.45~22.04.1                             amd64        Linux kernel version specific tools for version 6.8.0-45
hi  linux-tools-common                         5.15.0-122.132                                  all          Linux kernel version specific tools for version 5.15.0

```

The command ([COLOR=#000000][FONT=&quot]apt-mark showholds[/FONT][/COLOR]) gives the following:
```

linux-base
linux-firmware
linux-generic-hwe-22.04
linux-headers-6.8.0-45-generic
linux-headers-generic-hwe-22.04
linux-hwe-6.8-headers-6.8.0-45
linux-hwe-6.8-tools-6.8.0-45
linux-image-6.8.0-45-generic
linux-image-generic-hwe-22.04
linux-libc-dev
linux-modules-6.5.0-18-generic
linux-modules-6.5.0-35-generic
linux-modules-6.5.0-41-generic
linux-modules-6.8.0-45-generic
linux-modules-extra-6.5.0-18-generic
linux-modules-extra-6.5.0-35-generic
linux-modules-extra-6.5.0-41-generic
linux-modules-extra-6.8.0-45-generic
linux-sound-base
linux-tools-6.8.0-45-generic
linux-tools-common

```

---

### Post by Bashing-om on 2024-10-18
tengerye >> cleanup

```

sudo dpkg -P linux-modules-6.5.0-{060500,18,35,41}-generic
sudo dpkg -P linux-modules-extra-6.5.0-{18,35,41}-generic

sudo apt-mark unhold linux-base linux-firmware linux-generic-hwe-22.04 linux-headers-6.8.0-45-generic linux-headers-generic-hwe-22.04 linux-libc-dev:amd64 linux-modules-6.8.0-45-generic linux-sound-base linux-tools-6.8.0-45-generic linux-tools-common

dpkg -l | awk '/^rc/{print $2}' | xargs sudo dpkg -P

```

[INDENT]are we done yet ?
[/INDENT]

---

### Post by tengerye on 2024-10-19
Perfect. When I reboot, the 6.8.0 starts as the default now. Thank you so much.

---

### Post by Bashing-om on 2024-10-19
tengerye - Outstanding :D

If the issue is now resolved >
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean, and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]Happy trails to you
[/INDENT]

---

