---
title: "Win98, WinXP and Ubuntu together"
date: 2005-02-12
forum: Installation &amp; Upgrades
---

### Post by ZuLuuuuuu on 2005-02-12
Hi, I am a Windows user for years but I really want to learn Linux. I saw Ubuntu and decided to start with it. I'm downloading iso file right now. I have 4 partitions and 2 OS's installed on my computer :shock:  :

c: 9,75 GB (Win 98 Installed) (FAT)
d: 29,2 GB (Win XP Installed) (NTFS)
e: 14,6 GB (Reserved for Ubuntu) (FAT)
f: 20,8 (For any files) (FAT)

Now, when I boot my computer it asks me which one of Win98 or WinXP to run. I want my computer to ask also after installing Ubuntu. But I don't have much technical knowledge and I haven't installed Linux before. My question will my computer keep asking me which OS to run on the start, after installing Ubuntu? (I hope I will install Ubuntu correctly.  :?  )

My system is:

PIII 733
256 MB RAM
32MB GeForce 1 DDR Plus
80 GB Samsung harddrive

---

### Post by piedamaro on 2005-02-12
[QUOTE=ZuLuuuuuu]Hi, I am a Windows user for years but I really want to learn Linux. I saw Ubuntu and decided to start with it. I'm downloading iso file right now. I have 4 partitions and 2 OS's installed on my computer :shock:  :

c: 9,75 GB (Win 98 Installed) (FAT)
d: 29,2 GB (Win XP Installed) (NTFS)
e: 14,6 GB (Reserved for Ubuntu) (FAT)
f: 20,8 (For any files) (FAT)

Now, when I boot my computer it asks me which one of Win98 or WinXP to run. I want my computer to ask also after installing Ubuntu. But I don't have much technical knowledge and I haven't installed Linux before. My question will my computer keep asking me which OS to run on the start, after installing Ubuntu? (I hope I will install Ubuntu correctly.  :?  )

My system is:

PIII 733
256 MB RAM
32MB GeForce 1 DDR Plus
80 GB Samsung harddrive[/QUOTE]
 What you call "keep asking me" is a bootloader. Ubunru uses grub. During installation it should ask to install grub and to configure it to load other legacy operating systems.

---

### Post by ZuLuuuuuu on 2005-02-12
Thanks, the download has been completed. I will install Ubuntu after I do my backups. But I prepared the CD and tried it. It worked, the Ubuntu screen came and I wanted to go back to windows -or shut down the computer- but I couldn't find any exit button?
And I have one more question I won't need to format any of my drives again (My e:\ drive has already formatted.) and won't need to loose any data in other drives, do I?

---

### Post by Cyhatch on 2005-02-13
[QUOTE=ZuLuuuuuu]...I won't need to format any of my drives again (My e:\ drive has already formatted.) and won't need to lose any data in other drives, do I?[/QUOTE]

You will be asked whether you want to manually edit the partitions. If you choose so, you'll be able to leave the data on C:, D: (& etc.) intact (this option is under somth. like "*format the partition*").

Formatting your E: drive (*ext3* instead of *FAT*) isn't that hard - use the same menu.

If Ubuntu doesn't automatically configure *Grub*, go [here](http://ubuntuguide.org/#addwindowsentrygrubmenu) ([borrowed](http://www.ubuntuforums.org/showpost.php?p=66608&postcount=2) wisdom) .

---

### Post by ZuLuuuuuu on 2005-02-13
[QUOTE=Cyhatch]You will be asked whether you want to manually edit the partitions. If you choose so, you'll be able to leave the data on C:, D: (& etc.) intact (this option is under somth. like "*format the partition*").

Formatting your E: drive (*ext3* instead of *FAT*) isn't that hard - use the same menu.

If Ubuntu doesn't automatically configure *Grub*, go [here](http://ubuntuguide.org/#addwindowsentrygrubmenu) ([borrowed](http://www.ubuntuforums.org/showpost.php?p=66608&postcount=2) wisdom) .[/QUOTE]
 Thanks :)

---

