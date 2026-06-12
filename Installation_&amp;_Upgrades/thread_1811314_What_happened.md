---
title: "What happened?"
date: 2011-07-24
forum: Installation &amp; Upgrades
---

### Post by mvelte54 on 2011-07-24
I have 10.04 installed on my WD 40GiB (sda1) with a WD 80GiB (sdb1) installed for extra storage.
I have another older machine with a WD 13GiB which I removed and installed into my current machine. First I unplugged the IDE cables and power supplies from the afor mentioned HDD's of course. I then installed 'Qimo' for my kids to the 13GiB. I removed the 13 and reinstalled the cables and power supplies back to the 40/80GiB HDD's. Now when I fire it up it sees both hard drives and the CDROM drive. But stops there. 'SYSTEM FAILURE INSERT BOOT DISK'? 
I do then it wants to reinstall 10.04 on sda1? 
I open GParted and it says that it is 38.xx GiB of unallocated space. Weird it says there are no operating systems on sda1.
When I try to install from the disk it says that 10.04 is installed and I can install them side by side and choose between them at startup. Or my other option is to install them on sdb1? I chose sda1. But it can't install there (sda1) it says it's mounted.

I admit I'm a n00bie at this but this I don't understand. If it's mounted why won't it load, second how could it erase 10.04 when it is unplugged and powered down and GParted say's it isn't there but if I try to reinstall it's a different story?

I love Ubuntu but sometimes it just makes me scratch my head in wonder. :confused:
Anybody have a clue as to what happened and how to fix it?

---

### Post by YesWeCan on 2011-07-24
> **mvelte54 said:**
> I love Ubuntu but sometimes it just makes me scratch my head in wonder. :confused:
:P Join the club.

Of course as your 40GB and 80GB disks were disconnected you cannot have done any harm to them. Perhaps when you reconnected them you accidentally switched their sata cables. So the bios was trying to boot the 80GB not the 40GB.

Try swapping the cables. If that doesn't work you need to provide more detailed info by booting from live Ubuntu CD and downloading and running this: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Post the RESULTS.txt hre inside code tags (use the #)

---

### Post by oldfred on 2011-07-24
You mentioned IDE cables. Very old systems used jumpers on hard drive to set primary master which was the only boot drive that BIOS could use.

Slightly newer IDE systems use cable select. The drive at the end of the cable is the primary master and the only boot drive. But newer BIOS that support SATA have BIOS that can change boot drive (my SATA only system still calls it primary master).

Did you switch order on cable or change jumpers?

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Old_Grey_Wolf on 2011-07-24
Edit: oldfred probably has the right answer if they are really IDE drives.

---

### Post by mvelte54 on 2011-07-24
Thank you all for you quick replies.
Yes it is IDE cables and yes I have them set with jumpers to master and slave. I reinstalled the cables as they were. The end of the cable with the blue stripe the master the second cable attachment which is gray set as slave. 

I did not remove the jumpers or the hard drives for that matter just unplugged from the system. No power, no data corruption that is what has got me puzzled. I am prepared to open GParted and reformat and start over but I won't learn anything that way.

As 'YesWeCan' suggested I have inserted the 10.04 live CD and it just wants to install 10.04 not boot into 10.04. 

That is what I'm trying to figure out if it's there, because as I stated earlier '_I can install 10.04 beside 10.04 on sda1 (master) and choose between them_' which was my original thought. Just reformat the new 10.04 partition and hopefully run the original.

When I tried to install to sda1 (master) it starts to format then says it can't because sda1 is mounted. Funny thing everything is still on sdb1 (slave) but sda1 (master) which is _38.xx GiB of unallocated space according to GParted_?

Any ideas? I'm stumped...

---

### Post by oldfred on 2011-07-24
I do not expect this to really show anything if you made no changes but just to check:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Old_Grey_Wolf on 2011-07-24
Have you looked in the BIOS setup to see what Hard Disk it is set to boot from first?

---

