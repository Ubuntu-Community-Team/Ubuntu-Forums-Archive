---
title: "Help accessing hard disk w/out boot loader"
date: 2007-07-22
forum: Installation &amp; Upgrades
---

### Post by kouran on 2007-07-22
Hello. I'm in a really bad situation, please take the time to read. Thanks.

I have two hard disks. I recently reformatted my Windows XP disk and my other hard disk, which had Kubuntu on one partition, and music, video and personal files (100+Gb) on another partition of that disk. Now I know this isn't about support for Windoze, but I cannot access my personal files Windows; it says the disk is not formatted, and I do NOT want to format the disk, I know the data is there because I could see it in Kubuntu.

Now my GRUB loader has buggered up somehow and I can't access Kubuntu to try and move the files out of the partition and into my Windows partition.

I attempted to fix the MBR where GRUB was located, only to screw things even more; I have an empty MBR on the Kubuntu/personal files disk with no boot loader.

So can I get some help with installing GRUB so I can access my files? I really, really would appreciate any help to overcome this, I've got files I've stockpiled over about 5-6 years. Or, does anyone have any other suggestions for me?

Many, many thanks.

PS. I wasn't really sure where to post this thread...

---

### Post by ddrichardson on 2007-07-22
[This howto]("http://www.sorgonet.com/linux/grubrestore/") helped me

---

### Post by Herman on 2007-07-22
Or use [Super Grub Disk]("http://geocities.com/supergrubdisk/"), that can do almost anything with GRUB, it can re-install GRUB for you and it can boot your computer without re-installing GRUB too if you want. It's only a small download and it can work from CD, floppy disk or USB, depending on which kind of file you download. 

Another thing you could think about is rescuing files with a Ubuntu Live CD first maybe, you'll need to mount your file systems to do that. Here's a page about how to mount all kinds of file systems, Windows or Ubuntu, [File Systems and Mounting Page]("http://users.bigpond.net.au/hermanzone/p10.htm").

Once you have a partition mounted with the Live CD, you can copy files to an external USB drive, or you can send them through the LAN network by SSH if you have a LAN set up. Here's a page about SSH networking that might help you with a file rescue, [SSH Network]("http://users.bigpond.net.au/hermanzone/p11.htm").

If you can't do that you can probably use Puppy Linux to rescue your files. Puppy Linux boots from a CD, and loads into the RAM and runs from there. So you can take the Puppy Linux CD out and put in a blank CD whle Puppy Linux is still running. You can use Puppy Linux to copy your files to blank CDs or DVDs. [Puppy Linux Home Page]("http://www.puppylinux.org/user/viewpage.php?page_id=1").

---

### Post by kouran on 2007-07-22
Thanks for the feedback. I'll try some of these tomorrow, bed time for me hehe.

Will let you know if I failed or succeeded.

---

### Post by kouran on 2007-07-23
Nothing works :'(

Super Grub Disk fails when i select GNU/Linux. I get Error 15 - File not found.

I'm almost about to give up hope, short of contacting an expert and being charged an arm and a leg; which I'm nearly willing to do...

Woe is me.

---

### Post by ddrichardson on 2007-07-23
There is another way.

Mounting the root drive, proc and udev and using chroot before reinstalling grub, there is a post [here]("http://ubuntuforums.org/showthread.php?t=224351") that explains it better than I ever could.

Also, error 15 means it can't find the kernel - is it available/corrupt or has super grub disk named it wrong?

---

### Post by Wim Sturkenboom on 2007-07-23
You can boot from the liveCD and copy files using that. And I hope that you will [COLOR="Red"]**make backups**[/COLOR] in the future.
Or hook the disk up in another PC and copy there.

---

### Post by Herman on 2007-07-23
Please post here the output you get when you type 'sudo fdisk -lu' (without the inverted commas), in a terminal when you're running a LiveCD,
```
sudo fdisk -lu
```Also, what do you mean 'nothing works'? What did you try and what happened or didn't happen? Did you try mounting your file systems with the Live CD and could you then see any files, or did you not try that or did you think you mounted your partitions okay but they look empty or  what? :)

Quoted from your first post,
> I have two hard disks. I recently reformatted my Windows XP disk and my other hard disk, which had Kubuntu on one partition, and music, video and personal files (100+Gb) on another partition of that disk.
  Can you explain about what you did there in more detail please?
EDIT: If you really did reformat both of your hard disks then there's still a good chance of recovering your operating systems and all your data with [TestDIsk]("http://www.cgsecurity.org/wiki/TestDisk").


Assuming that's not what you really meant, you should be able to either boot with Super GRUB DIsk or restore your MBR or normally both.

