---
title: "Mounting a FAT32 partition that previously was NTFS."
date: 2006-11-01
forum: Installation &amp; Upgrades
---

### Post by davidsolar on 2006-11-01
Hi.. I'm a one week newbe-user of Ubuntu and have this problem I'm not used to from the plug n'play world of Windows. 
My Linux dedicated HDD has 3 partitions: ext2, Swap and one NTFS. Yesterday I went in Windows and changed the NTFS partition to FAT32 for easier synch between the two OS's.
As you probably know, Linux cant autoupdate this. But I did a little research on mounting. But nothing really happend when I followed the guides. 

This is how my fstab file looks like:
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdc2
UUID=8ff54508-de53-47ce-9a61-e006c35f6d85 /               ext2    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=127C449C7C447C8B /media/hda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda5
UUID=FC2089D1208992F6 /media/hda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb1
UUID=AAD0A38FD0A35FF5 /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc5
UUID=76D048DBD048A36B /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdc3
UUID=cfe05625-b84f-495e-9e7c-db88f66cba67 none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
```

On the device manager the FAT32 partition is called "hdc5" and I have a hdc5-directory in the /media and find it in /dev.  
So....... any suggestions? 
I did try to change the "ntfs" tag there into both "FAT32" and tried $sudo mount -a

Dave

---

### Post by Beaucephus on 2006-11-01
Have you tried changing NTFS->FAT32 in your /etc/fstab file?

Do you know why there are so many NTFS drives listed in fstab?  

I would think all you had to do was change the formatting in windows and then update fstab.

---

### Post by davidsolar on 2006-11-01
There are many NTFS drives because I have 3 HDD's hehe.. but now I have tried to write both "vfat" and "fat32" instead of the "nfts" tag. AND removed the long tag after "/dev/hdc5" . The terminal told that the "UUID=76D048DBD048A36B" could not be found.

before:
```
# /dev/hdc5
UUID=76D048DBD048A36B /media/hdc5     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
```
after:
```
# /dev/hdc5 /media/hdc5     FAT32    defaults,nls=utf8,umask=007,gid=46 0       1
```

But what is the thing to do now? I write $sudo mount -a. But guess this isn't enough? Have a feeling i have to tell Ubuntu something else =)

---

### Post by davidsolar on 2006-11-01
Jehoo..progress. Now I've done: $mount -t vfat /dev/hdc5 /media/hdc5
And it finally shows FAT32 and ~90GB when I do properties on the /media/hdc5 folder. It only showed ~5GB before.

But now it only remain to get it on the desktop and filebrowser.

---

### Post by davidsolar on 2006-11-01
-

---

### Post by davidsolar on 2006-11-01
okay.. progress is really cool. Love this now =) 
BUT.. when I restart I have to mount the hdc5 every time. :(

I do this: ```
$sudo mount -t vfat /dev/hdc5 /media/hdc5
```
Then : ```
$sudo chmod -R 777 /media/hdc5
```

I can now write and read on the partition through the /media/hdc5 folder, but still not see it on the desktop or "Places". 

The /etc/fstab file has this line for this drive:
```
# /dev/hdc5 /media/hdc5     vfat    defaults,nls=utf8,umask=007,gid=46 0       0  
``` 

Any clue what the problem is?

Dave.

---

### Post by Beaucephus on 2006-11-01
Found everything you need here.  Following this will meet your objectives of an automatically mounted drive that shows up in places.

[http://www.ubuntuforums.org/showthread.php?t=271403&highlight=places]("http://www.ubuntuforums.org/showthread.php?t=271403&highlight=places")

---

### Post by davidsolar on 2006-11-02
Thanks a lot for the help Beaucephus. Very appreciated!   /bow
But the thing is that whatever I tried, the partition never wanted to be mounted like the others :-k 

I did eventually get permission to read from the /media/hdc5 folder. But never got it to show on the desktop or "places". I got write permission as a root in the terminal as well. But even if I wrote in the /etc/fstab file, I had to manually mount it on every reboot.

Sooooo.. after 3 days of struggle I took a shortcut and did a clean Ubuntu install. Now everything works like a charm! <3 ubuntu, though I wonder why there can't be an application simular to the partitionmanager we use during the installation avaliable here in Gnome. But guess my knowledge of how things work isn't Class-A yet. Anyway, love learning and using this OS I must say I do!

Here is a sample of the fstab file now that I've done the new install. Maybe the "UUID=4547-BC75" part made the whole difference?

```
# /dev/hdc5 UUID=4547-BC75  /media/hdc5     vfat    defaults,utf8,umask=007,gid=46 0       1
```



Dave

---

