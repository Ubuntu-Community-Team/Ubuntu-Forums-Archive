---
title: "Installation of Lubuntu 12.10 deleted Windows XP without warning!"
date: 2012-11-20
forum: Installation &amp; Upgrades
---

### Post by Flixter on 2012-11-20
Today I installed Lubuntu 12.10 to my girlfriends old laptop (which had Windows XP) to use it for web browsing and some pdf viewing and so. My plan was to have both OS's alongside each other, and I had read through documentation which clearly showed that there should be such option, as in this page:
[http://launchintolinux.wordpress.com/2012/04/04/installing-lubuntu-a-step-by-step-guide-to-dual-booting/](http://launchintolinux.wordpress.com/2012/04/04/installing-lubuntu-a-step-by-step-guide-to-dual-booting/)

I started install, and there was NO option "Install Lubuntu alongside Windos XP". First option was to overwrite Windows completely, and had appropriate warnings about losing all data. Second option gave some information about new partitions or so, and third was manual partition.
So, I thought maybe the second option is good because it does its thing automatically, and there was no warning that it will erase everything.
Installation started, there was never any questions about partitioning or anything, no warning about deleting current information and after installation finished, I noticed that Windows and all the data it contained is totally gone! Wheeewww, was my girlfriend happy!!!

Basicly, I want to criticize this installation procedure. As far as I (retrospectively) understand, all three options would have lead to losing all data (except maybe third one in capable hands), and yet only first had appropriate warning.
Secondly, there should be easy option to install alongside Windows, as I believe is in normal Ubuntu.
Thirdly, if installation is about to delete all information, there should be STRONG warning about that before anything is deleted. And this applies whether the person or installer software has decided to delete files.
All these issues are basic usability and user friendliness, which every programmer should be aware off!

Ok, the data is lost, and Lubuntu occupied the hard drive. Now comes the hard part:
**is there any way to get data back?** Can some program read the whole disc physically through, and try to identify files from there, and maybe save them to my (Windows) external USB hard drive?
Can this be done while Lubuntu itself is running, or should I run the recovery software from boot CD, and is there something suitable in this package: [http://ubuntu-rescue-remix.org/](http://ubuntu-rescue-remix.org/)

I am grateful of every piece of information, and if there is some software with easy-to-use GUI, I would be happy with it, because I am very new to Linux, especially using command line. Thus the software should be very user friendly.

Thank you!

---

### Post by cwsnyder on 2012-11-20
The documentation you read is not the official Canonical documentation.  That said, are you attempting to recover your girlfriend's data files or Windows?  You are unclear on that point.  To reverse the installation of Lubuntu is not possible. Period, end of discussion.

You can re-install Windows, but the data will be gone, and your Lubuntu installation with it.

There are file recovery programs to attempt to recover SOME of the data, but I would NOT, repeat NOT, try them from withing Lubuntu.  They would also have lost most of the capability to recover the data when you repartitioned and reformatted the entire drive.

You may not have had the option to install Lubuntu alongside Windows if you did not have at least 20 G free space on the drive before attempting an installation.  That is in the Canonical documentation.

---

### Post by Lyfang on 2012-11-20
**Warning: Don't to use the hard drive that you used to have Windows XP on!** Then find good software to recover the data.

---

### Post by oldfred on 2012-11-20
Testdisk and photorec. 

Testdisk will look for old partitions, and if it can find the file table show files. But some have to be damaged. Ubuntu install is not large and writes to various places on drive, but will have overwritten some data.

If testdisk does not work,  photorec can scan a drive for anything that looks like a file. Since file table is gone, you will not get file names, just extensions based on file type. Takes a very long time and then takes a long time to sort thru files. 

Some other similar programs:
       [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

       Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

   Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

Hard drives also fail, any major system change can cause problems as you found. So we always suggest backups and regular backups of most important data.

---

### Post by Mark Phelps on 2012-11-20
In my experience, Windows utilities do a better job of recovering Windows partitions; Linux utilities, a better job of recovering Linux partitions.

If you want to use Windows utilities, you will have to remove your drive and connect it to a Windows PC.  Then, download and install RecoverMyFiles from Runtime Software.  Run the scan in deepest recovery mode -- will take HOURS.

When done, look to see what it found.

IF it found what you wanted, you will then need to go online to purchase a License.

Your data -- your money -- your choice.

---

### Post by dannyboy79 on 2012-11-20
If you were following the guide you linked to and ended up NOT seeing exactly what the picture showed then why would you proceed with the install without definite knowledge that it wasn't going to overwrite windows xp. There's nothing wrong with the Ubuntu's install process, this is a case of "user error", NOT Ubuntu's.
Your data is most likely gone if you did repartitioning and reformating.

---

### Post by Flixter on 2012-11-21
> **cwsnyder said:**
> That said, are you attempting to recover your girlfriend's data files or Windows?
...
You may not have had the option to install Lubuntu alongside Windows if you did not have at least 20 G free space on the drive before attempting an installation.

I am only trying to get data files back, Windows was anyways very slow and old.

At the time of install there was around 40 gb of free space on the disk.


Dannyboy79, maybe there is nothing exactly wrong in the installation procedure, but it is definately not very logical, as I pointed out three issues in my first post. Of course, this is said from perspective of Linux/Lubuntu newbie, and general usability.

Oldfred, thank  you for the links! I'll try Photorec and Testdisk using some liveCD (Parted magic, Trinity rescue kit, etc.).

One question though, would it be possible to make low level copy (image?) of laptops hard drive to external USB hard drive, and use some Windows tools to operate on that image? What software would be recommended to that?

---

### Post by mastablasta on 2012-11-21
> **Flixter said:**
> I am only trying to get data files back, Windows was anyways very slow and old.
 
a very annoying thing. i hope you manage to recover some data.
> 
At the time of install there was around 40 gb of free space on the disk.

 
what they mean is you would need 20+ GB unformatted disk space. means no format on the drive. anyway manual parittioning would be better in this case.
 
> 
Dannyboy79, maybe there is nothing exactly wrong in the installation procedure, but it is definately not very logical, as I pointed out three issues in my first post. Of course, this is said from perspective of Linux/Lubuntu newbie, and general usability.
that's why there is documentation and you have to backup the data before repartitioning or creating dual boot. you are not the only one that fell for that trap. but dual boot is not newbie stuff. they tried to make it as simple as possible, but sometimes....
 
>  
One question though, would it be possible to make low level copy (image?) of laptops hard drive to external USB hard drive, and use some Windows tools to operate on that image? What software would be recommended to that?
 
you could have a look at clonezilla if it can do that kind of image, though i am not sure this is possible.
 
too bad you didn't use a simple backup like Redo Backup to create a disk image (or at least to backup the data) before installing new OS. that way you could easily restore it now.

---

### Post by Flixter on 2012-11-21
I ended up running PhotoRec from Parted Magic LiveCD. After half an hour the estimated time to completion ranges from 15-20 hours. Data is stored to external USB hard drive. Lets see how it goes!

---

### Post by darkod on 2012-11-21
It's now too late but testdisk would have been the better and first option. As oldfred said, photorec only in case testdisk can't help.

Testdisk usually can bring your partitions back and you will lose only the files that were directly overwritten by the ubuntu files (same physical sectors). You get all of your folder structure and files with complete filenames. Most of it anyway...

Photorec will scan the whole disk and try to recover everything it finds but without any file names. Not only that you will wait 20 hours to see how it did, after that you will have to spend double that to go through each file with a generic filename and rename it to something that makes sense to you.

---

### Post by oldfred on 2012-11-21
+1 on Darko's comments.

Also as posted in post#4 - instructions on image backup with gddrescue
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Flixter on 2012-11-26
Just to wrap this up I want to share my experience.

First I tried to run Photorec from livecd directly on my hard drive, but after one hour or so it crashed (remember, it is old laptop). Then I made .dd image of the disk to the external usb drive, and continued to process that image on a more modern computer.

First I ran Photorec, which took this time only some 4 hours for the whole disk, and it really managed to dig up lots of files. Now there was trouble of making some sense about them. So, after some head scratching and reading your comments, I decided to give another try to Testdisk.

I dont know what I missed in the first time, but this time I could actually find my NTFS partition, and there seemed to be most of the folders in their place. So I wrote the information back, and voila, after some mounting exercises I could actually read all those missing Windows files. I believe almost everything was rescued!

Basically, if I was more habituated Linux user, I could have done the whole rescue project probably in 15 minutes. Anyway, I am happy how it finally turned out, and at least I got some experience on different rescue techniques.

Thank you very much for all who contributed!

---

### Post by oldfred on 2012-11-26
Glad you got most of your data back. That is not always the case. 

May be a good time to plan good backup procedures? Part  of the problem in Linux is that there are so many ways to backup.
       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

---

