---
title: "Ubuntu won't install on unallocated partition alongside Windows 7"
date: 2014-02-07
forum: Installation &amp; Upgrades
---

### Post by vitale232 on 2014-02-07
I have a Windows 7 (preinstalled) Dell desktop.  I used the  Windows Partition Manager to shrink the main partition by 400 GB.  The  tool froze before confirming completion, but when I re-executed it,  everything looked as expected.  I then rebooted the system three times  to make sure Windows was feeling good about the smaller hard drive.
  I then booted to the Ubuntu 13.10 Live CD to use the installer tool.   I was greeted with the system acknowledging that an OS existed, so I  selected to install alongside.  Ubuntu produced an uniterpretable error  that literally read: ???? ????.  I clicked OK, and the install tool  now only gives the option to erase disk or something else.
  I decided to open GParted to get an idea of what was going on, and it continues to get hung up on Searching /dev/mapper/isw_ebffchhbhf_ARRAY partitions.  When I run it from the command line I get the following error:
  ubuntu@ubuntu:~$ sudo gparted
======================
libparted : 2.3
======================

(gpartedbin:13899): glibm    m-CRITICAL **: 
unhandled exception (type Glib::Error) in signal handler:
domain: g_convert_error
code  : 1
what  : Invalid byte sequence in conversion input
  Does anyone have any advice?  Any idea what the issue is?

---

### Post by Bucky Ball on 2014-02-07
Try again and this time choose 'Something Else' and partition manually (pretty simple as similar to Gparted setup). The 'alongside' option is known to be a bit buggy ...

PS: I'd try booting Win first just to make sure that is unaffected by all this.

---

### Post by vitale232 on 2014-02-08
Thanks for the response.  I've done that three times since I posted this.  I did something else and partitioned ~50 gb to /, ~ 16 gb to swap, and the rest to /home.  All were set to logical at the beginning of the drive, ext4 format.  As soon as I hit install, it gives me the uninterpretable ??? ??? error and the time zone screen.  I booted back into windows, and the unallocated space was partitioned.  Ubuntu, however, could not move past the error.  I've tried two DVDs, and plan on trying a USB next.  It's hard to believe the DVDs are bad, though, as the hardware is pretty new.

---

### Post by Bucky Ball on 2014-02-08
You created logical partitions at the beginning of the disk. I'm a little confused. Logical partitions exist inside extended partitions. Primary partitions are the only option outside of this. 

Do you have four partitions already and this is NOT and EFI install? If not EFI, four partitions, a combination of primary and extended or all of one or the other, is your limit. If you are trying to create more than four, that is your issue. Inside the extended partition you may create as many logical drives as you like (or, theoretically, your hardware can deal with).

You might run and post the output of this:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

Instructions:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Handy to have around, or, post the output of 'sudo blkid' from a terminal on a live boot.

---

### Post by carl4926 on 2014-02-08
> **vitale232 said:**
> Thanks for the response.  I've done that three times since I posted this.  I did something else and partitioned ~50 gb to /, ~ 16 gb to swap, and the rest to /home.  All were set to logical at the beginning of the drive, ext4 format.  As soon as I hit install, it gives me the uninterpretable ??? ??? error and the time zone screen.  I booted back into windows, and the unallocated space was partitioned.  Ubuntu, however, could not move past the error.  I've tried two DVDs, and plan on trying a USB next.  It's hard to believe the DVDs are bad, though, as the hardware is pretty new.

I suggest booting the live session and with a eth0 connection
Run
```
sudo apt-get install gparted
```

Open gparted
And post a screen of you partition setup here

---

### Post by Bucky Ball on 2014-02-08
Last I looked Gparted was already there, didn't need to install to a live boot ... :-k

---

### Post by carl4926 on 2014-02-08
> **Bucky Ball said:**
> Last I looked Gparted was already there, didn't need to install to a live boot ... :-k

Could be...
I was just going from memory, seem to recall having to install it on a new install for a customer recently.

---

### Post by oldfred on 2014-02-08
If issue is /mapper/... then is system RAID or Intel SRT which uses RAID? Or LVM?
Gparted does not work with RAID nor LVM.

If an Ultrabook then it is Intel SRT.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

---

