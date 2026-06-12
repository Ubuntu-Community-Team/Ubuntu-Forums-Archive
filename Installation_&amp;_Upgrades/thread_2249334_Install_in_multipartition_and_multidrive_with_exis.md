---
title: "Install in multipartition and multidrive with existing Win8.1 EFI"
date: 2014-10-21
forum: Installation &amp; Upgrades
---

### Post by andrea-g90 on 2014-10-21
Hello there,
I've followed a lot of guides to correctly install ubuntu with this particular configuration, but I've never managed to boot it.
My system came with win8.1 preinstalled over 1TB Hdd and used a 24 GB SSD with Intel RST to accelerate Windows. 
Seeing as I always use Ubuntu I decided to remove the acceleration and install ubuntu over the ssd in order to have better system performances.
- removed the acceleration from Windows
- disabled and deleted the raid partition from Bios
- shrink Windows partition from Windows to make space for /home swap /var and /tmp (the last two were a suggestion from another post in order to last long SSD life. Is this true??)
- have a reboot in Windows to filesystem adjustement
- disabled from Bios FastBoot and SecureBoot, leaving Uefi enabled
- booted a Ubuntu 14.04 usb in efi mode (checked /sys/firmware/efi/ folder)
- installed the system with the following configuration:
[LIST]
[*]sda2 /boot/efi 
[*]sda5 /var 
[*]sda6 /tmp 
[*]sda7 swap 
[*]sda8 /home 
[*]sdb2 / 
[/LIST]
I tried to install grub both in "/dev/sda" and "/dev/sda2" according to Uefi Linux guide and the result is always a fail in executing grub-update command:
"grub-install: error: cannot open 'boot/efi/EFI/ubuntu/shimx64.efi' no such file or directory"

