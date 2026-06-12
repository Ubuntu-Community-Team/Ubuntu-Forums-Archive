---
title: "Disk Access how ??"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by bladepif on 2006-07-12
Hello,

I'm new to the Linux and Ubuntu world, and have Installed Unbuntu 6.06 to my PC. The installation works fine, but now I have some problems accesing my harddrive.
I have 2 drives, the fisrt one the system is installed and the second one i want to use a data drive.
The second drive has 2 ext3 partitions. But when I logged in and try to double klick the disks, i get an message that this is not possible becaus e the disk is already mounted in /

What do i have to change to get access to my 2 partitions on disk 2 ? Should I mount something ?
Right now I have not really understand how is works with the disk and partitions.

What I already try was to klick on deactivate in the disk manager but this did not work !

Can someone give me a tip how to get access on this partions ?

CU Online

---

### Post by OpsVentus on 2006-07-12
Sounds like, somehow, you've got the other partitions set to mount on "/" where the first drive is allready mounted.
Open "Disk Manager" there you can see all your disks/partitions and where it wants to mount them.
For the second drive, first partition use(for example) "/media/data1".
For the second drive, second partition use(for example) "/media/data2".
Then try to enable them.

---

### Post by bladepif on 2006-07-12
@OpsVentus,

In the Disk Manager both partitions are already mapped to / like you say, but how can I change this? When I enter an other path like /mnt/disk1 and klick on save, the changes will not be saved. That the reason I try to klick on deactivate first but the partion will not be deactivated.

Is this a user problem, is it possible that the user set during the installation from live CD can not do this ?

Thanks
CU Online

---

### Post by OpsVentus on 2006-07-12
Well, I can imaging why the program is refusing to unmount "/" and won't allow to relocate "/", but in this case we really want to do it.
So lets try the good old "terminal" way.
You need to adjust 'fstab' so the partitions don't want to mount to "/".
Open terminal and type: "gedit /etc/fstab"
Now gedit will open fstab, this is the file where Linux stores the information on which partition should mount where and how.
Post here wat's in there, we will tell you what should be changed.

You know how to do this?

Cheers,
Bart.

---

### Post by bladepif on 2006-07-12
@OpsVentus

I think that something I can manage. I will try this, this evening when coming home from work, and post here.

Thanks for your help

CU Online

---

### Post by bladepif on 2006-07-12
Here is the content of fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

can you tell me what to change ?

Right now I try again the use the Diskmanager to mount the drive and could mount it in /mnt/Disk1. But I can not write to this disk and also not to system disk. Why? Probably the user have no rights to do this, but how to change it ?

Thanks
CU Online

---

### Post by OpsVentus on 2006-07-13
As a user you do not have rights to write to the bigger part of the systemdisk. This is a good thing, so we won't change it now.
But the other partitions should be writable to you. To do this add these 2 lines at the end of your fstab:

/dev/hdb1 /mnt/Disk1 ext3 defaults 0 0
/dev/hdb2 /mnt/Disk2 ext3 defaults 0 0

So it looks like:
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdb1 /mnt/Disk1 ext3 defaults 0 0
/dev/hdb2 /mnt/Disk2 ext3 defaults 0 0

To do this you go to the terminal and type: 
"sudo gedit /etc/fstab".
then add the lines, save, and type next commands: 
"sudo umount /dev/hdb1"
"sudo umount /dev/hdb2"
"sudo mount -a"

Now check if you can write to the 2 disks. :)

Cheers,
Bart.

---

### Post by bladepif on 2006-07-13
@OpsVentus,

Ok I will do this this evening.

A short question for the installation I have use the first disk (size 120GB).On a Windows system I usually create a first system partion that has 15 GB and use the second partitions on the disk as Data and install disk for applications.

Can I also do this on my Linux machine ? Is it possible to change the size of the system partition and split the disk one in 2 partitions without reinstalling ? if not reinstall will not be a problem.

Thanks for your help

---

### Post by OpsVentus on 2006-07-13
Let's start with the system layout:
/ = is the root
/home = here is all the users data
/media/ = is the normal place for extra media/disks

Therefor most users like to use one partition to mount on '/', this is your systemdisk, needs to be bigger then +-2 GB(if got 3GB), bigger isn't usefull.
Then mount a different partition on '/home', here will all your user settings/my documents and alike.
Any other partitions go in '/mnt' or '/media'.
Then you got an swap partition, which is about the size of your memory.

If you use this setup then it's very easy to do a clean install on '/' and still keep all your settings in '/home'.

It is possible to split up your disk into '/' and  '/home' but this will take way more time then a fresh install.
I would say, copy '/home' to the second disk, split up your first disk, fresh install Ubuntu, copy '/home' from the second disk back.
And there you have a fresh install of Ubuntu with your old settings.

But this kind of stuff is discussed befor and there are plenty of howto's on it, try the search button. ;)

Cheers,
Bart.

---

### Post by bladepif on 2006-07-14
@OpsVentus

Thanks for your help, the mountig has worked perfectly, now I understand a little bit better how it works.I also found some tutorials, that a really helpfull. So on Sunday I will reinstall Ubuntu.

CU Online

---

