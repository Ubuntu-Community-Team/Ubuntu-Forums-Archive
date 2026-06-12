---
title: "No such partition..."
date: 2012-02-02
forum: Installation &amp; Upgrades
---

### Post by Ashok24 on 2012-02-02
I have installed Kbuntu recently......I was using windows 7. And I installed Kbuntu on an un allocated space.... As dual boot...  For first time I was able to boot to windows 7 and kbuntu with out any issue. 

But the next day when I try to turn on the pc I get the message...

No Such Partition... 

Grub Rescue....


Any help would be greatly appreciated....

---

### Post by raja.genupula on 2012-02-02
> **Ashok24 said:**
> I have installed Kbuntu recently......I was using windows 7. And I installed Kbuntu on an un allocated space.... As dual boot...  For first time I was able to boot to windows 7 and kbuntu with out any issue. 

But the next day when I try to turn on the pc I get the message...

No Such Partition... 

Grub Rescue....


Any help would be greatly appreciated....
Look at grub recovery at my signature . 

if it not helped with your issue then post the output of bootinfoscipt (my signature) .

All the best.

---

### Post by Ashok24 on 2012-02-03
> **raja.genupula said:**
> Look at grub recovery at my signature . 

if it not helped with your issue then post the output of bootinfoscipt (my signature) .

All the best.
Thank for you quick reply..... 

May be this would help you.... 

I installed Kbuntu not ubuntu..... 

I tried install the grub by searching I got some commands... 

sudo fdisk -l  to check the linux installation and then entering the command


sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

After trying those commands.... Now I am getting just the Grub Version 1.99 and information about GRUB... 

grub.... cursor is blinking after grub that's it........

---

### Post by Ashok24 on 2012-02-03
> **Ashok24 said:**
> Thank for you quick reply..... 

May be this would help you.... 

I installed Kbuntu not ubuntu..... 

I tried install the grub by searching I got some commands... 

sudo fdisk -l  to check the linux installation and then entering the command


sudo mount /dev/sda2 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

After trying those commands.... Now I am getting just the Grub Version 1.99 and information about GRUB... 

grub.... cursor is blinking after grub that's it........
And I am not getting the boot repair..... 

I searching under system--Administration..... 

