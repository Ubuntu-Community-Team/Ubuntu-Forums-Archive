---
title: "Confussed about uninstalling ubuntu"
date: 2013-05-25
forum: Installation &amp; Upgrades
---

### Post by locogrande247 on 2013-05-25
I wanted to uninstall Ubuntu in a Toshiba laptop so I can sell it, but reading all the posts confused me. I do have a copy of Windows 7, should I just run that and reinstall windows, would that wipe everything away? I really just wanted to take out Ubuntu, but seems almost impossible. I'm not really comfortable messing with partitions having never done anything that technical before. 

Can someone offer some clear directions to fix this problem. I had received this laptop with Ubuntu already installed, but the whole laptop had always ran slow and is very temperamental, Ubuntu doesn't really seem to work well. 

 I just want to get rid of it for a new one I just bought.

Thanks.

---

### Post by DJWYMAN on 2013-05-25
does it dual boot to windows or does it just have ubuntu on it?  I would recommend getting a live cd of gparted and just formatting the hard drive for windows and then stick the windows 7 cd and do a fresh install especially if you are selling it anyway.

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by DJWYMAN on 2013-05-25
to further explain just delete all of the partitions and make a new one in either FAT32 or NTFS format.

---

### Post by locogrande247 on 2013-05-25
It's a dual boot, when I startup, I get several choices, Ubuntu, 2 Choices of Windows 7 (no idea why), then a couple other options relating to recovery or something like that. I never heard of GParted so I'm not sure how to use it.  Perhaps I should just wipe the drive clean? But I'm still not sure how to do it right

---

### Post by fantab on 2013-05-26
> **locogrande247 said:**
> I wanted to uninstall Ubuntu in a Toshiba laptop so I can sell it, but reading all the posts confused me. I do have a copy of Windows 7, should I just run that and reinstall windows, would that wipe everything away? I really just wanted to take out Ubuntu, but seems almost impossible. I'm not really comfortable messing with partitions having never done anything that technical before. 

Can someone offer some clear directions to fix this problem. I had received this laptop with Ubuntu already installed, but the whole laptop had always ran slow and is very temperamental, Ubuntu doesn't really seem to work well. 

 I just want to get rid of it for a new one I just bought.

Thanks.

Boot with Ubutnu install DVD/USB if you have one already, "Try Ubuntu"- Run Gparted and DELETE all Ubuntu partitions that you have on the disk. Leave the deleted partition space as 'UNALLOCATED", and do not create any partitions from it. If you don't have Ubuntu DVD/USB then use [GPARTED LIVE CD/USB]("http://gparted.sourceforge.net/livecd.php").
Then you have to fix the Windows Boot Loader and you can do this with Windows Repair Disc or Windows Recovery, [Read HERE]("http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html"). 

If it does not work then Reinstall Windows7.

---

### Post by locogrande247 on 2013-05-26
Well unfortinatly, I can't seem to get that to work, I just keep getting a window after the try & instalation screen, that says whether I want to reboot now or later, then I reboot and the whole stupid thing starts again.
If I just run windows, will it reinstall windows 7 and wipe everything else away? That seems to be my only option at this point. This laptop is really a peice of junk.

---

