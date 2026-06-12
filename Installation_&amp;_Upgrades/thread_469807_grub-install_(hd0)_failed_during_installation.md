---
title: "grub-install (hd0) failed during installation"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by toagu on 2007-06-10
Hi,
I have a AMD-64 machine with 2 SATA hard-disks of size 200 MB each (no IDE drives except the CD/DVD drive itself). WinXP is installed on the primary partition of the 1st hard disk (recognized as sda by Ubuntu LiveCD) and Ive selected 2 partitions on the 2nd hard hard disk (sdb) as "/" and "/home" respectively.

The installation (Feisty Fawn - Ive tried both CD and DVD) progresses fine till 94% (after detection of hardware etc) and fails with the error message :
[I]Error executing "grub-install (hd0)" failed. 
Fatal Error[/I]
and then the installer crashes with no other message / stack.

The target partitions remain mounted as /target and /target/home and by the looks of it - seems more or less complete. Of course, on reboot I don't get any grub and get straight booted into the XP partition.

Ive tried searching via Prof. Google - but most of the related threads are about Apple-Intel boxes :( One thread suggested checking device.map and that show hd0 mapped to sda correctly - so no issues there.

Firstly, is there anything wrong in my selected configuration (e.g. can Ubuntu be made to boot from a partition on the second hard-drive). If not, any tips on how I can resolve this problem / move ahead ?

Thanks in advance.

---

### Post by toagu on 2007-06-13
Just as an update (in case someone else comes looking) - I tried a number of things from various forums/websites and finally got it all working (in fact posting from the Ubuntu installation now :) ) ! 

Of course, having tried so many things, one can never be sure what actually did the trick, but I believe it was a combination of the following problems:

(1) Some genuine problems with the boot record on the 2nd hard disk (I formatted the entire drive eventually)

(2) My lack of awareness on handling the 2 Hard disk scenario (esp. the fact that I didn't need to disturb the MBR on the first Windows OS hard disk)
This thread helped a lot to understand those aspects:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Finally, I could only get Ubuntu installed cleanly when either only the 2nd hard drive was connected (i.e. physically disconnected the 1st Windows drive) OR when the drives were switched around (i.e. the Ubuntu drive was the 1st SATA drive and Windows one was the 2nd SATA drive).  
My original configuration did not work . However, I have both drives working, both have their respective MBRs and everything seems to be good for now (fingers xx-ed :) )

Cheers.

---

### Post by Pumalite on 2007-06-13
> **toagu said:**
> Just as an update (in case someone else comes looking) - I tried a number of things from various forums/websites and finally got it all working (in fact posting from the Ubuntu installation now :) ) ! 

Of course, having tried so many things, one can never be sure what actually did the trick, but I believe it was a combination of the following problems:

(1) Some genuine problems with the boot record on the 2nd hard disk (I formatted the entire drive eventually)

(2) My lack of awareness on handling the 2 Hard disk scenario (esp. the fact that I didn't need to disturb the MBR on the first Windows OS hard disk)
This thread helped a lot to understand those aspects:
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

Finally, I could only get Ubuntu installed cleanly when either only the 2nd hard drive was connected (i.e. physically disconnected the 1st Windows drive) OR when the drives were switched around (i.e. the Ubuntu drive was the 1st SATA drive and Windows one was the 2nd SATA drive).  
My original configuration did not work . However, I have both drives working, both have their respective MBRs and everything seems to be good for now (fingers xx-ed :) )

Cheers.

Try this:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by ub-noob on 2007-06-17
Hi,

I get the same problem, but I have only one hard drive with windows vista on it..  I created a new ext3 partition and a swap partition (2GB).  The installation halts at 94% with "Grub install (hd0) failed" error message and when I reboot, the first time, vista MBR was screwed up, the second time, it booted into windows.  In both cases, there was no indication that Ubuntu is present?

Any clue guys?

Any help will be appreciated.

Thank you.
Ram

---

### Post by merlinus on 2007-06-17
Vista does not like sharing.   Basically, you need to use vista's disk manager to create partitions, and only then use the live ubuntu cd to format them and install.

-merlin

---

### Post by ub-noob on 2007-06-18
It finally worked.  I took the suggestion from another thread here about the same problem.  I had initially set the swap partion to 2GB.  The suggestion was to keep it at 1GB or less.  I allotted 1019MB for the swap partition and voila, the installation completed without any problems.

Thanks for the help guys.

---

### Post by OzzyFrank on 2007-06-18
Posted this in a couple of posts re GRUB, so in case this is the answer you seek, am doing so again here:

Here is an excerpt from my Ubuntu ebook concerning this. Remember to replace the drive path with your own; if sharing one drive with Windows, it will be (hd0) for the whole drive or (hd0,0) for the first partition or (hd0,1) for the second partition (if Windows was there first):

Restoring GRUB

You will either need a Super GRUB Disk or your Ubuntu disc, and as long as your drive references are fine everywhere, it will only take a couple of commands to fix things. You will need to decide if GRUB is going in the MBR (master boot record of the drive) or on the partition. If Ubuntu is sharing a drive with Windows, choosing MBR will get back the GRUB menu and let you boot either. If Ubuntu is installed on another drive, and you use a boot manager to boot your partitions, then choosing to install GRUB on the partition may be better. If one doesn't work, then try the other. Simply enter the first command followed by the other. To get to the command prompt on the Super GRUB Disk, type C; to get to the grub> prompt on your Ubuntu CD, go to command line and enter the following before entering the GRUB restore commands:
grub


Restore GRUB to the Master Boot Record (eg: 1st partition on 2nd drive)

root (hd1,0)
setup (hd1)


Restore GRUB to a Partition (eg: 1st partition on 2nd drive)

root (hd1,0)
setup (hd1,0)


Note sure? Find the Partition where GRUB is

At the grub> prompt enter:
find /boot/grub/stage1

---

### Post by gingitsune on 2008-03-28
My system was flawless for 6 moths when it suddenly got a grub 'Error 17'. After ripping all my hair of I decided to reinstall using the live cd. Imagine my frustration when the 'grub-install (hd0) failed' apperared. Don't know which of the things, or a combination of them, but now I'm back on track. This is what I did:

1. A manual partition of hda. I had to delete the existing partitions (/ and swap) and recreate them, only choosing to format existing partitions wasn't enough(!).

2. Reducing the swap from 1044Mb to 999Mb.

Thx for this thread!!!

---

