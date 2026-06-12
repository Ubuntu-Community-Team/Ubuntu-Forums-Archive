---
title: "No grub menu after installing Win7 &amp; Ubuntu 11.04"
date: 2011-07-06
forum: Installation &amp; Upgrades
---

### Post by tech_girl on 2011-07-06
I recently got myself a Lenovo x120e and have installed Win7 Ultimate (32-bit) and Ubuntu 11.04 AMD64 respectively. However I do not see GRUB menu instead I boot automatically into Windows. This is my first time dual booting Windows and Linux. I have read some of the dual booting guides but I think I have missed a step which resulted in automatic booting into Win7.

I first installed Win 7 Ultimate in a 30GB partition, and then using a live cd, I installed Ubuntu with boot, root, home and swap partitions.And I did not shrink the volume in my Win7 partition as mentioned in the guide though. Not sure if this will cause any errors or if this is why its not showing the grub menu.

I will need some help in trying to fix it. I have used the BIS from meierfra to generate the output.
```

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos1)/boot/grub on this drive.
 => Grub Legacy (v0.97) is installed in the MBR of /dev/sdc and looks on the 
    same drive in partition #2 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1    *          2,048       206,847       204,800   7 NTFS / exFAT / HPFS
/dev/sda2             206,848    61,941,759    61,734,912   7 NTFS / exFAT / HPFS
/dev/sda3          61,941,760    62,918,655       976,896  83 Linux
/dev/sda4          62,920,702   625,141,759   562,221,058   5 Extended
/dev/sda5          62,920,704   101,980,159    39,059,456  83 Linux
/dev/sda6         101,982,208   613,423,103   511,440,896  83 Linux
/dev/sda7         613,425,152   625,141,759    11,716,608  82 Linux swap / Solaris


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 8168 MB, 8168931328 bytes
22 heads, 52 sectors/track, 13946 cylinders, total 15954944 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *          2,048    15,953,919    15,951,872  83 Linux


Drive: sdc _____________________________________________________________________

Disk /dev/sdc: 16.4 GB, 16437477376 bytes
255 heads, 63 sectors/track, 1998 cylinders, total 32104448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1                  63    32,097,869    32,097,807   b W95 FAT32


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/sda1        32209F9B209F649F                       ntfs       System Reserved
/dev/sda2        9E1AAEB51AAE8A3B                       ntfs       
/dev/sda3        e8e0df10-ef7e-4fa7-ab4f-e6c6c570732d   ext2       
/dev/sda5        2b1d15bb-9d9a-41ff-99ea-12befe82bc97   ext4       
/dev/sda6        59c1e536-2efa-4508-8407-ea26be365bcc   ext4       
/dev/sda7        01c58c5c-e565-4132-a438-acf2bd7bc95d   swap       
/dev/sdb1        1f6c7299-5126-49b0-82d6-98d9f8367e1e   ext3       
/dev/sdc1        4AB7-69CF                              vfat       PORTABLE

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /tmp/BootInfo0/sda1      fuseblk    (ro,nosuid,nodev,allow_other,blksize=4096)
/dev/sdb1        /                        ext3       (rw,errors=remount-ro,commit=600)
/dev/sdc1        /media/PORTABLE          vfat       (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


========================== sda1/grldr embedded menu: ===========================

--------------------------------------------------------------------------------

=============================== StdErr Messages: ===============================

unlzma: Decoder error
./boot_info_script.sh: line 1888: (  / 2 ) + 16 : syntax error: operand expected (error token is "/ 2 ) + 16 ")


```

Also I would like some advice on what is the best partitioning  scheme? My current partitioning is as follows (as I went through the ubuntu installation wizard: 

first partition system(primary), 
second partition Win7 (primary), 
third partition boot ext 2 (primary)
fourth partition /root ext4 (logical)
fifth partition /home ext 4
sixth partition /swap ext 4

Would be grateful if someone can point me in the right direction. :)

---

### Post by ajgreeny on 2011-07-06
You have two grubs showing in your RESULTS.txt file, grub2 on sdb, and legacy grub (from the live CD/USB?) on sdc.  Nothing in that txt file looks to be wrong to me, but if that was the complete text output, there are several parts missing, eg /boot/grub/grub.cfg file is normally quoted in full.

