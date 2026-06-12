---
title: "Hard disk mounted to /cd-rom, can't inst"
date: 2011-05-20
forum: Installation &amp; Upgrades
---

### Post by Pullumpkin on 2011-05-20
My hd is somehow mounted to /cd-rom, I am running from a cd drive looking to install. The mounted hd has an unworking xp install and is formatted to ntfs. I cannot unmount to create a new partition, and cannot get the ubu installer to recognize the disk for install. The info on the disk is important so I have not tried to format.

---

### Post by Hedgehog1 on 2011-05-20
> **Pullumpkin said:**
> ... I cannot unmount to create a new partition, and cannot get the ubu installer to recognize the disk for install. The info on the disk is important so I have not tried to format.

Pullumpkin,

I think we might be able to help.

First we need to get a look at your disk drive data.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by Pullumpkin on 2011-05-20
thanks for the quick response, new to linux but not to coding necessarily, been trying console commands and every mounting tutorial out there. not really caring about the xp installation, will format that part once i can part it out, just want some data contained on the volume, not familiar with partitioning in dos (and the whole damn xp install is shot to hell).
#```
                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/sda.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   976,751,999   976,751,937   7 NTFS / exFAT / HPFS


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/sda1        DEE879C6E8799D89                       ntfs       

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /cdrom                   fuseblk    (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)


================================ sda1/boot.ini: ================================

--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 
--------------------------------------------------------------------------------

========= Devices which don't seem to have a corresponding hard drive: =========

sdb sdc sdd sde 


