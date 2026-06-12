---
title: "Software updates wants to install certain upgrades again and again"
date: 2015-12-18
forum: Installation &amp; Upgrades
---

### Post by darth.jon09 on 2015-12-18
[ATTACH=CONFIG]266235[/ATTACH]

My Kubuntu 14.04.03 OS asks to install the above upgrades multiples times in a month. When the installation is completed I don't get any errors except when I run autoremove I get the following messages:

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-headers-3.19.0-39 linux-headers-3.19.0-39-generic
  linux-image-3.19.0-39-generic linux-image-extra-3.19.0-39-generic
  linux-signed-image-3.19.0-39-generic
0 to upgrade, 0 to newly install, 5 to remove and 4 not to upgrade.
After this operation, 288 MB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 263423 files and directories currently installed.)
Removing linux-headers-3.19.0-39-generic (3.19.0-39.44~14.04.1) ...
Removing linux-headers-3.19.0-39 (3.19.0-39.44~14.04.1) ...
Removing linux-signed-image-3.19.0-39-generic (3.19.0-39.44~14.04.1) ...
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-41-generic
Found initrd image: /boot/initrd.img-3.19.0-41-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-73-generic
Found initrd image: /boot/initrd.img-3.13.0-73-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-extra-3.19.0-39-generic (3.19.0-39.44~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
update-initramfs: Generating /boot/initrd.img-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-41-generic
Found initrd image: /boot/initrd.img-3.19.0-41-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-73-generic
Found initrd image: /boot/initrd.img-3.13.0-73-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-3.19.0-39-generic (3.19.0-39.44~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
dkms: removing: virtualbox 4.3.34 (3.19.0-39-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  virtualbox
Version: 4.3.34
Kernel:  3.19.0-39-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

vboxdrv.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-39-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetadp.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-39-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxnetflt.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-39-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.


vboxpci.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.19.0-39-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
update-initramfs: Deleting /boot/initrd.img-3.19.0-39-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.19.0-39-generic /boot/vmlinuz-3.19.0-39-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-41-generic
Found initrd image: /boot/initrd.img-3.19.0-41-generic
Found linux image: /boot/vmlinuz-3.13.0-73-generic
Found initrd image: /boot/initrd.img-3.13.0-73-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done

```

Thank you in advance.

---

### Post by Bashing-om on 2015-12-18
darth.jon09' So ;

What is the question/issue ?

I see it as virtualbox depends on " Kernel:  3.19.0-39-generic (x86_64) "

as you are removing that old kernel, will also remove the dependency of virualbox .
So far so good - if you do not use virtualbox. .... The system is seeing virtualbox as orphaned and will remove it .

Presently:
```

sudo apt update
sudo apt upgrade
sudo apt-get -f install

```
runs clean ?

[INDENT][INDENT]if it ain't broke
[INDENT][INDENT][INDENT]do not fix it
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by darth.jon09 on 2015-12-18
Well, my issue is that almost every week I have to install the same upgrades. I have VirtualBox installed, and Windows is also installed as a second OS but how these affect Kubuntu software updates?

I run update and upgrade (dist-upgrade) and I got the following (again):

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-73 linux-headers-3.13.0-73-generic
  linux-image-3.13.0-73-generic linux-image-extra-3.13.0-73-generic
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed
  linux-headers-3.13.0-74 linux-headers-3.13.0-74-generic
  linux-image-3.13.0-74-generic linux-image-extra-3.13.0-74-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 to upgrade, 4 to newly install, 0 to remove and 0 not to upgrade.
Need to get 61.6 MB of archives.
After this operation, 271 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-74-generic amd64 3.13.0-74.118 [15.2 MB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.13.0-74-generic amd64 3.13.0-74.118 [36.8 MB]
Get:3 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-generic amd64 3.13.0.74.80 [1,786 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-generic amd64 3.13.0.74.80 [2,252 B]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-74 all 3.13.0-74.118 [8,889 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-74-generic amd64 3.13.0-74.118 [698 kB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-generic amd64 3.13.0.74.80 [2,240 B]
Fetched 61.6 MB in 1min 56s (531 kB/s)                                         
Selecting previously unselected package linux-image-3.13.0-74-generic.
(Reading database ... 233231 files and directories currently installed.)
Preparing to unpack .../linux-image-3.13.0-74-generic_3.13.0-74.118_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-74-generic (3.13.0-74.118) ...
Selecting previously unselected package linux-image-extra-3.13.0-74-generic.
Preparing to unpack .../linux-image-extra-3.13.0-74-generic_3.13.0-74.118_amd64.deb ...
Unpacking linux-image-extra-3.13.0-74-generic (3.13.0-74.118) ...
Preparing to unpack .../linux-generic_3.13.0.74.80_amd64.deb ...
Unpacking linux-generic (3.13.0.74.80) over (3.13.0.73.79) ...
Preparing to unpack .../linux-image-generic_3.13.0.74.80_amd64.deb ...
Unpacking linux-image-generic (3.13.0.74.80) over (3.13.0.73.79) ...
Selecting previously unselected package linux-headers-3.13.0-74.
Preparing to unpack .../linux-headers-3.13.0-74_3.13.0-74.118_all.deb ...
Unpacking linux-headers-3.13.0-74 (3.13.0-74.118) ...
Selecting previously unselected package linux-headers-3.13.0-74-generic.
Preparing to unpack .../linux-headers-3.13.0-74-generic_3.13.0-74.118_amd64.deb ...
Unpacking linux-headers-3.13.0-74-generic (3.13.0-74.118) ...
Preparing to unpack .../linux-headers-generic_3.13.0.74.80_amd64.deb ...
Unpacking linux-headers-generic (3.13.0.74.80) over (3.13.0.73.79) ...
Setting up linux-image-3.13.0-74-generic (3.13.0-74.118) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-41-generic
Found initrd image: /boot/initrd.img-3.19.0-41-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-73-generic
Found initrd image: /boot/initrd.img-3.13.0-73-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-extra-3.13.0-74-generic (3.13.0-74.118) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.19.0-41-generic
Found initrd image: /boot/initrd.img-3.19.0-41-generic
Found linux image: /boot/vmlinuz-3.13.0-74-generic
Found initrd image: /boot/initrd.img-3.13.0-74-generic
Found linux image: /boot/vmlinuz-3.13.0-73-generic
Found initrd image: /boot/initrd.img-3.13.0-73-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-generic (3.13.0.74.80) ...
Setting up linux-headers-3.13.0-74 (3.13.0-74.118) ...
Setting up linux-headers-3.13.0-74-generic (3.13.0-74.118) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-74-generic /boot/vmlinuz-3.13.0-74-generic
Setting up linux-headers-generic (3.13.0.74.80) ...
Setting up linux-generic (3.13.0.74.80) ...

```

Thank you.

---

### Post by Bashing-om on 2015-12-18
darth.jon09; Hummm ..

Well there is so far this inconsistency:
> 
Unpacking linux-image-3.13.0-74-generic (3.13.0-74.118) ...
bk
Found linux image: /boot/vmlinuz-3.19.0-41-generic

which begs the question as to why install a trusty kernel when you have the updated vivid stack ?

Maybe we best look at what kernels and control files are installed:
```

dpkg -l | grep linux-

```

Virtualbox:

Are you running ubuntu as the virtual operating system within Windows as the host ? 
OR is virtualbox setting there in ubuntu awaiting further deployments ?

[INDENT][INDENT]sometimes
[INDENT][INDENT][INDENT]I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by darth.jon09 on 2015-12-18
I have a multiboot, Kubuntu and Windows. Also, I have VirtualBox installed because I want to try a math software SAGE, but I haven't installed any operating system with VirtualBox.

```

ii  linux-firmware                              1.127.19                                all          Firmware for Linux kernel drivers
ii  linux-generic                               3.13.0.74.80                            amd64        Complete Generic Linux kernel and headers
ii  linux-generic-lts-vivid                     3.19.0.41.26                            amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.13.0-74                     3.13.0-74.118                           all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-74-generic             3.13.0-74.118                           amd64        Linux kernel headers for version 3.13.0 on 64 bit x86 SMP
ii  linux-headers-3.19.0-41                     3.19.0-41.46~14.04.2                    all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-41-generic             3.19.0-41.46~14.04.2                    amd64        Linux kernel headers for version 3.19.0 on 64 bit x86 SMP
ii  linux-headers-generic                       3.13.0.74.80                            amd64        Generic Linux kernel headers
ii  linux-headers-generic-lts-vivid             3.19.0.41.26                            amd64        Generic Linux kernel headers
rc  linux-image-3.13.0-71-generic               3.13.0-71.114                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.13.0-73-generic               3.13.0-73.116                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-3.13.0-74-generic               3.13.0-74.118                           amd64        Linux kernel image for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-25-generic               3.19.0-25.26~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-33-generic               3.19.0-33.38~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-37-generic               3.19.0-37.42~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-3.19.0-39-generic               3.19.0-39.44~14.04.1                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-3.19.0-41-generic               3.19.0-41.46~14.04.2                    amd64        Linux kernel image for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-71-generic         3.13.0-71.114                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.13.0-73-generic         3.13.0-73.116                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
ii  linux-image-extra-3.13.0-74-generic         3.13.0-74.118                           amd64        Linux kernel extra modules for version 3.13.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic         3.19.0-25.26~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-33-generic         3.19.0-33.38~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-37-generic         3.19.0-37.42~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
rc  linux-image-extra-3.19.0-39-generic         3.19.0-39.44~14.04.1                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-extra-3.19.0-41-generic         3.19.0-41.46~14.04.2                    amd64        Linux kernel extra modules for version 3.19.0 on 64 bit x86 SMP
ii  linux-image-generic                         3.13.0.74.80                            amd64        Generic Linux kernel image
ii  linux-image-generic-lts-vivid               3.19.0.41.26                            amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                        3.13.0-74.118                           amd64        Linux Kernel Headers for development
ii  linux-signed-generic-lts-vivid              3.19.0.41.26                            amd64        Complete Signed Generic Linux kernel and headers
rc  linux-signed-image-3.19.0-33-generic        3.19.0-33.38~14.04.1                    amd64        Signed kernel image generic
rc  linux-signed-image-3.19.0-37-generic        3.19.0-37.42~14.04.1                    amd64        Signed kernel image generic
rc  linux-signed-image-3.19.0-39-generic        3.19.0-39.44~14.04.1                    amd64        Signed kernel image generic
ii  linux-signed-image-3.19.0-41-generic        3.19.0-41.46~14.04.2                    amd64        Signed kernel image generic
ii  linux-signed-image-generic-lts-vivid        3.19.0.41.26                            amd64        Signed Generic Linux kernel image
ii  linux-sound-base                            1.0.25+dfsg-0ubuntu4                    all          base package for ALSA and OSS sound systems
ii  syslinux-common                             3:4.05+dfsg-6+deb8u1                    all          collection of boot loaders (common files)
ii  syslinux-legacy                             2:3.63+dfsg-2ubuntu5                    amd64        Bootloader for Linux/i386 using MS-DOS floppies

```

---

### Post by Bashing-om on 2015-12-18
darth.jon09; Hummm ...

Debating with myself
You have installed :
> 
ii  linux-generic 
ii  linux-generic-lts-vivid

ii  linux-headers-generic
ii  linux-headers-generic-lts-vivid

ii  linux-image-generic
ii  linux-image-generic-lts-vivid


Where i "think" the linux-generic , linux-headers-generic, and linux-image-generic control the trusty kernels - that are no longer required as 
the others control the vivid kernels that you are on .

So what are you presently booting with ?
Show:
```

uname -r

```

Maybe what we need to do here is remove the trusty meta package control files - and purge all those 'rc' files .

I believe that, but will welcome others input here also .

[INDENT][INDENT]clean up the system and call it good
[/INDENT][/INDENT]

---

### Post by darth.jon09 on 2015-12-18
I am using Kubuntu most of the time. I only boot Windows for pc games. Do you know how that might have happened? Because the only thing I did was to install Kubuntu and then installed the upgrades and some programs.

When I typed ```
uname -r
```
This is the output I got:

```

3.19.0-41-generic

```

---

### Post by Bashing-om on 2015-12-18
darth.jon09; Welp;

No, I do not have any idea how the situation as shown by "dpkg -l ' could have happened . Sure is a mis-podge of partially installed kernels .
But the good news is that it is fixable. However, presently I am tired and my thinking is forced .
Lemme have the night to consider a proper procedure here to straighten this out . Things must be done in the proper order .

[INDENT][INDENT]study twice
[INDENT][INDENT][INDENT]act once
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by ian-weisser on 2015-12-18
The OP seems to have tried to follow the 14.04 LTS Enablement Stack, but has perhaps fallen off the wagon.
See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Do you recall why you added a 15.04 (Vivid) kernel?

If not, remove the linux-generic-lts-vivid package, which provides those 15.04 kernels. Autoremove the dependencies (the actual kernels), and stick to the security updates in 14.04 provided by linux-generic.

However, if you installed the 15.04 kernel packages for a good reason, then it should be safe enough to do the opposite. Remove linux-generic and autoremove it's 14.04-based kernels.
Then it's probably time for you to migrate to 15.10 kernels, the linux-generic-lts-wily package. You may then remove linux-generic-lts-vivid and autoremove it's 15.04-based kernels.

---

### Post by darth.jon09 on 2015-12-20
No, I do not recall if I added a 15.04 (Vivid) kernel. But, since my system works okay, do you think it's safe to just leave as it is? Will a clear new installation of Kubuntu fix these problems? Yesterday I got a new message for software updates.

[ATTACH=CONFIG]266282[/ATTACH]


If someone installs Kubuntu 15.04 on a partition and then from Windows  deletes the partition and after that installs Kubuntu 14.04.03 could it  be the reason of creating problems in the kernels?

---

### Post by ian-weisser on 2015-12-20
> **darth.jon09 said:**
> No, I do not recall if I added a 15.04 (Vivid) kernel.
If you don't recall the reason for adding it, then follow the advice in Post #9.

> **darth.jon09 said:**
> But, since my system works okay, do you think it's safe to just leave as it is?
If you wish, sure. It's a minor problem. Like you painted your bathroom two incompatible colors.
You will continue to receive Vivid kernel updates until you follow the advice in Post #9 and remove the appropriate package.

> **darth.jon09 said:**
> Will a clear new installation of Kubuntu fix these problems?
Yes, in the sense that a bad paint choice can be remedied by a very expensive remodel-and-refixture.
A new installation will fix the problem, but is rather overkill. This is a minor problem, and easily (permanently) fixed in a few seconds.

> **darth.jon09 said:**
> If someone installs Kubuntu 15.04 on a partition and then from Windows  deletes the partition and after that installs Kubuntu 14.04.03 could it  be the reason of creating problems in the kernels?
That's easy: No. Not a chance. The paint in your bathroom does not affect the drippy faucet.

---

### Post by oldos2er on 2015-12-20
Moved to Installation & Upgrades.

---

### Post by darth.jon09 on 2015-12-20
Okay then. Thank you and Bashing-om very much for your help. I appreciate it. :)

---

### Post by Bashing-om on 2015-12-21
darth.jon09; Hey ....

We are ALL here to help, guide and assist. IF you are satisfied and happy with your system;
AND there are no further questions regarding this present matter:
Please mark this thread solved;
aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]we go on about our merry way
[/INDENT][/INDENT]

---