### Post by YesWeCan on 2011-07-25
Oops, IDE cables not SATA.
> **mvelte54 said:**
> As 'YesWeCan' suggested I have inserted the 10.04 live CD and it just wants to install 10.04 not boot into 10.04.
I'm not sure what is going on here. When you boot off the CD do you not get a menu with things like "try before installing", "check disc", "memory test"? It has to be the "PC desktop CD" not the alternate install CD. [http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

---

### Post by mvelte54 on 2011-07-25
To 'YesWeCan' I'm sorry yes, when I load the CD 10.04 into the machine it does show the menu:
Try without installing
Install
Memory check, etc.
Yes it is the Desktop PC CD not the Alternative. 

I'm sorry I miss spoke. I did do the memory test and all checks out fine that is when I just decided to reinstall and I then 'found a spanner in the works' as it were.

I was thinking that maybe I didn't insert the IDE cable in fully into the HDD but then I don't understand how it would see it and say that 10.04 is already installed. 

To Old_Gray_Wolf I will check again and see which it is trying to boot from.

I did download the 'bootinfoscript' and I will give it a try and report the results. 

Thanks again for all the help guys...

---

### Post by mvelte54 on 2011-07-25
Okay now I am really corn-fused!
If I disconnected the HDD's both the IDE cables and the power cables then reinstalled them but now I see my MBR is toast if I'm reading this right:

                 Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => No boot loader is installed in the MBR of /dev/sda.
 => Windows is installed in the MBR of /dev/sdb.

sda1: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''

sda2: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda3: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''

sda4: __________________________________________________________________________

    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
mount: unknown filesystem type ''
mount: unknown filesystem type ''

sdb1: __________________________________________________________________________

    File system:       ext3
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files:        

============================ Drive/Partition Info: =============================

Drive: sda _____________________________________________________________________

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sda1       2,147,518,464 4,370,149,375 2,222,630,912  83 Linux
/dev/sda2       2,222,635,006 4,373,131,263 2,150,496,258   5 Extended
Invalid MBR Signature found.
EBR refers to a location outside the hard drive.
/dev/sda3       2,147,516,416 4,295,032,831 2,147,516,416   0 Empty
/dev/sda4       2,147,516,416 4,295,032,831 2,147,516,416   0 Empty

/dev/sda1 ends after the last sector of /dev/sda
/dev/sda1 overlaps with /dev/sda2
/dev/sda1 overlaps with /dev/sda3
/dev/sda1 overlaps with /dev/sda4
/dev/sda2 ends after the last sector of /dev/sda
/dev/sda2 overlaps with /dev/sda3
/dev/sda2 overlaps with /dev/sda4
/dev/sda3 ends after the last sector of /dev/sda
/dev/sda4 ends after the last sector of /dev/sda

Drive: sdb _____________________________________________________________________

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot  Start Sector    End Sector  # of Sectors  Id System

/dev/sdb1    *             63    78,109,903    78,109,841  83 Linux


"blkid" output: ________________________________________________________________

Device           UUID                                   TYPE       LABEL

/dev/loop0                                              squashfs   
/dev/ramzswap0                                          swap       
/dev/sdb1        ce9cc3cd-816d-4da9-8aab-e29132237f9e   ext3       C-3PO Storage

================================ Mount points: =================================

Device           Mount_Point              Type       Options

/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)


======================== Unknown MBRs/Boot Sectors/etc: ========================

Unknown BootLoader on sda1


Unknown BootLoader on sda2


Unknown BootLoader on sda3


Unknown BootLoader on sda4



=============================== StdErr Messages: ===============================

hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda1: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda2: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda3: No such file or directory
hexdump: /dev/sda4: No such file or directory
hexdump: /dev/sda4: No such file or directory

You notice it sees sdb (aka C-3PO Storage)
but not sda (aka C-3PO)

I see that sdb has windows as the MBR, how is that possible when I formatted it with GParted before I installed it and started using it?

