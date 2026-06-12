---
title: "Can't see Windows 7 on installation only FreeDos"
date: 2014-02-24
forum: Installation &amp; Upgrades
---

### Post by MadleSs on 2014-02-24
Hi, I'm trying to install Ubuntu 13.10 alongisde with Win7 and I only can see FreeDos when I'm trying to install. If I installed it alongside with FreeDos would it delete Windows? FreeDos has only 1GB partition so I don't know if it would work if i tried to install ubuntu over it. Partitions in my pc are a one 100GB Windows partition, 900GB for stuff on other partition and there are two other 1GB partitions one i guess is recovery (there's one key folder) and other one is FreeDos ... I don't care if FreeDos will be there 1GB won't kill me. So please give me some advice. 
Thank you

---

### Post by sudodus on 2014-02-24
Please run the boot-info script and upload it according to this link

[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by MadleSs on 2014-02-24
[http://paste.ubuntu.com/6990545/](http://paste.ubuntu.com/6990545/) Here it goes ... Thanks for quick response

---

### Post by sudodus on 2014-02-24
You have 4 of 4 possible primary partitions in the internal drive. So there is no logical space in the partition table for Ubuntu to be installed.

sda1: FREE-DOS (I guess)
sda2: Windows 7
sda3: Data partition ?
sda4: Compaq diagnostics

In order to be able to install Ubuntu, you must sacrifice one partition (for example the FREEDOS partition; it is possible to run a FREEDOS version off a USB pendrive [http://rufus.akeo.ie/](http://rufus.akeo.ie/)

You must also create disk space with ***gparted***, I would suggest at least 20 GB but 40 GB makes it 'last longer', and that can be created by shrinking sda3 and making an extended partition using the unallocated space. 

```

Filesystem     Type       Size  Used Avail Use% Mounted on
/dev/sda3      fuseblk    832G  256G  [COLOR=#ff0000]577G[/COLOR]  31% /mnt/boot-sav/sda3

```

```

============================= Boot Info Summary: ===============================

 => Windows 7/8/2012 is installed in the MBR of /dev/sda.
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows 7/2008: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /boot/bcd /grldr /KERNEL.SYS 
                       /COMMAND.COM

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 7/2008: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/bcd

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  SYSLINUX 4.04 2011-04-18
    Boot sector info:  Syslinux looks at sector 10216952 of /dev/sdb1 for 
                       its second stage. SYSLINUX is installed in the  
                       directory. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot/grub/grub.cfg /syslinux/syslinux.cfg 
                       /casper/vmlinuz.efi /EFI/BOOT/grubx64.efi /ldlinux.sys
```

---

### Post by Mark Phelps on 2014-02-24
> Hi, I'm trying to install Ubuntu 13.10 alongisde with Win7Just make sure that you do NOT use the Ubuntu installer to shrink the Win7 OS partition to make room for Ubuntu.  Doing that can sometimes result in corruption to the Win7 filesystem, and if that happens, you will not be able to back into Win7 to fix it.

Also, before you start down this path, do yourself a favor and use the Win7 Backup feature to create and burn a Win7 Repair CD.  That will give you the tools needed to repair or restore Win7 boot capability, should that become damaged during dual boot setup.

---

