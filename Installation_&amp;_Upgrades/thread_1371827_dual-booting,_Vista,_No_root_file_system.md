---
title: "dual-booting, Vista, No root file system"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by ubuncha on 2010-01-03
Hello everyone, I recently recieved Ubuntu 9.04 Desktop Edition CD-ROM through snail-mail after requesting a copy online and I want to install it on my laptop, although I wish to keep Vista which is on it now.

My laptop has a 250GB hard drive. Although when in Vista this is represented as two separate drives each of 110GB, (C:) or ACER and (D:) or DATA.

Using the CD, I start the installation and everything is straightforward and self explanatory, until I get stuck at step 4...
Where I am told by the ubuntu installer: "This computer has several operating systems on it." (I'm confused now, I thought it had one, Vista.)
Beneath I am shown a bar representing my disk space which is divided between...

Windows Vista (loader) (/dev/sda1) - 9.8GB
Windows Vista (loader) (/dev/sda2) - 110.1GB
/dev/sda3 - 110.1GB
Microsoft Windows XP Embedded (/dev/sda4) - 3.0GB

I am given the option to use the entire disk: 
'SCSI1 (0,0,0)(sda) - 250.1GB ATA WDC WD2500BEVT - 2', 
(and from the mention of 250BG in the name I'm assuming this is one disk and not the two separate drives named C: & D: in Vista.) 

...along with a warning - "This will delete Windows Vista (loader), Windows Vista (loader), Microsoft Windows XP Embedded and install Ubuntu 9.04". (The aforementioned "several operating systems" obviously.)
But I wish to keep Vista, so I select the option to "specify partitions manually" and am brought to a screen named 'Prepare Partitions',
where there is a table somewhat like this:

Device        Type     Mount Point     Size                  Used
               
/dev/sda     fat32                          
/dev/sda1    ntfs                           10485MB           9495MB
/dev/sda2    ntfs                           118166MB         84157MB
/dev/sda3    ntfs                           118183MB         3225MB
/dev/sda4    ntfs                           3221MB            2583MB

I am then given the option for "New partition table", and if I select any of the bottom four devices I can 'edit partition' or 'delete partition'.
Selecting the device /dev/sda3 (because it is the one that I'm guessing has no operating system data on it, judging by the previous screen) and choosing 'edit partition', allows me the following options...
to create a new partition size, to select what I want to use the partition as. (There are also two options for formating a partition, which is a checkbox, and Mount point. These are both greyed out.)

When I look at the 'Use as:' option, within 'edit partition', the drop down box allows me to use the partition in the following ways:
- do not use the partition
- swap area
- NTFS
- FAT 32 file system
- FAT16 file system
- XFS journaling file system
- ReiserFS journaling file system
- Ext2 file system
- Ext4 journaling file system
- Ext3 journaling file system

I've read on another post I need to set the partition that I wish to use to install Ubuntu on to 'swap area', I think I should use sda3 for this (maybe not?), but when I do this and click 'Next' I get an error message... "No Root File System - No root file system is defined. Please correct this from the partitioning menu."

I've no idea how to correct this. What I would like is to have the dual boot option between Ubuntu and Vista and to to be able to save files while using either OS in a way which allows me to access them with whatever OS I'm running at A later time.

I know this was a long post for what probably is a simple or common problem, thanks for bearing with me. Any pointers or help would be greatly appreciated, thankyou. Best wishes.

---

### Post by lmarmisa on 2010-01-03
This video could be useful for you:

[http://www.youtube.com/watch?v=T9Nm7plRKHw](http://www.youtube.com/watch?v=T9Nm7plRKHw)

---

### Post by ubuncha on 2010-01-03
Thanks [lmarmisa]("http://ubuntuforums.org/member.php?u=955260") the video was very useful, even though I didn't watch it lol, I have a 56k dial-up modem (I know, I know)...
There was a link to a static page below the video though, which was helpful. 

[http://www.coverlesstech.com/dualboot](http://www.coverlesstech.com/dualboot)


I followed the instructions, partitioned the disk in Vista, I now have 20GB unallocated.
When I try to install Ubuntu though, at step 4 'Prepare Disk Space', although it shows me that I do now have 20GB free space, there simply is no option to select "Use the largest continious free space", as is instructed in the cloverlesstech.com blog.
If I select "Specify partition manually", I come to the same table I saw before, though this time there is device listed as 'unusable', with a size of 21474MB. If I select (right-click) the 'unusable' device, the only option is 'undo changes to partitions'.

I hit the forward button hoping for more options but I get the "No root file system" error again.

Thanks for any help.

---

### Post by MIJ-VI on 2010-04-19
> **ubuncha said:**
> Thanks [lmarmisa]("http://ubuntuforums.org/member.php?u=955260") the video was very useful, even though I didn't watch it lol, I have a 56k dial-up modem (I know, I know)...
There was a link to a static page below the video though, which was helpful. 

[http://www.coverlesstech.com/dualboot](http://www.coverlesstech.com/dualboot)


I followed the instructions, partitioned the disk in Vista, I now have 20GB unallocated.
When I try to install Ubuntu though, at step 4 'Prepare Disk Space', although it shows me that I do now have 20GB free space, there simply is no option to select "Use the largest continious free space", as is instructed in the cloverlesstech.com blog.
If I select "Specify partition manually", I come to the same table I saw before, though this time there is device listed as 'unusable', with a size of 21474MB. If I select (right-click) the 'unusable' device, the only option is 'undo changes to partitions'.

I hit the forward button hoping for more options but I get the "No root file system" error again.

Thanks for any help.

Hi ubuncha.

It's likely too late but...

Did you burn some Vista restore disks before trying any of this?

Have you considered learning how to install Ubuntu by practice installing it as a virtual machine in VirtualBox?: _[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)_

--------

EDIT: This is what I found by Googling: 'How to install Ubuntu 9.04.'

**Installing Ubuntu 9.04**

**Step-by-step installation guide with screenshots**

[http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-04-110794.shtml)

Please do more research before doing anything else to your computer which would risk compromising its functionality.

Thank you.

---

