---
title: "Vista, GRUB, and corrupt NTFS."
date: 2008-08-07
forum: Installation &amp; Upgrades
---

### Post by Rockman4140 on 2008-08-07
I've come across a very interesting problem. After reading about GRUB and how it works, I may have a small understanding of what I did wrong, but I'm still not 100% sure with continuing. Any guidance I could get would be wonderful.

I recently re-installed Ubuntu after having failed attempts with Feisty's wireless with the Atheros card. During the install I wiped and remade the partitions. After being greeted with a broken GRUB, I went online to read what was happening. Error 22, Apparently GRUB doesn't enjoy me deleting and remaking partitions all willy-nilly.

It seems that I messed up more than I originally thought. It seems I corrupted my NTFS with resizing it through GParted. This is the error that is given to me while looking at it in GParted
"Failed to startup volume: Invalid Argument"
A large errata follows, and I will type it up if it is needed. My fdisk -l scares me, it says under /dev/sda1 (My Toshiba backup Partition) Partition 1 does not end on a cylinder boundary.

Back to what I originally was posting about, When I boot GRUB and choose Windows, it says starting Stage 2, and prompts me again to choose an OS. I can boot into Ubuntu fine, but I cannot get into my Vista partition.

My biggest problem now is unscrewing my NTFS side, I have very vital files I cannot lose. Is there any program I could use to attempt to copy the data over, or is there any way to salvage my data?

---

### Post by SuperSonic4 on 2008-08-07
Can you not access the NTFS files from ubuntu and put them somewhere else?

---

### Post by falcon61102 on 2008-08-07
If you can mount your NTFS partition, your best bet would be to backup your NTFS partition now before proceeding any further just in case it gets wiped later.  If you have an external or another HD you can use the dd function and example would be:
```
sudo dd if=/dev/sda3 of=/dev/sdb1
```
Replace the "if" statement with your NTFS partition and the "of" statement with your destination, perferably an external.  Then you can extract whatever data you need to without worrying about losing it to a corrupt drive.

After backing up that partition, you have a couple options on how to go about fixing your partitions but the easiest may end up running gparted off a LiveCD and repartitioning the entire drive.

Your other option is to attempt to fix your partitions one by one.  Post the output to your fdisk-l and we can see about that as well.

---

### Post by Rockman4140 on 2008-08-07
At this current time, no I cannot. While fdisk -l shows the partition still there, I cannot mount it using the LiveCD. It reads my Toshiba Partition, root, and home partitions. I'm using the LiveCD because it seems GParted isn't included in the normal install of Ubuntu?

I could read it fine earlier today when I was still getting Error 22. I think I may have wrote GRUB to my MBR, which is probably a reason why it won't load? I do fear I will never gain a solid mastery of Linux.

Is there a tool that would repair Vista's Bootloader from a CD or USB device? At this moment I will sacrifice the rest of my computer to backup what I have on my NTFS partition.
EDIT: The copy of my fdisk -l

```
Disk /dev/sda: 160.0GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16085 * 512 = 8225280 bytes
Disk identifier 0x209b4b29

Device Boot     Start     End     Blocks     Id     System
/dev/sda1          1      192     1536000    27     Unknown
Partition 1 does not end on a cylinder boundary.
/dev/sda2         192    11384    89896960   7      HPFS/NTFS
/dev/sda3         11385  17521    492954452+  5     Extended
/dev/sda5        11385   11645    2096451    82     Linux swap / Solaris
/dev/sda6        11646   13603    15727603   83     Linux
/dev/sda7        13604   17521    31471303+  83     Linux
```

---

### Post by falcon61102 on 2008-08-07
If you have Vista's original CD you should be able to repair the MBR with that.  Also, the Super Grub Disk might be some help if that doesn't work; it will help you set up your GRUB.  

[www.supergrubdisk.org](www.supergrubdisk.org)

What type of error, if any, are you getting if you attempt to mount the partition?

---

