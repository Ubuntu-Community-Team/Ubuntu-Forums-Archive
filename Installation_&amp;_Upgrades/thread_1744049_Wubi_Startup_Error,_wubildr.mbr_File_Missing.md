---
title: "Wubi Startup Error, wubildr.mbr File Missing"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by Jasonix on 2011-04-30
Well, I installed wubi, ran the installation, and rebooted pc using the wubi program(restart now option). Then, I ran Ubuntu and it states wubildr.mbr is missing :sad:. I can boot into Windows 7 perfectly and uninstalled. Still doesn't work. Any help would be appreciated!

---

### Post by bcbc on 2011-04-30
Where did you install (C: drive? External drive? ). That's a strange problem.

---

### Post by Jasonix on 2011-04-30
> **bcbc said:**
> Where did you install (C: drive? External drive? ). That's a strange problem.
I have many partitions, and the partition with the most space is H:\ drive. Windows is located on C:\
C:\ and most other partitions have much too low disk space.
Any other advice?

UPDATE: I uninstalled ubuntu using wubi, and searched for wubildr.mbr in c:\drive. Even though I installed in h:\ drive previously, the file showed up in C:\Users\Dave\AppData\Local\Temp\pyl9624.tmp\ winboot along with other wubildr related files.

---

### Post by bcbc on 2011-04-30
When you install it in Windows 7, Windows boot manager boots it from the \ubuntu\winboot directory - so in your case it's looking for H:\ubuntu\winboot\wubildr.mbr.

It's highly unlikely that this file doesn't exist... but you can easily check this. What's more likely is that - for some reason - the partition corresponding to the H: drive isn't available at boot time, or it resides physically on an area of the disk that can't be accessed by BIOS functions (some older bios's cannot read beyond 137GB for instance - but this seems unlikely on a machine running windows 7), or perhaps you have some unusual volume management (dynamic disks?).

It's hard to know, but if you can boot from an Ubuntu live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") it might provide more information.

---

### Post by Jasonix on 2011-04-30
> **bcbc said:**
> When you install it in Windows 7, Windows boot manager boots it from the \ubuntu\winboot directory - so in your case it's looking for H:\ubuntu\winboot\wubildr.mbr.

It's highly unlikely that this file doesn't exist... but you can easily check this. What's more likely is that - for some reason - the partition corresponding to the H: drive isn't available at boot time, or it resides physically on an area of the disk that can't be accessed by BIOS functions (some older bios's cannot read beyond 137GB for instance - but this seems unlikely on a machine running windows 7), or perhaps you have some unusual volume management (dynamic disks?).

It's hard to know, but if you can boot from an Ubuntu live CD and run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") it might provide more information.

The thing is, live usb doesn't work for me. Live cd I haven't tried yet. When I run live usb, and I boot up usb first from bios, it says that syslinux.cfg is missing. well, it says that no configuration file is found and I did research and syslinux.cfg is the config file. I'm pretty sure live cd will give similar results to live usb. Therefore, I cannot run ubuntu bootinfoscript. I used pendrivelinux to copy the iso i downloaded on to the disc drive. I downloaded natty, by the way. This is why I used wubi, and the first few times I tried it it work, but monitor says no signal. I found out that I need to run with nomodeset parameters from this thread: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132). When I finally found this I had already uninstalled wubi, so I installed it again but I get this error.
Any suggestions?
P.S.: I really appreciate all of your help.

---

### Post by bcbc on 2011-04-30
Make sure you follow the instructions from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Go to Step 2, and click show me how. I'd be surprised if you had problems with the live CD, provided it's burned correctly (always use the slowest speed).

That's also useful because it can show whether Ubuntu will run on your machine, plus with the bootinfoscript you can analyse your drive.

---

### Post by Jasonix on 2011-04-30
> **bcbc said:**
> Make sure you follow the instructions from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

Go to Step 2, and click show me how. I'd be surprised if you had problems with the live CD, provided it's burned correctly (always use the slowest speed).

That's also useful because it can show whether Ubuntu will run on your machine, plus with the bootinfoscript you can analyse your drive.

I never tried live cd. I tried live USB. That didn't work for me...
It says no configuration file found.
I'll go try live cd now.

---

### Post by Jasonix on 2011-05-01
I'm starting to give up on Ubuntu...
I was able to run live cd, but random freezes happen everytime when trying to run without changes, or installing. I have also tried using nomodeset option on the disc. Any suggestions for this?

