---
title: "Upgraded to Ubuntu 20.04 &quot;New Partition Table&quot;"
date: 2021-01-20
forum: Installation &amp; Upgrades
---

### Post by Gnusboy on 2021-01-20
Hey All,

I finally went for a long delayed upgrade from 16.04 to 20.04. I made 4 or 5 attempts, using the 20.04 live disk - but canceled them when I came to something I wanted to be sure of before continuing.

However, as I started the newest attempt, there was a msg that Ubuntu 20.04 was already installed on the system. I went ahead and continued running 20.04, believing that the install would go back to step 1 and erase anything still on the HDD during the procedure as step one. Is this accurate?

I wanted a clean install - preferably with a single partition. Minus the boot, and any system partitions needed.
If the "[COLOR=#494949][FONT=DDG_ProximaNova]Focal Fossa" [/FONT][/COLOR]installation will automatically build-in whatever sub-partitions, do I need to manually divide the primary partition into sub-partitions? If I later want an extra partition, can do that with the installed O.S?

There is a line showing "installation type" which shows "/dev/sda"  the next lines are -- 

"/dev/sda1"  (type) Fat 32  (size) 536 MB  (used) 33 MB

"/dev/sda5"  (type) ext 4   (size) 639595 MB (Used) 16375 MB   (system) Ubuntu 20.04.1 LTS (20.04)

I seem to recall that "Fat 32" should be either "FAT 64" or "EXT 3" or "EXT 4"

Below this information at the right side of the screen is a button labeled 
"New Partition Table ..." and a button labeled "Revert"

Then it shows "Device for boot loader installation:"
/dev/sda  ATA WDC WD 6400AAKS-0 (640.1 GB"

If 




-------------------------------------------------------------------

Off topic question:
Also: I used the Ubuntu 20.04 live disk to finish a little bit of temporary work. I recently got a faster internet speed, but my system did not seem as fast as it should after a 5-fold speed increase. Assuming everything else is configured correctly, could Ubuntu 20.04 be slowing it down?

---

### Post by ajgreeny on 2021-01-20
I am totally confused about where you have got to at this point so for clarity, before you change any partitions already on the hard disk, I recommend that you abort the current installation process, boot to your 16.04 system and then show us the output of the following commands.
```
sudo fdisk -l
cat /etc/fstab
mount
```
which will show us more about that 16.04 installation and its partitions.

---

### Post by yancek on 2021-01-20
> I seem to recall that "Fat 32" should be either "FAT 64" or "EXT 3" or "EXT 4"
 

That would an EFI partition.  Is your install of 16.04 EFI?  I doubt it or it would already have an EFI partition   which would show as FAT32 or vfat in most cases.

 Can you clarify what you want to do.  Is it to install 20.04 and overwrite everything or install 20.04 alongside 16.04?  If you create a new partition table that will delete anything on the drive presently.

---

### Post by Gnusboy on 2021-01-20
[COLOR=#000000]yancek

Yes, I want to overwrite everything. Having two versions of Ubuntu on the same system turned out to be a goofy idea for my circumstances. Your comment is right on target. If I continue with the install I'm in now, will the automatic process essentially handle the FAT 32 question.
My big question now is do I manually do anything with FAT 32? 
Isn't the system supposed to have EXT3 and EXT4? It's been so long, that I don't remember .


[/COLOR][COLOR=#000000]That would an EFI partition. Is your install of 16.04 EFI? I doubt it or it would already have an EFI partition which would show as FAT32 or vfat in most cases.[/COLOR]

[COLOR=#000000]Can you clarify what you want to do. Is it to install 20.04 and overwrite everything or install 20.04 alongside 16.04? If you create a new partition table that will delete anything on the drive presently.[/COLOR][COLOR=#000000]


[/COLOR]

---

### Post by CelticWarrior on 2021-01-20
Yes, you can proceed with the "erase and install" option. Or you can, in the live session, open Gparted and with the target drive selected go to Device menu > Create new partition table > select "GPT". Then you're certain you're installing to a blank drive. The installer will create a small FAT32 partition, the ESP (EFI System Partition). Yes, it's FAT32 and is required for any installation in UEFI mode, this was already explained. By default the onlñpy other partition that will now be created is / (root) because by default /home is inside /, not a separated partition, and now Ubuntu uses a swapfile instead of a swap partition, therefore the partitioning is much more simplified. That's all.

---

### Post by grahammechanical on 2021-01-20
In regard to your off topic question, I think I am right in saying that running Ubuntu from a USB stick will be slower than running it from a hard disk. You can always open System Monitor and that will show the download and upload internet speeds. 

Regards

---

### Post by Gnusboy on 2021-01-20
Thanks

---

### Post by oldfred on 2021-01-20
If using UEFI, better to also use gpt partitioning. 
Ubuntu will let you install in UEFI boot mode to MBR(msdos) partitioning, but probably should not.
Windows has required gpt since 2012 for UEFI installs.
New install converting to gpt will erase a drive, but there are tools to convert a drive, but more for data drives. 

Be sure to have good backups.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by bcschmerker on 2021-01-21
@[Gnusboy](https://ubuntuforums.org/member.php?u=880166)  **When I installed 18.04.1-LTS on my currently down Hot Rod gPC, I used one 3.5" Western Digital and three 2.5" TOSHIBA SATA HDDs, all in AHCI mode.**  The 3.5" WD has since been replaced with a 2.5" WD to uniform max operating temps to 60°C.  All partitions are ext4 except /boot is ext2 and /home is BTrFS.  (Note to self:  Back up /home to eSATA ext4 prior to reformatting /sdd1 as Sun Microsystems ZFS.)  The dist-upgrade to 20.04 went smoothly enough, and the rig was reliable up to 15 January 2021, when it no longer recognized any i8042 keyboards during POST.

---

### Post by Gnusboy on 2021-01-21
Help!
I just logged in and saw this comment about "Installed 18.04.1-LTS on my currently down HOT Rod gPC ..." Etc.
To the very best of my knowledge, I did not write this. I certainly did not write it as response to this current thread. Can anyone tell me where it came from and hopefully why it is here?

---

### Post by CelticWarrior on 2021-01-22
@Gnusboy

Don't worry, you didn't post that, other user did.
That user seems to have a legit issue that have been dealt with in its own thread, so far so good. The problem is this person thinking it's OK to "spam" other threads like this one in order, I suppose, to raise awareness to their own issue (at least I hope that's the reason, otherwise it's just annoying and disrespectful). I already told them not to do it and also reported a few posts so the Mods can deal with it in a way they see fit.
You di nothing wrong, let that be clear.

---

### Post by Gnusboy on 2021-01-22
Hey Thanks. I knew It wasn't mine. He lost me at Hot Rod. This my old (Very,very old) Win XP setup from about a dozen years ago. I keep it for the thousands of songs I accumulated during the music peer-to-peer sites. I can't remember the name of it, but at the time I spent as 10 hours a day just D/L tracks. I'd rather sever an appendage than lose all that music.
Which begs a question: To transfer those files, would you recommend using a big USB or a portable HDD? Also, is there an easy way to figure out how much space I'd need to transfer it? The files are spread all over the drive, so I'm guessing it's gonna be a project. Your thoughts?

---

### Post by CelticWarrior on 2021-01-23
If the files aren't organized inside the same folder it will be hard to have an accurate picture of the total space they're using.
If up to 50GB a free Mega.nz account can be used *additionally *&#8203; to the external drive for backup.

---

### Post by Gnusboy on 2021-01-25
I will check it out. I've got 20.04 installed and up and running for the most part.
P.S. I appreciate your help with all this. Thanks.

---

