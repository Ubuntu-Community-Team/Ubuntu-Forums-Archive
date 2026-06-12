---
title: "Grub Error 22"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by docjones2 on 2010-11-23
I installed ubuntu 10.10 on an acer eee pc, dual boot with windows xp home.

After installation, everything worked fine (in linux) but windows would not boot (unrecognized device string), so in grub (before booting into any system, the grub prompt) I hit whatever key it was to edit commands for the windows boot option to diagnose the problem.

Problem was simple, the grub command that was installed for some reason specified only the device (hd0) and not the partition, so after some experimentation with this I modified the command to reference correctly the windows partition, yey!

On reboot grub returns error 22.

I booted into a linux disc and got a command prompt going.  My linux partition appears to no longer function, I can not (manually) mount it, however I can manually mount the windows partition. 

I have tried this from 2 different linux discs, one that gave me a gui and one that gave me a cli, and both can not mount my linux partition.

At this point I have no idea what the problem may be, all I know is that it started once I modified the grub command for windows from grub pre-boot screen.  

To reiterate, I was not booted into any system, I did not accidentally **** up the /boot/grub/menu.lst file, I merely used the grub boot interface to modify the windows grub command and then boot from the new command.  Now linux partitions seem not to be mountable and grub fails outright with error 22.

Thank you for any responses.

---

### Post by Quackers on 2010-11-23
Please go to the site below and download the boot script to your DESKTOP and then open up a terminal and run ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply).
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by sikander3786 on 2010-11-23
> My linux partition appears to no longer function, I can not (manually) mount it

This shouldn't have happened.

But please post the output of bootinfoscript as already suggested as it would tell us exactly about nearly everything going on in there regarding the boot problem.

Thanks.

---

### Post by docjones2 on 2010-11-23
Ran this from a linux boot cd, below is the output

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ntldr /NTDETECT.COM

