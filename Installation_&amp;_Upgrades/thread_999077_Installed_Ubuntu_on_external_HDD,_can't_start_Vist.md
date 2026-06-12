---
title: "Installed Ubuntu on external HDD, can't start Vista now"
date: 2008-12-01
forum: Installation &amp; Upgrades
---

### Post by feigerou on 2008-12-01
I'm totally new to Ubuntu (and Linux all-together) but was very interested after running the Live CD. I have a 160GB hard drive in a USB enclosure, and wanted to install it there to check it out without screwing with Windows Vista (Vista does that on its own). I had heard that installing Ubuntu on an external hard drive would sometimes overwrite the master boot record (not totally sure what that is), so I removed the Windows HDD from my laptop and put in my 160GB HDD in the laptop. Then I installed Ubuntu 7.10 onto the HDD. Now I can run Ubuntu with no problems from the USB HDD but when I try to boot up to Windows without the USB HDD plugged in, nothing happens.

Did I miss something? I am having problems with Vista right now, so this could also be an issue with that. I just wanted to get some input as to whether this is an Ubuntu or master boot record issue that I needed to address before I can get Vista to work again.

Any ideas as to what caused the problem or how to fix it would be greatly appreciated. Keep in mind that I'm new to this stuff and have no familiarity with the Linux/Ubuntu command line.

Thanks,
Andy

---

### Post by nvance on 2008-12-01
Greetings,

When you have your Vista HDD plugged in, are you getting any error message when you boot?  Also, does it make a difference if you have the USB drive plugged in when you are booting Vista (does Ubuntu boot instead)?  Another thing, when you are booted into Ubuntu does it see your other HDD?

Sorry for the all the questions but hopefully we can figure something out.

---

### Post by cariboo on 2008-12-01
I would suggest following this howto:

