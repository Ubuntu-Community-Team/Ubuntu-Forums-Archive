---
title: "Clean Install Partitioning for Music &quot;Server&quot;"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Ch3knraz3 on 2008-04-05
I know these kinds of questions have been asked before so I apologize if this is repetetive.

First, a little background.  I have a PII 266 with 192mb RAM.  I am planning on using it to store and play my music files. My sound card is a SoundBlaster Audigy card that gets freaky with its original drivers.  So I will be using drivers from the kx project.  I had a little problem booting from CD becuase its a home built machine I acquired and the CD Drives are SCSI not IDE.  It's taken me a while to get everything in place to start a fresh install.  Given the system parameters I intend to use Xubuntu.  The standard cd kept hanging so I now I am using the Alternate CD.

Anyway, my issue revolves around partitions.  I usually install two drives on a machine one for just the OS and Applications and a second with a swap partition and separate storage partition.  Since I am new to Ubuntu and Linux I will be experimenting with several machines so I am trying to conserve my hard drives.  I will only be putting one in this box.  I used the windows based seagate tools to prepartition the drive.  It's a 250gb drive and I have split it into 3.  The #1 Primary is a 20.4gb Fat32 for the OS and Applications, #5 Logical is 10.9gb FAT32 for the Swap File, and #6 Logical is 218.7gb NTFS for the Music Files.  Partition 1 and 2 are clean but I have already placed the Music Files on Partition 3.  Though I do have a backup in case I have a problem.

I beleive the 3 partition approach is valid.  However, I am now thinking I don't have the optimal sizes.  I am installing now and am at the Manual Partition portion of the process.  So I need to decide if I am going to adjust the sizes and I need to understand the Use As options like Ext3 and Ext2.  I also need to understand Mount Point and Mount Options.

Oh, at a certain point I will be setting up a SAMBA server on a different box.  I will want my Music Files to be accessible to all machines on the network regardless of OS.

I would appreciate it if I could get some advice on sizes and perhaps a link to a tutorial on this portion of the setup process.

Thanks in advance:)

Ch3knraz3:confused:

---

### Post by Peter Westley on 2008-04-05
Ch3knraz3,

If this disk will only have Linux on it and you don't expect to be able to access it from windows, I suggest you keep away from the FAT filesystems for performance and reliability reasons. Use instead the native ext3 filesystem for your partitions.

I suggest you partition this way:

/: 20GB
 (OS and applications) 

swap: 1-2GB
10GB is way too much. A rule of thumb is about 2-3 times the amount of RAM you have.

/var: 10GB if not storing music, remaining space if storing music)
var is short for variable and is where data that might grow is kept, this keeps it separate from your OS and application filesystem in case it fills up then it won't affect your OS. If you are going to use an application/server to serve your media files, I suggest storing your music on the var or home partition/filesysem then you can make it available via samba.

/home:10GB if not storing music, remaining space if storing music)
 is similar to var but as the name suggests it's equivalent to "Documents and Settings" under windows. By default ubuntu sets up a Music directory in your home directory

When the system boots, these filesystems get mounted onto the relevant places on the root filesystem. so the root fiesystem has a directory called /var but it's empty and /var filesystem gets mounted at that location.

So I recommend letting the installer do all the partitioning, create ext3 filesystems on them (expect for the swap one of course - that needs no filesystem, only a partition type)

HTH.

---

### Post by Ch3knraz3 on 2008-04-05
Peter,

Thanks for the answer.

Right now all the music files are on the NTFS partition in folder /MP3_Lib: but just to make things easier I will blow away the existing copy of the music files and reload them after the install is successful.  So I will need to be able to see the back up copy on an XP box or see /Home: the XP box.  I'd like to be able to do this before I build the SAMBA box.

So when installing from the live CD using the manual partition option I should have:
2gb | Use As: Swap | Mount Point: ??? | Mount Options: defaults
20gb | Use As: Ext3 | Mount Point: /: | Mount Options: defaults
228gb | Use As: Ext3 | Mount Point /Home: | Mount Options defaults

What is the difference between Ext3 and Ext2?
Is there anything I need to know about ReiserFS, JFS, or XFS?
I'll worry about the physical options when I actually build a server.

I'm guessing I don't need any of the alternate mount options, right?

What about the bootable flag?  That should be set for the 20gb drive with the /: mount point, right?

Thanks,

Ch3knraz3:-\"

---

### Post by Peter Westley on 2008-04-05
Ch3knraz3

I think you pretty well have it. I'm not an expert (used to do unix admin many years ago and have recently returned to playing with linux but some things never change ;-)

> So when installing from the live CD using the manual partition option I should have:
2gb | Use As: Swap | Mount Point: ??? | Mount Options: defaults
20gb | Use As: Ext3 | Mount Point: /: | Mount Options: defaults
228gb | Use As: Ext3 | Mount Point /Home: | Mount Options defaults


There's no mount point for swap, it just is.
Leave mount options default until you know more
Ext3 is a later version of ext2 I believe. The main thing is it has journalling which provides some level of extra protection against power loss at unexpected moments. You should go and search for ext3-howto or similar - I'm sure there's a dissertation on the differences somewhere but I'm not an expert...
As for Reiserfs, JFS and XFS sorry but you'll have to search on those too.

I think the bottable flag should be set for root yes. That might get done automatically given you're installing / there but best make it set, yes.

You will be able to browse to files served off an XP box pretty easily and copy from there when you have the whole thing setup.

Now I think you're good to go!

Good luck.

Peter

---

### Post by Ch3knraz3 on 2008-04-06
Peter,
Thanks for your help.
I repartitioned the drive.  I think I got it right.
Intalled Xubuntu without any real hitches.
I did have a problem with the hanging splash...
but I was able to
> Ctrl+Alt+F1 to get command line. At the command line:
sudo dpkg-reconfigure xserver-xorg
Accept most defaults, choose 'vesa' as the driver. 
That seemed to work.
So I am playing around in the environment.
Have to figure out why my NIC card isn't working.
I hope that won't end up being a thread...LOL.

Thanks again,
Ch3knraz3

---