### Post by Rockman4140 on 2008-08-08
Vista came OEM. No luck with a Vista CD. (Not like I'd pay for that POS anyways) It shows in GParted that sda2 is my 85 gig NTFS system, and it can read the boot flag.

Would it hurt any if I attempted to add some blank space in between the backup and main NTFS partitions? Would it help the situation any?
EDIT: Moved those 8 bits around and it helped nothing. Whenever I check the information, it lists this.

```
WARNING:
Failed to startup volume: Invalid argument.
Failed to mount /dev/sda2: Invalid Argument
This device '/dev/sda2/' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a partition (e.g. /dev/hda, not dev/hda1)? Or the other way around?

ntfsresize v2.0.0 (libntfs 10:0:0)
Failed to startup volume: Invalid Argument
ERROR(22): Opening '/dev/sda2/' as NTFS failed: Invalid Argument
This device '/dev/sda2/' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a partition (e.g. /dev/hda, not dev/hda1)?
This error might also occur if the disk was incorrectly repartitioned (see the ntfsresize FAQ)

Unable to read the contents of this filesystem!
Because of this some operations may be unavailable.
```

...That sounds damn depressing. I'm probably SOL, eh? I'll download and burn that ISO, I hope it works and can fix this.

---

### Post by nagasuman on 2008-08-08
check this out. more stuff coming in here

[http://iweavers.blogspot.com](http://iweavers.blogspot.com)

:guitar:

---

### Post by falcon61102 on 2008-08-08
You weren't given a recovery CD with your computer?  That's normally the OS install CD.

The Super Grub Disk will help you fix your GRUB problem but I don't think it will help you any on your partition problem.  

Did you attempt to resize your backup partition (sda1) at all?

---

### Post by Rockman4140 on 2008-08-08
> **falcon61102 said:**
> You weren't given a recovery CD with your computer?  That's normally the OS install CD.

The Super Grub Disk will help you fix your GRUB problem but I don't think it will help you any on your partition problem.  

Did you attempt to resize your backup partition (sda1) at all?

Honestly? I forgot... I know I removed my old Linux Distro and wipes the swap from that, remade partitions for them, and then I may have attempted to close up the unallocated space in between the other partitions...If that is the cause of this, I'm quite ready to kick myself in the face...

I'll have to rummage through my crap to find a CD...This will teach me to be lenient with system backups. Would it possibly help any if I were to wipe Linux and everything other than the NTFS partitions you think? I ***cannot*** allow myself to lose what I have.

EDIT: Well, unless it is possible to hand-hack a NTFS MBR back to health, I'm SOL. At least next time I'll devote an external to weekly backups of my files. I will see if I can use the CD that came with the PC as a Vista install CD. Most OEM programs enjoy not allowing such features, at least that has been my experience with it.

---

### Post by Rockman4140 on 2008-08-08
Ah, Yes. After removing my Ubuntu install, I get GRUB Error 22, File not Found. I shall return once I give it a go with my OEM disk.
EDIT1:It seems that Windows has made improvements with their OEM software. I'm quite pleased that I actually have an option other than "Bare Bones Wipe" now. (My first PC was a POS Compaq with ME)

---

### Post by falcon61102 on 2008-08-08
One thing you could try is deleting that first partition (sda1) and resizing you NTFS to incorporate all the space in front of it.  Part of the problem is likely to be associated with partition not ending on cylinder boundary.

Also, a GRUB 22 error is common when you delete your linux install.  Basically it means that the segment that is in your MBR is loading but it cannot find the boot files on your HD, which is because you erased it.  Once you reinstall, it will fix itself.

---

### Post by Rockman4140 on 2008-08-08
Well, I'm attempting to go at it with Startup Repair, but that has not worked. It seems the only command line tools this set is missing seems to be all the useful ones, like FIXMBR.

Yes, like a moron I installed GRUB over Vista's MBR, and it seems I do not have the tools to repair my partition. Would it be possible to see if I could expand the partition both ways and see if it would right itself that way?

---

### Post by Rockman4140 on 2008-08-08
> **falcon61102 said:**
> One thing you could try is deleting that first partition (sda1) and resizing you NTFS to incorporate all the space in front of it.  Part of the problem is likely to be associated with partition not ending on cylinder boundary.

Also, a GRUB 22 error is common when you delete your linux install.  Basically it means that the segment that is in your MBR is loading but it cannot find the boot files on your HD, which is because you erased it.  Once you reinstall, it will fix itself.
Well, I'm attempting to go at it with Startup Repair, but that has not worked. It seems the only command line tools this set is missing seems to be all the useful ones, like FIXMBR.

Yes, like a moron I installed GRUB over Vista's MBR, and it seems I do not have the tools to repair my partition. Would it be possible to see if I could expand the partition both ways and see if it would right itself that way?

I do not want to format the first partition, it is my Toshiba partition, and if everything goes to hell and back, it will be my absolute last shot, I don't want to risk that quite yet.

---

### Post by Rockman4140 on 2008-08-08
Alright, I have a new plan. It seems Photo Rec may be able to pull what I need to off of the hard drive, the harder plan is actually mounting my USB Hard-drive to the GParted LiveCD instance.

As a last resort I found out I can download a repair ISO from Bittorrent. Hopefully this can be salvaged. I do know that I can see my files. The maker of DiskTest and PhotoRec deserve praise.

---

### Post by falcon61102 on 2008-08-08
You're USB HD should automount even on the LiveCD.  If it doesn't automount, check under Places>Computer.

If you have to mount it, run:
```
sudo fdisk -l
```
Find the partition you'd like to mount, then run:
```
sudo mkdir /media/External
sudo mount /dev/sdb1 /media/External
```

The first command creates the mount point in your media folder.
Change /dev/sdb1 to be whatever partition that you need to.

If you receive any errors on attempting the mount, post here and we'll see what can do to fix it.  Hope this helps, good luck.

---

### Post by Rockman4140 on 2008-08-08
I'm slowly learning the ins and outs of the filesystem. I did successfully mount and copy files from my corrupt HD to my USB. I now have 40 gigs to search through, but it's better than nothing at least.

Just a question, does Photorec segfault often when dealing with large quantities of data? I only got halfway done with my drive, I guess it went south when I went to sleep.

Is there a good Windows/Linux tool that is optimized for searching through batches of folders? I currently have 300 folders of 500 files each. XP

---

### Post by falcon61102 on 2008-08-08
Glad that you got everything copied over so you can find what you need.

As far as Photorec goes, I'm not sure, I've never used the program.

That's a lot of files that you've got to go through.  Both Windows and Linux have built in search utilities that can search for a number of different attributes, but other than that, I'm not sure.  

Have you begun to put your system back together or you just concentrating on sorting all that data you have?

---

### Post by Rockman4140 on 2008-08-08
I've got half of them sadly, I need to try again and see if I can recover more. It seems my NTFS is quite corrupt, all of the Windows tools won't even recognize it. I do recall that the end of one cylinder was the beginning of another, would that be a major cause of it? If so, from Linux would there be an option to attempt to "force" the partition up a cylinder?

---

### Post by falcon61102 on 2008-08-08
It may help some.  I was doing some reading and it seems that many people have success with testdisk in being able to restore corrupted partition tables and whatnot.

---

### Post by Herman on 2008-08-08
Personally I prefer[ Ubuntu-rescue-remix]("http://ubuntu-rescue-remix.org/") for USB for running Photorec from. It seems to run best when USB external hard drive is larger (in GB) than the file system being recovered. 
That's only my opinion, I have only played with Photorec a little.

---

### Post by Rockman4140 on 2008-08-09
It got most of my files, 165417472 out of 179793920

But I have upwards of...Hundreds of thousands of files to sort through now...Hmm...

Is there anyone familiar with an easy GUI tool? (I see the command line in my sleep now.)

---

### Post by Herman on 2008-08-09
Actually, Linux commands are just the best things ever invented for sorting large numbers of files out fast.  :)

I wouldn't worry too much about that right now though, as long as they're all safe, you might be better off turning your attention back to trying to fix your problems.

From reading what you've posted so far I'd be inclined to try out TestDisk's [NTFS Boot sector recovery]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step#NTFS_Boot_sector_recovery") feature.
By the sounds of things you installed GRUB to your Vista boot sector somehow, (Vista doesn't have an MBR, that's short for 'Master Boot Record', and that belongs to the hard disk).
There's a spare copy of the boot sector at the end of your NTFS file system, TestDisk might be able to restore it for you. It should be worth a try at least, now that you have all your files copied to some other media.

Maybe you'll never need to bother sorting them, if you can fix your NTFS.

---

### Post by Rockman4140 on 2008-08-09
I'm moderately sure I really did a number on my system. After scrounging for a video file that is priceless to me, I found a small, 5kb chunk. It's likened to finding a piece of a broken urn that held a loved one's ashes. It sucks, it really does. It's all my fault, too.

I was wondering if Photorec is capable of searching for one certain file, which brings up another strange point.

TestDisk lets me browse for an image to use for the Bootloader, while browsing, my folders are all intact and it lists the actual file I need! Is there ANY way to use TestDisk to pull that one file to another hard drive? Once I secure that file, I'll go ahead and wipe everything else, leave the remains to be sorted through at a later date.

Thank you for correcting my terminology, I do need to keep this all straight. I attempted it with no luck. To clarify, it could not find a backup, and after pointing it to the file resting on my C: drive, it still didn't work. Instead of an actual GRUB 22 Error I get BOOTMGR not found, press Ctrl-Alt-Del to restart. I downloaded the Vista Support CD, and the automated startup wouldn't even help it. I may give that one last shot, though. For now the NTFS partition has not (cannot) be touched, and I am desperate enough to continue shooting to fix it until I can pull that damn movie off.

But, I must regain my wits. Rest shall befall me. I can hopefully tackle this tomorrow with a fresh mind.

---

### Post by Herman on 2008-08-09
Your hard disk will wait for you pretty much forever, having a rest is a good idea. You can leave these things for years and still come back and fix them or recover data.

---

### Post by Herman on 2008-08-09
:) Here are my thoughts on your problems.

