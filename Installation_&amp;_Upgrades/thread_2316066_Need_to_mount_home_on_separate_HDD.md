---
title: "Need to mount home on separate HDD"
date: 2016-03-04
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2016-03-04
On a new install (not yet done) System will be on SSD. Want to mount /home on HDD. Here are my code steps:

I'm more than rusty on this and have borrowed heavily from my notes from setting up the current mount that I am using now, so please make corrections or suggestions as appropriate. Thanks for any guidance.

------------------------------

```
sudo mkdir /mnt/newhome
```
# makes new subdirectory "newhome" under /mnt

```
sudo mount -t ext4 /dev/sda7 /mnt/newhome
```
# mounts the partition sda7 at /mnt/newhome (substitute appropriate partition for sda7)

```
cd /home/  
```
# so that command below will copy contents of /home/ to sda7

```
find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
```
# copies files in /home/ to /mnt/newhome (on sda7 in this case)

```
sudo umount /mnt/newhome
```

```
sudo mv /home /old_home
```
# renames /home as /oldhome

```
sudo mkdir /home
```
# makes new /home dir

```
sudo mount /dev/sda7 /home
```
# mounts /dev/sda7 as the (new) /home

```
cd /etc
```
# so that command below will find files with further prefix (i.e., "/dir/path/etc )

```
sudo cp fstab fstabbak
```
# this creates a backup copy of fstab in case of a problem with the edit

```
sudo gedit fstab
```
# edit to add the following line: 

```
/dev/sda7 /home ext4 nodev,nosuid 0 2
``` 

# AFTER ALL DONE AND ALL WORKING SMOOTHLY, DELETE THE "oldhome" with

```
sudo rm -r /oldhome
```

# IMPORTANT: IN COMMANDS ABOVE, BE SURE TO USE CORRECT FILE FORMAT (i.e. EXT3, EXT4, etc) and change sda7 to correct partition (i.e. sda for SCSI hdd, hda for EIDE hdd, and whatever is the correct partition # [where the below says sda7, it might be sda4 or hda3, or whatever])

Edit: Just found this in another post:
> The mount point can be anywhere. If it's in your /home or /media folders it will show up under "Places". If it's directly off "/" or /mnt it will not. I prefer /mnt so I do not see it other than thru the links So when the above is implemented, I will mount under /media so that home will show up under places.

---

### Post by howefield on 2016-03-04
Taking a step back and referring to your previous thread, you currently have 12.04 on an SSD with /home on a separate HDD. You want to clean install Ubuntu Mate keeping the same installation structure, ie operating system on the SSD and /home on the HDD - is that correct ?

Seems to me that selecting "Something Else" at the partitioning stage of the installation and mounting the SSD as / and mounting the HDD as /home but making sure it isn't marked for formatting would give you what you need. 

Can you expand on why you need to go through the above process ?

---

### Post by Odyssey1942 on 2016-03-04
TBH, I did not realize that one can do that. Sounds perfect, but just want to check one thing.

With the mount process, the data on the hdd seems to me to be quite "detached" from / and the SSD (only connected by the "mount"). If the SSD dies or the system goes south, is there better "insulation" from those adverse events if mounted vs your suggestion? If not, I am on it.

Assuming so, in the "something else" install, the HDD will show up just like the SSD does? It has been some time since I did a something else install and I cannot picture it in my mind.

If this is the case, I would just choose the HDD or a partition on the HDD as /home? Simple as that?

Love it! Thanks a ton.

---

### Post by Bucky Ball on 2016-03-04
[See here]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352"). 

Mark the /home partition to use but NOT to format. Create the / partition on the SSD (the / mountpoint is a default selection in there).

Make sure the ONLY partition you have ticked to format is the new / partition. You can also use the same /swap partition that is already there. Mark that to use and doesn't matter if it is ticked to format. (You may not even need to mark that to use, may happen 'automagically', don't remember. Best check, but bottom line, you don't need to create another /swap if you already have one.)

---

### Post by howefield on 2016-03-05
> **Odyssey1942 said:**
> With the mount process, the data on the hdd seems to me to be quite "detached" from / and the SSD (only connected by the "mount"). If the SSD dies or the system goes south, is there better "insulation" from those adverse events if mounted vs your suggestion? If not, I am on it.

I don't really understand what you are saying here.

> Assuming so, in the "something else" install, the HDD will show up just like the SSD does? It has been some time since I did a something else install and I cannot picture it in my mind.

To give you an example, does the attached image help. This is the screen after you select Something Else in the "*Installation Type*" screen. ?

There are 4 disks in there..

```
sda : an HDD which will be used for /home and /swap (partitions created and populated before running the installer)
sdc : an NTFS HDD formatted disk which I use for ntfs virtual machines and ignored for this exercise.
sdh : a 120gb SSD mounted for / 
sdi  : a 240gb SSD ignored for this installation.
```

You don't have to mount swap, if the installer finds a swap partition it will use it automatically, although might be easier just to mount it anyway :) Note that /home has not been marked for formatting. If it were a virgin install with nothing on sda it could be marked for formatting but as I understand, your /home is currently being used and you won't want it wiped clean.


