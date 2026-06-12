---
title: "Cannot boot Windows 8 after unsuccessful install"
date: 2012-12-04
forum: Installation &amp; Upgrades
---

### Post by furmada on 2012-12-04
Hello all,

I purchased an Acer Aspire ME600 desktop computer. It  came with Windows 8 preinstalled. I tried to install Ubuntu 12.10 on it.  Here are my steps:
1. Download Ubuntu 12.10 64-bit
2. Burn .iso file to USB
3. Put the USB in the Aspire, and boot from it
4. Select "Install Ubuntu"
5. Resize Windows partition
6. Make two partitions in freed space: (1) ext4 /, (2) swap
7. Complete install, and reboot.

I got Windows. No GRUB, or anything. From my LiveUSB, I tried "Boot-Repair" several times. The Ubuntu Pastebin numbers are:

paste.ubuntu.com/1409298
paste.ubuntu.com/1409405
paste.ubuntu.com/1409420
paste.ubuntu.com/1409428

All  this did was break the Windows boot. Still no Ubuntu. Now, when I boot  my PC, I get a message saying "Your PC needs to be repaired", and says  there is an error in \EFI\Microsoft\Boot\BCD. The error number is 0xc000000f. My PC did not come with any  installation or recovery disks.

I would like to get Windows working again.

Do you have any idea how?
Thank You, 
furmada

---

### Post by oldfred on 2012-12-05
Click-able pastebin

[http://paste.ubuntu.com/1409428/](http://paste.ubuntu.com/1409428/)

I do not see Linux partition and you have two efi partitions. You can only have one efi partitions. Use gparted to remove boot flag from sda4. Two efi partitions totally confuses everything.

Different model:
       Acer V5-571P-6815 secure boot off worked
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

    
You do need to turn fast boot or quick boot off. Also best to turn off secure boot. You do have to boot Ubuntu in UEFI mode to get it to install in efi mode.

---

### Post by furmada on 2012-12-05
I tried deleting the Linux partition to get Windows back to working. The sdb1 efi partition is my Ubuntu LiveUSB. I have secure boot off.

---

### Post by oldfred on 2012-12-05
LInux partition would not make any difference to Windows booting. Windows does not know it exists.
But two efi partitions definitely confused system. It has to know which partition to find boot files. And it looks like the Windows boot files are still in the 'real' efi partition. 
The only other issue may be how did you resize Windows? Always best to use Windows to shrink Windows and immediately reboot as it wants to run chkdsk or other repairs on the NTFS partition. So chkdsk may also be required if still having boot issues with Windows.

---

### Post by jdmgwaka89 on 2012-12-05
I had this problem after I tried to install Debian one time. You should go back through the installation and make sure you install the boot loader so you can freely switch between operating systems.

---

### Post by YannBuntu on 2012-12-06
Hello

> **furmada said:**
> Now, when I boot  my PC, I get a message saying "Your PC needs to be repaired", and says  there is an error in \EFI\Microsoft\Boot\BCD. The error number is 0xc000000f. My PC did not come with any  installation or recovery disks.

1) backup your documents if not done yet
2) get a Windows disc and use it this way: [https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader) , until you get direct access to Windows
3) then use Boot-Repair to recover your GRUB menu

---

