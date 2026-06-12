---
title: "Installer wants to put extra partitions on a new SSD"
date: 2020-03-26
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2020-03-26
I'm trying to install Ubuntu-MATE 18.04.4 on a new, empty, external standalone 1 terabyte SSD.  

I have 2 other drives in my desktop workstation, so in the installer I selected "do not use" for the swap spaces on those drives.

I then selected to create an 8 GB swap space for the SSD as a "logical" or extended partition at the end of the SSD's empty space. (Since my desktop box has 8 GB of RAM.)

Then I set up one large primary partition for both "/" (root) and /home directories from "Beginning of space" using  the ext4 filesystem.  

I selected for the bootloader to be on "sde" which is the SSD.

But when I click on "Install now," the informational box that pops up says that the large primary partition will be partition 2, and that the 8 GB swap partition will be partition 5. 

The installer wants partitions 1, 3 and 4 to be "unallocated space" partitions.  Is this normal?  I defined just 2 partitions.  I don't understand why the installer wants to create five partitions on my SSD.  

Since I want to understand what's going on with this, I did not go ahead with the install.

Can anyone shed light on what's going on here?

---

### Post by Impavidus on 2020-03-26
It is normal, but you don't get 5 partitions. You get 3.

MBR partitioned drives (and using that partitioning method may not be the best choice) support at most 4 primary partitions, which always get numbered 1–4. To be able to create more partitions, it is possible to make one of these an extended partition, so you can put logical partitions inside. The logical partitions get number 5 and up. So when you create the first partition as a logical partition, the Ubuntu installer creates a primary partition, number 1, and makes it an extended partition. Then it creates you swap partition as a logical partition inside and gives it number 5. Finally it creates the root partition as a primary partition, giving it number 2, as 1 was already taken.

The way you partitioned the drive will work, but it may not be ideal. Of course, nobody will agree on what is ideal.

---

### Post by watchpocket on 2020-03-26
What would be "standard"?  Seems like a lot of space is getting wasted with three "unallocated space" partitions.  How would I correct this so as to limit the number of partitions and also not have unused or wasted space.  Or do I want some small bit of free or unallocated space as, say, one partition?

Could I avoid all this if the first partition I create is the large / and home as primary, from the beginning of the space (leaving only 10 GB at the end), then, secondly, create the 8 GB swap space from "end of space" (or even from "beginning of space" which would be at the end of the primary partition, with 2 GB at the end - thoough maybe that would create a 3rd partition.) 