this is my last BootInfo created with Boot-repair: [http://paste.ubuntu.com/8615754/](http://paste.ubuntu.com/8615754/)

I've also tried to create a bios_grub partition and a /boot partition, and that was the only one occasion when I menaged to get through the installation, but grub never appeared. Boot-repair didn't help me, saying that i needed to enable Efi-x64 repository or something like that. However I read that the bios_grub partition is not needed if installing in efi mode, so my actual configuration is the one descripted above.

What am I doing wrong? I thought to be an experienced Linux user, but all this s**t is making me crazy.... Any help would be appreciated, thanks!!!

---

### Post by Bucky Ball on 2014-10-21
Welcome. Looks like your EFI partition is on sdd1, sdd being a seperate physical device. Not sure it should be there. What is sdd?

Also, you don't need to create an EFI partition (sda2 /boot/efi in your setup description). If you're booting Win in EFI, you already have one and the Ubuntu install will see it and use that when installing. Creating another may be where the confusion is happeining. Can you still boot Windows?

---

### Post by andrea-g90 on 2014-10-21
sdd is just the live usb where i booted ubuntu so it is normal that there is an efi there. My actual efi is in /dev/sda2 and it is still working because i can boot in windows

---

### Post by Bucky Ball on 2014-10-21
Tried with the USB out? If sda2 is your EFI partition it should have an entry similar to sdd in your bootinfoscript output.

---

### Post by oldfred on 2014-10-21
I do not recommend separate partitions for most desktops. And now SSD have lives comparable to hard drive which is still not forever.
       SSD life test: 2014
[http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte](http://techreport.com/review/26523/the-ssd-endurance-experiment-casualties-on-the-way-to-a-petabyte)
[http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb](http://techreport.com/review/27062/the-ssd-endurance-experiment-only-two-remain-after-1-5pb)
    
I do make sure trim is working, since I make a small / partition I do use ext4 but turn journaling off. Some now say that is not even necessary. And I do set noatime in fstab. But one or two apps may need that left on like mutt.

I have an SSD with 25GB / (root)  and that includes /home. But all my data is on my hard drive in data partitions. When I still booted XP I had a shared NTFS and ext4 data partitions.

I also suggest each drive be bootable without any other drive, even if data partitions may give mount issues when other drive has failed. But at least both drives should not fail at same time unless you have lightning strike.

So I also have an efi partition on my SSD. 
If you install Ubuntu in BIOS boot mode, you will not be able to boot Windows from grub menu, only from UEFI menu. UEFI & BIOS are not compatible so once you start booting in one mode you cannot switch without rebooting. 

If you have lots of RAM, I have seen mounting some tmp into RAM. I do write DVD as a backup periodically and that would use 4GB of tmp, so I do not put tmp into RAM. Although that may just then use swap anyway and everything else might be faster. Have not tried or tested that.

What brand/model system? 
Some modify UEFI to only boot the UEFI entry with Windows in it. There are multiple work arounds for that issue.

I added a daily trim cron job. Some brands of SSD Ubuntu 14.04 may automatically create a weekly trim task.
 Shows both discard & fstrim methods for trim
[http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html](http://www.webupd8.org/2013/01/enable-trim-on-ssd-solid-state-drives.html)

A couple of users who used SSD for Ubuntu on Ultrabook. Intel is similar across all brands.
      
  lenovo u310  - install Ubuntu to part of SSD Post #19 
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

            Installing Ubuntu 12.10 alongside Windows 8 on Asus K95V laptop HD/SSD (EFI) Two drives. Details in post #6
[URL="http://ubuntuforums.org/showthread.php?t=2116610"]http://ubuntuforums.org/showthread.php?t=2116610

[/URL]
  Intel Smart Response Technology
[URL="http://mjg59.dreamwidth.org/26022.html"]http://mjg59.dreamwidth.org/26022.html
      [/URL]
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

    [URL="http://mjg59.dreamwidth.org/26022.html"]
[/URL]

[URL="http://ubuntuforums.org/showthread.php?t=2116610"]
[/URL]

---

### Post by andrea-g90 on 2014-10-21
I just rebooted with sdd out, and the system works as it used to. Previous BootInfo had more info in the boot section of sda2, I don't know why they disappeared, but if you look at "Drive/Partition Info" of sda, it clearly says that sda2 is an ESP

> ============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                   1 1,953,525,167 1,953,525,167  ee GPT


GUID Partition Table detected.

Partition    Start Sector    End Sector  # of Sectors System
/dev/sda1           2,048       821,247       819,200 Windows Recovery Environment (Windows)
/dev/sda2         821,248     1,353,727       532,480 EFI System partition
/dev/sda3       1,353,728     1,615,871       262,144 Microsoft Reserved Partition (Windows)
/dev/sda4       1,615,872   967,915,519   966,299,648 Data partition (Windows/Linux)
/dev/sda5     967,915,520   971,915,263     3,999,744 Data partition (Linux)
/dev/sda6     971,915,264   987,916,287    16,001,024 Data partition (Linux)
/dev/sda7     987,916,288 1,003,917,311    16,001,024 Swap partition (Linux)
/dev/sda8   1,003,917,312 1,319,397,375   315,480,064 Data partition (Linux)
/dev/sda12  1,907,007,488 1,953,509,375    46,501,888 Data partition (Windows/Linux)

This is the link to my previous configuration, if you want to compare them [http://paste.ubuntu.com/8591180/](http://paste.ubuntu.com/8591180/)

---

### Post by andrea-g90 on 2014-10-21
So your suggestion is to place /tmp and /var as usual in the root, to create an EFI partition in my SSD and to install grub in /dev/sdb, right?
 I'm not sure I can place the SSD prior the HDD in boot order anyway, so maybe I can't boot grub as well if bios still points to sda's EFI, right?

---

### Post by andrea-g90 on 2014-10-21
I've attempted to install the system two times, In both cases I shrinked my /(root) in the SSD to create /dev/sdb2 /boot/efi.

The first attempt grub target was /dev/sdb: I received the usual error message, as above.
The second time grub target was /dev/sdb2 (the EFI partition): I received this error:  "the 'grub-efi-amd64-signed' package failed to install into /target/. Without the grub boot loader, the installed system will not boot". And the installation crashed.
What is the right partition to place grub?

---

### Post by oldfred on 2014-10-21
If you have created a FAT32 partition with the boot flag so it is the efi partition, you should just specify sdb as the drive. With UEFI it knows to only install grub to efi partition. If partition is not correctly seen as an efi partition then it will give those type of errors.

---

### Post by andrea-g90 on 2014-10-21
From gpated I shrinked / to create a fat32 partition (/dev/sdb2) and re-labelled it to boot.
When the installer asked to select the partition where to install the system, /dev/deb2 was already selected as efi, so I just set /, /home and the others and put /dev/sdb as grub target. As usual I got: "unable to install grub in /dev/sdb executing 'grub-install /dev/sdb' failed".
/dev/sdb2 is empty
/etc/fstab clearly says that designed efi partition is /dev/sda2, infact /target/boot/efi/ contains sda2 content. 
Why is it that the new efi is not considered at all?

Maybe this can be helpfull: found a thread in one of @oldfred's guide [http://ubuntuforums.org/showthread.php?t=2185869](http://ubuntuforums.org/showthread.php?t=2185869) that can be very similar to mine, seeing as I have an HP Envy j100.
the difference is that he menaged to install ubuntu and the efi file, for then replace the /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi file with the one my installer should create in my new partition.

---

### Post by oldfred on 2014-10-21
Your pastebin above only shows sdb2 an ext4 partition for / (root) not an FAT32 efi partition. Did you create that after the update to the summary report?

You can have grub in the sda efi partition or both places. I just prefer to keep boot loaders on same drive as install. And efi files have no install issues. You can just copy the files in /efi/ubuntu into a new /efi/ubuntu folder in the other drive.

And HP will not boot Ubuntu. They have modified UEFI against UEFI standard to only boot an UEFI entry with Windows in the name. Many work arounds. Most rename bootx64.efi and make grubx64.efi be bootx64.efi. And then in UEFI menu boot hard drive. UEFI should see all installed drives and any efi partitions. But only one efi partition per hard drive.

Boot-Repair always renamed the Windows efi file bootmfgw.efi and made it grub. But that leads to later issues when Windows updates. Better just to rename bootx64.efi.

---

