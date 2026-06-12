---
title: "Windows 7 and Ubuntu installed on separate drives"
date: 2015-10-12
forum: Installation &amp; Upgrades
---

### Post by ben179 on 2015-10-12
Hi folks.  I'm kinda new to Ubuntu and running two operating systems.  So here's the deal.  My primary OS is Windows 7 which is installed on my primary hard drive.  On my second hard drive, I'd like to install Ubuntu.  What I don't want is for the boot process to acknowledge that Ubuntu is installed on the computer.  I want my computer to boot straight into Windows without the "please select an OS in the next 7 seconds" window.  I only want Ubuntu to be an option when I hit F8 and select from the myriad of boot options.  I had done it once a couple of years ago, but I have no idea how I managed it.  Can someone point tell me or point me to a walkthrough that will explain it?  Thanks in advance!

---

### Post by oldfred on 2015-10-12
Do not use any auto install options, grub's default with all auto install options is to overwrite the Windows boot loader in sda. You want grub installed to the sdb drive and then with your one time boot key choose that when you want it.

But you have to use the Something Else install option, create & choose partitions. I usually create partitions with gparted first as it seems a bit easier. Gparted is on live installer. But you still use Something Else to choose format ext4 and / (root), you also need swap but if partitioned in advance it will auto find it. With Something Else you have the option to create /home as another partition and/or you can leave space for another NTFS partition so you can share data between systems. Best not to mount Windows 7 system partition as read/write, read only or just not use it.

       Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

---

### Post by ben179 on 2015-10-14
Just so I understand, when you're saying to not use the auto install, you men to use the Something Else option?  Also, I need to install the bootloader for Ubuntu on the second drive?  If I'm following the logic here, the boot order looks at the first drive (Windows) and only sees Windows and thus loads it.  Correct?

---

### Post by yancek on 2015-10-14
I believe your assessment is right on the mark.  If you use anything other than the manual (Something Else) option it is basically an auto-install.  You don't have any control and you will not be able to make selections.  On the installation type window you will see all drives and all partitions on them.  Well you should, if you don't definitely stop.  There is also a selection option below that window "Device for Bootloader installation".   If you have two drives, that will probably be /dev/sdb.  You can use fdisk or gparted on the installation medium to check the drives as they will show by size.  If this is done correctly and you leave the BIOS settings it should boot windows and when you want to boot Ubuntu, go in the BIOS and change the boot priority to the second drive.  The link below is an excellent tutorial on installing Ubuntu.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