sda3: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda4: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    79,687,562    79,687,500   7 HPFS/NTFS
/dev/sda2         302,246,910   312,496,379    10,249,470  1c Hidden W95 FAT32 (LBA)
/dev/sda3         312,496,380   312,576,704        80,325  ef EFI (FAT-12/16/32)
/dev/sda4          79,687,678   302,245,887   222,558,210  15 Unknown


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 2021 MB, 2021654016 bytes
4 heads, 32 sectors/track, 30847 cylinders, total 3948543 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1    *             32     3,948,542     3,948,511   b W95 FAT32


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        7AE0A82DE0A7EE17                       ntfs                                     
/dev/sda2        CCED-990E                              vfat       PE                            
/dev/sda3: PTTYPE="dos" 
/dev/sda4: PTTYPE="dos" 
/dev/sda: PTTYPE="dos" 
/dev/sdb1        645F-8BE6                              vfat       SWORD                         
/dev/sdb: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb1        /media/SWORD             vfat       (rw,nosuid,nodev,uhelper=udisks,uid=999,gid=999,shortname=mixed,dmask=0077,utf8=1,showexec,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=30

default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
```

sdb is the flashdrive that I put the script on

And I notice that on sda, like I explained in the first post, my linux partitions seem to have become inoperative.  sda4 should be an ext4 root directory of an ubuntu install.

---

### Post by Quackers on 2010-11-23
I see some problems :-)
Firstly if you are using 10.10 you should have grub2, whereas you have grub. Secondly grub is lookin at "partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst" but there isn't a partition 6.
Partitions 3 and 4 appear to be indecipherable to grub - maybe try testdisk to see if anything can be salvaged.
Basically the only thing that appears that it may be bootable is Windows and that may need repairing.
These are only guesses but was Ubuntu only bootable while the flash drive was plugged in? I also wonder if you chose to install alongside in the 10.10 installer? 
Do you have a Windows install disc?

---

### Post by kansasnoob on 2010-11-23
> **Quackers said:**
> I see some problems :-)
Firstly if you are using 10.10 you should have grub2, whereas you have grub. Secondly grub is lookin at "partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst" but there isn't a partition 6.
Partitions 3 and 4 appear to be indecipherable to grub - maybe try testdisk to see if anything can be salvaged.
Basically the only thing that appears that it may be bootable is Windows and that may need repairing.
These are only guesses but was Ubuntu only bootable while the flash drive was plugged in? I also wonder if you chose to install alongside in the 10.10 installer? 
Do you have a Windows install disc?

I saw something similar recently but the OP stopped responding before we learned much more:

[http://ubuntuforums.org/showthread.php?p=10131101#post10131101](http://ubuntuforums.org/showthread.php?p=10131101#post10131101)

I have no answers though.

---

### Post by Quackers on 2010-11-23
Frighteningly similar Mr. K :-)

---

### Post by docjones2 on 2010-11-23
> **Quackers said:**
> I see some problems :-)
Firstly if you are using 10.10 you should have grub2, whereas you have grub.

I explicitly chose to install grub 1 at install time.  I have had problems in the past with grub 2, also, I don't recall if the most recent ubuntu install disc has the same disclaimer, but previous versions of ubuntu install discs have warned not to use grub 2 in a production environment.  Is there an actual reason why grub2 should be used for ubuntu 10.10 or is that just what typical discs do by default?

> 
 Secondly grub is lookin at "partition #6 for /boot/grub/stage2 and /boot/grub/menu.lst" but there isn't a partition 6.

This makes sense, but like I said before, there was a time when grub worked perfectly and ubuntu booted perfectly.  The only problem was that windows wouldn't boot.

> 
Partitions 3 and 4 appear to be indecipherable to grub - maybe try testdisk to see if anything can be salvaged.

I did notice this and it is what disturbs me the most.  I can not mount these partitions, they just appeared to have become ghosts once I booted into windows for the first time since installing ubuntu.

> 
Basically the only thing that appears that it may be bootable is Windows and that may need repairing.

Well, Windows is disposable in my situation.

> 
These are only guesses but was Ubuntu only bootable while the flash drive was plugged in? I also wonder if you chose to install alongside in the 10.10 installer? 

Ubuntu was bootable always perfectly without any outside assistance.  It was the first entry in menu.lst and booted fine for about a week.  The problem arose when I tried fixing the boot error for windows.

On the grub interface, you are given the option I believe to hit 'e' and edit the grub commands for a particular menu entry.

I edited the windows grub command to point to the correct windows partition (prior to this it was not pointing to any partition and causing an "unrecognized device string" error)

Once windows booted successfully I thought all was fine and dandy, I rebooted the system and found the grub error 22.  At this point I was on a bus, my computer has no optical drive so I had to wait till I got home before I could plug in a usb/ide adapter into an internal cd drive to boot from a linux disc, and that's when I discovered that my linux partitions were now unable to mount.

And yes, I explicitly chose to install ubuntu side by side xp, if by "alongside" you mean in a separate partition for dual boot.

> 
Do you have a Windows install disc?
Yes.  The installation on the computer now was oem, but I have my own copy that is better than the oem one anyway, so it is not an issue to start from scratch.

It would be easy for me to "fix" the problem by reinstalling windows xp, then reinstalling ubuntu 10.10, but that's not really a "solution," that's starting over.  Is there anyway I do not have to resort to this?

---

### Post by Quackers on 2010-11-23
I was thinking more like running fixmbr from the Windows cd in order to get XP booting.

[http://www.ehow.com/how_5087994_fix-windows-xp-bootloader.html](http://www.ehow.com/how_5087994_fix-windows-xp-bootloader.html)

I would then suggest booting from the Ubuntu Live cd and running testdisk to see what, if anything, can be recovered from the other partitions.

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

With regard to grub or grub2, I would suggest that as grub2 is the default loader for 10.10, it would have been (indeed it was :-) ) my first choice.

---

### Post by docjones2 on 2010-11-23
Have to go to work now, I'll get back later tonight with any progress.  If it is not fixed within a day or two I will have to resort to starting over (which I probably should have done the first day I got the computer, I hate that you can't buy empty computers and it always happens that I have to fix some retarded manufacturer's ******** down the road anyway)

One idea did occur to me, maybe the ghost partitions had there labels or whatever the correct term is some how removed and they can be mounted if I specify via command arguments information like "ext4" or what have you.

I will try that, and if that works, then it looks like I'm in business.

---

### Post by Quackers on 2010-11-23
Of it's just a pbr problem testdisk would sort that out.

---

### Post by kansasnoob on 2010-11-23
> **Quackers said:**
> Of it's just a pbr problem testdisk would sort that out.

I've generally found that working with a netbook means no CD drive is available. So you'll seldom find a Win CD available. And, quite often, the user does not have a USB powered CD drive.

So with netbooks you're likely to be looking at USB only which made me think we should ask (just to be sure) if this was a Wubi install or a true dual boot.

Or was it some sort of net-install?

It seems odd that the triple e's and Acer's have this problem :confused:

My old Acer One crapped itself due to a bad charger (smoke and melted plastic)!

---

### Post by kansasnoob on 2010-11-23
Just happened to think of something else. You know how grub2 likes identifying both Win and Win recovery as bootable OS's?

Could doing so hose things like this?

Yes, I'm grabbing at straws.

---

### Post by docjones2 on 2010-11-24
testdisk doesn't even seem to know those partitions exist, trying to explicitly name the filesystem type as ext4 yields no success...

gparted even dies for some reason (yes I was root) so apparently whatever happened to those partitions is pretty ****ed up...

Anyway, I'm going to put in the Ubuntu 10.10 alt install disc, set up my partitions for a windows xp pro n install and an ubuntu install right after, I doubt I'll have problems from this point

Can anyone tell me why grub2 is preferred in ubuntu 10.10 now?  What are the advantages of having grub2 and what has changed in grub 2 since 10.04? (which is the last time I tried it and had problems)

I'll be doing this install from my ide cd-rom drive that I found in a windows 98 computer later today, someone respond sometime before then or else I'm going with grub 1

---

### Post by Quackers on 2010-11-24
Details on grub/grub2 in this guide by drs305. If you scroll down past the red headings to the blue headings grub is explained fully.

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by docjones2 on 2010-11-24
This is a disclaimer from the Ubuntu 10.10 install disc.

> GRUB 2 is the next generation of GNU GRUB.  It has interesting new features **but is still experimental software.**  If you chose to install it, **you should be prepared for breakage**, and have an idea of how to recover your system if it becomes unbootable.  **You're advised not to try this in production environments**.

I installed GRUB Legacy as a result.

Is this disclaimer out of date or is Ubuntu pushing experimental software onto new users?

---

### Post by Quackers on 2010-11-24
I've used 10.04 32 bit and 64 bit discs and a 10.10 64 bit disc to install/re-install Ubuntu and I haven't seen that disclaimer myself.
I suspect it is old - like the warning about 64 bit desktop installation!

I suspect though, that at some time in the future, as grub is updated you may come across problems. Just my suspicion, you understand :-)

---

### Post by docjones2 on 2010-11-24
> **Quackers said:**
> I've used 10.04 32 bit and 64 bit discs and a 10.10 64 bit disc to install/re-install Ubuntu and I haven't seen that disclaimer myself.
I suspect it is old - like the warning about 64 bit desktop installation!

I suspect though, that at some time in the future, as grub is updated you may come across problems. Just my suspicion, you understand :-)

The dislaimer is on the alternate install disc with expert mode enabled.

The only way I know how to install ubuntu anymore

---

