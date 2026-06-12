---
title: "Allocate drive space???"
date: 2011-06-10
forum: Installation &amp; Upgrades
---

### Post by ikirby77 on 2011-06-10
Hi all,

I am trying to install ubuntu as a dual operating system with windows 7. I am a little bit confused as to what I should do in the allocate drive space section. I have a table displayed as follows:

Device size used

/dev/sda1 208 mb 69mb
/dev/sda2 485491mb 80607mb
/dev /sda3 14297mb 11916mb
/dev/sda4 108mb 33mb

I then have another drop down menu with the header: Device for boot loader installation. Menu options:

/dev/sda ATA TOSHIBA MK5056GS(500.1 GB)
/dev/sda1 Windows 7(loader)
/dev/sda2 windows recovery eniroment (loader)
/dev/sda3 windows recovery eniroment (loader)
/dev/sda4

I am very new to ubuntu and hard drive partitioning, I would be very grateful if someone could give me some advise on the options I should select before clicking the install now icon.

Thanks

Ian

---

### Post by amalbose on 2011-06-10
u may want to reformat ur drives:
u hav to have a partition for the root(/)
u can have a separate partition for the home directory.
also can use a swap partition(2 GB)

---

### Post by ajgreeny on 2011-06-10
> **ikirby77 said:**
> Hi all,

I am trying to install ubuntu as a dual operating system with windows 7. I am a little bit confused as to what I should do in the allocate drive space section. I have a table displayed as follows:

Device size used

/dev/sda1 208 mb 69mb
/dev/sda2 485491mb 80607mb
/dev /sda3 14297mb 11916mb
/dev/sda4 108mb 33mb

I then have another drop down menu with the header: Device for boot loader installation. Menu options:

/dev/sda ATA TOSHIBA MK5056GS(500.1 GB)
/dev/sda1 Windows 7(loader)
/dev/sda2 windows recovery eniroment (loader)
/dev/sda3 windows recovery eniroment (loader)
/dev/sda4

I am very new to ubuntu and hard drive partitioning, I would be very grateful if someone could give me some advise on the options I should select before clicking the install now icon.

Thanks

Ian
Your problem is that all 4 primary partitions are used by Windows 7, so you can't do anything without deleting and reformatting at least one of those, and unfortunately it is difficult with the information we already have to tell you which to use in that way.

Can you boot to the Ubuntu live CD/USB and then run System->Administration->gparted and post a screenshot of the gparted window.  It may also help to have the output of ```
sudo fdisk -l
```though the gparted window should tell us all that is needed.

---

### Post by ikirby77 on 2011-06-10
> **ajgreeny said:**
> Your problem is that all 4 primary partitions are used by Windows 7, so you can't do anything without deleting and reformatting at least one of those, and unfortunately it is difficult with the information we already have to tell you which to use in that way.

Can you boot to the Ubuntu live CD/USB and then run System->Administration->gparted and post a screenshot of the gparted window.  It may also help to have the output of ```
sudo fdisk -l
```though the gparted window should tell us all that is needed.

Hi ajgreeny,

I have attached a screen shot of gparted and the output from the fdisk command

Many thanks

Ian

---

### Post by oldfred on 2011-06-10
Several links to similar issues. You should make the recover DVDs so worst case you can reinstall to as purchased. It may be even better if you have made a lot of changes to do a full image backup.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. 
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

---

### Post by ajgreeny on 2011-06-10
OK, as expected all your partitions are primary and therefore you can not do anything without deleting at least one of them and reformatting.

DO NOT TOUCH sda1 nor sda2 at the moment, which are the boot, and operating system partitions.

You may be able to run something like clonezilla to clone both sdd3 and sda4, which are the Recovery and HP Tools partitions, then using windows own disk management utility, delete sda3 and sda4, then shrink sda2 to make room for ubuntu.  This should give you a large unallocated area at the end of the drive in which you can make an extended partition of the whole space.

It should now, as far as I'm aware, be possible to make two logical partitions in this new extended partition into which you can return the clones you made earlier.  Finally in the still unallocated space you should be able to install Ubuntu.

This is a bit complicated, I accept, but blame HP for using all four of the possible primary partitions on the disk; it is not the fault of ubuntu.

I suggest you wait a little while for more replies which may know of better ways to do things.  It may be possible to simply backup the sda3 and sda4 onto a USB hard disk, and not bother to reinstate their partitions into the extended partition, but my knowledge of Windows after XP, and specially Win 7 is just about zero, so I may be wrong.  I am also assuming you don't have any Win7 install disks of any sort, but if you do, you may be prepared to just delete the Recovery partition.  As for HP Tools, I've no idea at all what they are.

EDIT:
Thanks for coming to my help, oldfred, as I was getting seriously out of my depth here.  It looks as if I got things generally correct, apart from the burning of DVDs of the recovery utilities.

That's what happens when no longer using Windows and being M$ free, I suppose!

---

### Post by ikirby77 on 2011-06-13
Hi Guys,
 
I have now managed to install ubuntu alongside windows 7 as a dual operating system at the expense of the recovery partition, having made all the necessary back up cds. I managed to achieve this by using the following link:
 
The Hedge show graphically how to delete & create partitions:
[[COLOR=#444444]http://ubuntuforums.org/showthread.php?t=1713649[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1713649")
 
I would like to say thanks to both ajgreeny and oldfred for there advice.:)
 
Although everything is working fine, I would now like to free up space taken up by windows 7 and transfer this free space to the partition which ubuntu is now installed on. Having had a little play around to see if I could manage to do this by myself, I found that I can free up space on the windows 7 partition but I am having problems moving the free space to the ubuntu partition, any ideas guys?
 
I have attached a screen shot of how gparted now looks. Ubuntu is installed on sda5 ext 4, so I need to somehow move the unallocated free space attached to sda 2 to sda5 ext 4.
 
Thanks
 
Ian

---

### Post by oldfred on 2011-06-13
I typically do not like to move partitions left as then it has to copy & verify all data which also is a slow process. Since it is a new install you have little risk, but it may take just as long as a new install.

You will have to do all of this using gparted from a liveCD. You cannot work on mounted partitions (little key says it is mounted). You may also have to click on swap and right click swap off as the liveCD uses swap to speed things up. And mounting any logical partition in effect mounts the extended partition.

You cannot add space from a primary to a logical unless you also can include the space into the extended partition. In your case you can expand the extended partition left into the aunallocated space, then move your / (root) partition left and then expand it right.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

I prefer to keep system partitions small at 10 to 20GB and use /home for data. You could move the extended partition left to include the free space and then create another new partition for /home. It then is a bit of work to move /home.

These are three essentially identical ways to move /home, just using different commands for the copy function. See if one makes more sense than the other.
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
cp without -a and copying as sudo root takes ownership
To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cpio
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you create the expand the extended & create /home, you then can do a new install. Just use manual so you can choose the existing partitions you have already created.

---

### Post by ikirby77 on 2011-06-14
Hi Oldfred,
 
Thank you for all your advice I have now successfully increased my ubuntu partition to the size I wanted and everything is working fine. I managed to do this by using gparted off the live cd, firstly I had to unmount sda6 by right clicking and selecting swap off. I then moved sda3 partition to the left, once this was complete I moved sda5 to the left to occupy the free space. Luckly by doing this it did not effect any of the data or boot loaders so everything is working fine.
 
Thanks again Oldfred :D

---

