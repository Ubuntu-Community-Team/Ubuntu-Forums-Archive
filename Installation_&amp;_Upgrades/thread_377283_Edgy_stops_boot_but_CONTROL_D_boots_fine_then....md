---
title: "Edgy stops boot but CONTROL D boots fine then..."
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by entropyfoe on 2007-03-05
Recently installed Edgy (xubuntu 6.10) from alternate CD.

When booting, processes stops with this error:

file system check failed
please repair file system manually

with the log produced:

Log of fsck -C -R -A -a 
Mon Mar  5 21:37:27 2007

fsck 1.39 (29-May-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda6: 218 files, 2441/1638912 clusters
fsck.ext3: Unable to resolve 'UUID=0394e102-716f-4635-8e86-0c2dedd6e43c'

fsck died with exit status 

I press CONTROL-D, and everything boots fine.  xubuntu is great, I just want to fix this error for faster boot.  How can I get it to see dev/sda6 correctly?  I think this is a vfat partition I have for transfer from ntfs partition to linux and back to the windows world.

Do I just edit fstab?
How so?

Thanks
Jay

---

### Post by Herman on 2007-03-06
Hello entropyfoe,
This is normally due to removing one of your filesystems (partitions) since you installed Ubuntu. 
Your /etc/fstab file still has the UUID for this filesystem in its list of files the operating system is supposed to look for during startup and check to make sure they are okay to mount. Since you have removed this filesystem, the operating system is missing it and it is protesting by halting with an error message during boot-up.. 

 To fix this you need to update /etc/fstab and the only way I know is to do this manually. Here's how to open the file with mousepad in Xubuntu,
```
sudo mousepad /etc/fstab
```Look for a line in your /etc/fstab file with this UUID nuimber, UUID=0394e102-716f-4635-8e86-0c2dedd6e43c
You might want to 'hash out' that line for now, (so it will not be read by the operating system).

If you have added a new filesystem in place of the one you deleted and you want to add the UUID number for that to /etc/fstab, now is a good time to do so. When you do that, it will be automatically mounted on each boot-up. Most people like that.
You need to create a mount point for the filesystem to be mounted in /media if you don't have one already. For example, maybe I want to mount a filesystem (partition) and I want to call it 'data_share'. I would make a directory for it with a command like this,
```
sudo mkdir /media/data_share
```Now you need a list of your partitions, it would be best to open a terminal in a different desktop for that, and it is also best to expand it to the full size of your monitor.
```
sudo fdisk -lu
```Under that, in order to get a list of the UUID numbers that identify the filesystem in the partitions,
```
ls /dev/disk/by-uuid/ -alh
```Now you can copy one of these UUID numbers from the terminal and change desktops to the one where you left your /etc/fstab file open and and paste the UUID number into the file. 
Make sure the other details for the entry for the filesystem are all appropriate and correct.
Remove the hash mark from the line when you want it to be read by the operating system.

Remember to save the file before closing it. That's it! :)\

Regards, Herman

---

### Post by entropyfoe on 2007-03-10
Herman,
Thanks for the detailed information.  But I think I have something else going on.
I ls by-uuid, but I do not see the uuid that is displayed in the fsck error message that I goto below in var/logs/fsck.

So why is a fsck being done that fails on this non-existant partition uuid???

entropyfoe@AMDX2:/$ ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 180 2007-03-09 23:18 .
drwxr-xr-x 6 root root 120 2007-03-09 17:17 ..
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 0A1C4A8B1C4A71AD -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 50E7-D052 -> ../../sda6
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 8234dbf9-8a8e-453a-93ed-f7639eaa9817 -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 9f2636f7-1c9e-4548-87cb-c8c2c1853b5b -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 A8DF-A4CF -> ../../sdb2
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 C000FDB200FDAF90 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 cc4da848-c86c-4663-86fa-d7877ae6b441 -> ../../sda3


entropyfoe@AMDX2:/var/log/fsck$ cat checkfs
Log of fsck -C -R -A -a 
Fri Mar  9 23:18:05 2007

fsck 1.39 (29-May-2006)
fsck.ext3: Unable to resolve 'UUID=0394e102-716f-4635-8e86-0c2dedd6e43c'
fsck died with exit status 8

Here is fstab-

entropyfoe@AMDX2:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cc4da848-c86c-4663-86fa-d7877ae6b441 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C000FDB200FDAF90 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=0394e102-716f-4635-8e86-0c2dedd6e43c /media/sda2     ext3    defaults        0       2
# /dev/sda6
UUID=50E7-D052 /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sdb1
UUID=0A1C4A8B1C4A71AD /media/sdb1     ntfs    
d up.defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sda5
UUID=6b30f057-070b-4c2e-8731-5c4dbbf7be21 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0



Either I am missing something, or something does not add up here.  The boot stops and a shell is terminated by CONTROL-D, with the log error message generated.
Then the boot is fine afterwards.

-Jay

---

### Post by rsambuca on 2007-03-10
You have to change the UUID for sda2 in your fstab to the UUID as listed in the ls command.  Fix that and you are good to go.

---

### Post by Herman on 2007-03-10
Yeah, that's right.
I made  bold and red the lines that I want to bring to your attention in your UUID list.
```
 entropyfoe@AMDX2:/$ ls /dev/disk/by-uuid -lah
total 0
drwxr-xr-x 2 root root 180 2007-03-09 23:18 .
drwxr-xr-x 6 root root 120 2007-03-09 17:17 ..
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 0A1C4A8B1C4A71AD -> ../../sdb1
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 50E7-D052 -> ../../sda6
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 **[COLOR=Red]8234dbf9-8a8e-453a-93ed-f7639eaa9817[/COLOR]** -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 **[COLOR=Red]9f2636f7-1c9e-4548-87cb-c8c2c1853b5b[/COLOR]** -> ../../sda5
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 A8DF-A4CF -> ../../sdb2
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 C000FDB200FDAF90 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-03-09 23:18 cc4da848-c86c-4663-86fa-d7877ae6b441 -> ../../sda3
```I made bold and  blue here (below), the lines that are out of date and need to be fixed in your /etc/fstab file. 
See? One of them is the one mentioned in your error message. I also noticed that your swap area is not being mounted, you should fix that one too.
```
 entropyfoe@AMDX2:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cc4da848-c86c-4663-86fa-d7877ae6b441 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C000FDB200FDAF90 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=[COLOR=Navy]**0394e102-716f-4635-8e86-0c2dedd6e43c**[/COLOR] /media/sda2     ext3    defaults        0       2
# /dev/sda6
UUID=50E7-D052 /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sdb1
UUID=0A1C4A8B1C4A71AD /media/sdb1     ntfs    
d up.defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sda5
UUID=[COLOR=Navy]**6b30f057-070b-4c2e-8731-5c4dbbf7be21**[/COLOR] none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```I have made bold and red, (below), where you would want to paste the current UUID numbers from your UUID list. You should copy those from your UUID list, and go to your /etc/fstab file. Highlight the old out of date numbers and paste the new ones over the top of the old UUID numbers, to replace the old out of date information that is there. 
```
 entropyfoe@AMDX2:/etc$ cat fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda3
UUID=cc4da848-c86c-4663-86fa-d7877ae6b441 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=C000FDB200FDAF90 /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda2
UUID=[COLOR=Red]**8234dbf9-8a8e-453a-93ed-f7639eaa9817**[/COLOR] /media/sda2     ext3    defaults        0       2
# /dev/sda6
UUID=50E7-D052 /media/sda6     vfat    defaults,utf8,umask=007,gid=46 0       0
# /dev/sdb1
UUID=0A1C4A8B1C4A71AD /media/sdb1     ntfs    
d up.defaults,nls=utf8,umask=007,gid=46 0       0
# /dev/sda5
UUID=**[COLOR=Red]9f2636f7-1c9e-4548-87cb-c8c2c1853b5b[/COLOR]** none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```That should be okay now, don't forget to 'save' the file and close it. Reboot for the changes to take effect. Your /etc/fstab file will now be up to date. 

You should be able to boot smoothly from now on, except once in a while when a filesystem comes due for a filesystem check. Possibly you will have one or two due for a filesystem check right away if you have booted them a number of times already and they have been missing being checked. If they do, just be patient and wait for the filesystem check to be finished. Each filesystem will be checked once  every thirty mounts. You should have normal booting most of the time.

Regards, Herman :)

