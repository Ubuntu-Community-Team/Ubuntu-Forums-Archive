---
title: "URGENT - HDD not detected after failed installation :-("
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by AM_SOS on 2010-04-03
hello all !
due to virus problems i decided to create a dual boot config of windows 7 and ubuntu 9.10.
first i made a fresh installation of windows 7. strangely, there doesn't seem to be the provision of extended partition and it listed all 3 - C, D, E as primary partitions.
then when used the ubuntu installation DVD, there was not option of choosing to shrink the NTFS partition !!
there were only two choices - either install ubuntu to the entire disk or configure partitions manually.
while trying to manually configure i made some mistakes.

now, when i am trying to use the windows 7 installation to reinstall it without 9.10 for (for the time being) i dont see any hard drive partitions listed !

i have no idea how to make windows 7 installation detect the hard disk!

please help !!!
this was a friend's laptop and i had convinced him to go for ubuntu as a dual boot.

---

### Post by prodigy_ on 2010-04-03
Calm down and try booting from Ubuntu Live CD. When you're there use ```
sudo fdisk -l
``` command. It should show all hard disks and all partitions. Post the output here.

---

### Post by tommcd on 2010-04-03
You could try using a Parted Magic live CD:
[http://partedmagic.com/](http://partedmagic.com/)
Just delete all the partitions with Parted Magic. Then start over. Install Windows 7 to whatever size partition you want. Then install Ubuntu to the remaining free space.

I am pretty sure that Parted Magic can also format partitions to NTFS for Windows, though I have never used it for this purpose.

---

### Post by AM_SOS on 2010-04-03
thanks prodigy and tommcd !

you are right, i did panic a bit but this was because this was someone else's machine and the problem seemed weird on the face of it.

anyway, i sort of did the right thing - i used gparted from the 9.10 DVD and deleted all the partitions.

i was then relieved to find that the windows 7 installation was able to detect the hard drive !

so this system is now running only on windows 7 .

however, this episode has not only irritated me but made me dislike (hate!) microsoft even more. i personally use XP sometimes and its quite decent. other than the eye candy that adornes vista and 7 , i really feel that XP was simpler and easier to use.

hence, can you guys please direct me to some kind of tutorial which shows how to make a dual boot set up with windows 7 ultimate and U 9.10 ?

thanks again for the quick replies !
regards

---

### Post by tommcd on 2010-04-03
> **AM_SOS said:**
> ... can you guys please direct me to some kind of tutorial which shows how to make a dual boot set up with windows 7 ultimate and U 9.10 ?

First, a quick disclaimer from *Itchy and Twitchy LLC* (my lawyers):
I have never run Windows 7, so use my advice at your own peril ...
If you google: < ubuntu +windows 7 dual boot >
You will be presented with:
[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)
[http://www.bauer-power.net/2009/06/how-to-dual-boot-windows-7-and-ubuntu.html](http://www.bauer-power.net/2009/06/how-to-dual-boot-windows-7-and-ubuntu.html)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
... among many others. 
Since I have never run Windows 7, I can not provide any specific assistance in this matter.
From what I have read though, it seems that Windows 7 rather tenaciously guards the Master Boot Record of the hard drive. So there have been some difficulties in dual booting with Ubuntu when grub2 (or grub-legacy) takes over the MBR of the hard drive.

---

