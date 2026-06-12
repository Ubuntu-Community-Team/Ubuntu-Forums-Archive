---
title: "Where's my other partition?"
date: 2005-02-10
forum: Installation &amp; Upgrades
---

### Post by Jonathan_ on 2005-02-10
I installed ubuntu today after using windows previously. I had a 'C' and a 'D' drive. 20gb and 180gb (partitioned from one hard drive)

While setting up ubuntu i selected to delete and create a partition on the 20gb partition 'C' but left 'D' alone. Now I am in ubuntu I cannot see any way to access my old 'D' drive. Any suggestions?

EDIT:
By looking around I can see the partition I want to access - sda5 in the 'dev' folder, but there is a cross by it and it doesnt let me access it. I get the following error:

couldn't display "dev/sda5"
there was an error launching the application

---

### Post by FLeiXiuS on 2005-02-10
Define the drive location of 'C' and 'D'.  If its windows, windows will keep it as a 'C' drive regardless.  It loves its boot patterns so let them be.  If its not windows, 

```

fdisk -l

```

Run the command above to give you an indepth conclusion about your drives.

You may paste it here, i'd take a look at it.  But please on your next post give more details about the partitions.

---

### Post by Jonathan_ on 2005-02-10
Im new to Linux, so im sorry I cant be of much help with the information I give because im not sure which information you want. I ran the command you gave and I get the following:

jonathan@Jonathan:~ $ fdisk -l
Cannot open /dev/sda
jonathan@Jonathan:~ $
jonathan@Jonathan:~ $

does that mean anything to you?

---

### Post by ikletti on 2005-02-10
> I installed ubuntu today after using windows previously. I had a 'C' and a 'D' drive. 20gb and 180gb (partitioned from one hard drive)
So you have one 200GB hard disc, right?

> 
While setting up ubuntu i selected to delete and create a partition on the 20gb partition 'C' but left 'D' alone. Now I am in ubuntu I cannot see any way to access my old 'D' drive. Any suggestions?

I guess that 'D' is the second partition on your hard drive, so you might try adding the following to your configuration in /etc/fstab (all in one line):

```
/dev/hda2               /media/data             vfat            defaults  0  0
```
You also have to create a directory 'data' in /media. With this, you should be able to mount the partition as root with

[INDENT]$sudo mount /media/data[/INDENT]

If this basic configuration is working, we afterwards can configure the partition so that it is writeable as a user, too.

Ingo.

EDIT:
I just saw your edit: Is your harddrive a SCSI drive or IDE?
If it's IDE, try changing /dev/hda2 to /dev/hda5 if the first attempt should fail.

---

### Post by Jonathan_ on 2005-02-10
Yes its one 200gb hard disc.

I can open /etc/fstab but I cannot edit it, It will not let me type anything into it, its as though it is locked.

---

### Post by ikletti on 2005-02-10
Try "sudo whatever_your_editor_is" to get to get write acces to the file.
Inside GNOME, press ALT + F2 and enter "sudo gedit" to launch the text editor with write acces to /etc/fstab.

Ingo.

---

### Post by Jonathan_ on 2005-02-10
Thanks alot, that works. Because im a newbie here I dont want to do something stupidly wrong. So here is the text inside etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

The line you say to add in, do i add it at the bottom or in order (sda1, sda5, sda6) I think sda6 is a very small partition (windows used it for something not sure what) and sda5 is the partition I want to access.

---

### Post by ikletti on 2005-02-10
[QUOTE=Jonathan Steel]
The line you say to add in, do i add it at the bottom or in order (sda1, sda5, sda6) I think sda6 is a very small partition (windows used it for something not sure what) and sda5 is the partition I want to access.[/QUOTE]
I haven't yet noticed that a special order is required, but it helps in finding things later, even in a small config file :wink: 

So you might want to try to add the following:

[INDENT]/dev/sda5  /media/data   auto   defaults   0 0[/INDENT]

in between /dev/sda1 and /dev/sda6. What confuses me is: How do you know it's sda5? And something else: How big is sda6? If it's used as /home (that's where the user's folders are put and where most programs store user specific configuration), you might run out of space rather soon.

Could you try "sudo fdisk -l"? That might give an idea about the file system on sda5 and what specific options to use for mounting it for user write access.

Ingo.

---

### Post by Jonathan_ on 2005-02-10
Ok here is what I get with 'sudo fdisk -l'

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+  83  Linux
/dev/sda2            2551       24321   174875557+   f  W95 Ext'd (LBA)
/dev/sda5            2551       24320   174867493+   7  HPFS/NTFS
/dev/sda6           24321       24321        8001   83  Linux

I know its sda5 because I saw the names for the partitions when partitioning them in the install of ubuntu... but I could be wrong, but im pretty sure.

