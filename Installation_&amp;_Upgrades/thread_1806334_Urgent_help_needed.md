---
title: "Urgent help needed"
date: 2011-07-17
forum: Installation &amp; Upgrades
---

### Post by Shinokaze on 2011-07-17
I had some trouble with my installation of Ubuntu 10.4 so I decided to re install the OS. (I have my /home on a separate partition)

[ntfs] [ntfs] [ext3/home] [ubuntu] [swap]

I re installed Ubuntu on the partition I set aside for the OS. Ubuntu installed, everything works as it should but now all the contents my Home folder is gone! I did not set any options that would of formatted the /home partition during installation I only set the partition to be used for home selecting [use this partition]

I suspect that Ubuntu set the home folder back to the way it comes out of the box

So my question; I need to recover this drive, its so important that its life or death! How can I recover this partition and the files that where on this drive?!

Thank you and advance and please help!

---

### Post by Dangertux on 2011-07-17
Have you tried mounting the old /home partition and copying the files? (this is assuming it wasn't encrypted, if it was you might be stuck)

---

### Post by Shinokaze on 2011-07-17
I've been reading around and it seems there are other steps in mounting your old /home to your new /home during a fresh install of ubuntu but I haven't seen anything that explains this step-by-step

and I don't believe the partition /home from my previous install was encrypted.

---

### Post by Mr.Kappa on 2011-07-17
Go to System -> Users . Click Advanced Settings and selected the last tab (Advanced). There you will find the "home directory". Write down the path to your home partition (like media/sd* or whatever). Remember that your home partition must be mounted automatically at every machine boot otherwise you will not be able to login!!

Hope this helped!

---

### Post by Shinokaze on 2011-07-17
I followed your directions Mr.Kappa, my home directory is /home/patricia but not sure what to do from there.

Let me explain what happened again a little more clearly.

my partitions are setup like this.
[NTFS][NTFS][/HOME][UBUNTU][SWAP]

Everything was fine up till I made some adjustments and decided to re install Ubuntu. I followed the prompts of the live cd as I've done before and chose to set up my partitions manually. I left the [NTFS]'s untouched set [/HOME] with the options (use this partition) and (do not format) I set [UBUNTU] with the option / (format) then continued with the installation. the installation completed without error and booted into my fresh install. I went to places>home folder and noticed that all my photo's, Documents and other important files were not there as they were on my previous install.

I did not tell the liveCD to format my /home partition. I just assumed that Ubuntu would leave all my files intact and they would be there when I finished the installation...

help?...

---

### Post by Mr.Kappa on 2011-07-18
If you didn't format your home partition then it's still there. 
Use ```
sudo mount -a
``` to mount every partition you have and then search for the home partition, or you can use the Disk Utility.
You have look how that partition is mounted (if it's mounted) then you have 2 options:

[LIST=1]
[*]Point to home directory to where the home partition is mounted (like I told you before)
[*]Edit your /etc/fstab file to mount the drive in your home folder (/media/sd* to /home )
[/LIST]
If you choose the second option be sure to move everything you put in the "new" home folder because when the drive is mounted in the directory it wipes every else.

If you have other doubts (after my explanation I'm sure you'll have them) don't hesitate to ask before doing anything!

---

### Post by steve11911 on 2011-07-19
Because data recovery is so important here you might consider:

The Ultimate Boot CD which has been around awhile...

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

and contains a tool for data recovery:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I'll cross my fingers for you...

---

### Post by Shinokaze on 2011-07-27
> steve11911	
Re: Urgent help needed
Because data recovery is so important here you might consider:

The Ultimate Boot CD which has been around awhile...

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

and contains a tool for data recovery:

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

I'll cross my fingers for you...

Ok, Think I may try that if this one last thing don't work


> If you didn't format your home partition then it's still there. 
Use
Code:
sudo mount -a
to mount every partition you have and then search for the home partition, or you can use the Disk Utility.
You have look how that partition is mounted (if it's mounted) then you have 2 options:
Point to home directory to where the home partition is mounted (like I told you before)
Edit your /etc/fstab file to mount the drive in your home folder (/media/sd* to /home )
If you choose the second option be sure to move everything you put in the "new" home folder because when the drive is mounted in the directory it wipes every else.

can you give me a step-by-step? and I think I tried editing my fstab. I added a line using the UUID and used a comment to unmount the other /home entry in fstab. but Im sure I may have made a mistake so I'll try again when I get home. I'll play around with that till I hopefully get a reply back to make sure I'm doing it right, thanks

---

### Post by Mr.Kappa on 2011-07-27
Can you post here your fstab? Also post the output ```
sudo fdisk -l
```

---

### Post by YesWeCan on 2011-07-27
It is a bit confusing.
Have you tried booting from live CD and mounting the home partition to see if your files are still there?
Just boot from CD and look for the partition in Places.

If your files are there then we need to check why the new Ubuntu installation is not mounting this partition.
The entry in fstab may not be correct.
Post the outputs of
sudo blkid
cat /etc/fstab

---

### Post by Shinokaze on 2011-07-27
**results of blkid**
```

patricia@patricia-laptop:~$ sudo blkid
/dev/sda1: LABEL="PQSERVICE" UUID="449475B59475AA56" TYPE="ntfs" 
/dev/sda2: LABEL="SYSTEM RESERVED" UUID="6ED8761AD875E12F" TYPE="ntfs" 
/dev/sda3: LABEL="Gateway" UUID="1C5495555495328E" TYPE="ntfs" 
/dev/sda5: UUID="fe2baf5f-ee77-4f57-9811-5c58f4195306" TYPE="ext3" 
/dev/sda6: UUID="c70a3101-0ac2-495e-a48d-9357944be231" TYPE="ext3" 
/dev/sda7: UUID="cf9cb54a-523d-4884-a9ab-b47df674d5ef" TYPE="swap"
```[B]
contents of etc/fstab[/B]
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext3    errors=remount-ro 0       1
/dev/sda5       /home           ext3    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=cf9cb54a-523d-4884-a9ab-b47df674d5ef none            swap    sw              0       0

```[B]

results of sudo fdisk -l[/B]
```

Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1567    12586896   27  Unknown
/dev/sda2   *        1568        1580      104422+   7  HPFS/NTFS
/dev/sda3            1581       12023    83883397+   7  HPFS/NTFS
/dev/sda4           12024       60802   391810049    5  Extended
/dev/sda5           12024       49850   303840256   83  Linux
/dev/sda6           49850       60293    83881984   83  Linux
/dev/sda7           60293       60802     4085760   82  Linux swap / Solaris

```[B]

results of sudo mount[/B]
```

patricia@patricia-laptop:~$ sudo mount
/dev/sda6 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda5 on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/patricia/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=patricia)

```

---

### Post by YesWeCan on 2011-07-27
That all looks ok. Or not ok if you are unable to find your files.
I was wondering whether, if you boot offlive CD/USB you can mount sda5 and see any of your files? This may be redundant but is a second chance to see if you files have been erased or not.

Otherwise its recovery tool time, as steve suggested. There are other tools too: you may wan to do a search. I think member coffeecat once mentioned one to me.

---

### Post by Mr.Kappa on 2011-07-28
I agree with yeswecan..unfortunately there's nothing wrong in the mounting procedures. Maybe you should look here for more info about recovering lost partitions [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition) if booting with a live session doesn't bring up anything.


Ps remember to NOT write on your home partition!!

---

### Post by Mr.Kappa on 2011-08-03
Did you solve your issue??

---

