---
title: "Can't find my paritions with kubuntu"
date: 2023-11-03
forum: Installation &amp; Upgrades
---

### Post by oilhat on 2023-11-03
Kubuntu would not start today.  I got an error [HTML]gave up waiting for suspend ...[/HTML] or something like that and then ```
booting into emergency mode
```  My laptop is dual boot windows 10 and kubuntu.  I can still boot into Windows and that is what I am using now.  I also have Kubuntu on a usb stick and I can boot into that.  My home is backed up, so I figured that I would just reinstall Kubuntu.  When I started the installer, it does not show any of the partitions on /dev/sda.  I aborted the install, and launched the kde partition manager, and I had the same problem.  I don't see any of the partitions on /dev/sda.  fdisk -l in emergency mode doesn't seem to work either.  It shows a lot of loop devices.

A few days ago I got an error saying that root was running out of space.  With the usb stick, I used the kde partition manager to move the home partition over and increase root from 20 Gb to 25 Gb.  It worked fine, but today there are problems.  Now I can't see the partitions with the kde partition manager or the kubuntu installer.  /dev/sda appears but it shows that there are no partitions on it at all.  They must still be there, since I can still boot and run windows.  Also, grub starts and runs normally.

What can I do?  I would like to find my partitions and reinstall Kubuntu.

---

### Post by MAFoElffen on 2023-11-03
From the LiveUSB, do this:
```

sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq
lsblk -e7 -o name,label,fstype,fsuse%,model

```
With the output pasted into a post within Code Tags (refer to the link in my signature).

Please confirm that in Windows that you have fastboot turned off, and that you have not suspended any Windows session. Please confirm that you have SecureBoot turned off in your BIOS settings.

---

### Post by oilhat on 2023-11-05
I looked in the bios and secure boot is not enabled.  I cannot get into windows at the moment.  I executed some commands that deleted gci or something, and now windows won't boot.

fdisk below shows the partitions on /dev/sda like they should be.  I did not include /dev/sdb and /dev/sdc as they are the two usb sticks that I have connected.  Nice to see that my partitions are still accessible.

```
[FONT=monospace][COLOR=#54ff54]**kubuntu@kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo fdisk -l 2>&1 | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq [/COLOR]

Ignoring extra data in partition table 7. 
Invalid flag 0x6465 of EBR (for partition 7) will be corrected by w(rite). 

Disk /dev/sda: 223.57 GiB, 240057409536 bytes, 468862128 sectors 
Disk model: INTEL SSDSC2BF24 
Units: sectors of 1 * 512 = 512 bytes 
Sector size (logical/physical): 512 bytes / 512 bytes 
I/O size (minimum/optimal): 512 bytes / 512 bytes 
Disklabel type: dos 
Disk identifier: 0x5c2e5d12 

Device     Boot      Start        End    Sectors   Size Id Type 
/dev/sda1  *          2048    1126399    1124352   549M  7 HPFS/NTFS/exFAT 
/dev/sda2          1126400  287846399  286720000 136.7G  7 HPFS/NTFS/exFAT 
/dev/sda3        287848446  467832831  179984386  85.8G  5 Extended 
/dev/sda4        467832832  468856831    1024000   500M 27 Hidden NTFS WinRE 
/dev/sda5        287848448  289169407    1320960   645M  7 HPFS/NTFS/exFAT 
/dev/sda6        289171456  340371455   51200000  24.4G 83 Linux 
/dev/sda7       2166147887 3934994587 1768846701 843.5G 6e unknown

[/FONT]
```
 And here is lsblk.  sda7 is absent.
