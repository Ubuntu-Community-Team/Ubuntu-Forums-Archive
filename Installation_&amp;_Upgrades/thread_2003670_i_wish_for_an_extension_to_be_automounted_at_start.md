---
title: "i wish for an extension to be automounted at startup..."
date: 2012-06-14
forum: Installation &amp; Upgrades
---

### Post by shantiq on 2012-06-14
.....   how can i work out the command   to enter in startup applications   [i have all my music on the partition and players will not starts until it is mounted which only requires double-clicking on partition but i would like it to automount at startup

[ATTACH]219695[/ATTACH]


i have tried   sudo mount /media/777a9ed8-803f-42d0-af07-c03b98c26ba2


and   sudo mount   /dev/sda1/media/777a9ed8-803f-42d0-af07-c03b98c26ba2



and neither work

[B]Writing this it is stares me in the face that with sudo it could not since password will be required
[/B]


so how can do this?         i hope it does not involve rewriting the Talmud into Albanian:KS




if there is a manageable way to do this i will love to hear it     ..   shan

---

### Post by ajgreeny on 2012-06-14
It depends on the filesystem type of the partition; fat32, ntfs, ext#.

You will need to add a line for the partition to /etc/fstab so open that with root permissions ```
gksu gedit /etc/fstab
```and add one of the following lines to the file, amended to your fit own disk names/UUIDs, etc etc. and after making the mount point folder **media** in your home so the music files will show there, rather than in /media in the root filesystem.
```
#Automount linux partition. Add line to /etc/fstab:-
UUID=66E53AEC54455DB2 /home/user/media ext3 defaults, relatime 0 1

#Automount fat32 partition. Add line to /etc/fstab:-
UUID=66E53AEC54455DB2 /home/user/media vfat defaults,user,dmask=027,fmask=137 0 0

#Automount ntfs partition. Add line to /etc/fstab:-
UUID=66E53AEC54455DB2 /home/user/media ntfs nls=utf8,umask=0222 0 0
or
UUID=66E53AEC54455DB2 /home/user/media  ntfs    defaults    0    0
```

---

### Post by shantiq on 2012-06-15
thank you aj    i do not understand much of this



 gksu gedit /etc/fstab



gives me this


> # /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=eec8a741-3a68-4891-b8ea-ae1b04876bdf /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=96539b44-e44d-4076-892a-76dda9280424 none            swap    sw              0       0
/dev/sr0   /media/cdrom0   udf,iso9660  user,noauto,exec   0 0



can you see what i need to add precisely here  ??           sorry i find all this very cryptic   i have never looked at this before

---

### Post by ajgreeny on 2012-06-16
OK, I could not get your attachment to work last time, but now I can see it.

First make a mountpoint folder in /media with command ```
sudo mkdir /media/media
``` and back up your current fstab file with ```
sudo cp /etc/fstab /etc/fstabbak
```You then need to open your /etc/fstab file again with terminal command as above then add these two lines and save the file.
```
# media partition on sda1
UUID=777a9ed8-803f-42d0-af07-c03b98c26ba2 /media/media ext4 defaults,relatime 0 2
``` Now use command ```
sudo mount -a
```Hopefully no error messages will appear, and depending on your desktop environment, a new icon may appear on the desktop labelled **media**

Come back again if needed.

---

### Post by shantiq on 2012-06-16
ok did this


it placed a link on desktop for the 196Gb partition    but did not help with the folders within



the Music is all in


/media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music


so it looks as if it mounted the partition but not the folders in it



in fact the players then could not see the files in the Music folder so i deleted the addition to fstab     until   i understand more


what can i try next here?

---

### Post by ajgreeny on 2012-06-16
What was the folder name that you made in media?

How is the icon on Desktop labelled?  If the mountfolder you made was called media I think that is how it would show, but I may be wrong about that.

How were the folders including the Music folder in that partition made and who is the owner of the files?  I suspect the folder and files are owned by another user so you may not be able to see them. It may need nothing more than a terminal command to make you the owner of the mount folder for the partition you made earlier.
```
sudo chown username:username /media/777a9ed8-803f-42d0-af07-c03b98c26ba2/Music
```Again more info is needed, which may help sort out the problem.

---

