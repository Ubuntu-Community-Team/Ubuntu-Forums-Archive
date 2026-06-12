---
title: "warning repeats after reboot &amp; after the fix: &quot;invalid backup GPT header&quot;"
date: 2020-10-10
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2020-10-10
When I boot to a new UEFI/GPT install of Ubuntu-MATE 20.04 on an external SSD, I get a warning when I open either gdisk or Gparted. 

 gdisk says *"Caution: invalid backup GPT header, but valid main header; regenerating backup header from main header."   *(The Gparted warning is similar, *backup table is corrupt, using main one,* etc.)

When, in gdisk, I hit the **"p"** (for print) command, I get this further warning: *"Warning! One or  more CRCs don't match. You should repair the disk!"*

and: *"Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but  disk verification and  recover are STRONGLY recommended."*

Continuing in gdisk, I hit **"v"** and then write to  disk [as per the answer provided here]("https://askubuntu.com/questions/386752/fixing-corrupt-backup-gpt-table"), then everything is fine, no more warnings.  [I][B]

But when I re-boot, it starts all over again with the same warnings.[/B][/I]

My bootloader is grub2, I'm not dual-booting, I don't use Windows, and I don't have Secure Boot.  I  do have an internal drive (my current working system, Ubuntu-MATE 18.04) that is not UEFI/GPT and boots via BIOS. (For what it's worth, both 18.04 and 20.04 are using the same Linux kernel, 5.4.0-48-generic.)

 (And I do have back-ups (created with rsync) of both the ESP and root partitions of the external drive.  The backups are on a separate, storage-only SSD drive.)

(I also have the rEFInd boot manager installed on the external drive; I only see it when I press <F10> while booting. I installed rEFInd because I plan later to dual-boot 20.04 and a new UEFI/GPT 18.04. Both will eventually be placed as internal drives.)

I found [one answer that was related]("https://superuser.com/questions/822380/caution-invalid-backup-gpt-header-gdisk") (he also was able to fix the same warning problem, yet the warning would repeat after reboot). He said [I]"Eventually I tracked it down to the firmware overwriting the CRC entries  in the backup GPT header every boot to some invalid value."   

[/I]Something similar may be going on with my situation.   One thing to note is that when I shut down, this drive goes dark and just hangs.  I then have to hold the  power button (on the desktop workstation that the drive is connected to) in for 6 seconds, and shut  down that way. So I may need to address how to shut down  properly before anything else.

His solution was to *"Change the disk mode in the firmware setup from RAID to AHCI."*  

In my case, I don't know that this would help:  My BIOS firmware menu (in "*Advanced -> Drive configuration -> Configure SATA as ...*") is already set (and has always been set) to "AHCI."  The other two choices are  "RAID" and "IDE." At the moment I'm  not inclined  to change from ACHI to either RAID or IDE.
  
Does anyone suspect what might be the cause of the warning and how it might be remedied?


