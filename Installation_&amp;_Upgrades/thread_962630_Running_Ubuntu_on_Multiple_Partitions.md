---
title: "Running Ubuntu on Multiple Partitions"
date: 2008-10-29
forum: Installation &amp; Upgrades
---

### Post by aajax on 2008-10-29
I have it in mind to setup my computer to run Ubuntu on multiple partitions with somewhat the same philosophy that I've always used with Windows.  The basic idea is to define 3 types of storage as follows:

1.  Software and other static information that is needed to make the system run and that is recovered by restoring an image of the partition.  It is worth noting that I like to have more than one of these on the same computer in order to have a way to experiment with new applications/software without risking loss of the stability associated with a well functioning tried and proven system.  These would be bootable (root) partitions.
2.  Storage area for temporary files.  These are files that require no backup.  It is desirable to keep such files out of the partition images that are created in order to economize on the size of image files as well as to improve the performance of image creation and restoration.  In Windows this is a good place for the principal paging file.  In Linux it looks like the use of separate swap partition/s is prescribed but these partitions cannot be used for anything else.
3.  Storage area for files that I create.  These files need to be backed up.  While images can be used it is preferable to create archives that allow subsystems or databases to be backed up at those times that are appropriate for each kind of activity/subsystem.

Category 2 & 3 are such  that the same partitions can be used with different instances of category 1.  In that, I may have multiple different bootable systems (partitions) that would mount the same partitions (file-systems) for category 2 & 3.

It looks to me like /tmp is a good candidate for category 2 above and that some subset of /home is a good candidate for category 3.

Some concerns/questions follow:

1.  Insofar as /home defines storage that is controlled at the user level, how important is it to have the same users defined on all of the systems that might mount this file-system?  Are the numeric (binary) uid's what matters?  In that if a user named Aaron is uid=1000 on System A and a user named Erin is uid=1000 on System B would they each have access to the files associated with uid=1000 on a separately mounted file-system?

2.  It seems that the desktop systems (GNOME/KDE) opt to store a lot of settings in the respective users subdirectory of /home.  Therefore, it would seem like a bad idea to separate these files form the root partition/s (i.e., Category 1 above).  Does anyone have a suggestion about how this should be done?  To do this some technique for mounting the Category 3 file-system and linking it subdirectories of /home would seem to be needed.  Is there a recommended technique (i.e., good practice)?

3.  What have I failed to recognize?

---

### Post by lemming465 on 2008-10-30
> **aajax said:**
> I have it in mind to setup my computer to run Ubuntu on multiple partitions ...

Perfectly reasonable; I do it myself.

> 1.  ...  bootable (root) partitions.

One per OS, minimum recommended size 12 GB.

>  2.  Storage area for temporary files...

Depending on your partitioning strategy, you could make /tmp be separate and shared, though I'm not sure it's worth it.  Sharing swap partitions is pretty easy, and will tend to happen by default; let it.  You can make swap files inside a partition formatted with, say, ext3, but there won't be a net space savings, and it's more work, so unless you are bumping up against the 16 partition per disk limit, don't bother.  Minimum swap space is around 20 MB; my recommendation is 2X memory up to about 2GB, and perhaps 1.5X memory or memory + 1 GB beyond that.

> 3.  Storage area for files that I create... 

> 1.  Insofar as /home defines storage that is controlled at the user level, how important is it to have the same users defined on all of the systems that might mount this file-system?  Are the numeric (binary) uid's what matters?  In that if a user named Aaron is uid=1000 on System A and a user named Erin is uid=1000 on System B would they each have access to the files associated with uid=1000 on a separately mounted file-system?

Yes, shared access is controlled by numeric UID/GID.  Root can access anything, of course.  This can either be a help if you are trying to share, or a hindrance if you are not.  Different systems may not create the same UID's by default, but you can insist on that with some effort.  If all else fails, brute force with vipw, vigr, and chown -R works wonders.

> 2.  It seems that the desktop systems (GNOME/KDE) opt to store a lot of settings in the respective users subdirectory of /home.

Yes, and furthermore it's not a good idea to share a user's home directories between different OS's, because the per-user configuration data for Gnome and other applications tends not to be compatible between different versions.  You can still share a single /home partition if you make differently named users for the different OS installs. Otherwise not making /home be on a separate partition so each OS has its own private set of home directories also works.

Sharing data partitions is not a problem, as long as you don't get too exotic with the filesystem choices.  E.g. not everything can do reiserfs, or ext4, or ntfs, but pretty much everything will do ext3 and vfat32.

How you do the partitioning varies depending on your purposes.  I run a lot of home and experimental Linux installs with one giant root partition plus a swap partition.  But some of my servers have 15+ partitions, with separate / /boot /home /usr /var /tmp /usr/local /opt and various server specific things, with complex disk layouts involving hardware RAID, software RAID, LVM, etc.

---

