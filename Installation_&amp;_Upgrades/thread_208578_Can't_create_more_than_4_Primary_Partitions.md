---
title: "Can't create more than 4 Primary Partitions?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by lukeblack on 2006-07-03
Hello.

I have CentOS, Windows XP, Linux Swap and a Boot partition isntalled on my current harddrive. When I try and create a new one for Ubuntu, the computer tells me that I have reached the limit (4) of primary partitions, and I can't create a new one. Is there any way to get around this?

Thankyou,
Luke

---

### Post by tonyr on 2006-07-03
For some reason, four primary partitions is the limit.  Thee way to get around it is to make
one of the primary partitions an Extended partition,  and create Logical partitions
inside the Extended partition.

EDIT:  Learn about partitioning [here]("http://www.tldp.org/HOWTO/Partition/").
Read about partition planning [here]("http://www.psychocats.net/ubuntu/partitioning.html").

---

### Post by lukeblack on 2006-07-03
I see. So would it be possible to:

remove my swap partition
create an extended partition in it's place
create a swap partition within the extended partition
create an ext3 partition within the extended partition

---

### Post by yabbadabbadont on 2006-07-03
Yes, but the problem is that the extended partion you create would only be the same size as the swap partition that it replaces.

Edit: actually, if the swap partition is physically last on the disk and there is free space after it, then you could make the extended partition larger.

---

