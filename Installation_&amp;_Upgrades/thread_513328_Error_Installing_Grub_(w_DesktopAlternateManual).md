---
title: "Error Installing Grub (w/ Desktop/Alternate/Manual)"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2007-07-30
First here is the setup:
1 sata drive 2 partitions
1 IDE drive 3 partitions (+ swap)
XP on sata part. 1
Ubuntu on IDE part. 1
When I isntalled from the desktop CD I received the following error:
Executing grub-install(hd0) failed´
So I tried the alternate cd and received errors there also for grub, so I choose the Lilo boot manager. The problem is that it does not work correctly all of the time (ie - does not recognize my windows install).
I tried installing grub manually:
sudo grub-install hd0
and I get the following error:
The file /boot/grub/stage1 not read correctly.

I haven googled this yet, but any input would be helpful!

---

### Post by MQMike on 2007-07-30
I would try again to re-install GRUB.

First, you need to get a grub prompt (grub>) somehow.  
Your two choices are: (1) Use a rescue disk, like Super Grub Disk, from which you can boot into your OS, or press the “c” key to get a GRUB prompt.  Or, (2) Use your Live Kubuntu CD.  
Let's assume (2) here.  
Put your Live CD in the CD tray, re-boot your PC, startup your Live Kubuntu.  
Now get a terminal and proceed as follows:

Get a GRUB prompt as root by typing sudo grub  (then press Enter), and type the following (press Enter after each command):
grub>  root (hdx,y)          # (hdx,y) is the partition of your "main" Linux OS--SEE NOTE BELOW
grub>  setup (hd0)          # This assumes (hd0) is your “main” booting hard drive MBR (Windows)
grub>  quit
$ exit

Close out all windows.
Re-boot to test it.

NOTE:  
From what you said, Windows was there first, probably on (hd0, 0) – the first hard drive hd0, the first partition (partition 0).  (Note that the bootloader GRB starts numbering drives and partitions from zero).
And then Ubuntu is on the second hard drive, first partition?
If so, the root (hdx, y) would then be root (hd1, 0).

- - - - -

Edit the boot menu (/boot/grub/menu.lst)?

After doing all this, you may still have to edit the boot menu for GRUB, which is contained in Ubuntu at /boot/grub/menu.lst.  (.lst is an “l” as in “list.”)
You must edit it as root, and don’t forget to save your changes when you are done (File-Save, File-Quit).

The part you need to check/edit is the boot menu for Windows, which should look like:

title Windows XP or whatever you wish to call it
rootnoverify (hdx, y)     #I think that would be (hd0, 0), right?
makeactive
chainloader +1

where:
(hdx, y) is your Windows partition.
x is the hard drive number = 0
y is the partition = 0
 (GRUB, the bootloader starts counting from zero.  So hd0 is the first hard drive, hd1 is the second hard drive, etc.;  the first partition is partition 0, the second partition is partition 1, etc.)


For all the details:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

---

### Post by lsutiger on 2007-07-30
Hwne I get into grub and type root(hd1,0) I get the following:
```
       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> root(hd1,0)

Error 27: Unrecognized command

```
I can boot into ubuntu fine by switching the boot drive in bios to the second hard drive. I installed Lilo, but it doesn´t recognize windows all of the time.
Thanx for the quick reply!

---

### Post by merlinus on 2007-07-30
You might try this:

```

sudo grub
find /boot/grub/stage1
root (hdx,x)
setup (hdx)
quit

```Substitute your results for the xes.

-merlin

---

### Post by MQMike on 2007-07-30
There is a space after root:

root   (hd1, 0)

So, root, space, (hd1, space 0)

---

### Post by merlinus on 2007-07-30
> 
So, root, space, (hd1, space 0)


I may be mistaken, but the space between hd1, and 0 is incorrect.

Should be:

(hd1,0)

-merlin

---

### Post by MQMike on 2007-07-30
merlin:   "I may be mistaken, but the space between hd1, and 0 is incorrect.
Should be:
(hd1,0)"

Doesn't matter (I run these almost everyday with the space).  
But that space after the root command is make-or- break.
root(hd1, 0) gives bad command.
root (hd1, 0) will run.

--Mike

---

### Post by merlinus on 2007-07-30
Thanks, Mike, for the info.

-merlin

---

### Post by vanth13 on 2007-07-31
I'm having the same installation problem..and so the installation stops.. and the menu.lst file is empty... I Just don't know how to go on...

---

