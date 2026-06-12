---
title: "External HDD - Files Erased?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by gnackattack on 2008-05-24
Okay, I want to precede this with the warning that despite being fairly computer literate, I'm not that great when it gets down the nitty gritty details that might be important in solving this problem.  If you could try to be fairly detailed in your assistance that would be great.

Basically I wanted to install Ubuntu Hardy Heron (this bit went okay, I'm using it right now in fact) but when it came to the hard drive partitioning part I was a bit confused.  I had a previous installation of Ubuntu (7.10) that I wanted to eliminate before installing 8.04 so I deleted that partition and set it up as the new install location for 8.04.  It all seemed to go fine until I tried to view the files on my external hard drive - they all seem to be gone!

Here's the thing though, the hard drive is a 500gb drive and I find it hard to believe that the drive could have possibly been formatted in the brief time it took to install Ubuntu.  Note that I never clicked anything relating to this 500gb drive when installing Ubuntu, also note that my other drive - home to my Windows installation - remains completely functional.  So given this information, are all those files really gone, or is it possible that - for some reason - they just can't be seen?  Is there any way to restore them?

---

### Post by Steve413z on 2008-05-24
it's possible for a professional to recover those files

i've also seen some people have luck with this program: [http://www.recovermyfiles.com/](http://www.recovermyfiles.com/)

---

### Post by gnackattack on 2008-05-24
Hey Steve - thanks for the suggestion.  Having looked at the software, it seems as though if there are indeed any files left this software will find them.  Any ideas on why this might have happened?  It just seems bizarre :confused:



:guitar:
(I saw that in the list and had to click it)

---

### Post by Steve413z on 2008-05-24
the installer can format an entire drive very quickly now, and I think its too easy to screw up the formatting with the ubuntu installer, it doesn't give you much warning, when you play with the ubuntu installer, double and tripple check everything before you mess with the partitions

---

### Post by iaculallad on 2008-05-24
Lesson learned :lolflag:

Assuming that you did really "wrongly" partition your drive, there's a big possibility of losing those precious data. So, before doing the partition thing (and assuming that you had previously been working on Gutsy and saved all your data to it's /home directory), learn to BACKUP. Doing partition is an irreversible thing.

Always backup you data prior to using a Partition Manager. If you're planning to install Hardy, try creating a separate /home partition on another logical partition on your HDD.

---

### Post by binary00mind on 2008-05-24
> **gnackattack said:**
> Okay, I want to precede this with the warning that despite being fairly computer literate, I'm not that great when it gets down the nitty gritty details that might be important in solving this problem.  If you could try to be fairly detailed in your assistance that would be great.

