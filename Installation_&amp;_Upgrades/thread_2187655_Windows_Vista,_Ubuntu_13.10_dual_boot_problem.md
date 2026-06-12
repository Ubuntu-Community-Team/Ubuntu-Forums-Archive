---
title: "Windows Vista, Ubuntu 13.10 dual boot problem"
date: 2013-11-13
forum: Installation &amp; Upgrades
---

### Post by jason17 on 2013-11-13
Hello All,

I am somewhat of a newbie to this kind of stuff, so I apologize if I don't provide all the necessary or correct info for my problem. On an HP g60, I reset windows vista to factory using the recovery partition. Everything worked fine. After resetting vista, I installed Ubuntu 13.10(64 bit). Btw, vista is 32 bit. After looking around for the right graphics driver, Ubuntu seems to run fine, though I have not used it extensively. However, when I try to boot into vista, it will make it to the screen with the loading bar and then reboot. This happens about 9 out of 10 times. The other time, it will boot up as it should. I have done all the things I could think of and find with google and in these forums. I tried to repair startup in windows and I think every other option that was there. I also tried updating grub. None of these things worked. I am now to the point where I am about to start over the whole process, which is quite long, namely because of windows and its updates. If someone has any idea other than the usual which has already been posted, I would greatly appreciate it. I don't think using 64 bit ubuntu and 32 bit windows should be a problem, but I could be wrong. Outside of that, it seems to me that something got modified in the wrong kind of way windows boots up. I don't know. Again, thanks. One more thing. Getting rid of windows is not really an option because it is a friend's computer.

---

### Post by fantab on 2013-11-13
I am not sure here, but it sounds like an issue with either Vista or your Hardware. How does Ubuntu run on the machine? Any Problems? Since you can see the Windows Vista Loading Bar, its not a GRUB related issue AFAIK.
Is your Vista upto date? If I were you I would let Vista run alone for a Week and if it has any issues. If all is good for a Week then I would install Ubuntu.

No, it doesn't matter if you have 32bit Vista and 64bit Ubuntu.

Get your Hardware tested or test it yourself to see if all is ok. Sometimes Bad Sectors in HDD can also cause issues similar to yours... 

Can you post a Screen-Shot of your HDD partitions from Vista, if you can, that is?
From Ubuntu post the output of:
```
sudo parted -l
sudo fdisk -l
```
Just to see if any errors are reported.

---

### Post by Mark Phelps on 2013-11-13
You didn't mention HOW you installed Ubuntu after installing Vista.  A known problem with using the Ubuntu installer to shrink Vista/Win7 OS partitions is that they can introduce filesystem corruption into the Windows OS partition.  This would make it unstable, and can possibly, render it unbootable.

A safer and more stable solution is to use ONLY the Windows Disk Management utility to shrink Vista/Win7 OS partitions.

Also, you said you ran Startup Repair for Vista, but it's not unusual for it to require three passes in order to find and fix all the problems.

---

### Post by jason17 on 2013-11-13
jeremy@Jeremy-G60:~$ sudo parted -l
[sudo] password for jeremy: 
Model: ATA TOSHIBA MK3252GS (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      32.3kB  167GB  167GB   primary   ntfs            boot
 3      167GB   309GB  143GB   extended
 5      167GB   307GB  140GB   logical   ext4
 6      307GB   309GB  2951MB  logical   linux-swap(v1)
 2      309GB   320GB  10.6GB  primary   ntfs

---

### Post by jason17 on 2013-11-13
Also, as far as how I installed ubuntu. I installed it from a usb flash drive which created the partitions.

---

### Post by fantab on 2013-11-13
Try as Mark suggest run 'startup repair' in Vista and run it three times.
Restore Vista to Factory settings and make sure its booting again. Once Vista is booting correctly we can install Ubuntu again.

Good Luck.

---

### Post by jason17 on 2013-11-16
Since my last post, I have done a few different things, including installing windows 7. Windows 7 ran fine before ubuntu install. After ubuntu install, I still have the same problems with windows 7 rebooting during startup. The windows event log points to psu or ram as the source of the problem. So I guess my question is: What could the ubuntu install change that would affect the way windows looks at the power supply, and how can I fix it? Btw, the Event id is 41 and task category is 63 in the windows event log.

---

