---
title: "Win7 BOOTMBR missing after upgrade"
date: 2012-04-13
forum: Installation &amp; Upgrades
---

### Post by chortle on 2012-04-13
I had Windows on a 60GB SSD, where I booted, and another installation on a 1TB internal drive (the original Win install, before I bought the SSD). I rarely used the 60GB SSD Windows as I planned to move to Ubuntu. So I booted up and then chose the 1TB Windows 7 most days.

I wiped the 60 GB SSD drive and installed Ubuntu. I want to be able to boot that 1TB Windows install. It didn't appear in grub, so I had it added (/dev/sdc). When I choose it from the grub menu I get BOOTMGR missing. 

I *think*, reading around, that all my Windoze 7 boot information was switched onto that SSD once I installed Windows there. I guess that wiping that drive killed the boot information for the wiped Windows partition and also Windows on the separate 1TB drive.

Fooling around I added Lilo to the 1TB Windows drive, hoping this would solve my problem. No luck. Just mentioning this so that you can understand why Lilo is on this drive.

See below for the bootinfoscript output (there is more - grub contents - if you want it)

 ```
                 Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    for (,msdos1)/boot/grub on this drive.
 => Grub2 (v1.99) is installed in the MBR of /dev/sdb and looks at sector 1 of
    the same hard drive for core.img. core.img is at this location and looks
    for (,msdos1)/boot/grub on this drive.
 => Lilo is installed in the MBR of /dev/sdc.
 => Windows is installed in the MBR of /dev/sdd.

sda1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:  Ubuntu 11.10
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sdb1: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:
    Operating System:
    Boot files:

sdb2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:

sdb5: __________________________________________________________________________

    File system:
    Boot sector type:  -
    Boot sector info:
    Mounting failed:   mount: unknown filesystem type ''

sdc1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

sdd1: ______________________________________________    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:
    Boot files:

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes/dev/sda1                  63   117,226,304   117,226,242  83 Linux


Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1               2,048 1,914,062,847 1,914,060,800  83 Linux
/dev/sdb2       1,914,064,894 1,953,523,711    39,458,818   5 Extended
/dev/sdb5       1,914,064,896 1,953,523,711    39,458,816  82 Linux swap / Solaris


Drive: sdc _____________________________________________________________________
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdc1               2,048 1,953,521,663 1,953,519,616   7 NTFS / exFAT / HPFS


Drive: sdd _____________________________________________________________________

Disk /dev/sdd: 2000.4 GB, 2000365289472 bytes
255 heads, 63 sectors/track, 243197 cylinders, total 3906963456 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdd1               2,048 3,906,963,455 3,906,961,408   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/mapper/cryptswap1 def11974-e47c-4fcd-836b-f5249c07a052   swap
/dev/sda1        c08cc9db-256a-41bf-aa9b-886e6a11511a   ext4
/dev/sdb1        ee3425e5-c5ac-4d4b-9d6b-a1b87b092514   ext4
/dev/sdc1        7244832D4482F361                       ntfs
/dev/sdd1        C6B04293B0428A3F                       ntfs       My Book

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:

control
cryptswap1

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,errors=remount-ro,commit=0)
/dev/sdb1        /home                    ext4       (rw,commit=0)
/dev/sdd1        /media/My Book           fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permiss$


=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------
=========================== sda1/boot/grub/grub.cfg: ===========================

--------------------------------------------------------------------------------

```

---

### Post by ronaldbrijo on 2012-04-13
I would suggest that you disconnect the ssd, boot form the windows intall disk and run startup repair on your windows drive. This will restore the MBR on that drive to be bootable again. 

Then reconnect the ssd, boot into Ubuntu and run "sudo upgrade -grub" in terminal.

This should then add the windows installation to grub.

---

### Post by raja.genupula on 2012-04-13
> **ronaldbrijo said:**
> I would suggest that you disconnect the ssd, boot form the windows intall disk and run startup repair on your windows drive. This will restore the MBR on that drive to be bootable again. 