Basically I wanted to install Ubuntu Hardy Heron (this bit went okay, I'm using it right now in fact) but when it came to the hard drive partitioning part I was a bit confused.  I had a previous installation of Ubuntu (7.10) that I wanted to eliminate before installing 8.04 so I deleted that partition and set it up as the new install location for 8.04.  It all seemed to go fine until I tried to view the files on my external hard drive - they all seem to be gone!

Here's the thing though, the hard drive is a 500gb drive and I find it hard to believe that the drive could have possibly been formatted in the brief time it took to install Ubuntu.  Note that I never clicked anything relating to this 500gb drive when installing Ubuntu, also note that my other drive - home to my Windows installation - remains completely functional.  So given this information, are all those files really gone, or is it possible that - for some reason - they just can't be seen?  Is there any way to restore them?
[COLOR="Black"][/COLOR] I Was just about to leave, and I could not belive my eyes. The exactly same thing happened to me. Your drive or disk was't formatted. Your MBR is messed up. I Tried to fix it (recover) by Disc Recovery Pro. Linux friendly. But the land is too big and 60% I got it back RAW. but since then I Have found a better tool. There are 2 tools, both open source. 1 is "Test Disk", manipulation with MBR and "Part 240" (go for 244) Where You can created up to 33 Primary Partitions on 1 Disk ! with back up to recover the tables later. But Test Disk You can view MBR like newspaper..But I wonder how it happen. I never said anything, because I did not think anybody would believ me. There is also G.A.G. but It has to be done before the disaster occure..The place to get the toys- [http://majorgeeks.com](http://majorgeeks.com)

---

### Post by gnackattack on 2008-05-24
> **binary00mind said:**
> [COLOR="Black"][/COLOR] I Was just about to leave, and I could not belive my eyes. The exactly same thing happened to me. Your drive or disk was't formatted. Your MBR is messed up. I Tried to fix it (recover) by Disc Recovery Pro. Linux friendly. But the land is too big and 60% I got it back RAW. but since then I Have found a better tool. There are 2 tools, both open source. 1 is "Test Disk", manipulation with MBR and "Part 240" (go for 244) Where You can created up to 33 Primary Partitions on 1 Disk ! with back up to recover the tables later. But Test Disk You can view MBR like newspaper..But I wonder how it happen. I never said anything, because I did not think anybody would believ me. There is also G.A.G. but It has to be done before the disaster occure..The place to get the toys- [http://majorgeeks.com](http://majorgeeks.com)

That's very interesting - I suspected there was something funny going on.  I seriously did NOT touch the drive at all during installation of Ubuntu (it didn't even OFFER me the ability to format a drive until I had selected the partition and deleted it - surely I didn't accidentally perform both of those tasks on two separate drives without noticing).

> 
Lesson learned

Assuming that you did really "wrongly" partition your drive, there's a big possibility of losing those precious data. So, before doing the partition thing (and assuming that you had previously been working on Gutsy and saved all your data to it's /home directory), learn to BACKUP. Doing partition is an irreversible thing.

Always backup you data prior to using a Partition Manager. If you're planning to install Hardy, try creating a separate /home partition on another logical partition on your HDD.

Well the real lesson learned here is not to install Ubuntu with an external HDD plugged in.  I didn't touch it at all during installation.  I didn't wrongly partition - I didn't even partition at all, as I already had partitions set up from the last time I installed Ubuntu.  Additionally, the external HDD is entirely separate, I didn't do anything to that drive at all.  The drive I was working with is an entirely different device.  Not sure how it happened but as binary00mind has suggested, I assume for whatever reason the MBR of the external HDD has been overwritten.

---

### Post by iaculallad on 2008-05-24
As to what I know, Ubuntu does NOT do a thing you would not let it do. Just be patient on reading notes being displayed on screen before clicking on buttons or answering with "YES" on questions, as the saying goes "Haste makes Waste".

But as you said, it's much better to unplug external devices before installing Ubuntu (w/c might work for you anyway) :lolflag:

---

### Post by meierfra. on 2008-05-24
> or is it possible that - for some reason - they just can't be seen? 

Please post the output of 

```
sudo fdisk -l
```
(l is a Lowercase L)

---

### Post by meierfra. on 2008-05-24
> I assume for whatever reason the MBR of the external HDD has been overwritten.

But that can be easily fixed.

---

### Post by gnackattack on 2008-05-24
> **meierfra. said:**
> But that can be easily fixed.

Actually after writing that I did a bit more looking around and I think its more likely it's the MFT that's broken.  Is it possible to fix this?  I can see a "System Volume Information" folder which leads me to believe there is a new MFT in place - does that make the other one unretrievable?

I ran the file recovery software someone recommended earlier and it began turning up files, so I know they're there - but the software would surely require me to copy the files somewhere else before being able to actually use them normally again.  That's 500gb of free space that I don't have!  In other words to avoid having to slowly copy off the files to another location is there a way I might be able to restore the lost MFT?

---

### Post by gnackattack on 2008-05-24
> **iaculallad said:**
> As to what I know, Ubuntu does NOT do a thing you would not let it do. Just be patient on reading notes being displayed on screen before clicking on buttons or answering with "YES" on questions, as the saying goes "Haste makes Waste".

But as you said, it's much better to unplug external devices before installing Ubuntu (w/c might work for you anyway) :lolflag:

