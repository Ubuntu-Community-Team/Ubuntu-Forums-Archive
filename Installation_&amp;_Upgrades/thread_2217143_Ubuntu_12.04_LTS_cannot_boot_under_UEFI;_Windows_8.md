---
title: "Ubuntu 12.04 LTS cannot boot under UEFI; Windows 8 disappeared too"
date: 2014-04-15
forum: Installation &amp; Upgrades
---

### Post by Karl_Lerud on 2014-04-15
Hi everyone, I hope my problem is solvable. I just got my MSI GE70 back as it was being fixed and upgraded. It had Windows 8 and Ubuntu 12.04 on it, but I was expecting to have to reinstall everything. But everything was still there, but Ubuntu wouldn't boot (the BIOS had been updated). I reinstalled it on the same partition, and after a restart it went straight to the BIOS because all of a sudden, no hd's were recognized. All of this has been with "UEFI with CSM" set in the BIOS. 

I then discovered that I can't even boot from the Ubuntu liveUSB unless the boot mode is set to "Legacy" (the third mode is just "UEFI"): I get as far as the menu with the options to "try", "install", and check for errors, but if I select any of them, the screen goes black and nothing happens. I followed some instructions here [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) and used boot-repair and here is the output of that [http://paste.ubuntu.com/7257929/](http://paste.ubuntu.com/7257929/)

After a restart and switching the BIOS back to UEFI, it successfully went to GRUB, which included both Ubuntu and Windows. I selected Ubuntu and I got a blank purple screen that never went anywhere. After another restart, I don't get GRUB anymore, it just goes straight to the BIOS again, not seeing any hd's. 

I hope there is a way to get it work with UEFI, but I've also read that I can switch the Ubuntu installation to legacy, which would also be fine I guess. But I don't understand why I don't even have an option to boot into Windows anymore. The installation must have overwritten something. 

Thanks for any help!

---

### Post by oldfred on 2014-04-15
Did you have RAID originally?
I really do not know RAID, but thought the efi partition had to be outside the RAID, but yours is inside the RAID?

It looks like sda & sdc are RAID and sdb is a data drive? And sdd is flash drive.

From UEFI do you have Windows & Ubuntu entries?

Please do not forget to make your BIOS boot on mapper/isw_cgjjededdc_Volume1p2/EFI/ubuntu/grubx64.efi file!

But I do not know if this is your drive or your RAID which is inside your partitions:
You also show this error:
Error: The backup GPT table is not at the end of the disk, as it should be.
This might mean that another operating system believes the disk is smaller.
Fix, by moving the backup to the end (and removing the old backup)?

gpt partition table in middle of drive
  launch gdisk, then type x, then type e, then type w to save your changes
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table)


 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by Karl_Lerud on 2014-04-15
Thanks, yes I forgot to mention, I have two solid state hd's in RAID 0, and there's nothing on the platter storage drive. Before the BIOS upgrade I had the dual boot working, but not with GRUB actually, I had to change which partition to boot from in the BIOS, so that might have to do with what you said about EFI being outside the RAID. I don't know how to do this...

By entries, do you mean in the BIOS? There are currently no hard drives listed as boot devices in the BIOS; the only way I can get to them is by legacy booting with the liveUSB.

