---
title: "How to disable EFI boot mode on Phoenix securecore tiano - ubuntu 12.04.2"
date: 2013-06-26
forum: Installation &amp; Upgrades
---

### Post by keyshawn on 2013-06-26
After installing ubuntu 12.04.2, 64bit to my acer aspire 5560-7414 laptop, on a single 500gb hard drive. 


After  installation, and manually setting my hard drive  partitions in the  ubuntu installer as / 20gb, /var 20gb, /swap 8gb, and  remaining /home  (all under ext4 except the swap), I successfully  completed the  installation and it asked me to reboot. 

I did and even before grub appeared, I received the error: 

**             Error file not found, error you need to load the kernel first         **

I did some googling, found a suggestion to sudo update-grub did that received the error:  

/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

so I googled that error and did boot-repair which recreated this log

[http://paste.ubuntu.com/5802488/](http://paste.ubuntu.com/5802488/)


While running boot-repair, I received a message that 

running boot-repair, "the boot of your pc is in EFI mode but  there's no EFI partition detected. and retry after creating a EFI  partition , FAT32, 100MB-250MB, start of disk, boot flag."

More googling, I tried to remove the UEFI mode 
 I  have not found  legacy mode or any other mode that would disable the  UEFI in the boot screen (that I obtain by hitting f2) to my bios (or  UEFI ) - Phoenix SecureCore Tiano, v1.15


I have found the  UEFI Installing Tips [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) , a  nice synopsis of some of problems that users have experienced and  possible solutions but no clear solution of next steps. 


Should I continue to try to disable UEFI (if so, how) or install a EFI partition ? What are my other next steps /

---

### Post by oldfred on 2013-06-26
You must have booted Boot-Repair in UEFI mode or turned it on in BIOS. Some UEFI/BIOS have switches that make sense like UEFI on, CSM/BIOS on/off. Others may just have an auto mode or UEFI on/off where off then means BIOS on. Or BIOS on means UEFI off.

But your install is on a MBR(msdos) partitioned drive so you have to boot with BIOS. UEFI requires gpt partitioned drives. Windows only boots with UEFI from gpt drives, but Ubuntu can use gpt partitioning for either BIOS or UEFI.

Since your install is BIOS/MBR, you should make sure UEFI/BIOS is set to BIOS mode. And if booting repair disks to boot them in BIOS mode. Boot-Repair will convert a BIOS install to UEFI, but you have to have gpt partitioning, so you cannot easily convert.

If you boot Boot-Repair in BIOS mode it should help you reinstall grub to the MBR.

---

### Post by keyshawn on 2013-06-27
> **oldfred said:**
> You must have booted Boot-Repair in UEFI mode or turned it on in BIOS. Some UEFI/BIOS have switches that make sense like UEFI on, CSM/BIOS on/off. Others may just have an auto mode or UEFI on/off where off then means BIOS on. Or BIOS on means UEFI off.

But your install is on a MBR(msdos) partitioned drive so you have to boot with BIOS. UEFI requires gpt partitioned drives. Windows only boots with UEFI from gpt drives, but Ubuntu can use gpt partitioning for either BIOS or UEFI.

Since your install is BIOS/MBR, you should make sure UEFI/BIOS is set to BIOS mode. And if booting repair disks to boot them in BIOS mode. Boot-Repair will convert a BIOS install to UEFI, but you have to have gpt partitioning, so you cannot easily convert.

If you boot Boot-Repair in BIOS mode it should help you reinstall grub to the MBR.


Thanks for your reply. As I understand you, I need to boot my ubuntu-live cd in BIOS mode and then launch Boot-repair and do the standard repair ? Unfortunately, as I explained above, I haven't figured out how to boot into the bios mode yet.

---

### Post by keyshawn on 2013-06-27
I resolved my issue - of not being able to boot into ubuntu 12.04.02 although was unable to figure out how to disable the EFI. 

After reading 
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace) [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) , I

I decided to try the following: made a 250mb partition at the beginning of my single hard drive by removing space from my previous boot-flagged / ext4 drive, formatted into FAT32 and added a boot flag, all in  gparted.

Then I did automatic repair in bootrepair, said my boot sucessfully repaired.

My new boot-repair log is at [http://paste.ubuntu.com/5804963/](http://paste.ubuntu.com/5804963/) 

I'm now able to boot into ubuntu although I never figured out how to disable the EFI boot mode.

---

### Post by oldfred on 2013-06-27
I am not sure how you are booting. You have grub in the MBR for BIOS boot and a FAT32 partition with efi files, but it cannot be flagged as an efi partition as that is only available with gpt partitioning not MBR(msdos). ??

---

