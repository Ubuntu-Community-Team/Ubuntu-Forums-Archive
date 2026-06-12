---
title: "Dual-boot problems with Windows 10 and ubuntu 18*"
date: 2018-07-04
forum: Installation &amp; Upgrades
---

### Post by fitzgreen on 2018-07-04
I have a problem with my Lenovo h500. I replaced the hard drive with a 1 TB WDC drive and upped the RAM to 8 GB.

  The unit came with Windows 8, and I upgraded to Windows 10 and have installed every update up until May 2018. SO, I have the latest version of the OS.

  Then  I installed ubuntu 18.04 in a dual-boot configuration, keeping my  Windows 10.  A few days ago, while ubuntu was updating to a new version,  my mouse ran out of power, and the machine suddenly switched off. 

  When  I rebooted, I got a black screen with a message that lasted less than a  second. By videoing the screen, I was able to get this:

  **Failed to open \EFI\BOOT\grubx64.efi – Not Found**

  **Failed to load image ** **\EFI\BOOT\grubx64.efi – Not Found**

  **Start_image() returned Not Found**

  So,  I can’t boot into windows or ubuntu, but I can get to a cmd prompt line  using a Windows recovery DVD. My bios doesn’t help. It only gives me an  option to start in UEFI or legacy mode. After failing with legacy, I’ve  switched to UEFI permanently. But the BIOS won’t let me scrounge around  and delete references to ubuntu. And I can’t get to it through the  command line on the Rescue Disk either.

  So here are the things I’ve tried to fix this:

  
[LIST=1]
[*]Ran the ubuntu Boot_repair program. Didn’t fix it.
[*]Tried to replace the file in terminal. Didn’t fix it.
[*]Re-installed ubuntu. Didn’t fix it. Just added another copy.
[*]Removed the new installation of ubuntu. Didn’t fix it.
[*]Deleted the partitions on which ubuntu resided. Created a new partition in that space. Didn’t fix it.
[*]Tried to fix the FAT32 system partition through a number of different means, including:
[LIST=1]
[*]Using the bootrec /fixboot command. Response: Access is denied.
[*]Tried bootrec /rebuildbcd. Access denied.
[*]Tried to open the bcd with BCDedit. OS couldn’t find the “object.”
[*]Decided  I needed full access to the System Disk. Assigned a drive letter to the  system disk. Didn’t fix it. Access problem not fixed.
[*]Changed the gpt attributes of the file. Access problem not fixed..
[*]Tried  the Set=id 07, and 17. Those commands, though suggested in many blogs,  were not recognized by Recovery disk OS. Access problem not fixed.
[*]Using  DISKPART, deleted the system partition. Created a new EFI partition.  Didn’t fix it. SWith a brand new system drive, still can’t use the  bootrec tools. Couldn’t unhide the partition I created. Still no access  to bootrec tools.
[/LIST]
[/LIST]
                          If  the problem is that the BIOS is still being told to look for the ubuntu  starter, then the problem appears not reside in the system disk, which  although still hidden doesn't have any references to the ubuntu files.  My questions are:

  Why can’t I use the bootrec tools?

  On which partition is this screen message stored? 

  How can I access what the BIOS appears to accessing, namely, a file that is telling it to try to open ubuntu?

  Why is there no ubuntu uninstall program?

   

Thanks

---

### Post by oldfred on 2018-07-04
Abnormal shutdown often corrupts file system. Windows needs chkdsk if it was in use. And with Ubuntu it may need fsck on all ext4 partitions.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

If you can boot to command line:
       To see all the ext4 partitions
sudo parted -l
#From liveDVD/Flash so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
# -y auto answers yes for fixes needing response, also see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1 
    
some systems may need full cold boot or total power down to allow access to UEFI to change settings or boot order. Remove all power, if laptop remove battery, hold power switch for 10 to 20 sec to drain any remaining power. Then boot and press correct key to get into UEFI/BIOS.

---

