---
title: "i changed a 100 mb partition (may have been made by windows) to swap space"
date: 2013-09-23
forum: Installation &amp; Upgrades
---

### Post by uday-j-nakade on 2013-09-23
hello
while installing ubuntu 13.04 on my dell inspiron 15 laptop, i changed a 100 mb partition which was already there (maybe created by windows7) to linux swap. now i cannot dual boot windows7. are these in anyway related? i desperately need windows for autodesk inventor professional that cannot be run by wine. i changed the flag of my c drive to boot from gparted but it did not help. i also tried boot repair without effect. how do i boot from my c drive or dual boot ubuntu and windows? or is my laptop incapable of dual boot. it has 2 gb ram 1.5 GHz intel core i3 processor.
Thanks in advance.

---

### Post by mastablasta on 2013-09-23
why did you do that? 100MB is too small for swap anyway.
it was probably the windows boot partition and someone in windows forums might be of more use.

---

### Post by santosh83 on 2013-09-23
Never heard of Windows using a dedicated boot partition at least on legacy BIOS systems. I've no experience with UEFI systems. Now you've learnt never to delete/reassign partitions without knowing exactly what they are for, and what's on them. In any case the Windows repair CD should've been able to restore your MBR, and I'm surprised that it didn't.

Just an idea: Linux can easily read NTFS and FAT (the Windows filesystem types), so if you've only a small amount of data, can you consider mounting your Windows C drive under Linux, copying off all the data you need to a CD/DVD or USB flash device and simply reinstalling Windows from scratch? This seems the simplest solution at present for you.

Also if you install and fire-up gparted under Linux you can get a graphical listing of all the partitions on all your disks. If you can post the detailed listing of your partitions and their types maybe someone with better knowledge (oldfred?) can help you to recover from this? The parition type (MBR or GPT) is also important and this will be displayed by gparted too.

---

### Post by uday-j-nakade on 2013-09-23
thank you very much. re-installing windows really seems to be the best option. but, gparted is not showing[ATTACH=CONFIG]246454[/ATTACH] the partition type.

---

### Post by oldfred on 2013-09-23
If you have a fair amount of RAM you may not have overwritten the Windows boot partition. Windows 7 usually installs with a separate 100MB (hidden) boot partition that has two essential boot files and the repair console. It primarily is for encrypting main install as boot files cannot be encrypted.

You can try testdisk and see if you can restore NTFS partition you need to unmount or swap off swap or use a liveCD that does not use swap. Do not use Ubuntu liveCD as it uses swap to speed things up as CD or flash is slow and that will overwrite your Windows data for sure. Parted Magic or gparted are liveCD that will not auto use swap.

       [URL="http://www.cgsecurity.org/wiki/TestDisk"]http://www.cgsecurity.org/wiki/TestDisk
[/URL]
 [URL="https://help.ubuntu.com/community/DataRecovery#Lost_Partition"]https://help.ubuntu.com/community/DataRecovery#Lost_Partition
      [/URL]
 Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

You could just try unmounting it and in Disk or Disk Utility change to type 07  or NTFS. You must remove entry from fstab so when booting it is not trying to use swap partition.

      
 Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
[COLOR=#ff0000]/bootmgr /Boot/BCD[/COLOR] /Windows/System32/winload.exe 

If you have your Windows repairCD or flash drive you can put boot flag on main Windows partition and repair it. It will add bootmgr & new BCD to main install and you do not have to have separate Boot partition.

    


    [URL="https://help.ubuntu.com/community/DataRecovery#Lost_Partition"]

[/URL]

[URL="http://www.cgsecurity.org/wiki/TestDisk"]
[/URL]

---

### Post by santosh83 on 2013-09-23
> **uday-j-nakade said:**
> thank you very much. re-installing windows really seems to be the best option. but, gparted is not showing[ATTACH=CONFIG]246454[/ATTACH] the partition type.

Hmm it seems you've created four primary partitions which means you cannot create any more partitions. That's how the MBR partition format works. People who need more than four partitions normally will create the fourth partition (after 3 primary partitions have been created) as an "extended partition" which is sort of like a container partition. Inside the extended partition you can create upto (if I'm not mistaken) 64 more so-called "logical" partitions.

You've a weird partitioning scheme there, wasting some space between sda2 and sda3 and again at the end of the disk, and because you've created all four as primary partitions, you can't utilise those empty spaces until you delete one primary partition, create and extended partition in it's place and create logical partitions within the extended partition.

Coming to your problem, the 100Mb partiton (sda1) is of type Linux Swap and if you've booted up into Linux (as you've obviously done) then mostly like all previous (Windows) data on that partition is long gone and not recoverable now.

What does the GRUB boot menu say when your system is starting up after the BIOS screen? Is there an entry for booting into Windows.The default Ubuntu behaviour during installations already containing a Windows system is to setup GRUB to boot into Windows as a menu option. Is there such a menu option in your GRUB boot screen? Did you select it and see if you can boot into Windows?

---

### Post by mastablasta on 2013-09-24
i think the windows boot partition should be fat32 file type. then you can try to repair it with the two mentioned files.

---

### Post by uday-j-nakade on 2013-09-24
no, there is no entry for windows in the grub menu. and the very fact that i was not able to create a new partition tempted me to use the existing partition as swap. (i did not know of extended partitions). and now i am stumped!

---

### Post by oldfred on 2013-09-24
The Windows 100MB partition is NTFS in BIOS mode and needs the boot flag. Testdisk will show you what it was.

With UEFI it is FAT32, but is not just a Windows boot partition but a UEFI boot partition for every install.

---

### Post by uday-j-nakade on 2013-09-26
Thank you very much oldfred. my problem is solved :D.

---

### Post by uday-j-nakade on 2013-09-26
and thank you all others too :D

---

