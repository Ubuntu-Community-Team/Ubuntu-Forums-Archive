---
title: "Problem w/ Partitioner"
date: 2005-07-19
forum: Installation &amp; Upgrades
---

### Post by bhound89 on 2005-07-19
HI

I have windows xp installed, and I want to install Ubuntu on another partition. I went to manually edit table, went to the windows partition, and then went to size. It then asked me if I wanted to save changes, so I say yes, and it asks what size the partition should be. I change it from 80 GB to 20 GB and hit enter.  It takes me back to the table with windows still at 80 GB!

Help please!

---

### Post by darkmatter on 2005-07-19
The installers partitioner doesn't handle the resizing of existing partitions. For that you need a third party partitioning tool such as Partition Magic, etc.

---

### Post by Benchrest on 2005-07-19
[QUOTE=darkmatter]The installers partitioner doesn't handle the resizing of existing partitions. For that you need a third party partitioning tool such as Partition Magic, etc.[/QUOTE]

Maybe I'm too new to know what I'm doing and got lucky, but I used the partitioner on the ubuntu 5.04 and had no problems partitioning an existing windows partition. I think it should work. I have Windows 98SE on a laptop with a 20gb harddrive already partitioned to 1.7 gb drive C and 18 gb drive D. I first defraged drive D. Then ubundu installer reduced that drive to 8 gb without losing any data. The 10 gb left I made two linux partitions.

The partitioner started automatically as part of the install. Took all the easiest answers. I think it should work.
Rich

---

### Post by darkmatter on 2005-07-19
[QUOTE=Benchrest]Maybe I'm too new to know what I'm doing and got lucky, but I used the partitioner on the ubuntu 5.04 and had no problems partitioning an existing windows partition. I think it should work. I have Windows 98SE on a laptop with a 20gb harddrive already partitioned to 1.7 gb drive C and 18 gb drive D. I first defraged drive D. Then ubundu installer reduced that drive to 8 gb without losing any data. The 10 gb left I made two linux partitions.

The partitioner started automatically as part of the install. Took all the easiest answers. I think it should work.
Rich[/QUOTE]

Yes, technically it should be safe, but my comment was directed at the resize of a Windows partition (the one with the OS), as Windows tends to write system files across the disk, the first stage of partitioning should always be handled prior to actually setting up the partitions for your GNU/Linux installation(to defrag/move files). 

He may get lucky if he uses the method above - However, there is always a chance that a straight resize/install may delete system files which may have been written at the end of the windows partition, hence my comment that the partitioner doesn't handle resizing.

Better safe then sorry.

As for the partitioning, I personally prefer fdisk. Though for someone new to Linux partitioning, I would recommend cfdisk (menu driven, and similar to Windows)

---

### Post by bhound89 on 2005-07-19
So are you saying that if I defrag, it will work?

---

### Post by mingus on 2005-07-19
Everyone is correct above.  This is a safe approach:

1.  In XP, from the command line do >chkdsk /r or invoke chksk from My Computer/Properties/Advanced, check all the options.  This will (well, *should*) fix any broken chains in the filesystem and then quarantine any bad sectors.  This permits the next step to be done cleanly.

2.  Defrag the disk.  Do it again.

3.  Now you can try the Ubuntu partitioner.  The files should have already been packed to the front of the partition, so there is little to move.  If you have a Knoppix, Kanotix, SimplyMEPIS, etc. live-CD you can run QTParted from it to resize; that does provide better feedback and control than the Ubuntu partitioner.

Finally, PartitionMagic is, well, magic.  If the other tools can't do it, quite possibly PM still can.

---

### Post by not_yet on 2005-07-19
yes you can use the ubuntu install disk to resize your NTFS partition

first defragment your drive with windows

when you get to the part about choosing a "size" the size needs to be put in as a "%"

the % that you enter will be the % of the disk allocated to windose

for example if you enter 80%, then 80% will be windose and 20% free space

for this to work there must be free space available, ie: if your drive is 90% full, you cannot resize it to have say 30 or 40 % free space

---

