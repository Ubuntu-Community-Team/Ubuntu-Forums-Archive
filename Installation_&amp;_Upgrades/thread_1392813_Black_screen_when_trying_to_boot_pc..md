---
title: "Black screen when trying to boot pc."
date: 2010-01-28
forum: Installation &amp; Upgrades
---

### Post by SusieSA on 2010-01-28
Last weekend, I upgraded my old PC and installed Ubuntu 9.10 on a brand new pc.  It worked perfectly for 5 days.

When I got home tonight, it wouldn't boot and got stuck on a black screen.  

So I picked the 
Ubuntu, Linux 2.6.31-17-generic-pae (recovery mode)
option and got the following messages:
[FONT="Arial"][FONT="Courier New"][SIZE="3"][SIZE="2"][SIZE="1"][SIZE="2"]
Begin: Loading essential drivers... ...
Done.
Begin: Running /scripts/init-premount... ...
Done.
Begin: Mounting root file system... ...
Begin: Running /scripts/local/top
Done.
Begin: Waiting for root file system... ...
Done.
Gave up waiting for root device.  Common problems:
 - Boot args (cat /proc/cmdline)
  - Check root delay = (did the system wait long enough?)
  - Check root = (did the system wait for the right device?)
 missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/disk/by-uuid/a34ae23e-edb8-4006-a9e8-ab0767f6005c does not exist.  Dropping to a shell!

