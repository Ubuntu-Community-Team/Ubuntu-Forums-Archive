---
title: "Ubuntu 12.04 bootloader error"
date: 2012-08-14
forum: Installation &amp; Upgrades
---

### Post by Askags on 2012-08-14
Hi!

I am trying to install ubuntu 12.04 on my system but it is constantly giving me bootloader install fail error.
I have tried to lot to solve this issue but reading articles over the internet but still no gain.

Firstly since the bootloader was not getting installed I tried to install it on all the alternative paths given in the installer, failing with I selected install ubuntu with bootloader.

Then I tried to manually install bootloader via terminal at try ubuntu via grub-install, but I was not able to do that. Then I tried using boot-repair and it was also not able to install the bootloader because after it my system shows grub-rescue.

I tried to use boot-repair and install bootloader on a seperate partition mounted to /boot and still my system is booting and it shows grub-rescue.

The error which my system shows during boot is:

Error : no such device : 04ac0510-bd4f-43b8-b885-b885-11c4dec21db8

I am not dual booting and ubuntu is the only OS I am installing.

I am using Raid 0 with two blue western digital hard drive so I am not sure whether it is right or not.

The details given by boot-repair are in the below mentioned link;
[http://paste.ubuntu.com/1147208/](http://paste.ubuntu.com/1147208/)

Please tell me how can I boot my system.

---

### Post by mwl128340 on 2012-08-14
hey there askags, im not exactlt sure what is going on but at the end of the boot repair report there is 2 things that come up. one is that you may have to update your fstab which is possibly the reason your getting the uuid doesnt exist error. and another one says to make sure bios is set to boot from the hard drive containing the linux partition. i have never changed an fstab myself but i do know that it is very important to know what you are changing and why your changing it to that device. have you done either of those changes after boot repair. i saw boot repair did find the OS in the OS-prober during boot repair. these may not be solutions but could be something worth looking into.

---

### Post by Askags on 2012-08-14
> **mwl128340 said:**
> hey there askags, im not exactlt sure what is going on but at the end of the boot repair report there is 2 things that come up. one is that you may have to update your fstab which is possibly the reason your getting the uuid doesnt exist error. and another one says to make sure bios is set to boot from the hard drive containing the linux partition. i have never changed an fstab myself but i do know that it is very important to know what you are changing and why your changing it to that device. have you done either of those changes after boot repair. i saw boot repair did find the OS in the OS-prober during boot repair. these may not be solutions but could be something worth looking into.

Hi!

Thanks for the reply, my bios is set to boot with hard disk, bit I have no clue about fstab.
Can u tell me what kind of changes do I need to make on fstab and how to do that. Sorry I am complete noob in this area.

---

### Post by mwl128340 on 2012-08-14
i dont really know enough to give out advice myself. but i did some research because i wasnt really sure myself about the fstab and have included a few links. although if i was you, just a simple google search for fstab in ubuntu with raid would probably be a start cuz id recommend reading at least a few articles first before even looking at your fstab let alone change it. and maybe by then someone might see something else your issue could be.
[HTML]http://www.howtogeek.com/howto/38125/htg-explains-what-is-the-linux-fstab-and-how-does-it-work/[/HTML] [HTML]https://sites.google.com/site/installationubuntu/tweaking-ubuntu/fstab[/HTML] although i would research more than this to find out if the fstab is the issue. after reading a few articles from start to finish youll have a much better understanding.

---

### Post by mwl128340 on 2012-08-14
have you installed dmraid since installation.[https://help.ubuntu.com/community/FakeRaidHowto#Troubleshooting:_User_Contributions]("https://help.ubuntu.com/community/FakeRaidHowto#Troubleshooting:_User_Contributions")

---

### Post by Askags on 2012-08-15
Hi!

I made one more change I installed ubuntu again and this time I installed the bootloader at a different partition on /boot.
After this the bootloader error has gone but I am still not able to boot to ubuntu as I get the same error I was getting before.

---

### Post by Askags on 2012-08-15
> **mwl128340 said:**
> have you installed dmraid since installation.[https://help.ubuntu.com/community/FakeRaidHowto#Troubleshooting:_User_Contributions]("https://help.ubuntu.com/community/FakeRaidHowto#Troubleshooting:_User_Contributions")

Hi!

No I have not installed dmraid, it is neccessary for Raid0, i thought ubuntu already has Raid drivers. Moreover in the link provided I am not able to get installation instructions for 12.04, so I used the one for 10.04 and selected to install bootloader at the partitions from the dropdown. This time the installation finished normally without an error but still I am not able to boot my system as the same error shows during booting this time also.

---

### Post by mwl128340 on 2012-08-15
which guide(if you used one) did you use for assistance in installing your ubuntu. the installation should be about the same for most distros and you said you were using raid0 in your first post. i have been doing a little research lately and any info on how you partitioned the drives would be very useful. you didnt make any mention of using the alternate install cd, just wondering if you did use it

---

### Post by Askags on 2012-08-15
> **mwl128340 said:**
> which guide(if you used one) did you use for assistance in installing your ubuntu. the installation should be about the same for most distros and you said you were using raid0 in your first post. i have been doing a little research lately and any info on how you partitioned the drives would be very useful. you didnt make any mention of using the alternate install cd, just wondering if you did use it

I didn't use any alternate install cd and for partition I used gparted in the live cd session.
I was reading many articles and I dont remember the exact guide I used.

---

### Post by mwl128340 on 2012-08-15
ok and did you set the raid up in bios or are you going to use a software raid

---

### Post by Askags on 2012-08-15
I just got a mail from boot-repair team an they said "try to place the /boot partition OUTSIDE the RAID".

Now since the Raid on my pc is activated from boot I have no idea on how to keep any partition outside Raid. Any help for this?

---

### Post by Askags on 2012-08-15
> **mwl128340 said:**
> ok and did you set the raid up in bios or are you going to use a software raid

In BIOS

---

### Post by mwl128340 on 2012-08-15
since you did another install, could you run another bootinfoscript and post the results.[http://sourceforge.net/projects/bootinfoscript/]("http://sourceforge.net/projects/bootinfoscript/")

---

### Post by oldfred on 2012-08-15
I do not know RAID, but your sdb drive says it is RAID in one place and in another it has a totally different partition table with FAT16 partitions. It looks like you have some RAID issues to resolve first.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer)
With Linux RAID & LVM 
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

---

### Post by Askags on 2012-08-15
> **oldfred said:**
> I do not know RAID, but your sdb drive says it is RAID in one place and in another it has a totally different partition table with FAT16 partitions. It looks like you have some RAID issues to resolve first.

[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuServer)
With Linux RAID & LVM 
[https://help.ubuntu.com/12.04/serverguide/advanced-installation.html](https://help.ubuntu.com/12.04/serverguide/advanced-installation.html)

Hi!

I have formatted the disk completely and have only ext4 formatted partition.
I am confused between using the Raid from BIOS or software Raid. I habe no idea about software Raid but BIOS Raid was working perfectly fine in Windows 7.

If you still think that my hard drive currently has Fat16 area, can you tell me how to remove it?
Also should I stop BIOS Raid and continue without Raid right now? If so where can I configure it in ubuntu installation?

---

### Post by Askags on 2012-08-15
> **mwl128340 said:**
> since you did another install, could you run another bootinfoscript and post the results.[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

The output of bootinfoscript is here under:
```
                  Boot Info Script 0.61      [1 April 2012]


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Grub2 (v1.99) is installed in the MBR of 
    /dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b080000 and 
    looks at sector 1 of the same hard drive for core.img. core.img is at this 
    location and uses an embedded config file:
    
    ---------------------------------------------------------------------------
    search.fs_uuid 9c33d000-2ffd-4a37-8653-460b615ac2d0 root 
    set prefix=($root)/grub
    ---------------------------------------------------------------------------
    -----.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''

ddf1_00000000000000004b1b92914b1b92913b0800003b0800001: ________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

ddf1_00000000000000004b1b92914b1b92913b0800003b0800002: ________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

ddf1_00000000000000004b1b92914b1b92913b0800003b0800003: ________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info: 
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1                  63   976,768,064   976,768,002  83 Linux


Drive: ddf1_00000000000000004b1b92914b1b92913b0800003b080000 _____________________________________________________________________

Disk /dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b080000: 1000.0 GB, 1000047902720 bytes
255 heads, 63 sectors/track, 121582 cylinders, total 1953218560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b0800001              2,048     2,050,047     2,048,000  83 Linux
/dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b0800002   *      2,050,048 1,891,778,559 1,889,728,512  83 Linux
/dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b0800003      1,891,778,560 1,953,218,559    61,440,000  82 Linux swap / Solaris


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b080000p1 9c33d000-2ffd-4a37-8653-460b615ac2d0   ext4       
/dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b080000p2 69d41c00-d749-48e1-a44f-a2e1900aee70   ext4       
/dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b080000p3 5f3107d7-a31e-4afb-942e-5012a5a94871   swap       
/dev/sda                                                ddf_raid_member 
/dev/sdb                                                ddf_raid_member 
/dev/sr0                                                iso9660    Ubuntu 12.04 LTS amd64

========================= "ls -R /dev/mapper/" output: =========================

/dev/mapper:
control
ddf1_00000000000000004b1b92914b1b92913b0800003b080000
ddf1_00000000000000004b1b92914b1b92913b0800003b080000p1
ddf1_00000000000000004b1b92914b1b92913b0800003b080000p2
ddf1_00000000000000004b1b92914b1b92913b0800003b080000p3

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on ddf1_00000000000000004b1b92914b1b92913b0800003b0800001


Unknown BootLoader on ddf1_00000000000000004b1b92914b1b92913b0800003b0800002


Unknown BootLoader on ddf1_00000000000000004b1b92914b1b92913b0800003b0800003



========= Devices which don't seem to have a corresponding hard drive: =========

sdb: "isw" and "ddf1" formats discovered (using ddf1)! sda: "isw" and "ddf1" formats discovered (using ddf1)! 

=============================== StdErr Messages: ===============================

ERROR: ddf1: wrong # of devices in RAID set "ddf1_00000000000000004b1b92914b1b92913b0800003b080000" [1/2] on /dev/sdb
ERROR: ddf1: wrong # of devices in RAID set "ddf1_00000000000000004b1b92914b1b92913b0800003b080000" [1/2] on /dev/sda
ERROR: only one argument allowed for this option
xz: (stdin): Compressed data is corrupt
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b0800001: No such file or directory
hexdump: /dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b0800001: No such file or directory
hexdump: /dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b0800002: No such file or directory
hexdump: /dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b0800002: No such file or directory
hexdump: /dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b0800003: No such file or directory
hexdump: /dev/mapper/ddf1_00000000000000004b1b92914b1b92913b0800003b0800003: No such file or directory
ERROR: ddf1: wrong # of devices in RAID set "ddf1_00000000000000004b1b92914b1b92913b0800003b080000" [1/2] on /dev/sdb
ERROR: ddf1: wrong # of devices in RAID set "ddf1_00000000000000004b1b92914b1b92913b0800003b080000" [1/2] on /dev/sda
ERROR: only one argument allowed for this option

```

---

### Post by mwl128340 on 2012-08-15
ok, i think i may have found the problem. you said windows worked fine with your array. turns out(this is all new to me so we both learned) that with onboard bios raid controllers require a driver that is included with the mobo but usually are only windows drivers. you may be able to find linux drivers for the raid controller on your mobo website, although i have an msi and all they had was windows drivers(figures). if your raid was working then you should have seen only the one drive during installation, instead of two. and as it turns out and makes alot of sense, when using fake raid your actually using fake and software raid at the same time(windows drivers i think). ive included a link that really breaks it down and made me really understand about raid and linux. your best and easiest bet would be to not use raid through bios but a software raid that looks like ubuntu should set up nicely during the installation. [http://ubuntuforums.org/showthread.php?t=408461]("http://ubuntuforums.org/showthread.php?t=408461")

---

### Post by Askags on 2012-08-16
well its been impossible for me to use ubuntu over Raid so now I have decided to use it without Raid and its working fine.

---

### Post by YannBuntu on 2012-08-16
Good job.

---