[http://ubuntuforums.org/showthread.php?t=80811](http://ubuntuforums.org/showthread.php?t=80811)

it will mean reinstalling unfortunately. This is for older versions, but it should still work the same.

Jim

---

### Post by feigerou on 2008-12-01
> **nvance said:**
> 
When you have your Vista HDD plugged in, are you getting any error message when you boot?  Also, does it make a difference if you have the USB drive plugged in when you are booting Vista (does Ubuntu boot instead)?  Another thing, when you are booted into Ubuntu does it see your other HDD?

I have my computer set to boot up to a USB hard drive before the main hard drive, so if my Ubuntu HDD is plugged in it will start Ubuntu 7.10.  If I put my Vista HDD either in the laptop (external HDD unplugged) or in the enclosure and plugged in, it won't start.  I get the Gateway startup screen and then instead of a screen saying Windows with a progress bar, I get a black screen with a blinking cursor at the top left corner.  Nothing happens and I end up shutting the computer off by holding down the power button.  As for when I'm running Ubuntu, I don't think that it sees my Vista HDD.  I'll check tonight.

Let me know if this opens up any options.  I'll also look into this referred post with installation instructions, but I'm hoping to avoid re-installing Ubuntu if I can.

Thanks

---

### Post by caljohnsmith on 2008-12-01
Since you removed the Vista drive when you installed Ubuntu, Ubuntu would not have modified the MBR of the Vista drive. It sounds like you are simply having a problem with the Vista drive at this point. I would reseat its cable connection just to make sure it's secure and tight, and also you could try tweaking your BIOS settings for the Vista drive. I'm thinking that when you removed the Vista drive, that might have reset the BIOS back to default as far as any special configuration needed for the Vista drive, so tweaking your BIOS might be necessary at this point to get it working again. 

If you open a terminal in Ubuntu (Applications > Accessories > Terminal), and do:
```
sudo fdisk -l
```
That should show both your Ubuntu and Vista drives. If it doesn't, then you most likely have a hardware/BIOS issue with the Vista drive. Good luck and let us know how it goes. :)

---

### Post by feigerou on 2008-12-01
alright, I ran fdisk and it looks like Ubuntu can see the Vista HDD.  Here's the results-

"ubuntu@ubuntu:~$ sudo fdisk -l



Disk /dev/sda: 80.0 GB, 80026361856 bytes

255 heads, 63 sectors/track, 9729 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x5dbeb9a5



   Device Boot      Start         End      Blocks   Id  System

/dev/sda1               1        1152     9253408+   7  HPFS/NTFS

/dev/sda2   *        1153        9729    68894752+   7  HPFS/NTFS



Disk /dev/sdb: 160.0 GB, 160041885696 bytes

255 heads, 63 sectors/track, 19457 cylinders

Units = cylinders of 16065 * 512 = 8225280 bytes

Disk identifier: 0x4e7919bd



   Device Boot      Start         End      Blocks   Id  System

/dev/sdb1            2590       18820   130375507+   7  HPFS/NTFS

/dev/sdb2               1        2589    20796111    7  HPFS/NTFS



Partition table entries are not in disk order"

The first HDD is the Vista one, and it also shows up using the File Browser.  You can ignore the second HDD - it's the Ubuntu HDD that I needed to change the partitions around on, so I'll need to reinstall Ubuntu to it.  I ran this from Ubuntu using the Live CD.

Any ideas on what to do from here?

---

### Post by caljohnsmith on 2008-12-02
OK, let's do some basic checks on your Vista drive/partition; please post the output of:
```

sudo mount /dev/sda2 /mnt
ls -l /mnt
```
Also do:
```
sudo dd if=/dev/sda count=60 | gzip -c > ~/Desktop/sda.MBR.gz
```
The above command will create a really tiny "sda.MBR.gz" file on your desktop; please attach that file to your next post so I can check that your Windows MBR looks OK (you can attach it by clicking the "paper clip" icon at the top of the Ubuntu forum message box in your web browser).

---

### Post by feigerou on 2008-12-02
Ran the codes you said to run and here's what I got -
> 
&#65279;ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
ubuntu@ubuntu:~$ ls -l /mnt
total 1363690
drwxrwxrwx 1 root root       4096 2008-09-16 01:56 618c97691a81e8e80b9c
drwxrwxrwx 1 root root          0 2007-03-14 04:49 9ba77a84a99decc46510fb04
-rwxrwxrwx 1 root root         24 2006-09-18 21:43 autoexec.bat
-rwxrwxrwx 1 root root         70 2006-04-10 18:51 backup.bat
drwxrwxrwx 1 root root       4096 2008-09-23 01:43 Boot
-rwxrwxrwx 1 root root     333203 2008-01-19 07:45 bootmgr
-rwxrwxrwx 1 root root       8192 2006-06-12 00:36 BOOTSECT.BAK
-rwxrwxrwx 3 root root         10 2006-09-18 21:43 config.sys
-rwxrwxrwx 1 root root    1984512 2006-11-02 09:46 $$DeleteMe.authui.dll.01c7edc672eb0c28.0002
-rwxrwxrwx 1 root root     120320 2006-11-02 09:46 $$DeleteMe.dhcpcsvc6.dll.01c7edc672f95468.0005
-rwxrwxrwx 1 root root     204800 2006-11-02 09:46 $$DeleteMe.dhcpcsvc.dll.01c7edc672ed6d88.0003
-rwxrwxrwx 1 root root     134656 2006-11-02 09:46 $$DeleteMe.dps.dll.01c7edc6739d9348.000c
-rwxrwxrwx 1 root root     286720 2006-11-02 09:46 $$DeleteMe.ipnathlp.dll.01c7edc6738a8848.0007
-rwxrwxrwx 1 root root      38400 2006-11-02 09:44 $$DeleteMe.kmddsp.tsp.01c7edc67398d088.0009
-rwxrwxrwx 1 root root     694272 2006-11-02 09:46 $$DeleteMe.localspl.dll.01c7edc6739b31e8.000b
-rwxrwxrwx 1 root root      49664 2006-11-02 09:44 $$DeleteMe.ndptsp.tsp.01c7edc6739ff4a8.000d
-rwxrwxrwx 1 root root     383488 2006-11-02 09:46 $$DeleteMe.netcfgx.dll.01c7edc673966f28.0008
-rwxrwxrwx 1 root root     749568 2006-11-02 09:46 $$DeleteMe.qmgr.dll.01c7edc672b44c88.0000
-rwxrwxrwx 1 root root     467456 2006-11-02 09:46 $$DeleteMe.riched20.dll.01c7edc6739b31e8.000a
-rwxrwxrwx 1 root root     269312 2006-11-02 09:46 $$DeleteMe.schannel.dll.01c7edc672efcee8.0004
-rwxrwxrwx 1 root root   11314688 2006-11-02 09:46 $$DeleteMe.shell32.dll.01c7edc672fe1728.0006
-rwxrwxrwx 1 root root     712192 2006-11-02 09:46 $$DeleteMe.WindowsCodecs.dll.01c7edc672e8aac8.0001
drwxrwxrwx 1 root root          0 2007-03-05 11:20 Documents
drwxrwxrwx 1 root root          0 2007-03-10 02:04 Documents and Settings
drwxrwxrwx 1 root root       4096 2008-11-22 02:32 found.000
drwxrwxrwx 1 root root          0 2008-11-22 17:49 found.001
drwxrwxrwx 1 root root          0 2008-11-22 19:36 found.002
drwxrwxrwx 1 root root          0 2008-07-30 13:06 google
drwxrwxrwx 1 root root    1212416 2007-03-11 00:48 I386
drwxrwxrwx 1 root root          0 2007-03-05 11:06 Intel
-rwxrwxrwx 1 root root          0 2007-03-25 00:32 IO.SYS
-rwxrwxrwx 1 root root      33436 2007-03-16 01:25 iTrip.xml
drwxrwxrwx 1 root root       4096 2007-03-11 00:48 Mp3Gain
-rwxrwxrwx 1 root root          0 2007-03-25 00:32 MSDOS.SYS
drwxrwxrwx 1 root root      45056 2007-07-08 19:17 Music
drwxrwxrwx 1 root root          0 2007-09-11 03:04 Novell
-rwxrwxrwx 1 root root 1377247232 2008-11-25 23:33 pagefile.sys
drwxrwxrwx 1 root root          0 2008-09-14 20:43 PerfLogs
-rwxrwxrwx 1 root root        163 2007-03-05 11:14 power2go.log
drwxrwxrwx 1 root root       4096 2008-11-06 01:12 ProgramData
drwxrwxrwx 1 root root      20480 2008-11-06 01:10 Program Files
drwxrwxrwx 1 root root          0 2007-03-10 02:08 $RECYCLE.BIN
drwxrwxrwx 1 root root      24576 2008-11-25 03:46 System Volume Information
drwxrwxrwx 1 root root       4096 2007-09-18 02:38 Temp
drwxrwxrwx 1 root root       4096 2008-12-02 04:19 Users
drwxrwxrwx 1 root root      24576 2008-11-25 23:33 Windows

ubuntu@ubuntu:~$ sudo dd if=/dev/sda count=60 | gzip -c > ~/Desktop/sda.MBR.gz

60+0 records in
60+0 records out
30720 bytes (31 kB) copied, 0.342899 seconds, 89.6 kB/s

A second time when I ran the first code I got this response-

> ubuntu@ubuntu:~$ sudo mount /dev/sda2 /mnt
fuse: mount failed: Device or resource busy
FUSE mount point creation failed
Unmounting /dev/sda2 ()

I don't know why I got two different responses but I'm sure it's not good.  Although the terminal is able to read the directories in my Vista drive using the second command line, I can't access it using the File Viewer.

And I've attached the sda.MBR.gz file that I got from the third code line.

Any thoughts on what all of this means? I'm very close to completely reinstalling Windows, but am hoping to figure out what went wrong this time to make sure it doesn't happen next time... or at least I'll know how to fix it.  Thanks for all the help.

---

### Post by caljohnsmith on 2008-12-02
Looks like your Vista partition has at least the basic boot files/directories necessary to boot, so that's not an issue at this point. You mentioned earlier you have your BIOS set to boot the Ubuntu drive before the Vista drive; how about changing your BIOS so that Vista is first in the boot order, and see if that makes any difference. Also, your boot code in the MBR is different than the standard Windows boot code, but it looks like that is because you have a recovery partition on your HDD. The boot code makes reference to pressing F10/F11 to "start recovery", so I'm just curious, but when Vista was working did you see any message like that on start up? 

At some point you could try installing a standard Windows MBR to your drive and see if that makes a difference, but I really don't think that will help since you are simply getting a flashing cursor on start up right now; that would likely indicate that the drive is not even being booted at this point. Are there any jumpers on the drive that you have to set for master/slave/"cable select" or anything like that? That could be an issue. I'm almost positive that based on the symptoms you describe, reinstalling Vista won't help at this point so I wouldn't recommend doing that; but of course it's up to you. Anyway, let me know how it goes.

---

### Post by feigerou on 2008-12-03
When booting up, I can press F10 to access the boot menu and F2 to access the BIOS.  But there's no reference to pressing F11 or any recovery option.

Sounds like my computer is just a pile of electronics with Vista.  Thankfully I got the service plan from Gateway so I'll give them a ring now and have them fix up my computer.  I was hoping to get this issue resolved first, since I thought it might be related to Ubuntu and I'm sure Gateway wouldn't be too happy about that.

I know my computer came with XP before Vista showed up, so I'm going to make sure they give me XP instead this time.  Vista blows.  Then I'll probably set up a dual-boot with Ubuntu.

Thanks for all the help!

---

