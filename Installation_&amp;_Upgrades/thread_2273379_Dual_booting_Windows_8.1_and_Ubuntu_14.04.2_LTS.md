---
title: "Dual booting Windows 8.1 and Ubuntu 14.04.2 LTS"
date: 2015-04-12
forum: Installation &amp; Upgrades
---

### Post by Lucas_Zhou on 2015-04-12
Hello,

Recently I've been having trouble with dual booting both Windows 8.1 and Ubuntu 14.04.2 LTS on my Dell Vostro 220s.

My specs are as follows:

CPU: Intel Pentium E5400 Dual Core at 2.7 GHz (64-bit)
RAM: 3 GB
Storages: One 160 GB Hitachi HDD, One 320 GB HDD

The computer did not come with Windows 8, so it does not have UEFI.

I installed Windows first on the 160 GB HDD, then attempted to install Ubuntu on the 320 GB HDD using this method, only with newer OSs: [http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)

I made sure the bootloader was on the corresponding 320 GB HDD.

When rebooted to that HDD, GRUB gave me Windows 8, and Ubuntu to load, but as soon as I went into Windows 8.1 to check if it survived, Windows 8.1 showed a blue screen that said my PC needs to be repaired and showed this error code: 0xc000000e 

I tried to restart and this time it showed the same error code along with saying that winload.exe is not found or corrupt. Ubuntu boots fine, but Windows 8.1 is dead, no matter what I do by repairing the installation.

I am stuck at this point and don't know how to go on. Any help would be greatly appreciated. 

Thanks, LZ

---

### Post by ricky-flammia on 2015-04-12
To fix your Windows problem you should proceed to install GParted from the Ubuntu Software Center, delete your Windows 8.1 partition and reallocate the newly unused HDD space to Ubuntu. Problem solved. :cool:

---

### Post by oldfred on 2015-04-12
Even though you have BIOS boot, you still have to turn off the fast startup or always on hibernation in Windows 8. 
Grub only boots working Windows or Windows that is not hibernated nor needs chkdsk.
If Windows boot loader is still on Windows drive, use one time boot key often f10 or f12 or change BIOS to boot that drive to fix Windows.

Use you Windows repairCD or flash drive to fix Windows, if you cannot boot from BIOS or one time boot key.
You may be able to reinstall a Windows boot loader to MBR with Boot-Repair, fix Windows, and then restore grub to MBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System


[/URL]

---

