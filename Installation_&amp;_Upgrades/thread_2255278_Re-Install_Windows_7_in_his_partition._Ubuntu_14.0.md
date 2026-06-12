---
title: "Re-Install Windows 7 in his partition. Ubuntu 14.04 is installed"
date: 2014-12-03
forum: Installation &amp; Upgrades
---

### Post by luca122131 on 2014-12-03
Hi, I have Windows 7 Professional N installed alongside Ubuntu 14.04 and I have to re-install Windows 7 Ultimate SP1; the image below describes the situation:

[IMG]http://texnostuff.com/site/000RisorseScaricabili/SituationPreReinstallWin.png[/IMG]

I can't lose any Ubuntu data, so I checked a lot of post and I figured that I have to:
[LIST]
[*]Install Windows
[*]Repair the boot
[/LIST]

But the question is: I have to delete partitions **/dev/sda1** and **/dev/sda2 **and create a new **ntfs **partition insted of these two and install windows here **OR **I have only to delete the /dev/sda2 and install windows here o anything else?

Thanks!

---

### Post by oldfred on 2014-12-03
Do not know on Windows installs. May be best to ask that on a Windows forum.

But if your data is at all valuable are you not already backing all of it up regularly. Just be sure to refresh backup before install.

Windows will overwrite MBR and put its boot loader into the MBR, You have to have a current version Ubuntu live installer to restore grub boot loader to MBR.

Windows also sometimes rewrites partition table. And since it does not recognize Linux partition, just leaves it out. May be recoverable with testdisk, but best to have partition table backup. If you change partition sizes after backup, then the partition table backup will not help.

       Backup partition table structure to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by luca122131 on 2014-12-03
Thanks for the reply. I asked about /dev/sda1 and /dev/sda2 because I know that these partitions were both created by the first windows installation (at that time the disk was blank and only later I installed Ubuntu).

My doubt is if in the /dev/sda1 could be something of the Ubuntu Installation or maybe the GRUB...  If Ubuntu installation only occupy the /dev/sda3 and over, I can delete both the /dev/sda1 and /dev/sda2 and install windows here. Then I think that I can restore the GRUB w/o problems.

Where is the GRUB installed? There's a way to know?

Sorry, but when I have to do operations like this I'm always anxious...

---

### Post by oldfred on 2014-12-03
Grub is in the MBR, and occupies a few sectors after the MBR with core.img. And the rest of grub, menus & configuration settings are all in your Ubuntu install.

You should not have any Linux settings in the two NTFS partitions, unless you used EasyBCD or other non-standard configurations.
You should be able to delete sda1 & sda2, make sure you have backed up all you data and settings you may want. Not sure anymore all the details with Windows as my last Windows install was XP in 2006.

If you want lots of details on how your install is configured. You can run Boot-Repairs summary report.
The first part of the summary report is bootinfoscript which is just a bash script. I run the script as part of my rsync backup, so I always have a detail list of my configuration saved.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I run the updated fork version as it reports grub2 correctly in MBR.

 Updated fork  as bootinfoscript does not seem to be maintained
[https://github.com/arvidjaar/bootinfoscript](https://github.com/arvidjaar/bootinfoscript)
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Boot Info Script 0.61 is released April 2, 2012
boot_info_script.sh" file renamed to "bootinfoscript
[http://sourceforge.net/projects/bootinfoscript/files/latest/download](http://sourceforge.net/projects/bootinfoscript/files/latest/download)
Page with instructions and link to above download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Mark Phelps on 2014-12-04
When Windows 7 is installed on a blank hard drive, it automatically creates the two partitions -- the first one being a boot partition.  Once a drive has been partitioned, if you THEN install Windows 7, it will only create one partition.  So, after you remove sda1 and sda2, you can install Windows 7 into the newly unallocated space and only use one partition for that.

---