---

### Post by entropyfoe on 2007-03-10
Herman,

Excellent !
Problem solved, thanks.

I want to comment that the support from Ubuntu Forums is excellent, so many helpful people.

I wonder how these UUIDs get fouled up?  These were automatically generated.

Xubuntu is so fast. 

 Now  to just get my old HP 4200C scanner working!  I synaptic got sane.  I'll post in another forum.  Thanks again.
I think it so important to post the solutions that work, so others can find them.  I always try and do that, as previous posts have been helpful to me to for example get the nvidia driver working, of edit my grub/menu.lst.

-Jay

---

### Post by Herman on 2007-03-10
>  I wonder how these UUIDs get fouled up?  These were automatically generated. Maybe you had another operating system in /dev/sda2 and you re-installed it and it made a new swap area in /dev/sda5 when it was re-installed? That's what I would guess would have happened. That's the type of things that normally does it to my /etc/fstab files anyway. :) 
>  I want to comment that the support from Ubuntu Forums is excellent, so many helpful people. Good co-operation from the people asking the questions is vital as well. That's the most important of all! Thank you for your excellent replies and co-operation. 

Yes, Ubuntu is really catching on extremely fast. Almost everyone has special abilities that they can bring to the community, so the more new users we existing users can help, the better it makes the whole group. Everyone is welcome, even if you just feel like having fun and learning stuff and spreading the word. 

In the last couple of days about 640 per day joined the Ubuntu Web Forums, up from 577 per day for the last month, and that's up from an average of 475 per day a couple of months ago. That's a heck of a lot of installing going on out there! Ubuntu is really taking off! :)

Good luck and have fun and all the best, Regards, Herman :)

---

### Post by PseudoRasta on 2008-04-17
thank you both , i have had  similar problems on and off  for close to a year now , (no internet, no forum) with my constantly reinstalling different os's  and was of the mind that if it aint completley broke , dont try fix it .

well thanx to this post i am able to fix it .
thank you

---

### Post by Herman on 2008-04-17
:) Cool! Good to hear it! 
Thanks for taking the time to let us know, it makes me happy to have helped.
Happy Ubuntuing, PseudoRasta!
Regards, Herman :)

---