BusyBox, v1.13.3(Ubuntu 1:1.13-3-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built in commands.
(initramfs)[/SIZE][/SIZE][/SIZE][/SIZE][/FONT][/FONT]



So I had a look at the forums and found all sorts of great help, but haven't sorted the problem.  

I think this is telling:



ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda5: UUID="3066c1de-e3b7-47a2-82ce-55ae0eb48552" TYPE="swap" 
ubuntu@ubuntu:~$ cd /dev/disk/by-uuid
ubuntu@ubuntu:/dev/disk/by-uuid$ ls
3066c1de-e3b7-47a2-82ce-55ae0eb48552
ubuntu@ubuntu:/dev/disk/by-uuid$ ^C
ubuntu@ubuntu:/dev/disk/by-uuid$ 
ubuntu@ubuntu:/dev/disk/by-uuid$ ln -s 3066c1de-e3b7-47a2-82ce-55ae0eb48552 /dev/disk/by-uuid
ln: creating symbolic link `/dev/disk/by-uuid/3066c1de-e3b7-47a2-82ce-55ae0eb48552': File exists
ubuntu@ubuntu:/dev/disk/by-uuid$ 



I really am a newby here but I think that the blkid command gives me my uuid.  The uuid in the /dev/disk/by-uuid directory is in blue so I'm guessing that this is a symbolic link.  And then, when I try to create a symbolic link with the ln command, it already exists... doh!

But the issue is that the UUID that is referenced in the error displayed is not the same as the UUID in my /dev/disk/by-uuid directory.

Is this my problem and how do I fix it?

Thank you!

---

### Post by SusieSA on 2010-01-28
Here's some more info.

Other posts have asked to try running this command (and similar):

sudo mount /dev/sda1 /mnt 


When I type this command, I get the following error:

mount: you must specify the filesystem type

---

### Post by scratman on 2010-01-28
Try this..

Open a terminal and type: ```
sudo gedit /etc/usplash.conf
```

Enter your password, and Gedit should open displaying something along the lines of:-

# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1280
yres=1024

Or maybe just:

# Configuration file Usplash
# These parameters will only apply after running update-initramfs.


Sets Xres and Yres the resolution you want, for example 1024 × 768.

# Configuration file Usplash
# These parameters will only apply after running update-initramfs.
Xres = 800
Yres = 600

And save your changes.

Now your initramfs for the changes to take effect:  ```
sudo update-initramfs -u
```

When you restart your computer, it should display the new resolution at boot.

---

### Post by SusieSA on 2010-01-28
Thank you for your response.

Oh my goodness - is this really a resolution issue?

The only problem that I had when installing 9.10 was a resolution problem and I updated some .conf file (according to some other post) which sorted out the resolution.

OK - I've managed the gedit part of your reply.

But when I run the second part:
ubuntu@ubuntu:~$ sudo update-initramfs -u
update-initramfs is disabled since running on read-only media


To be able to run Ubuntu at all, I had to boot my pc using the installation CD.  Could that be part of the problem?

---

### Post by SusieSA on 2010-01-28
I wonder if this helps anybody.  I had a look at 
[http://ubuntuforums.org/showthread.php?t=1325788&highlight=sudo+update-initramfs+read+media](http://ubuntuforums.org/showthread.php?t=1325788&highlight=sudo+update-initramfs+read+media)

And got the following boot information:

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d826e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   468,519,659   468,519,597  83 Linux
/dev/sda2         468,519,660   488,392,064    19,872,405   5 Extended
/dev/sda5         468,519,723   488,392,064    19,872,342  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda5        3066c1de-e3b7-47a2-82ce-55ae0eb48552   swap                                     

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

aufs             /                aufs       (rw)
/dev/sr0         /cdrom           iso9660    (rw)
/dev/loop0       /rofs            squashfs   (rw)

---

### Post by SusieSA on 2010-01-28
I've been reading so many posts about a similar problem.  I really cannot find any solution.  A resolution issue is not suggested in any of the replies.  How do you know this is a resolution problem?

If I reinstall 9.10 from the CD, what happens to all my files / data / email?

---

### Post by presence1960 on 2010-01-28
> **SusieSA said:**
> I wonder if this helps anybody.  I had a look at 
[http://ubuntuforums.org/showthread.php?t=1325788&highlight=sudo+update-initramfs+read+media](http://ubuntuforums.org/showthread.php?t=1325788&highlight=sudo+update-initramfs+read+media)

And got the following boot information:

============================= Boot Info Summary: ==============================

 [COLOR="Red"]=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
sda1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''
[/COLOR]
sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000d826e

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   468,519,659   468,519,597  83 Linux
/dev/sda2         468,519,660   488,392,064    19,872,405   5 Extended
/dev/sda5         468,519,723   488,392,064    19,872,342  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda5        3066c1de-e3b7-47a2-82ce-55ae0eb48552   swap                                     

============================ "mount | grep ^/  output: ===========================

Device           Mount Point      Type       Options

aufs             /                aufs       (rw)
/dev/sr0         /cdrom           iso9660    (rw)
/dev/loop0       /rofs            squashfs   (rw)
It is not a resolution problem. See red in quoted text above. Your ububtu root partition has become unmountable. Boot the Ubuntu Live CD and choose "try ubuntu without any changes". When the desktop loads open a terminal and run ```
sudo e2fsck /dev/sda -y -f -v -c
```
This will run a filesystem check and hopefully correct your errors on that filesytem.

---

### Post by SusieSA on 2010-01-29
Thank you for the response presence1960 and sorry to take so long to respond.  I eventually had to go to bed (feeling rather panicked that I hadn't been able to do any of the work I intended to do on my pc!)

I tried the above command and this is what happened:

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda -y -f -v -c
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?


How does a filesystem become unmounted?
I'm sure we're getting closer...

---

### Post by presence1960 on 2010-01-29
> **SusieSA said:**
> Thank you for the response presence1960 and sorry to take so long to respond.  I eventually had to go to bed (feeling rather panicked that I hadn't been able to do any of the work I intended to do on my pc!)

I tried the above command and this is what happened:

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda -y -f -v -c
e2fsck 1.41.9 (22-Aug-2009)
e2fsck: Device or resource busy while trying to open /dev/sda
Filesystem mounted or opened exclusively by another program?


How does a filesystem become unmounted?
I'm sure we're getting closer...

```
sudo e2fsck /dev/sda1 -y -f -v -c
```

Try that because using sda may cause a problem if the Live CD has mounted swap.

---

### Post by SusieSA on 2010-01-29
Dear presence1960.

This command worked and it's busy doing it's thing... 21 % done.

I'm so glad you're still around... but... what are you still doing up?

I hope for my sake you're still up when this thing gets to 100% but for your sake, I hope you get some sleep!

Thank you for your assistance.  I still feel like such an Ubuntu noob even though I've been using it for about 3 years now.  It just works so well (normally) that I don't often have to fiddle around in the terminal window.

---

### Post by presence1960 on 2010-01-29
> **SusieSA said:**
> Dear presence1960.

This command worked and it's busy doing it's thing... 21 % done.

I'm so glad you're still around... but... what are you still doing up?

I hope for my sake you're still up when this thing gets to 100% but for your sake, I hope you get some sleep!

Thank you for your assistance.  I still feel like such an Ubuntu noob even though I've been using it for about 3 years now.  It just works so well (normally) that I don't often have to fiddle around in the terminal window.

ha-ha-ha! I bowled in my money league tonight and got home about an hour ago. had a decent night on the lanes 246,247,216 for a 709 series.

---

### Post by SusieSA on 2010-01-29
OK - it's finished.  I'm posting the output and then I'll reboot and retry...  Hold thumbs.

ubuntu@ubuntu:~$ sudo e2fsck /dev/sda1 -y -f -v -c
e2fsck 1.41.9 (22-Aug-2009)
Checking for bad blocks (read-only test): done                                
/dev/sda1: Updating bad block inode.
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information

/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

  154504 inodes used (1.05%)
     938 non-contiguous files (0.6%)
     109 non-contiguous directories (0.1%)
         # of inodes with ind/dind/tind blocks: 0/0/0
         Extent depth histogram: 133256/51
 5650200 blocks used (9.65%)
       0 bad blocks
       1 large file

  110263 regular files
   17231 directories
      68 character device files
      26 block device files
       0 fifos
     394 links
   26900 symbolic links (21086 fast symbolic links)
       7 sockets
--------
  154889 files
ubuntu@ubuntu:~$

---

### Post by SusieSA on 2010-01-29
Oh dear... no luck.  It's still exactly the same.  What next?

---

### Post by presence1960 on 2010-01-29
> **SusieSA said:**
> Oh dear... no luck.  It's still exactly the same.  What next?

Is this the PC that you did a dist-upgrade on or is it the new one?

---

### Post by SusieSA on 2010-01-29
It's a brand new one.  It worked fine last weekend (after I'd resolved the resolution issue).

---

### Post by presence1960 on 2010-01-29
> **SusieSA said:**
> It's a brand new one.  It worked fine last weekend (after I'd resolved the resolution issue).

The file system check found and modified errors but it still will not boot. I would say you may have to reinstall. The good thing is it is new and you probably don't have a lot of data on there. Hopefully you have a backup.

You may want to wait, maybe someone like meierfra will come along and maybe he will see something I do not.

Your situation happened to me one time and the file system check fixed it and I was able to boot again. Sorry I can't be of more service.

---

### Post by SusieSA on 2010-01-29
Oh no this sounds terrible.  What could cause such a problem?  Have I bought a dud pc?  I've just paid the guy yesterday before I got home.  I've got backups of everything from before last weekend.  But I've been working on a project that I did HEAPS of work on last weekend and those files are sitting on my harddrive.  Will I lose them?  Can't I save them before reinstall?  

If I put in the boot disk and reinstall it, isn't it possible that it installs the new copy over the old one and keeps my files?  Surely if I reinstall, I'm still going to have the same issue?  Why will a reinstall fix it?

Oh my goodness - so many questions.  I'm feeling a bit panicked... to say the least. 
 
Thank you so much for your help presence1960 - you have earned all those beans!  Is it possible to contact meierfra to get some help? 

Yuck.

---

### Post by SusieSA on 2010-01-29
OK so I've decided that I'm going to reinstall Ubuntu 9.10 to try and fix this but I want to try and get some data off my new disk first.  There's not much that I need to save, but it would be amazing to succeed.

So I took the harddrive out of my old machine and put this into the new machine and booted from there.  Now I am able to boot up and in Places -> Computer, I can see my new harddrive, but when I try and open it, I get the following error:

Cannot Mount Volume
The volume uses the ext4 file system which is not supported by your system

How do I overcome this hurdle?

---

### Post by presence1960 on 2010-01-29
> **SusieSA said:**
> OK so I've decided that I'm going to reinstall Ubuntu 9.10 to try and fix this but I want to try and get some data off my new disk first.  There's not much that I need to save, but it would be amazing to succeed.

So I took the harddrive out of my old machine and put this into the new machine and booted from there.  Now I am able to boot up and in Places -> Computer, I can see my new harddrive, but when I try and open it, I get the following error:

Cannot Mount Volume
The volume uses the ext4 file system which is not supported by your system

How do I overcome this hurdle?

Boot the Live CD and recover those files. If that doesn't work I use BackTrack Linux to recover files from client's unbootable windows boxes. This saves the trouble of opening up the case and pulling the hard disk. Get it[ here]("http://www.backtrack-linux.org/").

---

### Post by SusieSA on 2010-01-29
Oooh Welcome back presense 1960.  I hope you slept well.

Things have moved on since my previous post.  I got advice that the old Ubuntu version that I was on, could not read the ext4 file system.  As all my files on my old harddrive were backed up, I unplugged the new harddrive and did a fresh install of 9.10 on my old harddrive. 

My plan is to get the preciouls files off my new harddrive and then reinstall 9.10 on my new harddrive.

So, now I have BOTH harddrives plugged into the pc and I am running 9.10 off my old harddrive.  But I STILL can't access the new harddrive but now because of a different problem... When I go to Places -> Computer, it doesn't even exist.  So I read some other threads and decided that I need to mount my new harddrive.  So I did the following:


sue@sue-desktop:/media$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06210620

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d826e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29164   234259798+  83  Linux
/dev/sdb2           29165       30401     9936202+   5  Extended
/dev/sdb5           29165       30401     9936171   82  Linux swap / Solaris
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2010-01-29 13:01 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-01-29 13:01 cdrom0
drwxr-xr-x 2 root root 4096 2010-01-29 14:14 exthd
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ sudo mount -t ntfs /dev/sdb /media/exthd
[sudo] password for sue: 
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
sue@sue-desktop:/media$ 




I understand this to mean that my new harrdrive (the 250G) is on sdb1.  

I created a directory in /media called 'exthd' and I tried to mount sdb to this directory (I also tried to mount sdb1), but I get an error because I've got the wrong type for the harddive - it's not a NTFS.  

You're probably giggling at how blindly I follow these other posts.  What is NTFS and how do I find out what type my harddrive is?


btw - I spoke to the guy who sold me the PC and he reckoned that some energy surge or something must have corrupted a very important file and that this problem is not really an Ubuntu problem.  Thus the reinstall suggestion.  I could just ditch my precious files but they're not called precious for nothing.

---

### Post by SusieSA on 2010-01-29
Oh yes... and I'm also a little bit concerned about this:

sue@sue-desktop:/media$ ls -l
total 8
lrwxrwxrwx 1 root root 6 2010-01-29 13:01 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-01-29 13:01 cdrom0
drwxr-xr-x 2 root root 4096 2010-01-29 14:14 exthd

Why is my cdrom pointing to cdrom0?  Is this OK?

---

### Post by SusieSA on 2010-01-29
Oh doh!  I got it!

sudo mount -t ext4 /dev/sdb1 /media/exthd

Now I can access my files, back them up and then reinstall.....

Oh yippy.  Maybe I'll have this fixed within 24 hours of finding the fault.

---

### Post by presence1960 on 2010-01-29
> **SusieSA said:**
> Oooh Welcome back presense 1960.  I hope you slept well.

Things have moved on since my previous post.  I got advice that the old Ubuntu version that I was on, could not read the ext4 file system.  As all my files on my old harddrive were backed up, I unplugged the new harddrive and did a fresh install of 9.10 on my old harddrive. 

My plan is to get the preciouls files off my new harddrive and then reinstall 9.10 on my new harddrive.

So, now I have BOTH harddrives plugged into the pc and I am running 9.10 off my old harddrive.  But I STILL can't access the new harddrive but now because of a different problem... When I go to Places -> Computer, it doesn't even exist.  So I read some other threads and decided that I need to mount my new harddrive.  So I did the following:


sue@sue-desktop:/media$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x06210620

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9327    74919096   83  Linux
/dev/sda2            9328        9729     3229065    5  Extended
/dev/sda5            9328        9729     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d826e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       29164   234259798+  83  Linux
/dev/sdb2           29165       30401     9936202+   5  Extended
/dev/sdb5           29165       30401     9936171   82  Linux swap / Solaris
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ ls -l
total 8
lrwxrwxrwx 1 root root    6 2010-01-29 13:01 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2010-01-29 13:01 cdrom0
drwxr-xr-x 2 root root 4096 2010-01-29 14:14 exthd
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ 
sue@sue-desktop:/media$ sudo mount -t ntfs /dev/sdb /media/exthd
[sudo] password for sue: 
NTFS signature is missing.
Failed to mount '/dev/sdb': Invalid argument
The device '/dev/sdb' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
sue@sue-desktop:/media$ 




I understand this to mean that my new harrdrive (the 250G) is on sdb1.  

I created a directory in /media called 'exthd' and I tried to mount sdb to this directory (I also tried to mount sdb1), but I get an error because I've got the wrong type for the harddive - it's not a NTFS.  

You're probably giggling at how blindly I follow these other posts.  What is NTFS and how do I find out what type my harddrive is?


btw - I spoke to the guy who sold me the PC and he reckoned that some energy surge or something must have corrupted a very important file and that this problem is not really an Ubuntu problem.  Thus the reinstall suggestion.  I could just ditch my precious files but they're not called precious for nothing.

Do not use the ntfs switch because that is a windows filesystem and linux on sdb1 is ext4 filesystem. Try this from terminal ```
sudo mount /dev/sdb1 /mnt

```
Then from Places > Computer go Filesystem (on left pane). navigate to the mnt directory and then open sdb1 directory. This is of course assuming it was mounted by the mount command.

---

### Post by SusieSA on 2010-01-29
Hello from my new installation.  This worked fine.  I hear that the most likely reason for this problem was that a very special file was corrupted due to a power surge.  Whatever it was.  It's working now.

I hope this thread helps somebody else.

Thank you everybody.

---

### Post by presence1960 on 2010-01-29
> **SusieSA said:**
> Hello from my new installation.  This worked fine.  I hear that the most likely reason for this problem was that a very special file was corrupted due to a power surge.  Whatever it was.  It's working now.

I hope this thread helps somebody else.

Thank you everybody.

Glad you got it working again! Enjoy Ubuntu.

---