```
[FONT=monospace][COLOR=#000000]lsblk -e7 -o name,label,fstype,fsuse%,model [/COLOR]
NAME   LABEL                            FSTYPE  FSUSE% MODEL 
sda                                                    INTEL SSDSC2BF240A4H 
&#9500;&#9472;sda1 System Reserved                  ntfs            
&#9500;&#9472;sda2                                  ntfs            
&#9500;&#9472;sda3                                                  
&#9500;&#9472;sda4 System Reserved                  ntfs            
&#9500;&#9472;sda5                                  ntfs            
&#9492;&#9472;sda6                                  ext4            
sdb    Kubuntu 22.04.3 LTS amd64        iso9660        Cruzer Glide 
&#9500;&#9472;sdb1 Kubuntu 22.04.3 LTS amd64        iso9660   100%  
&#9500;&#9472;sdb2 ESP                              vfat            
&#9500;&#9472;sdb3                                                  
&#9492;&#9472;sdb4 writable                         ext4        0%  
sdc    openSUSE-Leap-42.1-NET-x86_64026 iso9660        U3 Cruzer Micro 
&#9492;&#9472;sdc1 FlashStick1GB                    ntfs            
sr0                                                    U3 Cruzer Micro

[/FONT]
```

---

### Post by MAFoElffen on 2023-11-05
This is what I see i the first results:
```

Device     Boot      Start        End    Sectors   Size Id Type               Part_type
/dev/sda1  *          2048    1126399    1124352   549M  7 HPFS/NTFS/exFAT    Primary
/dev/sda2          1126400  287846399  286720000 136.7G  7 HPFS/NTFS/exFAT    Primary
/dev/sda4        467832832  468856831    1024000   500M 27 Hidden NTFS WinRE  Primary

/dev/sda3        287848446  467832831  179984386  85.8G  5 Extended           Extended
/dev/sda5        287848448  289169407    1320960   645M  7 HPFS/NTFS/exFAT    Logical
/dev/sda6        289171456  340371455   51200000  24.4G 83 Linux              Logical

[COLOR=#008000]/dev/????        340371456  467832831  127461375  60.7G ?? ?????              Logical[/COLOR]
                 
[COLOR=#ff0000]/dev/sda7       2166147887 3934994587 1768846701 843.5G 6e unknown[/COLOR]

```
Indicated in Red, is invalid. There might be something there, but what is writen in the partiton table is not valid. Then math doesn't add up for that.

What is indicated in Green, I added from doing the math, as what it should be at least close to. You can see the difference, right?

What 'was' there, and do you have backups of it?

---

### Post by oilhat on 2023-11-06
/dev/sda7 is my home partition for the kubuntu installation that does not work.  It is about 60Gb.  Yes, I have a backup of it.  

About a week ago, I expanded root on /dev/sda6 from 20gb to 25gb and I moved and resized home on dev/sda7 to make up the difference.  I used the Kpartition manager on the usb live stick.  Could it have become corrupted then?