Here is a thought what if I uninstall sdb (IDE and the power cable and see if it will boot from sda would that possibly reinstall the MBR?
Again I'm stumped. I checked and yes, I am trying to boot from sda. 
I will await your replies.
Thanks again.

---

### Post by YesWeCan on 2011-07-25
> **mvelte54 said:**
> I see that sdb has windows as the MBR, how is that possible when I formatted it with GParted before I installed it and started using it?
It looks *as if* the partition table and boot code (which comprise the MBR) on sda have been corrupted. But it may be the bios is not reading the data off the disk correctly and it just looks corrupted.

The MBR has 3 parts to it: boot code, signature (optional) and partition table. The MBR is created before the disk is partitioned and formatted. When you formatted using GParted you didn't need to change the boot code and signature. The standard MBR is called "Windows" by bootinfoscript.

> Here is a thought what if I uninstall sdb (IDE and the power cable and see if it will boot from sda would that possibly reinstall the MBR?
No. The MBR has to be written by a tool like GParted or lilo or a Windows CD.

If it was working ok and then you disconnected it and then reconnected it and it no longer works, I imagine there is some connection problem. But I am not sure what to recommend. I'm a fan of simplification. So I'd probably leave sdb disconnected and try cable and slot combinations and set sda to master, until I got it working.

---

### Post by oldfred on 2011-07-25
I might see if testdisk can find the old partition table entries. It looks like the start of the drive was totally overwritten but it still sees 4 partitions but with totally invalid entries.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)

---

### Post by mvelte54 on 2011-07-25
Thanks oldfred I am in the process of down loading Test Disk I will burn and familiarize myself with how to use it from the wiki.

Thank you all I will keep you posted.

---

### Post by 23dornot23d on 2011-07-25
The old BIOS ..... you had to set the [COLOR=Red]**[cylinder heads sectors]("http://en.wikipedia.org/wiki/Cylinder-head-sector")**[/COLOR]  if I remember and the disk up and sometimes they had three choices ..... only one being the right one ......

Check the BIOS settings against the HDD disk information on the disk  ...... not sure how old your BIOS is .......


[COLOR=Red][B]If this is the case and it wrongly identified the disk ..... then the problems you are seeing may come from that

( just a thought - but maybe worth checking first )[/B][/COLOR]


on the disk drives the information is usually printed on them somewhere 

My initial thought is the BIOS is set up wrong for one of the the drives ........ 
(as sdb looks ok and is giving the correct information.)

so sda may be set up for the wrong  [COLOR=Red]**[cylinder heads sectors]("http://en.wikipedia.org/wiki/Cylinder-head-sector")**[/COLOR] in the BIOS ..... maybe .... 

hope its as simple as this.

( thinking about it if you just added one disk the automatic settings may have been re-set 
to the right settings for the other 13 Gig disk you had in there ,,,,, just ensure they swapped back properly
for the 40 Gig disk matching it precisely in the BIOS it should let you see the figures next to it on a old BIOS
these can sometimes be set manually to match the disk you put in ..... )

> 
I have another older machine with a WD 13GiB which I removed and installed into my current machine.
seeing its just one disk thats wrong ..... and it is sda ..... which is the initial boot disk .....

and now it may not correctly be identified in your BIOS for the 40 Gig disk you are now putting back into it ..... 

seems to make sense ..... ( used to happen if the battery backup failed )

Maybe why just one disk is not giving the right information back .....

[I][U][B]sda may be set up for the wrong  [COLOR=Red][cylinder heads sectors]("http://en.wikipedia.org/wiki/Cylinder-head-sector")[/COLOR] in the BIOS

used to happen on very old motherboards 
[/B][/U][/I]

---

### Post by mvelte54 on 2011-07-26
To 23dornot23d: 
That was my first thought when I fired it up was, what HDD is it seeing. I went into the BIOS and it listed WD000000 or what ever weird number it was just not the one of two I expected. Well that didn't make any sense at all so I changed it to the 80 GiB HDD and tried to reboot. No MBR which didn't surprise me because there is none. So I went back into the BIOS again and there it was the 40 GiB HDD. The numbers escape me now. But at least now it sees it, but it too has no MBR.

To oldfred: 
I really need to pay more attention to what I read. I see you clearly pointed out that 'TestDisk' is available in the repositories. Doh!?!

I read the wiki twice wondering how I was going to use TestDisk when I clearly need the LiveCD to boot into the machine. Again Doh!?! I downloaded the disk and burned it so I have a copy if anyone is interested... anyone? Sorry but I'm keeping this one. I'm going to wear it around my neck like a dead Albatross. ;)