You have three problems.

1) I corrupted my NTFS with resizing it through GParted. This is the error that is given to me while looking at it in GParted  "Failed to startup volume: Invalid Argument"

2) My fdisk -l scares me, it says under /dev/sda1 (My Toshiba backup Partition) Partition 1 does not end on a cylinder boundary.

3) I think I may have wrote GRUB to my MBR, which is probably a reason why it won't load? 

1) About problem number 1 exists in your file system, (which Vista is installed in) you should be able to fix that with CHKDSK. You'll need some kind of a Windows Installation CD for that.
It is recommended to run CHKDSK after resizing an NTFS partition with GParted. The documentation for GParted advises that. I think it's fairly normal for the NTFS file system to need a CHKDSK after resizing with GParted.
Probably your video file is fragmented and the rest of the file exists somewhere else on the disk. The problem with recovering the file right now is that since the file system was already a mess, the end of the file doesn't point to the next part of the file right now. That's what file system checks are for. I don't know how you can fix that except for running CHKDSK on the volume. The catch 22 here is you're frightened of touching the partition until you recover the file. The reason why you can't recover the complete file is because the file system needs to be fixed.
The file system chck might solve your boot loader problem too, (can't find bootmgr).

2) Problem number 2 exists in your partition table, which is in your hard disk's MBR. (Which is not part of Vista). The first partition not ending on cylinder boundary should be fixable simply by resizing the partition smaller. I would try with GParted first and if that doesn't do it, I'd try with another partition editor or TestDisk.