* Remember to select the disk that you want marking for grub.

Your screen will obviously reflect your setup, but you should see all your disks and partitions that are available for selecting.

As always, should go without saying but ensure a backup of important data before upgrading :)

---

### Post by vidtek on 2016-03-05
Odyssey1942-

One thing that has previously caught me is the not-so-obvious place on the install screen to choose where the install puts the boot files.  If your new install drive is not /dev/sda, but something else, it could put them onto another (say large data drive).  Just double-check at the bottom of the install screen that it's going to install grub (boot stuff) in the drive you want.

Cheers, Tony.

---

### Post by Odyssey1942 on 2016-03-05
Thanks for all these. Just to try to clarify my question for Howefield:

If / is on SSD and /home is on HDD by virtue of the process that I was originally contemplating (see OP), then the SSD fails or the /system goes pear-shaped, would /home be "insulated" to a greater extent than would be true if /home is placed on the HDD during a "something else" install?

Hope that might be more clear, but the more I think about it, since I back up pretty regularly, /home going toes-up might only affect any data that hasn/t been backed up yet, and so a minor risk.

-------------------------------

Next question is, and /home will have had a current backup just before the install, should the data in /home survive the something else install (assuming one does not format /home?)

It might be useful to see current disks:

> 
robert@i3-2120:~$ sudo fdisk -lu

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes  [COLOR="#FF0000"][this is the HDD][/COLOR]
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00001736

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    31250431    15624192   82  Linux swap / Solaris
/dev/sda2   *    31250432    89843711    29296640   83  Linux
/dev/sda3        89845758  1953523711   931838977    5  Extended
/dev/sda5        89845760  1066405887   488280064   83  Linux
/dev/sda6      1066407936  1953523711   443557888   83  Linux

Disk /dev/sdb: 128.0 GB, 128035676160 bytes  [COLOR="#FF0000"][this is the SSD][/COLOR]
255 heads, 63 sectors/track, 15566 cylinders, total 250069680 sectors
[COLOR="#FF0000"][these three lines which are same as in sda above, deleted to save space][/COLOR]
Disk identifier: 0x0000d4ca

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    48828415    24413184   83  Linux
/dev/sdb2        48828416   250068991   100620288   83  Linux

Disk /dev/sdc: 2000.4 GB, 2000398931968 bytes [COLOR="#FF0000"][this is a new portable backup drive][/COLOR]
255 heads, 63 sectors/track, 243201 cylinders, total 3907029164 sectors
[COLOR="#FF0000"][these three lines which are same as in sda above, deleted to save space][/COLOR]
Disk identifier: 0x85d63c95

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1          206848  3907024064  1953408608+   7  HPFS/NTFS/exFAT
[COLOR="#FF0000"][The "Linux" formats above are EXT4][/COLOR]

I note that:
> /dev/sda1 2048 31250431 15624192 82 Linux swap / Solaris it appears that my swap file is on the HDD. Been too long for my feeble memory to know if the install process just did this or whether it was something deliberate on my part.

This raises another question. Would it not be better to format my portable backup drives EXT4 (instead of NTFS as currently) so as to preserve permissions, etc? Have never had to restore a backup and so I may currently have an issue with permissions should it be needed.

---

### Post by yancek on 2016-03-05
> If / is on SSD and /home is on HDD by virtue of the process that I was  originally contemplating (see OP), then the SSD fails or the /system  goes pear-shaped, would /home be "insulated" to a greater extent than  would be true if /home is placed on the HDD during a "something else"  install?

The major difference is that using the Something Else option is much less complicated.  When you install Ubuntu using the Something Else option, you select your / partition to install to, you then select your current home partition from the main window and select /home as the mount point and as pointed out above, do NOT select the box in the main window to format the /home partition.  You would select to format the / partition.

 If you already have a swap partition you don't need to make a new one.

If your backup partition is used only for Ubuntu or other Linux installs, then formatting it with a Linux filesystem makes sense.  The only reason to use ntfs is if you are using windows or sharing data between the two systems.

---

### Post by Odyssey1942 on 2016-03-05
Thanks. Using NTFS just preserves the flexibility to use the same drive to back up our Windows computer. 

With respect to permissions, or any other consideration, is there an advantage, where Linux backups only are concerned, to using EXT4? If there is, I can always partition the portable drive, with EXT4 on one partition and NTFS on the other

Also, and the other question, is should the data now on the HDD survive a "something else" install?

---

### Post by oldfred on 2016-03-05
You never can have enough backups.
But I do not back up Ubuntu / as I just plan to reinstall. I do copy a few configuration files that I manually edit into /home so my normally backup of /home includes copies of those few files.

If just your data copied to NTFS then you can restore the data and easily reset ownership(you) & permissions (same as /home). But if system files, you either have to know each files ownership (not always root) and exact permissions.  So you cannot copy / into NTFS as backup anyway. 
The few text configuration files I save, I do not plan to restore as a file, but would open file & copy settings into new install's file that has correct ownership & permissions.

