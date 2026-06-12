---
title: "Sudden install problems on dell mini 9"
date: 2011-05-14
forum: Installation &amp; Upgrades
---

### Post by starrider1026 on 2011-05-14
Hello all, I've been using various versions of ubuntu (8.10 on up) on my dell mini 9 netbook for a couple years now without any major problems. Unfortunately, that good luck streak seems to have finally run out in a big way.

Earlier this week ubuntu 10.10 NBR pinged me with the update notice to 11.04. I was busy at the time, and didn't get around to updating until yesterday. I let it update as I slept, and woke up this morning to find my netbook unable to boot. I did a format/reinstall of 11.04 and all seemed to work fine, and I left the computer asleep to go do other things. A few hours later I came back and tried to wake up my computer and log in and while I was able to log in, I was met with a flat black screen and the notification that ubuntu had sucessfully connected to my house's wifi. I tried restarting a couple times, and figured I would just reinstall again to see if that would fix it. This time the install failed most of the way through with this error.

```
[errno 30] Read-only file system '/target/opt'
```

It also had some kind blurb underneath the error message talking about how this was generally caused by old hard drives that are failing. This is highly distrubing becasue I literally bought and installed this ssd less than a month ago, with everything working perfectly until today. 

I tried installing 11.04 once more with the same error (but a different filename this time) before I decided to try an earlier version. 9.04, but this install attempt failed aswell telling me what looked like an earlier version of the same error.

At this point i dug up my 10.10 live USB and booted from it using the "try ubuntu" feature, which worked perfectly. I used the disk utility feature which at the time told me that my drive was healthy, and just to be sure I formatted it once more to get rid of any of the past few attempts installation fragments and told it to go ahead and install 10.10. This install failed aswell in the closing stages telling me that grub-update failed to install and that this was a fatal error. It then gave me the option of installing the bootloader to another location, skipping that step, or cancelling the install. Strangely, no matter what option I choose it would not allow me to press ok. After letting it sit for a while and hoping it would make up its mind, I forced it to turn off, removed the battery, replaced it and booted up again using the try ubuntu feature of the live usb. Now however, the disk utility tells me that my drive's status is not supported, and when I try to format the partitions it has i get an error saying

```

Error creating patition table: helper exited with exit 
code 1: in part_create_partition_table: device_file=/dev/seda, scheme=0
got it
got disk
committed to disk
BLKRRPART ioctl failed for dev/sda: Device or resource busy

```

This happens regardless of the filesystem I try to format the drive in. I have tried installing 10.10 again, but recieve the same error at the same time on each attempt. If I try to boot the computer normally after it reaches this point I get a command line based grub interface telling me I can use basic BASH commands for minimal navigation, but have not been able to get anywhere in that interface.

Any help would be hugely appericiated!

---

### Post by Hedgehog1 on 2011-05-14
Because you are having issues like this, but your drive health is good, I am wondering if your partition table is damaged. To find out:

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the [noparse]```
 & 
```[/noparse] tags.

***The Hedge***

:KS

---

### Post by starrider1026 on 2011-05-14
Here is the RESULTS.TXT that I got from running that script.

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => No boot loader is installed in the MBR of /dev/sda

sdb: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Unknown
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.3 GB, 15267151872 bytes
255 heads, 63 sectors/track, 1856 cylinders, total 29818656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System



blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda: PTTYPE="dos" 
/dev/sdb         1C08-221D                              vfat       PENDRIVE                      

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sdb         /cdrom                   vfat       (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown BootLoader  on sdb

00000000  eb 58 90 53 59 53 4c 49  4e 55 58 00 02 04 20 00  |.X.SYSLINUX... .|
00000010  02 00 00 00 00 f8 00 00  3f 00 ff 00 00 00 00 00  |........?.......|
00000020  00 b0 3b 00 bb 1d 00 00  00 00 00 00 02 00 00 00  |..;.............|
00000030  01 00 06 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000040  80 00 29 1d 22 08 1c 4e  4f 20 4e 41 4d 45 20 20  |..)."..NO NAME  |
00000050  20 20 46 41 54 33 32 20  20 20 fa fc 31 c9 8e d1  |  FAT32   ..1...|
00000060  bc 76 7b 52 06 57 1e 56  8e c1 b1 26 bf 78 7b f3  |.v{R.W.V...&.x{.|
00000070  a5 8e d9 bb 78 00 0f b4  37 0f a0 56 20 d2 78 1b  |....x...7..V .x.|
00000080  31 c0 b1 06 89 3f 89 47  02 f3 64 a5 8a 0e 18 7c  |1....?.G..d....||
00000090  88 4d bc 50 50 50 50 cd  13 eb 5c 8b 55 aa 8b 75  |.M.PPPP...\.U..u|
000000a0  a8 c1 ee 04 01 f2 81 fa  b7 07 73 2b f6 45 b4 7f  |..........s+.E..|
000000b0  75 25 38 4d b8 74 20 66  3d 21 47 50 54 75 10 80  |u%8M.t f=!GPTu..|
000000c0  7d b8 ed 75 0a 66 ff 75  ec 66 ff 75 e8 eb 0f 51  |}..u.f.u.f.u...Q|
000000d0  51 66 ff 75 bc eb 07 51  51 66 ff 36 1c 7c b4 08  |Qf.u...QQf.6.|..|
000000e0  cd 13 72 13 20 e4 75 0f  c1 ea 08 42 89 16 1a 7c  |..r. .u....B...||
000000f0  83 e1 3f 89 0e 18 7c fb  bb aa 55 b4 41 8a 16 74  |..?...|...U.A..t|
00000100  7b cd 13 72 10 81 fb 55  aa 75 0a f6 c1 01 74 05  |{..r...U.u....t.|
00000110  c6 06 45 7d 00 66 b8 9a  3b 00 00 66 ba 00 00 00  |..E}.f..;..f....|
00000120  00 bb 00 7e e8 10 00 66  81 3e 24 7e d4 ff 73 72  |...~...f.>$~..sr|
00000130  75 76 ea 38 7e 00 00 66  03 06 60 7b 66 13 16 64  |uv.8~..f..`{f..d|
00000140  7b b9 10 00 eb 2b 66 52  66 50 06 53 6a 01 6a 10  |{....+fRfP.Sj.j.|
00000150  89 e6 66 60 b4 42 e8 7f  00 66 61 8d 64 10 72 01  |..f`.B...fa.d.r.|
00000160  c3 66 60 31 c0 e8 70 00  66 61 e2 da c6 06 45 7d  |.f`1..p.fa....E}|
00000170  2b 66 60 66 0f b7 36 18  7c 66 0f b7 3e 1a 7c 66  |+f`f..6.|f..>.|f|
00000180  f7 f6 31 c9 87 ca 66 f7  f7 66 3d ff 03 00 00 77  |..1...f..f=....w|
00000190  17 c0 e4 06 41 08 e1 88  c5 88 d6 b8 01 02 e8 37  |....A..........7|
000001a0  00 66 61 72 01 c3 e2 c9  31 f6 8e d6 bc 68 7b 8e  |.far....1....h{.|
000001b0  de 66 8f 06 78 00 be df  7d e8 09 00 31 c0 cd 16  |.f..x...}...1...|
000001c0  cd 19 f4 eb fd 66 60 ac  20 c0 74 09 b4 0e bb 07  |.....f`. .t.....|
000001d0  00 cd 10 eb f2 66 61 c3  8a 16 74 7b cd 13 c3 42  |.....fa...t{...B|
000001e0  6f 6f 74 20 65 72 72 6f  72 0d 0a 00 00 00 00 00  |oot error.......|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


```Hope this helps diagnose the issue!

---

### Post by Hedgehog1 on 2011-05-15
***Well, it is not good news.***

Your internal 16 gig drive appears to have an empty/missing partition map:

```
Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 15.3 GB, 15267151872 bytes
255 heads, 63 sectors/track, 1856 cylinders, total 29818656 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System


```

The references to 'sdb' are your LiveCD/LiveUSB.

I think you will need to create the partition map fresh before trying another reinstall.

To do this, use gparted from your LiveCD/LiveUSB, and select this option:

[IMG]http://img534.imageshack.us/img534/9282/mbrpariondemo01.png[/IMG]

[IMG]http://imageshack.us/m/858/9979/mbrpariondemo03.png[/IMG]

Then do a clean install of whatever Ubuntu release level you wish to use.


***The Hedge***

:KS

---

### Post by starrider1026 on 2011-05-16
Unfortunately, while the initial results were promising, this did not work either.

I created the partition table as instructed above, and began the install process for 11.04. Everything went well until the system install portion, where I encountered the following error.

```

Error while installing packages

An error occured while installing packages:
E:Sub-process /usr/bin/dpkg returned an error code (1)

The following packages are in a broken state:



this may be due to an old installer image, or it may be due to a bug in 
some of the packages listed above. More details can be found in /var/log/syslog. 
The installer will try to continue anyway, but may fail at a later point, and will 
not be able to install or remove other packages (possibly including itself) from the 
installed system. You should first look for newer versions of the installer image, 
or failing that contact your distributor.


```

I figured that this may be because I was installing without the system connected to the internet, and thus it was unable to download updates. I attempted to boot up the system as this point, since the install seemed to finish sucessfully anyway, and upon restart was greeted with a plain black screen with a blinking cursor in the top left corner. I was unable to type anything, and so I tried to install again this time connected to the internet. This went well until about halfway through the copying files stage, when I encountered the following error:

```


The installer encountered an error copying files to the hard disk:

[Errno 5] Input/Output error: '/target/usr/lib/syslinux/com32'

This is often due to a faulty hard disk, 
it may help to check whether the hard disk 
is old and in need of replacement, or move 
the device to a cooler environment.


```

Immediately following acknowledgement of this error message, the installer crashed. I rebooted the machine using the live usb, and checked the drive's health using the disk check utility, and it shows it as being all green and healthy.

Any more help would be greatly appreciated. While waiting, I may try to format, and install starting from scratch with the internet active on the machine and see if that helps anything.

---

### Post by starrider1026 on 2011-05-18
Part update and part bump.

I was going to try and install again to see if that would work, however I wanted to format the drive again to get a clean install. This time when I format (running off the live usb) I am told that the drive is being used. This doesn't make sense to me because the install obviously failed and I'm running of a live usb. Thus I have not yet attempted a reinstall yet for fear of another failure and possibly doing more damage to the drive.

Any help would be greatly appreciated.

---