I am on my way to the laboratory now and I will keep all posted on my progress.

YOU GUYS ROCK!

---

### Post by 23dornot23d on 2011-07-26
If you have a digital camera or camera phone .... take a photo of the BIOS and the setting for the Hard Drive
if you would ...... and post it on here .... ( [[COLOR=Red]_***imageshack***_[/COLOR]]("http://imageshack.us/") is good for uploading photos or [COLOR=Red]_***[Minus]("http://minus.com/")***_[/COLOR] which is dead simple drag and drop )
 when set for the 40 Gig ..... also could you give more information like the make and model
of the 40 Gig hard drive ......

I would start with this as the main thing .....track down as much as we can about it first ..... sometimes the 
serial number on the drive contains the vital information .......

Once we can relate the 40 Gig drive ...... and its physical set up

to

The BIOS and its Set up ...... for the 40 Gig Hard Drive then ....


We can then make some clear decisions on what is wrong .......... and move on knowing that it is picking
the correct information up for the 40 Gig HD and setting the drive correctly in the BIOS ....

---

### Post by oldfred on 2011-07-26
The boot script showed this for sdb, but there was no info for sda:

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

I think 23dornot23d may be onto something in the BIOS. Perhaps to get other drive working a setting was changed & it was not changed back? For last 12-15 years since drives got too large for MBR CHS cylinder, heads, sectors settings, drives have been configured as LBA. 

Post info 23dornot23d requested and/or details of how drive is configured in BIOS.

---

### Post by mvelte54 on 2011-07-27
I'm back... C-3PO unfortunately was very uncooperative. I tried it all. The TestDisk, Ubuntu Rescue Remix, even GParted Live CD all to no avail.
When I put in TestDisk and ran: sudo testdisk6.9/linux/testdisk_static it froze. I tried rewriting it at least a dozen ways and got the same results.  Tried Ubuntu Rescue Remix I got this message: cannot write outside partition on hard drive.
System Rescue CD pretty much the same.

I then fired up GParted off the live CD and told it to format sda. I then proceeded to reinstall the OS 10.04. All is working and all programs reinstalled. I for the life of me can't figure that one out.

If you care here are the specks for C-3PO:
ASUS P4B motherboard running an Intel Pentium 4 cpu 1400 Mhz with 497.3 MiB of memory
Gnome 2.30.2 (Ubuntu 2010-06-05)
Linux 2.6.32-33 generic (Kernel)
i686

Primary Master WDC WD 400BB-00DEA0 dev/sda 37.27 GiB
Primary Slave WDC WD 800JB-00FSA0 dev/sdb
Secondary Master Sony CD-RW CRX300E

After the formatting and reinstall of the 40 GiB here are the stats:

Unallocated 1.00 MiB
dev/sda1   ext4   35.83 GiB   3.35 GiB used   32.50 GiB boot
sda2 extended 1.426 GiB
sda5 linux-swap 1.42 GiB

I also installed 'Back in Time' from the Ubuntu Software Center and told it to save the file on sdb1.
Don't know if it will do any good but in hindsight I wish I had it.

I believe it was in 2000 when I had him built. Yes, an old machine but my faithful companion through thick and thin. At his age I'm sure I'll be back here again. Thank you all I learned a lot. I guess I'll call this solved.

---

### Post by 23dornot23d on 2011-07-27
Excellent result - glad you got it sorted out ...... ;)

[I still keep a older machine going too a Acer Aspire 1350L laptop ..... 6 years old ...
but very battered and if you so much as touch a USB cable it will lock up ...
The CD drive is non operable ... and the battery is dead ..... but I will not part with it .... ]

It too only has a 40 Gig hard drive ..... but it still has plenty of life left in it yet .... ;)

---

