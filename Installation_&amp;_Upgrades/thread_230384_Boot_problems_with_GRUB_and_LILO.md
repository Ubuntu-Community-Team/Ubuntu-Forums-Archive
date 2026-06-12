---
title: "Boot problems with GRUB and LILO"
date: 2006-08-05
forum: Installation &amp; Upgrades
---

### Post by kebes on 2006-08-05
This post will describe some difficulties I had with getting Kubuntu 6.06 LTS booting after a straight-forward install. I explain how I solved the problem. Thus this post doesn't require any replies... I'm only posting it so that others in my situation have a guide towards a solution. Note that nothing about this is KDE-specific, so this all applies to Ubuntu as well.

After a fresh (dual-booting) install of Kubuntu on my 160 Gb hard drive, I rebooted and received this unhelpful error message during the boot process:

```

Grub Loading Stage1.5
GRUB loading, please wait...
Error 18
```

"Error 18" means that the location of "/boot" is beyond the "1024 cylinder" limit inherent to older motherboard BIOS. That is, because my linux root partition (which includes "/boot") is the second partition on a large drive, it is more than 8 Gb from the start of the drive, and my legacy BIOS cannot handle this.

One possible solution at this stage is to reformat the drive in some way so that "/boot" sits as a small partition at the start of the drive. That way the GRUB bootloader can refer to it properly. In my case this was not an option. The LILO bootloader, on the other hand, can circumvent the BIOS limitation because it creates a drive map that can load the kernel from any point on the drive.

This is how I managed to install LILO on my Kubuntu system, instead of the default GRUB. The instructions assume that you have already installed Ubuntu/Kubuntu to the system, and know which partition the root directory resides on (in the example below, "/dev/hda6" is the location of the root directory for the new install). All the commands should be entered in a terminal (such as Konsole).

1. Boot off a Ubuntu/Kubuntu install CD, using it like a LiveCD. Once booted in, do not active the "Install" option.

2. mount the new install directory somewhere, and then "chroot" into it:
```

$ cd /mnt/
$ sudo mkdir newfs
$ sudo mount /dev/hda6 newfs
$ sudo chroot newfs/
```
This means that from within this terminal window, you will "appear to be" within the new installed filesystem (the one on the hardrive).

3. Install LILO. Now that you are chrooted, the installation will occur into the your new install, which means that it will be there when you (eventually) reboot into it:
```

# aptitude install lilo
```

If you try to actually use LILO at this stage, you will get a variety of errors. For instance, running "liloconfig" will say something like:
```

WARNING!
Your /etc/fstab configuration file gives device /dev/hda6 as the root filesystem device. This doesn't look to me like an "ordinary" block device. Either your fstab is broken and you should fix it, or you are using hardware (such as a RAID array) which this simple configuration program does not handle.
```
If you try to manually build a "/etc/lilo.conf" file, and run "/sbin/lilo" you'll probably get:
```

Fatal: raid_setup: stat("/dev/hda")
ERROR: correct /etc/lilo.conf manually and rerun /sbin/lilo
```
Despite what the errors say, the problem is not with "/etc/lilo.conf" but with your device directory "/dev/". Since you have not booted this particular filesystem, you'll notice that "/dev/" is empty. In particular this:
```
# ls /dev/hd*
```
returns nothing! (This problem and solution are described [in this forum post.]("http://forums.xandros.com/viewtopic.php?t=23794&view=previous")) To fix this, we need to get devices mounted properly.

4. Mount devices. First:
```

# mount /proc
# mount -t sysfs none /sys
```
...and now we need to explicitly mount the hardware devices that the LiveCD recognized. To do this, in *another* terminal (one that is NOT chrooted), run this:
```

$ sudo mount --bind /dev /mnt/newfs/dev/
```
This "bind-mount" creates aliases for all the devices in the installed filesystem. In the original terminal (the chrooted one), you should now be able to see hardware devices. In particular:
```

# ls /dev/hd*
```
should return your partitions!

5. Now you can run liloconfig:
```

# liloconfig
```
and follow the instructions (let it create a new "/etc/lilo.conf" for you, and install it to the master boot record (MBR) ).

6. You may need to modify the generated "etc/lilo.conf" (for instance, adding your "MS Windows" partition if you are dual-booting) and then run "/sbin/lilo" to update the MBR.


Hopefully this will be of some help to those who need to boot Ubuntu/Kubuntu off of older motherboards (without destroying the current arrangement of their partitions!).

---

### Post by VK2XCI on 2006-08-06
Well done!!

I have struggled with this problem for some time, with other debian based distros as well.

I knew what had to be done, but not how to do it. Simply not enough Linux knowlege. Now I do!!

The irony is... after updating all the mobo bios's, there's only one left that won't boot. 

Does now tho'.


Many thanks

---

