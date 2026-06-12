---
title: "Ubuntu + Windows 7 Help"
date: 2013-04-02
forum: Installation &amp; Upgrades
---

### Post by dillwillhill on 2013-04-02
I tried the windows installer onto my hard drive containing windows 7 but when i booted onto ubuntu, there was a countdown in the top left hand corner then it got stuck on 'Completing the Ubuntu instalation:
For more installation boot options, pres 'Esc' now...
0' for about 5 minutes then the computer turned off. I tried a different method by formatting my second hard drive so it was completely empty, installed ubundu to that drive but when i booted it said 'bootmgr is missing press ctrl+alt+del to restart' unfortunetely when i held the buttone nothing happened. any support is thanked. id prefer to have the two OS on seperate drives. thanks in advance. p.s. I used the most recent ubuntu

---

### Post by oldfred on 2013-04-02
Not sure where you are at. The Windows installer just installs inside the existing Windows NTFS partition. A full partitioned install is not a Windows install.
With two drives you need to use Something Else or manual install to get the option on the partitioning screen on where to install the grub2 boot loader. You want the boot loader on the Ubuntu drive. All the auto install options will install to sda which usually is the Windows drive. You may be able to set BIOS to boot the second drive first, so then the installer sees that as sda? 

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

      
 Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)


 Install options, Do not use erase entire drive unless that is really what you want.
[http://www.ubuntu.com/download/help/install-desktop-long-term-support](http://www.ubuntu.com/download/help/install-desktop-long-term-support)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
Install Ubuntu 12.10 0 with screenshots
[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)
[http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/](http://howtoubuntu.org/how-to-install-ubuntu-12-04-precise-pangolin/)

---

