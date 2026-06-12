---
title: "Grub not showing windows 10 after trying boot-repair and reinstall grub manually"
date: 2016-11-01
forum: Installation &amp; Upgrades
---

### Post by rizkhy45 on 2016-11-01
I've been struggling to fix my GRUB. I've tried to use boot-repair's recommended recover and manual reinstall grub manually. Sometimes both shows no error but sometime does. After restarting my laptop, there are only 2 things that I occur. 1) System automatically load ubuntu. 2)System shows GRUB prompt in a black background.

here is my boot info generated from boot-repair
[http://paste2.org/4M9vcj8F](http://paste2.org/4M9vcj8F)


And if this is relevant, when I run "fdisk -l", it shows Partition 2 does not start on physical sector boundary.

Hope you guys can help, me.

---

### Post by oldfred on 2016-11-01
You have a newer UEFI hardware based system, but both Windows & Ubuntu installed in the 35 year old BIOS/MBR configuration.
You also then booted Boot-Repair in UEFI mode, you need to boot in BIOS mode all the time to avoid confusion.

Grub only boots working Windows.
And that also means Windows cannot be hibernated nor needing chkdsk.
And Windows will turn its fast start up on after updates, so you regularly have to turn it off.

Since the only way to boot Windows is now to restore a Windows boot loader to MBR, best to have a Windows repair/recovery flash drive.
       Windows 10 repair disk
[http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html](http://www.tenforums.com/tutorials/4200-recovery-drive-create-windows-10-a.html)
[http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html](http://www.tenforums.com/tutorials/36083-system-repair-disc-create-windows-10-a.html)
Repair/backup/restore
[https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive](https://support.microsoft.com/en-us/instantanswers/3a747883-b706-43a5-a286-9e98f886d490/create-a-recovery-drive)
[http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options](http://windows.microsoft.com/en-us/windows-10/windows-10-recovery-options)

Boot-Repair will restore a Windows type boot loader, if it sees Windows. It uses syslinux which is the same boot loader the BIOS version of Ubuntu installer uses.
You can from most Linux install the syslinux or Lilo boot loaders which work like a Windows boot loader. But you only want to install the part of the code that goes into MBR, not full boot loader.

       
 sudo apt-get install syslinux
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda 
or:

 sudo apt-get install lilo
sudo lilo -M /dev/sda mbr 
May show errors as full boot loader not installed, but that is what you want.

After you turn Windows fast start & hibernation off, reinstall grub to MBR either manually or with Boot-Repair.
      
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 
    
One advantage of UEFI, is both boot loaders are always on system, so if one does not work or you need to directly boot Windows you can use UEFI to directly boot that system.

Error message on partition 2 does not matter. Partition 2 is the extended partition which you do not write into, only the logical partitions inside it. So it is ok.

---

