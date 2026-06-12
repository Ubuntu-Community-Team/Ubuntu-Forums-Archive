---
title: "Dual Boot XP &amp; Ubuntu 10 - Can't read from Windows partitions"
date: 2010-05-19
forum: Installation &amp; Upgrades
---

### Post by jeff92677 on 2010-05-19
I am editing this post to save people time and  effort.
This is one of those "Pilot Error" issues or faulty readout issue, not sure which.

It turns out that when I saved a document in PDF format to my NTFS Drive (the one I want to share between Windows XP and Ubuntu 10) the .PDF file extension was missing.
What caused real confusion

1.  Ubuntu identified the files as a PDF document (even though the file extension was not there)
2.  When trying to access it by double clicking it, the message was "Unable to open document, Permission Denied"

The problem was not permissions, and it was not a PDF file according to the default Document Viewer, but it WAS a PDF file according to the directory listing.
The permissions message really had nothing to do with the problem, and identifying the file as a PDF document when it didn't have an extension, was another problem.

What SHOULD have happened is a file without an extension should not be identified as a PDF file
  or
If Ubuntu says it's a PDF file, and I double click it, why is the message "Permission Denied" ?? How about "No File Extension" or something like that?


Read the following if you want to see what my problem WAS before I just appended ,PDF to the filename, and now it works fine.

Thanks to those who tried to help.

On the positive side, installing XP first, then setting aside a large chunk of space for a shared NTFS drive, and THEN installing Ubuntu in the free space works fine.

-------------------------------------------

I installed a new 320 GB drive on laptop.

Installed Win XP in 32 GB
Set aside 250 GB for another Windows partition using MANAGE and formatted D: as an NTFS drive

Then successfully Installed ubuntu 10 into remaining unused space.

Problem: Ubuntu cannot access files from D: (NTFS Windows) partition. but it can WRITE files without problems, and create directories, just not read them.

Have set properties of the Windows drive to shared, still nada.

Any trick I'm missing? If I plug in an external USB drive, Ubuntu can read/write to it easily, it just can't read from the 250 GB partition formatted in Windows XP that I wanted to share between operating systems.

Thanks

jeff

---

### Post by SlidingHorn on 2010-05-19
If you're looking to mount your windows partition from ubuntu, open a terminal, and run:

```
sudo fdisk -l
```

Find your windows partition and enter the following:

```
sudo mount -t ntfs -o nls=utf8,umask=0222 <your/windows/partition*> /media/c
```

If you choose to unmount, do:

```
sudo umount /media/c
```

This will allow you to access your windows partition on ubuntu...I don't really know how to do it the other way around, but I'm sure someone else will be able to help

---

### Post by Cavsfan on 2010-05-19
I dual boot Lucid Lynx and windows 7 and every time I messed with the windows files, it (windows) went nuts.
I had to do a clean install of Win 7 as a result. I am not all that experienced with accessing windows files from 
Ubuntu but, after that happened I don't do it anymore. I move stuff from Windows to a USB drive and then access 
it from Ubuntu. And vice versa.  Windows has a bunch of processes that it manages when files are accessed by it and 
when Ubuntu deleted one or created one, Windows didn't know what happened and windows "likes" being in control of it's files.

---

### Post by wilee-nilee on 2010-05-19
> **Cavsfan said:**
> I dual boot Lucid Lynx and windows 7 and every time I messed with the windows files, it (windows) went nuts.
I had to do a clean install of Win 7 as a result. I am not all that experienced with accessing windows files from 
Ubuntu but, after that happened I don't do it anymore. I move stuff from Windows to a USB drive and then access 
it from Ubuntu. And vice versa.  Windows has a bunch of processes that it manages when files are accessed by it and 
when Ubuntu deleted one or created one, Windows didn't know what happened and windows "likes" being in control of it's files.

Your experience makes no sense, you must have done more then add or remove documents or videos....etc. There are no problems between the operating systems unless you mess with the actual operating system. If you had a virus and you were trying to remove then yes, there could be problems, if the virus had gotten control over key systems.

---

### Post by KinKiac on 2010-05-19
Ive never seen an issue like this, or windows "freak" out because i changed filers with ubuntu, especially when those files are on a separate storage drive.  Ive always had my windows OS partition, ubuntu OS partition and then 2 100 gig storage partitions and have read write and everything on all drives and Ive never had a problem regardless of what OS i was using.  
As for the OP, is it possible that your ubuntu may have taken away your read permissions for the mounted NTFS drive?  Im not sure if that is even possible for a non-system drive but it does sound like that is what happened.

---

### Post by Cavsfan on 2010-05-19
> **wilee-nilee said:**
> Your experience makes no sense, you must have done more then add or remove documents or videos....etc. There are no problems between the operating systems unless you mess with the actual operating system. If you had a virus and you were trying to remove then yes, there could be problems, if the virus had gotten control over key systems.

