---
title: "Hard Disk Partitioning not shown during installation"
date: 2014-06-18
forum: Installation &amp; Upgrades
---

### Post by Mithun_Raj_Arackal on 2014-06-18
I use a laptop with Windows 8 installed on it. When I am trying to install any version of linux the _partition window doesn't show any partitions _but when I booted the system using an OS for disk management the disk was partitioned. All the partition managers that I used in Windows (EASEUS, default Disk Management tool of Windows) also showed the partitions. The HDD size is 500GB, its make is Hitachi and during installation_ the whole HDD is shown as 1 disk drive_. I think the _disk is a basic disk_ because when I used the OS for partition management the option for converting the disk from Dynamic to Basic was greyed out. What should I do to install Linux alongside Windows without affecting my files.[ATTACH=CONFIG]254049[/ATTACH]

---

### Post by oldfred on 2014-06-18
Did laptop come with Windows 8 or did you install it yourself. 
Not sure from Windows tools if it shows some of the typical UEFI install partitions. With UEFI you have a FAT32 partition and you do have one FAT32 partition. But some vendors use that as the recovery partition.

Post this from terminal in Ubuntu live installer.
sudo parted -l

Do not let Windows create partitions as it may convert to dynamic and that does not work with Linux at all and even some Windows repair tools do not work.

Do shrink the Windows NTFS partition using the Windows partition tools and reboot so it can run chkdsk and make repairs for its new size.

Linux NTFS driver will not mount a NTFS partition needing chkdsk, but it also does not mount NTFS if hibernated and Windows 8 is always hibernated, called fast boot. You must make sure fast boot is off.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
Fast boot is hidden.
Control Panel -> Power icon -> Choose what power buttons do -> Change settings that are currently unavaliable, make sure fast startup is unchecked 

Still better to use Something Else or manual install. But you have to manually create and mount / (root) partition, specify format like ext4 and a swap partition, no format. You can also then specify additional partition like /home if desired and it is normally recommended. Default or auto installs only create / & swap.

Only real difference with UEFI or BIOS installs is which grub is installed.

 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

Something Else required for installs to second drive, but manual install process is identical even if only one drive. Only difference is which drive to install grub boot loader into, sda or sdb. With either UEFI or BIOS you install grub to sda.

 Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

