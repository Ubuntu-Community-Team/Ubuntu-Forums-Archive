---
title: "Problem in mounting special device at boot"
date: 2008-03-22
forum: Installation &amp; Upgrades
---

### Post by metaphongtov on 2008-03-22
I just installed Ubuntu 7.10.After the splashscreen running about 30%,I get a prompt  like this: 

[http://i47.photobucket.com/albums/f163/metaphongtov/bootproblem.jpg]("http://i47.photobucket.com/albums/f163/metaphongtov/bootproblem.jpg")

I can log on successfully anyway but I really dun wanna see that prompt again and again.Somebidy help me plzzz.

---

### Post by Herman on 2008-03-22
:) Hello metaphongtov,
 It look like you have probably changed a file system or a partition since you installed and you forgot to update your /etc/fstab file, here's a link to help you with that, [About /etc/fstab files with UUID filesystem ID added]("http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with").

Regards, Herman :)

---

### Post by metaphongtov on 2008-03-22
I am new to Ubuntu.I dun know how to edit in fstab UUID.When I start fstab by typing "gksudo gedit /etc/fstab",I got some information about my harddisk:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8
UUID=ad33d124-e98e-4a84-98fc-3f34900f7d93 /               ext3    defaults,errors=remount-ro 0       1
[B]# /dev/sda1
UUID=1C7E-ABC4  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1[/B]
# /dev/sda5
UUID=D55F-0085  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=7B0F-B764  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/sda7
UUID=f7b2014a-7159-4abf-8b35-20524c529edd none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0

I think the problem comes with sda1,the filesystem drive.Could you show me how to edit it.Thanks for ur kind.

---

### Post by Herman on 2008-03-22
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda8
UUID=ad33d124-e98e-4a84-98fc-3f34900f7d93 /               ext3    defaults,errors=remount-ro 0       1

# /dev/sda1
UUID=[COLOR=Red]**1C7E-ABC4**[/COLOR]  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda5
UUID=D55F-0085  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda6
UUID=7B0F-B764  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       1