### Post by not_yet on 2005-07-19
visual example ->[http://www3.telus.net/linux4u/](http://www3.telus.net/linux4u/)

---

### Post by mingus on 2005-07-19
[QUOTE=bhound89]So are you saying that if I defrag, it will work?[/QUOTE]

You must have been typing as I was . . . see my post above.  IMO, it is critical to run chkdsk first.  Defrag can run and there can still be bad sectors.  When a resizing program encounters such, it can choke.  That is why PartitionMagic will sometimes stop and tell you to run chkdsk.

---

### Post by bhound89 on 2005-07-19
Thanks for all the help!
I will try chkdsk and defrag.

---

### Post by bhound89 on 2005-07-19
OK, I tried chkdsk and defragging, and when I clicked on Size: 80 GB in the installation, I just get a blue screen with the hard drive light on.

---

### Post by az on 2005-07-19
You do not need to express the size as a percent.  You can, but you do not have to.

How long did you wait at the blue screen?  Was there a progress bar?  It can take quite a while to move around a lot of data, and even with a small partition, the progress bar only tends to start moving at the very end.

If you do CTRL-ALT-F3, do you see any errors or warnings?  There is also a log kept in /var/log (?), you can go to CTRL-ALT-F3 and look there for a clue...

The installer will refuse to do something before screwing up your system knowingly...

---

### Post by mingus on 2005-07-19
azz's advice is good.  If that doesn't work . . .

double-check that chkdsk /r actually executed.  You must reboot, and then there is a DOS screen which reports the progress.  It usually takes a good while when the /r option is invoked.  Also try chkdsk with the /f switch, from the command window.  Be sure to note that chkdsk completed without errors; I have seen it be unable to do the repair (blame MS).

If you are quite sure that chkdsk ran successfully, and you defragged, then AFAIK you are left with several options:

1.  Download a live-CD like Knoppix and try QTParted to resize.  
2.  Use PartitionMagic.  If PM can't do it, it usually tells you why.
3.  Use Microsoft's recommended procedure, which is to create a backup, delete the partition, create a new smaller partition, and then restore from your backup.  

btw, what is the disk partition layout?  If you have a live-CD, do a "fdisk -l" and post it back here.  Is there a recovery or hidden partition on the disk?

---

### Post by bhound89 on 2005-07-20
I am positive that chkdsk /r ran with no errors. I can't really understand why it is blanking out where it is, because its not doing any partitioning, its just taking me to the size dialog.

No progress bar.

I might be able to install Ubuntu first, then install windows, because in the windows installation, you can create a partition for it. Then I could reconfigure GRUB? Is that an option, because this is a clean install of windows anyway?

---

### Post by mingus on 2005-07-20
*I am positive that chkdsk /r ran with no errors. I can't really understand why it is blanking out where it is, because its not doing any partitioning, its just taking me to the size dialog.*

It's finding something it doesn't like, or maybe . . . umm . . . a data entry issue?  The installer's user interaction is not very intuitive.
[I]
I might be able to install Ubuntu first, then install windows, because in the windows installation, you can create a partition for it. Then I could reconfigure GRUB? Is that an option, because this is a clean install of windows anyway?[/I]

So it's OK to do a **clean** install of Windows again???  If so, in the re-install just delete all the partitions and then create the first one with the size you wanted all along for W$.  Leave the rest of the disk unpartitioned; do not use W$ to create the partition that you will put Ubuntu on.  The Ubuntu partitioner should not have problem using that unallocated space.  If for some strange reason it does, you can go back and create that partition in W$, but as a general rule, it's best to create partitions with the OS that you will install on that partition.

As far as installing Ubuntu and then W$, this is possible but you need to know what you are doing.  One method would be to have Ubuntu create a first partition but not format it, and a second partition that would be for itself (formatted ext3, mount point is / meaning root directory); then when you installed W$ it would format the first partition with NTFS.  W$ would also over-write grub in the MBR, so you would either need to dual-boot from W$ or re-install grub.  

An alternate method would be to create and install Ubuntu on the first partition, then install W$ and let it create a second partition for itself; this method will *only* work if you mark the W$ partition as "active" (also called setting the "bootable" flag).  And again as above, you would eithe need to set up dual-boot in W$ or reinstall grub to the MBR.

Perhaps I misunderstood your post, but if you have the option to clean install W$, then IMO the first procedure above, just installing it on a first partition the size you want and leaving the rest of the space unallocated, is the easiest and safest.

And just fyi, running chkdsk with the /f switch might do different checks than the /r swtich.  MS documentation is very frustrating about chkdsk.  In one place it describes using the /p switch, not described anywhere else.  And supposedly /r includes what all the other switches do, but that's not really clear.  I suspect /f looks at filesystem integrity and /r checks disk sectors.  With NTFS, you can get corruption in what is called the MFT (master file table); when that happens you're hosed, and the only option is to backup/reformat/restore.

---