---

### Post by vidtek on 2016-03-05
> **oldfred said:**
> You never can have enough backups.
But I do not back up Ubuntu / as I just plan to reinstall. I do copy a few configuration files that I manually edit into /home so my normally backup of /home includes copies of those few files.

If just your data copied to NTFS then you can restore the data and easily reset ownership(you) & permissions (same as /home). But if system files, you either have to know each files ownership (not always root) and exact permissions.  So you cannot copy / into NTFS as backup anyway. 
The few text configuration files I save, I do not plan to restore as a file, but would open file & copy settings into new install's file that has correct ownership & permissions.

This is something I've always done, keep a few of the config files I use with every distro change/upgrade.  Good tip with copy and paste the contents though, I always find the permissions issue a pain to deal with, simple idea from you, I'm just obviously a real simpleton not to think of doing it that way! Cheers OldFred.

Tony

---

### Post by Odyssey1942 on 2016-03-05
Good morning OldFred and thatks for your usual erudite, top-down view. That sounds like good general guidance and a project for whenever I might be able to research it and learn more. OTOH, if you would please provide a list of those .directories that need to be handled separately, that would be very interesting indeed.

Also, I want to move ahead on my current project, so answers (from anyone) to my two questions will be appreciated. Thanks.

---

### Post by oldfred on 2016-03-05
I use rsync to backup /home and I do use a separate /mnt/data partition for almost all my data. My /home is still inside / and is about 2GB only because we use .wine & Picasa which is now about to be discontinued. 

My script also includes update of list of installed apps (dpkg list) and system configuration (bootinfoscript) so /home has newest data.
Note if server type install, you would have a lot more files in / to backup - apache, database, etc.

 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by mikodo on 2016-03-05
> **Odyssey1942 said:**
> 
If / is on SSD and /home is on HDD by virtue of the process that I was originally contemplating (see OP), then the SSD fails or the /system goes pear-shaped, would /home be "insulated" to a greater extent than would be true if /home is placed on the HDD during a "something else" install?

I think it is the same "insulation" if you do the separation and mounting like in the "OP" or, you let the installer do the mounting during the installation in "Something else" (for the /home partition). You are seemingly following a guide that undoubtedly works but, most of us just set up that process with the .iso installation disk and let the installer do the mounting that has been discussed by others here.

1. You do the set up and mounting to a separate /home on HD, as in "OP" or,

2. You have the separate /home on the HD and point to that as /home in the installer and let it do the mounting. Once you have a separate /home parition on the separate HD, just keep it there. You don't need to keep separating it from the / SSD partition each install like you are doing in the "OP". Just follow what the others have been telling you about doing in the installer with "Something Else". 

I believe neither is a way of providing better "Insulation" for your /home partition on the HD. Your way seems more complicated though.

The only wild card, "question mark"  I have is, I don't know what the below command is or, if this is "superior" than using the installer way that has been discussed.

```
find . -depth -print0 | cpio --null --sparse -pvd /mnt/newhome/
```

---

### Post by Odyssey1942 on 2016-03-05
Thanks for that input. Yes, I have moved away from the mount process suggested in the OP. I only commented further to try to clear up any confusion resulting from the OP. As I mentioned above, it really doesn't matter as long as I am backing up regularly.

Having adopted the plan to use "Something else" to set up /home on the HDD, I now only want to better understand it, so I will repeat the two questions above in hopes of someone addressing them.

1) > Next question is, and /home will have had a current backup just before the install, should the data in /home survive the something else install (assuming one does not format /home?) and
2) > Would it not be better to format my portable backup drives EXT4 (instead of NTFS as currently) so as to preserve permissions, etc?

---

### Post by mikodo on 2016-03-05
I see. 

1. Yes

2. I would though, Linux sees NTFS I believe.

---

### Post by yancek on 2016-03-05
> 
Also, and the other question, is should the data now on the HDD survive a "something else" install? 				

It should as long as you don't select to format that partition.

---

### Post by Bucky Ball on 2016-03-05
Again, for 1., 'Use partition' but don't tick to 'format'. It would be a very good idea if you booted the install media and get to 'Something Else' and have a good look around to familiarise yourself. This is all theory now but if you actually have a look you'll know what we're talking about.

Didn't I already post[ this link]("http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation/343352#343352")? Gives you some idea, but better off taking a look in realtime yourself, then asking questions if there's anything in there now that confuses you. You don't need to install, just get to the partitioning section, have a look, then abort the install.

---

### Post by Odyssey1942 on 2016-03-06
BB, I must have missed the link earlier, but the tutorial is excellent. I am getting close to the upgrade, just need to complete the backup first. Learning how to do using BackInTime now.

Thanks, all.

---

### Post by Bucky Ball on 2016-03-06
> **Odyssey1942 said:**
> Learning how to do using BackInTime now.

I noticed. As I mentioned on your thread which was originally about partitioning with Gparted, best to post new threads for new problems rather than change tac part-way through a thread. That will decrease your chances of help.

---