### Post by vitale232 on 2014-02-08
Thanks for the responses.  As you've probably gathered, I'm pretty new to Linux and tinkering with my machines.  Most of what I do comes from online tutorials.  To clarify what I tried to do with the "Something Else" option, here's the [link]("http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html") I used.  It's instructions to set up a dual boot for Windows 8.  Since it worked for me on my home computer, I figured the same idea would apply to Windows 7 (aside from disabling Secure Boot).

I defragged my Windows C:\ drive, set up the unallocated partition with Windows Parition Manager, booted the Linux live CD, and followed the instructions from the link starting at step 5.

The dual boot I'm trying to set up now is on my work computer.  I'll head in sometime today or tomorrow and run those terminal commands.  The output will be posted as soon as I can.

Also, the machine is a Dell Optiplex.  I'll confirm the specific model # on my next post, along with the terminal outputs.

I appreciate the help.  I'm finding the Linux community to be awesome.

---

### Post by vitale232 on 2014-02-08
> **Bucky Ball said:**
> 
Do you have four partitions already and this is NOT and EFI install? 

You might run and post the output of this:

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)


The best answer I have right now is the description of what I did in my  last post.  To confirm or deny EFI, do I just boot back into BIOS and  look at the settings?

The results of the boot info script are below.

> **carl4926 said:**
> I suggest booting the live session and with a eth0 connection
Run
```
sudo apt-get install gparted
```

Open gparted
And post a screen of you partition setup here

Gparted is included in the live CD.  When I try to run it from terminal, I get the error that I reported in the OP.  It also scans forever in the /dev/mapper/isw_ebffchhbhf_ARRAY partitions.

> **oldfred said:**
> If issue is /mapper/... then is system RAID or Intel SRT which uses RAID? Or LVM?
Gparted does not work with RAID nor LVM.

If an Ultrabook then it is Intel SRT.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

So all of that sounded really intimidating.  How can I confirm or deny RAID or LVM?


OUTPUTS:
```
sudo blkid
/dev/mapper/isw_ebffchhbhf_ARRAY1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="5450-4444" TYPE="vfat" 
/dev/mapper/isw_ebffchhbhf_ARRAY2: LABEL="RECOVERY" UUID="2418BE8718BE578E" TYPE="ntfs" 
/dev/mapper/isw_ebffchhbhf_ARRAY3: LABEL="OS" UUID="EC94C46294C430BE" TYPE="ntfs" 
/dev/loop0: TYPE="squashfs" 
/dev/sda: TYPE="isw_raid_member" 
/dev/sr0: LABEL="Ubuntu 13.10 amd64" TYPE="iso9660" 
/dev/sdb: TYPE="isw_raid_member"
```

