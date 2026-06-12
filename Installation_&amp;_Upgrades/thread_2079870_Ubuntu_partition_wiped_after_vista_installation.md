---
title: "Ubuntu partition wiped after vista installation"
date: 2012-11-02
forum: Installation &amp; Upgrades
---

### Post by Dom8trix on 2012-11-02
Hi, I have a problem with my Ubuntu partition. I will describe the system I had, then describe the problem as best I can:

My laptop is a Dell Inspiron 1525, 250Gb HDD. The setup I had was a partitioned drive with Windows Vista/Ubuntu 10.04. Vista was on one half, Ubuntu on the other half. 

Two weeks ago, I tried to install visual studio on Vista, which was halted by the lack of service pack 1 for Vista. I then began the update of service pack 1; all went smoothly, restarted the laptop to finish updates and upon restart.... black screen of death (some sort of registry error it seemed). 

After several boot recovery trials and attempting to fix the problem from the Vista disk, I was finding no solution. I however was still able to access Ubuntu partition from boot menu - everything was fine with Ubuntu at this point. I then did something very silly... I gave up hope on the dead Windows Vista partition and created a new partition in un-allocated disk space and installed Vista there. I did this because I didn't want to overwrite the old Vista partition and risk losing all the stuff I have on there, so I figured I could create new partition, access stuff from old partition and transfer across, then delete old partition. 

However, I then tried something I hadn't tried on the old partition yet - a system restore. I Used the windows disk to get into restore mode, started system restore, and boom! It worked, old partition back to how it used to be, everything sorted. Except... Boot menu had changed - no Ubuntu there. 

Now the problem is, I don't know if the system restore caused this problem of Ubuntu disappearing, or if the installation of new Vista partition caused it (more likely in my opinion).

Using windows I can see that the Ubuntu partition is still there, however the partition is empty, except for a file called 'lost + found'. 

Another partition is also present when I run testdisk, which is a FAT32 type, and contains linux files, and it contains a lot of deleted files. 

I have tried restoring the partition to no avail. Any help would be appreciated, I can give more details of anything people would like to know if it helps. 

Thanks in advance, sorry for the long winded explanation! Hope it got the point accross!

Dom

---

### Post by dannyboy79 on 2012-11-02
i would just try to install grub again and see if it picks up your ubuntu install.

---

### Post by Mark Phelps on 2012-11-02
> **Dom8trix said:**
> Now the problem is, I don't know if the system restore caused this problem of Ubuntu disappearing, or if the installation of new Vista partition caused it (more likely in my opinion).
Most likely, it rewrote the MBR of the drive, removing the fragment of GRUB code there.  So, when you rebooted, there was nothing to direct you to Ubuntu.

> Using windows I can see that the Ubuntu partition is still there, however the partition is empty, except for a file called 'lost + found'. Windows can NOT read Ubuntu partitions, so, it can't be used in the manner you tried.  To read the Ubuntu partitions, you need to boot from an Ubuntu LiveCD or LiveUSB. I would do this before you presume that the Ubuntu files are gone.

---

### Post by Dom8trix on 2012-11-02
From the ubuntu live CD I can access the Ubuntu partition and it is still empty except for lost+found.

---

### Post by darkod on 2012-11-02
Boot the ubuntu cd in live mode and post the output of:
sudo parted -l (small L)

Lets see if the ubuntu partition is there at all. In most cases running the system restore will redo the machine like it came from factory, which means deleting the ubuntu partition. It all depends how the restore process works.

That's why in most cases those partitions are useless since nobody wants all of the other partitions deleted.

---

### Post by Dom8trix on 2012-11-02
I didn't do a full system restore, I just restored windows to a previous point before Sp1 installation. I'll post above output in a moment...

---

### Post by Dom8trix on 2012-11-02
OUTPUT:
ubuntu@ubuntu:~$ sudo parted -l
Model: ATA WDC WD2500BEVT-7 (scsi)
Disk /dev/sda: 250GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      115MB   3339MB  3224MB  primary   fat32
 2      3339MB  143GB   139GB   primary   ext3
 3      143GB   217GB   74.3GB  primary   ntfs
 4      217GB   250GB   32.9GB  extended
 5      217GB   248GB   30.9GB  logical   ntfs
 6      248GB   250GB   2065MB  logical   linux-swap(v1)


Model: TSSTcorp DVD+-RW TS-L632H (scsi)
Disk /dev/sr0: 4700MB
Sector size (logical/physical): 2048B/2048B
Partition Table: msdos

Number  Start  End     Size    Type     File system  Flags
 1      131kB  2916MB  2916MB  primary               boot, hidden

---

### Post by darkod on 2012-11-02
So, if you open the 139GB partition, /dev/sda2, it's empty?