```

---

### Post by Hedgehog1 on 2011-05-20
Thanks for posting the script results.

Right now you have a 500 gig drive with a single primary partition.

You indicate that this partition has XP install, but right now XP is not working/booting.

When you are running from the 'TRY' option on the LiveCD/LiveUSB, you can 'mount' the XP partition and then copy you data from the internal hard drive to an external USB stick or USB drive.

Are you able to read data from the /dev/sda1 (XP) partition?  Or is the partition damaged?

***The Hedge***

:KS

---

### Post by Pullumpkin on 2011-05-20
i can retrieve data but it is in a folder called /cdrom which is the mount point, can grab files i need i guess, was just hoping to make a new partition to install ubuntu on so i can just move the desired files to the new ubuntu partition, as I am liking the feel of the os and plan on using it mostly, perhaps a clean install of xp someday for gaming on the side. mostly having problem with the gui not allowing me to unmount the disk, or create a new partition. the error i get when i try to unmount sda1 from disk utility is Cannot unmount because file system on device is busy

---

### Post by Hedgehog1 on 2011-05-20
Pullumpkin,

Just to be sure I know what you are trying to do:

Is your goal to save your data and reinstall XP (Requires you have the XP install CD)?  Or are you looking to changing to using Ubuntu as your new OS?

Knowing this will help guide our answers.

***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-20
Here is the thing with leaving the data in the XP partition:

We have to 'shrink' that partition to make space for Ubuntu.  The 'shrink' process is best done after a complete defrag of the NTFS partition using the XP defrag tool.

We can still shrink it without doing the defrag, but there is a small risk that the data may get damaged.

If you are willing to take that risk, we can install Ubuntu 'along-side' the non-functioning XP using the standard install.

What are your thoughts on this?

***The Hedge***

:KS

---

### Post by Pullumpkin on 2011-05-20
i am not attached to much of the data, backing up pictures right now, really the only thing that is important. hoping to use ubuntu as my main system at the moment, as xp is no longer supported and I am running off an oem install with no disk to install. would've downloaded a working copy for my key if i could get xp working. really kind of ticked off to the whole microsoft thing at the moment, so very ready to make the switch. consider my files backed up. do not mind doing a full format.

---

### Post by Hedgehog1 on 2011-05-20
Ubuntu Only Install

If you are in a position to wipe the disk clean, please begin your Ubuntu install by using gparted and do this:

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://img858.imageshack.us/img858/9979/mbrpariondemo03.png[/IMG]

**Then begin creating 3 partitions for '/' (root) '/home' & Swap:**

[IMG]http://img853.imageshack.us/img853/503/mbrpariondemo04.png[/IMG]

**Make your root partition 20-30 gigs**

[IMG]http://img7.imageshack.us/img7/2554/mbrpariondemo05.png[/IMG]

**Make your '/home' partition all the rest of the disk space except that you need for swap (swap = RAM size + 10%)**

[IMG]http://img851.imageshack.us/img851/2815/mbrpariondemo06.png[/IMG]

**Next your swap partition:**

[IMG]http://img132.imageshack.us/img132/8353/mbrpariondemo07.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-20
**Press the 'check mark' button to make the changes real:**

[IMG]http://img402.imageshack.us/img402/5460/mbrpariondemo08.png[/IMG]

**gparted will ask this:**

[IMG]http://img826.imageshack.us/img826/7826/mbrpariondemo09.png[/IMG]

**Then it updates your partitions:**

[IMG]http://img101.imageshack.us/img101/5706/mbrpariondemo10.png[/IMG]

**You can see a list of the changes made once the work is done:**

[IMG]http://img862.imageshack.us/img862/7135/mbrpariondemo11.png[/IMG]

**And a view of what the partitions look like after the update:**

[IMG]http://img600.imageshack.us/img600/4516/mbrpariondemo12.png[/IMG]

---

### Post by Hedgehog1 on 2011-05-20
**Same layout, but as seen using the Disk Utility:**

[IMG]http://img825.imageshack.us/img825/2018/mbrpariondemo13.png[/IMG]

**Now when you re-install, select this method:**

[IMG]http://img51.imageshack.us/img51/337/mbrpariondemo15.png[/IMG]

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.


**And tell the install to use the three partitions this way (Your Drive is /dev/sda, not the /dev/sdc this screen shot was taken from):**

[IMG]http://img684.imageshack.us/img684/7977/mbrpariondemo16.png[/IMG]

You will need to right click on each partition and setup to mount points.


**Also, please install the boot loader in /dev/sda (not sda1 or sda2, just /dev/sda)**.


***The Hedge***

:KS

---

### Post by Hedgehog1 on 2011-05-20
If you are still having trouble un-mounting the old NTFS partiton, please do this:

Startup Gparted as Super User by typing this in the terminal:

```
gksudo gparted
```

Then right click on the partition and select 'unmount'

***The Hedge***

:KS

---

### Post by Pullumpkin on 2011-05-20
backing up, gparted did not give me success before trying to unmount, will try su command

---

### Post by Hedgehog1 on 2011-05-20
I am heading off to bed.

Hopefully you have enough to keep moving forward.

I will drop in tomorrow (Portland Oregon time) and see how you got on.

***The Hedge***

:KS

---

### Post by Pullumpkin on 2011-05-20
thanks for the help thus far, thinking I have to find a way to prevent the hd from mounting to /cdrom at boot, not sure how to do this. unsuccessful with terminal and gui's thus far.

---

### Post by Pullumpkin on 2011-05-20
bump

---

### Post by Hedgehog1 on 2011-05-20
Here is a link to the system rescue CD:

[http://www.sysresccd.org/Main_Page]("http://www.sysresccd.org/Main_Page")

If you can download the ISO and make a CD, you should be able to boot from the CD and not mount the hard drive at all.

The CD has **gparted** on it, so you can prepare the hard drive for Ubuntu using the guide I have already posted.

***The Hedge***

:KS

---

### Post by Pullumpkin on 2011-05-20
worked all day, currently downloading recovery cd, will keep posted here.

---

### Post by linuxinstalledfromhdd on 2011-05-20
I bet this is a hardware issue.  Maybe even a HDD slave setting that is physically set wrong. I've had this happen before when there was a incorrect jumper set wrong.

---

### Post by Pullumpkin on 2011-05-21
my  hd is booting as the first master, bios is pretty simple, have set it up as best i can. have tried different boot orders in bios.

---

### Post by Pullumpkin on 2011-05-24
thank you hedge,
recovery cd was incredibly helpful, formatted the drive, it ended up not mounting on the next boot of ubu. natty is installed and running! only problem I had was trying to use xfs as filesystem, tried to do that and installed, gave me some kind of hardware error on boot. reformatted to eft4, installed smoothly, no problems.

---

### Post by Hedgehog1 on 2011-05-25
[SIZE="3"]*HURRAY!!!!*[/SIZE]


I am happy to hear you are operational again!


***The Hedge***

:KS

---