EDIT:
adding that line seemed to do nothing :(

---

### Post by ikletti on 2005-02-10
[QUOTE=Jonathan Steel]Ok here is what I get with 'sudo fdisk -l'

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2550    20482843+  83  Linux
/dev/sda2            2551       24321   174875557+   f  W95 Ext'd (LBA)
/dev/sda5            2551       24320   174867493+   7  HPFS/NTFS
/dev/sda6           24321       24321        8001   83  Linux

I know its sda5 because I saw the names for the partitions when partitioning them in the install of ubuntu... but I could be wrong, but im pretty sure.

EDIT:
adding that line seemed to do nothing :([/QUOTE]

Houston, we have a problem.

Your data partition is sda5, that's fine.

BUT: It's NTFS and thanks to Microsoft's 'we won't let you play with us' strategy, there's no decent documentation for NTFS available and the Linux community so far was not able to reverse engineer the file system to a level where you would trust the NTFS driver not to mess up your data on a write access  :? 
At this stage, only read access is stable.

But back to your mounting problem:
You can change the fstab entry to:

[INDENT]/dev/sda5 /media/data ntfs defaults 0 0[/INDENT] 

Did you create a directory 'data' in /media? If so, you should open a terminal window and enter:
[INDENT]sudo mount /media/data[/INDENT]
If you get an error message, please post it. If nothing else happens, try opening the /media/data directory (still in the terminal):
[INDENT]cd /media/data[/INDENT]
and then
[INDENT]ls[/INDENT]

That should show you the contents of the main directory on sda5.

As an alternative, go to 'Computer > Drives'. If the directory does not show up there, select 'Computer > Drives' anyway, then press CTRL + L and enter /media/data manually.

Ingo.

---

### Post by Jonathan_ on 2005-02-10
Ok so basically would it be easier to reinstall windows, then copy my data to another computer, then clear all the partitions on this pc and copy the data back over after putting linux back on? Thats not a problem and I wouldnt mind doing that.

A quick question though, how should I partition my hard drive? I noticed there are two types of partition you can create, one was primary? I think, and I cant remember the other one. Also different partitions are used for different things, am I right? Im not quite sure because im new to linux so if you could give any tips on how I should partition a 200gb hard drive, that would be appreciated! Thanks

---

### Post by Buffalo Soldier on 2005-02-10
[QUOTE=Jonathan Steel]Thanks alot, that works. Because im a newbie here I dont want to do something stupidly wrong. So here is the text inside etc/fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda6       /home           ext3    defaults        0       2
/dev/hda        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

The line you say to add in, do i add it at the bottom or in order (sda1, sda5, sda6) I think sda6 is a very small partition (windows used it for something not sure what) and sda5 is the partition I want to access.[/QUOTE]

Your **/home** folder is mounted at your **/dev/sda6** partition. Ubuntu/Linux uses this partition and not windows. **/home** folder in Linux equals to C:\Documents and Settings\ folder in Windows.

---

### Post by giaco on 2005-03-23
hi everyone, sorry to jump in this way, but I have exactly the same problem & I am a real newbie to linux in generale, let alone ubuntu (if you know what I mean   :lol: ). 
I installed ubuntu on my laptop, dual boot with win XP ok but ubuntu won't let me see my other 2 FAT32 windows partitions   :-k (they should be hda1 and hda5, or at least thta's the way they were called by a previous knoppix installation and in the ubuntu installation process). I tried to get to /etc/fstab as suggested, but as I said I'm a real newbie, so I failed.  
I would really appreciate if someone could give some help with this
thanks a lot 
g.

---

### Post by giaco on 2005-03-23
[QUOTE=Jonathan_]Ok so basically would it be easier to reinstall windows, then copy my data to another computer, then clear all the partitions on this pc and copy the data back over after putting linux back on? Thats not a problem and I wouldnt mind doing that.

you do not need to reinstall windows! you can convert NTFS in FAT without losing data. I think windows can do it itself somehow, and I am sure that there are applications like Partition Magic that do that without any problem (I would back up everthing before doing it, of course)


A quick question though, how should I partition my hard drive? I noticed there are two types of partition you can create, one was primary? I think, and I cant remember the other one. Also different partitions are used for different things, am I right? Im not quite sure because im new to linux so if you could give any tips on how I should partition a 200gb hard drive, that would be appreciated! Thanks[/QUOTE]

the primary partitions are for operating systems, they are the ones that can be booted, so to speak. the logical partitions are basically for data, or at least that's what I always used them for. While  you can have as many logical partitions as you want, you are not allowed to have more than... well, don't really remember... primary ones, but for sure enough for a dual boot system.
hope I could help
g.

---

