---
title: "windows 8 and Ubuntu on different hard drives install"
date: 2015-04-18
forum: Installation &amp; Upgrades
---

### Post by seventeen17dima on 2015-04-18
So, I still want to win8 to be my primary OS. I already tried installing Ubuntu, it works, but some details did not satisfy me. I want to have everything to be installed right and clear :)

I have 3 drives:
1 - 2TB with win8 on it
2 - 2TB, empty, for backups, large files and experiments (dont ask)
3 - 320GB, where i want to install Ubuntu.

On first HDD i have two partitions: 100MB "used by system" and all other space as true windows space.

I'm quite new to linux and stuff, but i already had some experience with terminal, also bios and partitioning. I have read similar questions, mostly all of them have some specific cases and problems.

Also my native lang is russian, so I'm sorry for some grammar mistakes.

---

### Post by oldfred on 2015-04-18
Is Windows booting in BIOS or UEFI mode. You want Ubuntu to be booting in the same boot mode.

And with mulitple drives, you need to use Something Else. That is the only option that in BIOS mode gives you the option to install grub to your 320GB drive, default is always sda, which probably is your Windows drive and you want to keep the Windows boot loader in that drive. But change BIOS to boot from the Ubuntu drive and grub will have a menu entry for Windows. You only need Windows boot loader in sda for emergencies.

If Windows 8, whether UEFI or BIOS you must turn off the fast startup or always on hibernation. Windows does not make that exactly easy.
 Fast Startup off
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

If you have only the 100MB Boot partition and Main c: "drive" then that is BIOS. If UEFI then you have an efi FAT32 partition and multiple other partitions that Windows normally has.

      
 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

