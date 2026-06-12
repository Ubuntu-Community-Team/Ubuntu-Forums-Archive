---
title: "Trouble with Windows 7 dual boot"
date: 2009-11-28
forum: Installation &amp; Upgrades
---

### Post by mt1234 on 2009-11-28
I have an HP Pavilion dv4t with Windows 7 64-bit preinstalled. I only have a recovery disk for it, not the installation DVD. I setup a dual boot after reading several threads on this forum. Here is what I did:

[LIST=1]
[*]Defragged the hard drive.
[*]Used Windows Disk Management tool to shrink the main Win7 partition.
[*]Installed Karmic 64-bit in the free space using the "Install along side ... to allow dual booting" option (not an exact quote;))
[/LIST]
My problem is that when I tried booting into Windows the first few times it went into a check disk screen. The first few times it got hung up on that screen. One time it finally performed the check. Everything seems to be working fine now, but based on another thread I fear that this problem may come back. 

It seems (again from another thread) that my problem might be that Windows 7 has a Recover partition that is at the back of the disk. One person had difficulty fully removing this partition, so I'd rather not do that. Another person suggested moving this partition to be immediately following the main Windows 7 partition. 

Windows Disk Management doesn't seem to offer a move command. Others have warned against modifying Windows partitions with tools other than Disk Management. 

If the issue rears its ugly head again, I plan on using gparted to move the Recovery partition to be immediately following the main Windows 7 partition (I've never done anything like that before). Then I assume GRUB2 will be confused at that point. Will I need to reinstall Ubuntu or can I just run update-grub and have everything automagically work perfectly again? ;)

---

### Post by darkod on 2009-11-28
Unless some Win7 problem start showing, don't worry about the check disk. This is normal for windows if partition resizing was done, regardless which tool you used.
In fact, in your list what you did I would add one more step before installing Ubuntu:
3. Boot windows (any version) few times and do the disk checks if asked, to let windows sort itself out after the shrink.

---

### Post by phillw on 2009-11-28
+1 darkod - You NEED to have your Win area booting happily after you have done a re-size - just leave the proposed Ubuntu area as un-allocated. And, yes, it can take a few boots for Win to settle down.

Regards,

Phill.

---

### Post by mt1234 on 2009-11-28
Now I'm having trouble booting into Ubuntu since Windows has started booting properly. Why is that do you think? Did the check disk that Windows performed affect GRUB2?

---

### Post by darkod on 2009-11-28
It might. That's why the checks are recommended before you start ubuntu installation. You can reinstall Grub2 to remove that doubt if you want to. Or just try
sudo update-grub

as first step.

---

### Post by mt1234 on 2009-11-28
Do you think that I'm bound to have to move the Windows Recovery partition at some point in the future? If so, maybe I should do that now, rather than later when I have the system personalized.

---

### Post by mt1234 on 2009-11-28
If I move the partitions using gparted, can I keep the Ubuntu partitions? Or, will I have to reinstall? If I can keep them, then do I just reinstall GRUB2 after the move?

---

### Post by darkod on 2009-11-28
You don't want my opinion for those recovery/utility partitions. :)
My opinion is: delete them as soon as you get your computer. :)
Most of them are used not to REPAIR your windows installation but to RESTORE the computer to FACTORY STATE!!! That means deleting the whole HDD, and creating one (or maybe two) partition on it, and put an image of windows as it was when you bought the computer.
So even if you don't dual boot with linux, that process will DESTROY ALL YOUR DATA!!! What do you need it for then?
Of course, if you dual boot it destroys the data and the other OS too.
Not giving you proper windows installation media they are making this choice tough for you. Otherwise it would be really simple. In my personal opinion, ask Microsoft and the shop for windows OS media that you paid for. If they don't give you what you deserve, use any copy you can find, you already have your license.

Windows media would allow you to just repair or reinstall windows without losing all of your data. Regrdless whether you have linux too or not.

---

### Post by darkod on 2009-11-28
> **mt1234 said:**
> If I move the partitions using gparted, can I keep the Ubuntu partitions? Or, will I have to reinstall? If I can keep them, then do I just reinstall GRUB2 after the move?

Don't touch the partitions for now. Reinstall Grub2 with item number 12 from here:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

See if that helps.

---

### Post by mt1234 on 2009-11-28
Thanks Darkod. So far the sudo grub-update seems to have worked. If I continue to have problems I'll reinstall GRUB2 per your link.

Thanks for the info on the Recovery partition. For now I'd like to keep it. Given that, do you think I'm asking for trouble by not moving the Recovery partition? Or is there a chance I will continue on just fine with it where it is?

---

### Post by oldfred on 2009-11-28
Some HPs have an issue with Grub2. Grub2 is larger than the windows boot loader and old grub. HP decided to write a bit of data for secuity in the MBR and it can overwrite part of grub2.

HP protect tools write into MBR
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)

If you have made a copy of your recovery partition, I agree with darko that you do not need the recovery partition. If you want just to repair your windows there is a repair only CD available.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista Recovery Disc 
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by darkod on 2009-11-28
Until you start having problems, leave it alone as it is. After all, if it's problematic I guess it would already start giving you headaches. :)

---

### Post by mt1234 on 2009-12-04
Everything seems to be working well. Thanks again!

---