### Post by lsutiger on 2007-07-31
I am still having a few difficulties here, so I will post info. Here is my fdisk:
```
Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        9038    52114860    f  W95 Ext'd (LBA)
/dev/sda5            2551        9038    52114828+   7  HPFS/NTFS

Disk /dev/hdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        2432    19535008+   7  HPFS/NTFS
/dev/hdc2            2612       10444    62918572+   7  HPFS/NTFS
/dev/hdc3           10445       14593    33326842+   7  HPFS/NTFS
/dev/hdc4            2433        2554      979965   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 4194 MB, 4194303488 bytes
255 heads, 63 sectors/track, 509 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         510     4095968    6  FAT16
Partition 1 has different physical/logical endings:
     phys=(508, 254, 63) logical=(509, 236, 46)

```
I can not find stage1:
```
grub> find /boot/grub/stage1

Error 15: File not found
grub> root (hd1,0)

grub> setup (hd1)

Error 17: Cannot mount selected partition


```
the file stage1 is located at (through nautilus) File System/Boot/Grub/

---

### Post by MQMike on 2007-07-31
Need to find out the boot order of your drives,
What is (hd0)?
Which one is (hd1)?
and (hd2)?

(Note:  GRUB sees your drives the same way BIOS does (and labels them hd0, hd1, etc.; Linux may see and label them differently (as sda, sdb, etc.)

Get a grub prompt, by typing sudo grub at a terminal again, and experiment with the geometry command to see if you can recognize the drives:

grub>  geometry (hd0)
grub> geometry (hd1)
grub> (geometry (hd2)

This will tell you where Windows is (we hope (hd0, 0), and where Linux is (that’s sdb1, right, under fdisk –l?).

It is troubling that it could not find /boot/grub/stage1, because that file normally is located in your Ubuntu root files (sdb1 = (hdx, y)).

---

### Post by lsutiger on 2007-07-31
> **MQMike said:**
> Need to find out the boot order of your drives,
What is (hd0)?
Which one is (hd1)?
and (hd2)?

(Note:  GRUB sees your drives the same way BIOS does (and labels them hd0, hd1, etc.; Linux may see and label them differently (as sda, sdb, etc.)

Get a grub prompt, by typing sudo grub at a terminal again, and experiment with the geometry command to see if you can recognize the drives:

grub>  geometry (hd0)
grub> geometry (hd1)
grub> (geometry (hd2)

This will tell you where Windows is (we hope (hd0, 0), and where Linux is (that’s sdb1, right, under fdisk –l?).

It is troubling that it could not find /boot/grub/stage1, because that file normally is located in your Ubuntu root files (sdb1 = (hdx, y)).
Oh thats easy. When I boot into ubuntu, I have the IDE drive as 1st boot device, the SATA as the second.
I will boot into ubuntu in a sec and do the geometry comand. The sdb1 was my thumb drive that I connected at the time.

OK - Here is the output of grub> geometry
```

grub> geometry (hd0)
drive 0x80: C/H/S = 14593/255/63, The number of sectors = 234441648, /dev/hdc
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 1,  Filesystem type unknown, partition type 0x7
   Partition num: 2,  Filesystem type unknown, partition type 0x7
   Partition num: 3,  Filesystem type unknown, partition type 0x82

grub> geometry (hd1)
drive 0x81: C/H/S = 9039/255/63, The number of sectors = 145226112, /dev/sda
   Partition num: 0,  Filesystem type unknown, partition type 0x7
   Partition num: 4,  Filesystem type unknown, partition type 0x7

```
That means hd0 is the partition where ubuntu is installed ( I have 4 partitions on the drive). 
hd1 is my sata drive with 2 partitions and holds windows on the 1st partition.

---

### Post by MQMike on 2007-07-31
You can try this to re-install GRUB – this comes from my first post on page 1 here.

Get a GRUB prompt as root by typing sudo grub (then press Enter), and type the following (press Enter after each command):
grub> root (hd0, 0)  # that’s where your Ubuntu is, right?
grub> setup (hd0)
grub> quit
$ exit

Close out all windows.
Re-boot to test it.

***This assumes, as you seem to say, that when you turn on your PC, it boots first the hd0 drive containing Ubuntu and Ubuntu is on the first partition of that drive.***
- - - - -

Then when you edit the boot menu, you need to make sure the boot entry for Windows is right:

title Windows XP or whatever you wish to call it
map (hd0)  (hd1)
map (hd1)  (hd0)
rootnoverify (hd1, 0)  # That’s where your XP is, I think
makeactive
chainloader +1

See the How-To link above for any details.
Remember to edit the boot menu (/boot/grub/menu.lst) using sudo and don’t forget to save your edits (File-Save, File-Quit).
In the How-To link, scroll down past Post #1 until you come to Windows on a non-first hard drive; the map commands are explained there.
I have seen this work in other cases, but no guarantees – might take some tweaking.


Comment:  I'm not sure why your output keeps indicating filesystem type unknown, but you are certain Ubuntu and Windows are both there, where you say they are.

---

### Post by lsutiger on 2007-08-01
Yes, thats where they are. I ran gparted just to make sure, and  the hdc1 (dev/hdc1) has the ext3 filesystem. The mountpoint states /,/dev/.static/dev, and it is flagged as boot. 
When I run setup (hd0) I get the error ( after running root (hd0,0):
Error 17: Cannot mount selected partition

Now, I do have lilo installed at the moment as my boot loader. Would that cause a problem?

I am attaching a pic of gparted FYI

---

### Post by MQMike on 2007-08-01
"Now, I do have lilo installed at the moment as my boot loader. Would that cause a problem?"

I've not used LILO, but I would think that you should have just one bootloader going at a time.

---

### Post by MQMike on 2007-08-01
"I ran gparted just to make sure, and the hdc1 (dev/hdc1) has the ext3 filesystem. The mountpoint states /,/dev/.static/dev, and it is flagged as boot."

Hmm . . .back on page 1 where you ran sudo fdisk -l, hdc had the NTFS?

---

### Post by lsutiger on 2007-08-01
> MQMike
I've not used LILO, but I would think that you should have just one bootloader going at a time. 
True. I want to end up with grub because Lilo doesn't work correctly all of the time. But would having lilo prevent me from installing grub?

> Hmm . . .back on page 1 where you ran sudo fdisk -l, hdc had the NTFS?
Thats what it reported...which one is right?? And what if HPFS?
I cut and pasted the output from fdisk.


BTW, thanx for all of your input, everyone!

---

### Post by MQMike on 2007-08-01
"I want to end up with grub because Lilo doesn't work correctly all of the time. But would having lilo prevent me from installing grub?"

Probably not.  I would think LILO, like GRUB, is just a bunch of files stored somewhere (like under /boot or some such place).  When you install GRUB to the MBR, it will overwrite anything else that's there.

---

### Post by MQMike on 2007-08-01
Let’s go with your geometry command, where you concluded:

“That means hd0 is the partition where ubuntu is installed ( I have 4 partitions on the drive). 
hd1 is my sata drive with 2 partitions and holds windows on the 1st partition.”

NTFS is the Windows filesystem.
Your GParted screen shot for hdc doesn’t show any Linux ext2/ext3 partitions.  Where is Ubuntu?
It’s on (hd0), but what partition?  Did you actually install Ubuntu?  &#61514;
Maybe I’m just temporarily lost.

In that post I did above, where it says
“You can try this to re-install GRUB – this comes from my first post on page 1 here.”

. . . That’s the general method we would use here.  Now what we need to do is know where these operating systems are.  Maybe the (hd0, 0) assumption for Ubuntu is not correct?  Why is it on an NTFS partition, which is usually used for Windows?  I don’t know if Ubuntu OS can run on an NTFS partition.  One option would be to re-install Ubuntu on an ext2 or ext3 formatted partition.  Maybe someone else can chime in here about this NTFS formatted Ubuntu partition (which doesn’t look right to me).  

Also you could not find Stage1 (see above post you did.).  Usually, Stage1 will be located in the root files of your Ubuntu OS, /boot/grub/stage1.  It is installed there during the installation of Ubuntu.  It MUST be there!  Or this won’t work.  It must be somewhere, I should say, and (almost) anywhere would work!

Something seems wrong with your installation and the formatting of your Ubuntu partition.

---

### Post by merlinus on 2007-08-01
> 
I don&#8217;t know if Ubuntu OS can run on an NTFS partition. One option would be to re-install Ubuntu on an ext2 or ext3 formatted partition. Maybe someone else can chime in here about this NTFS formatted Ubuntu partition (which doesn&#8217;t look right to me).
You are correct.  Linux will not run on an ntfs or fat partition -- they are for windows.

In fact, I cannot imagine that ubuntu could install into that filesystem.

-merlin

---

### Post by MQMike on 2007-08-01
I don't know if you can tell or not, merlinus, but I can't see where his Ubuntu is.  Everything suggests it is on that hd0, but that's NTFS . . . ?  puzzling . . . If that's true, the only option is to wipe that drive/partitioning, re-format it ext2 or ext3, then re-install Ubuntu, right?

---

### Post by merlinus on 2007-08-01
Should work.  As you know, sometimes biting the bullet and reinstalling saves lots of time and agony.

Unless, of course, one is in love with agita....

;)

-merlin

---

### Post by MQMike on 2007-08-01
Now * you *  are correct.
And I agree.

---

### Post by lsutiger on 2007-08-13
Solved by unhooking the sata drive and reinstalling on the ide drive all by its lonesome. I then hooked the sata back up, edited fstab, and now dual booting. One quick question. How do I get grub to show its menu instead os the countdown? In Edgy, it did this, but in feisty it isn't...But I am pretty sure it has to do with setting up grub/fstab manually vs install taking care of it.
Thanx again for all the input!

---

### Post by MQMike on 2007-08-13
To show the GRUB boot menu after the POST,
edit /boot/grub/menu.lst
by placing a hash mark # in front of hiddenmenu:
# hiddenmenu

(edit /menu.lst as root, then File-Save, File-Quit)

---

