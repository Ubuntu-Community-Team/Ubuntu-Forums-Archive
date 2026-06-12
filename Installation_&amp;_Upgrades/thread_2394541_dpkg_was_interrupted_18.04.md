---
title: "dpkg was interrupted 18.04"
date: 2018-06-18
forum: Installation &amp; Upgrades
---

### Post by nhatnhan on 2018-06-18
I was installing GTX driver and then the power down so the laptop shutdown.
Then when i run sudo apt-get install <>
the error popped up, i ran sudo dpkg --configure -a as it suggested but 
things stoped here:

```
nhat@nhat-ThinkPad-T560:~$ sudo dpkg --configure -a
Processing triggers for initramfs-tools (0.130ubuntu3) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-20-generic
Setting up nvidia-dkms-390 (390.48-0ubuntu3) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG: Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG: Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG: Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Removing old nvidia-390.48 DKMS files...

-------- Uninstall Beginning --------
Module: nvidia
Version: 390.48
Kernel: 4.15.0-20-generic (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 390.48
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-390.48 DKMS files...
Building for 4.15.0-20-generic
Building for architecture x86_64
Building initial module for 4.15.0-20-generic
```

Plase help me to fix this, i can not install or do anthing  

Thank you

---

### Post by Bashing-om on 2018-06-18
nhatnhan; Hello -

Looks like it completed building on an old kernel.
Latest kernel is:
> 
4.15.0-23-generic


so, show us the results - Between code Tags - of terminal commands:
```

sudo apt update
sudo apt full-upgrade

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

from here we see what the next step in the process might be.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by nhatnhan on 2018-06-19
hello thank you for your help
I try whis 
```
$ sudo apt update 
```

then reveive this:
```

nhat@nhat-ThinkPad-T560:~$ sudo apt update
Hit:1 http://au.archive.ubuntu.com/ubuntu bionic InRelease
Get:2 http://au.archive.ubuntu.com/ubuntu bionic-updates InRelease [83.2 kB] 
Get:3 http://au.archive.ubuntu.com/ubuntu bionic-backports InRelease [74.6 kB]
Get:4 http://au.archive.ubuntu.com/ubuntu bionic-updates/main i386 Packages [132 kB]
Get:5 http://au.archive.ubuntu.com/ubuntu bionic-updates/main amd64 Packages [146 kB]
Get:6 http://au.archive.ubuntu.com/ubuntu bionic-updates/main Translation-en [56.9 kB]
Get:7 http://au.archive.ubuntu.com/ubuntu bionic-updates/main amd64 DEP-11 Metadata [112 kB]
Get:8 http://security.ubuntu.com/ubuntu bionic-security InRelease [83.2 kB]  
Get:9 http://au.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 48x48 Icons [25.1 kB]
Get:10 http://au.archive.ubuntu.com/ubuntu bionic-updates/main DEP-11 64x64 Icons [44.5 kB]
Get:11 http://au.archive.ubuntu.com/ubuntu bionic-updates/universe i386 Packages [84.3 kB]
Get:12 http://au.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 Packages [84.5 kB]
Get:13 http://au.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 DEP-11 Metadata [120 kB]
Get:14 http://au.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 48x48 Icons [123 kB]
Get:15 http://au.archive.ubuntu.com/ubuntu bionic-updates/universe DEP-11 64x64 Icons [198 kB]
Get:16 http://au.archive.ubuntu.com/ubuntu bionic-backports/universe amd64 DEP-11 Metadata [5,096 B]
Get:17 http://security.ubuntu.com/ubuntu bionic-security/main i386 Packages [86.2 kB]
Get:18 http://security.ubuntu.com/ubuntu bionic-security/main amd64 Packages [99.7 kB]
Get:19 http://security.ubuntu.com/ubuntu bionic-security/main amd64 DEP-11 Metadata [204 B]
Get:20 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 Packages [32.7 kB]
Get:21 http://security.ubuntu.com/ubuntu bionic-security/universe i386 Packages [32.6 kB]
Get:22 http://security.ubuntu.com/ubuntu bionic-security/universe amd64 DEP-11 Metadata [2,456 B]
Fetched 1,626 kB in 4s (409 kB/s)                               
Reading package lists... Done
Building dependency tree       
Reading state information... Done
15 packages can be upgraded. Run 'apt list --upgradable' to see them.
nhat@nhat-ThinkPad-T560:~$ sudo apt full-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 


```

---

### Post by deadflowr on 2018-06-19
Run the suggested command:
```
sudo dpkg --configure -a
```
if it runs normal then great, if it still has problems post the output from that command.

---

### Post by nhatnhan on 2018-06-19
yep i did and i received the thing i posted above then it stopped there.

---

### Post by nhatnhan on 2018-06-19
[B]@Basing-om

[/B]somehow i managed to resolve the "dpkg was interupted"
but when i ran
```

sudo apt update
sudo apt full-upgrade

```


the updating process stopped at 85%
this is the last bit in my terminal:
```

