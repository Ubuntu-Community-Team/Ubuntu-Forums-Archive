---
title: "Problems with MBR, Win 7, Ubuntu and two hard disks"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by SushiBoiNL on 2009-12-07
Hi Guys

Have searched the forums but not found an answer specifically for my needs. I am quite technical, but fairly new to Linux, MBR, adding hard drives etc. however I can normally figure out  everything using Google, but thought I would get an expert opinion before mucking about and making things worse!

I have:

Windows 7 RC installed on one hard drive, but my MBR appears to be on the other hard drive.

I want:

Windows 7 RC and Ubuntu 9.10, preferably one per hard-drive, with the second hard drive containing Ubuntu in one partition, with the other parition for my data (Main Data D:) which will be used by both Ubuntu and Windows 7.

I used to have one WD hard disk with Win XP installed. A few months ago I bought a new Samsung 1TB hard disk, removed XP and added Win 7 RC, subsequently attempted an installation of Ubuntu 9.04. However, when adding the new hard disk, it got added as the first hard disk, not the second one. Never added a hard disk before so this is probably why. 

Currently I'm guessing that my MBR is on the 1st hard disk, with win 7 on the second hard disk. See attached screenshots. I would like to replace the partition (S:) with Ubuntu 9.10, however, it appears that this partition may contain my MBR.

Also, the last time around when installing linux it asked me where I wanted to install GRUB to and got confused, can't remember which option I chose.

Currently when booting, if I select the first hard disk which is the new samsung disk I added, Win 7 boots. If I select the second hard disk I get a grub error 22. Ubuntu is not installed.

Please advise what the easiest way is to get this resolved, hopefully without repartitioning everything and reinstalling win 7 then linux.

Ultimately, just to summarise:

I want win 7 RC on the smaller hard drive (Currently the second hard drive which is the smaller one) and Ubuntu on the larger hard drive (Currently not installed, but want it installed on the partition S, with the other partition to have data which both Ubuntu and Win 7 can access). Please see screenshots.

Please help!

Thank you

Cheers

---

### Post by darkod on 2009-12-07
OK, first of all, all hard drives have a MBR. Master Boot Record. That's usually like the first sector. What you are referring to is the windows bootloader. Easy test would be this, unplug the big drive and see if Win7 boots. If it boots, then its bootloader is on its drive.

If it doesn't boot, we'll deal with that.

---

### Post by presence1960 on 2009-12-07
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by SushiBoiNL on 2009-12-07
First of all, thanks for taking the time to reply. Hopefully I won't frustrate you very much ;)


@darkod: Unplugged my Samsung 1TB drive, then switched on. Got Grub Error 21 on bootup (I think it was error 21, may have been 22), so no joy there, no Windows 7. 

Also, why does the partition (S:) show as 100% free, but have 125 MB taken up?

Originally, I had Disk 1 as Disk 0, would swopping the plugs in my computer make a difference and screw up my boot?

@presence1960: Here we go!

```
============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #3 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 148. But according to the info from fdisk, 
                       sda5 starts at sector 92213248.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /Boot/BCD

sdb2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x1fa738b5

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    92,213,099    92,213,037   7 HPFS/NTFS
/dev/sda2          92,213,100   390,716,864   298,503,765   5 Extended
/dev/sda5          92,213,248   390,713,343   298,500,096   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x15f267e8

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             63    78,140,159    78,140,097   7 HPFS/NTFS
/dev/sdb2          78,140,160 1,953,520,064 1,875,379,905   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="844414094414009A" LABEL="Windows" TYPE="ntfs" 
/dev/sda5: UUID="400E33EE0E33DC1A" LABEL="Backup" TYPE="ntfs" 
/dev/sdb1: UUID="34829C591AE6A24C" LABEL="" TYPE="ntfs" 
/dev/sdb2: UUID="B288B97C88B94021" LABEL="Main Data" TYPE="ntfs" 

=============================== "mount" output: ===============================

aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type tmpfs (rw,mode=0755)
/dev/sr0 on /cdrom type iso9660 (rw)
/dev/loop0 on /rofs type squashfs (rw)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)

```

---

### Post by darkod on 2009-12-07
OK, first a very IMPORTANT question: Did you install ubuntu by clicking wubi.exe in windows? Is it a wubi installation or ubuntu dual boot installation?

Because you don't seem to have ubuntu ext3/ext4 partition at all. It's either wubi inside windows on ntfs or you've lost your ubuntu partition.

---

### Post by SushiBoiNL on 2009-12-07
Definitely not WUBI, it was an attempted dual boot of Ubuntu 9.04/Mint 7 with Win 7 RC, which didn't work, I think just Ubuntu worked back then (might have been Ubuntu 9.04, or Linux Mint 7, can't remember it was a while ago) (suspect GRUB was installed to wrong disk) so I eventually had to repair my Windows bootup using the Win 7 disk and erased the Ubuntu partition then I think ik. This is the reason I am now asking for help as I probably would otherwise make the same mistake and end up with Win 7 no longer booting nor Linux.

Does that help?

---

