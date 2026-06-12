---
title: "Install Ubuntu over existing dual boot partition"
date: 2009-12-29
forum: Installation &amp; Upgrades
---

### Post by David_UK on 2009-12-29
Currently, one of my PC's dual boots Win98 (C: drive) and WinXP (D: drive)

I'd like to install Ubuntu over the unrequired C: partition, but I'm not sure what will happen to the MBR (I'm familiar with FIX MBR and with inserting Grub into the MBR).

Presumably, the MBR is currently on C: drive, so Ubuntu will over-write this.  

Then I'll need to FIX MBR - **but will windows expect to boot from C: after FIX MBR?**  If so, can I modify the MBR to point windows to D: ?

Subsequently, I'm expecting that inserting Grub will allow selection of either Linux or XP.

Have I got any of this wrong?  Any issues to consider?
Thanks

PS it's a small HDD so I want to erase Win98 rather than triple-booting alongside both windows versions

---

### Post by louieb on 2009-12-29
Depending  on where the MS boot loader is installed - Win98 or WinXP.  MS has a weird way of setting up Dual booting - only one install has a boot loader. 

If you overwrite the one with the boot loader - then GRUB will not be able to boot the other one. Grub cannot boot Windows - it passes control to the windows boot loader. 

If you have internet with the live CD please follow the [Boot Info Script: How to]("http://ubuntuforums.org/showthread.php?t=1291280")  and put the results.txt in your next post. That will show if you can dual boot Linux and XP or not.

---

### Post by David_UK on 2009-12-31
louib

Thanks for your help.  Here are the results:

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Windows XP: Fat32
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /boot.ini /BOOT.INI /ntldr /NTLDR /NTDETECT.COM 
                       /ntdetect.com

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  Windows XP
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd0f4738c

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    15,631,244    15,631,182   b W95 FAT32
/dev/sda2          15,631,245   156,248,189   140,616,945   f W95 Ext d (LBA)
/dev/sda5          15,631,308   156,248,189   140,616,882   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

sda1: LABEL="WIN98" UUID="2349-10FE" TYPE="vfat" 
sda5: UUID="02B83061B830557F" LABEL="WinXP" TYPE="ntfs" 

=============================== "mount" output: ===============================

proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/WIN98 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=999,utf8,umask=077,flush)


================================ sda1/boot.ini: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\="Microsoft Windows" 


================================ sda1/BOOT.INI: ================================

[boot loader]

timeout=10

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

C:\="Microsoft Windows"

---

### Post by louieb on 2009-12-31
Good thing you asked first. If you overwrite win98 with Ubuntu you will not be able to boot XP.  

a liitle translation **sda1 = c:  , sda5 = d: **

You boot loader files are in sda1 your win98 install.  On top of that sda5 is a logical partition. So you can't just copy the boot loader files from sda1 to sda5. Windows XP is almost impossible to get to boot when it installed in a logical partition unless there is another windows install in a primary one. 
[Multibooters, Pictures here worth 1000 words]("http://www.multibooters.co.uk/multiboot.html") 


I guess you could reinstall XP. 
or it would be tricky  but you could triple boot - shrink sda1 as far a possible if you can get 10GB or more of unallocated space. 

