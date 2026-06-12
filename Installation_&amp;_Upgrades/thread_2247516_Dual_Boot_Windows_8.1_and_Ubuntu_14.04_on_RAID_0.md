---
title: "Dual Boot Windows 8.1 and Ubuntu 14.04 on RAID 0"
date: 2014-10-08
forum: Installation &amp; Upgrades
---

### Post by Noelson on 2014-10-08
Hello.

I just ordered a new laptop (MSI GT72 Dom Pro) and while I'm eagerly waiting for it to get here, I am trying to figure out a way to install Ubuntu 14.04 on it.

It comes with 4x SSDs in a RAID0 setup and Windows 8.1 installed.

The thing is that during the last few years, the only reason I go on windows is mainly gaming or when I need to code in Visual Studio. For everything else I use Ubuntu. However this is the first time I will have a system with a raid setup and I'm fearing issues with the installation. I've had no experience with this UEFI thing or RAID before but I wouldn't say I'm a novice Ubuntu user.

Any directions about how I should do this?

One more thing, the laptop also has an extra 1TB HDD for data storage. Is there a way that I can backup the entire RAID0 array onto that disk (total raid size is 512GB) to be able to restore it in case of a failure?

Thanks in advance!

---

### Post by oldfred on 2014-10-08
With 4 SSD in RAID 0, I would expect it to be very fast. But you have a higher risk of failure as if any drive fails you lose all your data.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

I do not know much about RAID and then whether you have BIOS RAID which is called 'fakeRAID' as it is not hardware based. 

The only other MSI system I have seen:

 MSI gaming laptop [SOLVED] Dual Boot Ubuntu 14.04 & Windows 8, Ubuntu won't boot
[http://ubuntuforums.org/showthread.php?t=2218742](http://ubuntuforums.org/showthread.php?t=2218742)

Some others with dual SSD:
EFI dualboot Ubuntu 12.04 and Windows 8 in Raid0 on Sony Vaio S dual SSD
[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)
      acer aspire s7 Dual SSD RAID - [SOLVED] Installed Ubuntu on Pre- UEFI Win 
[http://ubuntuforums.org/showthread.php?t=2240043](http://ubuntuforums.org/showthread.php?t=2240043)
Acer Aspire S7 can't install ubuntu - UltraBook erased RAID meta-data
[http://ubuntuforums.org/showthread.php?t=2121187](http://ubuntuforums.org/showthread.php?t=2121187)

---

### Post by Noelson on 2014-10-08
Thank you, oldfred.

The truth is that considering the system will come pre-built like this, I am willing to take the risk and find out how fast it can be. Also thanks to miracles like git and dropbox, all my important stuff are on cloud storage and in case of a complete disaster, I will only have to reinstall OSes and programs.

Also that is why I am also looking to see if there is a way to create an image of the whole dual boot raid on the extra HDD, in case I need to do a system restore.

As for the raid type, I believe it is in fact bios setup RAID and not pure hardware.

---

### Post by oldfred on 2014-10-08
I think your backup is the same, it just is different drivers required to mount and manage RAID partitions over standard partitions. 

You may not be able to use Desktop installer also. With 12.04 there was an alternative installer that included the RAID & LVM drivers. They discontinued the alternative installer and said they would include RAID & LVM in the standard Desktop installer. I now see LVM, but not RAID as a choice, although some with the Intel SRT which looks like RAID (or is RAID) is now seen by the installer, but grub then may not install correctly. Or not fully implemented for RAID yet.

You may have to use server installer and then add desktop of your choice which ends up as same thing.

You also need to review a lot of the UEFI info. The install is a lot different than the old BIOS type installs and usually requires UEFI/BIOS settings & Windows setting changes to let install work correctly.

---

### Post by Michael_McKenney on 2014-10-08
Laptop with 4 hard drives in RAID 0.  Sounds risky.   The power hiccups and you lose one drive for a split second.  I would verify the RAID controller can handle four SSD drives in RAID properly.  Many RAID controller have problems because of the speed of the SSD drives.

---

### Post by Noelson on 2014-10-09
> **Michael_McKenney said:**
> Laptop with 4 hard drives in RAID 0.  Sounds risky.   The power hiccups and you lose one drive for a split second.  I would verify the RAID controller can handle four SSD drives in RAID properly.  Many RAID controller have problems because of the speed of the SSD drives.

I am sure MSI has tested and taken care of all that or they would not ship the machine like that. As for the power hiccups, doesnt the battery take care of that?

---

### Post by oldfred on 2014-10-09
Battery should help.

But we regularly get users who start some task that turns out to take longer and did not plug in laptop and battery runs out and they want help in recovering data. So just make sure battery has power and that you have good backup procedures.

---

### Post by Noelson on 2014-10-12
After further communication with the retailer, it looks like I will have the laptop on Tuesday... Let's see what happens when I give this a shot... Do you think it's better to install Server right away or go with the desktop and install Boot Repair?

---

### Post by oldfred on 2014-10-12
Do not know enough about how well desktop currently would work with your configuration.

Also be very careful of this bug and only use Something Else if using Desktop installer.
 Have not recently used server but do not remember any auto install options.

       Reinstall says overwrite Ubuntu but it also erases existing Windows. 
Sept 2014 Fix being released for one drive installs, but mulitple drive installs must use Something Else.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1265192)

Also with standard installs we suggest only using Windows to shrink Windows but not create new partitions. But with RAID not sure what works as gparted has not been configured to work with RAID.

      Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)

            User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

---

### Post by Noelson on 2014-10-13
Thank you very much for your effort and time spent to help me. I will read all of these and take a shot tomorrow (hopefully) when I have the laptop in my hands.

---

### Post by Noelson on 2014-10-16
Alright so I got the laptop, its an amazing machine... I shrank the raid array, made space for ubuntu and began fighting to install 14.04 alongside windows with UEFI dual boot.

Turns out the desktop iso didnt work no matter what I tried... I was getting the "??? ???" error on the beginning of the installation and I believe it is because of the lack of raid drivers. Installing mdadm and using --assemble --scan did not help and the problem persisted.

After several hours, I managed to setup the server version. That would hang after loading swap because of some GPU issues which i quickly resolved by googling the errors I got. I finally managed to get the uefi boot loader working, giving me the option to log on both windows and ubuntu using the following link:

[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)

Thanks for all your help. It pointed me towards the right direction. I now hope for two things: My raid0 not failing and the ubuntu desktop installer to include raid drivers at some point by default...

---

### Post by oldfred on 2014-10-16
Glad you got it working. :)

