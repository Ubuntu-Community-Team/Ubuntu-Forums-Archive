---
title: "Can not install to USB 2.0 HD drive"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by Helion on 2006-07-06
Hi.
I tryed to install Ubuntu 6.06 from a CD I made from the ISO download to my
USB 2.0 120G HD. But after partitioning the USB drive it tries to install the
OS but stops and says "Error installing Sysytem". 
My computer is a new Gateway P4 3.20Ghz system with windows XP home on
the internal drive (200gig sata) and 1Gig of RAM.
The external drive is connected to the computers USB port and the computer
is configured to boot from USB.
I am new to linux and am somewhat lost. Can anyone help me?
Thanks in advance.

:confused: :(

---

### Post by rcarring on 2006-07-06
It won't work that way, and the reason it won't work because you have disk on disk on your usb drive. I expect when you bought it it was already partitioned into one drive and made fat32, since fat32 does not support any partition bigger than 32GB the manufacturer uses a cludge to get it to work. 

So the reason it has problems installing is because it is like installing on a volume on the hard disk not the actual hard disk itself.

Suggest you download vmware-player and the latest appliance and upgrade to Dapper that way, using the alternate cd and adding a floppy disk drive device to get the network support to work.

---

### Post by nolongerlivecd on 2006-07-06
From what rcarring said, I think it would be safe for you to completely repartition your external hard disk, using some Windows based system. I did that, creating a seperate partition for my 40GB.

Space  Type    Mount           Use
4GB     ext3     /                    Root
0.5GB  swap    /swap?          Swap
5GB     FAT32  /media/sda2 Windows Portable Apps
30GB   FAT32  /media/sda1 Data

---

### Post by Helion on 2006-07-06
[QUOTE=nolongerlivecd]From what rcarring said, I think it would be safe for you to completely repartition your external hard disk, using some Windows based system. I did that, creating a seperate partition for my 40GB.

Space  Type    Mount           Use
4GB     ext3     /                    Root
0.5GB  swap    /swap?          Swap
5GB     FAT32  /media/sda2 Windows Portable Apps
30GB   FAT32  /media/sda1 Data[/QUOTE]

Hi, Nolongerlivecd.
I don't quite understand why I need a FAT32 partition on the USB hard drive.
The USB drive has no Windows OS on it. Windows is on the internal SATA
drive only. I did use Partitionmagic 8 to delete all partitioning on the USB drive
so that Linux could do a clean partitioning it self. 
I did look at the USB drive with PM 8 and Linux had partitioned it right.
Only the OS doesn't copy over.
I have attached a screen grab of MP8. Drive 2 is the Linux partitioned USB hard drive.
Thanks for all your help.

---

### Post by flip314 on 2006-07-06
[QUOTE=rcarring]It won't work that way, and the reason it won't work because you have disk on disk on your usb drive. I expect when you bought it it was already partitioned into one drive and made fat32, since fat32 does not support any partition bigger than 32GB the manufacturer uses a cludge to get it to work. [/QUOTE]

The maximum volume size on FAT32 is 2TB.  Windows XP and Windows 2000 can only create FAT32 volumes up to 32GB in size, which has created the misconception that that's the actual limit.

---

### Post by s3ppel on 2006-07-07
> **Helion said:**
> 
I did look at the USB drive with PM 8 and Linux had partitioned it right.
Only the OS doesn't copy over.
I have attached a screen grab of MP8. Drive 2 is the Linux partitioned USB hard drive.


The screen shot looks all right... making just one huge partiton and one swap space might not be the best idea, but should work. (You might search this forum to see how to best partition, i.e. one extra patiotion for /home maybe...)

However, your partitions look functional in the attaches screenshot. It even says 3300 MB used space. How comes that?

What I suppose is the following:
- The OS did copy over
- Grub (the boot manager) didn't install, so you cannot boot linux.

The boot manager (if installed succesfully) would come up on boot and would ask you wether you want to start Windows or Ubuntu.

So to clear things up, I would like to know: are you trying to install from the live CD? If so, maybe using the "alternate install CD" would work, as it offers more options on the Grub installation.

---

### Post by Helion on 2006-07-07
> **s3ppel said:**
> The screen shot looks all right... making just one huge partiton and one swap space might not be the best idea, but should work. (You might search this forum to see how to best partition, i.e. one extra patiotion for /home maybe...)

However, your partitions look functional in the attaches screenshot. It even says 3300 MB used space. How comes that?

What I suppose is the following:
- The OS did copy over
- Grub (the boot manager) didn't install, so you cannot boot linux.

The boot manager (if installed succesfully) would come up on boot and would ask you wether you want to start Windows or Ubuntu.

So to clear things up, I would like to know: are you trying to install from the live CD? If so, maybe using the "alternate install CD" would work, as it offers more options on the Grub installation.


Yes, I got the "alternate CD". It partitioned the drive and
started installing the OS to it. It worked on it for some time,
then the screen showed two vertical rectangles, one at the very left of the screen and one in the center. Then it stopped working
and just sat there forever. 
I was forced to reboot. After reboot windows booted not linux.
I set my system to try to boot the USB drive first then the internal HD (windows XP).
It allways goes to windows, never to Linux.
I am rely disapointed. I ecpected LINUX to be much easier to handle then windows. I guess I was wrong.
I will keep trying, I don't give up easely.

](*,)

---

### Post by Helion on 2006-07-07
SUCCESS!!!!!!!   :) :D 

I got Ubuntu installed on my USB HD. I used the "alternate" CD and made one
chage to my system settings.
Before the initial bootup to the install CD I went into my System Settings <F2> and changed the following:

Max CPUID value limit       <ENABLE>

This setting is needed for "Legacy OSes" that do not support CPUID functions.

That's all it took. Now I am a happy Linux user.
I hope this will help others to resolve some of their problems too.
For reference, my system is:
Gateway P4 HT 3.20Ghz  1Gig RAM  200Gig SATA HD (Windows XP Home)  
                                 120Gig USB HD (Ubuntu Desktop Linux)

. . .

---