3) Your boot sector (which is part of Vista), I think is already fixed? You said TestDisk couldn't find the backup for the boot sector, but you also said that now you are getting the 'bootmgr not found' error instead of the GRUB Error, which to me seems to indicate your boot sector is fixed. 
If not, there are other ways to fix your boot sector, FIXBOOT should be the command to use, (as opposed to FIXMBR). I think Vista uses the same boot sector as Windows XP. Super Grub Disk can probably fix Vista's boot sector too I think. Here's a linkto a thread, [HOW-TO restoring XP and Vista Bootloader & Restoring GRUB ]("http://ubuntuforums.org/showthread.php?t=740221")by lswest's and bodhi.zazen.

I'm not a Vista expert by any means, so take my opinions with a grain of salt and look for more advise and opinions before taking action. 
The main thing I'm trying to emphasize here is that you appear to have three separate problems, in three separate locations on your hard disk, which will require three solutions.

Regards, Herman :)

---

### Post by Rockman4140 on 2008-08-10
Thank you, everyone for your help with my issue, I really appreciate it more than you will ever know. Right now I'd be up a creek without a canoe without this forum.

I used Vista's Repair CD that was downloadable, and the problem is it did not recognize the drive at all, it was not available to be loaded, and the automatic start repair did nothing. The command you gave me is something I haven't tried, Herman, I'll have to give it a shot.

I'm still very confused and infuriated by TestDisk's ability to search the folders. The file I need is like, 3 folders deep from the C drive, and I can see the actual file I need! It's taunting me. Is there another tool other than Photorec? It seems there is nothing better than Photorec, though. If only there was some way to cling to what is left of my directory structure...

Windows cannot read my drive, Linux cannot read my drive, the only 3 programs that still detect it are GParted, Photorec and TestDisk. There is some file integrity there, but I just need some way to access it...

I removed GRUB, Window's bootloader should be running fresh now if I had BOOTMGR on my PC, but since it isn't I'm screwed. That small issue is fixed AFAIK. If I used GRUB to replace Vista's BL on accident, that wouldn't mess over BOOTMGR, would it? That is more a sign of the corruption?

---

### Post by Herman on 2008-08-10
> I removed GRUB, Window's bootloader should be running fresh now if I had BOOTMGR on my PC, but since it isn't I'm screwed. That small issue is fixed AFAIK. If I used GRUB to replace Vista's BL on accident, that wouldn't mess over BOOTMGR, would it? That is more a sign of the corruption?I'm sure you still have bootmgr in your PC. The problem is your computer doesn't know how to find it.