```
Boot info output:
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => Windows is installed in the MBR of /dev/mapper/isw_ebffchhbhf_ARRAY.

isw_ebffchhbhf_ARRAY1: _________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: FAT16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /DELLBIO.BIN /DELLRMK.BIN /COMMAND.COM

isw_ebffchhbhf_ARRAY2: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

isw_ebffchhbhf_ARRAY3: _________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /Windows/System32/winload.exe

isw_ebffchhbhf_ARRAY4: _________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info: 

isw_ebffchhbhf_ARRAY5: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

isw_ebffchhbhf_ARRAY6: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

isw_ebffchhbhf_ARRAY7: _________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: isw_ebffchhbhf_ARRAY _____________________________________________________________________

Disk /dev/mapper/isw_ebffchhbhf_ARRAY: 2000.4 GB, 2000405397504 bytes
255 heads, 63 sectors/track, 243202 cylinders, total 3907041792 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/isw_ebffchhbhf_ARRAY1                 63        80,324        80,262  de Dell Utility
/dev/mapper/isw_ebffchhbhf_ARRAY2   *         81,920     1,622,015     1,540,096   7 NTFS / exFAT / HPFS
/dev/mapper/isw_ebffchhbhf_ARRAY3          1,622,016 3,068,174,335 3,066,552,320   7 NTFS / exFAT / HPFS
/dev/mapper/isw_ebffchhbhf_ARRAY4      3,068,174,846 3,907,041,791   838,866,946   5 Extended
/dev/mapper/isw_ebffchhbhf_ARRAY5      3,068,174,848 3,165,830,655    97,655,808  83 Linux
/dev/mapper/isw_ebffchhbhf_ARRAY6      3,165,831,168 3,875,791,359   709,960,192  83 Linux
/dev/mapper/isw_ebffchhbhf_ARRAY7      3,875,791,872 3,907,041,791    31,249,920  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/isw_ebffchhbhf_ARRAY1 5450-4444                              vfat       DellUtility
/dev/mapper/isw_ebffchhbhf_ARRAY2 2418BE8718BE578E                       ntfs       RECOVERY
/dev/mapper/isw_ebffchhbhf_ARRAY3 EC94C46294C430BE                       ntfs       OS
/dev/sda                                                isw_raid_member 
/dev/sdb                                                isw_raid_member 
/dev/sr0                                                iso9660    Ubuntu 13.10 amd64

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
isw_ebffchhbhf_ARRAY
isw_ebffchhbhf_ARRAY1
isw_ebffchhbhf_ARRAY2
isw_ebffchhbhf_ARRAY3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on isw_ebffchhbhf_ARRAY4


Unknown BootLoader on isw_ebffchhbhf_ARRAY5


Unknown BootLoader on isw_ebffchhbhf_ARRAY6


Unknown BootLoader on isw_ebffchhbhf_ARRAY7



========= Devices which don't seem to have a corresponding hard drive: =========

sdc sdd sde sdf 

=============================== StdErr Messages: ===============================

hexdump: /dev/mapper/isw_ebffchhbhf_ARRAY4: No such file or directory
hexdump: /dev/mapper/isw_ebffchhbhf_ARRAY4: No such file or directory
hexdump: /dev/mapper/isw_ebffchhbhf_ARRAY5: No such file or directory
hexdump: /dev/mapper/isw_ebffchhbhf_ARRAY5: No such file or directory
hexdump: /dev/mapper/isw_ebffchhbhf_ARRAY6: No such file or directory
hexdump: /dev/mapper/isw_ebffchhbhf_ARRAY6: No such file or directory
hexdump: /dev/mapper/isw_ebffchhbhf_ARRAY7: No such file or directory
hexdump: /dev/mapper/isw_ebffchhbhf_ARRAY7: No such file or directory
  No volume groups found
```


Since I can't get Gparted running, here's a picture of what my hard drive looks like in the Windows tool both before an attempted install and after a failed install:

[IMG]https://lh4.googleusercontent.com/-4dFHzIcJz8I/UvaiyAeuTuI/AAAAAAAAZqc/xJmJiTkxuH4/w995-h449-no/partition1.JPG[/IMG]

[B]Prior to install
[/B]


[IMG]https://lh3.googleusercontent.com/-V7FfXCoxvlw/UvaiyDGN9cI/AAAAAAAAZqQ/qaJdNC8nzmc/w990-h448-no/partition.JPG[/IMG]

**After failed install attempt**

---

### Post by oldfred on 2014-02-08
Your hard drives sda & sdb are RAID.

 /dev/sda: TYPE="isw_raid_member" 
/dev/sr0: LABEL="Ubuntu 13.10 amd64" TYPE="iso9660" 
/dev/sdb: TYPE="isw_raid_member"

I do not know RAID, but standard desktop installer does not support RAID, as that is more common with servers.
You need to install grub to the root of the RAID not to the MBR of a drive.

You may have BIOS RAID or fakeRAID.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

