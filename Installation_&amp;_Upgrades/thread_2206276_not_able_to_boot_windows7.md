---
title: "not able to boot windows7"
date: 2014-02-18
forum: Installation &amp; Upgrades
---

### Post by sonamtobgay on 2014-02-18
Hi Everyone,

I was tryng to install UBUNTU in my pc which has windows7 installed as well. I wanted the PC to have two operating systems installed. While going through the installation process I selected the option to "Replace Windows7 with ubuntu", suddenly realising that i wanted both the OSs I cancelled the process? After this i tried to restart the PC and boot into windows 7 but it wont boot.


I have taken the snapshot of my partition info being displayed by Gparted. Hope it helps to point out what is wrong. Please help!!!

                                                                          [ATTACH=CONFIG]250458[/ATTACH]

---

### Post by Bucky Ball on 2014-02-18
Not looking promising right there. Did you have personal data on there you'd want to retrieve?

Looks exactly like an install that's been stopped half way through because your Win NTFS partitions are existing but looking empty and Ubuntu hasn't created any EXT4 partitions yet, which is where it lives. :-k

---

### Post by sonamtobgay on 2014-02-18
[SIZE=1]OMG!!! yes #BuckyBall. No hope?
[/SIZE]

---

### Post by fantab on 2014-02-18
That snapshots shows some error (round red with exclaimation mark icon)... 
Sounds to me like a file system error and/or messed up MBR..

Boot with Ubuntu DVD/USB and "Try Ubuntu without installing". Open 'Terminal' [ctrl+alt+T] and run the following command:
```
sudo ntfsfix /dev/sda1
sudo ntfsfix /dev/sda5
```
If you see any errors or warnings in the output then copy/paste the output here.

Reboot. If it boots, good. 
Do you have either Windows Install Disc or Windows Repair Diisc?


Fix Windows Boot
Try Windows Repair/Recovery.

But. as Bucky cautions, Backup your DATA.

---

### Post by Bucky Ball on 2014-02-18
Did you read all of my last post? I tend to edit a bit. ;)

Yes, I imagine there is hope, but I'm not an expert on how. There are data retrieval tools available to do this, but the most important thing is that you start posting from another computer and don't use the hard drive on the one you want to retrieve the data from. 

In simple terms, the disk space is marked as 'available to write on' but is NOT wiped out. So the data is still there ... unless you start writing data to it.

Have a look here:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

... and particularly here:

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Testdisk can resurrect your partition tables, and as fantab mentions, looks like that is the issue with the red exclamation marks. The info's there, just the MBR is a little muddled ... don't panic yet. ;)

PS: having said this, we are looking at getting your former Win setup and data back as there is very minimal chance Ubuntu would be installed if it was halted partway through, obviously enough ...

---

### Post by sonamtobgay on 2014-02-18
#fantab, Please find the output below:

ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda1
Mounting volume... OK
Processing of $MFT and $MFTMirr completed successfully.
Checking the alternate boot sector... OK
NTFS volume version is 3.1.
NTFS partition /dev/sda1 was processed successfully.
ubuntu@ubuntu:~$ sudo ntfsfix /dev/sda5
Mounting volume... ntfs_mst_post_read_fixup_warn: magic: 0x00000000  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
Record 0 has no FILE magic (0x0)
Failed to load $MFT: Input/output error
FAILED
Attempting to correct errors... ntfs_mst_post_read_fixup_warn: magic: 0x00000000  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
Record 0 has no FILE magic (0x0)
Failed to load $MFT: Input/output error
FAILED
Failed to startup volume: Input/output error
Checking for self-located MFT segment... ntfs_mst_post_read_fixup_warn: magic: 0x00000000  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
OK
ntfs_mst_post_read_fixup_warn: magic: 0x00000000  size: 1024   usa_ofs: 0  usa_count: 65535: Invalid argument
Record 0 has no FILE magic (0x0)
Failed to load $MFT: Input/output error
Volume is corrupt. You should run chkdsk.

---

### Post by sonamtobgay on 2014-02-18
I have tried the windows recovery, but no luck. :(

---

### Post by Bucky Ball on 2014-02-18
Umm ... yea. Stop using that drive and immediately download testdisk and perhaps the systemrescue disk on another computer if you want to have any hope of retrieving the data on that drive. Testdisk will put the partition table back together, NTFS, EXT or whatever. 

[http://www.sysresccd.org/SystemRescueCd_Homepage](http://www.sysresccd.org/SystemRescueCd_Homepage)

?

---

### Post by fantab on 2014-02-18
Okay
If you have Windows Repair Disc or Winows Install Disc then : [http://www.sevenforums.com/tutorials/433-disk-check.html](http://www.sevenforums.com/tutorials/433-disk-check.html)
If not find any bootable DVD which can run '[CHKDSK]("http://www.sevenforums.com/tutorials/433-disk-check.html")' for you.

Boot from Ubuntu Live DVD/USB only, don't boot from or use HDD.

---

### Post by sonamtobgay on 2014-02-18
#fantab,
I have tried the windows repair but still the problem persists. I cannot find the drives when i do the recovery(while using the command prompt). So there is no point to use CHKDSK.

---

### Post by fantab on 2014-02-18
'Recovery' is not working probably because of the filesystem error. Windows '[Repair]("http://www.sevenforums.com/tutorials/668-system-recovery-options.html")' is different.

---

### Post by sonamtobgay on 2014-02-18
I booted using UBUNTU linux.

---

### Post by sonamtobgay on 2014-02-18
I booted from UBUNTU live USB.

---

### Post by sonamtobgay on 2014-02-18
I have tried the ['repair]("http://www.sevenforums.com/tutorials/668-system-recovery-options.html")' as well.

---

### Post by Bucky Ball on 2014-02-18
Okay, I'm giving this one more try and seeing if you notice me. If you need further details, look at my other posts on this thread. You need to use testdisk, or something like it, to put the partition table back together. There is probably nothing wrong with the MBR or anything else and you probably don't need to use Win repair, chdsk and all that. The partitions have been marked as 'writeable'. You need to rebuild the partition table, with something like testdisk, and that partition table should still be there, ASAP. 

I've provided links previously. If you continue to tweak and screw with this drive you will drastically lessen the chances of retrieving your data. Good luck.

You stopped the Ubuntu install part-way through so it looks like it didn't have a chance to write anything, including writing over the Win partitions (or there would be NOOOO sign of NTFS partitions ANYWHERE).

---

### Post by sonamtobgay on 2014-02-18
Hey thanks #Bucky Ball. It worked at last. Sorry for ignoring the details. Thanks again!! :)

---

