---
title: "Copy OS while using it ...??"
date: 2021-06-13
forum: Installation &amp; Upgrades
---

### Post by anneranch on 2021-06-13
This is silly - but - after downloading and running "clonezilla" it became obvious I cannot use it from running OS. 
To clone real  working OS  I have to run another copy of OS ....
In essence I have to have two good  OS to use "clonezilla".

Is there a "smarter " copy / clone / duplicate  software to work FROM running OS and copy OS ?

---

### Post by dddman on 2021-06-13
To copy an OS while using it is called syncing, not cloning.  Clone requires the partition/drive to be unmounted (not in use) and does not require a second OS to be installed.

Sync can be used to clone, but clone cannot be used to sync.

Do a search on "syncing vs cloning"

---

### Post by grahammechanical on 2021-06-13
> Once you get Tuxboot installed, use it to create your nice live bootable  Clonezilla USB stick. First create a FAT32 partition of at least 200  megabytes; figure 1 (above) shows how it&#8217;s done in GParted. I like to  use labels, like &#8220;clonezilla&#8221;, so I know what it is. This example shows a  2GB stick formatted as a single partition.

[https://www.linux.com/training-tutorials/how-image-and-clone-hard-drives-clonezilla/](https://www.linux.com/training-tutorials/how-image-and-clone-hard-drives-clonezilla/)

So, it seems that Clonezilla is run from a USB stick to clone and non-working OS on the hard disc. 

> The size of your destination partition or drive must be the same size or larger than the volume you&#8217;re copying.

Regards

---

### Post by dddman on 2021-06-13
Quote
> So, it seems that Clonezilla is run from a USB stick to clone and non-working OS on the hard disc
It can also be added to the grub boot menu, bypassing the OS at boot.

---

### Post by TheFu on 2021-06-13
You can freeze blocks on a running OS using LVM or ZFS snapshots.

Otherwise, the solution is to boot from flash media with a "Try Ubuntu" option or keep a minimal install on a 2G partition with just the tools you want for cloning.

In general, image-based backups are better used for Windows, not Linux.  On Linux, we'd use file-based backups which can be versioned with greater efficiency, drastically shorter times, and much, much, much, less storage.

But if you gotta clone, then you gotta clone.

---

### Post by dddman on 2021-06-13
TheFu> But if you gotta clone, then you gotta clone
I am coming up with less and less reason to clone.  Maybe for something I need to stick in the desk drawer.  I was going to clone my first drive to my second, but crap.  I have hard enough time keeping up with snapshots (vbox), sync keeps me up to date without the bother.  And yes, there are other considerations.  I currently sink Ubuntu thru virtualbox thru windows to my second drive.  Could it get any crazier?  I'm working on it.

---

### Post by scorp123 on 2021-06-13
> **anneranch said:**
>  To clone real  working OS  I have to run another copy of OS ....
In essence I have to have two good  OS to use "clonezilla".

Live sessions (e.g. Ubuntu CD or USB stick that you used to install the OS) would work too. And there's also "CloneZilla Live":
[https://clonezilla.org/clonezilla-live.php]("https://clonezilla.org/clonezilla-live.php")

You boot that up and let it clone your actual OS. Voila, done.

---

### Post by TheFu on 2021-06-13
> **dddman said:**
> TheFu
I am coming up with less and less reason to clone.  Maybe for something I need to stick in the desk drawer.  I was going to clone my first drive to my second, but crap.  I have hard enough time keeping up with snapshots (vbox), sync keeps me up to date without the bother.  And yes, there are other considerations.  I currently sink Ubuntu thru virtualbox thru windows to my second drive.  Could it get any crazier?  I'm working on it.

Most people want a 1-trick solution.  The problem with that is size, time, and inefficiencies.  1 backup command to rule them all is full of inefficiencies.

Only time I clone is when a HDD is failing and I have an identical replacement. Then I use ddrescue. 
Otherwise, I use file-based, versioned, backups with a mix of LVM snapshots, a few data gathering scripts pre-backup, rdiff-backup from a backup server to "pull" the backups (CRITICAL!!!!), then some post-backup scripts to delete snapshots that aren't needed anymore.  All the while, the system was working, doing what it was supposed to do.  These backups have been automated for a long time. Versioned backups happen nightly for all but 1 system, which gets backed up every other day.  I do not backup the OS, just the settings, data, list of installed packages and personal settings, data, and manually installed software ... like AppImages and compiled programs.

I've posted my backup times about 20 times in these forums for almost all my systems.  They run from 20 seconds to about 10 minutes. Those are for the versioned backups. Because rdiff-backup uses a reverse-incremental backup strategy, the last backup looks like a mirror - just like what we'd have for an rsync backup, but older "versions" capture only the differences.  File differences are captured as diff.gz files.  Owner, group, permissions, xattr differences are captured in metadata files as needed.  This second part is where most rsync or hardlink-based versioned backups fail. They only retain the last owner, group, and permissions.  About 12 yrs ago, I was burned by this.  Never again.

I've posted example backup sizes about 5 times in these forums too.  For 60 days of versioned backups, the storage size usually increases 15-20% over the source amount.  So, if we are backing up 10G of stuff, 60 days of versioned backups would only need 12G of storage.  Seems like a bargain to me.

When backups take 1-2 minutes and don't eat up lots of storage, they are easier to run, easier to automate, and we'll do them without worry about running out of space on the backup storage.  The downside is that we have to know what actually needs to be backed up.  Took me about 5 attempts before I got down to exactly what was needed for a successful restore.  Once I had 1 system doing that well, all the others sorta dropped into line and only the snowflake aspects need much consideration.  
I do not backup the OS. 
I do not backup the boot files.
My goal at restore time is to end up with a system that looks like the backup I restore, not bit-for-bit exactly the same.  I just want the programs and data to be the same.  That simplifies and drastically reduces all sorts of things most people backup that just aren't necessary.  It also means that my restores begin from a minimal OS install.  THAT means the underlying storage, motherboard, CPU, and most other hardware can be modified without much risk.  I've used the restore to migrate from 32-bit to 64-bit OS installs.  I've moved machines. It all works.  Sorta like how virtual machines decouple the VM from the actual hardware, my backups decouple the backups from the exact OS.  If I stay within the same family of OS - "ubuntu" - then all will likely be just fine.

---

### Post by anneranch on 2021-06-13
First of all - did anybody actually  read my original post ?
A correct answer would have been - no. 

Secondly 
There  must be a difference between "backup"  and copy / duplicate/ clone  **Operating SYSTEM** .

Thirdly any other speculations... no comment

---

### Post by QIII on 2021-06-13
Then, "No."

To avoid the risk of enmity and rancor, closed.

---