# /dev/sda7
UUID=f7b2014a-7159-4abf-8b35-20524c529edd none            swap    sw              0       0

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```Probably you have reformatted the file system in partition number 1 of your hard disk or some program has changed the file system UUID number on you.

Your /etc/fstab file controls what file systems Ubuntu will mount at boot-up and other details about how they are to be treated.

You'll need more than one window open for the job you are about to do. In Windows, yopu might be used to 'minimizing' a window to the 'task bar'. Well in Ubuntu we can do that too, only we cal our 'taskbar' a 'panel' instead. But we have something better, down in the right of your bottom panel, you'll see your 'workspace switcher'. 
Right-Click on it and click 'Preferences', and in Workspace Switcher Preferences, set the number of workspace spinbox up to a larger number. I like eight or twelve, but any number you like will do.

Probably you will have this page you're looking at right now open in firefox right?
Okay, switch to a different workspace, (click on an empty one to go to it), and open your terminal and open your /etc/fstab file by copying and pasting the same command you used before, 
```
gksudo gedit /etc/fstab 
```Now switch workspaces again, to a new empty workspace, and open another (second) terminal.
Copy the following command and paste it into your second terminal,
```
sudo vol_id -u /dev/sda1
```That will give you the current and correct UUID number for your file system that's in /dev/sda1 partition.
Just copy that number, and go to the workspace where you left your /etc/fstab file open, and hilight the out of date or wrong UUID number with your mouse, right-click it and click 'paste', to overwrite it with the new UUID number.
Save and close the /etc/fstab file.

That's it! Whatever you do after that is up to you, probably close whatever else you have open and reboot to see if ti worked I imagine.

---

### Post by metaphongtov on 2008-03-24
I did as u show me to do though I still got the prompt after 30% splashscreen running in diffenrent way like this :

[http://i47.photobucket.com/albums/f163/metaphongtov/23-1.jpg]("http://i47.photobucket.com/albums/f163/metaphongtov/23-1.jpg")

[http://i47.photobucket.com/albums/f163/metaphongtov/34.jpg]("http://i47.photobucket.com/albums/f163/metaphongtov/34.jpg")

I think i have problems with mounting all my partition.I have 6 partitions but I just have 4 partitions automounted at first startup.When I mount the last 2 partitions that cannot automounted at first startup,i do not see their name with sda... but their names right away(name Vista and 777). What should I do now>? Thanks alot .

---

### Post by Herman on 2008-03-24
Well you have improved it, your /etc/fstab file is now pointing to the correct partition.

In your first photo in post #5, your sda3 / (root) ext3 file system is having a regular file system check. 
That's fine, it's supposed to do that at least once every thirty or so boot-ups, or every six months, whichever comes first, or if the computer was shut down the wrong way.
The only thing I can see that looks odd there is it says 'sda3', there, but according to your /etc/fstab file it should be /dev/sda8. I guess that doesn't matter for now, if everything's working okay. 

In your second photo in post #5, your /dev/sda1 FAT32 file system has been seen by Ubuntu for the first time. So your /etc/fstab file is improved. 
The problem now is it has found something wrong with your file system in that partition though.
The boot sector doesn't match the backup of the boot sector. 
If that partition has Windows in it, it could be caused by a virus, or just by Windows monkeying around with its own boot sector.
That can also be caused by installing a different boot loader to the first sector (boot sector) of that partition. For example, people learning how to install GRUB, if they get the command wrong, can install GRUB to the boot sector of the wrong partition by mistake.
If it's just a data partition it doesn't matter, you probably don't care.
To get rid of the error message, do what it says in this link, [When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup").

> I think i have problems with mounting all my partition.I have 6 partitions but I just have 4 partitions automounted at first startup.When I mount the last 2 partitions that cannot automounted at first startup,i do not see their name with sda... but their names right away(name Vista and 777). What should I do now>? Thanks alot .Please post a screencap from GParted and/oror the output from 'sudo fdisk -lu', and '[COLOR=#000000][FONT=Bitstream Vera Sans Mono]ls /dev/disk/by-uuid/ -alh'[/FONT][/COLOR]if you still need more help so I can see what's going on there.  :)
```
sudo fdisk -lu
``````
ls /dev/disk/by-uuid/ -alh
```The main thing is, you are making progress. It's better than it was before, you had more than one problem at once, that's all.

Regards, Herman :)

---

### Post by metaphongtov on 2008-03-25
When I check "sudo vol_id -u /dev/sda3", it shows UUID=ad33d124-e98e-4a84-98fc-3f34900f7d93,then I changed sda8 to sda3.
I am not sure what they say like this "GRUB should be installed to MBR, or a Linux bootsector, but not to a Windows bootsector".I have WinXP in sda1 as an active partition.I installed Ubuntu before WinXP so I lost boot grub,I only can log in to Windows XP.I restored boot grub by using Ubuntu live cd with this in terminal:

 find /boot/grub/stage1
 root (hd...) hay root (hd...,...)
 setup (hd0)

I think I don't have any virus in sda1 because I've just deep-formated to Fat32 before installing WinXP in it.And you said "Windows monkeying around with its own boot sector",I don't understand what it is.I try the link you gave me but it's compliated I dun understand much.Could u tell me more details?

Here is my screencap you wanna see.

heng@heng-desktop:~$ sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x083b083b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    58171364    29085651    c  W95 FAT32 (LBA)
/dev/sda2        58171365   292254479   117041557+   f  W95 Ext'd (LBA)
/dev/sda3       292254543   312576704    10161081   83  Linux
/dev/sda5        58171428   142994564    42411568+   b  W95 FAT32
/dev/sda6       142994628   248477354    52741363+   b  W95 FAT32
/dev/sda7       248477418   269522504    10522543+   7  HPFS/NTFS
/dev/sda8       269522568   271016549      746991   82  Linux swap / Solaris
/dev/sda9       271016613   292254479    10618933+   7  HPFS/NTFS
heng@heng-desktop:~$ ls /dev/disk/by-uuid/ -alh
total 0
drwxr-xr-x 2 root root 160 2008-03-25 17:52 .
drwxr-xr-x 6 root root 120 2008-03-25 17:52 ..
lrwxrwxrwx 1 root root  10 2008-03-25 17:52 1ABC0253BC022A39 -> ../../sda7
lrwxrwxrwx 1 root root  10 2008-03-25 17:52 36AC6F2EAC6EE7B7 -> ../../sda9
lrwxrwxrwx 1 root root  10 2008-03-25 17:52 505D-7FF3 -> ../../sda1
lrwxrwxrwx 1 root root  10 2008-03-25 17:52 7B0F-B764 -> ../../sda6
lrwxrwxrwx 1 root root  10 2008-03-25 17:52 ad33d124-e98e-4a84-98fc-3f34900f7d93 -> ../../sda3
lrwxrwxrwx 1 root root  10 2008-03-25 17:52 D55F-0085 -> ../../sda5


I am really appreciate your kind,thanks..!

---

### Post by Herman on 2008-03-25
:) Thank you, I will be back later and I should be able to use that information you sent to help you make some improvements to your /etc/fstab file and also explain more about the FAT32 boot sector.
Maybe it's nothing to worry about, you can get rid of the probelm if you want by restoring the backup from the original since you're sure the original is okay. I'll be back in a while.
Regards, Herman :)

---

### Post by Herman on 2008-03-26
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda3
UUID=ad33d124-e98e-4a84-98fc-3f34900f7d93   /   ext3    defaults,errors=remount-ro 0   1

# /dev/sda1
UUID=505D-7FF3  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0       2

# /dev/sda5
UUID=D55F-0085  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       2

# /dev/sda6
UUID=7B0F-B764  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       2

#/dev/hda7    
UUID=1ABC0253BC022A39  /media/[COLOR=Red]sda7[/COLOR] ntfs ro,umask=0002,nls=utf8    0      0

# /dev/sda9
UUID=36AC6F2EAC6EE7B7  /media/[COLOR=Red]sda9[/COLOR] ntfs ro,umask=0002,nls=utf8    0      0

# /dev/sda8
UUID=[COLOR=Red]f7b2014a-7159-4abf-8b35-20524c529edd[/COLOR] none            swap    sw    0       0

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
``` :) Okay, metaphongtov,
I hope this will be a better /etc/fstab file than you had before.
You will need to make your own mount points in /media or wherever you want for your two NTFS file systems.
I didn't see your swap area's UUID, so I used the same one as you had before, I hope that's still right. 

