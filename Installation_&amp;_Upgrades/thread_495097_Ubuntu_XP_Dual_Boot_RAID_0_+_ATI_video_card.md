---
title: "Ubuntu XP Dual Boot RAID 0 + ATI video card"
date: 2007-07-07
forum: Installation &amp; Upgrades
---

### Post by Nicepen on 2007-07-07
So...  I'm kinda new to linux but I know my way around by now and I'm good with windows, however I'm no expert with patitions.  What I'm trying to do is dual boot Ubuntu 7.04 and Windows XP Pro on my desktop which has an ATI Radeon 9800pro video card in it.  These are all the things I'm aware of that make this install a little difficult.  I read that I just have to use the Ubuntu Desktop Alternate Disk to install with the ATI video card so thats what I'm planning on doing.  If that is going to be a problem for me, please let me know.  

I found a guide for dual booting xp and linux on raid but it isn't as clear as I would like it to be.  
[http://www.overclock3d.net/articles.php?type=3&id=51&page=1&desc=dual_boot_raid_windows_and_linux](http://www.overclock3d.net/articles.php?type=3&id=51&page=1&desc=dual_boot_raid_windows_and_linux)
If I could get help with some of the details I don't understand that would be great.  

My first question is in reference to him saying I can point windows core and program files to different partitions, and the same thing (in respect) with linux.  

(page 1)
"You can however point the Windows core and/or the 'program files' directory to another drive. This certainly helps in putting all your apps and games on the RAIDed partition, but not Windows itself (because the installer can't see the RAID). The first partitions counterpart on the second drive is a great place to put your /boot directory, your /home, or anything else for which you don't want to risk to the redundancies (or lack thereof) of RAID 0. These directories don't, after all, really benefit from RAID anyway and it means that you can happily re-install your Linux desktop without wiping your /home."

How do I point all these folders to different places and when do I do it?
Also, how big should the different partitions be?

Thanks
Aaron

My Computer:
Chaintech ZnF3-250 (nforce 3) motherboard
2x WD Raptor 36.7Gb SATA 150
AMD Athlon 64 3200+ Newcastle 2.2GHz Socket 754
ATI Radeon 9800Pro 256MB

---

