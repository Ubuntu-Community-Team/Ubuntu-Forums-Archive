---
title: "Make an external drive internal"
date: 2012-03-05
forum: Installation &amp; Upgrades
---

### Post by lile001 on 2012-03-05
I have a 1 TB external drive I'd like to repurpose into an internal drive.  This used to be my backup drive but I have started using Spideroak online backup (Spideroak is really Ubuntu Friendly, BTW IMHO),  I also have two Linux computers, which gives me the ability to back up one from the other using rsync.  External drive has been sitting in a drawer, as I have plenty of easier backup options.  I think that the drive will be somewhat more robust inside the computer, less wires flopping about to get unplugged, less chance of jumping off the desk and getting ruined, etc.   Just bought a new brainbox, with only one 250GB drive (rather small by today's standards), planning to expand it by installing a drive one way or another. 

I have never taken one of these external drive cases apart, but I take it there is not much to them except a translator board  between hard-drive-ese and USB-ese, and a power supply. At the heart should be a standard hard drive, no?

What hardware would I need to install this into the computer? If anyone who knows such hardware can help me identify what I am looking at once I pop the case that would be helpful.  All the drive-install know-how I have is really obsolete.  They were still making 8-tracks and logging onto BBSs when I started installing hard drives.  The Internet was a twinkle in young Al Gore's eye.   Hell, all the cables are unfamiliar looking anymore. 

 What software install issues will I run into if I stick this in and fire up Ubuntu?  Will I have to format it or something?  I have never tried installing a new drive under Ubuntu before, although have done it under Winders plenty of times.  

If anyone has done this and decided it was a really bad idea, I'd like to know that before I get the screwdrivers out.  "Here there be Tygers" or something like that?

---

### Post by oldfred on 2012-03-05
I have not done it. Some have posted where they buy a case and put an older internal drive into a case and it works.

You need to determine if it is the old IDE/PATA or newer SATA drive.
with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

The old PATA drives use the wide flat 80 conductor cable and the SATA use the thin narrow cable. You then need to see that computer has another SATA or PATA port available. Most newer computer come with many SATA ports and only 1 or 2 PATA ports for a legacy device which often is used then by the CD/DVD drive. I converted to SATA about 6 years ago as soon as they were only a few dollars more than PATA just to avoid the tiny jumpers for master/slave.

---

### Post by lile001 on 2012-03-05
Thanks!  I will get the screwdrivers out, and let you know what I find.  If I do not post again in about 30 minutes, please call the authorities as I have been eaten by Tygers. :shock:


> **oldfred said:**
> I have not done it. Some have posted where they buy a case and put an older internal drive into a case and it works.

You need to determine if it is the old IDE/PATA or newer SATA drive.
with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)

The old PATA drives use the wide flat 80 conductor cable and the SATA use the thin narrow cable. You then need to see that computer has another SATA or PATA port available. Most newer computer come with many SATA ports and only 1 or 2 PATA ports for a legacy device which often is used then by the CD/DVD drive. I converted to SATA about 6 years ago as soon as they were only a few dollars more than PATA just to avoid the tiny jumpers for master/slave.

---

### Post by lile001 on 2012-03-05
SATA.  a spare connector was inside the new computer case already.  Hardest thing was getting the plastic case off of the external drive, which was designed to snap instead of screw together.  

OK, what happens when I turn it back on?  Will Ubuntu just recognize the drive and go? or do I have to configure something?

---

### Post by whatthefunk on 2012-03-05
If its a SATA, you should just have to plug it in and Ubuntu should see it after booting.

---

### Post by oldfred on 2012-03-05
Was the drive fully bootable on its own, or was grub2's boot loader in the MBR?