Regards, Herman :)

---

### Post by metaphongtov on 2008-03-28
I used the code you give me.It's not better.U can check 2 screens I captured below:

[http://i47.photobucket.com/albums/f163/metaphongtov/23-2.jpg]("http://i47.photobucket.com/albums/f163/metaphongtov/23-2.jpg")

[http://i47.photobucket.com/albums/f163/metaphongtov/12-2.jpg]("http://i47.photobucket.com/albums/f163/metaphongtov/12-2.jpg")

Could u find any more error in them?

---

### Post by Herman on 2008-03-28
> I used the code you give me.It's not better.U can check 2 screens I captured below:

[http://i47.photobucket.com/albums/f1...ngtov/23-2.jpg]("http://i47.photobucket.com/albums/f163/metaphongtov/23-2.jpg")

[http://i47.photobucket.com/albums/f1...ngtov/12-2.jpg]("http://i47.photobucket.com/albums/f163/metaphongtov/12-2.jpg")

Could u find any more error in them?The first photo still shows your boot sector in partition 1  is still not matching the backup boot sector as you complained about already back in post # 5.
Did you try to fix it the way I explained in the link in post #6?
Here is the same link again,  [When the bootsector is not the same as its backup]("http://users.bigpond.net.au/hermanzone/p10.htm#differences_between_the_bootsector_and_its_backup") . :)

The second photo show that you have edited your /etc/fstab file, but you obviously didn't understand what I said about making your own mount points, of you forgot.
I'll explain a little about 'mount points' for you.

A 'mount point' is a directory for the file system you want to mount.
You can make a mount point anywhere, but the normal places for a mount point are either in your /mnt directory or in your /media directory.
In Ubuntu, we prefer the /media directory, and if we use that one we usually get an icon for the mounted file system on our desktops. That's convenient for most people.
To make a mount point in /media, you need to use a 'sudo' command.
You can think of any name you like for your mount point.

Let's say we'll just call your two mount points 'sda7', and 'sda9' then.
```
sudo mkdir /media/sda7
``````
sudo mkdir /media/sda9
```That should fix the problem you have shown in the second photo.

Sorry about not explaining that the first time, maybe I was running late for work or something like that, so I needed to finish the post in a hurry.  I guess I should have been more verbose. Sorry.
If there is something you can't understand, don't be shy or embarrassed to ask and someone around here will help. :)

Regards, Herman :)

---

### Post by metaphongtov on 2008-03-31
Woo all my partitions are automounted now.Thanks Herman so much.You've done a great job.The remaining problem is the differences between boot sector and its back up.I dun understand much on the page u recommended me.I hope u can explain more detail here. :);-);-);-);-)

---

### Post by Herman on 2008-03-31
:) Okay, a 'boot sector' is the first sector of a partition.

