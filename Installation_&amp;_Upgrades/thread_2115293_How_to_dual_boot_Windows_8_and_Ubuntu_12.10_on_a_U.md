---
title: "How to dual boot Windows 8 and Ubuntu 12.10 on a UEFI GPT system?"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by kio_http on 2013-02-12
I have a UEFI based system with the following drives.

0) Hard disk drive 500 GB
1) Solid state drive 40 GB

I installed Windows 8 on the 500 GB drive and let Windows system automatically create a GPT based partition table to use the whole drive.

Then I shrunk the Windows partition slightly.

I want to install Ubuntu with / on the SSD and /home and /var on partitions of the HDD. The problem is that Ubuntu detects the HDD (with win8 already on it) as unpartitioned space.

How can I get Ubuntu to detect the partitions on the GPT disk and let me resize and create additional partitions?

---

### Post by Damascushead on 2013-02-12
If you are trying to install 12.10 from a live usb or cd, select the "something other" option to install. Even if you don't plan on installing it manually, it should at least let you see how Ubuntu is recognizing the different disk partitions. 
 
Also, after you shrunk the Windows partition down to make more space, was there any indication of unallocated space? Because that is where Ubuntu should look to install. I know it sounds obvious but just make sure that it is not allocated as a blank formatted partition.
 
I just went through the same process, so let me know what you figure out.

---

### Post by oldfred on 2013-02-12
Is your 40GB drive really the Intel SRT or similar system. That uses RAID which the desktop installer does not currently see. 

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

    If you turn off the SRT in Windows or UEFI and run the commands to break the RAID then you can create gpt partitions on the SSD. You do have to have UEFI installed for Ubuntu if Windows is UEFI.
       Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

    Some info on re-instating  details in post #9
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

           Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
            Samsung Series 7 - post #5 Windows 8 & UEFI, Ubuntu only to new SSD
[http://ubuntuforums.org/showthread.php?p=12382951](http://ubuntuforums.org/showthread.php?p=12382951)

            UEFI dual boot two drives - HP
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
UEFI dual boot two drives see #14 on how edit UUID to Windows efi partiton
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

---

### Post by kio_http on 2013-02-13
Yes, it is an Intel SRT system. However I have disabled Intel SRT in the bios.

Windows sees the partition as with one partition for windows and the rest is un-allocated space, Ubuntu sees the entire disk as unallocated space.

---

### Post by Jimbrix on 2013-02-13
I'm going to upgrade my OS to Windows 8.

Can I install Wubi in it?

---

### Post by oldfred on 2013-02-13
If you have gpt partitioning wubi will not work. If MBR(msdos) it should.

With gpt partitioning there is no more 4 primary partition limit so new partitions for a full install are easier, but UEFI complicates things and Intel SRT even more.
Windows only boots from gpt partitioned drives with UEFI. And if installing Windows in BIOs mode on a drive that was gpt will not correctly convert it to MBR. Windows only overwrites the primary partition table, but gpt has a backup that Windows does not erase and Linux tools then do not know for sure if MBR or gpt.

---