As grub2 is on sdb, I suspect you are booting with sda set as the first boot device.  Change that to sdb, and I think you may see grub try to appear, but with no configuration file I don't think it will get you anywhere and will simply drop you to a <grub repair> prompt.

I think that using a separate /boot partition is adding big complications to the situation, and suggest that as you have obviously not yet used this install, you might find it easiest to start again, using just a root, /home and swap for ubuntu, leaving out the /boot partition completely.  You do not need to set a boot flag to you ubuntu partitions as it is not needed for linux.

Using the live boot of ubuntu, can you mount the partition on which you have put the root partition of your installed ubuntu, and the /boot partition and see if there is a **/boot/grub/grub.cfg **file anywhere to be seen.

Lets go one step at a time, and see where we end up.  It should be quite easy to solve, even if eventually you re-install the system

---

### Post by tech_girl on 2011-07-06
Hi. Thanks for taking the time to answer my call for help.

I see a/boot/grub/grub.cfg file in my /boot partition.

sdb is my live cd and sdc is my sdhc card.

---

### Post by ajgreeny on 2011-07-06
I am not sure if I can sort this much further for you, other than repeating my comment about getting rid of the /boot partition when you re-install ubuntu.  I have no idea how to make grub look for the grub.cfg file in your /boot, but it may be worth trying a reinstall of grub using the live CD/USB before you do anything else.
[Grub 2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") has all the info you need for doing that.

If I were doing this I would use the manual partitioning at install, use separate root (10 - 15 GB) and /home (The remaining space except for 2 - 4 GB swap) and swap partitions, and let grub2 go on the MBR of the hard disk; it seems to make fewer problems than many other "exotic" partition arrangements, such as yours.

---

### Post by oldfred on 2011-07-06
It seems the boot script has an issue with grub4dos. It must find the file, but then not the rest of the configuration and error out.

this is line 1887 in the parsing of grub4dos info:
  # Check if magic bytes that go before the embedded menu, are present.

I agree with ajgreeny on preferring not to have a boot partition. I makes repairs a bit more comples as you have to also mount the /boot partition and many of the repairs instrucitons do not mentions that (since it is uncommon) or just have a footnote that most miss. Only very old systems, servers, RAID or LVM advanced configurations may need a /boot.

During install did you select to install grub2's boot loader to the 8GB flash or do have a BIOS that promoted the flash drive to sda and the default install just installed grub's boot loader back onto the flash drive? That would overwrite the syslinux boot so your liveCd then may not work.

Did you try booting from the 8GB flash. I may work, but without full boot script it is difficult to tell.

---

### Post by kjelljs on 2011-07-06
What is considered to be the GRUB menu? My computer boots and says something like GRUB then one other word and there is nothing to select. Is that considered to be the GRUB menu?

---

### Post by ajgreeny on 2011-07-06
This is the grub menu, though the contents may look different on your machine.  However, if you only have the one OS installed (ubuntu) no menu will appear unless you hold down shift when you see the word GRUB on screen.

---

### Post by YesWeCan on 2011-07-06
> **tech_girl said:**
> Would be grateful if someone can point me in the right direction. :)
Hi there. It appears that you boot straight into Windows because sda does not have Grub installed. It has a standard MBR which is set to boot Windows. As oldfred says, the Ubuntu installer might have installed Grub somewhere else.

To install Grub to sda, you need to boot from live CD/USB. Then double-check the name that your HD has:
[COLOR="Navy"]sudo fdisk -l[/COLOR]
Then identify the partition name that /boot is in.
Suppose the disk is sda and the partition containing /boot is sda5,
[COLOR="Navy"]sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda[/COLOR]
Then reboot.
If you are not offered a menu with Windows on it, after Ubuntu boots run
[COLOR="Navy"]sudo update-grub[/COLOR]

---

### Post by tech_girl on 2011-07-07
OK.. will try YesWeCan's method or re-install Ubuntu without /boot partition.Will report back.

---

### Post by tech_girl on 2011-07-09
All has been resolved. :) I followed YesWeCan's instruction. 

After the reboot, and selecting ubuntu on the grub menu, it went blank. I rebooted, selected recovery mode in the grub menu and updated the bootloader. After that all was ok.

Thank you for all the help.

---

### Post by YesWeCan on 2011-07-09
Glad to hear it.
Don't forget to mark this thread "solved" in [COLOR=Red]Thread Tools[/COLOR] above. :)

---