Will I still end up with more than 2 partitions?  Or rather, how can I do this to have only 2 (and is it ok to want just 2, or is there some need for a third partition to have "free space".  Is there generally a need for free space with an SSD?

---

### Post by ajgreeny on 2020-03-26
You do not need a swap partition any more as Ubuntu now uses a swapfile (generally 2GB, I think) instead, this being created automatically if no swap partition is found.

If this is a UEFI installation, and all recent machines will be using that by default nowadays, there will also be a small EFI partition which is fat32 format.

It is, however, difficult to give you much more help without knowing exactly what you've currently got on the disk, and I'm afraid I can not quite figure out the details of what you said in the first post.

Can you please run the following command from either your current OS (I'm assuming you already use Ubuntu?) or from a live system .
```
sudo fdisk -l
```

Please use **Code-Tags** for terminal output as it makes that output much more easily read and understood, formatting the text as seen in terminal, not as plain text when it is copied and pasted. See my signature below for a **How-to**

---

### Post by watchpocket on 2020-03-26
Thanks for the response.  FYI, I tried to do this yesterday on a different SSD, and I did  end up specifically with extra partitions: 

 Partitions 1, 3 and 4 were  "unallocated space" totaling about 40 or 50 GB of wasted space. I don't  know why or how it happened like that.

Just a note about my situation:  Failure for this install is not a good idea for me right now: My  16.04 drive broke and gives me a blank screen, so I'm working from an  older 14.04 spinner (internal) HDD that is crashing on me every 10  minutes and it re-boots slowly, Hence I'm in a bit of a painful place.

 (Also I'm supposed to be working from home right now, and they're starting to wonder what's up with me.)


 So I'd like to get 18.04 up and running asap, and, for right now,  I'll need to be able to boot from this new external 18.04 SSD that I'm trying to format and install right now.


  Over the weekend or as soon as I can,  I'll replace the internal  14.04 spinner with the new 18.04 SSD.  Right now I need a working  system.

My workstation uses BIOS, not UEFI.  Command output:

```
--> sudo fdisk -l  
[sudo] password for rj: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x3aec6e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1932552191   966275072   83  Linux
/dev/sda2      1932552192  1953525167    10486488   82  Linux swap / Solaris

Disk /dev/sdb: 960.2 GB, 960197124096 bytes
255 heads, 63 sectors/track, 116737 cylinders, total 1875385008 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b53b4

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048  1833400319   916699136   83  Linux
/dev/sdb2      1833400320  1854412799    10506240   82  Linux swap / Solaris

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41031e20

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048  1953523711   976760832   83  Linux

```

sda is an SSD with Ubuntu-MATE 16.04, but I'm getting a blank screen on it right now. This has been my main system up to now, but I can't use it now, the desktop is fubar.

sdb is a spinner HDD with Ubuntu-MATE 14.04, which is what I'm working on now, but it's crashing way too frequently.

sdc is a spinner with no OS, it's storage -- just images, files etc.

---

### Post by dragonfly41 on 2020-03-26
This is what I would try.
First ensure that you have a working LiveUSB which you appear to have.
Launch LiveUSB "Try Ubuntu" and then run GParted to view /dev/sda
I would venture (caveat emptor) to remove the bootflags in /dev/sda1 (this makes your first Ubuntu unbootable until you need to go back later to reset flags).
Now install Ubuntu into your external SSD by creating EFI partition (500MB with boot flags) and ext4 partition for root /..
I suspect that the unallocated spaces on SSD might be due to experimenting with SSD provisioning (not now needed apparently, or so I have been told).
I will venture further that you install rEFInd while in LiveUSB. The target location for rEFInd will be the EFI partition /dev/sdb1 in your SSD.
Then hope for the best and reboot.
If you get into your new SSD you can reset the boot flags in /dev/sda.
[Fuller tips read here]("https://forums.linuxmint.com/viewtopic.php?t=287353").

[P.S,] Secure boot to be disabled through BIOS options/settings.

---

### Post by watchpocket on 2020-03-26
Thanks, I'll read your 'further tips' link (looks like lots to read there).  

One thing that confuses me about your mention of "EFI" or "EFI partition" -- Doesn't "EFI" -- or anything to do with it -- apply only when you have a UEFI instead of a BIOS computer?  Mine is from 2010 and is BIOS, not UEFI.

Also, my /dev/**sda** is my only currently working (old, backup) system, and it crashes a lot - about every ten minutes.  It's my Ubuntu-MATE 14.04 installation on an old spinner HDD.  I don't know that I just yet want to mess with boot flags on it, for fear of losing my only working installation.

My new SSD that I want to install Ubuntu-MATE 18.04 on shows up as "**sde**".

Also, I'm afraid I have never seen or heard of "rEFInd" and don't know what that is.  

And I don't believe I have "Secure Boot" -- doesn't that exist only in EUFI (and not BIOS) systems?

Again, I'm sure that reading through your tips link will help with some of these questions.  So thank you for responding. I'm not a linux newbie, I just *rarely* do new installs and disk-partitioning, so I'm needing to get up to speed, just  to get 18.04 installed on an external SSD and have a working setup.

---

### Post by oldfred on 2020-03-26
Your signature shows a new UEFI based system. You should make it clear that you are installing on an old system and what the specs are on that system.

You are correct, UEFI only applies to system since about  2012 when Microsoft required vendors to use UEFI with gpt partitioning. Apple Macs used EFI before that from when they converted to using Intel chips.

The rEFInd program is for UEFI boot. Started with Macs but works for UEFI based PCs.

You can still use the newer gpt partitioning normally used with UEFI, but then would have a tiny 1MB unformatted partition for grub to correctly install in BIOS boot mode. Since I knew when I had my old BIOS system that eventually I would convert to UEFI on a newer system, I started converting all drives to gpt for future compatibility without total reformatting.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

