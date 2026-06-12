---
title: "Install Win7 64bit after Xubuntu"
date: 2013-02-13
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2013-02-13
I wasn't sure if I should post this here or in the other OS section. Move if you desire.

I have a Xubuntu 12.04 install and I want to install Win7 64bit along side it because I recently got an Elgato Game Capture HD for capturing my Xbox 360 gameplay. I have a youtube channel. I wish the Elgato worked in Linux but there's no supporting drivers yet so I have to install Windows. I don't have enough RAM to do a VM so I have to dual boot.

What is the exact thing I need to do after I install Win7 64bit onto a separate harddrive in my computer? Do i just have to run super grub disk and have it reinstall grub? If someone could detail out the instructions it would greatly be appreciated.

Thanks

---

### Post by oldfred on 2013-02-13
Are you installing to another hard drive or another partition on same drive.

Windows has to be installed or really boot from a primary NTFS formatted partition with the boot flag. If you have unallocated space and available primary partitions then it will just install. 

If installing to another drive, make sure to set BIOS to default to that drive first. Otherwise Windows may try to install its boot loader and hidden boot partition onto which ever drive is set in BIOS as boot. I would keep Windows as first drive in drive order.

If separate drive best to disconnect Linux drive. Then change BIOS back to to Ubuntu drive with grub still in MBR and run this to find the Windows install.
sudo update-grub

If on same drive you will have to reinstall grub to the MBR and then run update.

       [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

