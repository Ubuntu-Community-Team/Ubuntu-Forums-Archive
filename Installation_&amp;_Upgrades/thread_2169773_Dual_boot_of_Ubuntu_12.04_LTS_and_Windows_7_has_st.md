---
title: "Dual boot of Ubuntu 12.04 LTS and Windows 7 has stopped working"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by amatey-teye on 2013-08-23
Hi,

I created a dual boot system of Ubuntu 12.04 LTS and Windows 7, following this blog:
[http://www.ubuntugeek.com/use-the-windows-bootloader-to-dual-boot-windows-vista-and-ubuntu.html](http://www.ubuntugeek.com/use-the-windows-bootloader-to-dual-boot-windows-vista-and-ubuntu.html)

It's worked well for the past 6 months but has no stopped working for an unknown reason. I run the Boot Info Script as a diagnostic:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

This generated a RESULTS.txt file which I have attached to this post. The Boot Info Summary is below. Can anyone help determine why Ubuntu fails to boot?

Thanks.


```
============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 12.04.2 LTS
    Boot files:        /grub/grub.cfg /boot/grub/grub.cfg /etc/fstab 
                       /grub/core.img /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.06 4.06-pre7
    Boot sector info:  Syslinux looks at sector 30536 of /dev/sdb1 for its 
                       second stage. SYSLINUX is installed in the  directory. 
                       The integrity check of the ADV area failed. According 
                       to the info in the boot sector, sdb1 starts at sector 
                       0. But according to the info from fdisk, sdb1 starts 
                       at sector 62.
    Mounting failed:   fuse: mount failed: Device or resource busy
fuse: mount failed: Device or resource busy
mount: /dev/sdb1 already mounted or sdb1 busy
```

---

### Post by oldfred on 2013-08-23
It says it cannot mount your sda2 or main Windows NTFS partition. That can be hibernation or that it needs chkdsk. Boot-Repair cannot run chkdsk, you need to run that from a Windows repair console. If you can boot to repair since it does show sda1 as Windows boot partition and that contains a recovery or repair console. Most have to use a separate Windows repairCD or flash drive as the boot from grub to Windows is so quick that f8 rarely works. You can try the f8 and see but have to almost press at same time.

If you have access to another Windows 7 that is either 32 or 64 bit to match yours.
 Make your own Windows repairCD (not vendor recovery):
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)
Windows users only - Silverlight
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)

   Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by amatey-teye on 2013-08-23
Thanks for replying Oldfred (and for fixing my post). :)

I thought I should give you some more information before I committed to creating a Windows recovery disk:

I can boot up OK with windows, it only seems that  when I select Ubuntu from the window boot menu, I get directed to the Ubuntu boot up, then redirected to the start menu. So I'm not sure if the any issues with any Windows partitions is the cause.

As can be seen from my grub.cfg, the default record should boot so the issue is with my os-prober not seeing the Linux install in sda5 for some reason.

---

### Post by oldfred on 2013-08-23
Just like Boot-Repair could not mount the Windows partition, grub2 cannot chain load to a partition it cannot 'see'. So if you can boot directly it probably is the hibernation issue. Although with my old XP, I had an issue where it would boot, but gparted would not even see then entire drive. After chkdsk Windows booted quicker (3 minutes instead of 4)  and then it worked again in gparted and booting from grub.

---

### Post by amatey-teye on 2013-08-24
Hi oldfred,

I have fixed the issue. :) I followed the instruction in this blog to purge and re-install GRUB (had to do it twice):
[http://www.tavisonline.com/2011/10/fix-broken-grub/](http://www.tavisonline.com/2011/10/fix-broken-grub/)

It was important that I did NOT do this:
[COLOR=#C20CB9][FONT=monospace]**mount**[/FONT][/COLOR][COLOR=#000000][FONT=monospace] [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]dev[/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]sdYY [/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]mnt[/FONT][/COLOR][COLOR=#000000][FONT=monospace]**/**[/FONT][/COLOR][COLOR=#000000][FONT=monospace]boot
[/FONT][/COLOR]
I'd done it previously so I think the /boot directory went "missing" to os-prober. I could be wrong in my explanation as i'm fairly new to all of this. Anyway it works. There are a few error messages in the new bootinfoscript RESULTS file but I'll leave it for now.

Thanks once again.

---

### Post by oldfred on 2013-08-24
Most directions on manually reinstalling grub leave off the extra mount of a separate /boot partition as most users do not have a separate /boot nor need it. Only needed if a separate partition.
But you do not have the separate /boot partition so not needed.

---