---

### Post by Dom8trix on 2012-11-02
Yup, it is empty, except for the lost+found folder.

---

### Post by funicorn on 2012-11-02
I'm afraid you need  to describe more clearly what you exactly have done, which I noticed you already tried on  though. For example:

[LIST]
[*] > Using windows I can see that the Ubuntu partition is still there,  however the partition is empty, except for a file called 'lost + found'.
[/LIST]
How exactly did you do that, i.e., to find out under windows that a linux partition is empty left with only a file 'lost+found'? What kind of file browser did you use ? 


[LIST]
[*]How did you exactly restore Vista OS? what kind of system restoring tool did you use ?  Is the  system recovery based on partition-to-partition clone procedure ?
[/LIST]

[LIST]
[*]After you installed a new Vista OS in a newly created partition, did you reboot the computer and tried to enter Ubuntu BEFORE you did the restoration ?
[/LIST]
To clarify on these issues should be helpful to identify what status you are stuck to .

---

### Post by darkod on 2012-11-03
If ubuntu can open the partition and sees it as empty, I don't have high hopes honestly.

It's one thing if a partition is "gone, deleted" in which case you can try bringing it back and see if the files are there.

But when the partition is actually still there, with the same size as it originally was and the same location on the disk, and it sees it as empty, I don't like that.

I agree, this might not have been done with the system restore you did, but with the second installation you did. For example, where are the two vista installs right now? You have only one primary ntfs partition and that's #3. But for two vista installs you would usually have two primary ntfs partitions. Is the other vista #5?

The partitions might have been messed up during the second vista install, especially since windows and its partitioner don't understand linux partitions very well.

---

### Post by Dom8trix on 2012-11-05
Hi funicorn, to answer your questions - 

Oops I was wrong in my description, I accessed the ubuntu partition through ubuntu live CD NOT through windows, my bad. 

I restored windows vista using the vista cd, and went into repair mode and used the 'restore operating system to a previous time' option. I restored vista to the point in time just before I began the upgrade of service pack 1. So this was infact not a system recovery, just a restore of vista. 

Yes I think I did try enter ubuntu before I did the restoration, and again, it did not appear in the boot menu.

---

### Post by Dom8trix on 2012-11-05
> **darkod said:**
> If ubuntu can open the partition and sees it as empty, I don't have high hopes honestly.

It's one thing if a partition is "gone, deleted" in which case you can try bringing it back and see if the files are there.

But when the partition is actually still there, with the same size as it originally was and the same location on the disk, and it sees it as empty, I don't like that.

I agree, this might not have been done with the system restore you did, but with the second installation you did. For example, where are the two vista installs right now? You have only one primary ntfs partition and that's #3. But for two vista installs you would usually have two primary ntfs partitions. Is the other vista #5?

The partitions might have been messed up during the second vista install, especially since windows and its partitioner don't understand linux partitions very well.

Yes I fear you may be right. And yes, the second vista installation is #5. The original vista is as you say, #3. I think somehow, the second vista installation has wiped the ubuntu partition completely, no idea how or why! Oh well, I will keep trying a bit more to resolve this, but I think it's highly likely I will just have to reinstall ubuntu and accept I have lost all my old files. 

Thanks for all help so far, greatly appreciated.

---

### Post by darkod on 2012-11-05
> **Dom8trix said:**
> Yes I fear you may be right. And yes, the second vista installation is #5. The original vista is as you say, #3. I think somehow, the second vista installation has wiped the ubuntu partition completely, no idea how or why! Oh well, I will keep trying a bit more to resolve this, but I think it's highly likely I will just have to reinstall ubuntu and accept I have lost all my old files. 

Thanks for all help so far, greatly appreciated.

Well, I have one idea but no evidence. Windows doesn't really understand linux partitions, and if you tried to shrink or modify the ubuntu partition in order to create space for the new vista installation (you have to install it somewhere), then it's very probable it will mess up the partitions it tries to touch.

Don't forget to always modify linux partitions with linux tools.

---

### Post by funicorn on 2012-11-05
That's wired. windows installation in a logical partition will copy boot files and/or set env's onto the primary partition in which another windows resides. Generally speaking such primary partition should be marked with a boot flag. But there is no boot flag on any of your primary partitions based on the partition table you pasted.

If there is no boot flag on any of the partitions you cannot boot windows via windows boot loader, unless you are using a grub boot loader which does not need a boot flag. So this makes me wonder what is the boot menu you see now when your computer is starting up. It's can't be the grub boot menu right ? because grub partition was wiped so was grub.

---

### Post by Dom8trix on 2012-11-07
The boot loader I see is the windows boot loader (I think). It just shows the two windows partitions and an old neo-Grub option which is obsolete.

---

