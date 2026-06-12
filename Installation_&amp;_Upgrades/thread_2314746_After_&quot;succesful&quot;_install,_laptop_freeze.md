---
title: "After &quot;succesful&quot; install, laptop freezes during boot!"
date: 2016-02-23
forum: Installation &amp; Upgrades
---

### Post by irvine_himself2 on 2016-02-23
I am trying to install Ubuntu Studio Wily WereWolf, the live version works okay, and the laptop is a Toshiba Satellite P50-c

Initially, it repeatedly failed to create a working grub.

Then, there were multiple problems with incorrect partitions.

Now, after what it considers a succesful install, it runs through a series of checks before freezing: 

```

fsk from util-linux 2.26.2
[ok] started light display
       starting wpa supplicant......

[ok] ------
[ok] ------

[ok] ------
[ok] ------
[ok] reached target network....
       started host name
[   ] starting light display
```

At this point it freezes, with the cursor blinking at the position of the two empty brackets. 

Could somebody please explain what is  I can fix it.

Thanks Irvine.

---

### Post by irvine_himself2 on 2016-02-23
After some research, there seems to be a suggestion that the problem is related to the fstab file? (see here [http://ubuntuforums.org/showthread.php?t=1595358](http://ubuntuforums.org/showthread.php?t=1595358) )
 
Below is the fstab that freezes

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--studio--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sdb2 during installation
UUID=9d1e0e51-a62e-434b-a41f-9219cfbfab77 /boot           ext2    defaults        0       2
# /boot/efi was on /dev/sdb1 during installation
UUID=0180-0C11  /boot/efi       vfat    umask=0077      0       1
/dev/mapper/ubuntu--studio--vg-swap_1 none            swap    sw              0       0
```


For comparison, here is the fstab from the live ISO, (which boots fine.)

```
overlay / overlay rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
```

Knowing very little about fstab and understanding even less, I have no idea about how to proceed. So, would anybody care to comment on the above files, point me in right direction or otherwise give me a few clues? Additionaly, would it be worthwhile replacing the fstab that freezes with the fstab form the live ISO, or would that just muck things up beyond repair?

Thanks in advance, Irvine

Okay, I have done some more checking, (along with quite a lot of guessing,) and no longer think it is anything to do with the file system?

I have run the fdisk and fsck utilities from the live media, and here are the abreviated results

```
ubuntu-studio@ubuntu-studio:~$ sudo fdisk -l /dev/sda
Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 96F766AC-324F-4BFD-B049-3E22ABE952F8
Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 466903039 465852416 222.1G Linux filesystem
/dev/sda3  466903040 500117503  33214464  15.9G Linux swap


ubuntu-studio@ubuntu-studio:~$ sudo mount /dev/sda2 /mnt
ubuntu-studio@ubuntu-studio:~$ ls /mnt
bin    core  home        lib64       mnt   root  srv  usr
boot   dev   initrd.img  lost+found  opt   run   sys  var
cdrom  etc   lib         media       proc  sbin  tmp  vmlinuz

ubuntu-studio@ubuntu-studio:~$ cat /mnt/etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu 15.10"


ubuntu-studio@ubuntu-studio:~$ sudo fdisk -l
Disk /dev/sda: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 96F766AC-324F-4BFD-B049-3E22ABE952F8
Device         Start       End   Sectors   Size Type
/dev/sda1       2048   1050623   1048576   512M EFI System
/dev/sda2    1050624 466903039 465852416 222.1G Linux filesystem
/dev/sda3  466903040 500117503  33214464  15.9G Linux swap


ubuntu-studio@ubuntu-studio:~$ sudo fsck /dev/sda2
fsck from util-linux 2.26.2
e2fsck 1.42.12 (29-Aug-2014)
/dev/sda2: clean, 289896/14565376 files, 2673116/58231552 blocks

ubuntu-studio@ubuntu-studio:~$ sudo fsck /dev/sda1
fsck from util-linux 2.26.2
fsck.fat 3.0.28 (2015-05-16)
/dev/sda1: 6 files, 864/130812 clusters
```


One point to note though is that  unlike /dev/sda2, /dev/sda1 is not marked as "clean". Is that relevant? After all, this is the EFI partition, and if the problem was there, then the grub2 bootlaoder wouldn't load?


I have also discovered some more symptoms:


[LIST]
[*]Switching external media OFF and ON creates more ouput as it connects and disconnects from the devices. 
[*]Additionaly, when I power off to reboot into the live media, I get the Ubuntu Studio log-off screen 
[/LIST]

As a result, I think it is something to do with the desktop logon screen not loading?

Does anybody have any views on this, or even better, understand what is going wrong?

Thanks Irvine

Okay, it is definately something to do with the desktop not loading. When it freezes I managed to load the tty1 terminal. Subsequently, I tried reinstalling xorg and lightdm as suggested for a similar problem with 15.04: [https://askubuntu.com/questions/638850/ubuntu-15-04-boot-hangs-on-starting-light-display-manager-after-updates](https://askubuntu.com/questions/638850/ubuntu-15-04-boot-hangs-on-starting-light-display-manager-after-updates)

Needless to say, that particular solution failed, but, since I can load the tty1 terminal, it is looking more and more like the problem is something to do with the desktop.

Alternatively, there was a new bug report filed yesterday, (while I was installing Ubuntu Studio,) that suggests it may be something to do with the kernel version. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548867](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1548867)

I am not sure what is the best direction to take here, and am definately way above my paygrade, so a little bit of advice would be extremely welcome.

Thanks Irvine

Edit
I just rebooted into tty1 and checked the kernel version, it is :   4.2.0-16- lowlatency  and is dated Oct 2015. 

So, does this  exclude it being a problem with the kernel?

Irvine


The problem is definately something to do with xorg crashing. Unfortunately, (after searching online,) there are a multitude of possible reasons for it to crash, and some of the suggested solutions strike me as being dangerous.

Could somebody who knows what they are doing look at this Xorg log file and offer suggestions.


```
[   559.880] 
X.Org X Server 1.17.2
Release Date: 2015-06-16
[   559.880] X Protocol Version 11, Revision 0
[   559.880] Build Operating System: Linux 3.19.0-30-generic x86_64 Ubuntu
[   559.880] Current Operating System: Linux That-One 4.2.0-16-lowlatency #19-Ubuntu SMP PREEMPT Thu Oct 8 16:19:23 UTC 2015 x86_64
[   559.881] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.2.0-16-lowlatency root=UUID=9e999e92-e988-43f8-8cc1-b23bc112c0bc ro quiet splash vt.handoff=7
[   559.881] Build Date: 30 September 2015  09:08:47AM
[   559.881] xorg-server 2:1.17.2-1ubuntu9 (For technical support please see http://www.ubuntu.com/support) 
[   559.882] Current version of pixman: 0.32.6
[   559.885]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   559.886] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   559.891] (==) Log file: "/var/log/Xorg.0.log", Time: Wed Feb 24 17:24:51 2016
[   559.892] (==) Using config file: "/etc/X11/xorg.conf"
[   559.893] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   559.893] (==) ServerLayout "layout"
[   559.893] (**) |-->Screen "nvidia" (0)
[   559.893] (**) |   |-->Monitor "<default monitor>"
[   559.894] (**) |   |-->Device "nvidia"
[   559.894] (==) No monitor specified for screen "nvidia".
    Using a default monitor configuration.