I even typed boot-repair under Terminal.....No Go.............................:(

---

### Post by drmrgd on 2012-02-03
In this regard, there shouldn't be a difference between Ubuntu and Kubuntu.  To be sure that you're setting up Grub correctly, please follow the instructions in Raja's signature for Bootinfoscript and post the output.  It may be that there are some erroneous entries in your Grub config file, and the information from Bootinfoscript will help sort it out.

---

### Post by Ashok24 on 2012-02-04
Sure I would do that and keep you posted.... Is there any way to chat with you guys online... because getting a reply from you guys is like 24 hours....

---

### Post by Ashok24 on 2012-02-04
I have tried the bootinfoscript... But after typing the command to reinstall the grub....

I got the follow screen.... May be this would help you...Nothing after grub:......

---

### Post by raja.genupula on 2012-02-04
hi ashok 
        please place here the output of bootinfoscript here and place it in code tags by selecting all and press # in this window .we need that thing .

---

### Post by Ashok24 on 2012-02-06
> **raja.genupula said:**
> hi ashok 
        please place here the output of bootinfoscript here and place it in code tags by selecting all and press # in this window .we need that thing .
Here's the information, which you have requested sir..........

                  ```
Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Syslinux MBR (3.61-4.03) is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda6: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        /boot/grub/core.img

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /grldr /bootmgr /Boot/BCD /grldr

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdb1: __________________________________________________________________________

    File system:       vfat
    Boot sector type:  Syslinux 4.03 or higher
    Boot sector info:   Syslinux looks at sector 3691728 of /dev/sdb1 for its 
                       second stage. It is very unlikely that Syslinux is 
                       (still) installed. The second stage could not be 
                       found. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
240 heads, 63 sectors/track, 129201 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1               2,046   512,002,047   512,000,002   5 Extended
/dev/sda5         195,313,664   234,373,119    39,059,456  82 Linux swap / Solaris
/dev/sda6         234,375,168   512,002,047   277,626,880  83 Linux
/dev/sda2    *    512,002,048   512,206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda3         512,206,848   716,802,047   204,595,200   7 NTFS / exFAT / HPFS


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 2063 MB, 2063597568 bytes
16 heads, 32 sectors/track, 7872 cylinders, total 4030464 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             32     4,030,463     4,030,432   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda2        46A4995BA4994DF5                       ntfs       System Reserved
/dev/sda3        9E2A9DC42A9D99BB                       ntfs       
/dev/sda5        37276bdf-bcbc-4974-872f-f8f07cf22f83   swap       
/dev/sda6        330487a8-0edc-4667-a220-f8f46b48a9fe   ext4       
/dev/sdb1        8AAF-08D5                              vfat       PENDRIVE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/PENDRIVE          vfat       (rw,nosuid,nodev,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,uhelper=udisks)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


=================== sda6: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

               =                boot/grub/core.img                             1

========================== sda2/grldr embedded menu: ===========================

--------------------------------------------------------------------------------
--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

awk: cmd. line:36: Math support is not compiled in

a
```

---

### Post by oldfred on 2012-02-06
Added code tags to make boot script easier to review.

You are not showing any Linux boot files in sda6. You also have two grub4dos /grldr in the root of Windows which may confuse Windows.

You also have a 4K drive which I do not fully understand the partitioning.

Technical details - from 2010 so now newer kernel resolve linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

Your first partition starts at 2046 which is a bit unusual.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print

---

### Post by Ashok24 on 2012-02-07
> **oldfred said:**
> Added code tags to make boot script easier to review.

You are not showing any Linux boot files in sda6. You also have two grub4dos /grldr in the root of Windows which may confuse Windows.

You also have a 4K drive which I do not fully understand the partitioning.

Technical details - from 2010 so now newer kernel resolve linux issues
[https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues](https://ata.wiki.kernel.org/index.php/ATA_4_KiB_sector_issues)

Your first partition starts at 2046 which is a bit unusual.

First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of RAID arrays and some types of new hard disks (those with 4096-byte physical sectors). See article by srs5694:
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)
[http://ubuntuforums.org/showthread.php?t=1768635](http://ubuntuforums.org/showthread.php?t=1768635)
[http://ubuntuforums.org/showthread.php?t=1635018](http://ubuntuforums.org/showthread.php?t=1635018)
srs's to show 8 sector alignment
$ sudo parted /dev/sda unit s print
Honestly I did get any of these at all.................I am ready to reinstall the Kbuntu. If you have any better option to reinstall both windows and Kbunutu. I am ready to do it. If this helps, I am also trying to install the Windows 2008 in future...As Triple Boot......

---

### Post by Ashok24 on 2012-02-07
> **Ashok24 said:**
> Honestly I did get any of these at all.................I am ready to reinstall the Kbuntu. If you have any better option to reinstall both windows and Kbunutu. I am ready to do it. If this helps, I am also trying to install the Windows 2008 in future...As Triple Boot......
My System configuration. 

AMD X6 1090 T Processor. 
1 TB Sata Harddrive. 
8 GB DDR3 RAM. 
1 GB Nvidia Graphics card.

---

### Post by oldfred on 2012-02-07
Not sure if with Windows 8 it will still be the same. Windows 8 wants UEFI booting which is only new systems. Current test versions do install in BIOS systems as a few have posted it.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

With nVidia I have always had to add the nomodeset parameter.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by Ashok24 on 2012-02-08
> **oldfred said:**
> Not sure if with Windows 8 it will still be the same. Windows 8 wants UEFI booting which is only new systems. Current test versions do install in BIOS systems as a few have posted it.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

With nVidia I have always had to add the nomodeset parameter.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
I was talking about the Server 2008, and by the way seriously I did not had any issues when I was using only the Kbunut... That to the old version I had which was 8.10. It worked with out any issue. 

Only when I try to do dual boot, that's when all the problems started. Even now I could use the windows 7 by just repairing the boot, and I still have the Kbuntu installed on the computer. 

Only that I am not able to boot to it. 

You tell me what is the other option, because I tried the same method. Which is aval on your website. But it did not help me...Do you have any other option. Were I could try installing both windows 7 and Kbuntu as Dual boot. In future If I have to add, I could add any other operating system.

---

### Post by oldfred on 2012-02-08
Unless you have reinstalled, you show one Linux partition with only core.img which is part of grub2. You show no kernel or other files that are required to boot.

---

### Post by Ashok24 on 2012-02-10
> **oldfred said:**
> Unless you have reinstalled, you show one Linux partition with only core.img which is part of grub2. You show no kernel or other files that are required to boot.
So do you want me to reinstall the Kbunut again, in the same harddrive place.. As in windows do you have any option to do inplace upgrade or repair installation of Kbunutu. Which I could try.....

---

### Post by oldfred on 2012-02-10
If you have something in your install to save, you should back it up. Your /home should always be well backed up.
You can use chroot to get into a broken install and run many updates to fix it. 

drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

#Then run whatever other commands needed - no sudo needed if chroot (maybe good to run "df- H" and "cat /etc/issue" to be certain #you mounted the correct partition).
#Commands once in chroot:
#if not chroot use: sudo -i
#houseclean
apt-get autoclean   # only removes files that cannot be downloaded anymore (obsolete)
apt-get clean
#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a
# reinstall desktop
apt-get remove ubuntu-desktop
apt-get install ubuntu-desktop
# uninstall both grub legacy & grub2 reinstall grub2 and to sda
apt-get purge grub grub-pc grub-common
mv /boot/grub /boot/grub_backup
mkdir /boot/grub
apt-get install grub-pc grub-common
grub-install /dev/sda
grub-install --recheck /dev/sda

#reinstall kernel:
sudo apt-get update
sudo apt-get install linux-image
sudo update-grub

sudo dpkg-reconfigure grub-pc

---