As whatthefunk says BIOS should see drive. If you want to boot from it choose it in BIOS (if it has grub's boot loader). If you boot from another then you may need to run sudo update-grub to get it to find the new install on the new drive.

---

### Post by lile001 on 2012-03-05
> **oldfred said:**
> Was the drive fully bootable on its own, or was grub2's boot loader in the MBR?

As whatthefunk says BIOS should see drive. If you want to boot from it choose it in BIOS (if it has grub's boot loader). If you boot from another then you may need to run sudo update-grub to get it to find the new install on the new drive.


This is going a lot easier than I thought it would.  Maybe some of this Linux stuff has started to seep into the cracks in my thick head. 

1.  Physical install was really easy - plug and play because of spare cables already in the 'puter (Thanks, Dell!)

2. First time I rebooted, hit F12, BIOS didn't recognize the new drive.  Checked all cables, rebooted.  

3. Second time I rebooted, BIOS found the new drive. 

4.  I found this tutorial, written by a wonderful author who does not speak in gibberish or computerese:  [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

5.  Used Gparted to partition the new drive into two 500GB EXT3 partitions.  This allows me to use one partition as a local backup.  

As expected, Windows can't see the ext3 drives (although it tried to for a long time), but Linux can see the Windows drive partition.  Nya nya, I can see you but you can't see me! 

This is a fresh install, I don't have any data on anything, and I could still start over if need be.  I may have given Windows too much room.  Maybe I should have put Linux on the 500GB ext3 partition instead?  (Ooops, maybe. )


Now I have an interesting quandry:  Windows is hogging 150GB of my original 250GB drive, Linux has 100GB on FAT32, and then two 500GB EXT3 partitions.  I need to move 116GB of data from the old computer to the new one.  If I exceed the 100GB partition with the new data that was allowed for Linux, what happens?    Should I start over and install Linux on the EXT3?  Or have I screwed it all up as usual?

---

### Post by oldfred on 2012-03-05
I am not sure what you mean by Linux on FAT32? Linux does not work on FAT partitions except for the installer.

I do not recommend FAT partitions unless you have to have them for compatiblity with some device like an xbox or Mac. NTFS has a journal and can store files over 4GB where FAT does not.

I normally suggest Ubuntu's / (root) partition be 10 to 25GB with a separte /home and/or separate data partition. If sharing with Windows a separate shared NTFS partition makes it easier and safer to share data between the systems. I have my Firefox and Thunderbird profiles on my NTFS shared partition.

---

### Post by lile001 on 2012-03-05
> **oldfred said:**
> I am not sure what you mean by Linux on FAT32? Linux does not work on FAT partitions except for the installer.

I do not recommend FAT partitions unless you have to have them for compatiblity with some device like an xbox or Mac. NTFS has a journal and can store files over 4GB where FAT does not.

I normally suggest Ubuntu's / (root) partition be 10 to 25GB with a separte /home and/or separate data partition. If sharing with Windows a separate shared NTFS partition makes it easier and safer to share data between the systems. I have my Firefox and Thunderbird profiles on my NTFS shared partition.

Well maybe I don't understand what is going on, as usual.  I installed Linux from the live CD this morning, on a Windows machine.  Accepted the defaults for whatever.  I don't really know WHAT kind of partition Linux is installed on, just that it is 100GB and Winders has 150BG.  Now I am wondering if I didn't give Linux enough room.  


So what happens if I try to put 116 GB of stuff in my /home folder when Linux has 100GB available on one drive and 500GB available on the other drive?  Does it spill over, no problem, or will it complain?

---

### Post by lile001 on 2012-03-05
Maybe what I want to do is this???

[https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)


```
An interesting ability of mount is it's ability to move specific parts of a 
filesystem around. For example: 
sudo mount --bind /mnt/Files/Music /home/user/MusicWill  let the folder 
"/mnt/Files/Music" also be accessible in  /home/user/Music. If you wish to 
"move" a folder (no data is copied or  removed, it is merely displayed in a different place) then use: 
sudo mount --move /mnt/Files/Music /home/user/Music
```I don't understand this yet, but does this mean I could put my /home folder on the new drive? I have been RTFM'ing for some time now but I am still not understanding which command will physically locate my /home directory on the 500GB drive.

---

### Post by oldfred on 2012-03-05
It is easiest to do as part of a new install. But you can create another partition and copy (including hidden files) to another partition and edit fstab to include the new /home partition. All Linux system partitions have to be Linux formats. I often suggest the additional NTFS partition for shared data, but that cannot be /home.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

Actually the bind is a more advanced way. I do not use bind, but use links which works for many but bind has some advantages if networked or in a few other cases. I have a tiny /home that I now keep inside my / (root). My /home is about 1.5GB and most is my hidden .wine with the Windows version of Picasa. Actual system settings (the hidden files) are only 256K or abouts. But I am agressive in moving some larger hidden folders that may have data, not just settings to my data partitions.

See posts by Morbius1 as he uses bind.
Splitting home directory discussion:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata]("http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata")
Another way to share:
Morbius1 uses bind, now:
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)

If you put data in other partitions you may not have to move /home and / may only be 5 or 6GB with /home depending on what added apps you install.

---

### Post by lile001 on 2012-03-05
I was able to follow the instructions for using bind, for example:

```


sudo mount --bind "/media/Bigdrive/larry"  "/home/larry"


```Successfully allowed all the files stored on Bigdrive to appear in my home folder, and

```

sudo mount --bind "/media/OS/Users/Larry"  "/home/larry/WindowsFiles"

```Makes the files in my Windows folder appear in my Linux home folder.  Great!

Of course all this fancy stuff dissappears when I reboot.  I have read some things about how to make this permanent however have yet to understand them. RTFM'ing leaves my head spinning, usually.  It seems there are six ways of doing anything in Linux, and usually some of them are way simple, and there is always a helpful, geeky genius ready to tell me that the most complex and obfuscated way is the "best" way for some reason, but eventually someone comes along and says "oh just right click on it."  

What is the simplest way to make this stuff permanent?

---

### Post by lile001 on 2012-03-05
About the first thing I read about is called fstab, and about the first warning in one istruction is this:
```

**Editing Ubuntu's filesystem table**

 It  is possible to break Ubuntu if some of the earlier lines in the file  opened during this step are modified, so be sure to read this section  carefully.
```

This tells me I am loading dynamite in the blunderbuss (again :rolleyes:)  and should probably not continue with the instructions, since I haven't the foggiest idea what the next thing said is.  I am sure someone who knows this stuff well will post next and say "it's easy!".  Well, easy for you to say.  Check the avatar.  I am not represented by Homer just for humor. 

 It is possible that this page  [https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) 
is describing what I am asking about, or not, however it talks about 

```
The third - simple - method is to install the **pysdm** package (in Gutsy) and then use **System-Administration-Storage Device Manager** without any manual editing of the fstab file, and disregard most of the instructions that follow. 
```

which may be what I am looking for.  Is it?

---

### Post by lile001 on 2012-03-05
```
The third - simple - method is to install the **pysdm** package (in Gutsy) and then use **System-Administration-Storage Device Manager** without any manual editing of the fstab file, and disregard most of the instructions that follow. 
```which may be what I am looking for.  Is it?[/QUOTE]

Loaded up pysdm, but can't make any sense out of it, so it looks like it is made for people that are a lot smarter than me.

---

### Post by lile001 on 2012-03-05
This post

[http://ubuntuforums.org/showthread.php?p=10899012#post10899012](http://ubuntuforums.org/showthread.php?p=10899012#post10899012)

seems to make some sense at least, I'll try the suggestions.  This is what I did in a file called /etc/init/home-mounts.conf:

```
# Remount partitions with bind
#description "Bind Data Subdirectories to Larry and qhyrrae's Home Directories"

start on stopped mountall

script
mount --bind "/media/OS/Users/Larry" "/home/larry/WindowsFiles"
mount --bind  "/media/Bigdrive1/larry" "/home/larry"

end script
```

Will it go, or will it blow?

---

### Post by lile001 on 2012-03-06
> **lile001 said:**
> 
Will it go, or will it blow?

Nah, didn't work.  On reboot, none of the mounted folders show up where they are supposed to.

---

### Post by lile001 on 2012-03-06
> **lile001 said:**
> Nah, didn't work.  On reboot, none of the mounted folders show up where they are supposed to.

On further research this apparently is a script that is dependent on a program called Upstart.  The manual for Upstart is 180 pages, and begins by bragging they wrote parts of the manual in Emacs before diving off into gibberish I can't understand.  People like that should not be let out of their cages.  

I haven't been able to Grok any of this stuff about fstab either, and it is apparently much simpler.  

Can someone help walk me through a straightforward way to make these binds permanent?  I am in far over my head, and liable to do more damage than good unassisted. 

Or should I start over and reinstall Ubuntu?  Am I just beating my head against the wall?

---

### Post by lile001 on 2012-03-06
Apparently I can put some of this stuff in a file called /etc/rc/local and it will run at startup.  Here is what I did:

```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
mount --bind "/media/OS/Users/Qhyrrae" "/home/qhyrrae/WindowsFiles"
mount --bind "/media/OS/Users/Larry" "/home/larry/WindowsFiles"
mount --bind  "/media/Bigdrive1/larry" "/home/larry"
mount --bind  "/media/Bigdrive1/qhyrrae" "/home/qhyrrae"
exit 0
```

Let's see if this works.

---

### Post by lile001 on 2012-03-06
Well, it did and it didn't.  

Binds weren't showing up after a reboot.  I tried to run the script 

```
sudo /etc/rc.local
```manually, and i got an error message.  Apparently, the three partitions (windows, called OS, Bigdrive1 and Bigdrive2) aren't mounted at bootup by default.   After manually mounting them (by clicking on the picture in Nautilus, not by any fancy stuff!) the script would run and all those binds show up correctly.  

This is looking like it is almost working.  How to get all that stuff to mount automatically? GAAHH!  We are back into that fstab gibberish that I can't understand.  HELP!

Here is something about that, but I haven't been able to make any sense out of it: [https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts](https://help.ubuntu.com/community/AutomaticallyMountPartitions#Systemwide_Mounts)

---

### Post by oldfred on 2012-03-06
I use links, but here is some more info on bind. Use bind not bindfs now. But I think your issue is the mounting of your partitions. When you click on them you mount them and then your script works. You have to add the mounts to fstab to permanently mount them.

Advantages of bind post 16 - Morbius1
[http://ubuntuforums.org/showthread.php?t=1896695](http://ubuntuforums.org/showthread.php?t=1896695)
HowTo: Create shared directory for local users (with bindfs). - sisco311
[http://ubuntuforums.org/showthread.php?t=1460472](http://ubuntuforums.org/showthread.php?t=1460472) 
With upstart script 
[http://ubuntuforums.org/showthread.php?t=1771773&page=5](http://ubuntuforums.org/showthread.php?t=1771773&page=5)

Example of creating a mount point (Data2), and permanently mounting a partition.

# Make permanent mount point (unmount if already mounted):
sudo mkdir /media/Data2
# Find your UUID:
sudo blkid
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
# Anytime you edit fstab always do this before rebooting. If no errors it just remounts everything, but if errors you have to fix before rebooting or you may not be able to:
sudo mount -a

UUID=01CC498FE4856480 /media/Data2 ntfs defaults,uid=1000,nls=utf8,umask=000 0 0
Window_names prevents the use of invalid windows characters:
(which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) 
UUID=66E4DC83E4DC56C1 /media/Data2 ntfs defaults,uid=1000,windows_names,umask=000 0 0

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by lile001 on 2012-03-06
> **oldfred said:**
> I use links, but here is some more info on bind. Use bind not bindfs now. But I think your issue is the mounting of your partitions. When you click on them you mount them and then your script works. You have to add the mounts to fstab to permanently mount them.
[]("http://www.psychocats.net/ubuntu/mountlinux")

OK, slow down, this is way more information than I can digest at once.  I have read pages about fstab over and over and come away completely confused, and in fear that I am messing around like the sorcerer's apprentice. I basically don't understand anything that's being said from step one.   I may RTFM, but I don't understand TFM.  

What do I do first?  Can I post something that will help you walk me through this maze?

---

### Post by lile001 on 2012-03-06
here is a stab at fstab.  the "f" has the same meaning as the "F" in RTFM.  here goes;

It would have been really handy if the first three or four pages of gibberish i found about fstab had bothered to mention this:

```
sudo blkid
/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="5450-4444" TYPE="vfat" 
/dev/sda2: LABEL="RECOVERY" UUID="F2DCD958DCD917A5" TYPE="ntfs" 
/dev/sda3: LABEL="OS" UUID="8A20DBB920DBAB09" TYPE="ntfs" 
/dev/sda5: UUID="c1231a18-734c-4df2-b917-c7d8177fea45" TYPE="ext4" 
/dev/sda6: UUID="97d9f6ea-ad97-4fbd-aef7-ee4993a098ef" TYPE="swap" 
/dev/sdb1: LABEL="Bigdrive1" UUID="2d3d8a4a-95c4-4056-992a-c5cb9d3895bc" TYPE="ext3" 
/dev/sdb2: LABEL="Bigdrive2" UUID="698b3511-cbb6-44e1-b991-bf7fbf1813cf" TYPE="ext2"
```

So I have added these lines to a copy of fstab (not the original!)  
```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=c1231a18-734c-4df2-b917-c7d8177fea45 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=97d9f6ea-ad97-4fbd-aef7-ee4993a098ef none            swap    sw              0       0
#NEW AND PROBABLY ERROR-RIDDLED STUFF ADDED BY ME:
#LABEL=OS 
UUID=8A20DBB920DBAB09 /media/     ntfs    defaults    0    2
#LABEL=Bigdrive1 
UUID=2d3d8a4a-95c4-4056-992a-c5cb9d3895bc /media/    ext3    defaults    0    2
#LABEL=Bigdrive2 
UUID=698b3511-cbb6-44e1-b991-bf7fbf1813cf /media/    ext2    defaults    0    2
```OK, what have I got screwed up in that file?

---

### Post by lile001 on 2012-03-06
Although this isn't solved by far, I am going to mark this thread as solved and repost that last question in Absolute Beginner Talk under a new subject.

---