[   559.894] (**) |-->Inactive Device "intel"
[   559.894] (==) Automatically adding devices
[   559.894] (==) Automatically enabling devices
[   559.894] (==) Automatically adding GPU devices
[   559.894] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   559.894]     Entry deleted from font path.
[   559.894] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   559.894]     Entry deleted from font path.
[   559.894] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   559.894]     Entry deleted from font path.
[   559.894] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   559.894]     Entry deleted from font path.
[   559.894] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   559.894]     Entry deleted from font path.
[   559.894] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   559.894] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   559.894] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   559.894] (II) Loader magic: 0x5602f8b56d40
[   559.894] (II) Module ABI versions:
[   559.894]     X.Org ANSI C Emulation: 0.4
[   559.894]     X.Org Video Driver: 19.0
[   559.894]     X.Org XInput driver : 21.0
[   559.894]     X.Org Server Extension : 9.0
[   559.894] (II) xfree86: Adding drm device (/dev/dri/card0)
[   559.896] (--) PCI:*(0:0:2:0) 8086:1916:1179:f840 rev 7, Mem @ 0x92000000/16777216, 0xa0000000/268435456, I/O @ 0x00005000/64
[   559.896] (--) PCI: (0:1:0:0) 10de:1346:1179:f843 rev 162, Mem @ 0x93000000/16777216, 0x80000000/268435456, 0x90000000/33554432, I/O @ 0x00004000/128
[   559.896] (II) LoadModule: "glx"
[   559.896] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   559.896] (II) Module glx: vendor="X.Org Foundation"
[   559.896]     compiled for 1.17.2, module version = 1.0.0
[   559.896]     ABI class: X.Org Server Extension, version 9.0
[   559.896] (==) AIGLX enabled
[   559.896] (II) LoadModule: "nvidia"
[   559.897] (WW) Warning, couldn't open module nvidia
[   559.897] (II) UnloadModule: "nvidia"
[   559.897] (II) Unloading nvidia
[   559.897] (EE) Failed to load module "nvidia" (module does not exist, 0)
[   559.897] (II) LoadModule: "modesetting"
[   559.897] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   559.897] (II) Module modesetting: vendor="X.Org Foundation"
[   559.897]     compiled for 1.17.2, module version = 1.17.2
[   559.897]     Module class: X.Org Video Driver
[   559.897]     ABI class: X.Org Video Driver, version 19.0
[   559.897] (==) Matched intel as autoconfigured driver 0
[   559.897] (==) Matched intel as autoconfigured driver 1
[   559.897] (==) Matched modesetting as autoconfigured driver 2
[   559.897] (==) Matched fbdev as autoconfigured driver 3
[   559.897] (==) Matched vesa as autoconfigured driver 4
[   559.897] (==) Assigned the driver to the xf86ConfigLayout
[   559.897] (II) LoadModule: "intel"
[   559.897] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[   559.897] (II) Module intel: vendor="X.Org Foundation"
[   559.897]     compiled for 1.17.2, module version = 2.99.917
[   559.897]     Module class: X.Org Video Driver
[   559.897]     ABI class: X.Org Video Driver, version 19.0
[   559.897] (II) LoadModule: "modesetting"
[   559.897] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   559.897] (II) Module modesetting: vendor="X.Org Foundation"
[   559.897]     compiled for 1.17.2, module version = 1.17.2
[   559.897]     Module class: X.Org Video Driver
[   559.897]     ABI class: X.Org Video Driver, version 19.0
[   559.897] (II) UnloadModule: "modesetting"
[   559.897] (II) Unloading modesetting
[   559.897] (II) Failed to load module "modesetting" (already loaded, 22018)
[   559.897] (II) LoadModule: "fbdev"
[   559.897] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   559.897] (II) Module fbdev: vendor="X.Org Foundation"
[   559.897]     compiled for 1.17.1, module version = 0.4.4
[   559.897]     Module class: X.Org Video Driver
[   559.897]     ABI class: X.Org Video Driver, version 19.0
[   559.897] (II) LoadModule: "vesa"
[   559.897] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   559.897] (II) Module vesa: vendor="X.Org Foundation"
[   559.897]     compiled for 1.17.1, module version = 2.3.4
[   559.897]     Module class: X.Org Video Driver
[   559.897]     ABI class: X.Org Video Driver, version 19.0
[   559.897] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   559.897] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[   559.898] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[   559.898] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[   559.898] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[   559.898] (II) FBDEV: driver for framebuffer: fbdev
[   559.898] (II) VESA: driver for VESA chipsets: vesa
[   559.898] (++) using VT number 1