If the partition has a Microsoft Windows operating system in it, then when the computer boots up, the BIOS looks at the MBR, which is in the first sector of the hard disk, and code in the MBR directs the BIOS to the boot sector of whichever partition contains the Microsoft Windows operating system.
Code in the boot sector then directs the BIOS to the boot loader and necessary booting files inside the file system and the system boots up, (hopefully).
So, the boot sector is a stepping stone in the boot process of Microsoft Windows operating systems.

Microsoft Windows operating systems can not normally be booted if the boot sector is damaged, so with that in mind, many viruses were invented by mischevious people which target the boot sector and prevent Windows from being able to boot. 

Because the boot sector is so important, a backup of the boot sector is located a few sectors from the boot sector in the FAT32 file system, (I think it's in sector number 6), or at the end of the partition in an NTFS file system.

Modern viruses don't stop Windows from booting, they let Windows boot up, but they install virus code somewhere and a little code in the boot sector to direct Windows to boot via the viruse's program. Mostly that lets Windows seem to boot normally, but secretly in the background it's doing whatever the virus program tells it as well. Maybe it's doing work for someone else on the internet, or standing by ready to participate an attack on a website somewhere.

That's why it's a good idea for you to be alerted to the fact that the boot sector is not the same as it's backup. You may want to do something about it. Like re-install Windows, or better still, get rid of Windows and just use Ubuntu.

Very often, the boot sector not matching its backup is because of a normal operation that you might remember doing and may be harmless. There is a slightly different boot sector for Windows 95, Windows 98, Windows ME, XP and so on. 
If you ever had booting trouble and ran the FIXBOOT command from a Windows 'recovery console', or 'sys c:' from a Windows boot floppy, you would have fixed the boot sector, but the new one might not be identical to the old one. In that case, the difference would be harmless. There may be a few other situations like that where Microsoft or some innocent program alters it's own boot sector for some reason too. I'm not sure about that, but it's conceivable. I guess you would need to ask a Microsoft expert for more help with that possibility.

If you want to Ubuntu ignore the Windows boot sector, just change the last '2' in the line for that file system in /etc/fstab to a '0' and Ubuntu will skip checking that partition when it boots up.
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

# /dev/sda3
UUID=ad33d124-e98e-4a84-98fc-3f34900f7d93   /   ext3    defaults,errors=remount-ro 0   1

# /dev/sda1
UUID=505D-7FF3  /media/sda1     vfat    defaults,utf8,umask=007,gid=46 0 [COLOR=Sienna]**      0**[/COLOR]

# /dev/sda5
UUID=D55F-0085  /media/sda5     vfat    defaults,utf8,umask=007,gid=46 0       2

# /dev/sda6
UUID=7B0F-B764  /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       2

#/dev/hda7    
UUID=1ABC0253BC022A39  /media/sda7 ntfs ro,umask=0002,nls=utf8    0      0

# /dev/sda9
UUID=36AC6F2EAC6EE7B7  /media/sda9 ntfs ro,umask=0002,nls=utf8    0      0

# /dev/sda8
UUID=f7b2014a-7159-4abf-8b35-20524c529edd none            swap    sw    0       0

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
```Regards, Herman :)

---

