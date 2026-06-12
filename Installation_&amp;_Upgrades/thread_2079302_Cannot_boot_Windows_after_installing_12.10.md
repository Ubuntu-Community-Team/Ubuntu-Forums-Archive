---
title: "Cannot boot Windows after installing 12.10"
date: 2012-11-01
forum: Installation &amp; Upgrades
---

### Post by cazzerly on 2012-11-01
I decided to install Ubuntu 12.10 on my PC, which already had windows 7 on it. The steps that I took were:
1: skrink my HDD (which is not where I boot windows, I boot windows from my SSD), and leave it as unallocated space.
2. During installation of Ubuntu, press "Something Else" in installation type and then partition this unallocated space: 3 partitions with mount points "/", "swap area" and "/home".
3. I chose to install the bootloader on the partition which had the mount point "/".

HOWEVER, after the installation I cannot boot into Windows at all. After running boot repair it looks like the bootfile is in my Windows SSD drive...is there anything I can do to fix this?

Here is the paste from boot-repair:
[http://paste.ubuntu.com/1324785/](http://paste.ubuntu.com/1324785/)

Note: ENTIRE sda drive should be for Windows, whilst ubuntu partitions should be sda2-sda6.

Thanks heaps for any help at all!

---

### Post by Rubi1200 on 2012-11-02
Hi and welcome to the forums :-)

Asking others to jump in and help you out here.

Good luck.

---

### Post by oldfred on 2012-11-02
It looks like you have a UEFI system, but UEFI system can have either BIOS mode or UEFI mode installs. And both Windows & Ubuntu should be installed in the same mode or else you will have conflicts/issues.

Also Windows only boots from gpt(GUID) partitioned drives with UEFI. Ubuntu will work from either BIOS/UEFI and gpt or BIOS with MBR(msdos) partitioning.

Your 120GB sda drive is gpt partitioned with the first partition as efi and Windows main install in sda3.

Your sdb 1TB drive is MBR, but has a BIOS Windows boot loader in the MBR? And if you convert to gpt be sure to backup everything. I would delete Linux partitions, backup your NTFS data and see if gdisk will convert to gpt without data loss, but never attempted it.

Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)


From your UEFI menu can you boot Windows ok from the efi partition in sda?

It looks like Boot-Repair saw your UEFI system and Windows in UEFI, so it tried to convert Ubuntu to UEFI boot. Which normally works, but with Ubuntu in MBR, I do not know it that will work or not. Probably best to reinstall Ubuntu to sdb.

With both Windows & Ubuntu & UEFI you should get two boot choices when installing 64 bit versions. One is UEFI/efi and the other BIOS/AHCI or whatever mode BIOS is called. How you boot install disk is how it will install.

---

### Post by cazzerly on 2012-11-02
The thing is that I read up on installing ubuntu in UEFI before I actually installed and so I made a live usb and then made 100% sure that  I booted it in UEFI mode (something that could be specified in my Bios (pretty sure what I call my BIOS is actually the UEFI menu)). 
In the UEFI menu I have also made sure that Windows bootmgr is first in the boot order but I cannot boot into windows at all. All it says is "Windows is loading files" or something like that and asks if I want to do a system repair or boot windows normally. System repair will take me nowhere just back to that screen and "boot windows normally" will just take me to ubuntu...

But do you recommend that I convert the MBR to GPT? Do you think that might enable me to boot into Windows?

BTW, thanks so much for your time guys!

---

### Post by oldfred on 2012-11-02
I think the issue started with the 1TB drive being MBR before your install. I thought Ubuntu would install in efi mode, but maybe it tried to even with drive in MBR.

How much data is in your NTFS partition. I assume since the Ubuntu install is new there is nothing really to save there? If you have a good backup I would convert to gpt as that is more standard with UEFI. 

Some examples that made UEFI work with two drives:

UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)

Update - BootInfo shows use.
> 
/dev/sda3      fuseblk   112G  105G  6.9G  94% /mnt/boot-sav/sda3
 /dev/sdb1      fuseblk   541G  380G  162G  71% /mnt/boot-sav/sdb1
You have a lot of data, so it has to be your call on how good your backups are.

Plus your sda3 looks full. Windows really likes 30% free, starts to slow at 20% free.

---

### Post by cazzerly on 2012-11-06
Thanks for the help mate, really appreciate it :) It all worked out in the end...
Not the way I first wanted it to, but in the end I reformatted both partitions, removed all data, and changed tha partitioninhg table to gpt. I missed out on a bung of save games on windows but yeah, who cares :P
Im planning later on to get another SSD and install windows on that one; I might actually remove my current ssd when I do so though, just so I dont mess everything up again..

---

