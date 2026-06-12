---
title: "Pre-Install Planning of Obsidian &amp; Platinum"
date: 2017-12-31
forum: Installation &amp; Upgrades
---

### Post by gemmathetechie on 2017-12-31
Hello there Ubuntu Forums!

The reason for me posting this thread is to question what I should do with the partitions marked as /dev/sdb3 & /dev/sdb7 as well as all of the sizing for all of the partitions for the entirety of /dev/sdb. Please note that the HDD in question is 500GB as well as does this partition laid out best for a multiboot system.  Also as well I am unsure as to what boot manager to use (Out of GRUB2, BURG or rEFInd)

Obsidian's specification.
```
Manufacturer - Lenovo
Model        - ThinkCentre
Base System  - [LiveUSB] Ubuntu Studio 16.04.3 LTS
Processor    - Intel® Core(TM) 2 Duo CPU E7500 @ 2.93GHz
Graphics     - GeForce 210
Memory       - 3.9 GiB
Disk         - 1TB
```
Obsidian (Master HDD) 500GB

[TABLE="class: outer_border, width: 750"]
[TR]
[TD][FONT=courier new]_**Location**_[/FONT][/TD]
[TD][FONT=courier new]_**Mount Point**_[/FONT][/TD]
[TD][FONT=courier new]_**Name**_[/FONT][/TD]
[TD][FONT=courier new]_**Label**_[/FONT][/TD]
[TD][FONT=courier new]**_File System_**[/FONT][/TD]
[TD][FONT=courier new]_**Size**_[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sda1[/FONT][/TD]
[TD][FONT=courier new]/boot/efi[/FONT][/TD]
[TD][FONT=courier new]BOOT[/FONT][/TD]
[TD][FONT=courier new]Boot Partition[/FONT][/TD]
[TD][FONT=courier new]FAT32/EFI[/FONT][/TD]
[TD][FONT=courier new]2G[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sda2[/FONT][/TD]
[TD][FONT=courier new]--[/FONT][/TD]
[TD][FONT=courier new]MSR[/FONT][/TD]
[TD][FONT=courier new]Microsoft Reserved[/FONT][/TD]
[TD][FONT=courier new]--[/FONT][/TD]
[TD][FONT=courier new]2G[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sda3[/FONT][/TD]
[TD][FONT=courier new]/win/drive_a[/FONT][/TD]
[TD][FONT=courier new]MEDIA[/FONT][/TD]
[TD][FONT=courier new]Ambience[/FONT][/TD]
[TD][FONT=courier new]NTFS[/FONT][/TD]
[TD][FONT=courier new]100G[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sda4[/FONT][/TD]
[TD][FONT=courier new]/win/drive_b[/FONT][/TD]
[TD][FONT=courier new]BACKUP[/FONT][/TD]
[TD][FONT=courier new]Backup Tower[/FONT][/TD]
[TD][FONT=courier new]NTFS[/FONT][/TD]
[TD][FONT=courier new]100G[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sda5[/FONT][/TD]
[TD][FONT=courier new]/win/drive_c[/FONT][/TD]
[TD][FONT=courier new]WIN10[/FONT][/TD]
[TD][FONT=courier new]Windows 10[/FONT][/TD]
[TD][FONT=courier new]NTFS[/FONT][/TD]
[TD][FONT=courier new]50G[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sda6[/FONT][/TD]
[TD][FONT=courier new]/win/drive_d[/FONT][/TD]
[TD][FONT=courier new]DUMP[/FONT][/TD]
[TD][FONT=courier new]Dumping Ground[/FONT][/TD]
[TD][FONT=courier new]NTFS[/FONT][/TD]
[TD][FONT=courier new]50G[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sda7[/FONT][/TD]
[TD][FONT=courier new]/android[/FONT][/TD]
[TD][FONT=courier new]ANDROID7[/FONT][/TD]
[TD][FONT=courier new]Android Nougat[/FONT][/TD]
[TD][FONT=courier new]ext4[/FONT][/TD]
[TD][FONT=courier new]66G[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sda8[/FONT][/TD]
[TD][FONT=courier new]/android/storage/PARTUUID[/FONT][/TD]
[TD][FONT=courier new]SDCARD[/FONT][/TD]
[TD][FONT=courier new]PART UUID[/FONT][/TD]
[TD][FONT=courier new]ExFAT[/FONT][/TD]
[TD][FONT=courier new]130G[/FONT][/TD]
[/TR]
[/TABLE]

Obsidian (Slave HDD) 500GB

[TABLE="class: outer_border, width: 750"]
[TR]
[TD][FONT=courier new]_**Location**_[/FONT][/TD]
[TD][FONT=courier new]_**Mount Point**_[/FONT][/TD]
[TD][FONT=courier new]_**Name**_[/FONT][/TD]
[TD][FONT=courier new]_**Label**_[/FONT][/TD]
[TD][FONT=courier new]**_File System_**[/FONT][/TD]
[TD][FONT=courier new]_**Size**_[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sdb1[/FONT][/TD]
[TD][FONT=courier new]/[/FONT][/TD]
[TD][FONT=courier new]STUDIOSYS[/FONT][/TD]
[TD][FONT=courier new]Studio 17.10[/FONT][/TD]
[TD][FONT=courier new]ext4[/FONT][/TD]
[TD][FONT=courier new][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sdb2[/FONT][/TD]
[TD][FONT=courier new]/home[/FONT][/TD]
[TD][FONT=courier new]STUDIOHOME[/FONT][/TD]
[TD][FONT=courier new]Studio Home[/FONT][/TD]
[TD][FONT=courier new]ext4[/FONT][/TD]
[TD][FONT=courier new][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sdb3[/FONT][/TD]
[TD][COLOR=#ff0000]**UNSURE**[/COLOR][/TD]
[TD][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/TD]
[TD][COLOR=#ff0000]**[FONT=courier new]UNSURE[/FONT]**[/COLOR][/TD]
[TD][FONT=courier new]**[COLOR=#FF0000]UNSURE[/COLOR]**[/FONT][/TD]
[TD][COLOR=#ff0000]**[FONT=courier new]UNSURE[/FONT]**[/COLOR][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sdb4[/FONT][/TD]
[TD][FONT=courier new][COLOR=#daa520]/dev/vram[/COLOR][/FONT][/TD]
[TD][FONT=courier new]SWAP[/FONT][/TD]
[TD][FONT=courier new]Studio Swap[/FONT][/TD]
[TD][FONT=courier new]Linux Swap[/FONT][/TD]
[TD][FONT=courier new]10GB[/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sdb5[/FONT][/TD]
[TD][FONT=courier new]/[/FONT][/TD]
[TD][FONT=courier new]MINTSYS[/FONT][/TD]
[TD][FONT=courier new]Cinnamon 18.3[/FONT][/TD]
[TD][FONT=courier new]ext4[/FONT][/TD]
[TD][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sdb6[/FONT][/TD]
[TD][FONT=courier new]/home[/FONT][/TD]
[TD][FONT=courier new]MINTHOME[/FONT][/TD]
[TD][FONT=courier new]Cinnamon Home[/FONT][/TD]
[TD][FONT=courier new]ext4[/FONT][/TD]
[TD][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sdb7[/FONT][/TD]
[TD][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/TD]
[TD][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/TD]
[TD][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/TD]
[TD][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/TD]
[TD][FONT=courier new][COLOR=#FF0000]**UNSURE**[/COLOR][/FONT][/TD]
[/TR]
[TR]
[TD][FONT=courier new]/dev/sdb8[/FONT][/TD]
[TD][COLOR=#daa520]/dev/vram[/COLOR][/TD]
[TD][FONT=courier new]SWAP[/FONT][/TD]
[TD][FONT=courier new]Mint Swap[/FONT][/TD]
[TD][FONT=courier new]Linux Swap[/FONT][/TD]
[TD]10GB[/TD]
[/TR]
[/TABLE]

Please note: I am aware that Swap is not mounted/mountable from /dev/vram

---

### Post by coffeecat on 2018-01-01
Welcome to the forum.

> **gemmathetechie said:**
> Post Script: If there is more information needed to help me with my problem, please go ahead and either PM me or drop a comment on the thread.

Please do not solicit help by means of pm or other means of private communication. Discussions and solutions posted to the forum can be of benefit to all, and not just the registered forum community. Many unregistered guests browse these and other forums seeking information that will help them.

I would also say, and I mean this kindly, that anyone minded to help you needs less information at this stage, not more. If there is a question in your post, I have been unable to find it. Without a succinct statement of what it is you want from the community, you are unlikely to get help.

---

### Post by gemmathetechie on 2018-01-01
> **coffeecat said:**
> Welcome to the forum.



Please do not solicit help by means of pm or other means of private communication. Discussions and solutions posted to the forum can be of benefit to all, and not just the registered forum community. Many unregistered guests browse these and other forums seeking information that will help them.

I would also say, and I mean this kindly, that anyone minded to help you needs less information at this stage, not more. If there is a question in your post, I have been unable to find it. Without a succinct statement of what it is you want from the community, you are unlikely to get help.

I have amended the thread post and I was hoping that you would be able to look it through, or having one of the mods look it through if you are busy.

Thanks
Gemma

---

### Post by gemmathetechie on 2018-01-05
Bump

---

### Post by oldfred on 2018-01-05
I am confused.

The Lenovo specs you posted are for an older BIOS only system.
But your partition layouts are for a newer UEFI system.

I prefer to have an ESP on every drive, even if Ubuntu's grub only installs to the ESP - efi system partition on sda.
My install of Fedora, did let me use the ESP on sdb, and I use it as a backup of all the /EFI folders entries in sda's ESP..

I have mostly Ubuntu installs. And I prefer to keep /home inside / (root), but then have a much larger shared data partition.
When I still had XP, I had a shared NTFS data partition. Then added a shared Linux data partition as I installed another Ubuntu flavor/version. Eventually all data migrated into an ext4 partition at /mnt/data which is mounted into all installs and folders linked into each /home to make it look almost like standard folder structure.

Make sure sdb is gpt partitioned.

I only use 2GB for swap and that probably is too much. I do not hibernate and do not suggest hibernation. The only reason to have a large swap is if hibernating. And now installs of Ubuntu from 17.04 and newer use swap file. They will use a swap partition if found.

My partitioning, just as one example, note drive not fully partitioned. Since added a couple of 25GB partitions for newer installs.
[https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413](https://ubuntuforums.org/showthread.php?t=2305833&p=13404413#post13404413)

I do not think burg even works with UEFI. If you want graphical boot then you can use rEFInd. But I use grub2 as I only see menu for 3 sec, in case I am booting one of my other installs.
       [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by gemmathetechie on 2018-01-05
Thank you for the reply oldfred!


[LIST]
[*]Obsidian's hardware is capable of UEFI as far as I am aware. (I know this from Ubiquity complaining at me to make sure that it needs UEFI mode to run properly) 
[*]In the past I have had problems with having multiple EFI partitions so that is down to my personal preference. 
[*]In regards to having seperate /home partitions, I do this to ensure that if something was to go wrong, the home partition is separate so all I would need to do is to mount that partition. I have a history for botching up Linux installs by messing around with things I shouldn't. 
[*]Both sda & sdb was going to be formatted using GPT (Who even uses MBR on new systems anyways?) 
[*]I was being slightly overzealous with the swap partitions... I do hibernate quite a fair bit compared to a standard user. In the new layout, I don't have any swap partitions but I was planning on having swap files for each install instead of a specific partition. 
[*]I was looking into rEFInd and what I was planning on doing was installing rEFInd via /sdb7 [New Layout] after all of the other OS's are installed. 
[/LIST]

I do have a newer plan if that would be of help to you?

The reason I have the number of partitions as they are is to stop any cognitive dissonance going on.

Thanks for your help!

---

### Post by oldfred on 2018-01-05
I find each user has his own preferences and then partitioning needs to be unique for that user.
Some general rules apply but otherwise you can do just about anything your want. 
And if you have good backups, I backup my /home and data partition(s), so I can easily reinstall.
My new installs may not use same /home info as I want different configuration, but will have same data.

Even if you want separate /home partitions, if multiple installs, you may want a shared ext4 partition.
But can use one or more of the NTFS partitions for shared data. Just make sure Windows fast start up or hibernation is off, or the Linux NTFS driver will not mount.

---