Then reconnect the ssd, boot into Ubuntu and run "sudo upgrade -grub" in terminal.

This should then add the windows installation to grub.

there the command is 
sudo update-grub

---

### Post by darkod on 2012-04-13
You are right. Your win7 install is on /dev/sdc1 but two of the boot files were on the SSD I guess. They are missing now.

Boot with the win7 dvd and repair the boot process. It's best to do it from the command prompt. I don't have the link at hand right now, but I guess google will help you if you need exact instructions about the procedure.

Another option is using the automated repair process once you boot with the win7 dvd.

After win7 is booting itself, you can simply boot ubuntu and do the update-grub command.

IMPORTANT NOTE: I just noticed that you have no partition with the boot flag on. Before you try to repair win7 boot, you must set the boot flag on /dev/sdc1 because the process will look for it. You can open Gparted in ubuntu and set the boot flag on /dev/sdc1 first.

---

### Post by chortle on 2012-04-13
Thanks, everyone. Will locate my Win7 disc and take it from there, having set SDC1 bootable & disconnected SSD.

---

### Post by chortle on 2012-04-16
I made SDC1 active but I get the message

The system partition was not found: The requested system device can not be found

I just have a single partition for Windows. I think that the SSD, before I cleared it, had a couple of Windows partitions - one of them a tiny one. Perhaps this is what is missing? A little partition for Windows to weave it's evil magic.

---

### Post by ronaldbrijo on 2012-04-16
It is possible that the system partition could have been on the SSD.

Have you used your windows install dvd? It should be able to restore the system partition, although I've not had that problem yet

---

### Post by darkod on 2012-04-16
> **chortle said:**
> I made SDC1 active but I get the message

The system partition was not found: The requested system device can not be found

I just have a single partition for Windows. I think that the SSD, before I cleared it, had a couple of Windows partitions - one of them a tiny one. Perhaps this is what is missing? A little partition for Windows to weave it's evil magic.

Yes, the boot files were there and it's missing now.

But still the repair should be smart enough and do it. Since windows is sometimes idiotic, try making /dev/sdc first HDD in the boot order, so that it thinks it is the main system HDD.
Of course, you will still need to have CD-ROM in front of HDD as a device so you can boot with the win7 dvd, but in the HDD order set /dev/sdc first. Then try the repair again, few times the command prompt procedure, if that doesn't work, three times the Repair This Computer from the win7 dvd. Sometimes the auto process fixes one thing at a time so you would usually run it three times even though it doesn't ask you to do it.

---

### Post by oldfred on 2012-04-16
We have seen several cases where users installed Windows 7 to a second or third drive but the 100MB boot/repair partition was installed to the first drive. I think it happens when BIOS is set to boot from sda. Grub just defaults to sda, so it is not much better.

Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

The bootmgr and BCD do not have to be a separate partition. I did see one poster who just copied his bootmgr & BCD from his repair CD to his Windows partition. He still had to run bcdEdit or BootRec.exe /RebuildBcd as the repair BCD was not correct.

see step 2 - Vista & 7 work the same.
How to fix Vista/Window 7 when the boot files are missing - rebuild BCD with bcdedit
[http://ubuntuforums.org/showpost.php?p=5726832&postcount=4](http://ubuntuforums.org/showpost.php?p=5726832&postcount=4)
Some advanced BCD rebuild, Vista post #17 on:
[http://ubuntuforums.org/showthread.php?t=1426103](http://ubuntuforums.org/showthread.php?t=1426103)

---

### Post by chortle on 2012-04-16
Thanks. Will give that a go.

---

### Post by chortle on 2012-04-19
I copied the boot etc. files from my rescue disc. Now I get a bit further. The files are booted, but the machine thinks my hard drive is a rescue disc. It seems I will have to fool around a bit more!

---

### Post by oldfred on 2012-04-20
Your BCD controls that. You can use bcdEdit or from repair console command line run this:

 BootRec.exe /RebuildBcd

---