Good auto regular backups then become important. But they should be for any user.

---

### Post by Noelson on 2014-10-17
After a big bunch of windows updates today, the bootloader was reset to windows. Boot-repair though made it very easy for me to restore grub. The great thing is that even if GRUB fails, I can still boot into either system by specifying the appropriate raid partition in the BIOS (UEFI)!

On another note, I still have not found a way to backup the whole raid array with both OSes on it...

---

### Post by oldfred on 2014-10-17
I do not know RAID. But if backing up just to another drive would it not be the same as any backup?

Windows users have recommended these as with Windows you typically need an image.

 The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

      
 discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[https://help.ubuntu.com/community/CategoryBackupRecovery](https://help.ubuntu.com/community/CategoryBackupRecovery)
[http://ubuntuforums.org/showthread.php?t=2236636](http://ubuntuforums.org/showthread.php?t=2236636)
If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

Since I can easily re-install Ubuntu, I backup the things that I have changed and I use rsync, but may change to rdiff.
      
 Oldfred's list of stuff to backup May 2011 (still current):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)

      
 Discussion of issues on rsycn bash file &  rdiff-backup  - TheFu
[http://ubuntuforums.org/showthread.php?t=2224428](http://ubuntuforums.org/showthread.php?t=2224428)
[http://www.kirya.net/articles/backups-using-rdiff-backup/](http://www.kirya.net/articles/backups-using-rdiff-backup/)
Sample rdiff file by TheFu
[http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880](http://ubuntuforums.org/showthread.php?t=2200427&p=12911880#post12911880)
[http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use](http://blog.jdpfu.com/2013/10/20/rdiff-backup-real-use)

---

### Post by darren22 on 2015-03-02
Hello, I have simillar system configuration. 3x SSD in RAID 0 with Win 8 preinstaled. Could you tell me how did you solve your problem, please.

---

