---
title: "Windows Install after Ubuntu?"
date: 2005-03-28
forum: Installation &amp; Upgrades
---

### Post by Recked on 2005-03-28
Hello,

I have a couple folks in my house who are resistant to change even if it is for the much, much better...Ubuntu!

Anyway, I was wondering if I can install XP after Ubuntu has already been installed on these two machines? I want to keep Ubuntu of course and want only a minimal install of XP (like there is such a thing). XP will not have any internet access.

Is this possible to do? If so, does anyone have any experience or suggestions?

Any help would be appreciated.

thanks in advance

---

### Post by Buffalo Soldier on 2005-03-28
[QUOTE=Recked]Hello,

I have a couple folks in my house who are resistant to change even if it is for the much, much better...Ubuntu!

Anyway, I was wondering if I can install XP after Ubuntu has already been installed on these two machines? I want to keep Ubuntu of course and want only a minimal install of XP (like there is such a thing). XP will not have any internet access.

Is this possible to do? If so, does anyone have any experience or suggestions?

Any help would be appreciated.

thanks in advance[/QUOTE]
I'm sorry but to my knowledge it is best to install Windows before Ubuntu or any type of Linux. Linux is more versatile in handling boot of multiple OS than Windows.

I guess it's possible to install Windows after Linux, but it's going to be messy.

---

### Post by Recked on 2005-03-28
Ok thanks for the quick response. 

I guess I will have to rebuild both machines and hope they get the hint when they can't surf or email via XP any longer!

thanks again Buffalo

---

### Post by alastair on 2005-03-28
Yes, you can install XP afterwards but look out for :

a) XP will assume it can use C: drive == /dev/hda1 (I think) - so be careful and check in the XP install that you see the right partition being used.

b) You will not be able to boot Ubuntu afterwards - until you reinstall a grub bootloader. You should be able to do this using the Ubuntu CD and "rescue"mode. You will have to add a grub stanza for XP before installing the bootloader.

---

### Post by Recked on 2005-03-28
Thanks alastair.

I think since I am new to all this that I will just do a clean install of XP and disable all internet/email functionality and then put Hoary back on.

---

### Post by bailout on 2005-03-28
It is no problem installing winxp to another partition (pri or logical), I have three XP installs on the same drive. The problem, as has been said, is that win will automatically overwrite the mbr and hence you will lose grub and won't be able to get into linux.

If you are going to wipe the drive and reinstall from scratch you might as well try the suggestion of installing win and using the rescue option to reinstall grub afterwards. I have never done so can't offer any advice but if you get it working it would be useful for others to know how. If it doesn't work then just wipe and reinstall as you are palnnign to anyway.

---

### Post by Julius on 2005-03-28
If you install windows in a partition that is not the 'first' partition in the table, window will take that partition C:\.
Let's assume that ubuntu is installed in the first partition of the table. Since windows will not recognize the ext3 file system, windows will ignore that and as I said before will take that second partition as C:\
However, if you ever format that first partition to any FS that windows can recognize, the letter will probably change, so windows will not boot, and I think it's rather difficult to make it work again :P

(From my own experience :.. :P)

---

### Post by bailout on 2005-03-28
Julius, Currently I have 1st pri-winxp; 2nd part, also pri-winxp and another winxp install on a logical part g:. So multiple win installs are certainly possible without any problems :wink: I now also have two ubuntu installs squeezed onto the disk as well. I used to have similar setups with win98 as well, although that needed a seperate bootloader.

---

### Post by Julius on 2005-03-28
I remember I had win2003 in my first partition and win xp (the OS I used) in the second one. No problems until I formatted the first partition to install linux. 
Win xp was installed in the D: partition, so when win2003 (C:\) was removed and formatted into ext3, winxp would no longer recognize D: as D:, but as C:\ (the first one) .. and changing the drive letter in windows is BAAAAAD :P
I guess you'd get similar results if you put a hard disk as slave with windows xp installed in the C:\ partition :P (providing that the master hard disk has a partition that windows can recognize) ...

---

### Post by Buffalo Soldier on 2005-03-28
A similar discussion going on at [How to REinstall WinXp and keep Ubuntu bootable](http://ubuntuforums.org/showthread.php?t=22539) thread.

---

### Post by vladuz976 on 2005-07-30
[QUOTE=Buffalo Soldier]A similar discussion going on at [How to REinstall WinXp and keep Ubuntu bootable](http://ubuntuforums.org/showthread.php?t=22539) thread.[/QUOTE]
 how would i go about installing windows on a totally different drive?   i have ubuntu on the primary master and on primary slave a storage drive. cani put a third drive on secondary master and somehow get windows on there?
how would i then edit grub so i can chose what to boot into?

thanks

---

### Post by spaznrq on 2005-11-27
*bump*

I have not yet seen the solution to this question in this and/or other threads.  I want reinstall my WinXP while keeping my perfectly working Ubuntu.  They are both on the same drive that is partitioned on my laptop.

Can anyone give me more specific instructions on what to do so that I do not screw up my Linux partition like I've done before?  Apparently, I need to reinstall WinXP, then run a "rescue" thing from the Ubuntu CD for Grub to work, and then add the WinXP option back to Grub...  A Howto on this would be really helpful, because I can see myself needing to do this over and over again in the future due to WinXP instablility/viruses/youknowtheproblems, and no, I cannot totally ditch Windows because, well, you know the reasons.

Thanks

---

### Post by romainb on 2006-07-05
*bump* again ;) 
A little late here... but
I would like to figure this out too... a nice simple how to would be good :D 
My disk is as follows: hda1-boot hda2-windows hda3-dell system restore hda4-logical hda5-linux main (ext2 or ext3 i dont remember) hda6 linux swap.
I have GRUB in my MBR and it's loading kubuntu and windows perfectly.
I want to reinstall windows because of an annoyance that I can't find the fix to.
Would booting from the kubuntu live CD and reinstalling GRUB work?
Cheers,
R. B.

PS: I could just wipe the linux partitions and reinstall linux later but i spent a week (several hours) getting my wireless card to work and I don't know how I did it... (a mix of A LOT of different HOW-TOs) so it would be nice not to have to go through that again :rolleyes:

---

### Post by Hiroshima on 2006-07-05
When working on a similar problem, I found this:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)

[https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub](https://wiki.ubuntu.com/phbc50/howtos/how-to_reinstall_grub)

Or the most comprehensive:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