Setting up amd64-microcode (3.20171205.1) ...
update-initramfs: deferring update (trigger activated)
amd64-microcode: microcode will be updated at next boot
Setting up linux-modules-4.15.0-23-generic (4.15.0-23.25) ...
Setting up intel-microcode (3.20180425.1~ubuntu0.18.04.1) ...
update-initramfs: deferring update (trigger activated)
intel-microcode: microcode will be updated at next boot
Setting up update-manager-core (1:18.04.11.2) ...
Setting up libwebkit2gtk-4.0-37:amd64 (2.20.3-0ubuntu0.18.04.1) ...
Setting up linux-headers-4.15.0-23-generic (4.15.0-23.25) ...


Progress: [ 85%] [#########################################################...........] 

```

---

### Post by nhatnhan on 2018-06-19
I solved it,

I used the ubuntu app Software & Update to recover the thing ( my initial problem ) 
then i used this as suggeted by Basing-om
```

sudo apt update
sudo apt full-upgrade
```
lastly this one
```

 sudo dpkg --configure -a

```

things got back to normal

Thank you guys,
hope this helps:D

---

### Post by Bashing-om on 2018-06-19
nhatnhan; outstading -

You do good work :)
And thanks for providing your solution.

[INDENT][INDENT]'buntu
[INDENT][INDENT]all in this together
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by con10t on 2018-07-04
Happy some ubunewbies like myself got the 'sudo apt full-upgrade' Error sorted with 'sudo dpkg --configure -a'.

Didn't work for my Thinkpad w. nvidia Quadro P4000 Mobile GPU running ubuntustudio 18.4. :(

The '**sudo dpkg --configure -a**' command hangs at ***Building initial module for 4.15.0-24-lowlatency***

*The entire log following the above command is:*
con10t@the-beast:~$ sudo dpkg --configure -a
Processing triggers for initramfs-tools (0.130ubuntu3.1) ...
update-initramfs: Generating /boot/initrd.img-4.15.0-24-lowlatency
Setting up nvidia-dkms-390 (390.67-0ubuntu0~gpu18.04.1) ...
update-initramfs: deferring update (trigger activated)
INFO:Enable nvidia
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/lenovo_thinkpad
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/put_your_quirks_here
DEBUG:Parsing /usr/share/ubuntu-drivers-common/quirks/dell_latitude
Removing old nvidia-390.67 DKMS files...

-------- Uninstall Beginning --------
Module:  nvidia
Version: 390.67
Kernel:  4.15.0-23-lowlatency (x86_64)
-------------------------------------

Status: This module version was INACTIVE for this kernel.
depmod...

DKMS: uninstall completed.

------------------------------
Deleting module version: 390.67
completely from the DKMS tree.
------------------------------
Done.
Loading new nvidia-390.67 DKMS files...
Building for 4.15.0-24-lowlatency
Building for architecture x86_64
Building initial module for 4.15.0-24-lowlatency

It freezes at this point.

I am running dual boot with windows 10 on my new 'beast', but stuck at this point. Any idea how to get 'dpkg' working?

*'apt list --upgradable' gives the following list:*

con10t@the-beast:~$ apt list --upgradable
Listing... Done
gir1.2-soup-2.4/bionic-updates,bionic-security 2.62.1-1ubuntu0.1 amd64 [upgradable from: 2.62.1-1]
libarchive-zip-perl/bionic-security,bionic-security 1.60-1ubuntu0.1 all [upgradable from: 1.60-1]
libexiv2-14/bionic-updates,bionic-security 0.25-3.1ubuntu0.18.04.1 amd64 [upgradable from: 0.25-3.1]
libnvidia-common-390/bionic,bionic 390.67-0ubuntu0~gpu18.04.1 all [upgradable from: 390.48-0ubuntu3]
libsdl2-2.0-0/bionic-updates 2.0.8+dfsg1-1ubuntu1.18.04.1 amd64 [upgradable from: 2.0.8+dfsg1-1ubuntu1]
libsoup-gnome2.4-1/bionic-updates,bionic-security 2.62.1-1ubuntu0.1 amd64 [upgradable from: 2.62.1-1]
libsoup2.4-1/bionic-updates,bionic-security 2.62.1-1ubuntu0.1 amd64 [upgradable from: 2.62.1-1]
libvulkan1/bionic 1.1.73+dfsg-1~gpu18.04.1 amd64 [upgradable from: 1.1.70+dfsg1-1]
libxnvctrl0/bionic 396.24-0ubuntu0~gpu18.04.1 amd64 [upgradable from: 390.42-0ubuntu1]
libzzip-0-13/bionic-updates,bionic-security 0.13.62-3.1ubuntu0.18.04.1 amd64 [upgradable from: 0.13.62-3.1]
nvidia-kernel-common-390/bionic 390.67-0ubuntu0~gpu18.04.1 amd64 [upgradable from: 390.48-0ubuntu3]
nvidia-settings/bionic 396.24-0ubuntu0~gpu18.04.1 amd64 [upgradable from: 390.42-0ubuntu1]

a conundrum this ubunewbie can't fix without a bit of wizardry from the ether in here.

Cheers! TY - Philip

---

### Post by Bashing-om on 2018-07-04
con10t; Well. 

We just see about that ,, and see what we can do to unravel the sloppyation.

Post back - between code tags - the outputs of terminal commands:
```

sudo dkms status
sudo lshw -C display
lsmod | grep nvidia
ls -al /usr/src/
ls -al /boot/
dpkg -l | grep linux-
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


These I expect to point us in the direction of what is not going on.

[INDENT][INDENT]gotta be a reason
[/INDENT][/INDENT]

---

### Post by felstrasse on 2018-07-10
Hi, I had a similar problem and did as you suggested in your reply. This is the output of those commands:

```

~$ sudo dkms status
bcmwl, 6.30.223.271+bdcom, 4.15.0-23-generic, x86_64: built

```

```

~$ sudo lshw -C display
*-display                 
    description: VGA compatible controller
    product: HD Graphics 520
    vendor: Intel Corporation
    physical id: 2
    bus info: pci@0000:00:02.0
    version: 07
    width: 64 bits
    clock: 33MHz
    capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
    configuration: driver=i915 latency=0
    resources: irq:125 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:4000(size=64) memory:c0000-dffff

```

```

lsmod | grep nvidia

```

```

~$ ls -al /usr/src/
total 28
drwxr-xr-x  7 root root 4096 Jun 18 20:29 .
drwxr-xr-x 10 root root 4096 Jan  5  2018 ..
drwxr-xr-x  5 root root 4096 Jun 18 20:29 bcmwl-6.30.223.271+bdcom
drwxr-xr-x 27 root root 4096 May 24 11:01 linux-headers-4.15.0-22
drwxr-xr-x  8 root root 4096 May 24 11:01 linux-headers-4.15.0-22-generic
drwxr-xr-x 27 root root 4096 Jun 10 11:30 linux-headers-4.15.0-23
drwxr-xr-x  8 root root 4096 Jun 10 11:30 linux-headers-4.15.0-23-generic

```

```

~$ ls -al /boot/
total 133264
drwxr-xr-x  4 root root     4096 Jun 12 08:48 .
drwxr-xr-x 24 root root     4096 Jun 10 11:31 ..
-rw-r--r--  1 root root  1537177 May 15 07:41 abi-4.15.0-22-generic
-rw-r--r--  1 root root  1537050 May 23 18:54 abi-4.15.0-23-generic
-rw-r--r--  1 root root   216807 May 15 07:41 config-4.15.0-22-generic
-rw-r--r--  1 root root   216807 May 23 18:54 config-4.15.0-23-generic
drwx------  4 root root     4096 Jan  1  1970 efi
drwxr-xr-x  5 root root     4096 Jun 12 08:48 grub
-rw-r--r--  1 root root 53816084 Jun 10 11:32 initrd.img-4.15.0-22-generic
-rw-r--r--  1 root root 53952781 Jun 12 08:48 initrd.img-4.15.0-23-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root        0 May 15 07:41 retpoline-4.15.0-22-generic
-rw-r--r--  1 root root        0 May 23 18:54 retpoline-4.15.0-23-generic
-rw-------  1 root root  4039542 May 15 07:41 System.map-4.15.0-22-generic
-rw-------  1 root root  4039393 May 23 18:54 System.map-4.15.0-23-generic
-rw-------  1 root root  8253176 May 17 08:12 vmlinuz-4.15.0-22-generic
-rw-------  1 root root  8256912 May 23 19:49 vmlinuz-4.15.0-23-generic


```

```

~$ dpkg -l | grep linux
ii  binutils-x86-64-linux-gnu                  2.30-20ubuntu2~18.04                        amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                 4.5ubuntu1                                  all          Linux image base package
ii  linux-firmware                             1.173.1                                     all          Firmware for Linux kernel drivers
ii  linux-generic                              4.15.0.23.25                                amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-22                    4.15.0-22.24                                all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-22-generic            4.15.0-22.24                                amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-23                    4.15.0-23.25                                all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-23-generic            4.15.0-23.25                                amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                      4.15.0.23.25                                amd64        Generic Linux kernel headers
rc  linux-image-4.13.0-21-generic              4.13.0-21.24                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-32-generic              4.13.0-32.35                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-36-generic              4.13.0-36.40                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-37-generic              4.13.0-37.42                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-37-lowlatency           4.13.0-37.42                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-38-generic              4.13.0-38.43                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-39-generic              4.13.0-39.44                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.13.0-41-generic              4.13.0-41.46                                amd64        Linux kernel image for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-4.15.0-20-generic              4.15.0-20.21                                amd64        Signed kernel image generic
ii  linux-image-4.15.0-22-generic              4.15.0-22.24                                amd64        Signed kernel image generic
ii  linux-image-4.15.0-23-generic              4.15.0-23.25                                amd64        Signed kernel image generic
rc  linux-image-extra-4.13.0-21-generic        4.13.0-21.24                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-32-generic        4.13.0-32.35                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-36-generic        4.13.0-36.40                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-37-generic        4.13.0-37.42                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-38-generic        4.13.0-38.43                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-39-generic        4.13.0-39.44                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
rc  linux-image-extra-4.13.0-41-generic        4.13.0-41.46                                amd64        Linux kernel extra modules for version 4.13.0 on 64 bit x86 SMP
ii  linux-image-generic                        4.15.0.23.25                                amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                       4.15.0-23.25                                amd64        Linux Kernel Headers for development
rc  linux-modules-4.15.0-20-generic            4.15.0-20.21                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-22-generic            4.15.0-22.24                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-23-generic            4.15.0-23.25                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-20-generic      4.15.0-20.21                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-22-generic      4.15.0-22.24                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-23-generic      4.15.0-23.25                                amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-signed-generic                       4.15.0.23.25                                amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
rc  linux-signed-image-4.13.0-32-generic       4.13.0-32.35                                amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-36-generic       4.13.0-36.40                                amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-37-generic       4.13.0-37.42                                amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-38-generic       4.13.0-38.43                                amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-39-generic       4.13.0-39.44                                amd64        Signed kernel image generic
rc  linux-signed-image-4.13.0-41-generic       4.13.0-41.46                                amd64        Signed kernel image generic
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5                        all          base package for ALSA and OSS sound systems
ii  syslinux-common                            3:6.03+dfsg1-2                              all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu9                        amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

```

~$ cat /var/log/gpu-manager.log


og_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-23-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-23-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? no
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:1916
BusID "PCI:0@0:2:0"
Is boot vga? yes
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do

```

Hopefully this helps.

---

### Post by Bashing-om on 2018-07-10
felstrasse; Hello -

Your issue does not appear to be graphic's driver related, you only have Intel for the chip set and a driver is loaded.
Let's isolate this to a package management issue.

Post back the results of:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```

see where we go from here.

[INDENT][INDENT]All in the process
[/INDENT][/INDENT]

---

### Post by dr.joker2 on 2018-07-16
Hello there, having similar problems. ran all the commands.  thanks in advance!

> ~$ sudo dkms status
nvidia, 396.24.02, 4.15.0-23-generic, x86_64: built

> ~$ sudo lshw -C display
PCI (sysfs)  
after this the terminal froze completely

> ~$ lsmod | grep nvidia
~$ 
this returned nothing

> ~$ ls -al /usr/src/
insgesamt 28
drwxr-xr-x  7 root root 4096 Jul 13 17:49 .
drwxr-xr-x 10 root root 4096 Apr 26 20:18 ..
drwxr-xr-x 27 root root 4096 Apr 26 20:23 linux-headers-4.15.0-20
drwxr-xr-x  8 root root 4096 Apr 26 20:23 linux-headers-4.15.0-20-generic
drwxr-xr-x 27 root root 4096 Jul 13 16:47 linux-headers-4.15.0-23
drwxr-xr-x  8 root root 4096 Jul 13 16:47 linux-headers-4.15.0-23-generic
drwxr-xr-x  8 root root 4096 Jul 13 17:49 nvidia-396.24.02

> ~$ ls -al /boot/
insgesamt 133020
drwxr-xr-x  4 root root     4096 Jul 16 16:25 .
drwxr-xr-x 23 root root     4096 Jul 13 16:47 ..
-rw-r--r--  1 root root  1536934 Apr 24 06:56 abi-4.15.0-20-generic
-rw-r--r--  1 root root  1537050 Mai 23 18:54 abi-4.15.0-23-generic
-rw-r--r--  1 root root   216807 Apr 24 06:56 config-4.15.0-20-generic
-rw-r--r--  1 root root   216807 Mai 23 18:54 config-4.15.0-23-generic
drwx------  3 root root     4096 Jan  1  1970 efi
drwxr-xr-x  5 root root     4096 Jul 13 16:48 grub
-rw-r--r--  1 root root 54162598 Jul 13 16:48 initrd.img-4.15.0-20-generic
-rw-r--r--  1 root root 53363003 Jul 16 16:25 initrd.img-4.15.0-23-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root        0 Apr 24 06:56 retpoline-4.15.0-20-generic
-rw-r--r--  1 root root        0 Mai 23 18:54 retpoline-4.15.0-23-generic
-rw-------  1 root root  4038188 Apr 24 06:56 System.map-4.15.0-20-generic
-rw-------  1 root root  4039393 Mai 23 18:54 System.map-4.15.0-23-generic
-rw-r--r--  1 root root  8249080 Apr 26 20:35 vmlinuz-4.15.0-20-generic
-rw-------  1 root root  8257272 Mai 23 19:49 vmlinuz-4.15.0-23-generic



> ~$ dpkg -l | grep linux-
ii  binutils-x86-64-linux-gnu             2.30-20ubuntu2~18.04                amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                            4.5ubuntu1                          all          Linux image base package
ii  linux-firmware                        1.173.1                             all          Firmware for Linux kernel drivers
ii  linux-generic                         4.15.0.23.25                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-20               4.15.0-20.21                        all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-20-generic       4.15.0-20.21                        amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-23               4.15.0-23.25                        all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-23-generic       4.15.0-23.25                        amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                 4.15.0.23.25                        amd64        Generic Linux kernel headers
ii  linux-image-4.15.0-20-generic         4.15.0-20.21                        amd64        Signed kernel image generic
ii  linux-image-4.15.0-23-generic         4.15.0-23.25                        amd64        Signed kernel image generic
ii  linux-image-generic                   4.15.0.23.25                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                  4.15.0-24.26                        amd64        Linux Kernel Headers for development
ii  linux-modules-4.15.0-20-generic       4.15.0-20.21                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-23-generic       4.15.0-23.25                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-20-generic 4.15.0-20.21                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-23-generic 4.15.0-23.25                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-signed-generic                  4.15.0.23.25                        amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  syslinux-common                       3:6.03+dfsg1-2                      all          collection of bootloaders (common)
ii  syslinux-legacy                       2:3.63+dfsg-2ubuntu9                amd64        Bootloader for Linux/i386 using MS-DOS floppies


> ~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-23-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-23-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:3e9b
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:1c8d
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do



appreciate any hint on how to approach this

---

### Post by Bashing-om on 2018-07-16
dr.joker2; Well .....

This:
> 
Is nvidia loaded? no
bk
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
bk
Has nvidia? no
bk
Single card detected


sure bears a close look.
Post back:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
the lshw command will take a while to find the info .. give it time to complete.

[INDENT][INDENT]a case of mistaken identity ?
[/INDENT][/INDENT]

---

### Post by dr.joker2 on 2018-07-18
> **Bashing-om said:**
> 

sure bears a close look.
Post back:
```

sudo lshw -C display
lspci -nnk | grep -iA3 vga

```
the lshw command will take a while to find the info .. give it time to complete.
[INDENT][INDENT]a case of mistaken identity ?
[/INDENT]
[/INDENT]


Hi, 

what would be an appropriate time? I am waiting for half an hour now, nothing happened so far... :popcorn:

---

### Post by Bashing-om on 2018-07-18
dr.joker2; Yukkie

> 
what would be an appropriate time? I am waiting for half an hour now, nothing happened so far...


Just a couple of minutes - tops !
My result:
```

sysop@x1810:~$ sudo lshw -C display
[color=green][sudo] password for sysop:[/color] 
  *-display                 
       description: VGA compatible controller
       product: GK208 [GeForce GT 710B]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:4c00(size=128) memory:c0000-dffff
sysop@x1810:~$ 

```
where my output shows the nvidia driver loaded.

Now if the 'lshw' command fails to run on your system, then we need to investigate the why the failure. Keep in mind that this is an admin command (sudo) and your password is required in order to execute the command,

Else:
[INDENT]Houston, we have a problem
[/INDENT]

---

### Post by hopeinformer on 2018-07-19
How is this issue solved? I don't see any resolution.

I'm having a very similar problem after trying to install Virtualbox. The terminal just stops after "Building initial module for 4.15.0-23-generic" I have waited for over an hour and it hasn't moved past it. I have tried entering my password and hitting enter twice, I have tried simultaneously hitting enter & right arrow. Nothing works.

error:

bowlcut3x@bowlcut3x-Inspiron-5559:~$ sudo apt-get install virtualbox
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
bowlcut3x@bowlcut3x-Inspiron-5559:~$ sudo dpkg --configure -a
Setting up virtualbox-dkms (5.2.10-dfsg-6ubuntu18.04.1) ...
Removing old virtualbox-5.2.10 DKMS files...


-------- Uninstall Beginning --------
Module:  virtualbox
Version: 5.2.10
Kernel:  4.15.0-23-generic (x86_64)
-------------------------------------


Status: This module version was INACTIVE for this kernel.
depmod...


DKMS: uninstall completed.


------------------------------
Deleting module version: 5.2.10
completely from the DKMS tree.
------------------------------
Done.
Loading new virtualbox-5.2.10 DKMS files...
Building for 4.15.0-23-generic
Building initial module for 4.15.0-23-generic

---

### Post by wildmanne39 on 2018-07-19
Hello and welcome to the forum hopeinformer, the answer that solved the issue for the OP is in post 7, please start your own thread if you need help instead of posting someone else's thread.

Thanks

---

### Post by dr.joker2 on 2018-07-20
> **Bashing-om said:**
> dr.joker2; Yukkie



Just a couple of minutes - tops !
My result:
```

sysop@x1810:~$ sudo lshw -C display
[COLOR=green][sudo] password for sysop:[/COLOR] 
  *-display                 
       description: VGA compatible controller
       product: GK208 [GeForce GT 710B]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:24 memory:fb000000-fbffffff memory:d8000000-dfffffff memory:e6000000-e7ffffff ioport:4c00(size=128) memory:c0000-dffff
sysop@x1810:~$ 

```
where my output shows the nvidia driver loaded.

Now if the 'lshw' command fails to run on your system, then we need to investigate the why the failure. Keep in mind that this is an admin command (sudo) and your password is required in order to execute the command,

Else:[INDENT]Houston, we have a problem
[/INDENT]


My result: 

```

...:~$ sudo lshw -C display
PCI (sysfs)

```

and still running. waited for 2h in the end, nothing happed. Any idea?

---

### Post by Bashing-om on 2018-07-20
dr.joker2; Humm ...

> 
My result:

Code:

...:~$ sudo lshw -C display
PCI (sysfs)

and still running. waited for 2h in the end, nothing happed. Any idea? 


broken sudo ? .. Is this account you are in now that 1st user account that was created in the install ?
what shows :
```

groups

```

system does not do 'sudo' =
[INDENT][INDENT]got to be a reason[/INDENT][/INDENT]

---

### Post by hopeinformer on 2018-07-21
Ok wildmanne39. I thought the 2 scenarios were similar and to open a new thread with the same info would be redundant. Thank you for the feedback.

---

### Post by adisinambela on 2018-07-23
> **Bashing-om said:**
> con10t; Well. 

We just see about that ,, and see what we can do to unravel the sloppyation.

Post back - between code tags - the outputs of terminal commands:
```

sudo dkms status
sudo lshw -C display
lsmod | grep nvidia
ls -al /usr/src/
ls -al /boot/
dpkg -l | grep linux-
cat /var/log/gpu-manager.log

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)


These I expect to point us in the direction of what is not going on.
[INDENT][INDENT]gotta be a reason
[/INDENT]
[/INDENT]

I have the same problem bro, please help me too 

```
adi_sinambela@adisinambela:~$ sudo apt update
[sudo] password for adi_sinambela: 
Hit:1 [http://packages.microsoft.com/repos/vscode](http://packages.microsoft.com/repos/vscode) stable InRelease              
Hit:2 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) bionic InRelease                     
Hit:3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Hit:4 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease    
Get:5 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) bionic-updates InRelease [88,7 kB]
Get:6 [http://id.archive.ubuntu.com/ubuntu](http://id.archive.ubuntu.com/ubuntu) bionic-backports InRelease [74,6 kB] 
Fetched 163 kB in 13s (12,8 kB/s)                                              
Reading package lists... Done
Building dependency tree       
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
```

when i get to 'apt list --upgradable'

```
adi_sinambela@adisinambela:~$ apt list --upgradable
Listing... Done
linux-generic/bionic-updates,bionic-security 4.15.0.29.31 amd64 [upgradable from: 4.15.0.24.26]
linux-headers-generic/bionic-updates,bionic-security 4.15.0.29.31 amd64 [upgradable from: 4.15.0.24.26]
linux-image-generic/bionic-updates,bionic-security 4.15.0.29.31 amd64 [upgradable from: 4.15.0.24.26]

```
when i get 'Sudo apt full-upgrade

adi_sinambela@adisinambela:~$ sudo apt full-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

i have follow your instruction too, that is

[first] 
```
adi_sinambela@adisinambela:~$ sudo dkms status
nvidia, 390.77, 4.15.0-24-generic, x86_64: built

```
[second] 
```
adi_sinambela@adisinambela:~$ sudo lshw -C display
  *-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 07
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:128 memory:ed000000-edffffff memory:c0000000-cfffffff ioport:f000(size=64) memory:c0000-dffff
  *-display
       description: 3D controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:132 memory:ee000000-eeffffff memory:d0000000-dfffffff memory:e0000000-e1ffffff ioport:e000(size=128) memory:ef000000-ef07ffff
```


[third] ```
adi_sinambela@adisinambela:~$ lsmod | grep nvidia
```
nothing happen

[forth]
 ```
adi_sinambela@adisinambela:~$ ls -al /usr/src/
total 28
drwxr-xr-x  7 root root 4096 Jul 23 19:40 .
drwxr-xr-x 10 root root 4096 Apr 27 01:18 ..
drwxr-xr-x 27 root root 4096 Jun 12 15:39 linux-headers-4.15.0-23
drwxr-xr-x  8 root root 4096 Jun 12 15:39 linux-headers-4.15.0-23-generic
drwxr-xr-x 27 root root 4096 Jul  2 20:06 linux-headers-4.15.0-24
drwxr-xr-x  8 root root 4096 Jul  2 20:06 linux-headers-4.15.0-24-generic
drwxr-xr-x  8 root root 4096 Jul 23 19:40 nvidia-390.77
```

[fifth]
```
adi_sinambela@adisinambela:~$ ls -al /boot/
total 132736
drwxr-xr-x  4 root root     4096 Jul 23 21:50 .
drwxr-xr-x 24 root root     4096 Jul  2 20:06 ..
-rw-r--r--  1 root root  1537050 Mei 23 23:54 abi-4.15.0-23-generic
-rw-r--r--  1 root root  1537161 Jun 12 23:09 abi-4.15.0-24-generic
-rw-r--r--  1 root root   216807 Mei 23 23:54 config-4.15.0-23-generic
-rw-r--r--  1 root root   216807 Jun 12 23:09 config-4.15.0-24-generic
drwx------  3 root root     4096 Jan  1  1970 efi
drwxr-xr-x  5 root root     4096 Jul 12 12:15 grub
-rw-r--r--  1 root root 54088516 Jun 23 14:08 initrd.img-4.15.0-23-generic
-rw-r--r--  1 root root 53137358 Jul 23 21:50 initrd.img-4.15.0-24-generic
-rw-r--r--  1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw-r--r--  1 root root        0 Mei 23 23:54 retpoline-4.15.0-23-generic
-rw-r--r--  1 root root        0 Jun 12 23:09 retpoline-4.15.0-24-generic
-rw-------  1 root root  4039393 Mei 23 23:54 System.map-4.15.0-23-generic
-rw-------  1 root root  4040379 Jun 12 23:09 System.map-4.15.0-24-generic
-rw-------  1 root root  8257272 Mei 24 00:49 vmlinuz-4.15.0-23-generic
-rw-------  1 root root  8257272 Jun 13 15:33 vmlinuz-4.15.0-24-generic

```

[sixth] 
```
adi_sinambela@adisinambela:~$ dpkg -l | grep linux-
ii  binutils-x86-64-linux-gnu                  2.30-20ubuntu2~18.04                amd64        GNU binary utilities, for x86-64-linux-gnu target
ii  linux-base                                 4.5ubuntu1                          all          Linux image base package
ii  linux-firmware                             1.173.1                             all          Firmware for Linux kernel drivers
ii  linux-generic                              4.15.0.24.26                        amd64        Complete Generic Linux kernel and headers
ii  linux-headers-4.15.0-23                    4.15.0-23.25                        all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-23-generic            4.15.0-23.25                        amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-4.15.0-24                    4.15.0-24.26                        all          Header files related to Linux kernel version 4.15.0
ii  linux-headers-4.15.0-24-generic            4.15.0-24.26                        amd64        Linux kernel headers for version 4.15.0 on 64 bit x86 SMP
ii  linux-headers-generic                      4.15.0.24.26                        amd64        Generic Linux kernel headers
rc  linux-image-4.15.0-20-generic              4.15.0-20.21                        amd64        Signed kernel image generic
rc  linux-image-4.15.0-22-generic              4.15.0-22.24                        amd64        Signed kernel image generic
ii  linux-image-4.15.0-23-generic              4.15.0-23.25                        amd64        Signed kernel image generic
ii  linux-image-4.15.0-24-generic              4.15.0-24.26                        amd64        Signed kernel image generic
ii  linux-image-generic                        4.15.0.24.26                        amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                       4.15.0-29.31                        amd64        Linux Kernel Headers for development
rc  linux-modules-4.15.0-20-generic            4.15.0-20.21                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-4.15.0-22-generic            4.15.0-22.24                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-23-generic            4.15.0-23.25                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-4.15.0-24-generic            4.15.0-24.26                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-20-generic      4.15.0-20.21                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
rc  linux-modules-extra-4.15.0-22-generic      4.15.0-22.24                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-23-generic      4.15.0-23.25                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-modules-extra-4.15.0-24-generic      4.15.0-24.26                        amd64        Linux kernel extra modules for version 4.15.0 on 64 bit x86 SMP
ii  linux-signed-generic                       4.15.0.29.31                        amd64        Complete Signed Generic Linux kernel and headers (dummy transitional package)
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5                all          base package for ALSA and OSS sound systems
ii  syslinux-common                            3:6.03+dfsg1-2                      all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu9                amd64        Bootloader for Linux/i386 using MS-DOS floppies

```
[seventh]
```
adi_sinambela@adisinambela:~$ cat /var/log/gpu-manager.log
log_file: /var/log/gpu-manager.log
last_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
new_boot_file: /var/lib/ubuntu-drivers-common/last_gfx_boot
can't access /run/u-d-c-nvidia-was-loaded file
can't access /opt/amdgpu-pro/bin/amdgpu-pro-px
Looking for nvidia modules in /lib/modules/4.15.0-24-generic/updates/dkms
Looking for amdgpu modules in /lib/modules/4.15.0-24-generic/updates/dkms
Is nvidia loaded? no
Was nvidia unloaded? no
Is nvidia blacklisted? no
Is intel loaded? yes
Is radeon loaded? no
Is radeon blacklisted? no
Is amdgpu loaded? no
Is amdgpu blacklisted? no
Is amdgpu versioned? no
Is amdgpu pro stack? no
Is nouveau loaded? no
Is nouveau blacklisted? yes
Is nvidia kernel module available? no
Is amdgpu kernel module available? no
Vendor/Device Id: 8086:5917
BusID "PCI:0@0:2:0"
Is boot vga? yes
Vendor/Device Id: 10de:174d
BusID "PCI:1@0:0:0"
Is boot vga? no
Error: can't access /sys/bus/pci/devices/0000:01:00.0/driver
The device is not bound to any driver. Skipping...
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Skipping "/dev/dri/card0", driven by "i915"
Found "/dev/dri/card0", driven by "i915"
output 0:
    card0-eDP-1
Number of connected outputs for /dev/dri/card0: 1
Does it require offloading? yes
last cards number = 1
Has amd? no
Has intel? yes
Has nvidia? no
How many cards? 1
Has the system changed? No
Single card detected
Nothing to do
```

---

### Post by Bashing-om on 2018-07-23
adisinambela; Wellll ..

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

What we know:
a) the kernel 4.15.0.29.31 is only partially installed - the why we do not know
b) we have the nouveau driver for nvidia display chip set; yet it is blacklisted- and again, we do not know why

Things have changed under systemd and I have yet to learn where the nouveau blacklisting takes place, so this too will be a learning process for me.

Presently we need to know what kernel you are booting and the state of the package manager:
```

uname -r
df -h
df -i
sudo apt update
sudo apt upgrade
sudo apt -f install

```
What happens when the system attempts to update its self ?

and what role does the nvidia driver may play in this - if any
```

dpkg -l | grep -i nvidia

```


[INDENT]all in the process
[/INDENT]

---

### Post by flocculant on 2018-07-23
> we have the nouveau driver for nvidia display chip set; yet it is blacklisted- and again, we do not know why

Check /etc/modprobe.d/ for an nvidia.conf file

Bug was fix released : [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1761593](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1761593)

---

### Post by mB&amp;1tx*) on 2018-07-23
I'm having similar problems when loading several different packages. Here's the latest I got:

kristin@kristin-Inspiron-5558:~$ dpkg --configure -a
dpkg: error: requested operation requires superuser privilege
kristin@kristin-Inspiron-5558:~$ sudo dpkg --configure -a
[sudo] password for kristin: 
Setting up rtl8812au-dkms (4.3.8.12175.20140902+dfsg-0ubuntu8) ...
Removing old rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...


-------- Uninstall Beginning --------
Module:  rtl8812au
Version: 4.3.8.12175.20140902+dfsg
Kernel:  4.15.0-29-lowlatency (x86_64)
-------------------------------------


Status: This module version was INACTIVE for this kernel.
depmod........


DKMS: uninstall completed.


------------------------------
Deleting module version: 4.3.8.12175.20140902+dfsg
completely from the DKMS tree.
------------------------------
Done.
Loading new rtl8812au-4.3.8.12175.20140902+dfsg DKMS files...
Building for 4.15.0-29-lowlatency
Building initial module for 4.15.0-29-lowlatency

Everything stops at the Building initial module point.

---

### Post by Bashing-om on 2018-07-23
flocculan; Hey hey :)

> **flocculant said:**
> Check /etc/modprobe.d/ for an nvidia.conf file

Bug was fix released : [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1761593](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-390/+bug/1761593)

Not as far as I can tell . I do run presently with the proprietary driver.. and /etc/modprobe.d/ :
> 
sysop@x1810:~$ ls -al /etc/modprobe.d/
total 60
drwxr-xr-x   2 root root  4096 Jul 21 01:42 .
drwxr-xr-x 131 root root 12288 Jul 23 11:32 ..
-rw-r--r--   1 root root  2507 Jul 30  2015 alsa-base.conf
-rw-r--r--   1 root root   154 May 25 13:38 amd64-microcode-blacklist.conf
-rw-r--r--   1 root root   325 Jan 28 09:34 blacklist-ath_pci.conf
-rw-r--r--   1 root root  1603 Jan 28 09:34 blacklist.conf
-rw-r--r--   1 root root   210 Jan 28 09:34 blacklist-firewire.conf
-rw-r--r--   1 root root   697 Jan 28 09:34 blacklist-framebuffer.conf
-rw-r--r--   1 root root   156 Jul 30  2015 blacklist-modem.conf
lrwxrwxrwx   1 root root    41 May 20 12:47 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r--   1 root root   583 Jan 28 09:34 blacklist-rare-network.conf
-rw-r--r--   1 root root   127 Feb  7  2017 dkms.conf
-rw-r--r--   1 root root   154 May  3 14:45 intel-microcode-blacklist.conf
-rw-r--r--   1 root root   347 Jan 28 09:34 iwlwifi.conf
sysop@x1810:~$


And nope, nouveau is not in the blacklist.conf file either .

mystery to me -

---

### Post by Bashing-om on 2018-07-23
1066kwebb; Hey .

So far looks good .. did you give it LOTS of time to compile the driver .. and do all its background stuff ?

what results now:
```

sudo apt update
sudo apt full-upgrade
sudo apt -f install
sudo dpkg -C

```

[INDENT][INDENT]maybe yes -
[INDENT][INDENT][INDENT]could be not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by QIII on 2018-07-23
Please do NOT hijack the OP's thread.  If you are still having problems of your own, please start your own threads.  Feel free to post the URL of this thread if you think it might be helpful.

Closed.

---

