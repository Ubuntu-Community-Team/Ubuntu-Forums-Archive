---
title: "Is there a SIMPLE way to install on a different hard drive and change boot load order"
date: 2011-07-29
forum: Installation &amp; Upgrades
---

### Post by gbswales on 2011-07-29
When I run Ubuntu 11.04 live from USB I can see all of my hard drives.  However when I try to install I see only drive 0 (this drive has two partitions that I need to leave exactly as they are) - I want to install it on a spare empty 60GB SATA drive in my computer drive 3, which I had renamed "ubuntu", but cannot find a simple way of forcing Ubuntu to install there rather than on drive 0.  Is Ubuntu more likely to see it if I delete its existing partition and set up a different type of partition on the spare drive?

The overall install is very good but there are options I would like in the install interface

1. the above - select any partition on any drive in the computer as the linux system drive
2. the option to select the boot order for dual boot system (ie maybe boot windows by default) and/or
3. related to that the option to force loader to wait for user input before booting into any system

thanks

---

### Post by walt.smith1960 on 2011-07-29
I use a 3rd party boot and partition manager.  It'll recognize OSs on different partitions and different drives and enable me to boot whichever OS I choose.  I assume there's a way to do what you want in GRUB but I'm not familiar.  The way to insure you don't mess up your other disk would be to simply open your machine and unplug the disk you don't want touched and plug in the disk you want to install to.  The trick then would be to have both disks plugged in and have GRUB recognize all the bootable partitions.

---

### Post by YesWeCan on 2011-07-29
> **gbswales said:**
> Is Ubuntu more likely to see it if I delete its existing partition and set up a different type of partition on the spare drive?
I had a disk that had been used in a Windows RAID once. The Ubuntu installer could not see it at all - as if it were not connected. But a running Ubuntu saw it and could mount it. It turned out that I had to remove the RAID metadata from the disk.
[COLOR="Navy"]sudo dmraid -E -r /dev/sdx[/COLOR] (substitute x for your 60GB drive's letter)

This wasted a lot of my time trying to track down so I am not enamoured with the Ubuntu installer.
Also, for folks who are new to linux I recommend disconnecting other HDs while they install Ubuntu: the installer defaults to putting the Grub MBR code on sda even if Ubuntu is being installed on a different disk!

> The overall install is very good but there are options I would like in the install interface

1. the above - select any partition on any drive in the computer as the linux system drive
2. the option to select the boot order for dual boot system (ie maybe boot windows by default) and/or
3. related to that the option to force loader to wait for user input before booting into any system

Obviously. I think it does cater for 1 already except when it doesn't and doesn't tell you why. ;)
There are many improvements the installer and the Grub system need.

---

### Post by YesWeCan on 2011-07-29
> **walt.smith1960 said:**
> The way to insure you don't mess up your other disk would be to simply open your machine and unplug the disk you don't want touched and plug in the disk you want to install to.  The trick then would be to have both disks plugged in and have GRUB recognize all the bootable partitions.
Agreed. After reconnecting all disks, the command [COLOR="Navy"]sudo update-grub[/COLOR] will sniff out all the OS's and add them to the Grub boot menu. Mostly.

Which loader do you use?

---

### Post by walt.smith1960 on 2011-07-29
> **YesWeCan said:**
> Agreed. After reconnecting all disks, the command [COLOR=Navy]sudo update-grub[/COLOR] will sniff out all the OS's and add them to the Grub boot menu. Mostly.

Which loader do you use?

I'm using something I first got when i wanted to run multiple Windows installs.  It's shareware from a company called Terabyteunlimited.  I'm sure it doesn't do anything that other software won't do but I had it before i discovered Ubuntu and the price wasn't too bad considering.  Its partition management has a couple neat tricks.  You can also choose which partitions each OS "sees" which can be handy.  If you google terabyteunlimited you'll find it.  I was once accused of spamming so don't want to post a direct link.  There are a couple things to be aware of if you choose to try it. 

One is if you choose to go beyond 4 primary partitions. you're limited to using their software for partition manipulation. it creates an "extended Master Boot Record" which is proprietary.  Second is when installing Ubuntu or other Linux distros using GRUB, GRUB needs to go into the partition, not into the MBR of the hard disk.  That will overwrite the EMBR and you won't be able to choose OSs. You can restore BootitBM but it's an unnecessary PITA.   Also, the trial mode is crippled - some functions are disabled.

---

