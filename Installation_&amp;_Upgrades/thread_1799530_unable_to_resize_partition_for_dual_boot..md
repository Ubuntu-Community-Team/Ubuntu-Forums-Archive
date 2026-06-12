---
title: "unable to resize partition for dual boot."
date: 2011-07-07
forum: Installation &amp; Upgrades
---

### Post by Matrix01 on 2011-07-07
I like to install ubuntu on HP mini which has already Win7 starter.
and

was unable to resize partition from Gparted other day.
any helps?

---

### Post by oldfred on 2011-07-07
We usually suggest to shrink the windows partition from the windows MMC. Then use gparted to create new partitions.

Have you used all 4 primary partitions? Gparted often will not mount a NTFS partition that needs chkdsk, have you run chkdsk until there are no errors and defragged windows partition?

Post screen shot from gparted and/or from terminal:
```

sudo fdisk -lu
```

---

### Post by Matrix01 on 2011-07-07
this HP mini has win7 starter...
and 
i created screen shot of hard drive with Paint...
how do i post screen shot in thread?

---

### Post by Blasphemist on 2011-07-07
You can attach a screen shot using the paper clip icon here to add it as an attachment.

I to recommend starting in windows. Run defrag in windows to try and get that done as best you can. I do however think you could run defag forever without fully getting it accomplished. I'd then use ubuntu to shrink the windows partition. Use GParted to look at your partitions. As oldfred said, you may already have the maximum of 4 primary partitions. If so, likely at least one of them is a waste. For instance I had a partition that would have recovered my windows to it's original vista, as if I'd want that. :)

If you have any questions along the way, just post em back here. In the end you want to be able to have an extended partition that can have both ubuntu and a swap in it. Swap should be a little more than your memory. Ubuntu will need 5 GB plus whatever you need for documents, music, pictures, etc. Herman has a great site here for installing dual boot. [http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by Matrix01 on 2011-07-08
here's how my hard drive looks like;

[ATTACH]196990[/ATTACH]

---

### Post by Matrix01 on 2011-07-08
and....
i did defrag hard drive  for a while ago...

[ATTACH]196991[/ATTACH]

---

### Post by Matrix01 on 2011-07-08
i read Herman's Dual boot tutorial for netbook for a while ago.

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

his tutorial says delete partition, and create new one..
someone told me if partition is deleted, existing OS will be deleted.

---

### Post by Quackers on 2011-07-08
You've got 4 primary partitions on the hard drive. This is the maximum number of primary partitions allowed on an MBR partitioned disc.
In order to create another partition (or install another operating system) you will need to delete one of the primary partitions and create an extended partition in its place.
This extended partition can hold as many logical partitions as you want (almost).

Others in your position have deleted the HP TOOLS partition, for 2 reasons. Firstly the tools are unlikely to be needed. Secondly, if they are needed they can be downloaded from the HP site.

Deleting this partition won't give you enough free space for another operating system so it will still be necessary to resize the C: partition.
This should be done using the Windows Disk Management utility (as previously advised) and the partition should be defragmented first - twice is better.

Your Windows system will not disappear unless you choose to delete the C: partition :wink: or the System Reserved partition

---

### Post by Blasphemist on 2011-07-08
I agree with quakers. I will offer this though. I went through much grief trying to get win 7 to shrink its partition. Vista is less helpful. Win 7 kept having files at the end of the partition no matter how many times I defragged. I'd then look at the application log in windows, see what file was at the end, address that file (delete it or in other ways cause it to stop being used for a while) and ask windows to shrink again. And start that loop all over for a different file. I started with win 7 telling me it could give me less than 2 GB. I ended up with 30 GB, still not enough. That would leave me with much to much space unused and being hogged by win 7. I ended up using GParted to shrink win 7 the rest of the way. I then rebooted to windows, let it do its chkdsk. All was fine. 

I agree to try and use windows to change it's own partition but if that fails don't give up, use GParted. That is the only way I could get what I wanted (see screenshot) done. I left win 7 and natty where they were on the disk (sda3 and sda5). I expanded the extended partition to include the reclaimed space from win 7. I created all my new distro partitions. I deleted my swaps and created one at the end for all distro's to use. I created a data partition to use for shared data by all including win 7. All distro partitions have root mount points but you can't see that in this screenshot since they aren't mounted though I can do that at will. There are no partitions for home directories so no settings get confused.

Sorry, way more than you asked for but I got on a roll.

---

### Post by Matrix01 on 2011-07-08
thank u, 

i used MS paint, and made screen shot of hard drive,

how do u make screen shot of Gparted?
does ubuntu have software like that installed?

---

### Post by Blasphemist on 2011-07-08
Yes, there is a setting that is involved but when I press print screen or alt/printscreen the shot shows on the screen and I'm prompted to save it. If you don't see this in Ubuntu, here is a shot of the setting in natty. If you don't have this set up, what you did to paste it into paint or another app is fine too.

---

### Post by Quackers on 2011-07-08
There's also a utility called Screenshot, or Take Screenshot installed by default.

---

### Post by Matrix01 on 2011-07-08
thank u, 
will check it out

---

### Post by Matrix01 on 2011-07-08
I found 'screen shot.'

'here's how my hard drive looks like in gparted.

---

### Post by oldfred on 2011-07-08
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And win repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

Basics of partitions:
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Matrix01 on 2011-07-09
i looked hedge's tutorial for a while ago.

so
which partition do i neeed to delete?
Herman's tutorial says not to delete recovery partition because existing os may not work...

---

### Post by oldfred on 2011-07-09
Only delete the recovery if you have made the recvoery DVDs. Note that those only restore your system to as purchased, you still have to then houseclean cruft, download updates and reinstall software. It is more if you ever want to do a restore as a last case repair or if selling it.

You should be able to backup and delete the HP tools as it only has 10MB of data and supposedly can be redownloaded from HP.  See previously posted links above.

---

### Post by Matrix01 on 2011-07-13
so,
how do u back up HP Tools before delete it?

---

### Post by oldfred on 2011-07-13
You can copy it into your windows install, copy it to a USB flash drive or even just burn it to a CD to have it. I think you can download a copy from HP but I would check as I do not have an HP and never have done it.

Do you have good windows backup? And a windows repairCD. You will need to have a repair CD or liveCd for every system you install.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

---

### Post by steve11911 on 2011-07-14
There is an excellent free software for resizing partitions in windows:

Easeus-Partition-Master-Home-Edition

download link:

[http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html?tag=mncol;1](http://download.cnet.com/Easeus-Partition-Master-Home-Edition/3000-2248_4-10863346.html?tag=mncol;1)

Homepage:

[http://www.easeus.com/](http://www.easeus.com/)

---

### Post by Matrix01 on 2011-07-20
this HP mini has recovery media creation; to restore recovery partition in dvd or usb,

do window repair cd which you are talking about, and HP recovery media creation same things?

> **oldfred said:**
> You can copy it into your windows install, copy it to a USB flash drive or even just burn it to a CD to have it. I think you can download a copy from HP but I would check as I do not have an HP and never have done it.

Do you have good windows backup? And a windows repairCD. You will need to have a repair CD or liveCd for every system you install.

Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

---

### Post by oldfred on 2011-07-20
You need the vendor recovery DVDs just in case you have to do a total reinstall. It usually is just an image of the hard drive as purchased. It it not really a windows install disk.

You also need a windows repair CD.

Also In Backup and Restore centre This creates a repair CD which is different from recovery DVDs:
create system recovery disc

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

