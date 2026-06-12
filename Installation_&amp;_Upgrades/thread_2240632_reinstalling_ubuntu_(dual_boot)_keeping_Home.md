---
title: "reinstalling ubuntu (dual boot) keeping Home"
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by o0larry0o on 2014-08-21
Hi,

I'm Having some troubles reinstalling Ubuntu 14.04.
Here the situation :

I have a dual boot with Ubuntu LTS 14.04 and Ubuntu Studio LTS 14.04 (EFI booting)
For both Install the / is on a SSD, and var tmp and home are on another drive in separate partitions.

What I want to do is reinstall Ubuntu, and keep my /home. I don't want to touch Ubuntu Studio

When I boot with ubuntu live and access the installation menu It detects properly both ubuntu install, but I don't have the "reinstall" option.

[[IMG]http://img11.hostingpics.net/thumbs/mini_710342installtype.png[/IMG]]("http://www.hostingpics.net/viewer.php?id=710342installtype.png")

And if i choose "something else" I cannot check the format option for any partition, and I cannot set the mount point for any partition ...
well basicaly the only thing I can do is delete the partitions and recreate them to achieve what I want, and I don't want to do that ...

[[IMG]http://img4.hostingpics.net/thumbs/mini_370794format.png[/IMG]]("http://www.hostingpics.net/viewer.php?id=370794format.png")

I'm kinda lost here, and some help would be greatly appreciated.

Thx a lot

---

### Post by grahammechanical on 2014-08-21
Some have reported that using the option to Upgrade an existing install of Ubuntu using the live session does not only re-format the selected partition but the entire hard disk. So, be glad that you cannot use that method

Are you saying that at the Installation Type screen after you have selected the partition and clicked Change the Edit Partition dialog does not allow you to change "Use As" from "Do Not Use" to "Ext4 file system?" The little down arrow shows that the panel is a drop down menu. It is logical that we cannot set a mount point for or set to format a partition if we have not first selected a file system for that partition.

Regards.

---

### Post by yancek on 2014-08-21
> And if i choose "something else" I cannot check the format option for any partition,

Do you mean when you click the down arrow to the right of Use as it doesn't offer you filesystem types?  I don't see the Mount point option either.  Did you verify the download with an md5check?

---

### Post by oldfred on 2014-08-21
With Something Else you should be able to click on the change button and get this screen. I am overwritting old installs, if you have a separate /home you also need to mount it but be sure NOT to format it. DO NOT tick the format box. It will find swap automatically.

Be sure you have booted installer in UEFI boot mode.
       Shows install with screen shots for both BIOS(purple) & UEFI(grub menu), so you know which you are using.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Just ignore all the Windows steps, but follow the Something Else steps:
      
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

I prefer to have entire system including /home (the part with hidden settings) on my SSD so system is fast. But have all data on hard drive as data is accessed less often. I use 25GB for / and use 11GB of that for install. My /home is 2GB but that is only because I have .wine and that is 1.5GB in /home.

---

### Post by o0larry0o on 2014-08-22
Okay so in my understanding of the 3 previous post, the first 2 one are different from the last one...

If I understand correctly Grahammechanical and Yancek it's normal that I can't edit the mount point, and to answer your question yes, I can change the "USE AS" and I can set the filesystem, but then when should I specify the mount point ??

Oldfred, I'm booting my live sessions in UEFI (grub menu), but on the opposite of you're screenshots, the partition editor shows what is on my partition / but when I hit change, I dont have the same window as you do, see my screen shot, I can only set the filesystem and that's it

---

### Post by o0larry0o on 2014-08-22
Okay i m ****ing stupid,  i just needed to set ext4 filesystem and then i can set the mout point and choose fornat or not .....

sorry for my dumbiness ......

One more thing, concerning the / partition, ive read somewhere that i should format it, and somewhere else that i should not.... so what should i do ?

---

### Post by oldfred on 2014-08-22
Usually we recommend formatting /, but if you have /home inside /, then you can not format it. Either way all new files are written. If not reformatted any old files that are not part of a new install would not be overwritten which would preserve your data.

Not sure then if all the accumulated log files, old .deb and others that you should be housecleaning and almost no one does houseclean are also kept. Then you fill up / faster unless you do the housekeeping.

 Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

              RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

