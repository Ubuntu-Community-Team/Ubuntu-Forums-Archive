---
title: "Why are there two links to Windows 7 in my boot menu?"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by zacktu on 2011-03-26
I have a new Thinkpad which has a boot partition and a Windows 7 partition.  (There's a third partition with recovery software that I'll ignore.)  I have installed older Ubuntu releases on several other systems and always prepared the partitions in advance and then done a manual installation.  This time I prepared /boot, /, /home, and swap partitions.  

When I started the install of Maverick, I the installer suggested that the boot manager be in sda1, which is the Thinkpad boot partition.  I stopped and read some forum submissions suggesting that the Ubuntu boot manager should go into the first partition, so I removed my /boot partition and let the installer place the boot manager into sda1.

Now the boot menu has two links for Windows 7: sda1, the original boot manager partition, and sda2, the original partition for Windows 7.  Both links work, so it appears that everything is okay.  I just want to know that this is what is supposed to happen.

---

### Post by Dutch70 on 2011-03-26
I have 2 on mine also, but one of them goes to recovery and I found the hard way that you don't want to select it unless you intend to do a recovery. You might want to post your boot info script. I don't know that much about it, but someone will.

To post your boot info script, boot up to your live cd/usb,  download the boot info script from the following link & save it to your desktop. 
[COLOR="RoyalBlue"][[COLOR="RoyalBlue"]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")[/COLOR]
Then open a terminal (Cntrl+Alt+T) and run the following command...

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a results.txt file on your desktop. Open that file and copy/paste the info  **between code tags** using the "#" symbol in the toolbar of your next post.

---

### Post by coffeecat on 2011-03-26
> **zacktu said:**
> Now the boot menu has two links for Windows 7: sda1, the original boot  manager partition, and sda2, the original partition for Windows 7.  Both  links work, so it appears that everything is okay.  I just want to know  that this is what is supposed to happen.

Don't worry about it. I get the same. The "proper" way of booting Windows 7 is from the boot manager partition but grub can manage to get Windows to boot from the C: drive without invoking the boot partition. I've never really bothered working out exactly how.

However...

> **zacktu said:**
> When I started the install of Maverick, I the installer suggested that the boot manager be in sda1, which is the Thinkpad boot partition.  I stopped and read some forum submissions suggesting that the Ubuntu boot manager should go into the first partition, so I removed my /boot partition and let the installer place the boot manager into sda1.

I really hope it didn't and I really hope you didn't. In fact I'm fairly confident that it didn't and you didn't, since you can boot Windows from sda1. If grub had written files to sda1 then it would have interfered with Windows' ability to boot. I'm sure the installer suggested sda, not sda1, meaning that it wanted to install grub code to the mbr, not the boot sector of sda1. But if there is any doubt, run the boot script that Dutch70 mentions. It will tell us where grub was installed.

---

### Post by zacktu on 2011-03-26
Now I remember that the installer suggested sda, rather than sda1.  I've already done what dutch suggested, so here's the beginning part of RESULTS.TXT:

<><<><><><><><><><><><>

                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.10
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  According to the info in the boot sector, sdb1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdb1 starts at sector 62.
    Operating System:  
    Boot files/dirs:   /boot/grub/grub.cfg

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *          2,048     2,459,647     2,457,600   7 HPFS/NTFS
/dev/sda2           2,459,648   212,174,847   209,715,200   7 HPFS/NTFS
/dev/sda4         212,176,894   354,787,327   142,610,434   5 Extended
/dev/sda5         212,176,896   220,565,503     8,388,608  82 Linux swap / Solaris
/dev/sda6         220,567,552   287,676,415    67,108,864  83 Linux
/dev/sda7         287,678,464   354,787,327    67,108,864  83 Linux

---

### Post by coffeecat on 2011-03-26
That looks fine to me:

> **zacktu said:**
> Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => [COLOR=Red]Grub 2 is installed in the MBR of /dev/sda [/COLOR]and looks on the same drive in 
    partition #6 for (,msdos6)/boot/grub.
 => Syslinux is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info: [COLOR=Red] No errors found in the Boot Parameter Block.[/COLOR]
    Operating System:  
    [COLOR=Red]Boot files/dirs:   /bootmgr /Boot/BCD[/COLOR]

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    [COLOR=Red]Boot files/dirs:   /bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe


I've reddened the important bits. Grub is installed to the mbr of sda and not the boot sector of sda1. Actually, it's  a common mistake for people to override the installer and install grub to a Windows partition. Takes a bit of sorting out, and I'm glad it's not what happened to you. :)

Also - I think your bootscript explains why Windows will happily boot from sda2 as well as sda1. Bootmgr and BCD are in both - although tbh I'm a bit hazy about the details of Windows boot files.

---

### Post by zacktu on 2011-03-26
Thanks for having a look.  All is well.

---

