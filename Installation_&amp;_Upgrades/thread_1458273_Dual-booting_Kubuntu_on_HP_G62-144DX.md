---
title: "Dual-booting Kubuntu on HP G62-144DX"
date: 2010-04-19
forum: Installation &amp; Upgrades
---

### Post by PacSci on 2010-04-19
I'm attempting to dual-boot Kubuntu on a friend's brand new HP G62-144DX laptop (he's been using Kubuntu for a while on his desktop and laptop). After dealing with all the stupid vendor-specific stuff on the Win7 side, I am now attempting to install Kubuntu.

Due to graphics issues, I am having to use the beta version of 10.04, since the graphics driver and required kernel version apparently don't come with 9.10. I shrunk the Windows partition from 486 GB to 286 GB (or so), but the installer is reading "unusable". The disk layout is four primary partitions, in this order:

[LIST]
[*] 209 MB NTFS boot partition
[*] 286 GB NTFS partition (this has the main data on it - used to be 486 GB before I shrunk it)
[*] 200 GB free space (installer lists it as "unusable")
[*] 13.4 GB NTFS partition (I think this is for system restore)
[*] 108 MB FAT32 partition with LBA flag set (not sure what this is - it just has a folder named "Hewlett-Packard", with a subfolder "SystemDiags", with a bunch of weird files inside)
[/LIST]

So, my questions (if anyone can answer any of these, that would be great):

[LIST]
[*] What the frack is that 108 MB partition?
[*] Can that partition be nuked?
[*] How are there 4 primary partitions on the same MS-DOS drive?
[*] Why is the free space I made reading "unusable"?
[*] Is using the beta affecting this?
[*] Is using Kubuntu affecting this?
[*] Why doesn't Kubuntu come with a graphical partition manager?
[*] Has anyone else had similar issues with this computer?
[*] Has anyone got a dual-boot to work on this computer?
[*] Any ideas?
[/LIST]

---

### Post by PacSci on 2010-04-24
I'm sorry for bumping this, but I can't find any useful information on the Internet. Also, the same thing happens with the new 10.04 RC.

---

### Post by smokineasy on 2010-06-20
did you manage to get it workin???
i also have a problem trying to install ubuntu 10.04 (as well as 9.1) alone side windows on a hp g62 :( :confused: 

it keeps wantin to use whole hard drive

EDIT: its find now, i just defraged the hard drive in windows and the install side by side option came up
wish i tryed that b4 deleting the recovery partition :(

---

### Post by deedsofhaphazzard on 2010-07-08
> **smokineasy said:**
> did you manage to get it workin???
i also have a problem trying to install ubuntu 10.04 (as well as 9.1) alone side windows on a hp g62 :( :confused: 

it keeps wantin to use whole hard drive

EDIT: its find now, i just defraged the hard drive in windows and the install side by side option came up
wish i tryed that b4 deleting the recovery partition :(
I have the same laptop. I bumped into the same problem. Does it really work after the defrag. I tried doing it in vain. However, I accidentally converted my hard drive into a dynamic partition before doing the defrag. If the defrag actually worked I could convert it back to a basic partition (which entails a complete format).

---

### Post by deedsofhaphazzard on 2010-08-13
smokineasy's solution works absolutely fine. Just defragment and ubuntu detects windows and lets you allocate space for ubuntu and dual boot..

---

### Post by Soul_Retriever on 2011-02-02
> **PacSci said:**
> I'm attempting to dual-boot Kubuntu on a friend's brand new HP G62-144DX laptop (he's been using Kubuntu for a while on his desktop and laptop). After dealing with all the stupid vendor-specific stuff on the Win7 side, I am now attempting to install Kubuntu.

Due to graphics issues, I am having to use the beta version of 10.04, since the graphics driver and required kernel version apparently don't come with 9.10. I shrunk the Windows partition from 486 GB to 286 GB (or so), but the installer is reading "unusable". The disk layout is four primary partitions, in this order:

[LIST]
[*] 209 MB NTFS boot partition
[*] 286 GB NTFS partition (this has the main data on it - used to be 486 GB before I shrunk it)
[*] 200 GB free space (installer lists it as "unusable")
[*] 13.4 GB NTFS partition (I think this is for system restore)
[*] 108 MB FAT32 partition with LBA flag set (not sure what this is - it just has a folder named "Hewlett-Packard", with a subfolder "SystemDiags", with a bunch of weird files inside)
[/LIST]

So, my questions (if anyone can answer any of these, that would be great):

[LIST]
[*] What the frack is that 108 MB partition?
[*] Can that partition be nuked?
[*] How are there 4 primary partitions on the same MS-DOS drive?
[*] Why is the free space I made reading "unusable"?
[*] Is using the beta affecting this?
[*] Is using Kubuntu affecting this?
[*] Why doesn't Kubuntu come with a graphical partition manager?
[*] Has anyone else had similar issues with this computer?
[*] Has anyone got a dual-boot to work on this computer?
[*] Any ideas?
[/LIST]



[LIST]
[*]The 108MB partition is used to store HP's tools and other stuff from them
[*]I'd advise against nuking it as there seems to be somthing on the hard drive that is needed to boot properly (i took mine's hard drive out, poped in a new one and it wouldn't boot from it)
[*]4 partitions is the maximum amount of partitions you can have on a drive if i remember correctly
[/LIST]
Still trying to get mine to dual boot but not having much luck
I'd take all this with a pinch of salt though, i'm still quite new to messing with partitions and dual-booting

---

