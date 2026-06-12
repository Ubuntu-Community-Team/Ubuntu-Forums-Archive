---
title: "Messed up repartitioning during first-time Ubuntu Installation."
date: 2014-08-21
forum: Installation &amp; Upgrades
---

### Post by sang-gyegmx.de on 2014-08-21
Hi,

I am trying to install Ubuntu alongside Windows 7 on an ASUS Eee PC Netbook. I created a bootable USB and managed to boot from there. Following the instructions here: [http://askubuntu.com/questions/6328/how-do-i-install-ubuntu](http://askubuntu.com/questions/6328/how-do-i-install-ubuntu), which discouraged to use the automatic installer, I followed the following instructions: [http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation). In particular the sub-section "If you have disk that contains Windows installed". 

However, the first difference was that I had two loaders (it looked somewhat like this, not sure that I remember all the details, I have marked ? where I am not sure)
[TABLE="width: 1000"]
[TR]
[TD]Device[/TD]
[TD]Type[/TD]
[TD]Mount Point[/TD]
[TD]Format?[/TD]
[TD]Size[/TD]
[TD]Used[/TD]
[TD]System[/TD]
[/TR]
[TR]
[TD]/dev/sda1[/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD][/TD]
[TD]107374 MB[/TD]
[TD]37606 MB[/TD]
[TD]Windows 7 (loader)[/TD]
[/TR]
[TR]
[TD]/dev/sda2[/TD]
[TD]fat32[/TD]
[TD][/TD]
[TD][/TD]
[TD]196574 MB[/TD]
[TD]11782 MB[/TD]
[TD]Windows Recovery Environment (loader)[/TD]
[/TR]
[TR]
[TD]/dev/sda3[/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD][/TD]
[TD]not sure it 
was the biggest partition[/TD]
[TD]93 MB[/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda4[/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD]16MB? [/TD]
[TD]unknown?[/TD]
[TD][/TD]
[/TR]
[/TABLE]


I proceeded as instructed, choose sda3, reduced it to 60% to 118000 MB. I also set the mountpoint to /windows and from not use to ntsf. I chose not to format the drive. Then I hit ok .... darn, b/c instead of free space I ended up with unusable, pressed revert. This is what I have now:

[TABLE="width: 1000"]
[TR]
[TD]Device[/TD]
[TD]Type[/TD]
[TD]Mount point[/TD]
[TD]Format[/TD]
[TD]Size[/TD]
[TD]Used[/TD]
[TD]System[/TD]
[/TR]
[TR]
[TD]/dev/sda[/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda1[/TD]
[TD]ntfs[/TD]
[TD][/TD]
[TD][/TD]
[TD]107374 MB[/TD]
[TD]37605 MB[/TD]
[TD]Windows 7 (loader)[/TD]
[/TR]
[TR]
[TD]/dev/sda2[/TD]
[TD]fat32[/TD]
[TD][/TD]
[TD][/TD]
[TD]16106 MB[/TD]
[TD]11782 MB[/TD]
[TD]Windows Recovery Environment (loader)[/TD]
[/TR]
[TR]
[TD]/dev/sda3[/TD]
[TD]ntfs[/TD]
[TD]/windows[/TD]
[TD][/TD]
[TD]118000 MB[/TD]
[TD]93[/TD]
[TD]MB[/TD]
[/TR]
[TR]
[TD]unusable[/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD]78574 MB[/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]/dev/sda4[/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD]16 MB[/TD]
[TD]unknown[/TD]
[TD][/TD]
[/TR]
[/TABLE]


How can I save the machine and the installation. (No, I don't have a backup and I did not create a restore point, although, it's not a problem to set it back to factory settings, if that's the only path).
For you suggestions, please bear in mind that I am absolutely new at this .... I will probably need more step-by-step instructions


Also, could I/should I further reduce the loader partitions, they seem pretty big in comparison to what's actually used (Windows 7 loader, at least). 

[I found an entry that suggests that the issue arose b/c I have too many partitions (4 being the max), what do I need to delete, how can I reassign the unusable space to free space?]

Thanks so much for your help
[TABLE]
[TR]
[TD="class: answercell"][/TD]
[/TR]
[/TABLE]

---

### Post by TheFu on 2014-08-21
Please run the **boot-info** script from a liveCD boot of ubuntu. This will gather the real information and post it online for us to review. Links for boot-info in my signature.

Oh - and it isn't that we don't believe you , but ... I don't believe you. ;)  Seeing the actual output from the script means we don't have to guess and huge mistakes won't be made, by accident.

Really, I'm extremely concerned that you are attempting this without a backup. What happens is the "factory restore" partition is wiped? Do you have the OS on a DVD somewhere?

---

### Post by roger_1960 on 2014-08-21
Hi

Suggest you look at this thread [http://ubuntuforums.org/showthread.php?t=2049797&p=12210385#post12210385](http://ubuntuforums.org/showthread.php?t=2049797&p=12210385#post12210385) inparticular posts #4 and my post #7.  It relates to the same issue with very similar hardware.  I believe the problem is that the OP is trying to have more than 4 primary partitions.

Roger

---

### Post by sang-gyegmx.de on 2014-08-21
Thank you, Roger .... that makes sense, shouldn't have repartitioned here. What do you suggest I do now? Would a system reset put me back on a level playing field and I could start the suggested process? 
And the process would mean deleting sda4 before attempting to install ubuntu, is that right?

Sang-gye

---

### Post by sang-gyegmx.de on 2014-08-21
oh and ... this machine doesn't have a CD or DVD drive ... some of the steps that are suggested require creating a back-up CD of Windows. Does a 16 gig thumbdrive work, instead?

---

### Post by sang-gyegmx.de on 2014-08-21
Hi The Fu,  thank you for your reply. I thought I replied earlier, but can't see that post. 
I don't a live CD boot of ubuntu. I created a thumb drive ... does that have the same features? Thanks for pointing out the safety issue. I am about to create a bootable windows 7 usb stick as we speak.

---

### Post by sang-gyegmx.de on 2014-08-21
I tried system restore, but that doesn't seem to have touched the partitions ... fudge.

---

### Post by oldfred on 2014-08-21
I think these all are basically the same instructions:
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB](http://www.winhelp.us/create-a-recovery-drive-in-windows-8.html#USB)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

Some links on full backups of Windows:

 Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Do not attempt to create partitions with Windows as it will convert to Windows proprietary dynamic partitions which do not work with Linux.

As suggested by TheFu best to see details from BootInfo report. Just post link it gives you.

      
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by sang-gyegmx.de on 2014-08-21
Thank you, everybody .... I just took the 'easy way out'. Created a (hopefully bootable windows 7 usb) and proceeded to just install Ubuntu, with the automatic partition option, but without encryption of the home directory. It starts up, it looks nice, but the keyboard doesn't work .... fudge. I had hoped this would be simpler .... Any suggestions for this this one. Google didn't bring much up, except a bug report from 2013 ...36 experienced the bug ....

---

### Post by sang-gyegmx.de on 2014-08-21
Oldfred, just out of curiosity: there seems to be a conflict: you say I should NOT attempt to partition with Windows, but the link you recommend ([http://ubuntuforums.org/showthread.p...0#post12611710]("http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710") -like so many others I've read) says I should not try anything BUT windows to repartition. Am I misunderstanding?

---

### Post by Mark Phelps on 2014-08-21
Since you cited my thread ... let me respond.  You should use ONLY Windows utilities (the Windows Disk Management, or Windows-based partitioning tools) to resize Windows OS partitions for Windows Vista or newer OS installs.  Why? Because, sometimes, using GParted or the Ubuntu installer, to shrink such OS partitions results in filesystem corruption -- which is very hard to fix because you can't then reboot into Windows to run CHKDSK.

As to resizing and/or partitioning Linux filesystem partitions, using GParted works just fine.

---

### Post by sang-gyegmx.de on 2014-08-21
Thanks Mark, too late now. I obviously followed the wrong instructions. ... Wouldn't it be a good idea to take down 'How to's' such as this? If I understand you correctly the installation procedure promoted here is not feasible.

[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)


???

---

### Post by oldfred on 2014-08-21
Posts like that are just from users like us. 
And we have had many users say it does work as they did not have any issues, but many others say they have issues.

I think many of the issues are because a user has pre-existing issues (sometimes not even known) in Windows and resizing does not help.
But if Windows has issues after using Linux, they always blame Linux, so better to follow the rule of using Windows tools for  Windows and Linux tools for Linux. Then at least if there are issues it was not caused by the other system.

---

### Post by yancek on 2014-08-21
Changing/shrinking a windows partition usually works better from windows.  Changing Linux partitions works better from Linux.  You can use windows to create a partition on which to put Linux but you will need to use Linux to create a filesystem/format it as a default windows system doesn't even recognize a Linux filesystem, usually showing it as unallocated or free space.

---

### Post by sang-gyegmx.de on 2014-08-21
Thank you, everybody .... your support was much appreciated. I think (wonders over wonders ....) my installation is up and running now. Without windows.

---

