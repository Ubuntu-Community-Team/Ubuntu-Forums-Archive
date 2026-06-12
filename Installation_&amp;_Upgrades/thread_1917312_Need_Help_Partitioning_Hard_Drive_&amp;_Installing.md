---
title: "Need Help Partitioning Hard Drive &amp; Installing Windows 7"
date: 2012-01-29
forum: Installation &amp; Upgrades
---

### Post by belliot2 on 2012-01-29
Hi,

I just built a new computer yesterday and installed Ubuntu on it. I now want to partition the hard drive so I can run either Ubuntu or Windows 7 on it. My hard drive is 1TB so space isn't really an issue as this is a brand new computer. I'm a computer science major and I can get Windows 7 (download, not the disc) for free thanks to the college.

I've never used a dual-boot before so I want to make sure I get this right. Can anyone instruct me on how to go about this??

Thanks

---

### Post by kevdog on 2012-01-29
Its actually very easy.

You need to install windows first then windows 7.  I usually like to do this two separate hard-drives, but you don't have to -- the reason is that if one of OS dies (like during a future upgrade) you don't bork the other. 

You'll neep to partition your drive.  At a minimum you'll need a boot partition, a Ubuntu partition and Windows partition.  I usually add two additional partitions for my Ubuntu installs, /home and /swap, however this is not mandatory.  

You also need to think about the journaling system you are going to use.  Windows uses ntfs which Ubuntu can read and write to.  New versions of Ubuntu want to install ext4 by default, however I'd think about doing ext3 partitions so Windows could read and write to the Ubuntu partition with help from an external program such as ext2fs for windows.  If this isn't important to you, then don't worry about it.

I usually use the stand alone Gparted OS (can be run directly from a CD) to partition my discs.  I usually download the iso file and burn it to disk, and then boot from cd, allow the OS to detect my hard drive(s), and partition at will.  I then would install windows, and finally Ubuntu.

---

### Post by belliot2 on 2012-01-29
> You need to install windows first then windows 7.

I'm not quite sure what you mean by that. Right now I have only Ubuntu on the hard drive. I'm trying to add Windows 7 in addition to Ubuntu

---

### Post by allenb.bigal on 2012-01-30
I'm in a similar situation to Belliot2 but a little different.

I've just purchased a new notebook that has W7 on it and I'm trying to just run the live CD of U 11.10 and I damned if I can get it to run.
I got the DVD from a mag and burned the .iso file to CD as instructed. When the CD starts to load, it goes through heaps of crap on the screen and then eventually goes into a loop with a message that I haven't written down. I have to get out of it with CTR/ALT/DEL.
I have always thought that to use the live option to see how it works that all I have to do is boot the .iso file.
Anybody got any ideas of what might be wrong?

---

### Post by varunendra on 2012-01-31
First off, welcome to the forums *belliot2 *:)

> **kevdog said:**
> You need to install windows first then windows 7.
> **belliot2 said:**
> I'm not quite sure what you mean by that.
I couldn't understand either.. perhaps kevdog was lost in something else while typing this (like I do when I'm tired or too sleepy..) ;)
> **kevdog said:**
> **At a minimum **you'll need a boot partition, a Ubuntu partition and Windows partition.
Nope! When you really mean 'Minimum..' it'd be 2 in OP's case - One for win7, One for Ubuntu (everything in '/', including 'swap' as a file).
> **kevdog said:**
> however I'd think about doing ext3 partitions so Windows could read and write to the Ubuntu partition with help from an external program such as ext2fs for windows..these applications can also read ext4 without problems (assuming them ext2/ext3 partitions). As a matter of fact, I have all my linux partitions on all of my internal and external drives formatted as ext4 (I don't use any other) besides swap. The installed [Ext2Fsd]("http://sourceforge.net/projects/ext2fsd/") lists them as ext3, and I can both read and write to them.


@*belliot2 ,*
I think the easiest and most straightforward way is to just install Win7 first, let it do with the partitions whatever it wants to do, afterwards install Ubuntu in a separate partition (and swap in another one). But if you want to keep the current Ubuntu installation, that's not a problem either. You can do it as follows:

[LIST=1]
[*]boot with Ubuntu live cd, and run gparted
[*]Assuming you have no more than three primary partitions on the drive, create one more primary ntfs partition for Win7, in the beginning if possible without moving the existing ones. _For win7, it has to be a primary partition_.
[*]label this new ntfs partition for easy recognition, when installing win7. [COLOR=Red]Also, right-click on this partition > click "Manage Flags" > check (tick) the "boot" checkbox to set it 'active'.[/COLOR] [COLOR=Red]*(thanks to oldfred for the heads up)*[/COLOR]
[*]now reboot with Win7 dvd this time, and choose the newly created partition for installation
[*]when the installation is finished, boot win7 to see if it works correctly (I am a little bit doubtful because if the win7 partition is not in the beginning, it 'may' refuse to boot correctly)
[*]If win7 works, reboot with Ubuntu live cd (same one from which you have installed it) and follow [this quick guide to restore grub]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2") on MBR to be able to boot already existing Ubuntu again.
[*]After correctly reinstalling grub, reboot into installed Ubuntu, and run **sudo update-grub** to let it recognize and add win7 to its boot menu.
[/LIST]
If you have any confusions, please boot with live cd, run gparted and post its screenshot while it is showing the target hard disk layout.




@*allenb.bigal,*
Your problem is clearly different than *belliot2's*, so please post your question in a separate thread of your own. You can then post its link here so we can follow.

---

### Post by LinuxBill on 2012-01-31
> @*belliot2 ,*
I think the easiest and most straightforward way is to just install Win7  first, let it do with the partitions whatever it wants to do,  afterwards install Ubuntu in a separate partition (and swap in another  one). But if you want to keep the current Ubuntu installation, that's  not a problem either. You can do it as follows:

[LIST=1]
[*]boot with Ubuntu live cd, and run gparted
[*]Assuming you have no more than three primary partitions on the  drive, create one more primary ntfs partition for Win7, in the beginning  if possible without moving the existing ones. _For win7, it has to be a primary partition_.
[*]label this new ntfs partition for easy recognition, when installing win7
[*]now reboot with Win7 dvd this time, and choose the newly created partition for installation
[*]when the installation is finished, boot win7 to see if it works  correctly (I am a little bit doubtful because if the win7 partition is  not in the beginning, it 'may' refuse to boot correctly)
[*]If win7 works, reboot with Ubuntu live cd (same one from which you have installed it) and follow [this quick guide to restore grub]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2") on MBR to be able to boot already existing Ubuntu again.
[*]After correctly reinstalling grub, reboot into installed Ubuntu, and run **sudo update-grub** to let it recognize and add win7 to its boot menu.
[/LIST]
If you have any confusions, please boot with live cd, run gparted  and post its screenshot while it is showing the target hard disk layout.Great post. 

Good post but i agree had trouble getting it working before when Ubuntu was running before the win7 install. If its just a new install i would boot Ubuntu live cd. Wipe the whole drive and start from there installing windows first. Then create a couple of other partitions for Ubuntu and swap in disk utility in windows. Live CD and install Ubuntu. 

Job Done. 

William

---

### Post by oldfred on 2012-01-31
+1 varunendra's info
Just one addition. Windows only sees active partitions for install, repairs or boot, or in gparted you have to see boot flag on for the NTFS primary partition that you want to install to:

Some more info, but it is so easy just to reinstall the MBR from a liveCD, that you do not have to use dd to backup MBR:
[https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu]("https://help.ubuntu.com/community/WindowsDualBoot#Installing%20Windows%20After%20Ubuntu")

---

