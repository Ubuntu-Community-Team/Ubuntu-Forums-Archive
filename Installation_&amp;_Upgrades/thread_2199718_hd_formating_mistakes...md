---
title: "hd formating mistakes.."
date: 2014-01-15
forum: Installation &amp; Upgrades
---

### Post by spiridonios on 2014-01-15
I received my new 1T wd hd, connected the sata and power cables and turned on the machine.
(for some reason i thought the proccess would be easy as plug'n'play, apparently not)

Reading some online tutorials and trying to format/install the new drive I ended up defying it as an extended hd, and when I try to "fix" it I just added 1 partition as a primary..
I got pissed of myself for not reading enough before starting to act and now I hope I 'll be able to do it from the beggining, erasing the partitions I ve created.

First I followed this tutorial [http://www.makeuseof.com/tag/how-to-format-a-new-internal-hard-drive/](http://www.makeuseof.com/tag/how-to-format-a-new-internal-hard-drive/) that seemed quite right. I just decided for some reason to define the partition as extended an when I got to the point to use mkfs I just didnt know to define the number of blocks of the hd.
then I found [https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive), that seems more official and user friendly since it lets you use gparted, but I found out that I m not able to change the "extended" type through gparted..

I d like to do it nice and properly, having only one decent partition, as I want to use the disk as a storage media. I use an ssd for the Os.
I run ubuntu studio 3.8.0-35-lowlatency

Any advice?

---

### Post by grahammechanical on 2014-01-15
Are you saying that Gparted will not let you delete that partition? Will Gparted let you shrink the partition to create unallocated space in front of it? Then create that unallocated space and use it to create a new primary partition and then delete the extended partition and enlarge the single primary partition to take up all the space on the drive. Then instruct Gparted to format the partition. If you are only using Linux then the format can be Ext4. If you need to share data on the partition with a Windows OS then you might want to use Windows tools to format the partition to a Windows format.

Regards.

---

### Post by Bashing-om on 2014-01-15
spiridonios; Hi !

I really like:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

Read the tutorial once more, it is fdisk at it's finest.
The tutorial is directed at making a single partition, there is no need at this time to make that partition "extended" . One may make as many directories with in that one partition as one needs (within the limits of inode allocation -huge).

-fdisk to delete the partition, and fdisk to write a new partition table.
Read for comprehension so you know what those options mean and what you want to do.
Remember this is linux at the command line, it assumes that you know exactly what you are doing. It will happily comply and - if there are errors in your logic - will also happily destroy the operating system.
Additional info:
```

man fdisk

```

[INDENT][INDENT]a piece of cake
[/INDENT][/INDENT]

---

### Post by spiridonios on 2014-01-15
Ok. I followed [**[COLOR=#000000][/COLOR]**[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1087323")Grahammechanical's advice and now it did work, meaning that now I got one primary partition :). I cant seem to create a folder in the disk though..
I ll read the tutorial mentioned by Bashing-om[[COLOR=#000000][/COLOR]]("http://ubuntuforums.org/member.php?u=1111508") above, search some more and refer
thank you people :)

---

### Post by Bashing-om on 2014-01-15
spiridonios; Hanging with you.

Now it sounds like a permission issue ( so you are making great progress).

We need to know your mount point with it's permissions:
Are you mounting the disk automagically from /etc/fstab, or from terminal as "ondemand" ?

Or --- what is your preference for mounting ?

[INDENT][INDENT]we can do this
[/INDENT][/INDENT]

---

### Post by spiridonios on 2014-01-15
thanks a lot bashing-om!

About mounting. Since I see the disk icon on the desktop and I m able to open it, doesn't it means that it is mounted? Furthermore when I right-click on xfce's file manager I got an unmount option availiable, which when I click I got the hd icon disappeared from file manager's interface..

I also followe the afformentioned tutorial's "create a mount point" step, and made a new directory. 
and I also tried a mounting command : mount -t ext4 /dev/sdb /mount_point
Finally, in gparted, I was also able to suposelly mount and unmount my disk.

Something that seems weird is that when i open when right-click(in the opened window of the hd) --> Properties --> Permissions
 i get root as an owner  access: read&write,   group: root  access: read only others: read only

could this restricted permission be related?

---

### Post by Bashing-om on 2014-01-15
spiridonios; Well, like this;

To make a change in the operating system ya got to have the elevated privileges to do so.
OK ? so ya did a "sudo mkdir", now as sudo was invoked, that directory belongs to "root" !.
So what ya want to do is change the ownership of the directory(s) to "you".
```

sudo chown  <username>:<username> <mount_point>

```
for example:
> 
sudo chown sysop:sysop /mnt/backup

Your username and mount_point will be different, adjust accordingly,

All about permissions:
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

And hey !
[INDENT][INDENT]you are going to be the master of your system
[/INDENT][/INDENT]

---

### Post by spiridonios on 2014-01-15
I did previously sudo mkdir /media/myvolume
then i did sudo chown myusername:myusername /media/myvolume

The permission didn't really change. I m still not able to copy any file in the hd.
but wasn't I supposed to type sudo chown root:myusername /media/myvolume ( --from=CURRENT_OWNER:CURRENT_GROUP)

then i looked at [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
should i use a command kinda like: chmod +w /media/myvolume    ?

..I think we 're getting there..
\\:D/

---

### Post by spiridonios on 2014-01-15
new information:

the /media/myvolume i' ve created is editible (i can create a folder in it). but when i right-click --> properties in the window i see that i got a space of 110 gb wich is the size of my first(other) disk (ssd)
the hd icon on the desktop has a different path /media/myusername/myvolume. I get the correct volume size on this one, and.. it's still not editible..

---

### Post by Bashing-om on 2014-01-15
spiridonios; uhmmm;
Either one should work, Most depends on the permissions assigned to the target directory.
example, here is what the permissions look like prior to mounting an external device (backup) : 
Keep in mind it is <owner>:<group>, is the group included in the owners world ?
> 
sysop@1310mini:~$ ls -la /mnt
total 24
drwxr-xr-x  6 root root 4096 Sep 15 10:35 .
drwxr-xr-x 22 root root 4096 Jan  4 17:17 ..
drwxr-xr-x  2 [color=blue]root root[/color] 4096 May 19  2013[color=red] backup[/color]
drwxr-xr-x  3 root root 4096 May 29  2013 boot
drwxr-xr-x  2 root root 4096 May 31  2013 temp
drwxr-xr-x  2 root root 4096 Sep 15 10:35 ubie

Now watch what happens:
> 
sysop@1310mini:~$ sudo mount /dev/sdb1 /mnt/backup
sysop@1310mini:~$ ls -la /mnt
total 24
drwxr-xr-x  6 root  root  4096 Sep 15 10:35 .
drwxr-xr-x 22 root  root  4096 Jan  4 17:17 ..
drwxr-xr-x  8 [color=blue]sysop sysop[/color] 4096 Dec 13 13:34 [color=red]backup[/color]
drwxr-xr-x  3 root  root  4096 May 29  2013 boot
drwxr-xr-x  2 root  root  4096 May 31  2013 temp
drwxr-xr-x  2 root  root  4096 Sep 15 10:35 ubie
sysop@1310mini:~$


So in this instance it is the permissions on the target that drive the permissions on the mount point.

So, on the target directory, one may do a number:
```

sudo chown sysop:sysop /mnt/backup

``` to effect the permissions of the mount point.
> 
sysop@1310mini:~$ ls -la /mnt/backup
total 112
drwxr-xr-x 8 sysop sysop  4096 Dec 13 13:34 .
drwxr-xr-x 6 root  root   4096 Sep 15 10:35 ..
drwx------ 2 sysop sysop  4096 May 16  2013 bashin
-rwxr-xr-x 1 sysop sysop  1716 May 16  2013 bbm
drwx------ 3 sysop sysop  4096 May 16  2013 bin
-rw-rw-r-- 1 sysop sysop   174 Mar 13  2013 buntu-autostart
-rwxr-xr-x 1 sysop sysop   571 Aug  4  2012 chglog
-rw-r--r-- 1 sysop sysop  1586 May 16  2013 file_sharing
-rw-rw-r-- 1 sysop sysop  1007 Jun 17  2013 gedit-f.txt
-rw-rw-r-- 1 sysop sysop 28396 May 19  2013 libudev0_175-0ubuntu13_amd64.deb
-rwxr-xr-x 1 sysop sysop  2929 May 16  2013 looksee
drwx------ 2 sysop sysop 16384 Aug  3  2012 lost+found
drwxr-xr-x 2 sysop sysop  4096 Oct  3 18:21 restore
drwxr-xr-x 2 sysop sysop  4096 Dec 22 09:45 save
-rw-r--r-- 1 sysop sysop     0 Apr 15  2013 throwaway
<snip>


Does it make more sense now ?
see:
```

man chown
man chmod

```

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by spiridonios on 2014-01-16
hooray!!
we did it!
I got too tired yesterday, with focus difficulties as a result.
I read your last post and chown man, and I did it correctly:
sudo chown myusername:myusername directory
(yesterday i was typing the directory that i had created in command line, which actually had nothing to do with the real one.
Today i opend the hd icon on the desktop, and copied the directory shown at the top, and I got it!
Bashing-om I love you O:)! you 've been really helpfull and methodic.
see you around

---

### Post by Bashing-om on 2014-01-16
spiridonios; Outstanding !

Glad ya got it all sorted out and up and running.

I look forward to
[INDENT][INDENT]our next adventure
[/INDENT][/INDENT]

---