When you use Super GRUB Disk and you  have two or more hard disks you would need  to use the  'Advanced' menu.
'Gnu/Linux has the simple menu which is mainly for single hard disk installs.
Try 'Advanced'-->'Gnu/Linux (Advanced)'--> , and try our some of the options there.
Any of those should work.  In the 'Advanced menus, you'll be asked to choose a hard disk first and then a partition. 
You'll also be given a choice of which hard disk's MBR to restore GRUB to. (Choose your first hard disk, normally).
There are three ways to boot with Super GRUB Disk, one is by your menu.lst file, (boot Gnu/Linux), the other is by symlinks to your kernel and initrd.img, (Boot Gnu/Linux Directly) one of those should work if you have anything there. I don't think there is any chance of getting the names of the symlinks wrong. A third option is chainloading, (Boot Partition of Gnu/Linux), but that will only work if you have a bootloader installed to your partition's first sector, which is not the default in Ubuntu, unless you did that yourself, manually.

Regards, Herman :)

---

### Post by kouran on 2007-07-24
Damn, I should have been MUCH more clear.

I have two physical hard disks. One is split in two partitions: Windows, and another one I use for storage. The other physical disk has a partition I use for storage and a partition I use for Kubuntu.

I tried *sudo fdisk -lu* when I tried mounting the kubuntu partition when i was using the live cd; the only partition that appeared for the latter disk (the one with Kubuntu) was the partition I use for storage, etc. And that partition looked empty.

I'll try the advanced menu in SGL, from memory I don't think there was one there...

@ Herman: I'm from Australia too ^_^

---

### Post by kouran on 2007-07-24
Well, I don't have an 'Advanced' menu item in SGL.

I think I might research that data recovery solution....

---

### Post by Herman on 2007-07-24
>  @ Herman: I'm from Australia too ^_^ Hey, that's great! It's always nice to see more Aussies here. :)

Sometimes, if I can see a copy of the actual output from sudo fdisk -lu myself I can see what's wrong, like maybe a partition doesn't end on a cylinder boundary, or the end of one partition finishes after another one begins, (partition overlap). Other times it doesn't help to see sudo fdisk -lu, but it's worth a try usually. Well, that's okay, I'll just have to go by your description then, > I tried *sudo fdisk -lu* when I tried mounting the kubuntu partition when i was using the live cd; the only partition that appeared for the latter disk (the one with Kubuntu) was the partition I use for storage, etc. And that partition looked empty. Well it sounds like your partitions have been deleted somehow, or your partition table is corrupt. Or you might have some hardware or BIOS problem. It seems strange that both hard disks are having problems at once. I think we should start with your hardware or BIOS.

