---
title: "Unable to boot xp after installing Ubuntu"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by Art1x on 2008-11-06
Hello guys, new to this forum.

Well problem here.. I have a dual boot Vista/XP computer, and I decided to install Ubuntu (intrepid) on it. I used ubuntu to create two partitions in between my Vista and XP partition (well my hard disk's gone through various random partitioning processes), and right now it looks like this:

[IMG]http://www.fileden.com/files/2006/9/8/209083/partition.jpg[/IMG]

The 9.76GB is the recovery partition, and the 3GB and 27GB partitions are the swap space and ubuntu partitions respectively. (I also don't know how I got 5 partitions -.-)

Well now Vista and ubuntu works well (except for my stupid nvidia card..), but I can't boot my XP. When I tried to start XP up, a message saying "hal.dll file is missing. please reinstall a copy of the file" popped up. I understand that this should result from an error in the boot.ini file (I think?), but I don't know what to do as I'm scared that using the recovery disc will screw up my booting process.

Suggestions, anyone? Thanks a lot.

SOLVED

---

### Post by Pumalite on 2008-11-06
The ideal order of installation for that special triple boot is: XP, Vista; Ubuntu.

---

### Post by Art1x on 2008-11-06
Err.. So am I supposed to reinstall everything? >< That will be sick.

Is there no way I can save my XP ><

---

### Post by tommcd on 2008-11-06
> **Art1x said:**
> 
Is there no way I can save my XP ><

I assume you are booting with grub installed to the MBR, is that correct?
If so, check your Windows XP entry in grub against mine:
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
The **root (hd0,0)** part will be different according to what partition XP is on.
Here is some info I found about 'missing hal.dll' and how to recover it:
[http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm](http://pcsupport.about.com/od/findbyerrormessage/a/missinghaldll.htm)
[http://www.kellys-korner-xp.com/xp_haldll_missing.htm](http://www.kellys-korner-xp.com/xp_haldll_missing.htm)

---

### Post by caljohnsmith on 2008-11-06
> **Art1x said:**
> ... but I can't boot my XP. When I tried to start XP up, a message saying "hal.dll file is missing. please reinstall a copy of the file" popped up. I understand that this should result from an error in the boot.ini file (I think?), but I don't know what to do as I'm scared that using the recovery disc will screw up my booting process.

You're absolutely right, one cause of a "missing hal.dll" error is if the boot.ini file points to the wrong partition for Windows. How about opening a terminal (Applications > Accessories > Terminal) and posting:
```
sudo fdisk -lu
```
Also, please post the Windows XP entry that you are using in your /boot/grub/menu.lst. And for whichever is your Windows XP partition, for instance sda3, do:
```
sudo mount /dev/sda3 /mnt
cat /mnt/boot.ini
```
And replace sda3 above with your XP partition. Please post the output of that and we can work from there.

---

### Post by Art1x on 2008-11-07
I'm sorry but I'm quite a noob at this, so I'll try my best..

Yes I'm using grub as my bootloader. However it's kinda weird because 3 windows entries are added inside but I can only use 2. These are my windows entries:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista Recovery Disk
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Windows Vista/Longhorn (loader)
root		(hd0,4)
savedefault
makeactive
chainloader	+1

```

The first one is the recovery partition, the second one leads me to the multiboot options between Vista and XP and the third one (supposedly XP) actually leads me an error 12 or something, saying that it's not found. I get the hal.dll error when I try to boot XP from the second loader followed by choosing XP.

This is what I get from sudo fdisk -lu:

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xf1729d35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63    20466809    10233373+  12  Compaq diagnostics
/dev/sda2   *    20467712   333178871   156355580    7  HPFS/NTFS
/dev/sda4       333188161   488395119    77603479+   f  W95 Ext'd (LBA)
/dev/sda5       396098703   488395119    46148208+   7  HPFS/NTFS
/dev/sda6       333188163   339485579     3148708+  82  Linux swap / Solaris
/dev/sda7       339485643   396098639    28306498+  83  Linux

Partition table entries are not in disk order
```

And this is my XP boot.ini file:

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(5)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(5)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

The boot.ini file actually had multi(0)disk(0)rdisk(0)partition(4), but I figured that as I installed 2 partitions in the middle of my disk it might be shifted instead or something. I'm not sure but I can change it back right?

Once again, thanks so much for helping. Really appreciate it.

---

### Post by caljohnsmith on 2008-11-08
Art1x, so was XP's boot.ini file in sda2 I assume? If so, you should make the partition number 2, not 5, in your boot.ini file:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition([COLOR="Red"]2[/COLOR])\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition([COLOR="Red"]2[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```
Then you should be able to boot XP from the Vista boot loader screen. I should mention though that if you would prefer not to go through two boot loader screens to get to XP (Grub > Vista boot loader), it is possible to separate Vista's boot files from XP, and then you can just boot Vista/XP directly from Grub. If you are interested in doing that, let me know, otherwise I think the above change to your boot.ini file should work. :)

---

### Post by Art1x on 2008-11-08
Nope, actually the XP boot.ini file was in sda5. sda2 is my Vista partition..

Is it because I have five partitions that's why XP couldn't recognize itself as a partition or whatsover? I read somewhere that a 'normal' hard disk can only have a max of 4 partitions..

if I delete the swap space so that I only have 4 partitions, will it work? Or not haha.

And yeah I would really appreciate if you would teach me to boot XP directly from grub. Thanks so much! :D

---

### Post by caljohnsmith on 2008-11-08
Do you also have the files "ntldr" and "NTDETECT.COM" in sda5? If those files are in sda2, then please move them to sda5. Next modify your boot.ini so that the partition number is 3:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition([COLOR="Red"]3[/COLOR])\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition([COLOR="Red"]3[/COLOR])\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```
And next you'll need to change your menu.lst to use the following entry to boot Windows XP:
```
title Windows XP
rootnoverify (hd0,4)
chainloader +1
```
Then try booting Windows XP from Grub. It may be that we will have to fix the boot sector of the Windows XP partition, but let me know first exactly what happens when you boot XP from Grub using the entry I gave above.

---

### Post by Art1x on 2008-11-09
Yups I have ntldr and NTDETECT.COM in my XP root folder, I copied them when I was trying to make Vista/XP dual boot before I installed Ubuntu.

For the changing of menu.lst, do I change root (hd0,4) to rootnoverify (hd0,4)? I did that but the same error message showed up when I was trying to boot XP form grub:

```
Error 12: Invalid device requested

Press any key to continue..
```

Oh and I just realised I don't have an sda3 lol

---

### Post by Pumalite on 2008-11-09
Probably you are trying to boot Windows from a logical partition. Not imposible, but tricky:

[http://users.bigpond.net.au/hermanzone/p15.htm#12_](http://users.bigpond.net.au/hermanzone/p15.htm#12_)

---

### Post by caljohnsmith on 2008-11-09
Did you use the exact Grub menu entry that I gave in post #9 to boot Windows? You need to make sure you don't have the "makeactive" line, which is why you may be getting that Grub error. Try booting Windows with the entry I gave in post #9 and let me know the results.

---

### Post by Art1x on 2008-11-09
@pumalite: Yes I'm trying to boot my XP from the logical partition, I'm still reading the grub page to look for more info. Will post results when I can.

@caljohnsmith: Oops I'm so sorry! Okay I changed it (removed the lines savedefault and makeactive) and now I get this error:

```
Starting up..

A disk read error occured.
Press Ctrl+Alt+Del to restart.
```

My grub entry is something like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda5
title		Windows Vista/Longhorn (loader)
rootnoverify	(hd0,4)
chainloader	+1
```

edit: omg this is scary according to the grub page the disk read error is sign of failing hard disk?! I'm quite scared now. My XP partition is at the end of the hard disk..

---

### Post by caljohnsmith on 2008-11-09
OK, that "Starting up..." error is usually due to the file system parameters being incorrect in the Windows boot sector, and the good news is that "testdisk" can usually fix that problem. From a terminal in Ubuntu, do:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk, choose "no log", choose the correct HDD and "proceed", choose "intel", choose "advanced", select the Windows XP partition, choose "boot", then choose "Rebuild BS"; if testdisk gives you an error about boot sectors not matching, then choose "write". After you are done doing the "rebuild BS" in testdisk, reboot and let me know what happens. 

I should mention that I'm also a little concerned to about the disk read error, so do you have your Windows Install CD handy? We might need that.

---

### Post by Art1x on 2008-11-09
Firstly thanks so much.

Okay I got the testdisk working and I'm currently rebuilding my boot sector.. I encountered the non-matching bootsector and I chose write. Then I restarted the rebuilding thing and this appeared:

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
     Partition                  Start        End    Size in sectors
 5 L HPFS - NTFS          24656   1  1 30401  48 31   92296417 [XPROX]

filesystem size           92296417
sectors_per_cluster       8
mft_lcn                   786432
mftmirr_lcn               5767331
clusters_per_mft_record   -10
clusters_per_index_record 1
Extrapolated boot sector and current boot sector are identical.







[  Dump  ]  [  List  ]  [  Quit  ]

                           List directories and files
```

What should I do?

---

### Post by caljohnsmith on 2008-11-09
You don't need to restart the "Rebuild BS" since you have all ready did it once. Just choose "quit", reboot, and let me know how far you get when you boot Windows. :)

---

### Post by Art1x on 2008-11-09
I BOOTED INTO THE WINDOWS XP PARTITION!

Thanks so much. Really appreciate your help!

Hmm.. So if I want to remove the entry from the Vista-XP dual booting options in the vista bootloader how do I go about doing it? (Sorry I'm asking a lot!)

Once again thanks so much!

---

### Post by caljohnsmith on 2008-11-09
I'm really glad to hear that worked. :) To remove XP from the Vista boot loader, probably the easiest way is with [EasyBCD]("http://neosmart.net/dl.php?id=1"). Give that a shot and let me know how it goes.

---

### Post by Art1x on 2008-11-10
Okay so yesterday night I was so happy and I deleted the XP entry from the vista bootloader and happily pressed the Write Vista Bootloader to MBR option from FreeBSD -.-

I searched online for methods to recover my grub bootloader and I managed to do that by using my Install CD to go into terminal to reinstall using the grub thingy in terminal. So yeah I got my booting stuff correct finally!

Thanks so much for your help!

---

### Post by Art1x on 2008-11-11
Omg something wrong occured again. I didn't test my XP partition after I fixed my MBR, and now when I try to boot into XP I go to vista (as in when I selected "windows xp" in grub vista came up instead). I checked my menu.lst, nothing's changed, testdisk didn't show any errors, XP's boot.ini is the same as before.. Do I need to recopy some files or is it my XP partition that has a corrupted bootloader?

---

### Post by caljohnsmith on 2008-11-11
OK, so just to check, is your Windows XP entry in Grub using (hd0,4) I assume? If that is true, and if you are still booting into Vista, then that probably means your Vista boot files are in sda5; also, the sda5 boot sector would have to be a Vista boot sector rather than an XP one I think. How about booting your Windows Install CD, go to the "recovery console", and do:
```
map
```
That will show the drive letters of your partitions, and you want to find the drive letter of the XP partition (most likely D); then do:
```
fixboot D:
```
And replace D if XP's drive letter is different. Then from Ubuntu, please post the output of:
```
sudo mkdir /mnt/sda2 /mnt/sda5
sudo mount /dev/sda2 /mnt/sda2
sudo mount /dev/sda5 /mnt/sda5
ls -l /mnt/sda2 /mnt/sda5
```
Note "-l" is a lowercase L, not a one. Do you also have your Vista Install CD? If not, you can download a Vista Recovery CD from [here]("http://neosmart.net/blog/2008/download-windows-vista-x64-recovery-disc/"), because you will most likely need that. Let me know how it goes.

---

### Post by Art1x on 2008-11-11
I used the XP Install CD, I went to the recovery console, then it asked me "which windows installation would you like to boot into", so I tried both, and it asked for my administrator password. Strange, since I do not have administrator passwords on both my Windows installations.

I tried a variety of passwords like admin, administrator, not typing anything, my own account's password, but all doesn't work. So now I'm practically stuck -.-

Anyway, one interesting thing is that as I chose the No GUI Boot for my vista, when I chose vista in grub it booted up with that nice picture but when I chose xp and vista booted up it used the default loader (just a loading bar).

I still don't understand why this happened, is it because when I clicked on the write vista boot MBR it also overwritten my XP boot sector or something. I was able to boot into the XP partition before I deleted the XP selection from my vista bootloader.

---

### Post by caljohnsmith on 2008-11-11
You could probably use EasyBCD to add XP back to the Vista boot loader if you want, but if you want to boot Vista and XP separately from Grub, then please post the output of those commands I gave in my last post. Also, when the XP install CD asks for your admin password, have you tried just leaving it blank and hitting enter? I think that is what I have to do with my XP, because I don't have an admin password set either.

---

### Post by Art1x on 2008-11-12
I did it finally I removed the need for password for the recovery console through accessing the registry from vista.

```
/mnt/sda2
total 2097968
-rwxrwxrwx 2 root root       3913 2008-01-03 21:34 -20080103.log
-rwxrwxrwx 1 root root         24 2006-09-19 05:43 autoexec.bat
drwxrwxrwx 1 root root      24576 2008-10-31 12:30 $AVG8.VAULT$
drwxrwxrwx 1 root root          0 2007-07-08 03:44 Book
drwxrwxrwx 1 root root       4096 2008-03-22 12:14 Boot
-rwxrwxrwx 1 root root        211 2008-11-12 11:27 boot.ini
-rwxrwxrwx 1 root root     333203 2008-01-18 23:45 bootmgr
-rwxrwxrwx 1 root root       8192 2007-07-08 03:46 BOOTSECT.BAK
-rwxrwxrwx 1 root root        512 2007-12-17 06:38 CHAIN0
-rwxrwxrwx 3 root root         10 2006-09-19 05:43 config.sys
drwxrwxrwx 1 root root          0 2006-11-02 21:02 Documents and Settings
drwxrwxrwx 1 root root       4096 2007-07-08 05:30 DRV
drwxrwxrwx 1 root root          0 2008-07-08 17:10 found.000
-rwxrwxrwx 1 root root 2145837056 2008-11-12 23:38 hiberfil.sys
drwxrwxrwx 1 root root          0 2007-07-08 04:02 Intel
-rwxrwxrwx 1 root root          0 2008-01-03 15:41 IO.SYS
-rwxrwxrwx 1 root root         91 2008-01-03 19:51 MCEDS.log
-rwxrwxrwx 1 root root         91 2008-01-03 19:50 MDisc.log
-rwxrwxrwx 1 root root         91 2008-01-03 19:50 MDR.log
-rwxrwxrwx 1 root root         10 2008-01-02 22:06 Medion.ini
-rwxrwxrwx 1 root root          0 2008-01-03 15:41 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-06-11 15:03 msdownld.tmp
-rwxrwxrwx 1 root root      47564 2001-08-18 20:00 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2001-08-18 20:00 ntldr
drwxrwxrwx 1 root root          0 2008-03-22 12:06 PerfLogs
-rwxrwxrwx 1 root root         91 2008-01-03 19:50 PMovie.log
-rwxrwxrwx 1 root root        437 2008-01-03 19:50 PowerDV.log
drwxrwxrwx 1 root root       8192 2008-11-04 19:04 ProgramData
drwxrwxrwx 1 root root      28672 2008-11-06 12:06 Program Files
drwxrwxrwx 1 root root          0 2008-01-02 22:03 $RECYCLE.BIN
drwxrwxrwx 1 root root          0 2008-01-08 14:44 RECYCLER
-rwxrwxrwx 1 root root        420 2007-07-08 04:07 RHDSetup.log
-rwxrwxrwx 1 root root         90 2008-01-03 19:51 SDMA.log
-rwxrwxrwx 1 root root        178 2007-07-08 04:46 setup.log
drwxrwxrwx 1 root root       8192 2008-11-12 19:19 System Volume Information
drwxrwxrwx 1 root root       4096 2008-07-06 18:55 Users
-rwxrwxrwx 2 root root    1690322 2007-07-08 05:01 vcredist_x86.log
drwxrwxrwx 1 root root      32768 2008-11-11 17:43 Windows

/mnt/sda5:
total 1054
drwxrwxrwx 1 root root   4096 2008-01-03 19:33 Boot
-rwxrwxrwx 1 root root    211 2008-11-09 23:55 boot.ini
-rwxrwxrwx 1 root root 333203 2008-01-18 23:45 bootmgr
drwxrwxrwx 1 root root   4096 2008-06-13 14:15 Common Folder
drwxrwxrwx 1 root root   4096 2008-01-03 17:02 Documents and Settings
-rwxrwxrwx 2 root root 305672 2008-06-11 14:59 dxwebsetup.exe
-rwxrwxrwx 1 root root  47564 2001-08-18 20:00 NTDETECT.COM
-rwxrwxrwx 1 root root 250032 2001-08-18 20:00 ntldr
drwxrwxrwx 1 root root  24576 2008-11-09 23:56 Program Files
drwxrwxrwx 1 root root      0 2008-01-03 19:42 $RECYCLE.BIN
drwxrwxrwx 1 root root      0 2008-01-05 22:00 RECYCLER
-rwxrwxrwx 2 root root    268 2008-11-09 23:46 sqmdata00.sqm
-rwxrwxrwx 2 root root    244 2008-11-09 23:46 sqmnoopt00.sqm
drwxrwxrwx 1 root root   4096 2008-01-03 15:44 System Volume Information
drwxrwxrwx 1 root root  90112 2008-11-09 23:51 WINDOWS

```

---

### Post by caljohnsmith on 2008-11-12
OK, part of the problem is that you have Vista boot files in both sda2 and sda5. But f you can run that "fixboot" command on your Windows XP partition, you will probably be able to boot XP just fine, because the fixboot command will rewrite the XP partition boot sector so that it boots the XP "ntldr" boot file instead of the "bootmgr" boot file used in Vista. Just make sure you run fixboot on the XP partition, and not the Vista one.

---

### Post by Art1x on 2008-11-12
Ok let me try booting XP and I'll edit this post..

edit: I'm done! I got XP working again. Thanks so much!

---

### Post by caljohnsmith on 2008-11-12
That's great news, glad it's all working now. One last thing you could do if you want is delete the "boot" directory and the "bootmgr" file from your XP partition, since those are Vista's boot stuff. Anyway, cheers and have fun with all your OSes. :)

:popcorn:

---