---

### Post by wilee-nilee on 2011-05-01
> **Jasonix said:**
> I'm starting to give up on Ubuntu...
I was able to run live cd, but random freezes happen everytime when trying to run without changes, or installing. I have also tried using nomodeset option on the disc. Any suggestions for this?

The cd will run slower, when you get freezes are you using a lot of the resources? The cd is really to confirm that it seems to run so you can decide to install.

I would post that bootscript though before you install, with the mention of a H partition I would wonder what your setup is, and want to make sure you don't brick it.

---

### Post by Jasonix on 2011-05-01
> **wilee-nilee said:**
> The cd will run slower, when you get freezes are you using a lot of the resources? The cd is really to confirm that it seems to run so you can decide to install.

I would post that bootscript though before you install, with the mention of a H partition I would wonder what your setup is, and want to make sure you don't brick it.

No, I'm not using many resources when freezing.
I ran into another problem. To start off, I am using a ralink wireless connecter plugged into usb. When I try Ubuntu, I enter the wep key, and it freezes. A bunch of lines and letters on one row show up. Now, when I load the cd and enter my wep key before clicking try ubuntu or install it, it works. But, when I load up try Ubuntu, it freezes after loading immediately. These crashes probably do not have any relationship to the ones before. Is there any way to get bootscriptinfo without a internet connection in Ubuntu? By the way, I can use windows 7 with the usb wireless and it works perfectly. Can I use windows 7 someway to help get the bootscriptinfo?
Any suggestions would be appreciated!

---

### Post by bcbc on 2011-05-01
I see quite a few threads on freezing with the ralink, e.g.
[http://ubuntuforums.org/showthread.php?t=1593527](http://ubuntuforums.org/showthread.php?t=1593527)
I'm not sure how you can try this solution from the live environmnent (I don't think you can). 

It's unfortunate that you have to struggle like this - I've been fairly fortunate with my hardware - but you're not alone. The fact is some devices aren't well supported on linux. In some cases there's a viable workaround, in others, there isn't.

---

### Post by Jasonix on 2011-05-01
> **bcbc said:**
> I see quite a few threads on freezing with the ralink, e.g.
[http://ubuntuforums.org/showthread.php?t=1593527](http://ubuntuforums.org/showthread.php?t=1593527)
I'm not sure how you can try this solution from the live environmnent (I don't think you can). 

It's unfortunate that you have to struggle like this - I've been fairly fortunate with my hardware - but you're not alone. The fact is some devices aren't well supported on linux. In some cases there's a viable workaround, in others, there isn't.

Can you explain why I wouldn't be able to do that fix?

---

### Post by bcbc on 2011-05-01
> **Jasonix said:**
> Can you explain why I wouldn't be able to do that fix?
That particular fix is blacklisting modules that the kernel loads - on a live CD you cannot save the blacklist file to the CD so when you reboot the changes will  be lost. 

I'm not saying it wouldn't work on a normal install.

---

### Post by Jasonix on 2011-05-01
> **bcbc said:**
> That particular fix is blacklisting modules that the kernel loads - on a live CD you cannot save the blacklist file to the CD so when you reboot the changes will  be lost. 

I'm not saying it wouldn't work on a normal install.

I understand...
So is there a way to get the bootinfo from windows? Like I download with windows and you ubuntu to load it?
I probably need you guys to analyze it so I can be sure it will install fine. Plus, you guys need to analyze it so you can fix my crashes...

---

### Post by bcbc on 2011-05-01
> **Jasonix said:**
> I understand...
So is there a way to get the bootinfo from windows? Like I download with windows and you ubuntu to load it?
I probably need you guys to analyze it so I can be sure it will install fine. Plus, you guys need to analyze it so you can fix my crashes...

Yes, download from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) in windows and save it.
Boot the Ubuntu live environment and mount your windows partition. You can select it either by size or volume label. From Unity, select the Home Folder icon (top left) and you'll see the Label or size in GB of the partition below "Network" on the left panel.
Then it will open it up and you can browse to the location you saved it and copy it to your Downloads folder. (This is probably the simplest). Then drop to a terminal (CTRL+ALT+t) and run it:
```
cd Downloads
sudo bash boot[TAB] (press the TAB key to autocomplete)
```

---

