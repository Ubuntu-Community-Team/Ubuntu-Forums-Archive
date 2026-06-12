---
title: "Saving files to use when upgrading Ubuntu"
date: 2018-01-20
forum: Installation &amp; Upgrades
---

### Post by Docfxit on 2018-01-20
I would like to upgrade Ubuntu Gnome.  Before the upgrade I would like to copy all my files to a second computer.  I have found a way to do it but it needs modifying to meet my needs.  This is the command I found:
sudo rsync -aAXv --exclude={"/dev/*","/proc/*","/sys/*","/tmp/*","/run/*","/mnt/*","/media/*","/lost+found"} -e 'ssh -i /path/to/private_key' root@SERVER_IP_ADDRESS:/* ~/backup/

I am currently booted up from a USB.  I need to modify the above command to copy from a partition on the hard drive /media/it to a folder on the same hard drive /home/docfxit/BackupFiles

Could someone please let me know what the new command line should be?

After all the files are in the BackupFiles folder I will copy them to another computer so I can clean install the latest version of Ubuntu.

Thank you,

Docfxit

---

### Post by Bashing-om on 2018-01-20
Docfxit; Hello -

Let's do this in small steps so you understand what the process is .

As a reference this is my command to backup my personal files.
```

rsync -aiv --exclude=".*" /home/sysop/ /media/sysop/8023-774F/storage/

```
where I - sysop - am booted into my install and coping my files to an external USB thumb drive ( 8023-774F ) .
Be aware it is not a good practice to make backups into the same device . If the drive dies or you make an error in direction you loose everything !
Can you not come up with a better option than coping back to the install drive ?
Say, work from the install and copy the files to that USB ?

The process is simple - once the source and the destination is known.
Simply mount the source, mount the destination, make sure the file access rights are permissible  and then:
copy the files you want to backup.
When the copy operation completes - ReMeMber - to UN-mount what you have mounted !

Now we are at " what process do you need to use to copy your data from the install to where " ?
As all things are relative; what is the relative source to what you are working from, and what is the relative destination from where you are working from ? Then we can know the "paths" to give to rsync .

[INDENT][INDENT]easy as falling out of bed wide awake
[/INDENT][/INDENT]

---

### Post by Docfxit on 2018-01-20
Thank you for the example.

I guess I need to break it down so I can figure out what I need.

In my example the options are "-aAXv"  in your example the options are "-aiv"  What do they mean?
In your example you are copying one folder.  In my example I think it's copying all folders.
In your example what does this mean?   --exclude=".*"
In both examples I think it's copying files from the drive it's booted to.
I need an example that copies files from a drive that it's not booted into.  I'm booted from a USB and the files I need to copy from are on a hard drive.   How can I figure out the name of the hard drive?
In my example there is a -e option.  What does that mean?
I understand it's not good practice to backup files to the same hard drive.  I am only doing that to make it simpler to get all the files I need (excluding the files I don't need) into one place.  It would be harder to do the copy to a shared folder on another computer.  In my first post I mentioned after I do the initial copy I will move the files to a separate computer.
I'd also like to know how to set the permissions on the /home/docfxit folder so I can copy everything into there.

Thanks,

Docfxit

---

### Post by Bashing-om on 2018-01-20
Docfxit; well ...

> 
In my example the options are "-aAXv" in your example the options are "-aiv" What do they mean?

The manual will explain the switches much better than I :
```

man rsync

```

> 
In your example you are copying one folder. In my example I think it's copying all folders.

nope, " /home/sysop/" is top level - all directories and files within my home are exposed.

> 
In both examples I think it's copying files from the drive it's booted to.

true, but the paths are always relative !

> 
 I'm booted from a USB and the files I need to copy from are on a hard drive. How can I figure out the name of the hard drive?

```

sudo fdisk -lu

```
terminal command ^ from the live USB to show us the drive ID, from this we can mount the partition containing the files you want to copy.

> 
I'd also like to know how to set the permissions on the /home/docfxit folder so I can copy everything into there.


One sets the access rights on the mount point - once this target is identified (^^) .

[INDENT][INDENT]small steps ->
[INDENT][INDENT][INDENT]progress made
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Docfxit on 2018-01-22
I see the output from:
sudo fdisk -lu
shows the drive ID is 83

How do I input the copy from for all files on the drive with drive ID 83 on the rsync command?

Thanks,
Docfxit

---

### Post by Bashing-om on 2018-01-22
Docfxit; Nope ..

what we seek here is the drive ID .. the "83" is the file type:

as an example; my output :
```

sysop@x1604:~$ sudo fdisk -lu
[sudo] password for sysop: 
Disk /dev/sda: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xb6a9f0ca

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 290818047 290816000 138.7G 83 Linux
/dev/sda2       290818048 321538047  30720000  14.7G  5 Extended
/dev/sda5       290820096 300036095   9216000   4.4G 82 Linux swap / Solaris
sysop@x1604:~$ 

```
where my 'root' partition is on the drive sda and is partition sda1 .

code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

We must identify - correctly - our respective targets before we can proceed further.

[INDENT][INDENT]small steps
[/INDENT][/INDENT]

---

### Post by Docfxit on 2018-01-22
So for rsync would the from be:
/dev/sda2/*

To specify all files on the drive?
Thanks,
Docfxit

---

### Post by Bashing-om on 2018-01-22
Docfxit;

Look, you are making this so much more difficult than it is .
There is absolutely no need to backup system files - the only files needed to be backed up are your personal files that are located in your /home. All system files will be on that new install .. any system files you may save will not be compatible with the newer version packaging .

So what we need to see at this time is the output of "some" command to see the hard drive structure .
I do suggest :
```

sudo fdisk -lu 

```

What we want to do is find the location of your /home , determine the location of where the files are to be copied to, mount the respective locations and tell rsync what to do - unmount as needed when done.

as simple as that .

[INDENT][INDENT]all in a day's work
[/INDENT][/INDENT]

---

### Post by Docfxit on 2018-01-22
If I had VNC running in Ubuntu I could copy paste the output from:
sudo fdisk -lu

Here.

Docfxit

---

### Post by oldfred on 2018-01-22
I started using rsync based on this, note that /media/backup must exist as mount point or you have issues.
 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603](http://ubuntuforums.org/showthread.php?t=868244&p=7015603#post7015603)
Sample rsync file, use a text editor and paste into a file & name it mybackup.sh
of course, do the dry run first  

There is no need to back up system folders, almost all your data is in /home. But if you manually edited some config files those are in /etc. I just copy the few I edit like 40_custom, grub, and a couple others into /home so backup includes them. I also export list of installed applications.


 Oldfred's list of stuff to backup May 2011 (still mostly current, see added links below):
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)
Adding extra commands to rsync 
[http://ubuntuforums.org/showthread.php?t=2260658](http://ubuntuforums.org/showthread.php?t=2260658)
More detail on /etc files and others to backup - post #3:
[http://ubuntuforums.org/showthread.php?t=1500559](http://ubuntuforums.org/showthread.php?t=1500559)
Some files(temp, cache etc) to exclude from /home backup - post #8 by  Paddy Landau
[http://ubuntuforums.org/showthread.php?t=1883834](http://ubuntuforums.org/showthread.php?t=1883834)
[http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders](http://askubuntu.com/questions/545655/backup-your-home-directory-with-rsync-and-skip-useless-folders)

---

### Post by Docfxit on 2018-01-22
I am not interested in any system files.  All I need is my personal files so I can install a new version of Ubuntu on the hard drive and then update all the personal files.  The problem that I see it is it's not as simple as copying everything in /home.  I have Asterisk installed on the driver and nun of the Asterisk files are in home.

Thanks,
Docfxit

---

### Post by Bashing-om on 2018-01-22
Docfxit; so ?

Just run 2 rsync commands .

[INDENT]this is not rocket science
[/INDENT]

---

### Post by Docfxit on 2018-01-22
Bashing-om 

You are making this a ton harder than it has to be.
When you say "Just run 2 rsync commands ."

I have no idea what you have in mind.
What would the 2 rsync commands look like.
I'm trying to figure out what would be in the commands and you aren't giving me any examples so I can't figure out what to put in the rsync commands.

Docfxit

---

### Post by Docfxit on 2018-01-22
I need to copy all files on the hard drive in etc/asterisk 
to a windows PC on my LAN at 192.168.168.9/backup/AsteriskBackup

Would this be correct?
rsync -avvP /c3d00b1d-c292-4038-bc64-475dfc3d66e4/etc/asterisk 192.168.168.9:/* ~/backup/asteriskbackup/

Thanks,
Docfxit

---

### Post by Bashing-om on 2018-01-22
Docfxit; Well.

I can not provide guidance when I have no info to formulate a command.
1) once more show us the fdisk output
2) see what is mounted
3) know what you are booted up to
4) know what the paths are relative to what you have booted into
5) know the path of the destination
6) KNOW what you are going to back up
7) make up the proper mount points
8) verify what is the path(s) and the files to be backed up

we can not tell you how to administer your system - it is your system

[INDENT][INDENT]I do not own a crystal ball
[/INDENT][/INDENT]

---

### Post by oldfred on 2018-01-22
If you copy to a Windows PC (NTFS), you lose all ownership & permissions.
You can restore data files from /home or data partitions and reset permissions & ownership to you, but you cannot do that with any system files such as those in /etc or any other system folder.

Always better to label partitions, so then you are not trying to use the long UUIDs.
With gpt partitioning there are now two labels:
```
fred@Z170N:~$ lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT
NAME   LABEL   PARTLABEL    SIZE UUID                                 MOUNTPOINT
sda                       232.9G                                      
&#9500;&#9472;sda1 ESP     ESP         49.8G D966-440A                            /boot/efi
&#9500;&#9472;sda2 xenial  xenial      30.3G 5c1e1a3f-261f-4da5-a0c2-8f479b3039de /
&#9500;&#9472;sda3 ISO     ISO         20.5G ab916e15-8a74-4d6e-a0b1-32718a505dc7 /media/fre
&#9492;&#9472;sda4         bionic      25.4G e1e5879e-1828-4a1c-806c-b29c426ccc34 
sdb                       931.5G                                      
&#9500;&#9472;sdb1 ESP_B   EFI System Partition
&#9474;                          48.9G F496-1330                            
&#9500;&#9472;sdb2 zesty   zesty       30.3G a9bd9a65-bc8c-41b1-95b1-2dceb66b2652 
&#9500;&#9472;sdb3 ISO_b   ISO_b       49.8G c395f36d-5e02-4913-a904-e336054b2eff /media/fre
&#9500;&#9472;sdb4 backup_b
&#9474;              backup_b    49.8G dd4e4a2e-4785-4441-91b0-28234b98e625 
&#9500;&#9472;sdb5 server  server      30.3G b76dc590-99a3-4e34-af35-e0dd43507232 
&#9500;&#9472;sdb6 data    data       205.1G f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data
&#9500;&#9472;sdb7                      2.1G 3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd [SWAP]
&#9500;&#9472;sdb8         yakkety     25.4G 6c042846-fc6c-4f5b-80fc-7aa678cf09b7 
&#9492;&#9472;sdb9 Fedora  Fedora      25.4G 5326d262-26af-4b38-a523-b0f4d261f1a4 
```

---

### Post by Docfxit on 2018-01-22
> **Bashing-om said:**
> Docfxit; Well.

I can not provide guidance when I have no info to formulate a command.
1) once more show us the fdisk output

5) know the path of the destination
```
 sudo fdisk -lu
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6ef67c30
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    55906199    27952076   17  Hidden HPFS/NTFS
/dev/sda2   *    55906200   137916415    41005108   83  Linux
/dev/sda3       461900880   465804674     1951897+  92  Unknown
/dev/sda4       465805312   488396799    11295744   1c  Hidden W95 FAT32 (LBA)
Partition 4 does not end on cylinder boundary.

```

> **Bashing-om said:**
> 
2) see what is mounted
3) know what you are booted up to

I am now booted up to /dev/sda2

> **Bashing-om said:**
> 
4) know what the paths are relative to what you have booted into
5) know the path of the destination

I need to copy all files on the hard drive in etc/asterisk
to a windows PC on my LAN at 192.168.168.9/backup/AsteriskBackup

> **Bashing-om said:**
> 
6) KNOW what you are going to back up

All files in the asterisk folder

> **Bashing-om said:**
> 
7) make up the proper mount points

What else do you need to know to make up the proper mount points?

> **Bashing-om said:**
> 
8) verify what is the path(s) and the files to be backed up



Does this answer your questions?

Docfixt

---

### Post by Docfxit on 2018-01-22
> **oldfred said:**
> If you copy to a Windows PC (NTFS), you lose all ownership & permissions.
You can restore data files from /home or data partitions and reset permissions & ownership to you, but you cannot do that with any system files such as those in /etc or any other system folder.

Always better to label partitions, so then you are not trying to use the long UUIDs.
With gpt partitioning there are now two labels:
```
fred@Z170N:~$ lsblk -o NAME,LABEL,PARTLABEL,SIZE,UUID,MOUNTPOINT
NAME   LABEL   PARTLABEL    SIZE UUID                                 MOUNTPOINT
sda                       232.9G                                      
&#9500;&#9472;sda1 ESP     ESP         49.8G D966-440A                            /boot/efi
&#9500;&#9472;sda2 xenial  xenial      30.3G 5c1e1a3f-261f-4da5-a0c2-8f479b3039de /
&#9500;&#9472;sda3 ISO     ISO         20.5G ab916e15-8a74-4d6e-a0b1-32718a505dc7 /media/fre
&#9492;&#9472;sda4         bionic      25.4G e1e5879e-1828-4a1c-806c-b29c426ccc34 
sdb                       931.5G                                      
&#9500;&#9472;sdb1 ESP_B   EFI System Partition
&#9474;                          48.9G F496-1330                            
&#9500;&#9472;sdb2 zesty   zesty       30.3G a9bd9a65-bc8c-41b1-95b1-2dceb66b2652 
&#9500;&#9472;sdb3 ISO_b   ISO_b       49.8G c395f36d-5e02-4913-a904-e336054b2eff /media/fre
&#9500;&#9472;sdb4 backup_b
&#9474;              backup_b    49.8G dd4e4a2e-4785-4441-91b0-28234b98e625 
&#9500;&#9472;sdb5 server  server      30.3G b76dc590-99a3-4e34-af35-e0dd43507232 
&#9500;&#9472;sdb6 data    data       205.1G f9537995-8b44-4abb-b5fb-ec27023f57b2 /mnt/data
&#9500;&#9472;sdb7                      2.1G 3ef43e7c-8a35-4f8b-bc73-c91d6098d4cd [SWAP]
&#9500;&#9472;sdb8         yakkety     25.4G 6c042846-fc6c-4f5b-80fc-7aa678cf09b7 
&#9492;&#9472;sdb9 Fedora  Fedora      25.4G 5326d262-26af-4b38-a523-b0f4d261f1a4 
```

Thank you very much for the information.  
Currently I am booted up to Ubuntu on the hard drive.  It doesn't have the cmd lsblk.  I know I need to get to a more recent version of Ubuntu.  I don't want to start a 2hr discussion on the reasons to get this updated.  I have been trying to figure out how to copy the files I need off of this hard drive so I can build a new version of Ubuntu.  This PC is running a PBX called Asterisk.  It's been running fine since 2007.  I installed a current version of Ubuntu on a USB so I could use the current commands.  I have had way to many problems getting the basic programs that I need to install, configure and run.  I have been working on this for 4 days and can't seem to figure out how to copy files.  A very simple task that should have taken no more than an hour.

Thanks,
Docfxit

---

### Post by Bashing-om on 2018-01-22
Docfxit ;

Yuk on me -
> 
a windows PC on my LAN at 192.168.168.9/backup/AsteriskBackup

Sorry, but you have dropped out of my experience range. I have not touched Windows in years; setting up file sharing on the LAN to Windows is not in my tool box.

[INDENT][INDENT]exit stage left
[/INDENT][/INDENT]

---

### Post by Docfxit on 2018-01-22
> **Bashing-om said:**
> Docfxit ;

Yuk on me -

Sorry, but you have dropped out of my experience range. I have not touched Windows in years; setting up file sharing on the LAN to Windows is not in my tool box.

[INDENT][INDENT]exit stage left
[/INDENT][/INDENT]

I have windows sharing setup.  I don't need help with that.  All I need is the command syntax for rsync.

Thanks,

Docfxit

---

