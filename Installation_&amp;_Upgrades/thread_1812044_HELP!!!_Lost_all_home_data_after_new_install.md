---
title: "HELP!!! Lost all /home data after new install"
date: 2011-07-25
forum: Installation &amp; Upgrades
---

### Post by Andre305 on 2011-07-25
I decided to do a fresh install from mavrick to natty. I had 4 partitions in my previous setup. /, /usr, /home, and a swap. I identified all the drives before installation and took special care to only fomat the / drive. I wanted to leave the /usr and /home drives intact since they had all saved data and programs. Now when I log into my fresh install all my information is GONE! My partition scheme is still the same minus all of my data. 

Is there any way to recover all my /usr and /home data?

---

### Post by oldfred on 2011-07-25
Post this and if you know what is in each partition. Or if you labeled the partitions the blkid will show labels also:

```
sudo fdisk -lu
sudo blkid
```Also post contents of /etc/fstab

When you want to reuse partitions you have to tell the installer to use them but then be careful not to reformat.

---

### Post by Kira_Belka on 2011-07-25
> **Andre305 said:**
> I decided to do a fresh install from mavrick to natty. I had 4 partitions in my previous setup. /, /usr, /home, and a swap. I identified all the drives before installation and took special care to only fomat the / drive. I wanted to leave the /usr and /home drives intact since they had all saved data and programs. Now when I log into my fresh install all my information is GONE! My partition scheme is still the same minus all of my data. 

Is there any way to recover all my /usr and /home data?

I think testdisk utility can do it ... but mmmm.. I can work with ext4 a bit ...mmmmm.. not so well as with ext2,ext3 or ntfs,fat..

---

### Post by grahammechanical on 2011-07-25
Did you remember to give /usr, /home and /swap a mount point? Other wise the install would have put everything into the choosen / partition and not connected those other partitions into its file structure. I am just asking to eliminate a possibility.

Regards.

---

### Post by Andre305 on 2011-07-25
ok...

_**sudo fdisk -lu**_

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000286fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    19531775     9764864   83  Linux
/dev/sda2        19533822   488396799   234431489    5  Extended
/dev/sda5        19533824    66406399    23436288   83  Linux
/dev/sda6        66408448   484377197   208984375   83  Linux
/dev/sda7       484378624   488396799     2009088   82  Linux swap / Solaris

_**sudo blkid**_

/dev/sda1: UUID="4f5cc51f-311a-4d09-a025-549496147540" TYPE="ext4" 
/dev/sda5: UUID="274adcfe-1c16-41c2-b01b-f60adffdb999" TYPE="ext4" 
/dev/sda6: UUID="ba8379eb-27f9-4391-a0a1-0d43365598d8" TYPE="ext4" 
/dev/sda7: UUID="0b28f05f-f660-4949-a513-a851742f4b43" TYPE="swap"

---

### Post by Andre305 on 2011-07-25
oh... and everything IS mounted in disk utility. I took special care to identify each partition and mount it when I did my new installation. Only the / was checked with the format option.

---

### Post by oldfred on 2011-07-25
Need to see fstab to confirm that it is mounted. Are sda5 & sda6 your "Missing" partitions?

You may just need to add to fstab. If so you must not have included them in the install screen to be mounted but not formated. If data is missing from those partitions then that is a bigger issue.

---

### Post by Andre305 on 2011-07-25
I noticed this when I ran testdisk. No idea what it means though but I suspect it might be my old data. Thoughts?[IMG]http://i764.photobucket.com/albums/xx284/drdistruct0/Screenshot-andreandre-1005PE.png[/IMG]

---

### Post by psusi on 2011-07-25
You can not retain programs in /usr across a reinstall.  The whole point of the reinstall is to wipe out the system and install a new one.  Your /home should be there though.  Does mount show the partition in question as mounted in /home?  And I assume that you used the same username as before?

---

### Post by Andre305 on 2011-07-25
> **psusi said:**
> You can not retain programs in /usr across a reinstall.  The whole point of the reinstall is to wipe out the system and install a new one.  Your /home should be there though.  Does mount show the partition in question as mounted in /home?  And I assume that you used the same username as before?

Its mounted. Same username too. Although now my computer name is andre-1005PE instead of simply andre.

---

### Post by oldfred on 2011-07-25
If you are booted into you install you can see what is mounted by default.

gksudo gedit /etc/fstab

Post a copy of fstab.

---

### Post by Andre305 on 2011-07-26
_**fstab**_

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=4f5cc51f-311a-4d09-a025-549496147540 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=ba8379eb-27f9-4391-a0a1-0d43365598d8 /home           ext4    defaults        0       2
# /usr was on /dev/sda5 during installation
UUID=274adcfe-1c16-41c2-b01b-f60adffdb999 /usr            ext4    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=0b28f05f-f660-4949-a513-a851742f4b43 none            swap    sw              0       0

---

### Post by Elfy on 2011-07-26
If you do 

ls /home

Does it show andre ?

---

### Post by Andre305 on 2011-07-26
> **forestpiskie said:**
> If you do 

ls /home

Does it show andre ?

it surely does

---

### Post by otto67at on 2011-07-26
You can try [http://www.ufsexplorer.com/rdr_ext23.php](http://www.ufsexplorer.com/rdr_ext23.php) from a lifefilesystem or booted from a seperate disk or usb-drive and see, if it finds any data previosly unseen.
Do you remember a typical filename you can search for with find / -name ?

---

### Post by Quackers on 2011-07-26
What files are missing, do you think?

---

### Post by Andre305 on 2011-07-26
> **Quackers said:**
> What files are missing, do you think?

200gb of music, videos, documents, photos, etc. my entire /home directory seemingly got wiped.

---

### Post by Andre305 on 2011-07-26
Seriously guys. I'm in the dark here about what I should do. I'm debating a data recovery but I feel like there might be a simpler way to just revert the partition to its previous setting. Any real help would be appreciated.

---

### Post by oldfred on 2011-07-26
When you did the ls  /home did it show more than one? Perhaps andre & Andre? The files may be there just under a different path. Have you explored thoughly?

---

### Post by Andre305 on 2011-07-27
> **oldfred said:**
> When you did the ls  /home did it show more than one? Perhaps andre & Andre? The files may be there just under a different path. Have you explored thoughly?


It only shows one path to andre. Don't know of other paths or how to search them. Nothing I have tried so far works. Keep in mind that I'm a bit of a noob to the inner linux workings. 

I was under the impression that by creating 3 partitions initially that I wouldn't have had to worry about this kind of issue. one for the file system, other for the programs, and lastly for my files. Damn computer does what I tell it to do and never what i WANT it to do...

---

### Post by oldfred on 2011-07-27
If you really did tick format by mistake then about the only way to recover some data is to use tools to scan partition. Very tedious, requires space to copy files to, and does not recover full file names, but some type can be rebuilt.

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
How to recover lost files after you accidentally wipe your hard drive
[http://www.linux.com/archive/feed/56588](http://www.linux.com/archive/feed/56588)

[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by Andre305 on 2011-07-27
Awesome resources for recovery. Thanks. Although I know for a fact that I did not reformat it. Made very sure not to click it and rechecked it multiple times. Any other thoughts? Maybe a way to revert to my other partitions to my pre installation settings? I'm really hoping I wont have to go through the mess of a recovery.

---

