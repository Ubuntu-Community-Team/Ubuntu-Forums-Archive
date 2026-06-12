---
title: "No hard drive found for installation"
date: 2019-02-09
forum: Installation &amp; Upgrades
---

### Post by flowerncsu on 2019-02-09
I'm trying to install linux on a new computer, but the installer won't identify a hard drive to install onto, despite the fact that GParted can see it just fine (see screenshot).

I do get a couple of errors when GParted starts up; in case they're useful, they are:
"Could not stat device /dev/mapper/isw: untested metadata version 1.4.01 found on /dev/sda - No such file or directory."
"Not all of the space available to /dev/sda appears to be used, you can fix the GPT to use all of the space (an extra 4544 blocks) or continue with the current setting?"

My first choice would be to install linux on sda5 (which is currently an empty partition), but I'm happy to wipe the partitions and start completely fresh instead. I'd like to dual-boot but if I can only have one OS I'd rather it be linux.

I did try to do a fresh windows install to get rid of the extraneous partitions and simplify, but the windows installer couldn't identify a drive to install to, either.

I'm also happy to test things out in the terminal if those would help. I just don't know where to start given that GParted can see the drive but the installer can't. Any suggestions?

---

### Post by yancek on 2019-02-09
The reason the installer doesn't show any options to install to is because there are none.  Your entire drive (except for about 22MB at the end of the drive) is taken up with microsoft proprietary ntfs partitions.  No Linux system can be expected to install to an ntfs partition and if it did, it wouldn't work.  If you have no data on sda5, use GParted to format it as ext4 so you can install Ubuntu there.

I would also suggest you read the Ubuntu documentation at the link below regarding installing Ubuntu on the same drive as windows 10 using UEFI, which your windows is.  

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2019-02-09
The red exclamation icon on sda2, the Microsoft reserved is normal.
But the same icon on the main c: drive sda3 is not normal. It usually means you left Windows fast start up on, but also could be that NTFS needs chkdsk or other errors.

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Use Windows to shrink a NTFS partition to make unallocated space for Ubuntu's ext4 partition. And reboot immediately after the shrink so it can run chkdsk or it may still show error. The chkdsk is required on NTFS after any resize.

---

### Post by flowerncsu on 2019-02-09
@yancek
Yes, I know linux can't be installed on an ntfs partition, but the installer usually gives you the option to reformat. Also, in previous troubleshooting, I did try manually reformatting it to ext4 using GParted. That succeeded (remained ext4 even through a reboot) but at some point in the interim windows "helpfully" put it back to ntfs. I hadn't put it back to ext4 because having the partition formatted as ext4 (or fat32, which I tried as well, because why not) didn't change the installer behavior. It still showed no drive options.

I also read over the link you provided, and I am running Ubuntu in UEFI mode, so that shouldn't be a blocker at this point.

@oldfred
Thanks for that, I'd disabled FastBoot in the BIOS but hadn't realized there was a separate FastStartup in windows. I've disabled that now (and rebooted windows to confirm that the change took, and unfortunately it made no difference. sda3 still has its red bang, and the installer still gives no drive options.

I also had already tried changing the drives directly through windows, and the disk management utility wouldn't let me change them. The options to delete, resize, and move were there in the interface when no partitions were selected, but as soon as I selected a partition, they all disappeared. I am soooooo not a windows person, so I threw my hands up and figured I'd try to repartition directly from linux. If you have any idea why it's doing that, I'm all ears.

---

### Post by oldfred on 2019-02-09
We typically do not recommend using gparted for resizing NTFS. While it normally works, when it does not users blame Linux/gparted when usually it then is just another Windows issue.
Did you run chkdsk on your Windows NTFS partition(s)? And with chkdsk you may have to run more than once as it does not fix all errors on one pass.
Any other Windows issues really should be fixed in Windows first.

Rule is:
Windows tools for Windows and Linux tools for Linux.
Windows tools will never work on Linux, but some Linux tools may work on Windows but best to use Windows tools.

Do you have good backups? And a Windows repair flash drive?

---

### Post by flowerncsu on 2019-02-09
Yep, I ran chkdsk and it didn't find any errors. I don't need a backup as this is a brand new computer (I'm really a linux-primary person; windows is "as needed to run things that don't support linux"). I did create a windows installation flash drive, so I have that. That's how I found out that the windows installer couldn't access the drive, either.

---

