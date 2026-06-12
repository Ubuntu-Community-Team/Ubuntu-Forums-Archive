---
title: "Dual drive dual boot partitioning strategies"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by ElBuscador on 2006-12-15
I have wanted to try Linux again for awhile now, especially as I learned more about Vista and realized it was not for me. I was planning to buy a new hard drive, so I held off on installation until I did that. I did not worry about partitioning, beyond a separate Swap partition, as I knew this was just a test install. I have now played around with Kubuntu Edgy enough over the last two weeks to decide that I want to make it my primary OS, despite the fact that it sometimes does not play well with Nvidia. Windows XP, being Windows, has developed enough little glitches after multiple hardware & driver changes over the last 3 years that I am willing to wipe both hard drives and reinstall everything from scratch. (Acronis TrueImage reports that the clone image of my original clean install with all major apps loaded is corrupted, damn it!) Now I need to decide on the best partitioning strategy. Here is what I currently have on my Windows drive:

Drive: 160GB IDE
Partitions: 
C: - 1GB - FAT - Swap (pagefile) (Windows)
D: - 15GB - NTFS - Windows OS and all apps
E: - 1GB - NTFS - Temporary files
F: - 130GB (approximate) - NTFS - Data

The swap is the first partition to keep it on the outer edge, which really helps performance. Most Linux partitioning guides recommend putting it last, which I don't understand at all. The various OS and Internet temp file locations are redirected to E: to reduce fragmentation issues.

My new setup:
1. 400GB SATA drive. The new, much faster drive.
2. The 160GB IDE drive listed above,. I am thinking this is best used for backups of the other drive's main partitions, data overflow (mostly downloaded videos and DVD rips, since I can't receive English-language TV where I live), and a swap partition. However, I could consider leaving Windows here and using the other drive just for Linux, especially if it got me out of having to reinstall and reconfigure Windows at this moment.

If this was your setup, how would you partition it with both Windows XP and Kubuntu installed? 

A few considerations:
- Data partitions needed to be readable from both OSes, and from my laptop or other computers on the network. I really don't want to use a FAT file system to accomplish this. So far, using Ext3 with EXT2IFS plus Samba seems to work fine for this. I will need at least one NTFS partition for sensitive work-related files and anything else I want to keep out of access to other users. EXT2IFS is unable to preserve user permissions, and anyone else using the computer will probably need to use Windows.
- The 400GB disk needs to be able to continue to function correctly and retain all data with a minimum of reconfiguration if the 160 GB drive dies or is removed. However, if I lost the Windows system and application partition it would not be a major problem as long as I had a backup - assuming that has not become corrupted.
- One reconfiguration guide I read said that having two Linux swap partitions of identical size on the outer edge of a drive will provide better performance due to a quasi-striping effect, with Linux swapping out to whichever drive is available first. Anyone tested this? 
- I have 1 GB of RAM, and would rather be generous than stingy when it comes to swap partitions. I don't plan to add another gig soon, since I am not a gamer and don't do heavy video or scientific work, but it might happen.
- I have no idea how big the partition needs to be for Linux plus all apps - I tend to install a lot of utilities, and a fair number of major applications.
- I have a programming background, and even administered a Unix server 10 years ago, but am really rusty with Linux at this time. I don't mind using a command line, but I need stuff spelled out explicitly, or I have to do a lot of research to figure out the details. Thanks for everyone's help.

---

### Post by happy-and-lost on 2006-12-15
I've found the best way to share between Win and Lin is with a FAT32 partition which is set, using TweakUI, to be the "My Documents" folder, and then creating a softlink to the drive in /home

I've never seen my Ubuntu using more than 100mb swapspace (I have 1gb ram), but it's safest to create a swapspace which is 512-1024mb in size.

20gb should suffice for Linux and all its apps, as most of them are small and very efficient.

---

### Post by ElBuscador on 2006-12-16
Thanks, although unless someone knows of problems I have not read about with EXT2IFS, I'll use an Ext3 partition for most of the shared space. FAT is a pretty antiquated file system, especially for such a large partition. If Ubuntu and the applications need 20 GB, then that is on par with Windows. With lots of applications loaded, my Windows + apps takes up about 12GB. Anyone else have more suggestions?

---

### Post by gn2 on 2006-12-16
You've got enough RAM for running a Virtual PC on the SATA drive....?

---

### Post by ElBuscador on 2006-12-17
Not quite sure what you are suggesting, gn2. Are you recommending using Wine/Cedega/Crossover Office instead of having a Windows partition? If so, that unfortunately won't work for all of the Windows apps that I need to run, although when and if SynCE  gets full functionality for Windows Mobile 5 devices I will be a lot closer. However, there are a few apps that I need on occasion that either have no Linux version (or fully compatible equivalent) or cost too much to justify buying a second copy.

---

### Post by gn2 on 2006-12-17
Suggesting running Windows as a "Virtual PC" with either VMWare or Parallels.

No need to dual boot and both OS's running at the same time.

Not good for games though.....

[http://www.vmware.com/download/server/](http://www.vmware.com/download/server/) (free)

[http://www.parallels.com/](http://www.parallels.com/) (not free)

---