As binary00mind mentioned earlier, its not the kind of thing anyone would expect anyone else to believe :p  I know what it looks like, but I carefully read everything (I had 3 other partitions I wanted to keep safe so I was being even more cautious than usual).

At any rate regardless of how it happened I know that the files are there now (thank god) it's just a matter of fixing the HD so the OS can read them.  Any ideas?

---

### Post by meierfra. on 2008-05-24
You should provide more details: Post "sudo fdisk -l". Are you able to mount your NTFS partition in Ubuntu, but it does not show any files? Same thing from Windows?

Running "CHKDSK /F /R"   might fix your  MFT: [http://www.ntfs.com/quest14.htm]("http://www.ntfs.com/quest14.htm")

---

### Post by gnackattack on 2008-05-24
> **meierfra. said:**
> You should provide more details: Post "sudo fdisk -l". Are you able to mount your NTFS partition in Ubuntu, but it does not show any files? Same thing from Windows?

Running "CHKDSK /F /R"   might fix your  MFT: [http://www.ntfs.com/quest14.htm]("http://www.ntfs.com/quest14.htm")

Correct - the hard drive mounts but doesn't show any files (except in Ubuntu where I see a "System Volume Information" folder).

At the moment I'm not at home I have the HD with me running some utilities on it from my Vista laptop - is there a tool in Vista that might give you the information you'd like to see?  If not I'll be home in a few hours and can run fdisk -l then.

---

### Post by meierfra. on 2008-05-24
"fdisk -l"  list all the partition on your hard drive. I just want to see whether your 500GB drive got formated or partitioned  in some way. I don' t know much about Vista, but I think you should  be able to go into "Disk Management" and have a look at you partitions.

---

### Post by gnackattack on 2008-05-24
> **meierfra. said:**
> "fdisk -l"  list all the partition on your hard drive. I just want to see whether your 500GB drive got formated or partitioned  in some way. I don' t know much about Vista, but I think you should  be able to go into "Disk Management" and have a look at you partitions.

Okay no problem - heading home to try "fdisk -l" now, in the meantime this is what disk management says (no filesystem? hmm...).  The HD in question is "Disk 2".  (Shown at the top with a blank volume label).

[IMG]http://www.gnackattack.com/disk_screen.jpg[/IMG]

---

### Post by gnackattack on 2008-05-24
> **meierfra. said:**
> "fdisk -l"  list all the partition on your hard drive. I just want to see whether your 500GB drive got formated or partitioned  in some way. I don' t know much about Vista, but I think you should  be able to go into "Disk Management" and have a look at you partitions.

Here is the fdisk -l output.

```

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa633edf0

Device Boot         Start         End      Blocks   Id  System
/dev/sdc1               1       60801   488384001    7  HPFS/NTFS

```

Thanks so much for all the help by the way, I really appreciate it.

---

### Post by meierfra. on 2008-05-24
Sorry, fdisk and Disk Management don't seem to reveal anything new. So I suggest "chkdsk" (see post 14)

---

### Post by binary00mind on 2008-05-25
[COLOR="DarkGreen"][/COLOR][LEFT][/LEFT]I see that the thread sparked some interest. First during partitioning or formatting NO Files are Erased.
 One Must understant how it works. It is subject that has so many little things involved together(complexity) that each situation differs.
Every HARD Disk has Master Boot Records (the most important one is the main on PC. Where partition tables are stored. Every Change is recorded there and stays there until it runs out of space (and there is a lot of space)or is overwritten.
 Example. There is little app named "Cute Partition Manager" very small runs from floppy 1.44 or CD iso image. There You can do a lot of things, but can not format partition or disk. Few times I changed partition tables from NTFS to Fat32 and after boot the tree with files was still there.
 If You deleted on purpose or accident (using any partitioning utility}It is a child play to recover All in few seconds.
 During Booting on Linux the partition tables are checked like in fat Fat 1 is compared to Fat 2 if something is not OK, there you have fsch running.
Also the monster portable Hard Drives with 300 or 500 and up. usually are sold as 1 big partiton or maybe top 2.
The first thing any owner should do is to divade the land, before storing data.
Important , Most of these HD comes with NTFS file system. If Any of You install Ubuntu and want to use external Disks and register them to use extended attributes or use the "quite change of ownership" (between root/plugdev and You ), so to speak, You must enter mount points and file system.
When You have Big Land as our friend here, 500 GB and your file system is NTFS, You out of luck, because NTFS is not in the Ubuntu Partitioning installation menu.
You can pick FAT32 but then You change the partition tables thus all your stored data (if any) disappears. this is the case with 7.10. I don not remember about Hardy, because my land was already divaded when I installed Hardy.
Just a note the mount points could be named differently. I found, that using /sdb/sda1 then 2 and 3 etc.are the easiest, to deal with later. You have all partitions in 1 SDB Folder. Important thing also for those with dual OS's. The Hard Drive Count IN MBR. Which is interconected with BIOS readings. IRQ assigments and so on, in computer starts from "0" the external ones start with "1". I readed in few posts a question being asked if NTFS partitions can be used using Ubuntu ?
Yes go to Synaptics Manager You shall find a few packages. That do the trick for You. With root privilages more or less. (the deggree of root privilages depends on few factors, one of them is installing quite a few packages, that grand You those privilages in mounting all types of devices and file systems, without entering password, something like "nosuid" scenario. There was an a advice of using fdisk.
You beetter fully understand what fdisk can do before You go for it. There is a possibility of doing mbr/fdisk out of floppy DOS, but for experienced users. While I Am in this subject. I would like to mention that You can play with your BIOS changing the boot order sequence and put external HD with Ubuntu on it, ahead of SATA and IDE or whatever. Finally Installing Ubuntu Grub, it is important to be as close to #1 As possible. (like the old magic line of 8 GB Limit Line) otherwise failure percentage grows.
I uninstalled Hardy because, despite debconf priority LOW !, IT Refused to install Grub in hd0 out of first primary partition without any other OS present. That I must investigate why. Besides Hardy in my opinion is an a marketing stunt. But that is my opinion and I am happy for others who liked. (Status Quo)
It is alsa a good idea, if You have full trust in your hardware, to divaded Ubuntu into several partitions. The most I had is 8. but that is too much. I think root, var, usr, home, swap and LVM is the best, plus RAID of course if needed. 
The bottom line ! Everything is recoverable. Just the right tools and knowledge.
I Left Windows out of anger. I Did easy over 100 Ubuntu, Kubuntu , Xubuntu installations. In past 6 months. Since I left "MouseSoft" after decades. The best way to learn is the hard way (do not follow my footsteps). But I did tons of reading all over the place. And I have miles to go.
Thanx for reading this.

---

### Post by gnackattack on 2008-05-25
> **binary00mind said:**
> Lots of useful knowledge...

Thanks binary00mind for your informative post. In this case though, it seems as though the partition is perfectly fine, but it has been 'formatted' so that the MFT has been cleared.  Despite all the data still being there (I still haven't put anything onto the HD at all, so it should all still be intact).  At this stage I've basically given up and have decided to just wait until I have access to 500gb of free space to copy all the external HD's files onto, before shifting them back onto the external HD.

I was hoping to avoid that though!  Surely, since there is software out there capable of locating all the files on the HD, there must be one that can then use that information to recreate an MFT for the drive that includes the found files...?

---

### Post by meierfra. on 2008-05-25
Tried "chkdsk" yet? It could be an easy fix.

The MFT is automaticaly backedup on your partition. So if the backups are in good shape, chkdsk should have no problem fixing your MFT

---

### Post by gnackattack on 2008-05-25
> **meierfra. said:**
> Tried "chkdsk" yet? It could be an easy fix.

The MFT is automaticaly backedup on your partition. So if the backups are in good shape, chkdsk should have no problem fixing your MFT

Yep, tried that - thanks.  Unfortunately it looks as though the backup has been messed up as well.  I even tried using a program called "Test Disk" that can also restore the MFT from its backup, but that didn't work either.

---

