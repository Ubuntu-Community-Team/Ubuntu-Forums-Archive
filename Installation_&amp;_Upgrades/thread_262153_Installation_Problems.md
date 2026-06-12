---
title: "Installation Problems"
date: 2006-09-21
forum: Installation &amp; Upgrades
---

### Post by ashfaq.s on 2006-09-21
Sir,
I had a windows XP version which was certified as not genine by microsoft and a warning message was displayed, this started my quest to search an alternative, but with my limited knowledge I was not able to decide and risk linux. I somehow traced the 'Ship it' address and requested them for a CD which they did it, thankfully!

During the intervening time I Installed a copy of licenced xp2, here I faced problems again as I was not able to connect through the bluetooth as before, because the microsft team has come up with thier own bluetooth capabilities and my bluetooth software started giving me trouble! In xp1 it was working fine.

I wiped up some more Data and formated another partition for Windows 98, this worked, but with limitations, I am writing you this mail through the same connection on win98. Now again I took up the ubuntu live CD, this live cd wiped out the ntfs partition along with xp2. The partition is free full 4.87 GB and I need help to install this linux on this partition.

Please help me do the installation now freed from xp-2. I am a newbe, and have my limitations. For your info, I am pasting the window displayed of system information below:

I am pasting the system info as displayed in window for you. D: is free for linux.
 presently I am using win98 as described in earlier posts.
 
 Microsoft Windows 98 4.10.2222 A 
 Clean install using Full OEM CD /T:C:\WININST0.400 /SrcDir=F:\WIN98 /IS /IZ /II /NR /II /C /U:xxxxxxxxxxxxxxxxx
 IE 5 6.0.2800.1106
 Uptime: 0:00:13:14
 Normal mode
 On "A" as "a"
 
 AuthenticAMD AMD Duron(tm) processor 
 224MB RAM
 52% system resources free
 Windows-managed swap file on drive C (3876MB free)
 Available space on drive C: 3876MB of 4994MB (FAT32)
 Available space on drive D: 4994MB of 4994MB (FAT32)
 Available space on drive E: 1965MB of 4994MB (FAT32)
 Available space on drive F: 1473MB of 4438MB (FAT32)

History of problems faced during installation so far:

After running the live cd, clicking the install icon, out of 6 steps four stages get completed some how, in the fifth stage the problems start.

The three options window for auto partitioning, complete erase and manual partition is displayed. Clicking the 1st option shows resizing of disk 1 partion 5 when okayed displays a partition to be created of 51%, but when clicked the computer hangs and no further action takes place.

Clicking the third option of manual partition, only once the Gpart window came up I chosed the actions for formating as fat32 the drive which was holding the xp2 and creating swap partition as well. Out of three action only one got completed and the pc hanged after Restarting thier after this xindow of Gpart was never displayed but my xp2 has gone and the partition got formated. Now that dirve is (D:) and empty for ubuntu insatallation, please help me in guiding step by step how to move ahead and got this ubuntu installed on my D:

I have tried the above two procedures numerous times but got held up exactly at the same points.

Please help me out!

Ashfaq.

---

### Post by pansz on 2006-09-21
My only concern is that the packages like openssh-server and build-essential are not installed by default.

This may confuse quite a few people with or without experiences of Linux.

I just cannot understand why the openssh-server and gcc can be missing for a modern Linux system.

---

### Post by ashfaq.s on 2006-09-28
I am pasting the system info as displayed in window for you. D: is free for linux.
presently I am using win98 as described in earlier posts.

Microsoft Windows 98 4.10.2222 A 
Clean install using Full OEM CD /T:C:\WININST0.400 /SrcDir=F:\WIN98 /IS /IZ /II /NR /II /C /Uxxxxxxxxxxxxxxxx
IE 5 6.0.2800.1106
Uptime: 0:00:13:14
Normal mode
On "A" as "a"

AuthenticAMD AMD Duron(tm) processor 
224MB RAM
52% system resources free
Windows-managed swap file on drive C (3876MB free)
Available space on drive C: 3876MB of 4994MB (FAT32)
Available space on drive D: 4994MB of 4994MB (FAT32)
Available space on drive E: 1965MB of 4994MB (FAT32)
Available space on drive F: 1473MB of 4438MB (FAT32)

History of problems faced during installation so far:

After running the live cd, clicking the install icon, out of 6 steps four stages get completed some how, in the fifth stage the problems start.

The three options window for auto partitioning, complete erase and manual partition is displayed. Clicking the 1st option shows resizing of disk 1 partion 5 when okayed displays a partition to be created of 51%, but when clicked the computer hangs and no further action takes place.

Clicking the third option of manual partition, only once the Gpart window came up I chosed the actions for formating as fat32 the drive which was holding the xp2 and creating swap partition as well. Out of three action only one got completed and the pc hanged after Restarting thier after this xindow of Gpart was never displayed but my xp2 has gone and the partition got formated. Now that dirve is (D and empty for ubuntu insatallation, please help me in guiding step by step how to move ahead and got this ubuntu installed on my D:

I have tried the above two procedures numerous times but got held up exactly at the same points.



I have an original Ubuntu live cd received from ship it. My problem is the installation stalls before evan getting started, that is I am not able to complete the questionaire, out of the 6 stages, 5th is the one where the pc freezes.

I would like to know If I can copy the contents of the cd in one of the drive meant for ubuntu (Partition) and then get the thing installed with the help of dos like we do it for windows, if such alternate method is available please help meout with the procedure, and the additional files I have to download!

Will somebody help me out!!!!!!!

---