[   559.898] (--) controlling tty is VT number 1, auto-enabling KeepTty
[   559.898] (II) modeset(G0): using drv /dev/dri/card0
[   559.898] (WW) Falling back to old probe method for fbdev
[   559.898] (II) Loading sub module "fbdevhw"
[   559.898] (II) LoadModule: "fbdevhw"
[   559.898] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   559.898] (II) Module fbdevhw: vendor="X.Org Foundation"
[   559.898]     compiled for 1.17.2, module version = 0.0.2
[   559.898]     ABI class: X.Org Video Driver, version 19.0
[   559.898] (WW) Falling back to old probe method for vesa
[   559.898] (EE) No devices detected.
[   559.898] (EE) 
Fatal server error:
[   559.898] (EE) no screens found(EE) 
[   559.898] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[   559.898] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[   559.898] (EE) 
```


Due to a very limited data allowance, I can't immediately do a major download. So, tommorow, failing some easy, obvious solution I shall visit a friend and use his internet to install propietary drivers from the terminal. Hopefully, this will solve the problem, though I would still like some guidance.

Irvine

---

### Post by matthewk2 on 2016-02-24
I have been running 14.04 on a VM on my Windows notebook for a long time now.  Yesterday I got some updates that included the new abi-3.16.0-62-generic kernel.  Last night my Windows machine rebooted for updates.  Yea, the joys of Windows..  So my VM was closed.  Today when I went to restart the VM that has been working flawlessly for the past year, it was hanging after trying to start strongswan.  After booting up in single user mode and making it so it would not want to start strongswan, it started hanging after trying to start the vmware tools.  On a hunch I rebooted into the old kernel and poof, it came right up, happy as a clam.  If you have a kernel older than abi-3.16.0-62-generic, I am now running on abi-3.16.0-60-generic for example, you might want to give that a try.  It would be good to get the security updates in the new kernel, but for now it is more important to have a working machine.

---

### Post by irvine_himself2 on 2016-02-25
So, finally, after a major panic  attack I have fixed this problem. The solution was to launch the tty1 terminal by pressing the **"cntrl" "alt"** and **"F1" **keys

Then,
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get upgrade-distro

reboot

sudo ubuntu-drivers devices  #This a list of proprietary drivers

**# In my case**
sudo apt-get install intell-microcode
sudo apt-get install nvidia-352

reboot
```

**Note 1:**
The last two sudo lines are the proprietary drivers for my machine, you will need to edit the lines to suit your own situation

**Note 2:**
[LIST]
[*]I first tried this without doing a full update, only installing the Nvidia drivers and running  "startx" without rebooting, this lead to the black screen that has been reported elsewhere. 
[*]Even worse, because the GUI expected me to confirm I wanted to quit, I couldn't easily power off with the xserver running. 
[*]Restarting tty1 stopped the xserver, and I was able to reboot. 
[*]Upon rebooting, the OS went into cycle of repeatedly restarting the xserver. 
[*]At this point I had no other option than to completely re-install Wily Werewolf 
[*]In conclusion: Do a full update and upgrade of the system before installing the intell driver, followed by the Nvidia driver. Then, rather than use trying to start the xserver, just reboot. 
[/LIST]

If anybody else has this problem, then I can only wish you the best of luck.

Irvine

---

### Post by QDR06VV9 on 2016-02-25
Nicely Done Irvine! :wink: 			And thanks for posting your efforts and solution..
Should be helpful to others..
Cheers :grin:

---