*[P.S.   Is it possible to change or edit the title of a post after I've posted?]*

---

### Post by oldfred on 2020-10-10
I think you edit first post and then can change title. Posts already added will still have old title.

Check firmware.
udisksctl status
If internal SSD you can also use:
sudo nvme list

I am a bit surprised that gdisk is not showing an error, but when you boot, you do get an error.

Since I do not see a simple question with a straight forward answer, I find it easier to use Forum for multiple back and forth issues.
[https://askubuntu.com/questions/1281752/backup-gpt-header-warning-repeats-after-every-fix-reboot](https://askubuntu.com/questions/1281752/backup-gpt-header-warning-repeats-after-every-fix-reboot)

My Samsung NVMe drive has a bootable ISO, that looked like an old DOS screen with just the one new firmware.
Not sure about other vendors.

AHCI applies to internal drives. USB external drives are different. leave AHCI for internal drives.

How did you partition SSD?
Normal tools start first sector at 2048. But not using space from 2048 to 16384 should not be an issue.

see also:
[https://askubuntu.com/questions/633465/the-crc-for-the-main-partition-and-back-up-partition-table-are-invalid](https://askubuntu.com/questions/633465/the-crc-for-the-main-partition-and-back-up-partition-table-are-invalid)

---

### Post by watchpocket on 2020-10-11
Still getting this from gdisk (and the similar warning from Gparted) every time I boot to my external SSD /dev/sdc that I've installed 20.04 on:
```
GPT fdisk (gdisk) version 1.0.5                                                                                                                                                                              
    
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.
    
Warning! One or more CRCs don't match. You should repair the disk!
Main header: OK
Backup header: ERROR
Main partition table: OK
Backup partition table: OK
    
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged
    
****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************
    
Command (? for help): p
Disk /dev/sdc: 1875385008 sectors, 894.3 GiB 
Model: Ultra II 960GB--
Sector size (logical/physical): 512/512 bytes
Disk identifier (GUID): F4DEFA58-650D-4D70-98CF-06C88C5FCBBF
Partition table holds up to 128 entries
Main partition table begins at sector 2 and ends at sector 33
First usable sector is 34, last usable sector is 1875384974
Partitions will be aligned on 2048-sector boundaries
Total free space is 88132 sectors (43.0 MiB)
    
Number  Start (sector)    End (sector)  Size       Code  Name
   1           16384         1143336   550.3 MiB   EF00  EFI System (ESP)
   2         1146880      1875316735   893.7 GiB   8300  UbuntuMATE-20.0
```

From here in gdisk I can fix this with "v", "w" and "y" , run gdisk again and all is well,  but then I will get the same error when I run gdisk after every reboot.

I bought the drive in early May 2020 and it sat for 3 months before I began to use it. * udisksctl status* shows the firmware revision number to be ***X41320RL**:*
```
--> udisksctl status 
MODEL                     REVISION  SERIAL               DEVICE
--------------------------------------------------------------------------
WDC WDS100T2B0A           X61190WD  192762802683         sda     
SanDisk Ultra II 960GB    X41320RL  170901B001B2         sdb     
SanDisk Ultra II 960GB    X41320RL  172104A00B54         sdc 
```

(The first SanDisk Ultra II listed above is my internal storage disk. I bought 2 of the same disk at roughly the same time.) I couldn't find anywhere on the SanDisk forums exactly what the current revision of the Ultra II is, but I also couldn't find any revision numbers discussed that were *higher* than ***X41320RL***, so there's a good chance that I have the latest version, given that the drive is only 6 months old.

A screenshot is attached showing the results of an extended SMART self-test.[ATTACH=CONFIG]287148[/ATTACH]  Although I'm not an expert on what to look for here, the only potentially worrisome item would seem to be the fourth one up from the bottom, an *"Uncorrectable ECC Count" * of 304 sectors. 

Is that bad and/or meaningful?  

Here is a filesystem check:
```
--> sudo e2fsck -f -v /dev/sdc2
[sudo] password for rj: 
e2fsck 1.44.1 (24-Mar-2018)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

      311028 inodes used (0.53%, out of 58572800)
         593 non-contiguous files (0.2%)
         329 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 268909/65
     7322653 blocks used (3.13%, out of 234271232)
           0 bad blocks
           2 large files

      221945 regular files
       36228 directories
           9 character device files
           0 block device files
           0 fifos
         113 links
       52837 symbolic links (42037 fast symbolic links)
           0 sockets
------------
      311132 files
sudo e2fsck -f -v /dev/sdc2  3.00s user 0.33s system 22% cpu 14.849 total
```

I partitioned the drive using Gparted.  I first created the ESP, then the root partition. 

 gdisk, a week ago, threw a further warning that the root partition was not aligned  to 8 sectors, so I fixed that by expanding the size of that partition a small bit. Now gdisk and Gparted do *not* give me that error.  

The first sector of sdc1 (the ESP) is 1146880, last sector of the ESP is 1875316735.  The first sector of sdc2 (the root partition) is 1146880. Last sector is 1875316735.  I'm open to wiping this whole setup and re-partitioning (and re-installing the 20.04 OS) if there is a saner way to do it.
[ATTACH=CONFIG]287149[/ATTACH]

About the drive not completely shutting down, it's also the case that the installer flash drives I've use also do not completely shut down. With those, the message comes up saying "remove the installation media and press ENTER."  After I do that, I wait 30 seconds or so, and still no shutdown, so I then have to shut my machine down by holding in the power button for about 6 seconds. So the fact that the external SSD doesn't completely shut down may not be unique to it, may not be a problem with the drive itself.

I tried connecting the SSD with a different (admittedly thinner) cable (USB-C to USB-A) and with* that *cable the drive booted so unbelievably painfully slow that I threw the thinner cable away and went back to the cable I've been using all along.

About Rod Smith's suggestion of the possibility of "Host Protected Area" being set, it appears not to be:
```
--> sudo hdparm -N /dev/sdc 

/dev/sdc:
 max sectors   = 1875385008/1875385008, HPA is disabled
```

Any further suggestions are of course welcome, but I may be at the point of returning this disk for a replacement.

---

### Post by oldfred on 2020-10-12
I assume your other drive does not show anything similar?
I might test drive as internal just to see if that makes a difference. But I do not expect any change.

I have not seen gparted not align a gpt drive. Did you turn that off, or use a very old version of gparted to partition drive?

---

### Post by watchpocket on 2020-10-12
> **oldfred said:**
> I assume your other drive does not show anything similar?

The other SanDisk Ultra II that I have is internal and it doesn't boot. It's used for storage only. It's MBR.  There are no problems with it. 

 I do have a 2nd external SanDisk Ultra II that I've made UEFI/GPT that I've put 18.04 on.  With that disk, gdisk does show me *"Caution: Partition 1 doesn't begin on a 8-sector boundary," (*partition 1 is the ESP) but I should be able fix that. 

> I might test drive as internal just to see if that makes a difference. But I do not expect any change.

I'll try placiing the 20.04 external drive internally later today.  

Btw, I know you can't have 2 internal booting drives where one of them  is UEFI and the other MBR, but if I place a UEFI booting drive internally with an MBR drive that doesn't boot, I'm assuming there should be no problem with doing that, correct?

(Also, can or should I do anything about the *"Uncorrectable ECC Count" * of 304 sectors in my last post?)

> I have not seen gparted not align a gpt drive. Did you turn that off, or use a very old version of gparted to partition drive?

 Turn what off,  specifically?  I haven't turned anything in Gparted off that I'm aware of.  I'm using version 1.1.0 of Gparted.

---

### Post by oldfred on 2020-10-12
With new gparted, I would expect all partitions to be aligned with gpt.
Most new drives are now 4K and alignment is important for efficency, but if still 256 then alignment is not critical. 

I only use gpt now on all drives as it has advantages over MBR.
GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

Do not know about ECC type errors. 

You can have one drive booting via MBR and one UEFI as internal drives. Can be bit more difficult to manage.
Issue is you cannot have Windows in BIOS and Ubuntu in UEFI on same drive. Windows requires boot flag on primary NTFS partition with its boot files. And UEFI requires boot flag on ESP. Only one boot flag per drive, so Windows/BIOS and UEFI cannot be on same drive. But if different drives most UEFI now remember boot mode or select it correctly. It used to be you had to go into UEFI and turn on/off UEFI or BIOS to get correct boot mode.

UEFI also has fallback or hard drive boot entry for internal drives. It is the same as an external drive and uses /EFI/Boot/bootx64.efi. Ubuntu installer to ESP, does add a copy of shimx64.efi as bootx64.efi in ESP, so it can be booted from a fallback/drive boot entry. But Ubiquity installer does not install to ESP on external drives, unless seen as only drive or other work arounds.

---

### Post by watchpocket on 2020-10-12
What would you do with an SSD that presents the same gdisk error message 
( ```
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.
    
Warning! One or more CRCs don't match. You should repair the disk!
Main header: OK
Backup header: ERROR
Main partition table: OK
Backup partition table: OK
    
Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged
    
****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
``` )

every time you run gdisk on it just after booting to that drive, after "fixing" the problem before re-boot?

If I were to wipe this whole disk and start over from scratch and re-partition, would that be worth doing?  Is that something that might have a decent chance at UN-corrupting the backup GPT header?

---

### Post by watchpocket on 2020-10-12
Interesting update here, some good news with this drive, for a change:  I installed the 20.04 UEFI/GPT disk internally with no other disk connected except the storage (MBR) disk that doesn't boot.

So I boot into the drive, everything boots normally (more or less - I do get the same "System bootOrder not found" that I got when it was plugged in externally, but I can probably figure out how to fix that in grub).

I run gdisk - *sudo gdisk /dev/sda* - and, lo and behold, I DO NOT get any of the "invalid backup GPT header" warnings that I got when this SSD was connected externally.  I also do not get the similar warning (or any warnings) when I open Gparted. I re-booted and ran gdisk and Gparted a few times.  No error message from either.

The only bummer is that when I shut down, I see: 

"[OK] Finished Hold until boot process finishes up.
[151.352337] reboot: Power down"

I wait, there's no shutdown, and I have to press the power button to shut down.

When I shut down from the login screen (before logging in), I  get the same empty gray screen (with a black horizontal bar all the way across the top) that I got when shutting down while the drive was externally connected. And I still have to shut down with the power button.

 I still have no idea why the gdisk/Gparted errors kept appearing upon reboot when the drive is connected externally, but if I can figure out how to shut down properly with it connected internally, I think I'll finally be ready to use the drive. 

So at this point I'm looking for any suggestions about how to get the drive to shut down properly on its own. Also will be searching on this now.

---

### Post by oldfred on 2020-10-12
I have seen some others with slow shutdown.
I had that where some process was still running and it had to finish. Found it had to timeout after a minute and half. So found some setting to change that, but do not remember details.

Best not to force shutdown with power switch. If in middle of writing something, it can corrupt filesystem and then you need fsck to repair it.

Someone posted that not all these are valid now, but I still have used them.
Holding down Ctrl+Alt and SysRq (which is the Print Screen key) while slowly typing REISUB
R-E-I-S-U-B to force shutdown
A good way to remember it is, and S can be before E, but others should be in order
Raising Skinny Elephants Is Utterly Boring ...or
Reboot System Even If Ultimately Broken ...LOL.

---

### Post by watchpocket on 2020-10-12
> **oldfred said:**
> Best not to force shutdown with power switch. If in middle of writing something, it can corrupt filesystem and then you need fsck to repair it.

So even if you're holding the power button in for six or seven seconds?  I thought that was a safe way to shut down.  I've seen the REISUB before, I'll try that.

Meanwhile I want to figure out the cause of the problem.  I'll wait a while longer next time to see if  it shuts down on its own after a couple of minutes.

---

### Post by tea for one on 2020-10-12
I'm not sure about Ubuntu flavours but Ubuntu does not ship with REISUB fully enabled.

Here is a method to enable the process by editing a file:-

```
sudo nano /etc/sysctl.d/10-magic-sysrq.conf
```

Then change the number in line 26 from 176 to 244 i.e. kernel.sysrq = **244**

I found the solution at this site [https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/](https://digitalfortress.tech/debug/what-should-you-do-when-ubuntu-freezes/) and the information was in section 3.

By the way, the last letter in the process **B** reboots your system, sometimes you may want to power off completely by substituting the **B** for an **O**

---