The hard disk is divided up into little squares called 'sectors', much like a map is divided up with lines of latitude and longitude. Of course, we now know that the Earth is spherical, but a hard disk is flat, but the main thing is that we like to divide things up into squares because it's easier for us to think about that way. We can count them and give them numbers to keep track of which one is which.
Now, the MBR (Master Boot Record), is situated in sector number 1 of your hard disk, which is right at the outside edge somewhere. 
The MBR contains a little boot loader code, the hard disk ID number, ('disk signature'), your parition table, and a 2byte 'bootable disc signature', and that's about all it can hold because it's only a tiny wee 512 bye sector.
The boot loader code that can fit in the MBR is just big enough to point to a partition, there isn't enough room in there for a whole boot loader to fit into. 
When we say we are installing a boot loader in the MBR, we don't really mean that, it's just a quick way of saying we're installing the code in the MBR to point to a boot loader, and that's called the 'stage1' of the boot loader.
In the case of Windows, the stage1 file only points to the boot sector, which is like a stepping stone. The boot sector is located in the first sector of your Windows partition, which is quite a long way from the MBR. There's another pointer in the boot sector that points to the Windows boot loader, which is actually inside your Windows parition.

It doesn't hurt your Windows boot loader, bootmgr, if you install GRUB in your hard disk's MBR (recommended), or even in your Windows boot sector (not recommended), your bootmgr will still be there and will not be touched. 
The problem with having GRUB's pointer in your Windows boot sector is simply that it won't point to your Windows boot loader, it points back to GRUB. That's why when you selected Windows from your GRUB menu it kept going back to your GRUB menu again and it wouldn't boot Windows as you expected.

The tiny code in the MBR can be easily overwritten with code pointing to Windows again, that's what the FIXMBR command in Windows is for, and the tiny boot sector code is also easy to replace too, that's what the FIXBOOT command does.
The FIXMBR command and the FIXBOOT command are usually run from a [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm").
Or, it can be restored from the backup boot sector with TestDisk. There are other ways as well.
I am guessing that if you already fixed your boot sector, the reason why bootmgr is still 'missing' is most likely because the file system can't find it.

After the boot sector, the next few sectors of most partitions are 'file system blocks'. (A 'block' is two sectors, or some other given number of sectors). The file system blocks are full of numbers to record what sectors files were left in, and if there are bits and pieces of the file scattered in many locations on the hard disc (where ever there happened to be empty squares at the time the file was written to disc, then the end of one file needs to be able to remember where the beginning of the next joining bit is located somehow. How the file system does that is too complicated for me, but it does that somehow. 
Now, when GParted resized the partition, it did so as carefully as it could, but obviously it would have had to move some files if they were in the way. After GParted is done, it's a good idea to run CHKDSK /F or CHKDSK /R to tidy up the file system so it will link up all those bits and peices of scattered files and stuff. Right now your file system is in disarray I think, and that's why you only got the first part of your video file and probably why bootmgr is missing. It's probably there all right, but it can't be found because the file system is all confused. I'm just guessing, but that seems to be what happens sometimes with Linux too. Sometimes when GRUB can't boot Linux a file system check is all that is needed, so I suppose it happens with Windows as well.

CHKDSK /F or CHKDSK /R are normally also run from a [Windows Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm"). (Sorry, I only have a Windows XP link there and not Vista, but I imagine you would have something equivalent in your Vista Repair CD that you downloaded.

If the Vista Repair CD doesn't recognize the Vista partition, maybe that's because of the partitions not starting and finishing on a cylinder boundary. I'm not sure about that, because I have read somewhere that Vista has it's own unique ideas about partitioning. I'm not sure if that's true or not because I think most people use GParted for partitioning when they install Ubuntu and it probably has as high a success rate as any other partitioning program or maybe better.
However, something seems to be wrong there with yours, unfortunately. 
There is a good chance that TestDsik can fix your partition table or maybe GParted can. If you haven't tried yet to get your first partition fixed then maybe that should be a good thing to try next. If you can get your the Vista Repair CD to recognize the partition then I think you'll be okay from there.

Maybe you should go to GParted's website, it has it's own forum, probably TestDisk does too, or at least you should be able to find someone there who can help you, and see if you can get advice from someone who knows more than I do. I'm trying my best but I can only suggest fairly basic and common ways to fix things that have worked for me before, but I don't use Vista. Naturally there are experts will know a lot more than I do about file systems and disc partitioning, and maybe even Vista's peculiarities.
I really hope you can get it fixed and get your files back.

---