You said:
[COLOR=#000000]Please do not forget to make your BIOS boot on mapper/isw_cgjjededdc_Volume1p2/EFI/ubuntu/grubx64.efi file!
[/COLOR]I don't know what this means or how to do it...sorry I'm new at linux. Could you explain how to do this?

Meanwhile I will try to do the other two things you said.

---

### Post by oldfred on 2014-04-15
That entry is what Boot-Repair is saying but it does not make sense. 
With UEFI you only see in the menu Windows or ubuntu but the actual path is a lot longer. So Boot-Repair gives you the full path.
[COLOR=#000000]mapper/isw_cgjjededdc_Volume1p2/EFI/[/COLOR][COLOR=#ff0000]ubuntu/[/COLOR][COLOR=#000000]grubx64.efi 
All you should see in UEFI menu is the ubuntu and also a Windows entry.

But your UEFI is inside the RAID, and I thought UEFI did not have RAID drivers but only could read an efi or FAT32 partition outside the RAID.
But again I do not know RAID and only have seen one or two with RAID.

RAID 0 is not really recommended anyway. It is for a bit faster system, but you have high risk to total loss of data. If you have daily backups or other data preservation procedures or do not care about any data on this system then your RAID 0 may be ok.

[/COLOR]        Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

One or two users with similar systems, just broke RAID and went with two separate drives. Not sure of all the details.

---

### Post by Karl_Lerud on 2014-04-15
I'm aware of what RAID 0 does, and aside from the fact that it was the default on this machine, I decided I wanted the increase in speed, and I don't keep any extremely important stuff on here that I don't back up. So I want to try to fix this without breaking RAID and losing my windows install, but I'm definitely willing to do that if I can isolate the problem specifically to RAID. If I have to completely start over, then I'll probably go without the RAID because it's simpler, like you're saying. Meanwhile, I'm looking through the links you gave about gdisk, etc. I installed it while on legacy, inside the liveUSB session, but can't figure out how it works. The simple commands you pasted above don't seem to agree with its usage, they don't do anything.

Thanks again for any more help!

---

### Post by Karl_Lerud on 2014-04-15
Ok I'm starting to figure out gdisk. Here, /dev/sdc is the RAID array in question. Using the command 'v', I get the following error report:


[FONT=courier new]```

ubuntu@ubuntu:~$ sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 0.8.8

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): v

Caution: The CRC for the backup partition table is invalid. This table may
be corrupt. This program will automatically create a new backup partition
table when you save your partitions.

Problem: The secondary header's self-pointer indicates that it doesn't reside
at the end of the disk. If you've added a disk to a RAID array, use the 'e'
option on the experts' menu to adjust the secondary header's and partition
table's locations.

Problem: Disk is too small to hold all the data!
(Disk size is 468862128 sectors, needs to be 937713664 sectors.)
The 'e' option on the experts' menu may fix this problem.

Problem: GPT claims the disk is larger than it is! (Claimed last usable
sector is 937713630, but backup header is at
937713663 and disk size is 468862128 sectors.
The 'e' option on the experts' menu will probably fix this problem

Problem: partition 5 is too big for the disk.

Problem: partition 6 is too big for the disk.

Problem: partition 7 is too big for the disk.

Problem: partition 8 is too big for the disk.

Identified 8 problems!
```[/FONT]



If I use 'p' in Recovery/transformation options, it gives me this report of the array:


[FONT=courier new]
```

Recovery/transformation command (? for help): p
Disk /dev/sdc: 468862128 sectors, 223.6 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 9E857D76-B23B-45A7-8CCB-135AC9EC4D72
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 468862094
Partitions will be aligned on 256-sector boundaries
Total free space is 2014 sectors (1007.0 KiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048         1230847   600.0 MiB   2700  Basic data partition
   2         1230848         1845247   300.0 MiB   EF00  EFI system partition
   3         1845248         2107391   128.0 MiB   0C01  Microsoft reserved part
   4         2107392       457152511   217.0 GiB   0700  Basic data partition
   5       866632960       905695487   18.6 GiB    8200  
   6       905697280       906414079   350.0 MiB   2700  
   7       906416128       937711615   14.9 GiB    2700  Basic data partition
   8       457152512       866631039   195.3 GiB   0700
```
[/FONT]


I'm not sure about all these numbers. In the first report, it looks like it wants the RAID array to be the number of sectors that the 1TB platter drive is, which I definitely don't understand. The second report makes a little more sense to me; I've seen all 8 of these partitions before. Most of them were already there from Microsoft when I got the machine. The 217 GiB is my Windows install, and the 195 GiB must be the partition I made for Ubuntu, on which it is in theory still installed. (Again, I'm using the liveUSB right now, in legacy mode, because nothing else will boot.) I also made 20 gigs of swap space at some point, which is maybe what the 18.6 GiB entry is. 

Appreciate any help, I don't know how to interpret this. For instance, what do the "code"s and "name"s refer to? How do I use gdisk to repair this drive? I already tried the method suggested above, which is using 'x', then 'e', then 'w'. That doesn't seem to do anything, here it is:


[FONT=courier new]```

ubuntu@ubuntu:~$ sudo gdisk /dev/sdc
GPT fdisk (gdisk) version 0.8.8

Warning! Disk size is smaller than the main header indicates! Loading
secondary header from the last sector of the disk! You should use 'v' to
verify disk integrity, and perhaps options on the experts' menu to repair
the disk.
Caution: invalid backup GPT header, but valid main header; regenerating
backup header from main header.

Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Command (? for help): x

Expert command (? for help): e
Relocating backup data structures to the end of the disk

Expert command (? for help): w

Warning! Secondary partition table overlaps the last partition by
468849521 blocks!
You will need to delete this partition or resize it in another utility.

Problem: partition 5 is too big for the disk.

Problem: partition 6 is too big for the disk.

Problem: partition 7 is too big for the disk.

Problem: partition 8 is too big for the disk.
Aborting write operation!
Aborting write of new partition table.
```[/FONT]




Thanks again.

---

### Post by oldfred on 2014-04-15
Gdisk will use the primary partition table to create a corrected backup partiton table.
The link posted above to the askubuntu repair is by the author of gdisk and he is the one that really knows gpt partitioning.

The codes are used by gdisk to define the type of partition. Actually gpt uses very long GUIDs for definition of the partitions. The four letter codes are short cuts.
 Near bottom is list of standard GUIDs, descriptions should be the same as the gdisk shorten codes.
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Did your system boot in BIOS or UEFI before.
And do you have settings in UEFI/BIOS to directly boot RAID? That may be how it works.

The only reason not to have the RAID use all the disk is if you do have to have a efi or /boot partition outside of the RAID for it to work. But it seems you did not originally have that?

---

### Post by Karl_Lerud on 2014-04-16
In my Aptio setup utility (I don't know whether to call it a "BIOS" or "UEFI" or something else...) I have a "SATA Mode Selection" parameter, which is, and has always been, "RAID", since it has always treated these two drives as a RAID 0 config. The other options for that are "IDE" and "AHCI". And under "Boot" I have three "Boot mode select" options: "LEGACY", "UEFI", and "UEFI with CSM". The latter is what was selected when I recently got my computer back from the vendor. But I don't remember what the options were or what was selected here before the upgrade...maybe the upgrade updated the system to UEFI. 

I don't think I had any boot partition outside the RAID array before, when things were working, since the only place that could have been was on the 1TB platter drive, and I never have touched that. But as I said, the way it worked before was that I had to manually select, in the BIOS/whatever, which partition to boot from (in "Hard Disk Drive BBS Priorities") and "Windows Boot Loader" and "ubuntu" were both options. 

Appreciate advice. For now, I am wondering, since the outputs of gdisk clearly show that the array is messed up, if I can repair the array with gdisk, or some other way. The sector indeces overlap, etc. 

Thanks.

---

### Post by Karl_Lerud on 2014-04-16
Oh actually the sector indeces don't overlap, they're just out of order, sorry. I have no idea how to read this...

---

### Post by oldfred on 2014-04-16
I do not know RAID enough to know what issues you have.

But part of the issue is that the RAID says it is 480GB and gdisk says the drive is 223GiB.Disk /dev/sdc:

 468862128 sectors, 223.6 GiB
[FONT=courier new][/FONT] Disk /dev/mapper/isw_cgjjededdc_Volume1: 480.1 GB, 480109658112 bytes

I do not know if somehow your RAID is counting both drives. Normally it shows two hardware drives, but RAID then only sees one RAID drive that is the two combined. Depending on version of RAID, is how space is counted.
With RAID 0 it may just be the sum of the two drives? But then I do not know how gdisk would define partitions inside the RAID?

---

### Post by Karl_Lerud on 2014-04-16
RAID 0 should be seeing the two SSDs (240 GB each) as a single drive (of 480 GB) which gdisk seems to show, as the sizes of the partitions of that drive add up correctly. So, assuming we can think of the RAID array as a single drive as it's supposed to be (I don't know why it shows that [COLOR=#000000]223GiB number), I'm wondering how I can repair the boot processes of that drive. 






[/COLOR]

---

### Post by oldfred on 2014-04-16
I do not know how you mount & assemble a RAID, but gdisk may be just looking at each drive not at the RAID when it is working?

---

### Post by Karl_Lerud on 2014-04-16
That's possible, but there are a few things that make me think it is correctly interpreting the RAID, and I just have to fix the partitions. First, the partitions that I and windows have made in the past were to the RAID array, not to the individual disks, so I would think that, if gdisk was only able to see the two disks separately, there shouldn't be any partitions on them, there should just be two disks of exactly the same size. I don't know the details of how partition tables, file systems, etc., are distributed among the drives in a RAID array, but I would think it would be completely uninterpretable if something was only looking at the single drives, and would just appear unallocated. But I can't be sure.

If we go under the assumption that I am indeed looking at partitions on the array, can oldfred, or anyone else listening, offer advice as to how to use something like boot-repair to fix the partitions? There are a bunch of options in there and I certainly haven't exhausted them in my attempts so far. But I think I've already tried everything on the ubuntu UEFI page, to no avail. 

I might also try another format and reinstall of ubuntu, and track all the options I choose carefully. To recap, however, I currently can't boot even into the liveUSB under the UEFI modes, only legacy.

---

### Post by Karl_Lerud on 2014-04-16
I just found this, linked by oldfred, in a previous post; looks remarkably similar to my situation, and I am coming to accept that, one way or another, I'm going to have to start over :\

Would this be recommended? 

[http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/](http://sygard.no/2012/09/efi-dualboot-ubuntu-12-04-and-windows-8-in-raid0-on-sony-vaio-s/)

---

### Post by oldfred on 2014-04-16
Hope someone else can help that knows RAID a bit more than I do.

---

### Post by Karl_Lerud on 2014-04-16
A small update and complication...when I have it set to boot in legacy mode, it gives me an option to go into Intel's RAID configuration utility. I noticed that, usually, the array is "failed" and not bootable, and only one of the two physical ssd's appears. But sometimes, it labels the array as bootable and the status is normal and both ssd's are there. You were right that the 223 GiB number was the size of one of the physical drives; the boot during which I reported the gdisk output was one in which only one physical drive was recognized, so the array was completely broken. Also during that boot, Gparted showed that single drive as entirely unallocated...I guess I could have put two and two together. So it seems the partition table is stored on both (all) volumes in RAID, and that's what gdisk was trying to make sense of. This could explain quite a bit... (also, sometimes both ssd's will show up but only one will be a "member" so the array is still broken, and all I'm doing is here is restarting, eek)

I'm going to be depressed if this is a hardware issue, it will be the second time I RMA the machine. I just wonder why windows was working fine for a couple days (i.e. the RAID was working fine) and then I go and install ubuntu and all this stuff starts happening. 

Is there anything that could be causing this other than hardware? Advice...?

---

### Post by oldfred on 2014-04-16
I thought the advantage of RAID 0 was speed at the expense of reliability. If one drive fails both all data is lost as it is partiality on one and partially on the other.

But that was done more with hard drives as they were slower. Many that had to compile large applications or other drive intensive type applications changed to use SSDs as they were faster. But not necessarily SSD in RAID 0. 
Is system that much faster?

I find with my slow SSD on an older system is pretty fast. And what I  have seen is that new SSD are twice as fast as mine.

 [https://wiki.archlinux.org/index.php/SSD_Benchmarking](https://wiki.archlinux.org/index.php/SSD_Benchmarking)
[http://www.unix.com/unix-dummies-questions-answers/163209-difference-between-buffered-disk-reads-cached-reads.html](http://www.unix.com/unix-dummies-questions-answers/163209-difference-between-buffered-disk-reads-cached-reads.html)
SSD speed -T is cache, -t is device
fred@fred-Precise:~$ sudo hdparm -t /dev/sdd4
/dev/sdd4:
 Timing buffered disk reads: 626 MB in  3.01 seconds = 208.20 MB/sec
Older 160GB rotating drive:
/dev/sdb4:
 Timing buffered disk reads: 212 MB in  3.01 seconds =  70.46 MB/sec
USB2 flash drive
/dev/sde1:
 Timing buffered disk reads:  50 MB in  3.07 seconds =  16.26 MB/sec

Or would breaking the RAID 0 and having Windows on one drive and Ubuntu on the other drive make more sense. Only you can decide.

Many other threads that oldfred was posting in. I am sure there are many more.
I used this in google and changed date to just last year's search.
oldfred RAID 0 site:ubuntuforums.org

---

### Post by Karl_Lerud on 2014-04-18
[FONT=arial]Quite right about RAID 0. There have been side-by-side comparisons of single drives and RAID 0 arrays of comparable size, and the RAID arrays are indeed about twice as fast. But you're right that it's still probably pointless, and the point that's usually made is that ssd's are already fast enough for most purposes; the only serious advantage you'd have would be if you spend the whole day transferring 500 mb files between ssd RAID 0 arrays...not exactly my situation.

Benchmarking study:
[/FONT]http://www.tomshardware.com/reviews/ssd-raid-benchmark,3485-3.html[FONT=arial]

This might not, after all, be a hardware issue. Apologies for being hasty. Let me do a quick summary of this thread so far, and then a major update.[/FONT][FONT=arial]
[/FONT]
[FONT=arial]When I got the computer back from repairs, ubuntu wasn't booting, so I reinstalled it (at this point I have two main partitions, one for windows, one for ubuntu, on a RAID 0 array of ssd's). After the first restart, nothing booted and it went straight to the bios. There were no bootable hard drives/partitions listed in there. I tried many things to see if I could repair the boot sectors that got messed up, but I couldn't salvage either the windows or the ubuntu installs. And, I couldn't even boot bootable burned iso's off of a usb stick unless the boot mode in the bios was set to legacy (although that turned out to be another issue...). [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]When you boot in legacy mode, it also shows you the status of the connected hard drives and RAID arrays. Here I started to notice that the RAID array was usually broken and one ssd was completely missing. Sometimes however both would show up. This is the main thing that led me to conclude that it must be a faulty drive; it really seemed like a hardware issue. I was also thinking it might be a faulty bus or something on the new motherboard. As a last step, I completely deleted the RAID array, and the second drive was still not showing up.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]But then I switched the physical locations of the two drives, and the second drive re-appeared, along with the broken RAID array. I deleted the array again, restarted, and both drives remained. Then I switched the physical locations back to their original configuration, and both drives still remained. So...the ubuntu install, along with the attempts at repairs I made afterwards, must have permanently messed up the RAID array (I didn't know that was possible). I decided against trying RAID again and just attempted to reinstall the operating systems on the two separate drives (like oldfred suggested). [/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]This was initially still failing because I had put the bios back in UEFI mode. What I found out was that even the bootable usb stick, along with the hard drives, needed to be configured with a GPT partition table if you're using UEFI mode. I should have already known that...but I didn't even know what a partition table or partitioning scheme was until now. I was using Rufus 1.4.6 to burn the installation iso's for both operating systems, and it actually has an option for what kind of partition table to use; I had been using MBR. Long story short(er), once I made those bootable usb's with GPT, I installed both operating systems completely successfully. 

For the purposes of this thread, I think we can consider this "solved". However, GRUB isn't working, and I have to switch between the drives in the bios to "dual-boot". If anyone has any ideas about that, I'd be interested, but I'll do some better research if I decide I care enough to make another thread about it. I'm just glad to be booting into ubuntu again...

Thanks for the help oldfred!



[/FONT]

---

### Post by oldfred on 2014-04-18
If still 12.04 run a BootInfo report.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

With 14.04 there is not yet a ppa for trusty to install Boot-Repair.

---

### Post by Karl_Lerud on 2014-04-20
Yes I'm still using 12.04 LTS. The boot-repair-disk didn't boot for some reason, so I just used the installation liveUSB, did "try", and installed boot-repair. Here's the output:

[http://paste.ubuntu.com/7290068/](http://paste.ubuntu.com/7290068/)

Thanks, look forward to thoughts.

---

### Post by oldfred on 2014-04-20
I see your 4 drives all gpt partitioned. And one efi partition on sdc2. I do prefer to have a separate efi partition on every drive and an install on every drive so any drive can be booted if you have issues without any other drive.

Boot-Repair says you have secure boot on. Have you tried with it off. But still boot with UEFI.
You do show signed versions of grub & kernel so it should work with secure boot on.

But some have reported they cannot boot Windows from grub menu with secure boot on.

Can you boot ubuntu entry from UEFI/BIOS menu?
Some systems will only boot Windows entry as vendor has modified UEFI against standard to only boot a Windows entry.

---