### Post by tonyr on 2006-07-03
...and if you are uncertain, dump the partition table (as linux root, **fdisk -l**) and
post it here.  (That's ELL, not EYE)

---

### Post by lukeblack on 2006-07-03
Thanks guys, it works (even if it is a bit messy :D)

---

### Post by simul on 2006-07-03
Hi everyone,
I have almost the same question as lukeblack. Please find below my partition table as tonyr sugested.  My qeustion is if I can create the forth primary partition and then create within that partition a swap partition , a linux ext3 partition and maybe a /home partition

thank you,

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131   de  Dell Utility
/dev/sda2   *           6       18846   151340332+   7  HPFS/NTFS
/dev/sda3           18847       19452     4867695   db  CP/M / CTOS / ...
ubuntu@ubuntu:~$

---

### Post by tonyr on 2006-07-03
The partitions on your disk currently take up all the space, so there is no room
left over to make a new partition.  You would have to do some major rearranging,
which is not a simple task.

---

### Post by simul on 2006-07-04
[QUOTE=tonyr]The partitions on your disk currently take up all the space, so there is no room
left over to make a new partition.  You would have to do some major rearranging,
which is not a simple task.[/QUOTE]
Are you serious man?  I have to make this happen so can you please tell me what can I do. do you have any idea what is that /dev/sda3 ?  Do you think I can delete it ?

thank you anyway,
simul

---

### Post by yabbadabbadont on 2006-07-04
Well, only you can truly answer that question as you are the only one who can see the machine and it's contents...   :D

That last partition appears to be about 4GB in size.  Do you have a drive that size listed in Winblows?  Do you have any special OS's other than Windows?  Do you have any unusual or special software installed in Windows or perhaps by Dell?

All we can do is pretty much just guess.

---

### Post by tonyr on 2006-07-04
There is actually another way.  You can shrink the NTFS partition and add the extended
partition in the freed up space.  The most reliable way I have heard about to do this
is to download a CD iso image from [SystemRescueCD]("http://www.sysresccd.org/Main_Page"), burn it onto 
a CD, boot it and use one of the partitioning tools on there to shrink the NTFS partition.  
I've never done it, but there are other threads in these forums about it.

---

### Post by simul on 2006-07-04
thanks .
I have a new dell xps 200.
I have no other OS beside my windows XP (Media Center Edition). 
But I'm now realising that since I have "Dell 13 in 1 Media Card Reader", the last partition should be the removable media disks. I see in windows explorer something like this:

Local disk (C:)
DVD-RW Drive (D:)
Removable  Disk (E:)
Removable  Disk (F:)
Removable  Disk (G:)
Removable  Disk (H:)

Anybody can help me about this? Cant move around these fricking partitions.  Why my middle partiotion should be locked ? cant  I resize it so that I can have some space to create another partition ?

I will appreciate any help because as you may have guessed already, I have no idea about partitioning and such...  from the other side I MUST do a dual-boot win-xp / ubuntu.  That was even the reason I bought this computer !!!!

thanks
simul

---

### Post by flarkit on 2006-07-04
Apologies if I may have missed something, ... *(edit: deleted off-topic bits. sorry!)*

**edit:**
[quote=simul]Anybody can help me about this? Cant move around these fricking partitions. Why my middle partiotion should be locked ? cant I resize it so that I can have some space to create another partition ?[/quote]

OK...

If your C: is using most of the drive, then you are faced with quite a problem. There are applications which can resize an existing partition, such as PartitionMagic and possibly even Linux's GPartED. You would need to fully defragment the C: (I don't trust XP's defrag tool to pack all the data together properly), then use one of those utilities to create new partitions. I'm not too sure if they'll allow you to create an extended partition though.

Simply-put, I'd say back up everything of value on your C:, then delete the partition, start afresh with a new partition scheme (1 primary for XP and an extended partition containing a bunch of logical ones for your data and Linux, etc). Then install XP, Linux, etc and restore your data. Quite a daunting operation...

Lastly, do remember that you can rename your drive-letters in XP, so that the DVDRW and the card-reader are at the end of the alphabet. I've developed the habit of immediately assigning my optical drives (DVD, CD, etc) to X, Y and Z. Then the removable ones go downwards from W. That way, your hard-disks and their partitions have more freedom.

---

### Post by tonyr on 2006-07-04
[This]("http://dannyman.toldme.com/2005/10/20/shrink-ntfs-knoppix/")  article says that the Knoppix LiveCD has **QtParted**, one of the partitioning tools on the
CD I mentioned before, and describes how it was used to shrink the NTFS partition.

---

### Post by tonyr on 2006-07-04
[QUOTE=flarkit]Apologies if I may have missed something, but **why** would one want more than 1 primary partition + 1 extended partition (containing N logical partitions)?
\\:D/[/QUOTE]

Off topic.  This thread is about solving a particular problem from a given starting point.

---

### Post by tonyr on 2006-07-04
...BUT...
If this is a new machine, and the Windows installation is relatively unused, you might be 
able to redo the partitions, not worrying about what happens to the NTFS partition, reinstall
Windows in the new smaller NTFS partition,  create an extended partition in the freed up
space as I described before with one ore more Linux partitions and a swap partition.

You need to decide which way you want to go, and let us know.  Someone here will
help guide you.

---

### Post by simul on 2006-07-04
tonyr, I really appreciate your help...
I'm downloading SystemRescueCD.  Yes, the computer is new, but Im hoping to do the shrinking and all using SystemRescueCD first and then try the second method (resinstalling windows)

simul

---

### Post by tonyr on 2006-07-04
Good luck.  I'm signing off for  a few hours.  It's bedtime here on the US West Coast.

---

### Post by simul on 2006-07-04
well, I downloaded  SystemRescueCD and boot-ed the system with it. It seems like I could shrink the NTFS partition and make all my linux partition. I didnt commit any change yet ..
Can somebody confirm if I can install ubuntu in an extended partition ?
I read somewhere that it should be primary partition in order to boot up from that partition . Is this true?
thanks,
simul

---

### Post by tonyr on 2006-07-05
It can be a logical partition (inside an extended partition) without any problem.

Here's my layout:
```

/dev/hda1    Dell Utility (primary: Dell made this one)
/dev/hda2    HPFS/NTFS (primary: Windows XP)
/dev/hda3    Linux (primary: Mandriva 2006)
/dev/hda4    Extended (includes all of the next partitions)
/dev/hda5    Linux (logical: Kubuntu 6.0.6)
/dev/hda6    Linux swap / Solaris (logical)
/dev/hda7    Linux (logical: Ubuntu 6.0.6)
/dev/hda8    W95 FAT32 (LBA) (logical: WXP and Linux shared/common)
/dev/hda9    Linux (logical: Ubuntu data)

```

I boot Windows XP, Mandriva 2006, Ubuntu 6.0.6 and Kubuntu 6.0.6.  I'm in
Ubuntu 6.0.6 right now.

---

### Post by simul on 2006-07-05
I'm finally writing this post from ubuntu  !!!!!
Whith my previous computers, once in a while I used to give a try to make a dual boot system (winXP- linux...) but never succeeded. 
Anyway a short story about my ubuntu installation:

At first I had a partition table looking like this:
- some MB of FAT16 (dell utilities)
- 144.33 GB NTFS (windows installation)
- 5GB FAT32 (removable media)

I used systemRescueCD to change the partition.I first resized the windows partition (made it 40 GB)
then created an extended partition. Inside the extended partition I created the following logical partitions
70 GB of FAT32 for shared data between ubuntu and windows
15 GB of ext3 for ubuntu installation
15 GB of ext3 for ubuntu /home
4.3 GB of swap

The result looks something like the following
  
The partitioning process took just a few minutes.
Then I start to install ubuntu. Everything went as expected.  Just one small thing here. When the installation process started (step 7 i think) I got an message like "checking the file system on FAT16 .. found an uncorrected error".
I had 2 options "go back to check" and "continue". As you may guess , i just continued.  The rest of the process was just normal. It took no more than 10-15 minutes (less I think)

Everything is working like a charm 

thank you for helping me (especially tonyr)

---

### Post by rcarring on 2006-07-06
If you are running a desktop pc with room for another hard disk drive, the simplest way is to add the new drive as slave to the master hard drive and then use the new drive for all your Linux needs, thus allowing you to keep the original hard disks for Windows alone.

Alternatively, backup the data you need from Windows, swap out the hard disk drive for a new one, install Linux, and restore the Windows data.

Hard disks are relatively cheap compared to buying a recovery service due to a failed re-partitioning job.(Power cuts, error selecting partition)

---