There should not be any [COLOR=#008000]**unallocated space **[/COLOR]on the /dev/sda.  fdisk is showing **[COLOR=#ff0000]/dev/sda7[/COLOR]** as the wrong size.

---

### Post by MAFoElffen on 2023-11-06
What I would do... 

[LIST=1]
[*]Delete partition /dev/sda7.
[*]Create partition /dev/sda7 formatted as ext4.
[*]Restore the backup back onto /dev/sda7
[*]Get the new UUID of the filesystem on /dev/sda7 to update the fstab for the mount of /home
[/LIST]
 
During that process, during that time you could also, after adding the partition, and before formatting the filesystem, add a volume manager, such as LVM2, to add some features to it. That would be a good time to do that, if you wanted to.

For example: Add partition as type LVM PV > Create PV with that partition > Add VG > add LV > format LV > restore to that LV > add update fstab entry with the LV identifier... That would add the ability to resize it, and to do snapshots of that filesystem.

---

### Post by oilhat on 2023-11-06
That is fine idea, but I would need some help to get that done.  I would  probably opt for a reinstall of kubuntu and then go get any files that I  really need from my backup.  It seems like it would be easier.   Starting with step 1, how do I go about deleting and recreating  /dev/sda7 when neither KDE partition manager or Kununtu installer  recognizes any of the partitions on /dev/sda?  At this point I can do a  reinstall of kubuntu, but I am stuck deleting all of my windows  partitions.

---

### Post by MAFoElffen on 2023-11-06
[COLOR=#ff0000]<< EDIT --- Kept this to show I screwed up posting this. I lost track that he had a MBR partition table, and should have gave commands for him using 'fdisk' >>[/COLOR]

Personally, I do a lot of scripting, so instead of using gdisk, I use the API for it, called sgdisk. If you did
```

sudo su -
sgdisk -p /dev/sda

```
It should print out how gdisk see's your partition table, and return right back to your prompt...

If it shows partition #7, then do
```

sgdisk -d 7 -s /dev/sda
sgdisk -p /dev/sda

```
Then after verifying it is gone
```

sgdisk     -n7:0:0    -c7:home -t7:8300 /dev/sda
mke2fs -L home /dev/sda7 ## Dang (noticed typo)

```
To get the new UUID of the filesystem
```

blkid -s UUID -o value /dev/sda7

```
Then restore your backups of your home partition... That would take less time than starting all over and restoring everything, but...

Of course, if it does not show up with sgdisk or gdisk... Then destroy the partition table by creating a new partition table over it, and start over fresh. Then restore from your backups...

---

### Post by oilhat on 2023-11-06
I think I deleted the GPT sometime after these problems began.   Does this create a problem?  Do I -g to override?

```
[FONT=monospace][COLOR=#54ff54]**kubuntu@kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo su - [/COLOR]
**[COLOR=#ff0000]root@kubuntu:[/COLOR]**~# sgdisk -p /dev/sda 
EBR signature for logical partition invalid; read 0x6564, but should be 0xAA55 
Error reading logical partitions! List may be truncated! 

*************************************************************** 
Found invalid GPT and valid MBR; converting MBR to GPT format 
in memory.  
*************************************************************** 

Disk /dev/sda: 468862128 sectors, 223.6 GiB 
Model: INTEL SSDSC2BF24 
Sector size (logical/physical): 512/512 bytes 
Disk identifier (GUID): 542BCE45-FE25-45C3-987E-6496EE911D75 
Partition table holds up to 128 entries 
Main partition table begins at sector 2 and ends at sector 33 
First usable sector is 34, last usable sector is 468862094 
Partitions will be aligned on 2048-sector boundaries 
Total free space is 127472749 sectors (60.8 GiB) 

Number  Start (sector)    End (sector)  Size       Code  Name 
   1            2048         1126399   549.0 MiB   0700  Microsoft basic data 
   2         1126400       287846399   136.7 GiB   0700  Microsoft basic data 
   4       467832832       468856831   500.0 MiB   2700  Windows RE 
   5       287848448       289169407   645.0 MiB   0700  Microsoft basic data 
   6       289171456       340371455   24.4 GiB    8300  Linux filesystem 
**[COLOR=#ff0000]root@kubuntu:~#[/COLOR]** sgdisk   -n7:0:0    -c7:home  -t7:8300  /dev/sda 
EBR signature for logical partition invalid; read 0x6564, but should be 0xAA55 
Error reading logical partitions! List may be truncated! 

*************************************************************** 
Found invalid GPT and valid MBR; converting MBR to GPT format 
in memory.  
*************************************************************** 

Setting name! 
partNum is 6 
Non-GPT disk; not saving changes. Use -g to override. 
root@kubuntu:~# 
[/FONT]
```

---

### Post by TheFu on 2023-11-06
You are getting good advice from MAFoElffen.  This also points out a flaw in most backup solutions. The admin doesn't create a record of the partitioning, file system settings, etc. when they create backups (nightly or weekly).  If this data were saved automatically, then restoring the partition table to exactly what is was before to both the primary and backup table locations would be possible.

The MSDOS/MBR partition table has 2 copies, but unfortunately, these are side by side on a physical HDD. If 1 block fails, then the chances that the next block will also fail drastically increases.  However, with GPT, the 2 copies of the partition table are at opposite ends of the physical storage, reducing the chance that both copies will be corrupted.  This is one of the main reasons to use GPT, not MBR partitioning.  Linux supports both with no arbitrary limitations like MSFT decided to apply.  MSFT's choice is that UEFI == GPT and non-UEFI==MSDOS/MBR.

So, as part of your backup process, be certain you snag some system data like partitions, disk layouts, any volume manager layouts, etc to be included in your backups, in machine-readable form.

For partitions:
```
sudo parted -lm
```
Save that to a file that gets included in your backups.

For example, here's the layout of my NVMe storage:
```
BYT;
/dev/nvme0n1:1000GB:nvme:512:512:**gpt**:Samsung SSD 980 1TB:;
1:1049kB:2097kB:1049kB:ext2:GRUB:bios_grub;
2:2097kB:54.5MB:52.4MB:fat16:EFI-SP:boot, esp;
3:54.5MB:789MB:734MB:ext4:boot:;
4:789MB:1000GB:999GB::LVM:lvm;

```
That file can be fed into parted to create an exact copy of the allocation on different storage.  While it is seldom needed, having it can be a lifesaver.  I've only needed this information 3 times the last 25 yrs. Very happy I had it.

---

### Post by MAFoElffen on 2023-11-06
Sorry. I got ahead of myself, now remembering you are on a MBR partition. Dang. Must have been really tired.

Now I have had coffee!!!

Please use 'fdisk'!!! (my mistake)
```

sudo fdisk /dev/sda

```
Trying to remember from memory, adjust to what is there...

 then do <d> 7 > <n> 7.... then do <w><q>...

That should create it. Then format it.

---

### Post by oilhat on 2023-11-07
I thought I should post an update.  With gdisk, I added /dev/sda7 and recreated the GPT partition table.  At one point, I deleted the GPT partition table in an attempt to solve this problem.  It probably made things worse.  Anyway.  Here is my partition table now.  
```
[FONT=monospace][COLOR=#54ff54]**kubuntu@kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo gdisk -l /dev/sda [/COLOR]
GPT fdisk (gdisk) version 1.0.8 

Partition table scan: 
  MBR: protective 
  BSD: not present 
  APM: not present 
  GPT: present 

Found valid GPT with protective MBR; using GPT. 
Disk /dev/sda: 468862128 sectors, 223.6 GiB 
Model: INTEL SSDSC2BF24 
Sector size (logical/physical): 512/512 bytes 
Disk identifier (GUID): CA8E03C2-5B96-4823-9232-2E707C722804 
Partition table holds up to 128 entries 
Main partition table begins at sector 2 and ends at sector 33 
First usable sector is 34, last usable sector is 468862094 
Partitions will be aligned on 2048-sector boundaries 
Total free space is 11373 sectors (5.6 MiB) 

Number  Start (sector)    End (sector)  Size       Code  Name 
   1            2048         1126399   549.0 MiB   0700  Microsoft basic data 
   2         1126400       287846399   136.7 GiB   0700  Microsoft basic data 
   4       467832832       468856831   500.0 MiB   2700  Windows RE 
   5       287848448       289169407   645.0 MiB   0700  Microsoft basic data 
   6       289171456       340371455   24.4 GiB    8300  Linux filesystem 
   7       340371456       467832831   60.8 GiB    8300  Linux filesystem

[/FONT]
```

I also executed mke2fs as recommended above, but the kde partition manager shows the partition type on /dev/sda7 as unknown.  Given this, I don't think it is worthwhile to restore home.

I have a couple of other problems.  Root seems to be currupted because it ran out of space, and I cannot boot into my windows now.  The good thing is that the kubuntu installer does recognize my windows partitions, so I can procede with a reinstall.    I should be able to reinstall and get back up and running.  Thank you for all of your help.

---

### Post by TheFu on 2023-11-07
This is sounding more and more like failing hardware.  Have you run any SMART tests to see if the storage device is reporting issues?  I'd do that before wasting any time reloading an OS.

---

### Post by oilhat on 2023-11-07
No.  Do you mind telling me where to find a SMART test or how to run it?

Incidentally, I started an install, but it recommended that I create an efi partition.  It seems like I should already have one with windows10.  Here is my partition table again.  Do I not have an efi partition?  Where should I put it?
```
[FONT=monospace][COLOR=#54ff54]**kubuntu@kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo gdisk -l /dev/sda [/COLOR]
GPT fdisk (gdisk) version 1.0.8 

Partition table scan: 
  MBR: protective 
  BSD: not present 
  APM: not present 
  GPT: present 

Found valid GPT with protective MBR; using GPT. 
Disk /dev/sda: 468862128 sectors, 223.6 GiB 
Model: INTEL SSDSC2BF24 
Sector size (logical/physical): 512/512 bytes 
Disk identifier (GUID): CA8E03C2-5B96-4823-9232-2E707C722804 
Partition table holds up to 128 entries 
Main partition table begins at sector 2 and ends at sector 33 
First usable sector is 34, last usable sector is 468862094 
Partitions will be aligned on 2048-sector boundaries 
Total free space is 11373 sectors (5.6 MiB) 

Number  Start (sector)    End (sector)  Size       Code  Name 
   1            2048         1126399   549.0 MiB   0700  Microsoft basic data 
   2         1126400       287846399   136.7 GiB   0700  Microsoft basic data 
   4       467832832       468856831   500.0 MiB   2700  Windows RE 
   5       287848448       289169407   645.0 MiB   0700  Microsoft basic data 
   6       289171456       340371455   24.4 GiB    8300  Linux filesystem 
   7       340371456       467832831   60.8 GiB    8300  Linux filesystem


[/FONT]
```

---

### Post by #&amp;thj^% on 2023-11-07
Sure:
```
sudo apt install smartmontools
```
run it against the current drive:
```
sudo smartctl -i /dev/sda
```
For a lot of info run as:
```
sudo smartctl --all /dev/sda
```

---

### Post by oldfred on 2023-11-07
Your original post of MBR partitions showed Windows install. And only the two NTFS partitions, typically a boot and main (c: drive) partition. Since MBR that Windows install would have to be BIOS.
Windows requires MBR(msdos) with BIOS boot and gpt(GUID) with UEFI boot.
Not easy to convert Windows from BIOS to UEFI. Some instructions are on Internet, but most end up reinstalling.

---

### Post by MAFoElffen on 2023-11-07
In post #12 ([https://ubuntuforums.org/showthread.php?t=2492211&p=14164353#post14164353](https://ubuntuforums.org/showthread.php?t=2492211&p=14164353#post14164353)), I told you "No" and had amended my instructions to use use fdisk, to just use your MBR partition, and to delete just that last partition (7), then re-add it. Dang. I guess you didn't see that?

Start over with a fresh MBR partition table and restored from your backups.

---

### Post by oilhat on 2023-11-07
I ran the SMART tools, and it says that it passed.  

To back up, I deleted the GPT before I ever started posting here.  It seems to me, that is why all I had was the MBR.  I recreated it with gisk and then started an install, which I aborted because of the EFI message.  Are you sure that my original installation did not have EFI?  Should I delete the GPT and try the install that way?

---

### Post by TheFu on 2023-11-07
> **1fallen said:**
> Sure:
```
sudo apt install smartmontools
```
run it against the current drive:
```
sudo smartctl -i /dev/sda
```
For a lot of info run as:
```
sudo smartctl --all /dev/sda
```

Or perhaps running an actual test would be better?
```
sudo smartctl -t short  /dev/sda
```

There's also a "long" test.

In the output, will be a time to wait until the test completes.  Wait for that time.  Short testing is usually just a few minutes.  I run those weekly on all my drives on all systems.  Monthly, I run a long test.  I save the output for all these tests to files (using a yyyy-mm-dd timestamp in the name) so the sort nice and then I can compare parameters that change over time to see if I have a disk with a catastrophic failure happening or one that is just losing a few blocks every year.  Most of the time, drives should get to their warranty period with ZERO failures, ZERO reallocated blocks and the only errors that arise would be due to cable issues.  Long tests can take 2-24 hours to complete.  These tests are non-destructive and happily run in the background.

Anyway, after the test completes, that is when you want to run a report.
```
sudo smartctl -a /dev/sda
```

Some devices and disk controllers need help being recognized.  USB connected disks commonly have odd controllers - many don't support SMART in any way.  There are motherboard settings that must be modified to enable SMART - this won't fix the USB controllers that don't support SMART, but it will enable it for SATA, SCSI, NVMe devices.   NVMe SMART output generally sucks and doesn't really provide much information.  There are nvme-specific tools for those devices.

SMART won't tell you things it doesn't know.  There's a bunch of different parameters that the storage devices store related to processing, warnings, errors. I think there are really only 5-10 that are useful for whether a disk is on the way to failure.  Even with SMART, disks that look perfect sometimes just fail.  Reports claim that happens about 22% of the time, so SMART is useful about 78% of the time a disk is failing.  Not perfect, but it is the best we have.  

You can search these forums for example SMART output and analysis.  My general stance is that for primary storage, I don't want any errors or reallocated blocks, even if there are spares available.  When 1 reallocation happens, I'll pull that disk from use as primary storage and move it to at least backup, if not sneaker-net use.  I've had 1 drive that became a backup disk after 1 SMART reallocation and worked for another 5 yrs just fine, using a few more reallocations over that time. It was a nice, smooth degradation of the device.  All storage devices are going to fail.  Often, they will give us some hints and if we pay attention to those hints, the failure can be a non-issue and many years of service.

Of course, some devices die very fast with little or no warning at all.  Those are why we need backups that happen as often as the data we don't want to lose is stored on them.  I do nightly backups.  15 yrs ago, I did weekly backups, because I wasn't modifying my systems too often.  20+ yrs ago, I did manual backups, until I happened to get really, really, lucky and happened to have a huge failure, but also happened to have a backup that was less than 1 week old.  At the time, I was doing backups perhaps every 3-6 months.  A few years before that, I lost 80% of all my data when 1 drive failed in an LVM LV that spanned 3 HDDs.  My LVM-fu was weak back then, so all the data on all 3 HDDs was lost.  I think I could do better data recovery today, but I don't need to worry about that, since I've had backup religion for some time.

I sleep much better too.

---

### Post by MAFoElffen on 2023-11-07
+1 --

To complete what was mentioned by TheFu about NVMe drives: As mentioned, because of that, for NVMe, I use a tool specific for NVMe drives, called 'nvme' from package  'nvme-cli':
```

mafoelffen@Mikes-B460M:~$ sudo nvme smart-log /dev/nvme0n1 -H
Smart Log for NVME device:nvme0n1 namespace-id:ffffffff
critical_warning            : 0
      Available Spare[0]             : 0
      Temp. Threshold[1]             : 0
      NVM subsystem Reliability[2]   : 0
      Read-only[3]                   : 0
      Volatile mem. backup failed[4] : 0
      Persistent Mem. RO[5]          : 0
temperature                : 32 C (305 Kelvin)
available_spare                : 100%
available_spare_threshold        : 10%
percentage_used                : 0%
endurance group critical warning summary: 0
data_units_read                : 10,012,231
data_units_written            : 6,330,246
host_read_commands            : 61,276,654
host_write_commands            : 24,966,398
controller_busy_time            : 107
power_cycles                : 75
power_on_hours                : 16
unsafe_shutdowns            : 54
media_errors                : 0
num_err_log_entries            : 0
Warning Temperature Time        : 0
Critical Composite Temperature Time    : 0
Temperature Sensor 1           : 32 C (305 Kelvin)
Temperature Sensor 2           : 35 C (308 Kelvin)
Thermal Management T1 Trans Count    : 0
Thermal Management T2 Trans Count    : 0
Thermal Management T1 Total Time    : 0
Thermal Management T2 Total Time    : 0

```
I have 'a few' NVMe drives in my server and workstation, and I like to keep track of them with nvme-cli... As well as my other SDD & HDD drives with 'smartmontools'. I've been using 'smartmontools' for over 10 years. It has been out for over 20 years. Later, I found 'nvme-cli 'which fit the bill for those types of drives. 

All my SSD's are Samsung, so I use their own Samsung Magician software for those... _But_ they do not have a Linux version of that (I wish they did!), and I very rarely boot Windows anymore, unless I have to.

---

### Post by oilhat on 2023-11-07
Ok.  So do I convert from GPT to MBR and then try the install?
```
[FONT=monospace][COLOR=#54ff54]**kubuntu@kubuntu**[/COLOR][COLOR=#000000]:[/COLOR][COLOR=#5454ff]**~**[/COLOR][COLOR=#000000]$ sudo gdisk /dev/sda [/COLOR]
GPT fdisk (gdisk) version 1.0.8 

Partition table scan: 
  MBR: protective 
  BSD: not present 
  APM: not present 
  GPT: present 

Found valid GPT with protective MBR; using GPT. 

Command (? for help): r

[/FONT]
```

After this, if I type 'g', it says it will convert GPT to MBR and then exit.  Should I do it?

After that, will I need to set a boot flag?  I think /dev/sda1 was bootable, but I am not sure.

---

### Post by TheFu on 2023-11-07
If you change from MBR to GPT, then you'll need to reinstall MS-Windows.  I doubt that is really desired.

---

### Post by MAFoElffen on 2023-11-07
But he jumped ahead of us and already converted his MBR to GPT already in Post #13. Then later said he "deleted GPT"... And now? He is asking about converting it back to MBR again...

Honestly: I'm lost were he is and what is going on. This became a big mess very quickly...

His original was MBR (Post #3). I lost track, and posted instructions for GPT by mistake, after he confirmed he had backups... That was my fault. As soon as he posted what gdisk said, I posted back to stop him and use fdisk... Which was the very next post... I guess he didn't see that post. He went on his own since then, a bit further, back and forth. Not really his fault. He just didn't understand what was going on. Probably from all the "many posts" at that time. (dang)

So, yes, right now I am lost. He needs to be a MBR partition table, unless he uses the Windows based utilities to convert it to GPT... Which is quite a job, that I usually do not recommend to many users. It is so much easier, rather than do that, to just reinstall Windows as UEFI booted, reinstall all programs, then restore the data. It just is.

He said he has recent backups... If he is now GPT based... Chime in on this... He might be already closer to reinstall both OS'es as UEFI, and restore his backups for his data...

He could always go back to MBR based, remain as Legacy boot, and restore his backups...

Dang. I guess this really depends what and how he did his backups, and what he can restore.

What do you think?

---

### Post by MAFoElffen on 2023-11-07
Everyone just got "very quiet"... You all now see what went on right?
> **MAFoElffen said:**
> [COLOR=#ff0000]<< EDIT --- Kept  this to show I screwed up posting this. I lost track that he had a MBR  partition table, and should have gave commands for him using 'fdisk'  >>[/COLOR]

Personally, I do a lot of scripting, so instead of using gdisk, I use the API for it, called sgdisk. If you did
...
.
He needs "clear instructions" to get back going. With everyone on the same page.

---

### Post by #&amp;thj^% on 2023-11-07
> **MAFoElffen said:**
> 

Honestly: I'm lost were he is and what is going on. This became a big mess very quickly...


Yes it has I'm staying silent now....I know what I would do, but.......

---

### Post by TheFu on 2023-11-07
I got quiet because I didn't want to get in the middle and cause another distraction.  Plus, I need my sleep.

If it were me, 

a) I wouldn't setup dual booting. Period.

b) After wasting over 60 minutes on an issue like this, I'd have wiped the system and started over by following my system recovery process.  It takes me about 45 minutes to be back where I was before with my data on my OS.  Wasting too much time trying to fix things was something I did 20 yrs ago.  Not anymore.

c) I'd have checked my recent SMART data for the disk.  Since I automatically run weekly tests and save the output, it would be 30 seconds to check it - at most.  Just because SMART says "PASSED", that actually means the test worked, not that the storage is fine.  Looking at the details of the parameters is required.  Sorry it isn't so trivial as to look for "PASSED" or "Completed without error". That just isn't sufficient.

---

### Post by MAFoElffen on 2023-11-07
+1 -- Yup. That's why I said, start over. Check that the disk is healthy or not. If the disk is bad, replace it. If not, treat it as if it were blank. If so... Reinstall, and restore your backups.

That would be your fastest and safest plan.

---

