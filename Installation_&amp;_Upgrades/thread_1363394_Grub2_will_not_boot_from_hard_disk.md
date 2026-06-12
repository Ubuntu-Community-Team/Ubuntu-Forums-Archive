---
title: "Grub2 will not boot from hard disk"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by wkinney on 2009-12-24
I installed Ubuntu9.10 from CD. System is an hp p6230f with AMD 64b quad running Windows7. When booting, do not get menu or grub command line. Must use CD to boot. Using CD, I get option to boot from disk, and that works OK. I have run "Boot info script" as directed in the forum.  Results.txt is attached.

Please review Results.txt and tell me how to fix grub2.

I am a newbie to forums. I apologize if this post is not up to snuff.

Thanks

---

### Post by oldfred on 2009-12-24
If you can boot from the CD you install must be ok and it is the copy of grub that is the issue. I would try reinstalling grub first. Their is a small bug in grub that if grub is one one drive sda and the install is on another sdb your grub menu will take 20-30 seconds longer to appear. If you want to install grub to sdb and in BIOS make your sdb drive 1000GB the boot drive it will boot slightly faster. You could before switching drives install the windows boot to sda so in the future if you ever have a problem with sdb you just have to switch drives again to boot windows. I like having different operating systems on each drive and that system set up in the MBR of that drive. Since grub/Ubuntu is better at choosing which to boot I make it the first to boot.

First boot into Ubuntu and run this to install grub to sdb - it will give you a choice of which drive to install to:
sudo dpkg-reconfigure grub-pc 

You could switch drives and make sure it boots. If you then desire you could switch back and use your windows CD/DVD to reinstall windows boot to the sda drive.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

I am not sure grub has found the correct entries to boot windows? Windows will normally combine boots into one so grub can only find the one and then windows gives you the choice of which windows to boot. 
You have the 100mb boot partition for a new install of win7 but the boot flag is on the win7 main install partition not the boot partition. I think the boot flag needs to be on the 100mb  partition.

---

### Post by wkinney on 2009-12-24
I tried "sudo dpkg-reconfigure grub-pc " and put grub in the MBR of both disks. I also changed the BIOS boot sequence to sdb first. The system still does not boot without the CD. It gives the message "Reboot and Select proper Boot device". So it seems to not find either hard drive. The new Results2.txt file is attached.

---

### Post by oldfred on 2009-12-24
Maybe someone else can see something, I do not. Your grub in both MBR seem to point to the correct partition and you are able to boot when using the cd so install seems ok.

It seems very strange that you get no messages or at least the grub rescue command.

We have seen where windows can corrupt a grub2 MBR. Some installs do not take but first time but on reinstall work. Old raid can prevent install, but installing, looking correct from the script and not working is beyond me.

---

### Post by oldfred on 2009-12-24
Have you booted into windows before booting grub and does you HD have any of the HP protect tools?

HP laptop (nc6400) have HP protecttools and HP recovery manager installer that mess with the MBR. 
[https://bugs.launchpad.net/ubuntu/+s...b2/+bug/441941](https://bugs.launchpad.net/ubuntu/+s...b2/+bug/441941) 

and another users comments on HP tools
I have a Compaq netbook -- HP product. Turns out they have HP Recovery tools that will overwrite parts of the MBR. The thing is, I uninstalled every single piece of their recovery software, sync software, etc, cuz I didn't want any of that crap. I went into services, and lo-and -behold -- there was the hpqwmiex service running. So I disabled it, did the update-grub thing again, logged into Windows then back into Ubuntu, and all is well!

---

### Post by presence1960 on 2009-12-25
I would try reinstalling GRUB2 from the Live Cd. Boot the Live CD/USB, choose "try ubuntu without any changes". When desktop loads open a terminal and run ```
sudo mount /dev/sdb1 /mnt
```
This will mount your Ubuntu / partition. 

next run in terminal ```
sudo grub-install --root-directory=/mnt/ /dev/sdb
```

Reboot and go into BIOS and make sure your sdb disk (1 TB) is set to first in hard disk boot order. Save changes to CMOS and continue booting & see what happens.

---

### Post by wkinney on 2009-12-28
I've read the info in the link given in message #5. This seems somewhat different from my problem. My boot message to "Select proper Boot Device" seems to indicate that the boot process is not recognizing either hard disk.

I reinstalled Win7 after inadvertently trashing it. It boots from disk without any problem. I must use the Live CD to boot Ubuntu. The CD allows me to choose "Boot from first hard disk". I then get the expected menu. The menu entries are what I expect based on the grub.cfg file. Selecting either Ubuntu or Win7 works fine from this menu.

Is it possible that the BIOS is pointing somewhere unusual in the MBR when booting from hard disk but is OK when booting from CD?

---

### Post by wkinney on 2009-12-28
I forgot to mention that the Boot Info Script shows that sda1 starts at 2048 whereas sdb1 starts at 63. Don't know if this is relevant.

---

### Post by oldfred on 2009-12-28
It seems very strange that the script shows both MBR with grub and the CD boots ok from the selection of the HD.

The 2048 start is normal for Vista and Win7 and 63 is normal for XP and Ubuntu.

You have what looks like a win7 boot partition in sda (100mb) and that is where grub's win7 points to, but you have  the boot flag on sda2. Is the reinstall in sda4 or is that Vista and does it boot? Try moving the boot flag to sda1 with gparted from the liveCD. Only one boot flag per drive is allowed even though with gparted you may be able to set more than one. The error message is a windows error that seems to say it is trying to boot windows but from the wrong partition. Grub probably temporarily resets the boot flag so that is why it will boot windows. In old grub it was the makeactive line, but I do not know in grub2.

Does your BIOS have some sort of secure BIOS boot that we cannot see?

---

### Post by wkinney on 2009-12-28
Sorry, I forgot to include the most recent results from boot info script.  The latest version is attached. The sda boot is now listed on sda1.

After re-installing win7, the system now boots into windows unless I have the live CD in the reader. This happens now with either disk listed as the first boot in CMOS. I assume this is because it does not see a bootloader on sdb and then goes on to boot from sda.

I have not re-installed grub since re-installing win7 for fear of trashing windows again.


Thanks

---

### Post by presence1960 on 2009-12-28
> **wkinney said:**
> Sorry, I forgot to include the most recent results from boot info script.  The latest version is attached. The sda boot is now listed on sda1.

After re-installing win7, the system now boots into windows unless I have the live CD in the reader. This happens now with either disk listed as the first boot in CMOS. I assume this is because it does not see a bootloader on sdb and then goes on to boot from sda.

I have not re-installed grub since re-installing win7 for fear of trashing windows again.


Thanks

Windows bootloader is on MBR of sda, so if you are booting into windows that means sda (750 GB disk) is first in the hard drive boot order in BIOS.

GRUB2 is in MBR of sdb (1 TB disk). In order to get GRUB to boot you need to go into BIOS and make the 1 TB (sdb) disk first in the hard disk boot order. 

The hard disk boot order sets the order of hard disks which are searched for bootloaders when you boot your machine. If sda is first in that order it will detect the windows bootloader and boot to windows.

After setting sdb (1 TB) disk as first in the hard disk boot order save changes to CMOS and continue booting into Ubuntu. Open a terminal and run ```
sudo dpkg-reconfigure grub-pc
```

In this you will be given a choice of where GRUB2 updates are to be installed. Make sure you select sdb in the proper window.

---

