---
title: "Good to go?"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by Joe LV on 2007-05-24
Hello everyone,

I do not write to complain, merely to relate my personal experience during preliminary installation of Ubuntu to see if things I observed are normal.

Regarding hardware ...

My system is a Dell Dimension 2400 desktop, Pentium IV, 2.2GHz clock, 1GB memory, with a flat panel display.

To expand limitations of the system case size, CD-R/W and CD-ROM drives in front mounts were moved outboard to external cases with the 2 internal hard drives then moved up into the available slots and mounted in racks so they can be easily removed.  This expedites full backups using duplicate units and the entire system is now simply a resource for any operating system plugged into the "C" slot.  In normal Windows XP operations, the operating system and applications software are kept on "C" formatted in NTFS while production data is kept on "D" formatted in FAT32 to provide Linux compatability.  USB 2.0 was also used to add a second floppy as "B" and an external "E" hard drive to provide for daily backups of production work on "D".

Full configuration is now ... 

"A" internal 1.44MB floppy (bootable)
"B" external 1.44MB floppy on USB
"C" internal hard disk, removable,  40GB in NTFS (bootable), replaced for Ubuntu
"D" internal hard disk, removable, 160GB in FAT32
"E" external hard disk, 160GB in FAT32 on USB
"F" CD-R/W (bootable)
"G" CD-ROM

Bios boot scan first checks the "A" floppy, then the "F" CD, and lastly the "C" disk.

Parallel port links a Ricoh laser printer as LPT1.

Serial port links a Casio KL8100 plastic label printer.

USB ports also link:

    a Lexmark X6170 MFC,
    a Brother 5100C MFC,
    an Epson C5400 MFC,
    an Avery 9100 mailing label printer, and -
    a wireless keyboard and mouse.

Regarding the wireless keyboard and mouse, it was found after I acquired the system that they could not function with some applications so "hardwired" units were also installed and Windows recognizes 2 of each. 

When the Ubuntu CD arrived in the mail, I prepared a spare 40GB hard drive using Western Digital Data Lifeguard Tools on CD to format the entire unit as a single FAT32 partition and installed it in the "C" slot to make it available for Linux.

Booting the Ubuntu CD, the first problem was that the screen came up with the upper fifth of the display shown at the bottom, the remainder at the top, a half inch black bar between, and the entire display shifted to the left.  I noted that, as with Windows, parameters were set at 1024 x 768 with refresh at 75Hz so the only remaining control was rotation.  I attempted changing it from "normal" to "right" which initially flipped the display 90 degrees vertically but Ubuntu then indicated "correcting" and everything was fine when the display returned.

Another strange symptom was that Ubuntu kept polling my USB floppy drive designated "B" all during the installation.  I finally got it to stop by inserting a blank floppy in the unit.

Installation to hard disk was also a bit strange ...

1) Ubuntu identified both the internal IDE "C" and "D" drives as SCSI and it did not see the "E" drive on USB at all.

2) For some reason, although the "C" drive was completely blank, it also indicated it would condense the "D" drive (my production work) and install itself there so I instead selected the lower option directing it to use drive "C".

3) It then indicated it would install 2 partitions, partition 1 in EXT3 and partition 5 as swap.  It seemed strange that partitions would be designated 1 and 5, what happened to 2, 3, and 4?  Are 1 and 5 standard Linux designations?

In any event, I now have a dedicated drive which can successfully boot Ubuntu when installed in the "C" slot so my next attempts, when time permits, will be trying to reach the outside world using the Winmodem that came with the Dell and figuring out why Ubuntu cannot see the "E" drive connected via USB.

Another problem anticipated is that I noted the version of Open Office on the Ubuntu CD is apparently level 2 which I found to have problems when copying web data with both Internet Explorer or Firefox and using paste to transfer it into an Open Office document.  Something changed between Open Office 1 and 2 with the result that in some instances none of the paste options can successfully bring data into a document.  As a result, I continue to use level 1 and I expect a Linux version of it can still be obtained but I wonder if it will be compatible with Ubuntu.

If I can then get any of my printers functioning with Ubuntu, hopefully my Lexmark X6170 MFC which is most heavily used, I will be well on the way to minimizing Windows usage.

Any comments regarding symptoms I observed during the installation will be appreciated.  I have no experience with Linux so I hope to confirm that I have a correct installation before I proceed further.

Many thanks,

Joe

---

### Post by jpittack on 2007-10-07
You seem to be running in to a large amount of problems. I personally would check the integrity of the CD (Check CD for Defects) at the starting menu when the system is booted off of the CD.

Perhaps your "B" Drive is bootable?

Are you sure you have IDE drives?  Could you give me the models?

As far as condensing the "D" drive goes, it sounds like it defaulted to trying to use that drive.  You seem to have fixed that problem, but I am sorry it didn't default to where you would like it to.

I assume the partitions you mention are on this "C" drive.  1 and 5 are not standard.  I have 4 and no swap.  I suggest seeing if any space as been alloted to 2,3, and 4.  Your installation will work fine no matter what.  If space was alloted then you might run out of space (doesn't that happen no matter what?).

Legacy OpenOffice is available on the download page of their website.

I can't tell you about the printer.  What I can tell you is that Gutsy Gibbon due in under two weeks is supposed to be able to automatically detect your printer.

Post back any results that I have asked for or any questions you might have.

---

### Post by Herman on 2007-10-07
> 3) It then indicated it would install 2 partitions, partition 1 in EXT3 and partition 5 as swap. It seemed strange that partitions would be designated 1 and 5, what happened to 2, 3, and 4? Are 1 and 5 standard Linux designations? That's right, that's how partitions are normally numbered.
There is a special area reserved in the MSDOS type Master Boot Record in the first sector of our hard disks called the 'partition table'. 
The partition table has room in it for only _four_ partitions to be described, so we can have a maximum of four regular partitions called 'Primary' partions and the numbers 1,2,3 and 4 are reserved for those kind of partitions.

Probably your main Ubuntu partition would be installed in primary partition number 1.

You 'Extended' partition would probably have taken the next available slot of you partition table to make it partition 2.

An 'Extended' type of partition is a special type of 'Primary' partition and it is allowed to take any number between 1 and 4 too. It's a good idea to make one of your four main partitions an 'Extended' partition because your 'Extended' partition is special in that it can be subdivided into as many more partitions as you'd probably ever need. Those are called 'logical' partitions and they have to all be inside the extended partition and they work in a series, kind of like a series circuit in electricity, but not exactly, that's just an analogy.

Primary partitions are allowed to be numbered from 5 to whatever they go up to, some say it's possible to have 63 of them, but I think I read somewhere that 20 partitions is a limit for Ubuntu, I'm not sure, but that should be enough for most of us anyway (on one hard disk).
So your swap area, because it's a logical partition, took the first avaiible partition number that a logical partition is allowed to have, which is partition number 5.

Everything there seems perfectly normal with you partition numbering. If you want to some day you have the option open to you for making one or two more primary partitions which will take their place in your partition table as number 3 and 4.
If you decide to make more logical partitions some day they will be attached in series inside your extended partition and will be numbered 6, 7, 8.. and so on.

When you get used to the way partitions are numbered it will make sense to you and you'll start to like it. 

Regards, Herman :)

---

