---
title: "GParted/QTParted"
date: 2006-12-18
forum: Installation &amp; Upgrades
---

### Post by digitizemd on 2006-12-18
I'm trying to install Edgy Eft on an HD with one ntfs partition.  I want to resize the partition to allow room for linux.  QTParted/GParted isn't recognizing the file system type of the hard drive.  The only suggestion I've been given is to defrag the hd, which I'm doing right now.  Is there anything else that I could possibly do?

---

### Post by dbbolton on 2006-12-18
did you run the programs as root ?

---

### Post by Sef on 2006-12-18
1) Did you md5sum the download?

2) did you burn it at 4x or less?

---

### Post by mhenriday on 2006-12-26
> **dbbolton said:**
> did you run the programs as root ? Aye, there's the rub !

In installing **Ubuntu 6.06** from a shipit CD to what I hoped would be a dual-boot setup about three weeks ago, I managed to lose all my **Windows** files instead. I'd like to re-install **Windows** for certain applications, but now don't wish to lose **Ubuntu**, which I've grown to appreciate, in the process. Correct partitioning is obviously the crux of the problem. First I hoped to use System&#8594;Administration&#8594;Disk Manager to check my present situation out, only to discover that, unlike in **6.06**, this option is not available in **6.10**, to which I had updated. I then downloaded **QTParted** (v0.4.5-cvs), but every time I try to run it, I am met with a message *cum* query : «No device found. Maybe you're not using root user ?» After clicking on the «OK» button, I get a panel on which most of the menus and tools, like «Operations», «Disks», and «Device» are greyed out and cannot be used. Where do I go from here ? The RootSudo [tutorial]("https://help.ubuntu.com/community/RootSudo") makes it quite clear that going back to a traditional root account is _not_ recommended ; is there anything else I can do to make **QTParted** work ? Or does anyone have any other suggestions for partitioning my 160GB harddisk and reinstalling **Windows** ? Here I require a step-by-step tutorial, so that I don't lose the results that despite my lack of experience with **Linux** I've hitherto managed to obtain in modifying and upgrading my **Ubuntu** system....

Grateful for any help,

Henri

---

### Post by wilcan34 on 2006-12-28
Am having same problem.
Have Edgy installed,Going well.
Wanted to download CNC simulater, callesEMC2. A linux programme.
Download OK but when opened get splash page then it dreps out. 
Then found that the programme does not work for Edgy but works in Dapper.
So was going to do Dual Boot having Edgy and Dapper partioned.
Loades Qtparted fromSynaptic and turns up in Applications>System Tools>QParted.
Click on QParted,Splash,No Disc Found,Are you root user,Frame comes up and all GREYED out??
Could you Help
Regardshttp
Wilky

---

### Post by mhenriday on 2007-01-01
**Wilcan34** and I seem to be in the same position ; *viz*, to run **GParted** we have to be in root. Can anyone explain how we can manage to get two stories up, so as to be able to run the programme ?...

Henri

---

### Post by 454redhawk on 2007-01-01
Download the Gparted LIVE CD and boot it up. Eliminates most of theses problems.
[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828]("http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828")

---

### Post by tagra123 on 2007-01-01
> **mhenriday said:**
> Aye, there's the rub !

In installing **Ubuntu 6.06** from a shipit CD to what I hoped would be a dual-boot setup about three weeks ago, I managed to lose all my **Windows** files instead. I'd like to re-install **Windows** for certain applications, but now don't wish to lose **Ubuntu**, which I've grown to appreciate, in the process. Correct partitioning is obviously the crux of the problem. First I hoped to use System&#8594;Administration&#8594;Disk Manager to check my present situation out, only to discover that, unlike in **6.06**, this option is not available in **6.10**, to which I had updated. I then downloaded **QTParted** (v0.4.5-cvs), but every time I try to run it, I am met with a message *cum* query : «No device found. Maybe you're not using root user ?» After clicking on the «OK» button, I get a panel on which most of the menus and tools, like «Operations», «Disks», and «Device» are greyed out and cannot be used. Where do I go from here ? The RootSudo [tutorial]("https://help.ubuntu.com/community/RootSudo") makes it quite clear that going back to a traditional root account is _not_ recommended ; is there anything else I can do to make **QTParted** work ? Or does anyone have any other suggestions for partitioning my 160GB harddisk and reinstalling **Windows** ? Here I require a step-by-step tutorial, so that I don't lose the results that despite my lack of experience with **Linux** I've hitherto managed to obtain in modifying and upgrading my **Ubuntu** system....

