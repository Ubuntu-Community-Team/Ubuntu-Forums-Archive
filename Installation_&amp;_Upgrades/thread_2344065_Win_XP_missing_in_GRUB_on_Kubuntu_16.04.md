---
title: "Win XP missing in GRUB on Kubuntu 16.04"
date: 2016-11-22
forum: Installation &amp; Upgrades
---

### Post by stuck2 on 2016-11-22
Hi,

Updated my old laptop from Kubuntu 10.04 to 16.04(x64). Installation went well, 16.04 is running fine, but Win XP does not show up in GRUB.
sdb1 = Win XP
sdb2 = Lenovo Service partition
sdb3 = data
sdb4 = might be Lenovo Rescue & Recovery
sdb5 = 16.04
sdb6 = swap


1) tried ```
sudo update-grub
``` but nothing changed
2) checked partitions, boot flag for Win XP is set
3) installed Boot-repair from the live-usb (sda1) and generated this report: removed => see message below
 
Now Boot-repair suggested to write grub2 to all MBRs.
Would this not overwrite the existing entry of Win XP on sdb1 ? Am I missing something ?

Any help to get Win XP in my grub menu is highly appreciated.

Thanks,
Red

---

### Post by yancek on 2016-11-22
sdb4 is actually and Extended partition which is simply a container for the logical partitions.
I don't see your boot.ini file which is the boot menu for the old xp.  Could you check from Ubuntu to see if it exists.  It usually, but not always shows in the boot repair output so hopefully it is still there.  Did you also try running: sudo os-prober?   Obviously your xp won't boot as there is no windows entry in the grub.cfg, myabe os-prober will show.  Watch the output after you run the command.  Did you run update-grub from Ubuntu installed on the hard drive?

---

### Post by oldfred on 2016-11-22
If os-prober has not found it then yancek's analysis of missing boot.ini is correct.
Grub does not use boot flag to know a bootable partition, but looks for boot files. With Windows XP it looks for both ntldr & boot.ini. 

For what ever reason your flash drive is promoted to sdb. Your Windows boot.ini may have been set for first drive. Do you always have flash drive plugged in.

I found on several systems, not plugging drives into first SATA port or SATA0 and not skipping ports was important. Or on reboot flash drive would appear in location of missing unused SATA port renumbering all the drives. While UUID is used in many places you still use /dev/sdX in some places and then that changes.

Do not run Boot-Repair's auto fix. You do not want grub installed to flash drive. That should be considered an external drive which Boot-Repair would handle differently anyway.
Boot-Repair has advanced mode where you can choose operating system, and drive to install boot loader into. Only use that if needed.

---

### Post by stuck2 on 2016-11-23
Thanks for your help.
Drives sda, sdb, sdc: I ran boot-repair from a live system (sda) and saved output to another usb-stick (sdc).
Running os-prober from command line did not give any output and update-grub produced this output:
stuck@Kub1604:~$ sudo os-prober
[sudo] password for stuck: 
stuck@Kub1604:~$ sudo update-grub
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-4.4.0-47-generic
Found initrd image: /boot/initrd.img-4.4.0-47-generic
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done

Today I ran boot-repair from my ubuntu installation and this is the first part of the output:
```
 Boot Info Script cfd9efe + Boot-Repair extra info      [Boot-Info 26Apr2016]


============================= Boot Info Summary: ===============================

 => Grub2 (v2.00) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub. It also embeds following components:
    
    modules
    ---------------------------------------------------------------------------
    fshelp ext2 part_msdos biosdisk
    ---------------------------------------------------------------------------

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows 2000/XP: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /NTLDR /NTDETECT.COM

sda2: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: FAT32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /NTDETECT.COM

sda3: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info: 

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info: 
    Operating System:  Ubuntu 16.04.1 LTS
    Boot files:        /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/i386-pc/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info: 

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________
Disk /dev/sda: 298.1 GiB, 320072933376 bytes, 625142448 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *             63   146,815,199   146,815,137   7 NTFS / exFAT / HPFS
/dev/sda2         614,401,200   625,136,399    10,735,200  12 Compaq diagnostics
/dev/sda3         146,815,200   503,344,799   356,529,600   c W95 FAT32 (LBA)
/dev/sda4         503,344,861   614,401,199   111,056,339   f W95 Extended (LBA)
/dev/sda5         503,344,863   606,024,719   102,679,857  83 Linux
/dev/sda6         606,024,783   614,401,199     8,376,417  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        BA60C52B60C4EF67                       ntfs       Preload
/dev/sda2        3404-04F1                              vfat       SERVICEV001
/dev/sda3        AD2A-6438                              vfat       DATA
/dev/sda5        90151e74-0125-4af6-ad17-a12b53def267   ext4       
/dev/sda6                                               swap   

```

I did not see boot.ini on my Windows partition when checking from Ubuntu, so I guess you're right, it is missing. Not sure how this happened when installing Ubuntu on my pre-existing linux partition.

---

### Post by stuck2 on 2016-11-23
Solution: Added the missing boot.ini-file.
After copying the boot.ini-file from my backup to the Windows system partition (aka C), os-prober found Windows and update-grub added Windows to the grub menu. Now I can choose between Ubuntu and Windows as before, Windows is running too.

Thank you yancek & oldfred !

---