You may want to review this also:

 [http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

This is generic example, change to yours, note that you mount the partition with Linux and install to the root of the RAID.

 For RAID reinstall from live-CD/DVD/USB
sudo apt-get install mdadm
[http://ubuntuforums.org/showthread.php?t=2022679](http://ubuntuforums.org/showthread.php?t=2022679)
"fakeRaid" with nVidia
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

### Post by vitale232 on 2014-02-09
Thanks for the reply.  This is turning into a bigger PITA than hoped.

I'm a bit confused.  The generic example you shared (thanks for finding that) already had Ubuntu installed.  I can't even get it installed.  Will running those commands from the live CD then allow me to get the OS installed?

---

### Post by oldfred on 2014-02-09
I thought you had it installed in partition 5 & 6?

 /dev/mapper/isw_ebffchhbhf_ARRAY[COLOR=#ff0000]5[/COLOR]      3,068,174,848 3,165,830,655    97,655,808  83 Linux
/dev/mapper/isw_ebffchhbhf_ARRAY[COLOR=#ff0000]6[/COLOR]      3,165,831,168 3,875,791,359   709,960,192  83 Linux
/dev/mapper/isw_ebffchhbhf_ARRAY7      3,875,791,872 3,907,041,791    31,249,920  82 Linux swap / Solaris

sudo mount /dev/mapper/isw_ebffchhbhf_ARRAY[COLOR=#ff0000]5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_ebffchhbhf_ARRAY

But Boot-Repair did not mount everything so I cannot tell if your install in in those partition(s) or not.

---

### Post by vitale232 on 2014-02-09
Hmmm, I'd be surprised if it actually installed.  The installer tool crashes with the ??? ??? error within a minute of executing.  

How would I check to see if it's in there?  Something like:
sudo mount [COLOR=#000000][FONT=Ubuntu Mono]/dev/mapper/isw_ebffchhbhf_ARRAY5 /mnt
ls /mnt

From the live CD?[/FONT][/COLOR]

---

### Post by oldfred on 2014-02-09
That should work. Perhaps it only created partitions, but got no further.
You may need RAID driver
sudo apt-get install mdadm
or 
sudo apt-get install dmraid

The desktop installer does not support RAID. Not sure if installing RAID driver like Boot-Repair does in live version then works with installer or not.

---

### Post by vitale232 on 2014-02-11
```
sudo mount /dev/mapper/isw_ebffchhbhf_ARRAY5 /mnt
mount: special device /dev/mapper/isw_ebffchhbhf_ARRAY5 does not exist
```

Seems like it failed.  I'm going to have to boot back into Windows and get some work done.  I've seen some posts about disabling RAID windows side, install Ubuntu (it wasn't Saucy, though), then re-enable RAID on windows.  Worth a shot in your opinion?

---

### Post by oldfred on 2014-02-11
Did you install RAID driver before mounting RAID partition?

You can try turning off RAID, but then grub will install to MBR, which when you turn RAID back on will not work.

---

### Post by vitale232 on 2014-02-11
> **oldfred said:**
> Did you install RAID driver before mounting RAID partition?
Oops, no.  I'll have to do that and try again.

> You can try turning off RAID, but then grub will install to MBR, which when you turn RAID back on will not work.
Perhaps turning off RAID, installing, turning RAID back on, then following that example you linked previously?  I basically want the most straight forward route to install, as I'm a rook at this stuff.  But I definitely want Ubuntu on this PC, because I have a huge crush on it.

---

### Post by oldfred on 2014-02-11
Becuase I really do not know RAID, I cannot offer anything but suggestions, not real solutions.

One option may be to just install the server version. You then can install any desktop you want.

Bit older now showing different destops.
 Ubuntu 13.04 Desktop Comparison: 6 Desktops, 5 Driver/GPU Combinations
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_raring_desktops1&num=1)


 The key meta packages of Ubuntu are :
ubuntu-base (the whole base system which everybody should install)
ubuntu-desktop (the whole gnome environment)
kubuntu-desktop (the whole kde environment)
xubuntu-desktop (the whole xfce4 environment)
lubuntu-desktop (the whole LXDE desktop environment)
edubuntu-desktop (the whole kids/schools oriented gnome environment)
# choose version and install
sudo apt-get install ubuntu-desktop

---

### Post by vitale232 on 2014-02-12
This message is coming to you from Ubuntu!

I found a post talking about how easy it is to install a dual boot on a RAID0 (my system) with the alternate CD.  Unfortunately, Canonical has dropped the alternate CD for Saucy.  I took the easy way out and installed the LTS version, Precise, since it has the alternate ISO available for download.  It probably makes more sense, anyways, since it's a work computer and all.

When I finished the install, GRUB menu came up no problem.  I booted into Ubuntu, but all that existed was a bash terminal - no desktop.  I installed ubuntu-desktop and was good to go.  I've been into Windows and back, and everything seems to be functioning properly.

Thanks for sticking with me!

---

### Post by Bucky Ball on 2014-02-12
Fantastic news! Never fear, LTS is directly upgradeable to LTS, leapfrogging the interims, which means 12.04 upgrades to 14.04 LTS with a couple of clicks and hours if you want to go there when 14.04 LTS is released in April. 12.04 is supported until April 2017 and 16.04 LTS will be released by then. 

Yes, for work, production, servers, LTS is the go. That's the idea and one of the reasons you can upgrade LTS>LTS. You only need to do it every five years so there is very little downtime. ;)

---

### Post by vitale232 on 2014-02-12
> **Bucky Ball said:**
> ...Never fear, LTS is directly upgradeable to LTS, leapfrogging the interims...

That right there is some good news!  See you around the forums.

---