Grateful for any help,

Henri

[http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

Here's a post I wrote earlier this week to clone the drive.

Just use partimage to copy your existing ubuntu partitions.

Install windows

Install ubunu or just restore the partitions you backed up.

If restoring only youll need to reinstall grub.

---

### Post by mhenriday on 2007-01-01
> **tagra123 said:**
> [http://ubuntuforums.org/showpost.php?p=1917499&postcount=40](http://ubuntuforums.org/showpost.php?p=1917499&postcount=40)

Here's a post I wrote earlier this week to clone the drive.

Just use partimage to copy your existing ubuntu partitions.

...

Thanks for your suggestion, **tagra123** ! I proceeded to the post to which you provide a link and attempted to follow your instructions there. The result of my entering the command «sudo apt-get install partimage» in my terminal was as follows (as translated from the Swedish) :

[INDENT]Read package lists ... Finished
Build a relation tree        
Read in permissions information... Finished
The following package was automatically installed and is no longer necessary :
  libavahi-compat-libdnssd1 libsmokeqt1 ksysguardd
Use "apt-get autoremove" to delete them.
The following new package(s) will be installed :
  partimage
0 upgraded, 1 new installed, 0 to remove och 5 not upgraded.
Need to import 275kB archive.
After expansion a further 967kB disc space will be used.
Read:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) edgy/universe partimage 0.6.4-15ubuntu2 [275kB]
Imported 275kB in 1s (218kB/s)     
Choose the previously unchosen package partimage.
(Read the database ... 179243 files och directories installed.)
Expand partimage (from .../partimage_0.6.4-15ubuntu2_i386.deb) ...
Install partimage (0.6.4-15ubuntu2) ...[/INDENT]

Thus it seemed that the installation of **partimage** had been successful, and indeed, checking in the **Package Manager**, I was able to confirm that the programme was installed. But when I checked my hard disc with **GParted**, I did not find any new partitions, but rather /dev/hda1 (ext 3), /dev/hda2 (extended), and /dev/hda5 (linux-swap), precisely as before. Thus it would seem that while I have been able to install **partimage**, I have _not_ been able to install a new partion which can be expanded. What did I do wrong, and how can it be corrected ?...

Once again, I greatly appreciate any suggestions or ideas which could aid me in this matter....

Henri

---

### Post by tagra123 on 2007-01-01
> **mhenriday said:**
> Thanks for your suggestion, **tagra123** ! I proceeded to ................

Thus it seemed that the installation of **partimage** had been successful, and indeed, checking in the **Package Manager**, I was able to confirm that the programme was installed. But when I checked my hard disc with **GParted**, I did not find any new partitions, but rather /dev/hda1 (ext 3), /dev/hda2 (extended), and /dev/hda5 (linux-swap), precisely as before. Thus it would seem that while I have been able to install **partimage**, I have _not_ been able to install a new partion which can be expanded. What did I do wrong, and how can it be corrected ?...

Once again, I greatly appreciate any suggestions or ideas which could aid me in this matter....

Henri

Before doing anything print a copy of /etc/fstab and /boot/menu.list.  You may have to edit these files latter.

Partimage is installed.

Now with gparted  resize a partition to make some backup space. This is where an extra harddrive can come in real handy.

if hda2 is your home partition resize it using gparted to make some free space.  If you can get about 6 to 8 GB that should be more than enough

Take the free space created and format the free space to ext3.

lets say the newly created partition is hda6

Now if you follow the how to I wrote mount /dev/hda6 as /mnt/backup and follow the rest of the page.

This should get you images.

Boot into your normal ubuntu -- mount hda6 -- and burn the images to CD or DVD

Now you should have a copy of your working system on DVD and you can make changes knowing youll be able to restore them.

There are other examples of backing up and restoring using tar but they never seem to work without a hassle -- more trouble than re-installing.

If you google for sysrescue  cd there are also some very good instructions on that site too.

Make sure to backup the MBR and PArtition table before changing the partitions in case you need to undo your change.

Now to the real question  I'm guessing that the 3 partition consume all of the disk.

Try right clicking on a partition that has free space and use the resize option to reduce its size. This should create free space that can be turned into another partition. 

Remember the 4 primary partition limit, so make some of your partitions in an extended partition.

---

### Post by mhenriday on 2007-01-03
> **tagra123 said:**
> ...
Partimage is installed.

Now with gparted  resize a partition to make some backup space. This is where an extra harddrive can come in real handy.

if hda2 is your home partition resize it using gparted to make some free space.  If you can get about 6 to 8 GB that should be more than enough

...

The problem - or rather, _one_ of my many problems - seems to be that I find myself _unable_ to resize partitions /dev/hda2 (extended) or /dev/hda5 (linux-swap) ! When, for example, I attempt to resize the first-named by marking it and clicking on the resize/move icon, a frame telling me that both the minimum and the maximum size of the partition is 1475 MiB, i e, its present size ! None of my attempts to change these settings have succeeded. When I right click on the partition, I notice that the «format to» option is not available. When the same procedure is carried out on the /dev/hda5 partition, I am informed that the minimum size of this partition is 8 MiB, and the maximum 1475 MiB, which is the same as the present setting. Here, however, the «format to» option in the right-click menu is not disabled, and I am offered the options ext3, ext2, fat16, fat32, hfs, jfs, linux-swap (the present setting), reiser4, reiserfs, and xfs, respectively. But I cannot make it larger ! If I understand the situation aright, the reason these two partitions cannot be made larger is that the /dev/hda1 (ext3) partition takes up the whole of the rest of the disc, but this partition is locked and cannot be unmounted, as described above. Talk about **Catch 22** ! Usually, being the inquisitive type and not giving up so easily, I manage to figure my way 'round most things, but this really has me stymied ! I get the feeling that, due to my lack of familiarity with Linux systems, I'm missing something very elementary and obvious, but for the life of me, I can't figure out what it is ! So here I am, presuming on your patience and asking once again for your help....

Henri

---

### Post by bulldog on 2007-01-03
Read this and it should be clear.

[http://ubuntuforums.org/showthread.php?t=282018&](http://ubuntuforums.org/showthread.php?t=282018&)

If you have just one partition in the extended,in your case the swap,you can't resize that one,it uses the whole extended partition.

It depends on your needs how you partition a disk.

Some suggestions for disk partition.

Windows as big as you like.

Create an ext3 10GB for /
Create an extended from the rest off the space.
In the extended,
Create a /home 10GB
Create a swap 1GB
Create a ext3 partition for data if you have space left.
You have a separate /home for some data and a separate /data partition to backup important data.

---

### Post by tagra123 on 2007-01-03
> **mhenriday said:**
> The problem - or rather, _one_ of my many problems - seems to be that I find myself _unable_ to resize partitions /dev/hda2 (extended) or /dev/hda5 (linux-swap) ! When, for example, I attempt to resize the first-named by marking it and clicking on the resize/move icon, a frame telling me that both the minimum and the maximum size of the partition is 1475 MiB, i e, its present size ! None of my attempts to change these settings have succeeded. When I right click on the partition, I notice that the «format to» option is not available. When the same procedure is carried out on the /dev/hda5 partition, I am informed that the minimum size of this partition is 8 MiB, and the maximum 1475 MiB, which is the same as the present setting. Here, however, the «format to» option in the right-click menu is not disabled, and I am offered the options ext3, ext2, fat16, fat32, hfs, jfs, linux-swap (the present setting), reiser4, reiserfs, and xfs, respectively. But I cannot make it larger ! If I understand the situation aright, the reason these two partitions cannot be made larger is that the /dev/hda1 (ext3) partition takes up the whole of the rest of the disc, but this partition is locked and cannot be unmounted, as described above. Talk about **Catch 22** ! Usually, being the inquisitive type and not giving up so easily, I manage to figure my way 'round most things, but this really has me stymied ! I get the feeling that, due to my lack of familiarity with Linux systems, I'm missing something very elementary and obvious, but for the life of me, I can't figure out what it is ! So here I am, presuming on your patience and asking once again for your help....

Henri

If you boot from the live (install) cd the ext3 partition can be resized because it will not be locked.

Be patient, and you shouldn't lose any data.

Make sure to copy you most important data to a cd or something like that just in case.

---