You still can create 2 primary partitions One for Ubuntu and one for swap. 
[Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm") 

BTW: How much ram does this PC have?

---

### Post by meierfra. on 2010-01-01
> On top of that sda5 is a logical partition. So you can't just copy the boot loader files from sda1 to sda5. Windows XP is almost impossible to get to boot when it installed in a logical partition

Actually copying the boot files (boot.ini,ntldr and ntdetect.com) from sda1 to sda5 is almost all it takes to boot XP from /dev/sda5.  There is only one other problem you need to take care of:

> Boot sector info: According to the info in the boot sector, sda5 starts at sector 63.


63 is the number of sector from sda5 to the start of the extended partition sda2. To be able to boot from sda5, this needs to be the number of sector sfrom the begining of the hard drive. You can fix this with testdisk.   Try this:

Boot from the Ubuntu Live CD and open a terminal

[B]Step 1: Copy the boot files to the XP partition:
[/B]
```
cd /mnt
sudo mkdir sda{1,5}
sudo mount {/dev/,}sda1
sudo mount {/dev/,}sda5
sudo cp sda1/{boot.ini,ntldr,ntdetect.com} sda5/
```

**Step 2 Fix the XP boot sector:**


```
sudo apt-get install testdisk

sudo testdisk  /dev/sda  
```


Press "enter" to "proceed"
Press "enter" to select "intel"
Use the "down arrow" and "enter" to select "advanced"
Use the down arrow to select the "XP" partition and then "enter" to select "boot"
Use the "right arrow" key and "enter" to select "Rebuild BS"
This might take a while. Once done:
Use the "right arrow" key and "enter" to select "write". This will write a modified boot sector to the Windows partition.
Then press "q" a few times to exit testdisk


**Step3  Install some code to the MBR which can boot a logical partition and put the boot flag to the XP partition**


```
sudo apt-get install lilo 
(Ignore the message which is displayed, just press enter)
sudo lilo -M /dev/sda ext
sudo lilo -A /dev/sda 5 
```

Reboot and you should be get  the normal boot menu. (Although the item for Window 98 probably will not work without editing "boot.ini")

Step3 is not really necessary, since installing Ubuntu will overwrite the MBR again. But this way you can test whether you can boot from /dev/sda5 without deleting your Windows 98 partition.

If  for some reason, you are not able to boot into Windows XP, just put the boot flag back onto dev/sda1:


```
sudo apt-get install lilo 
sudo lilo -A /dev/sda 1 
```

---

### Post by David_UK on 2010-01-01
> **louieb said:**
> Good thing you asked first. If you overwrite win98 with Ubuntu you will not be able to boot XP.
Phew!  Yes, glad I engaged brain first.  Thanks for looking at the results file.

> **meierfra. said:**
> Actually copying the boot files (boot.ini,ntldr and ntdetect.com) from sda1 to sda5 is almost all it takes to boot XP from /dev/sda5....Interesting.  Thanks for your walkthrough.  So if I try your method using the live CD and it doesn't work, the only damage done will be to have added lilo into the chain?  I haven't used lilo before, but presumably I can set a default OS (just like in grub)?  The PC is used by children so I don't want them to have to make any selections at the boot stage.  The win98 install is no longer used to it won't matter if it's not accessible.

> **louieb said:**
> [Multibooters, Pictures here worth 1000 words]("http://www.multibooters.co.uk/multiboot.html")Good article!

> **louieb said:**
> I guess you could reinstall XP.Yes, that may not be a bad thing if it comes to it.  The install is about 7yrs old and could probably do with a refresh.

> **louieb said:**
> BTW: How much ram does this PC have?512mb.  It's mainly used for internet & office apps.

---

### Post by meierfra. on 2010-01-01
> I haven't used lilo before, but presumably I can set a default OS (just like in grub)? The PC is used by children so I don't want them to have to make any selections at the boot stage.

You will be using lilo only as a temporay solution until you install Ubuntu. During the  Ubuntu installation it will be replaced by grub.

And you won't be using the full blown lilo boot loader, just the part which is installed in the MBR.  Currently your  Windows MBR loads the boot sector of the  partition with the  boot flag. But the Windows MBR is not able to load the boot sector of a logical partition. The lilo MBR will to the exact same thing, except  that it also can handle logical partitions.

> The only damage done will be to have added lilo into the chain?
Actually, Lilo replaces the windows MBR and works just as well. So no damage done.


> 512mb. 
You can run Ubuntu with 512 MB, but it will be on the slow side. You might want to consider a more lightweight version like Xubuntu.


> shrink sda1 as far a possible 
That actually is also  a good idea. Just leave the three boot files (total of 300KB)  on /dev/sda1 and deleted everything else.  And if you  like you can use the same partition to hold the grub files. (Grub needs about 700 KB.) Then you can delete XP or Ubuntu at any time and still will be able to boot  the other OS.

---

### Post by louieb on 2010-01-01
@meierfra. :P Glad you came along. And to think for all these year though Herman was the the only one to get XP to boot from a logical partition.  Really like your writeup - nice and clear.  - And a Happy and prosperous New Year to you. 

@David_UK   Do let us know how it goes. I've dual booted a lot of computers - but I'm no meierfra - he's the one who authored the Boot_info_script.

---

### Post by David_UK on 2010-02-21
Ok.  I've had a chance to try this and this is an update:

I could follow the instructions pretty well.  I couldn't apt-get testdisk ("Couldn't find package") but I could d/l it from the website and run it as instructed.  Everything went fine then after installing lilo - I got the normal boot menu as usual and XP ran normally.
However, after then installing ubuntu, if I select XP from the grub menu it fails with "error 12: invalid device requested"

I need help now to sort out this last bit - grateful for any suggestions.  I'm thinking it's probably just a case of inserting grub into the MBR (output of find /boot/grub/stage1 = hd0,0).

Thanks

---

### Post by meierfra. on 2010-02-21
> I couldn't apt-get testdisk 
Sorry, I should have mentioned that you need to enable the "universe" repository. 

> If I select XP from the grub menu it fails with "error 12: invalid device requested"
Seems you installed Ubuntu 9.04 or older. Do this

```
gksudo gedit /boot/grub/menu.lst
```

Look for your windows item (should be at the end of the file)
Something like

title  Windows XP
root [COLOR="Red"](hd0,4)[/COLOR]
makeactive
chainloader +1

Change it to:

title  Windows XP
rootnoverify ([COLOR="Red"]hd0,4)[/COLOR]
chainloader +1

Just use  those three lines, but make sure to use the same numbers as in your current item (It probably is  "(hd0,4)" but it might different different if Ubuntu created a Swap partition during installation)

---

### Post by David_UK on 2010-02-21
> **meierfra. said:**
> 
Change it to:

title  Windows XP
rootnoverify ([COLOR="Red"]hd0,4)[/COLOR]
chainloader +1

Sweet.  Yes that's done the trick - both OS's are booting - thank you so much for such a quick reply!

Just to tidy up now then, after the grub boot menu, I then get the windows dual boot menu - which is ok, but I'd like to remove that stage if possible because selecting the old Win98 causes the system to freeze.  I guess I have to edit the boot.ini?  Which is currently:

[I][boot loader]
timeout=10
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect
C:\="Microsoft Windows"[/I]

If I just remove C:\="Microsoft Windows" and change timeout to 0 perhaps?

Thanks again

---

### Post by meierfra. on 2010-02-21
> If I just remove C:\="Microsoft Windows" 
Exactly


> and change timeout to 0 perhaps?
If  only  one operating system is listed in boot.ini, the timeout value is ignored and the system will boot directly into XP. So no need to change the timeout.

---

### Post by David_UK on 2010-02-21
meierfra

Perfect.  Exactly as you said.  Many thanks for your help - I'm sure others will find this thread invaluable too.

---