### Post by Jasonix on 2011-05-01
> **bcbc said:**
> Yes, download from [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/) in windows and save it.
Boot the Ubuntu live environment and mount your windows partition. You can select it either by size or volume label. From Unity, select the Home Folder icon (top left) and you'll see the Label or size in GB of the partition below "Network" on the left panel.
Then it will open it up and you can browse to the location you saved it and copy it to your Downloads folder. (This is probably the simplest). Then drop to a terminal (CTRL+ALT+t) and run it:
```
cd Downloads
sudo bash boot[TAB] (press the TAB key to autocomplete)
```

I don't want to mess with windows, so I'll save it to partition I:\ which has nothing on it. I'll hopefully report the .txt file back

---

### Post by Jasonix on 2011-05-01
More problems...
When using the live cd I always lock up in some random place. Are there any boot parameters I can use to help fix this other than nomodeset? Nomodeset locks up, too, just like a nonmodified live cd load up.

Thank you for any future suggestions...

---

### Post by bcbc on 2011-05-01
What computer brand/model do you have?

---

### Post by Jasonix on 2011-05-02
> **bcbc said:**
> What computer brand/model do you have?

It's actually custom(my dad built it) and its old, like 10 years old. I know it has an amd processor, and an ati radeon 9200 se...2 gbs of memory...
And once again, are there any boot parameters to fix this? I don't want to test out each one because one might mess up my system.

---

### Post by Jasonix on 2011-05-03
No one can help?

---

### Post by Jasonix on 2011-05-03
Should I try running 10.04 LTS?

---

### Post by bcbc on 2011-05-03
> **Jasonix said:**
> Should I try running 10.04 LTS?

It shouldn't hurt to try. Have you tried running without the ralink and see if it still freezes (just to confirm - obviously you will need wireless at some point).