I didn't mess with the operating system. In windows there is a user journal file ($[I]usrjrnl) that even XP uses and it is updated 
every time windows adds, changes, deletes any file. If files are changed in Ubuntu this file gets out of wack and  there is pretty 
much nothing you can do. Except re-install windows.  I been there once and I learned from it and decided not to touch my 
windows partition through Ubuntu. It was a major pain in the you know what...

I do not like doing unnecessary clean installs...
[/I]

---

### Post by Cavsfan on 2010-05-19
I have a 1TB USB drive I put files on when I need to do something with them on the other OS.

---

### Post by Cavsfan on 2010-05-19
I will say that you _should_ be able to access the windows partition, but at the same time I am saying why would you want to. 
If you want to view a file, that should be OK, but if you add, change or delete a file, you will slowly notice that "something 
is not quite right" with your XP OS. It will be subtle, but strange things will begin to happen and before you know it, you will be 
doing a re-installation of your windows XP OS.

I know a lot more about windows xp, vista and 7 than I do about Ubuntu. And I am just trying to get you to avoid the same mistake I made.

---

### Post by KinKiac on 2010-05-19
> **Cavsfan said:**
> I will say that you _should_ be able to access the windows partition, but at the same time I am saying why would you want to. 
If you want to view a file, that should be OK, but if you add, change or delete a file, you will slowly notice that "something 
is not quite right" with your XP OS. It will be subtle, but strange things will begin to happen and before you know it, you will be 
doing a re-installation of your windows XP OS.

I know a lot more about windows xp, vista and 7 than I do about Ubuntu. And I am just trying to get you to avoid the same mistake I made.

The problem you are experiencing sounds just like how windows normally acts.  Little things start to go over time and next thing you know you need to re-install or your windows is slow as molasses.  But what you are explaining still doesnt make sense unless you are editing your my documents folder in windows and even still wtf does windows do when a file becomes corrupt?  If editing a file from another OS has this effect so would a file becoming corrupt, windows would just see it as a change that it didnt perform.  Also, are you serious?  windows is actually keeping a journal of EVERY file change within EVERY windows partition?  No wonder it gets so damn slow after 6 months.

---

### Post by darkod on 2010-05-19
> **Cavsfan said:**
> I dual boot Lucid Lynx and windows 7 and every time I messed with the windows files, it (windows) went nuts.
I had to do a clean install of Win 7 as a result. I am not all that experienced with accessing windows files from 
Ubuntu but, after that happened I don't do it anymore. I move stuff from Windows to a USB drive and then access 
it from Ubuntu. And vice versa.  Windows has a bunch of processes that it manages when files are accessed by it and 
when Ubuntu deleted one or created one, Windows didn't know what happened and windows "likes" being in control of it's files.

I am dual booting win7 and Lucid (until a week ago it was Karmic) and have a separate ntfs data partition as the OP. Although I don't swap files between the OSs very often, recently I had created documents in Open Office in Lucid and then opened them in Open Office in win7 without any issues.

Also, photos downloaded from my digital camera in Lucid were then copied as a whole folder in win7, again, no issues.

I wouldn't say it's a rule that you will have problems. Maybe an exception...

As for the OP: What is MANAGE? Some piece of software that you used to create the ntfs partition? If XP reads it fine, and if you can, move all data from it on external hdd, then boot ubuntu and use Gparted to format it again as ntfs (make sure you get the CORRECT ONE!!!). Then put the data back.

See if ubuntu will access it as per your expectations after that.

---

### Post by jeff92677 on 2010-05-20
[QUOTE=SlidingHorn;9327960]If you're looking to mount your windows partition from ubuntu, open a terminal, and run:

```
sudo fdisk -l
```

Find your windows partition and enter the following:

```
sudo mount -t ntfs -o nls=utf8,umask=0222 <your/windows/partition*> /media/c
```

---------------

Here are the results (still cannot read from the NTFS drive, but can write, create directories, etc.)

jeff@jeff-M70:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34183418

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4177    33551721    7  HPFS/NTFS
/dev/sda2            4178        5482    10482412+   7  HPFS/NTFS
/dev/sda3            5483       30978   204796620    7  HPFS/NTFS
/dev/sda4           30979       38914    63739905    5  Extended
/dev/sda5           30979       38584    61093888   83  Linux
/dev/sda6           38584       38914     2644992   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x63202ec3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS

----------- I WANT THE 204 GB partition, /dev/sda3 ---------------
I copied, pasted in your command and put in the /dev/sda3

jeff@jeff-M70:~$ **sudo mount -t ntfs -o nls-usudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda3 /media/c **

Usage: mount -V  [/B]               : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
jeff@jeff-M70:~$

---

### Post by SlidingHorn on 2010-05-20
> **jeff92677 said:**
> 

jeff@jeff-M70:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x34183418

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4177    33551721    7  HPFS/NTFS
/dev/sda2            4178        5482    10482412+   7  HPFS/NTFS
/dev/sda3            5483       30978   204796620    7  HPFS/NTFS
/dev/sda4           30979       38914    63739905    5  Extended
/dev/sda5           30979       38584    61093888   83  Linux
/dev/sda6           38584       38914     2644992   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x63202ec3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS

----------- I WANT THE 204 GB partition, /dev/sda3 ---------------
I copied, pasted in your command and put in the /dev/sda3

jeff@jeff-M70:~$ **sudo mount -t ntfs -o nls-u**sudo mount -t ntfs -o nls=utf8,umask=0222 /dev/sda3 /media/c

Usage: mount -V  [/B]               : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
jeff@jeff-M70:~$

Is the command you posted exactly as you typed it in your terminal?  if so, you had part of another command in front of what I suggested.  (See: the bold part)

Looks like you started to type out the command and then decided to copy & paste halfway through.

---

### Post by Cavsfan on 2010-05-20
> **KinKiac said:**
> The problem you are experiencing sounds just like how windows normally acts.  Little things start to go over time and next thing you know you need to re-install or your windows is slow as molasses.  But what you are explaining still doesnt make sense unless you are editing your my documents folder in windows and even still wtf does windows do when a file becomes corrupt?  If editing a file from another OS has this effect so would a file becoming corrupt, windows would just see it as a change that it didnt perform.  Also, are you serious?  windows is actually keeping a journal of EVERY file change within EVERY windows partition?  No wonder it gets so damn slow after 6 months.

I added files to my W7 partition and also deleted them from Ubuntu and the "issues" that followed can only be chalked up to that fact. 
It was very subtle at first and I did not notice anything was wrong at all for a long time, but then my auto backup quit working.
W7 comes with an auto backup setup and I was backing up to my 1TB USB drive and then one day it would go for over an hour
and give this erroneous error that occurred on Vista, but the solution for that problem would not correct my W7 problem. 
I got on a W7 forum and had some real Windows geniuses working on a solution for me.
We tried for about a week because I refused to accept a clean install was the only answer.
But in the end I was forced to give up and perform a clean install. :mad:
I mean we tried everything under the sun for a week! Then it dawned on me that I had been messing with W7 files while in Ubuntu. 
The W7 guys didn't know anything about Ubuntu, but agreed that what I did could cause the problem. 
I had a box with XP Pro on it for about 10 years and NEVER had to do a clean install, but I never dual booted Ubuntu either.
You can do what every you want, I am just trying to save you from what I went through less than a year ago.
I know this forum is not for windows but if you want to learn about $*usrjrnl you will find that yes it does kee*p track of every file.
And windows does like to be exclusively in control of it's files.

> **darkod said:**
> I am dual booting win7 and Lucid (until a week ago it was Karmic) and have a separate ntfs data partition as the OP. Although I don't swap files between the OSs very often, recently I had created documents in Open Office in Lucid and then opened them in Open Office in win7 without any issues.

Also, photos downloaded from my digital camera in Lucid were then copied as a whole folder in win7, again, no issues.

I wouldn't say it's a rule that you will have problems. Maybe an exception...

As for the OP: What is MANAGE? Some piece of software that you used to create the ntfs partition? If XP reads it fine, and if you can, move all data from it on external hdd, then boot ubuntu and use Gparted to format it again as ntfs (make sure you get the CORRECT ONE!!!). Then put the data back.

See if ubuntu will access it as per your expectations after that.

I agree you can do what you mention without any apparent problems and if you don't use the backup feature, 
you may never have a problem. You may also find a different unexplainable problem eventually.
Because it did cause that one major problem, I decided that I would not mess with W7 files from within Ubuntu. 
I cannot access my Ubuntu partition from within W7, so I treat them the same.
But, of course I like Ubuntu better! :)

---

### Post by jeff92677 on 2010-05-20
Many thanks for the help. I edited the original post in case someone new was drawn into this problem, which turns out to be a misunderstanding.

The problem is that when saving a PDF file to my NTFS partition, the file was deposited without the PDF extension.

However, Ubuntu tagged it in the comments to the right as a PDF file, so naturally I assumed it was a valid pdf file.

When I doubled clicked it, I got the message about not having privileges to open the file.

When I appended the .PDF suffix to the filename, everything worked.

Here's why I think it's confusing: If Ubuntu recognizes the file as a PDF file, and an application in Ubuntu tries to open a file thought to be a PDF file by the Operating System, why would it need the PDF extension, or if it does need the extension, why pop out a message about lack of privileges to read the file?

Bottom line -- I was misguided by the "PDF FILE" interpretation by Ubuntu (which was correct) and assumed it would be opened as a PDF file (which it was not).

If the OS can inform an application that indeed, a file is of a certain type, it seems that the application might take direction from the OS and treat the file as the OS treats it, as a PDF file.

My confusion, sorry about that, but I think Ubuntu should not tag a file as PDF it it is not in the proper filename.extension format, e.g. doesn't have the PDF extension, or one of the other extensions recognized by a PDF reader (a form file, etc.).

Thanks again for those that helped.

Jeff

---

