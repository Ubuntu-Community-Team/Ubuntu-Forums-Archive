---
title: "Upgrade from 10.04 LTS to 12.04 LTS... successes?"
date: 2013-05-29
forum: Installation &amp; Upgrades
---

### Post by WaltL on 2013-05-29
Okay, I've read several posts about this, both web-wide and here, and I know find that, in theory, going from one LTS to the next LTS via Update Manager should work fine IF your current environment is pretty much stock.  However, there seems to be more users whose opinion is "do a clean install."  The problem is that I have installed quite a number work-related programs, many of which have dependent libs that aren't found in the SPM.  It would be a real PITA to have to go back and re-install all of these from scratch (prob. ~ 20 programs).  Thus, I'm leaning towards the upgrade path.  

Two years ago I successfully upgraded from 9.04 to 10.04.4 LTS via the UM, and nothing broke! :cool:  I've added quite a bit more software since then, and I'll also be jumping over ver 11 (some folks seem to be of the opinion that you should upgrade sequentially), so I'm hesitant to get on with this... though I know I must!

So, has anyone done this _exact_ 10.04 LTS to 12.04 LTS upgrade on a box that had a lot of extra/non-standard software installed, and been pleased with the outcome?  Of course, I am going to back home my home dir. to another drive, and will also boot first into 12.04 on USB to test drive it before installing.
 
I just want to know who has done this specific upgrade path via the UM and what your result was... are you happy, or did you end up with something slow and clunky that you had to go back and perform a clean install... along with days of re-installing software?

---

### Post by ahallubuntu on 2013-05-29
I haven't done this particular upgrade path.

I've upgraded a couple of times with different versions, and the biggest problem I've had is with Grub not being installed right after the upgrade.  But booting the live USB/live CD and re-installing Grub fixed it.  (I prefer the chroot method of updating Grub but there are lots of ways to do it.)

What I suggest is: backup your current 10.04 / partition first, then TRY the upgrade.  If it fails, you can "undo" to wherever you were before the upgrade.

Alternately, if you have a spare hard drive, clone your current drive with 10.04 to that, then try upgrading the clone.

If you have a lot of data in your / partition, then backing the whole thing up could be time consuming and require a lot of space.  If you have a small / partition (maybe separate /home partition or data somewhere else), then backing it up should be pretty easy with a live CD.  These days I prefer dump and restore for this purpose.  You'll have to install them in a live CD but that should be quick.  If your / partition is for example /dev/sda1 then you'd type:

sudo dump -f - /media/MyOSPartition > BackupOS.dump

(where MyOSPartition is your mounted OS partition (in a live USB/live CD session) and BackupOS.dump would be a huge file, presumably on an external drive or something).

---

### Post by WaltL on 2013-05-29
Thanks, that's an excellent idea!  This box is MacPro that I use as a dual boot machine (95% of the time I'm in Linux).  My Ubuntu drive is 1.5 TB with ~ 800 GB data on it, so I've been backing it up as a tarball.  I have 2 other 1.5 TB internal drives I use for Linux & Mac backup, so I'll just clone to the Linux backup drive and then upgrade that.  Presumably, cloning this amount of data will be as time consuming as backing up by tar?  Also, is there a disk cloning app you'd recommend for Linux/Ubuntu?  I've used a SeaGate utility for our PCs, but never needed to ghost a drive in Linux.

---

### Post by ahallubuntu on 2013-05-29
Lately I've been cloning with Gparted.  In a live CD/live USB session with both drives attached, you can choose the original partition and do "copy" and choose the new partition (create it first with Gparted) and do "paste."  And wait a long time for the copy to complete.  The downsides of this approach are: you have to create your swap on the new drive manually (easy in Gparted) and then update the /etc/fstab in the new / partition to pick up the UUID of the new swap partition.  And: you'll have to update/install Grub on the new drive.  I prefer the chroot method.  It's nice to know how to do this, anyway, though.

You can try cloning with Clonezilla - a stand-lone boot disk - but I've had poor luck with it.  The commercial software True Image from Acronis also supports Linux cloning these days pretty well, if you have access to a copy.

I've learned to move my data into a separate partition from the OS (from "/") so that cloning the OS is only a few GB of data and is very quick.  Then I can copy my data partitions with rsync - but in a case like yours, you wouldn't even need to copy the data.  Just a suggestion for the future.  Another suggestion for the future: learn about LVMs.  If you have your OS partition in an LVM, you can make a snapshot of it live while booted and clone or backup the snapshot, without requiring a live USB/live CD.

---

### Post by WaltL on 2013-05-30
One of our sys admins advised me not to clone the disk and, instead, make a dump file on the other drive to restore from, and then go ahead with the upgrade...  I did this, and it croaked during the installation of the packages. The mouse locked and the dialog box had 4 rows of small squares in it.  I'm starting another thread to see if I can get some help to repair.  Great sadness!

---