PS if you search on random freezes you'll see you're not alone. I had a bunch of freezes start happening out of the blue (on 10.10) - but it might have been because my battery was in the process of failing (I'm not sure, but when I dropped back to my backup of 9.10 it still failed, so likely a hardware issue). Now it tells me my battery is not healthy, but at least it's not freezing anymore (and I've been running Natty as well as some test Wubi installs of 10.04.2 and 10.10).

Anyway - that's a bit of a ramble, but the point is it's not always easy to tell what the cause is ...

---

### Post by Jasonix on 2011-05-03
> **bcbc said:**
> It shouldn't hurt to try. Have you tried running without the ralink and see if it still freezes (just to confirm - obviously you will need wireless at some point).


PS if you search on random freezes you'll see you're not alone. I had a bunch of freezes start happening out of the blue (on 10.10) - but it might have been because my battery was in the process of failing (I'm not sure, but when I dropped back to my backup of 9.10 it still failed, so likely a hardware issue). Now it tells me my battery is not healthy, but at least it's not freezing anymore (and I've been running Natty as well as some test Wubi installs of 10.04.2 and 10.10).

Anyway - that's a bit of a ramble, but the point is it's not always easy to tell what the cause is ...

I'm just worried about the grub 2 error stuff...Didn't 11.04 fix it?

---

### Post by bcbc on 2011-05-03
> **Jasonix said:**
> I'm just worried about the grub 2 error stuff...Didn't 11.04 fix it?

Yes. These problems were fixed in 11.04, but they are also being backported to 10.04.2 and 10.10. The fix is currently in -proposed for both releases, but no idea when this will be ready. (I've been testing them here [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898))

So the next grub update will include the fix, but if you want to be safe, just don't update them: either lock the packages grub-pc and grub-common, or review the list in Update manager and uncheck any grub updates.

---

### Post by Jasonix on 2011-05-03
> **bcbc said:**
> Yes. These problems were fixed in 11.04, but they are also being backported to 10.04.2 and 10.10. The fix is currently in -proposed for both releases, but no idea when this will be ready. (I've been testing them here [https://bugs.launchpad.net/wubi/+bug/610898](https://bugs.launchpad.net/wubi/+bug/610898))

So the next grub update will include the fix, but if you want to be safe, just don't update them: either lock the packages grub-pc and grub-common, or review the list in Update manager and uncheck any grub updates.

Wait, the grub 2 stuff only affects wubi?

---

### Post by bcbc on 2011-05-04
> **Jasonix said:**
> Wait, the grub 2 stuff only affects wubi?

I've found grub2 to be fine (for non-wubi), but in some cases there are some issues. Usually it's some software in windows that writes to the boot track (in areas it considers free). Grub2 is a lot more complex than e.g. a windows boot loader, so it takes up more space.

But that's not to say people don't have issues. 

The issues I referred to are specific grub2 problems affecting Wubi only.

---

### Post by Jasonix on 2011-05-04
I finally got the bootinfo from ubuntu 10.04.2

              ```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda
 => No known boot loader is installed in the MBR of /dev/sdb

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /boot.ini /bootmgr /Boot/BCD 
                       /Windows/System32/winload.exe /ntldr /NTDETECT.COM

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  According to the info in the boot sector, sda6 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

sdb1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sdb2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sdb5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sdb5 starts 
                       at sector 63.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63    53,255,474    53,255,412   7 HPFS/NTFS
/dev/sda2          53,255,475   156,248,189   102,992,715   f W95 Ext d (LBA)
/dev/sda5          53,255,538   114,688,034    61,432,497   7 HPFS/NTFS
/dev/sda6         114,688,098   156,248,189    41,560,092   7 HPFS/NTFS


Drive: sdb ___________________ _____________________________________________________

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sdb1                  63   281,844,359   281,844,297   7 HPFS/NTFS
/dev/sdb2         281,844,360   312,576,704    30,732,345   f W95 Ext d (LBA)
/dev/sdb5         281,844,423   312,576,704    30,732,282   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        AA40D8EE40D8C26D                       ntfs       SYS1                          
/dev/sda2: PTTYPE="dos" 
/dev/sda5        FCE2450AE244CA9A                       ntfs       Apps                          
/dev/sda6        14E2F1D2989425F1                       ntfs       DB                            
/dev/sda: PTTYPE="dos" 
/dev/sdb1        18B077EFB077D22C                       ntfs       Sea                           
/dev/sdb2: PTTYPE="dos" 
/dev/sdb5        702EAEE12EAE9F98                       ntfs       Linux                         
/dev/sdb: PTTYPE="dos" 
error: /dev/sdc: No medium found
error: /dev/sdd: No medium found
error: /dev/sde: No medium found
error: /dev/sdf: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sdb5        /media/Linux             fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)


================================ sda1/boot.ini: ================================

;
;Warning: Boot.ini is used on Windows XP and earlier operating systems.
;Warning: Use BCDEDIT.exe to modify Windows Vista boot options.
;
[boot loader]
timeout=5
default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /FASTDETECT /NOEXECUTE=OPTIN
=========================== Unknown MBRs/Boot Sectors/etc =======================

Unknown MBR on /dev/sdb

00000000  90 e9 7d 01 fa 33 c0 8e  d0 8e c0 8e d8 bc 00 7c  |..}..3.........||
00000010  8b f4 fb bf 00 06 b9 00  01 f3 a5 bb 20 06 ff e3  |............ ...|
00000020  90 90 be 7d 07 81 3c aa  55 75 11 e8 58 00 73 0c  |...}..<.Uu..X.s.|
00000030  e8 65 00 72 07 e8 b1 00  72 3b eb 2c be 7d 07 c7  |.e.r....r;.,.}..|
00000040  04 00 00 ba 80 00 be be  07 b9 04 00 f6 04 80 75  |...............u|
00000050  07 83 c6 10 e2 f6 eb 1d  8a 74 01 8b 4c 02 bb 00  |.........t..L...|
00000060  7c b8 01 02 cd 13 72 0d  81 3e fe 7d 55 aa 75 05  ||.....r..>.}U.u.|
00000070  ea 00 7c 00 00 be 6a 07  ac 0a c0 74 fe bb 07 00  |..|...j....t....|
00000080  b4 0e cd 10 eb f2 bb 00  7e c6 07 13 c6 47 01 00  |........~....G..|
00000090  b2 80 b8 00 e0 cd 13 c3  bf 00 7e ba f0 01 b3 a0  |..........~.....|
000000a0  e8 84 00 72 0c b1 01 e8  48 00 72 05 e8 19 00 73  |...r....H.r....s|
000000b0  16 f6 c3 10 75 05 80 cb  10 eb e5 81 fa 70 01 74  |....u........p.t|
000000c0  05 ba 70 01 eb d8 f9 c3  81 bd fe 01 55 aa 75 17  |..p.........U.u.|
000000d0  8b 75 02 81 fe be 01 77  0e 03 f7 81 3c aa 55 75  |.u.....w....<.Uu|
000000e0  06 f6 44 02 01 75 01 f9  c3 bf 00 7c b1 0a e8 01  |..D..u.....|....|
000000f0  00 c3 52 57 83 c2 02 b0  01 ee 42 8a c1 ee 42 32  |..RW......B...B2|
00000100  c0 ee 42 ee 42 8a c3 ee  42 b0 20 ee e8 33 00 ec  |..B.B...B. ..3..|
00000110  24 fd 3c 58 75 0d 83 ea  07 b9 00 01 fa f3 6d fb  |$.<Xu.........m.|
00000120  f8 eb 01 f9 5f 5a c3 52  83 c2 07 ec a8 80 75 0f  |...._Z.R......u.|
00000130  4a 8a c3 ee 42 ec 24 d0  3c 50 75 03 f8 eb 01 f9  |J...B.$.<Pu.....|
00000140  5a c3 51 8b 0e 6c 04 83  c1 12 81 c2 ff 01 ec 8a  |Z.Q..l..........|
00000150  e0 80 e4 d8 80 fc 58 74  06 3b 0e 6c 04 75 ef 81  |......Xt.;.l.u..|
00000160  ea ff 01 b9 00 20 e2 fe  59 c3 0d 0a 45 72 72 6f  |..... ..Y...Erro|
00000170  72 20 4c 6f 61 64 69 6e  67 20 4f 53 00 aa 55 00  |r Loading OS..U.|
00000180  00 e9 80 fe 00 00 00 00  00 00 00 00 00 00 00 00  |................|
00000190  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001a0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001b0  00 00 00 00 00 00 00 00  8e 50 5d 06 00 00 00 01  |.........P].....|
000001c0  01 00 07 fe ff ff 3f 00  00 00 49 9a cc 10 00 00  |......?...I.....|
000001d0  c1 ff 0f fe ff ff 88 9a  cc 10 39 f0 d4 01 00 00  |..........9.....|
000001e0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 00 00  |................|
000001f0  00 00 00 00 00 00 00 00  00 00 00 00 00 00 55 aa  |..............U.|
00000200


=======Devices which don't seem to have a corresponding hard drive==============

sdc sdd sde sdf 

```

Good Luck solving my Problems!

---

### Post by bcbc on 2011-05-04
> **Jasonix said:**
> I finally got the bootinfo from ubuntu 10.04.2

Good Luck solving my Problems!

That looks pretty vanilla - that's good. So install again, and if you have problems finding the wubildr.mbr, run the bootinfoscript again. Also go to a cmd prompt from windows, Start, CMD, right click, run as administrator, then enter: "bcdedit" and copy and paste the results. (After installing).

---

### Post by Jasonix on 2011-05-04
> **bcbc said:**
> That looks pretty vanilla - that's good. So install again, and if you have problems finding the wubildr.mbr, run the bootinfoscript again. Also go to a cmd prompt from windows, Start, CMD, right click, run as administrator, then enter: "bcdedit" and copy and paste the results. (After installing).

What do you mean pretty good vanilla? Anyway, I should install from 10.04.2 cd? Or from Wubi? And, I heard about one step in the installation that can cause problems...Please tell me how to install and the options to choose...Btw, I want to install to Linux, the 15gb drive, not C:\ the place where windows 7 is installed.

---

### Post by bcbc on 2011-05-04
> **Jasonix said:**
> What do you mean pretty good vanilla? Anyway, I should install from 10.04.2 cd? Or from Wubi? And, I heard about one step in the installation that can cause problems...Please tell me how to install and the options to choose...Btw, I want to install to Linux, the 15gb drive, not C:\ the place where windows 7 is installed.

Vanilla = plain; nothing fancy like dynamic disks/raid etc. 

If you want wubi, just install the way you did before. I assume the 15GB drive is H: right? There's not much where you can go wrong (it usually works fine - obviously not always).

---

### Post by Jasonix on 2011-05-04
> **bcbc said:**
> Vanilla = plain; nothing fancy like dynamic disks/raid etc. 

If you want wubi, just install the way you did before. I assume the 15GB drive is H: right? There's not much where you can go wrong (it usually works fine - obviously not always).

It's I:\ (named Linux) and is free of any data. But, in your opinion, should I install Wubi, or install it normally, taking in account that I will install on I:\ no matter what?
Maybe you could list the advantages and disadvantages of both? Sorry to make you write an essay...
Thanks in advance!

---

### Post by bcbc on 2011-05-04
> **Jasonix said:**
> It's I:\ (named Linux) and is free of any data. But, in your opinion, should I install Wubi, or install it normally, taking in account that I will install on I:\ no matter what?
Maybe you could list the advantages and disadvantages of both? Sorry to make you write an essay...
Thanks in advance!

Wubi is designed to allow you to try Ubuntu in a realistic way without having to partition or even create an Ubuntu CD/USB. It runs natively on the hardware, but uses a virtual disk that resides on an ntfs/fat filesystem.
The nice thing about Wubi is that if you don't like Ubuntu you can just uninstall "Ubuntu" from Add/Remove programs. Safe to install, safe to remove.

Since you already have a dedicated partition there's really no reason to use Wubi. If you are nervous about having the Grub2 bootloader on your MBR you can download and use EasyBCD to boot Ubuntu from Windows' boot manager. If you do install Grub2's bootloader (which I use) then just don't forget that if you delete/format the Ubuntu partition your computer won't boot. But you just have to simply reinstall the Windows boot loader to get windows booting again (from a windows repair disk prompt "bootrec /fixmbr"). If you're not planning to uninstall, don't worry about it.

And if you choose to do a normal install, go and look for a guide on how to install. There were some issues with 10.10 that confused some people. I think 11.04 should be better. This link should be about 10.10 [http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)

---

### Post by Jasonix on 2011-05-04
> **bcbc said:**
> Wubi is designed to allow you to try Ubuntu in a realistic way without having to partition or even create an Ubuntu CD/USB. It runs natively on the hardware, but uses a virtual disk that resides on an ntfs/fat filesystem.
The nice thing about Wubi is that if you don't like Ubuntu you can just uninstall "Ubuntu" from Add/Remove programs. Safe to install, safe to remove.

Since you already have a dedicated partition there's really no reason to use Wubi. If you are nervous about having the Grub2 bootloader on your MBR you can download and use EasyBCD to boot Ubuntu from Windows' boot manager. If you do install Grub2's bootloader (which I use) then just don't forget that if you delete/format the Ubuntu partition your computer won't boot. But you just have to simply reinstall the Windows boot loader to get windows booting again (from a windows repair disk prompt "bootrec /fixmbr"). If you're not planning to uninstall, don't worry about it.

And if you choose to do a normal install, go and look for a guide on how to install. There were some issues with 10.10 that confused some people. I think 11.04 should be better. This link should be about 10.10 [http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

I'm going to normal install, and follow the exact guide's instructions. I have a few questions though. If I install grub 2 to I:\(where I will install Ubuntu), how will it affect windows boot manager, and if I uninstall ubuntu, will I still need to fix mbr?

Thanks in Advance

---

### Post by bcbc on 2011-05-04
> **Jasonix said:**
> I'm going to normal install, and follow the exact guide's instructions. I have a few questions though. If I install grub 2 to I:\(where I will install Ubuntu), how will it affect windows boot manager, and if I uninstall ubuntu, will I still need to fix mbr?

Thanks in Advance
I don't think the installer gives you that option anymore - to install the grub2 bootloader to the partition (maybe they brought it back). If you do that you have to use easyBCD to boot Ubuntu. Follow the easyBCD guide [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Don't think of the partition as I: - that won't tell you anything in Ubuntu. Primary partitions are numbered 1 to 4. Logical partitions from 5. If you look at your bootinfoscript results you'll see you have /dev/sda1 (primary partition 1 on the first hard drive) and two logicals /dev/sda5 and /dev/sda6. Also, /dev/sdb1 and /dev/sdb5. You'll need to know what I: represents to tell the installer where to install. You might have to delete the partition before installing too - or run the installer manually (advanced settings) to format it prior to installing (I don't use the installer much so you best follow the guides out there).

When you install directly on I: it will wipe it and change the filesystem from NTFS to EXT4 (and windows will no longer recognize it... so no more I: )

---

### Post by Jasonix on 2011-05-05
> **bcbc said:**
> I don't think the installer gives you that option anymore - to install the grub2 bootloader to the partition (maybe they brought it back). If you do that you have to use easyBCD to boot Ubuntu. Follow the easyBCD guide [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

Don't think of the partition as I: - that won't tell you anything in Ubuntu. Primary partitions are numbered 1 to 4. Logical partitions from 5. If you look at your bootinfoscript results you'll see you have /dev/sda1 (primary partition 1 on the first hard drive) and two logicals /dev/sda5 and /dev/sda6. Also, /dev/sdb1 and /dev/sdb5. You'll need to know what I: represents to tell the installer where to install. You might have to delete the partition before installing too - or run the installer manually (advanced settings) to format it prior to installing (I don't use the installer much so you best follow the guides out there).

When you install directly on I: it will wipe it and change the filesystem from NTFS to EXT4 (and windows will no longer recognize it... so no more I: )

Read the guide you posted in your last post([http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")), click the option to install on two hdrives in the guide, read it, and tell me what I should do, because I'm really confused.
Wait, so I should install boot loader(grub)on sda1 and it will be able to load all operating systems? Is this the best option? Please reply soon.

---

### Post by bcbc on 2011-05-05
> **Jasonix said:**
> Read the guide you posted in your last post([http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")), click the option to install on two hdrives in the guide, read it, and tell me what I should do, because I'm really confused.
Wait, so I should install boot loader(grub)on sda1 and it will be able to load all operating systems? Is this the best option? Please reply soon.

No /dev/sda1 is your windows boot partition. If you install grub on it (it shouldn't let you, but if you do) it will break windows.

I think you need to read through those guides. They are written by people who have gone through in detail testing the install process and are documented with pictures. All of which I have not done. They're supposed to be for newcomers to Ubuntu so they should be relatively simple. 

I spend more time focusing on Wubi issues, which is easy to install and uninstall. Which is what I recommend if you find those guides too confusing. 
Or if you just want to do a normal install with EasyBCD, create a new thread in the Installation and upgrades forum titled e.g. "Please help me to install using EasyBCD", you might get someone who specializes more on these sorts of installs who can help you (unfortunately I've never used easyBCD)

---

### Post by Jasonix on 2011-05-05
> **bcbc said:**
> No /dev/sda1 is your windows boot partition. If you install grub on it (it shouldn't let you, but if you do) it will break windows.

I think you need to read through those guides. They are written by people who have gone through in detail testing the install process and are documented with pictures. All of which I have not done. They're supposed to be for newcomers to Ubuntu so they should be relatively simple. 

I spend more time focusing on Wubi issues, which is easy to install and uninstall. Which is what I recommend if you find those guides too confusing. 
Or if you just want to do a normal install with EasyBCD, create a new thread in the Installation and upgrades forum titled e.g. "Please help me to install using EasyBCD", you might get someone who specializes more on these sorts of installs who can help you (unfortunately I've never used easyBCD)

I understand now. Last question(hopefully) the person who wrote that guide says to load the second hard drive to load ubuntu, should I do this or EasyBCD?

---

### Post by Jasonix on 2011-05-05
Wait a minute, the EasyBCD page says that 10.04 does not allow you to install grub to another partition, so it will install to where?
And, I can follow either the EasyBCD guide or the herman guide right? Why is the EasyBCD guide different? Like, EasyBCD doesn't select where to install Grub, but herman guide does?

---

### Post by bcbc on 2011-05-05
What he is referring to is something many people seem to prefer when dual booting to keep things 'compartmentalized'. Instead of Windows and Ubuntu sharing the same physical drive, they dedicate one whole drive to Ubuntu, keeping even the bootloader separate. In that way, they can unplug the Ubuntu drive and Windows boots normally and vice versa.

In your case, your 15GB drive I: is actually a partition, not a physical drive (windows calls them drives but this is a misnomer). So I don't think that guide applies to you, unless you are planning to dedicate the whole /dev/sdb drive to Ubuntu (I didn't think you were).

---

### Post by Jasonix on 2011-05-05
> **bcbc said:**
> What he is referring to is something many people seem to prefer when dual booting to keep things 'compartmentalized'. Instead of Windows and Ubuntu sharing the same physical drive, they dedicate one whole drive to Ubuntu, keeping even the bootloader separate. In that way, they can unplug the Ubuntu drive and Windows boots normally and vice versa.

In your case, your 15GB drive I: is actually a partition, not a physical drive (windows calls them drives but this is a misnomer). So I don't think that guide applies to you, unless you are planning to dedicate the whole /dev/sdb drive to Ubuntu (I didn't think you were).

So, then what guide should I follow?

---

