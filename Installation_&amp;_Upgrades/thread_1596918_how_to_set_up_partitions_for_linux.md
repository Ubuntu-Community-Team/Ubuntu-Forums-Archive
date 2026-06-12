---
title: "how to set up partitions for linux?"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by FiveStarSky on 2010-10-14
Hey everyone, I made 2 partitions in windows xp (40gigs for xp, the other 200gigs or so for linx)

I've tried installing linux numerous times, but can never get it to find the partition to install to. 

Is there a special way you have to set up a partition so you can install linux on it?

---

### Post by Zimmer on 2010-10-14
A bit of reading is recommended, which may give you a clue as to where your problem lies.
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

[https://help.ubuntu.com/community/DrivesAndPartitions](https://help.ubuntu.com/community/DrivesAndPartitions)

Steps you should have taken are

1. Resize the Windows partition (taking note of how to do that safely) creating some unallocated space.
2. Use Gparted ( from the Live CD) to partition and format the unallocated space ready for Linux in a manner of your choosing..
3 Install Linux to the prepared partition (taking care where you install the GRUB boot loader.
See here for some specific examples and tips.

[http://members.iinet.net.au/~herman546/index.html](http://members.iinet.net.au/~herman546/index.html)

---

### Post by FiveStarSky on 2010-10-14
alright, i get to the Gparted part, but even there, i does not find the free unalofaked (or whatever big word it is) space on the hard drive i had set aside, all it shows is my 4gig flash drive that i'm using to boot off of. (netbook does not have a cd/dvd drive.)

---

### Post by rjs987 on 2010-10-14
> **FiveStarSky said:**
> Hey everyone, I made 2 partitions in windows xp (40gigs for xp, the other 200gigs or so for linx)

I've tried installing linux numerous times, but can never get it to find the partition to install to. 

Is there a special way you have to set up a partition so you can install linux on it?

Since you mention you want one of the partitions you made to be for Linux I would suggest using gparted to delete that 200GB partition and let the Linux install create what it needs in there. The install should find unallocated space. If not, you should have the option to manually pick the unallocated space on the disk. Unallocated means that there is no partition defined. Windows XP doesn't know how to define a partition specifically for Linux so it's best to leave or set the space unallocated before the install.

---

### Post by FiveStarSky on 2010-10-14
^ impossible, When i get to the Gparted screen, it does not show anything other than the flash drive i'm booting off of. So i cant access my hard drive at all right now.

EDIT: i open Gparted, and the only partition it finds is /dev/sdal which is mky 4gig flash drive i'm using to boot linux up (used pendrivelinux)

EDIT2: i don't care about running windows xp at all, is there anyway i can wipe windows off the hard drive and see if i can get linux to install then?

---

### Post by rjs987 on 2010-10-14
In the upper right corner of gparted there should be a volume select drop down that will allow you to choose a different disk than the flash drive. By default gparted will display the disk you started the program on. You have to choose a different disk using the chooser. An alternate method is to click on the GParted menu, then Devices, and then choose the device/hard disk you want to manage. You may have to refresh devices after starting gparted.

If you want to remove Windows altogether you should be able to do that also in gparted by deleting all partitions. Then the Linux install should find a blank disk to do with as it needs/wants. I've used gparted to do this many times. Once in a while I will get an error. To fix that you must run chkdsk /x in a Windows command prompt and then restart the computer twice after the chkdsk runs. Then gparted should be able to delete all partitions.

---

### Post by FiveStarSky on 2010-10-14
once again, the ONLY drive i'm allowed to access on Gparted is the Flash drive, the drop down has no other options (even after refreshing, reloading adn all that good stuff)

It can not find the hard drive, the windows, or the other partition

---

### Post by oldfred on 2010-10-14
Even though I could boot XP on sda, gparted would search for a long time and then not show sda. I went back and ran chkdsk on the NTFS partition and gparted showed sda.

Try chkdsk on your windows drive.

---

### Post by FiveStarSky on 2010-10-14
i'm sorry, i'm not familiar with 'chkdsk' could you give me a little more detail of how to do that?

---

### Post by rjs987 on 2010-10-14
Start Windows.
Open a command prompt window or click Start>Run and type "cmd" and click OK.
In the command prompt window type the following command at the prompt if your Windows disk is formatted as NTFS:
```
chkdsk /x
```

If your Windows partition is not NTFS - or if you don't know what it is then use this command:
```
chkdsk /f
```

The command will likely result in a message asking you if you want to run it at the next restart. Type 'y' there and press ENTER. Then restart the computer. It will run check disk for some time and should fix any errors found. When finished the computer will continue to start up to Windows. Do another restart. Then one more restart. Then start the computer with the flash drive and try gparted again. You should be able to see and choose the hard disk.

---

### Post by FiveStarSky on 2010-10-14
alright cool, i'll give all that a shot.

---

### Post by FiveStarSky on 2010-10-14
nope, that didn't work, any other ideas?

---

### Post by rjs987 on 2010-10-15
It seems that there is something else going on with this hard disk or computer system.
Is there any encryption on it?
Is there a setting in BIOS to lock it? (though I would expect gparted to see at least).
Can you give any details about your hardware. Model numbers/names, cpu, hard disk type (SCSI, IDE, SATA, etc.).
It is also possible that the disk is bad, but I would think gparted would still at least see it in this case too.

There is one other idea that I almost forgot about. I've had computers that when started up with a flash drive the hard disk was unavailable. This actually is more likely what is happening. Can you start up with a live CD? If so, run gparted from that.
Post 2 of this thread actually states that in step 2 of the steps to take.

---

### Post by oldfred on 2010-10-15
Is BIOS even seeing the drive? Do you have BIOS set for IDE compatibility mode?

---

### Post by dmp2010 on 2010-10-15
Just create one partition for Windows. Leave other unallocated. Linux will guide you to install it on the unallocated space.

---

### Post by rjs987 on 2010-10-16
Just to be sure I understand your situation correctly. 

Your Windows partion works fine (i.e.: you are able to start Windows and use it ok)?
And you would prefer to install Ubuntu in the unused partition if possible or just use the whole disk otherwise?

Since you cannot see the hard disk when starting from a live flash drive of Ubuntu I suggest you use a live CD instead. You should then be able to see the disk, and delete the unused partion (the one Windows is not on) using gparted. Then the Ubuntu install should see and offer to use the unallocated space to install to, or another option that should be given on the same seletion screen is to use the whole disk for Ubuntu if that is preferred.

I don't know where to go from here if you cannot see the hard disk even with the live CD. I would need to know details of your hardware to even start to think on it.

Hope this helps.

---

