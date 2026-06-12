---
title: "Ubuntu Fails to Boot after Network Install"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by kweiner on 2006-11-26
I wasn't able to get Ubuntu 6.10 to install on my new Dell 9200c using the Live CD or Alternate CD because it failed to mount my CD-ROM drive (_NEC DVD+-RW ND-6650A).  This led me to try a network installation from a spare Windows laptop as [described here]("https://help.ubuntu.com/community/Installation/WindowsServerNetboot").

Everything went well and the installation completed successfully, but when I tried to reboot, Ubuntu failed to start up.  I was able to see the nice new Ubuntu splash image as it was booting, but then the system hung for a few minutes and finally printed the message ```
ALERT! /dev/sde1 does not exist. Dropping to a shell!
``` and then dropped me into a BusyBox shell.

I think it might have something to do with not being able to find the CD-ROM drive again.  I'm thinking that I could get Ubuntu to boot if I could just prevent it from looking for /dev/sde1.  Is that possible? Any help you could give me would be greatly appreciated.  Thanks!

---

### Post by angryfirelord on 2006-11-26
Unless I'm wrong, I've never heard of a Linux distribution naming a drive sde. I think the issue lies in your /etc/fstab (that's where the drive directories are located).

Now unless you've never used a terminal before, it's an easy fix (provided that my solution answers the problem). Type **sudo nano /etc/fstab** and look for something that says /dev/sde1. Change that to **/dev/sda1**. Do a Ctrl-X, save it, and do a reboot.

If it's possible, show your dmesg (just run that command in the terminal) or at least the parts with drives if that solution fails.

---

### Post by kweiner on 2006-11-26
From the BusyBox shell, I was able to mount /dev/sda1 and look at the /etc/fstab file.  There is only 1 uncommented line in there for proc.  There are two commented lines, however, that begin with /dev/sde1 and /dev/sde5.  I changed all instances of sde to sda and still had the same booting problem.  This makes sense, I guess, because the lines with sde were commented anyway.

I ran dmesg and the last 8 lines are:
```
sd 6:0:0:2: Attached scsi removable disk sdb
sd 6:0:0:2: Attached scsi removable disk sdc
sd 6:0:0:2: Attached scsi removable disk sdd
sd 6:0:0:3: Attached scsi removable disk sde
kjournald starting. Commit interval 5 seconds
EXT3 FS on sda1, internal journal
EXT3-fs: recovery complete
EXT3-fs: mounted filesystem with ordered data mode
```

Earlier in the dmesg output, however, I see this line:
```
Kernel command line: root=/dev/sde1 ro quiet splash
```

Is my /etc/fstab all messed up?  Is there some other file I need to change in order to make Ubuntu think the root is /dev/sda1 instead of /dev/sde1?  Thanks.

---

### Post by kweiner on 2006-11-27
I figured out what to change.  I just had to edit /boot/grub/menu.lst, replacing all instances of /dev/sde1 with /dev/sda1.  Then I was able to boot Ubuntu 6.10 for the first time!  I wonder how it got set to /dev/sde1 in the first place.  It could be something related to a network installation.

My /etc/fstab looks like this.  I don't really understand what these lines with UUID mean, but it is working.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=05976f62-a06a-4998-9c0c-4c409a6405bf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f1c0bf23-66fc-4514-b502-84fa879d5452 none            swap    sw              0       0

```

I'm not able to set my monitor to its max resolution and my cdrom drive still doesn't work, but I'm happy to be able to boot Ubuntu working working internet access.  Thanks for your help.

---

### Post by angryfirelord on 2006-11-27
To set your monitor to the resolution, run **sudo dpkg-reconfigure xserver-xorg**, which will allow you to edit the xorg.conf. It's also useful if you just installed, let's say, nvidia drivers, and have to make xorg know to boot that. When you run it, just use the defaults until you hit the monitor resolutions. Select the best resolution and then the supported resolutions. The supported ones will let you choose how many resolutions you want. 

With your cdrom drive, that also has to be added to your /etc/fstab (you only have the / partition and swap). Instead of trying to explain it in a complicated way, I'll just post my fstab with the drives:
```

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

Depending on how many drives and what type of drives(IDE, SATA), this may not work for you. hda is my primary master and hdb is my primary slave. hdc is my secondary master (hdd). Normally, the hard drive is on hda, but I installed it in the wrong port and I'm too lazy to change it.

It's weird that Ubuntu didn't automatically configure all of this. Then again, I installed directly off a cd.

---

### Post by AndrewMc on 2006-11-27
> **kweiner said:**
> My /etc/fstab looks like this.  I don't really understand what these lines with UUID mean, but it is working.

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=05976f62-a06a-4998-9c0c-4c409a6405bf /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=f1c0bf23-66fc-4514-b502-84fa879d5452 none            swap    sw              0       0

```


For the curious, I mentioned UUIDs on another thread [here]("http://ubuntuforums.org/showpost.php?p=1802706&postcount=11").

---

### Post by kweiner on 2006-11-27
> **angryfirelord said:**
> 

With your cdrom drive, that also has to be added to your /etc/fstab (you only have the / partition and swap). Instead of trying to explain it in a complicated way, I'll just post my fstab with the drives:
```

/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda        /media/cdrom1   udf,iso9660 user,noauto     0       0

```

Depending on how many drives and what type of drives(IDE, SATA), this may not work for you. hda is my primary master and hdb is my primary slave. hdc is my secondary master (hdd). Normally, the hard drive is on hda, but I installed it in the wrong port and I'm too lazy to change it.

It's weird that Ubuntu didn't automatically configure all of this. Then again, I installed directly off a cd.

Thanks for your help.  I am not sure how to tell which drive listed in /dev is my cdrom drive (if any).  I have /dev/sda through /dev/sde.  I tried adding /dev/sde to the fstab and then when I mounted it, Ubuntu responded with "mount: No medium found".

---

### Post by AndrewMc on 2006-11-28
> **kweiner said:**
> Thanks for your help.  I am not sure how to tell which drive listed in /dev is my cdrom drive (if any).  I have /dev/sda through /dev/sde.  I tried adding /dev/sde to the fstab and then when I mounted it, Ubuntu responded with "mount: No medium found".

If I've understood how it works correctly (but I've only been looking at it for a few minutes), "udev" should automatically detect your drive and create a symlink in /dev for you. Can you see if /dev/cdrom exists, and if so, what it points at?

---

### Post by kweiner on 2006-11-28
> **AndrewMc said:**
> If I've understood how it works correctly (but I've only been looking at it for a few minutes), "udev" should automatically detect your drive and create a symlink in /dev for you. Can you see if /dev/cdrom exists, and if so, what it points at?

No, /dev/cdrom does not exist.  Ubuntu was not able to install off a CD which is what led me to do a network install in the first place.  I have an Intel G965 chipset and my CDROM/DVD hardware is _NEC DVD+-RW ND-6650A.  Maybe it isn't supported by linux yet?

---

### Post by kweiner on 2006-11-28
> **angryfirelord said:**
> To set your monitor to the resolution, run **sudo dpkg-reconfigure xserver-xorg**, which will allow you to edit the xorg.conf. It's also useful if you just installed, let's say, nvidia drivers, and have to make xorg know to boot that. When you run it, just use the defaults until you hit the monitor resolutions. Select the best resolution and then the supported resolutions. The supported ones will let you choose how many resolutions you want.

Thanks.  I tried running **sudo dpkg-reconfigure xserver-xorg**, but I wasn't able to get it to produce a working xorg.conf.  I ended up reverting to my original xorg.conf.  I found out that I have an Intel G965 chipset with  an Intel GMA X3000 onboard video chip.  My xorg.conf is using the i810 driver which I think is the right one based on some info I read on the web.  However, the description if the i810 driver mentions a list of chipsets that it works with and mine, G965, isn't on that list.  I am still searching the forums for information about the G965/GMA X3000 combination, but haven't found anything.

---