### Post by darkod on 2009-12-07
Well if you deleted the ubuntu partition then, and also the linux mint, because you don't seem to have any linux right now. As long as you're aware of that, that's fine.

Looking at the results file, can you tell where your Win7 is? You have part of the boot files on /dev/sda1 and part of them on /dev/sdb1. Where is it actually?

---

### Post by darkod on 2009-12-07
Here is what I would do:
/dev/sda is your 200GB disk
/dev/sdb is your 1TB disk
The 200GB disk seems to have 50GB unallocated space at the end.
The 1TB disk has almost nothing unallocated.

You said you prefer not to reinstall any OS and not to repartition.

Depending where is your Win7 system partition, I would reinstall the windows bootloader to the MBR of that drive using the win7 dvd and the Repair This Computer process. Then check if win7 is booting and working fine.

If you don't want to repartition, the only solution to install Ubuntu 9.10 is on the unallocated 50GB on the 200GB disk. Maybe your win7 is also there, but if you want ubuntu on the 1TB drive you have to do something about the partitions. It should be quite easy to install in the 50GB on the 200GB disk.

---

### Post by SushiBoiNL on 2009-12-07
Well I would imagine that Win 7 is installed to sdb. I am currently backing up everything tonight and am going to try and install ubuntu 9.10 tomorrow to sda. The plan is to delete the partition (S:) using Gparted, then let Ubuntu install guided - select largest continous free space, which should install it to that partition. Not sure about where Grub should be installed to, sda or sdb?

Can anyone please advise if what I am doing is correct, and where GRUB should be installed to. Have done this previously before and mucked things up, had to reinstall Win 7 as well which I'm not too keen on doing of course.

Also, is there anyway to fix my MBR of both hard drives, as I have a feeling that they both contain the windows bootloader, is this correct? Thanks!

---

### Post by darkod on 2009-12-07
> **SushiBoiNL said:**
> Well I would imagine that Win 7 is installed to sdb. I am currently backing up everything tonight and am going to try and install ubuntu 9.10 tomorrow to sda. The plan is to delete the partition Steffie (S:) using Gparted, then let Ubuntu install guided - select largest continous free space, which should install it to that partition. Not sure about where Grub should be installed to, sda or sdb?

Can anyone please advise if what I am doing is correct, and where GRUB should be installed to. Have done this previously before and mucked things up, had to reinstall Win 7 as well which I'm not too keen on doing of course.

Also, is there anyway to fix my MBR of both hard drives, as I have a feeling that they both contain the windows bootloader, is this correct? Thanks!

Yes, it should be OK like that. Delete that partition if that what you want and let Ubuntu use that unallocated space that will be created. That will be on disk /dev/sda so you definitely want grub2 on /dev/sda too. Check this on the last step of the installer (before clicking Install) on the Advanced button.

But before starting to install ubuntu, set the 200GB disk as first in boot order and use the win7 dvd to repair the win7 boot process. Windows wants its disk to be "main" that's why set it first in boot order. After you repair the boot process and check that win7 is working fine, make the 1TB disk first in boot order again and proceed with installing ubuntu. It should detect your repaired win7 automatically and you shouldn't have any problems to boot both of them.

---

### Post by SushiBoiNL on 2009-12-07
Just realised I made a mistake, Windows 7 is on sda (200GB), and the partition I am installing Linux to is on sdb (1TB). Does that make a difference?

Is GRUB always installed to the same hard disk that Ubuntu is installed to, in this case sdb?

So what I do is set the 200GB disk (sda) as first in boot order, use win 7 DVD to repair the win7 boot process, then set the 1TB disk (sdb) first and install Ubuntu and GRUB to sdb. Afterwards, which disk should I set as first in boot? Any why do I need to set the 1TB disk as first when installing Ubuntu?

Sorry for it being so complicated, and thank you for helping!

---

### Post by darkod on 2009-12-07
> **SushiBoiNL said:**
> 
So what I do is set the 200GB disk (sda) as first in boot order, use win 7 DVD to repair the win7 boot process, then set the 1TB disk (sdb) first and install Ubuntu and GRUB to sdb. Afterwards, which disk should I set as first in boot? Any why do I need to set the 1TB disk as first when installing Ubuntu?

Sorry for it being so complicated, and thank you for helping!

Yes, exactly as you said. You need to put sda first before repairing win7 because windows requires that. You do not have to set sdb first necessarily before installing ubuntu but it's better because that disk will remain first afterwards. Grub2 will get installed on sdb as you said (double check during install as I explained), and grub2 is the bootloader that can boot both win7 and ubuntu. So you want it first in the boot order, and why not make it first before installing ubuntu just in case. It will help grub2 recognize disk1 and disk2 properly.

---

### Post by SushiBoiNL on 2009-12-08
One last question hopefully,

So I have backed up my data and am ready to delete the empty partition (S:) to make free space for Linux, however Disk Management shows that it has 100% free space, but right-clicking and going to Properties shows that there is 125MB of space used (see attached screenshots in first post). I am reluctant to delete this partition as I am not sure if that 125MB used is necessary for Windows 7. Is there a way that I can confirm this?

