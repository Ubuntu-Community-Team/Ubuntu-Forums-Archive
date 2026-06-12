---
title: "Problem installing ubuntu 7.10 with IDE&amp;SATA H.D"
date: 2008-01-15
forum: Installation &amp; Upgrades
---

### Post by Spootnik on 2008-01-15
Hello all,
I'm new at Ubuntu scene i got a problem with installation ubuntu on IDE H.D
I got 2 H.D.
The first one is Western Digital  80G IDE - Primary (Got xp on it)
The 2nd one is Western Digital 250G SATA2 -  SLAVE (Got Ubuntu on it)
when i installed ubuntu it didnt even showed the IDE drive,
how can i fix it?.
thanks a lot.
Best regards,  Igor Bekerman.:)

---

### Post by iiibill on 2008-01-16
I suspect that there really is no problem.  By default the install only uses one disk.  When the install is complete it is up to you to mount any other disks you want to use.  I expect that with the installation on the data drive that if you do a df you will see a devices like /dev/sdaN, where N is the partition number.

To use the second disk you will need to make sure it has a partition table, create a file system, and mount the disk.  Here is an over view of the steps:

 1. Create a partition table with fdisk.  The command that you will want to use is
     "disk /dev/hda".  The utility has help and menus so you should be able to 
     figure out what to do.

 2. Create a file system.  You can use something like e2fs /dev/hda1.  I would 
     recommend that you you created a journaled ext3 file system.  It is simple
     and reliable.   The command would be "e2fs -j /dev/hda1".

 3. Mount the disk.  You will want to do this manually first.  Here are the steps:

      a. Create a directory to use as a mount point.  Something like "mkdir /disk1"
          will work.
      b. Issue the mount command "mount /dev/hda1 /disk1"

 4. Modify /etc/fstab to add the mount of your second disk so it is mounted at 
     boot.

You need to so these commands as root or using sudo.  Oh, yes, I am assuming that you can use the command line, i.e. the terminal application.  There might be a GUI, but I can't help you there.

Bill

---

### Post by iiibill on 2008-01-16
Sheeeeze, I just re-read the original post.  If you have data on that disk you are trying to access you want to stay away from fdisk and e2fs, that will destroy the data.  Just figure out how to mount the disk.  Spend some time reading "man mount" and experiment manually mounting the disk.  Then add the correct entry into /etc/fstab once you know what works.  The only tricky part will be figuring out what the file system it, I expect NTFS.

Sorry about the misdirection.  Course, if it was me any disk with Windows on it doesn't have anything important anyway---an fdisk would fix it just fine for my purposes.  ;-)

Bill

---

