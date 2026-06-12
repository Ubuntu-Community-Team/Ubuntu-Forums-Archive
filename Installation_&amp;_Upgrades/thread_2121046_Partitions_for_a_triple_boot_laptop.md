---
title: "Partitions for a triple boot laptop"
date: 2013-02-28
forum: Installation &amp; Upgrades
---

### Post by ads2996 on 2013-02-28
Hi,

I am considering upgrading my laptop hdd to 1tb and creating a triple boot system of Windows 7, Windows 8 and Linux (either Ubuntu or BackTrack). So my question is how to organize the partitions on my drive. 

1TB

     100GB (extended)
             Windows 7(C)
             System (System)

     100GB (Extended)
             Windows 8(C)
System (System)

     60GB (extended)
             Swap (8GB-Swap)
             Root (56GB-Ext3)

    740Gb (Data-NTFS)

I would be grateful for any help in this matter.

---

### Post by ads2996 on 2013-03-02
Does anyone have any ideas? Please

---

### Post by oldfred on 2013-03-02
Windows only boots from primary partitions. You could just have the 100MB hidden as a primary, but Windows also installs without the 100MB boot partition if you create the main install NTFS with the boot flag first. The main reason for the separate /boot was so you could encrypt the main install. Also you may be able to boot the repair console. But you should have a repairCD or flash drive just in case of issues anyway.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

---

### Post by darkod on 2013-03-02
Why using extended (logical) from the start when you can use primary partitions until you have 3 of them. Only then start creating them as logical.

Partition #1, primary, 100GB for win7
Partition #2, primary, 100GB for win8
Partition #3, primary, 740GB for data
Logical 56GB for root
Logical 8GB for swap

If you want both win7 and win8 to be in the grub2 boot menu separately, you have to be careful before installing, otherwise windows combines the boot files and it's not easy to separate them later. Better to do it properly first time.

Install win7 as normal, but prepare the 100GB ntfs partition first. This way it will not create the small 100MB system reserved partition. The installer does that if you make the partition with it. If the partition already exists, it will not create the small one even if you format the previously prepared partition during the install. So, after the win7 install is done, you should have only one single 100GB primary partition on the disk. Make sure you check in Disk Management or from ubuntu live mode that this is true.

After that is done, create another ntfs partition of 100GB, use Gparted from ubuntu live mode and turn off the boot flag on the win7 partition. Turn on the boot flag on the new 100GB partition. Only after that start the win8 installer. That way it will keep the boot files separate putting them on the same partition as win8.

After that is done, create the data partition and then install ubuntu. That's it.

---

### Post by ads2996 on 2013-03-02
So it is possible to install windows without the 100mb system partations.

Then have only the two windows partitions as primary and the rest logical, where is GRUB 2 stored? and would that partition have to be set as the boot partition.

---

### Post by oldfred on 2013-03-02
You install grub to MBR to use as the main boot loader. Leave boot flag on which ever Windows you prefer. Grub does not use boot flag at all, Windows has to have boot flag to know which partition to boot, to repair or to install into. A few BIOS have to see a boot flag on a primary partition (assumes Windows?), so leave a boot flag on a Windows primary partition.

A Windows boot loader in the MBR, just looks for which partition has boot flag and jumps to that partitions PBR or partition boot sector. Grub just chain loads to the PBR to boot Windows.

---

### Post by ads2996 on 2013-03-02
Sorry for all the questions but i am new to all this. Is MBR the boot loader installed by windows? If so, if i were to install bit windows 7 and 8 i would end up with two copies of the windows boot loader. Then GRUB is installed on the Linux partition. Then GRUB boots the specified windows boot loader.

---

### Post by darkod on 2013-03-02
No, the MBR is Master Boot Record which is actually the name for the first cylinder on the HDD. It's where any bootloader usually goes because the boot process starts there.

So, even after installing two versions of windows you still have only one windows bootloader because the second one is installed over the first one. Then later grub2 is installed over them, making it main bootloader on the MBR.

If using the auto methods to install ubuntu, it installs the bootloader to the MBR automatically.
If using the manual method, in the drop down box asking you where to install it, select /dev/sda for the first disk, or another letter like /dev/sdb, /dev/sdc, etc, depending how many disks you have and where do you want the bootloader. When you use the disk name like /dev/sda as bootloader destination, that means the MBR of that disk. When it has a number in it, like /dev/sda1, /dev/sda5, it means the partition number 1 or 5 on that disk.

So, grub2 goes to the MBR, which in a single disk system means /dev/sda. Without any number in it.

Make sure you do the boot flag thing correctly before installing the second windows.

---

### Post by ads2996 on 2013-03-02
That makes more sense to me now, All i have to do now is get the money for my new hdd which will be a challenge. If i do get the money i will let you know how it goes.

---