Try going into your BIOS and taking a good look around in there to see if you can spot any problems. [    Make sure your hard disk is properly detected in your BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Making_sure_your_hard_disk_is_properly").
           Check your system voltages and temperatures and things like that in '[    System Health Check]("http://www.users.bigpond.net.au/hermanzone/p1.htm#System_Health_Check")'.

Have you done any work inside your computer case recently that you can remember? Especially something to do with plugging in drives, IDE cables and moving around any jumper settings?
Is there any way you can try plugging your hard disks into another computer and see if they work okay in another computer? Or in an external USB case? 

If it's really a software problem and not a hardware problem, your hard disks seem to have corrupted partition tables, I would check for hardware problems first though. It's odd that they would both go at once.  [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") is the best software I know of for fixing a corrupted partitiion table.  Here's my page about using TestDisk in case that will help you, **[TestDisk Page]("http://www.users.bigpond.net.au/hermanzone/p21.html").** I'm fairly sure you can install TestDisk in the Ubuntu LiveCD, it will stay there for one session. I recommend TestDisk in [GParted -- LiveCD]("http://gparted.sourceforge.net/"). GParted LiveCD is worth getting and it's only a small download, around 47 Mb I think.

Regards, Herman  :)

---

### Post by kouran on 2007-07-24
Ah damn again, need to be even more clear :P

in sudo fdisk -lu, I see only the partition I used for storage on the disk that included the Kubuntu partition, AND my other physical disk appeared fine.

The BIOS looks tip-top. Haven't fiddled with any of the connections in the case since about 2 years ago. All signs point toward logic error.

Might be blasphemous, but couldn't I run TestDisk in Windoze, just for convenience's sake..?

---

### Post by kouran on 2007-07-24
> **Wim Sturkenboom said:**
> You can boot from the liveCD and copy files using that. And I hope that you will [COLOR="Red"]**make backups**[/COLOR] in the future.
Or hook the disk up in another PC and copy there.

Funny you should mention that. I just got a brand new NAS a last week EXACTLY for situations like this. Don't ask me why I didn't set it up immeadiately.

---

### Post by Herman on 2007-07-25
So here's a summary of what I *think* you *mean*:

SUMMARY:
> I have two hard disks. 
One is split in two partitions: Windows, and a storage (*data partition*).
The other has a storage (*data*) partition and a Kubuntu partition.

Right now I cannot access my personal files in (*from?*) Windows; it says the disk is not formatted, but I know the data is there because I could see it in Kubuntu.

Now my GRUB loader has buggered up somehow and I can't access Kubuntu to try and move the files out of the (*data)* partition and into my Windows partition.
I attempted to fix the MBR where GRUB was located, only to screw things even more; I have an empty MBR on the Kubuntu/personal files (*data)*  disk with no boot loader.

I tried sudo fdisk -lu when I tried mounting the kubuntu partition when i was using the live cd; 
the only partition that appeared for the latter disk (the one with Kubuntu) was the partition I use for (*data)*  storage, etc. And that partition looked empty.Does that look right so far?  :confused:

**1.** So do you mean 
** (a)** your **Windows in works okay** in hard disk number 1, but **you can't access your data partition in disk 1**?
Or do you mean
** (b)** your Windows in disk 1 works but **you can't access the data partition in disc 2** from Windows?
Or do you mean 
** (c) **your Windows works okay but **you can't access any other partitions** from Windows?

Or do you mean 
** (d)** Your **Windows doesn't work** and now your  Kubuntu doesn't either?  :confused:

**(e)** none of the above, (please explain)...

**2.**
And do you mean you had 
** (a) **Windows on hard disk one booting from the MBR of hard disk one, and Kubuntu in hard disk two, booting from the MBR in hard disk two? (So **you're trying to fix the MBR in hard disk 1?**)

Or did you have 
** (b)** Windows in hard disk one, with GRUB installed in MBR of hard disk one, booting both Windows and Kubuntu? (So **you're trying to fix the MBR in hard disk 2**?) :confused:

**(c) **none of the above, (please explain)...


Please keep trying to explain what you mean and this time if you can boot your Live CD and **post the output from sudo fdisk -lu or a screencap** from Gnome Partition Editor here **please**,  and then it will probably be a lot easier to see what your problem(s) is (are) and how to fix it (them). :)

I or someone here can help you when we can see what's wrong and understand what you want. :)

Regards, Herman :)

---

### Post by kouran on 2007-07-26
1 = B

2 = I initially used GRUB on the MBR of disk 2 (the Kubuntu disk) for both OSes. Now the MBR is frelled up. Disk one (the windows and data one) works totally fine at the moment.

But at the moment I'm about to resort to a data recovery option. i plan on imaging a disk backup of disk 2 (in its entirety) and running scandisk and chkdsk etc.

But i'll get fdisk -lu up asap

---

### Post by kouran on 2007-07-26
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
86 heads, 15 sectors/track, 378602 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           0   268435454   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders, total 268435455 sectors
Units = sectors of 1 * 512 = 512 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           0   268435454   134217727+   4  FAT16 <32M

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    91056419    45528178+   7  HPFS/NTFS
/dev/sdb2        91056420   234420479    71682030    f  W95 Ext'd (LBA)
/dev/sdb5        91056483   234420479    71681998+   7  HPFS/NTFS

```

Well. /dev/sdb is my Windows disk. And i can't make heads or tales of /sda; I have no idea what /sda1p1 is. It seems identical to /sda1 and I have no clue why it's FAT16. If i had to take a guess, I would say that's the storage partition. But that doesn't explain why its marked as 'boot'. Either way, where's the other partition?

---

### Post by ddrichardson on 2007-07-26
How did you set these partitions up? It looks as though sda1p1 is a partition within sda1 - which won't work (obviously).

And you're right it can't be FAT16 - that only supported up to 2GB.

---

### Post by kouran on 2007-07-26
I set up the partition I used for storage as FAT32 using windows. I left the rest of the disk untouched until I put Kubuntu on. That's when I set up the partitions for it.

---

### Post by Herman on 2007-07-26
According to that fdisk output you have Windows and an NTFS logical data partition in hard disk number2, not number 1..

You other hard disk looks really wierd, that's the most unusual partition table I have ever seen, that's not a dos type partition table. You won't be able to install GRUB to that.

Tell me, have you run any unusual software at all lately, and have you used any kind of partition editing software in your computer betweeen the time when you installed Kubuntu and the time when you noticed things were not working properly?
I think you have a corrupted partition table in hard disk number1, which is the one you have been calling hard disk 2, the one you say has a data partition and Kubuntu in it.

The only way I know of to fix that is to run TestDisk on it. That might work or maybe not. It could be that you have a hardware problem in that hard disk, and if that's the case then I'm afraid you can kiss goodbye to your data unless you have a lot of money. 

Actually I think you should get professional expert help if that data is very important. Don't touch it at all and take it to an expert and get professional help.
Buy another hard disk and use the new one in your machine and send that hard disk to a proper data recovery specialist if it's valuable data.

That's my opinion anyway.

Regards, Herman
EDIT: Unless you can remember when  you or someone might haveused some kind of partition editing software on it that could be associated with the problem. if it was a software accident then you should be able to fix it with TestDisk.

---

### Post by kouran on 2007-07-26
I have run no partitioning software or anything. All I did was format the Windows disk and reinstalled it.

I'm going to image the damaged disk (so if i screw up i can start again...) and use Acronis or TestDisk.

Does TestDisk repair partition tables? All i want to do is repair the partition enough to get my data out then I'm going to do a complete format. That's assuming it's salvageable...

---

### Post by Herman on 2007-07-27
That's a good idea to image the disk first.

Yes, TestDisk can be used to repair parition tables. [TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")scans the hard disk looking for the start sectors of file systems ( partitions ), and you can choose which ones you want to include in a new partition table based on that information. I have tried TestDisk in practice (test) simulated rescues and for real, and it works well for me, I like it.
TestDisk should work for the type of situation you have, if the partition table was corrupted by a Windows virus maybe, or a bug in a partition editing program, or just plain bad luck. 
But if the problem is caused by a blown circuit or part somewhere in the hard disk's firmware (circuitry) (BIOS) that talks to your motherboard's BIOS, bad sectors or physical damage to the hard disk's surface, then nothing will probably work and it might even make things worse to try.
The decision is up to you.
Another program that comes with TestDisk, called Photorec is supposed to be very good too, I think it recovers the files directly, without bothering with the partition table. I haven't tried that out myself yet.
TestDisk can be installed in Ubuntu (even when running the LiveCD I think, and it's also available in [GParted -- LiveCD]("http://gparted.sourceforge.net/"). Usually GParted lLiveCD has the most up to date software because it is released very few weeks instead of every six months, and it's a smaller, more specialized distro so it's probably easier for them to keep things up to date. You might like one of Larry T's 'Clonzeilla' versions of GParted, that can clone an entire hard disk for you, if you want to image your disk before you begin data recovery operations. I haven't tried [clonezilla]("http://clonezilla.sourceforge.net/") myself yet, but I will sometime. Here's a review on GParted/Clonezilla, [Manage partitions and disks with GParted-Clonezilla live CD]("http://www.linux.com/feature/115208")

Here's a link to [The Starman's Realm.]("http://www.geocities.com/thestarman3/index.html"), which is an extremely interesting site. The Starman has a  great web page on that site about data recovery you might like, [An Introduction to Data Recovery]("http://www.geocities.com/thestarman3/asm/mbr/DataRecovery.htm"). I think it's all explained there very nicely. 

I hope you can get your data back, 
Regards, Herman

---

### Post by kouran on 2007-07-27
Wow, thank's for all the info. I'll get to doing things this weekend. I'll keep you posted on how it goes :)

---

### Post by ddrichardson on 2007-07-27
[System Recue CD]("http://www.sysresccd.org/Download") might be more helpful - its a Live CD. It can repair the MBR and image disks using the very straight forward PartImage.

---

### Post by kouran on 2007-08-01
Oh no. TestDisk doesn't detect the damaged partition. It detects my Linux partition, but that's not what I want. I just want the other partion :(

---

### Post by Wim Sturkenboom on 2007-08-03
> **kouran said:**
> ```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 250.0 GB, 250059350016 bytes
86 heads, 15 sectors/track, 378602 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           0   268435454   134217727+   4  FAT16 <32M

Disk /dev/sda1: 137.4 GB, 137438952960 bytes
86 heads, 15 sectors/track, 208089 cylinders, total 268435455 sectors
Units = sectors of 1 * 512 = 512 bytes

     Device Boot      Start         End      Blocks   Id  System
/dev/sda1p1   *           0   268435454   134217727+   4  FAT16 <32M

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    91056419    45528178+   7  HPFS/NTFS
/dev/sdb2        91056420   234420479    71682030    f  W95 Ext'd (LBA)
/dev/sdb5        91056483   234420479    71681998+   7  HPFS/NTFS

```

Well. /dev/sdb is my Windows disk. And i can't make heads or tales of /sda; I have no idea what /sda1p1 is. It seems identical to /sda1 and I have no clue why it's FAT16. If i had to take a guess, I would say that's the storage partition. But that doesn't explain why its marked as 'boot'. Either way, where's the other partition?Only an explanation:
Somewhere along the line you have fdisked /dev/sda1 instead of /dev/sda. That's why you have /dev/sda1p1.

---

