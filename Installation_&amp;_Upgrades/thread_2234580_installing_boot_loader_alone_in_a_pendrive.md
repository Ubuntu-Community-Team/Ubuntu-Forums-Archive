---
title: "installing boot loader alone in a pendrive"
date: 2014-07-15
forum: Installation &amp; Upgrades
---

### Post by ashiqsultan on 2014-07-15
I want to install ubuntu 14.04 desktop in a PC in which there is two hard drives 1TB and other is 80GB
Windows 7 is Installed in the 1TB HD so i am not going to touch it and install ubuntu in the 80Gb HD
[I][B]My Question is 
[/B][/I]could I install ubuntu in that &#8203;80GB HD and install the boot loader *alone* in a pendrive so that the system will automatically boot to windows *when that pendrive isnot connected* 
Is doing like this will cause any boot loader problems ?????

---

### Post by yancek on 2014-07-15
> could I install ubuntu in that &#8203;80GB HD and install the boot loader *alone* in a pendrive so that the system will automatically boot to windows *when that pendrive isnot connected* 

Yes.  Are you using a standard mbr boot for windows or do you use uefi?  If mbr boot, it would be simpler to install Grub to the master boot record of the 80GB drive.  You could then select to boot Ubuntu drive from the BIOS.  More details if you post more details from the Ubuntu installation medium:  sudo fdisk -l(Lower Case Letter L in the command).

---

### Post by oldfred on 2014-07-16
Install to external drive. Also any second drive. Or any install with Something Else
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

The device for boot loader can be any drive, just do not choose sda, or whichever drive the Windows install is on.
Also agree with yancek it would just be easier to install grub to the MBR of the 80GB drive and use BIOS or one time boot key often f12 to choose which hard drive to boot from.
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

---