Thanks for taking the time to answer
Cheers

---

### Post by darkod on 2009-12-08
Only you can know that. I wouldn't say it has data important for win7 boot process, but it might have data important to you. Open it in win7 (or the LiveCD) and see what's there.
Don't get worried about showing 100% empty, I guess 125MB is so small compared to the whole partition size that it's less then 1% so it can't show even 99% empty.

You worry too much man. :) Just look inside and you'll see what's there.

---

### Post by SushiBoiNL on 2009-12-08
When browsing the partition with Windows 7 I see nothing, when using Ubuntu off the Live CD, I see quite a few files and folders (see screenshot) is it still safe to delete this partition? I presume when fixing the boot up of Win 7 these files will be recreated on the other disk?

---

### Post by darkod on 2009-12-08
> **SushiBoiNL said:**
> When browsing the partition with Windows 7 I see nothing, when using Ubuntu off the Live CD, I see quite a few files and folders (see screenshot) is it still safe to delete this partition? I presume when fixing the boot up of Win 7 these files will be recreated on the other disk?

Yeap, these are the boot files that shouldn't be here. Remember we said you have part of the files on one disk and the other part on the other. The repair will sort that out. Just make sure the 200GB is first in boot order before repairing win7 as we discussed.

---

### Post by SushiBoiNL on 2009-12-08
Having problems,

This is what I did:

- Booted GParted LIVE CD, deleted the partition S:
- Restarted and set the 200GB drive to first
- Then restarted and choose to boot from DVD, booted up the win 7 disk and choose repair startup, it then appeared to fix the problem and restart

However now nothing is working. 
When I try and boot off the 200GB drive I get still get Grub Error 22
To make matters worse, when I try and boot off the 1TB drive I get Disk Boot Failure, Insert System Disk and Press Enter

So It appears that Win 7 did not repair the MBR of the 200GB drive. What am I doing wrong and how can I then fix the MBR of the 200GB drive to startup Windows 7?

---

### Post by darkod on 2009-12-08
> **SushiBoiNL said:**
> Having problems,

This is what I did:

- Booted GParted LIVE CD, deleted the partition Steffie S:
- Restarted and set the 200GB drive to first
- Then restarted and choose to boot from DVD, booted up the win 7 disk and choose repair startup, it then appeared to fix the problem and restart

However now nothing is working. 
When I try and boot off the 200GB drive I get still get Grub Error 22
To make matters worse, when I try and boot off the 1TB drive I get Disk Boot Failure, Insert System Disk and Press Enter

So It appears that Win 7 did not repair the MBR of the 200GB drive. What am I doing wrong and how can I then fix the MBR of the 200GB drive to startup Windows 7?

It should have repaired it. Try disconnecting the 1TB drive and leave just the 200GB drive plugged in. That way it will have to write the MBR there. If it shows grub error on the 200GB disc there is still grub remains there, not windows bootloader.

---

### Post by SushiBoiNL on 2009-12-08
With the 1TB drive unplugged I managed to repair my 200GB and start up Windows 7, great stuff!

Then proceeded to plug back in the 1TB drive and make it the first in boot up, then installed Linux to the partition S (this partition had been deleted and is now free space). In Linux I choose the option install to largest continous free space, I thought I had set GRUB to install to the correct disk, and linux went ahead and installed.

Now when I went to try and use my computer, back to everything not working again. So have had to unplug the 1TB drive, repair my 200GB drive so that win 7 is working again. Linux appears to be installed on the 1TB drive but GRUB appears to have been installed to the wrong place.

Also, I read an article that if Linux is installed to a secondary drive, GRUB needs to be installed to MBR? Is that the reason why I am having problems?

Article: [http://linux.ioerror.us/2006/01/where-should-you-install-grub/](http://linux.ioerror.us/2006/01/where-should-you-install-grub/)


So is there an easy way to reinstall GRUB, or do I need to delete the partition and reinstall Ubuntu. Also, what option exactly do I choose when installing GRUB,it had default of hd0 or something like that.


Thanks for your help!

---

### Post by SushiBoiNL on 2009-12-08
Well I must have done something right because I fixed the 200GB drive and Windows 7 RC boots up again. I then plugged the 1TB drive back in again and tried booting off it, and got GRUB. So really not sure what happened there but its all working now.

Thank you very much for your help. I'll start tinkering around tomorrow and hopefully it will still be working by then!

---

### Post by darkod on 2009-12-08
> **SushiBoiNL said:**
> I thought I had set GRUB to install to the correct disk, and linux went ahead and installed.


You really have to make sure you check grub2 is installed to the correct drive.

OK, you repaired Win7 again and it's working. Now boot again with the ubuntu cd, open terminal and execute:
sudo fdisk -l

Copy the result here and I'll tell you how to install grub2 correctly to your 1TB drive.

PS. OK, I just saw your last post. All seems fine. Enjoy it now.

---

### Post by SushiBoiNL on 2009-12-13
Great, everything still working fine. Thanks very much for your help Darko!

---

