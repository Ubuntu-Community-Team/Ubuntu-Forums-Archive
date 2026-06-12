---
title: "Win 7 not booting after installing Ubuntu -- did you have a RAID array once?"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by NJBruce on 2010-11-12
If you once had a RAID setup on your system but have since disabled it, you may want to read this.  I hope it saves you time in figuring out why your system won't boot into Windows 7.

I installed Ubuntu 10.10 64-bit on my system, and Grub listed Windows 7 as a boot option but would not do anything except give me a blinking cursor when I selected it.  It took me 5 days of searching this forum for answers, but I finally did figure out what the problem was, mostly in thanks to the info in this thread: [http://ubuntuforums.org/showthread.php?t=1608366&highlight=raid+signature](http://ubuntuforums.org/showthread.php?t=1608366&highlight=raid+signature) .  It turns out that when you set up a RAID array on your system, metadata gets written onto the hard drives which identifies their role to play as part of the array.  Grub will see the metadata and try to use it to configure the boot menu.  Here's the kicker: disable the array in your BIOS, and your system will treat the drives as individual units again -- BUT -- the metadata is not erased, and Grub will still read that information and get wrong ideas about your setup.

My system has two identical Hitachi 500GB drives listed in the BIOS as SATA 3 and SATA 4, and one Samsung 80GB drive as SATA 1.  Windows 7 is installed on SATA 3 and is first in boot priority.  SATA 4 is NTFS formatted and is used as storage, and is second in boot priority.  SATA 1 has Windows XP and Ubuntu installed on it and is third in boot priority.  Formerly, I had the two Hitachis set up in a RAID 0 striped array but did away with this when it got corrupted.  (Note for the curious: before Ubuntu, I would move SATA 1 to be first in boot priority which would allow me to run Windows XP.)

Here's the steps I took to fix the Windows 7 boot problem.

1. I downloaded boot_info_script and executed "sudo bash boot_info_script055.sh" in a terminal which generated the RESULTS.TXT file, listing everything it could find about the hard drives including RAID info that still lived on them.  The tattletale info told me that my two Hitachi drives were still listed as being members of the former RAID array:

Device           UUID                                   TYPE       LABEL                         

/dev/mapper/nvidia_dcefddcb: PTTYPE="dos" 
/dev/sda                                                nvidia_raid_member                               
/dev/sdb                                                nvidia_raid_member                               
/dev/sdc1        9C00227800225992                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        50327195-c85d-4bb1-8577-735e0ce707a6   ext4                                     
/dev/sdc6        5f2cf18c-8aef-4387-957b-fd97ac7e5de9   swap       linux-swap                    
/dev/sdc: PTTYPE="dos" 
error: /dev/sda1: No such file or directory
error: /dev/sda2: No such file or directory

Note the two errors above.  I suspect that if I didn't have Windows XP on /dev/sdc1, I wouldn't have seen any listing in Grub's boot menu for Windows at all.  Instead, Grub seemed to think that Windows XP was Windows 7 instead and apparently failed to boot it properly.  This actually worked in my favor.  If I had not seen any listing for Windows 7 at all, I would have thought I'd lost the entire partition and probably would have done major havoc trying to restore it.  

2. I then executed "sudo dmraid -E -r /dev/sda" and "sudo dmraid -E -r /dev/sdb" which erased the metadata.  However, when I rebooted, to my amazement the metadata on the Hitachi drives came back!  The problem was in the Phoenix BIOS.  Under "Integrated Peripherals - RAID Config", even though the RAID Enable line was marked Disabled, I could see in grayed text that "Internal Phy SATA 3 RAID" and "Internal Phy SATA 4 RAID" were both still Enabled!  I had to mark RAID Enable as Enabled which highlighted these lines, then I could set them as Disabled. I then Disabled the RAID Enable line again.  After rebooting and re-executing the dmraid commands, I ran the boot_info_script again and got these new results:

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        7CB8D5B4B8D56D60                       ntfs       System Reserved               
/dev/sda2        060CF11A0CF10589                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb1        72B45733B456F8D5                       ntfs                                     
/dev/sdb: PTTYPE="dos" 
/dev/sdc1        9C00227800225992                       ntfs                                     
/dev/sdc2: PTTYPE="dos" 
/dev/sdc5        50327195-c85d-4bb1-8577-735e0ce707a6   ext4                                     
/dev/sdc6        5f2cf18c-8aef-4387-957b-fd97ac7e5de9   swap       linux-swap                    
/dev/sdc: PTTYPE="dos" 

3. I executed "sudo update-grub" to regenerate the Grub menu.  Success!  Windows 7 boots perfectly.  Now, all I have to do is get XP to boot... :-)

Update: Discovered the Grub command "drivemap -s (hd0) (hd2)" which allows XP to start!  Too cool, I have three working OS's now!

---

### Post by ronparent on 2010-11-12
Which all goes to explain why I recommend erasing the meta data before uninstalling dmraid. Although uninstalling dmraid will usually fix the problem after disabling the raid in bios, the drives will probably remain in use for a long time afterwards. The problem is likely to crop up again in a future install when the raid is long forgotten if meta data is still present on the drive and the fix is long forgotten.

---

