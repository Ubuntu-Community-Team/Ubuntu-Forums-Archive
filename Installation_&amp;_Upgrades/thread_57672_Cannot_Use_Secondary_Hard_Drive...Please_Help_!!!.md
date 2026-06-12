---
title: "Cannot Use Secondary Hard Drive...Please Help !!!"
date: 2005-08-17
forum: Installation &amp; Upgrades
---

### Post by Hammad on 2005-08-17
Finally today i got to install UBUNTU....
     
       I Installed UBUNTU & Windows Xp on my 20GB Hard Drive and it worked fine for me but after installation when i connected my 80GB Hard Drive parallel to my 20GB...i am new to UBUNTU so i can't find anything on my secondary hard drive (80GB) in UBUNTU as for Windows Xp i see all my partitions and i can access all my data i mean i don't know where UBUNTU is places my 80GB or simply i just don't know how to and from where to access my 80GB hard disk in UBUNTU i checked Device Manager it shows my secodary hard drive but i can't find a way to use it as i went to dev\.There i found hda1,hda2,hda3,hda4,hda5,hda6,hda7 & hdb,hdb1,hdb2,hdb5,hdb7 with CROSSES on them are these my hard drives ??? i mean i can't get a way to acces data in my 80GB...and when i click these icons or whatever it says "Couldn't display "/dev/hdb1"."

Please guide me through this that how can i see my 80GB in UBUNTU

Hammad
cHeErS

---

### Post by jasmuz on 2005-08-17
Asuming that you installed Ubuntu into the primary HD it would be hda, and the secondary would be hdb (hda1 and so on refer to partitions). Have you tried mounting the 80 gb disk? 

Is the 80 gb drive in NTFS? is so just go sudo mount -t /dev/hdbX /whateverplace (X is the number of partition)

I recommend you read this: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29)

Hope it helps.

---

### Post by Hammad on 2005-08-17
i don't know how to mount and i tried mouting it by the guide you reffered to me

[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29)

i pressed CTRL+ALT+F1 to go to the command prompt(or whatever you call it in linux) and typed those commands.it was going fine till when i followed step 3 and tried to add the following code in /etc/fstab

<file system>    <mount point>     <type>     <options>                      <dump>     <pass> 
/dev/hda1        /mnt/win98        vfat       defaults,auto,uid=1000,gid=1000 0 0

it says the file is readonly and i tried copying the fstab file to another location and then editing it the editing was done but when i tried to replace the one in etc/fstab it says that "you do not have permissions to modify its parent folder." and i checked the permissions of fstab by right clicking on properties they were somthing like this

Fil owner: Root
File group: Root
and at last it was written that "You are not the owner,so you can't change these permissions"

i mean i am the owner of the computer and my username is Hammad so why is it giving this error

plz tell me how to edit this file

Cheers

---

### Post by Buffalo Soldier on 2005-08-17
Hi Hammad,

What command did you use to edit the fstab file? Did you use the *sudo* command with it? Example, if the command that you used was:```
nano /etc/fstab
```then try```
sudo nano /etc/fstab
```
What is *sudo*? 
[ Sudo in a Nutshell](http://www.courtesan.com/sudo/intro.html)

---

### Post by Hammad on 2005-08-18
Hi Buffalor Soldier

           I used the command given in this guide there was no nano written in that guide simply this was written and i typed it as it was there i typed the following line 

> $ sudo gedit /etc/fstab

below is the link of guide which i followed
[https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions?highlight=%28windows%29)

bYe

---

### Post by RudolfMDLT on 2006-05-23
Hi Hammad,

The red crosses mean that they are probally NTFS drives?
If they are NTFS drives you nees to edit Fstab and tell Ubuntu
that they are NTFS and where you would like to mount them.

A good guide that I used and that I still read twice a day is this one:

[http://ubuntuguide.org/](http://ubuntuguide.org/)

Follow the instructions carefully and make sure you backup every file that you edit.
It is a huge page, so the specific topic I think you are looking for is here:

[http://ubuntuguide.org/#automountntfs](http://ubuntuguide.org/#automountntfs)

Good luck!


PS: If the drives are NTFS you wil not be able to write to them, only read. If you would like to copy data from a Ext3(Linux File System) drive to a NTFS you need to download a Linux File System driver for windows and then in windows do the copying. - But thats a worry for later, I just didn't want you getting your drives working and then getting all angry again because you can't write to them! :)

---

