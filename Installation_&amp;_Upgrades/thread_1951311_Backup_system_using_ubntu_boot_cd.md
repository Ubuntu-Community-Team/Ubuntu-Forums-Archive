---
title: "Backup system using ubntu boot cd"
date: 2012-04-02
forum: Installation &amp; Upgrades
---

### Post by shumifan50 on 2012-04-02
I would like to know if a backup made, using tar, of the relevant partitions, while booted off an Ubuntu CD, could be used to restore over a new system built (with a proper install off the Ubuntu CD).
Mostly I am interested to know whether this would restore all the 'other' installed software and settings e.g mysql etc. This of course assuming all partitions have been backed up by mounting them and then backing them up using tar.
I used to use PING, but it does not support (PARTImage) ext4 file systems and is now useless as I built my server using ext4.

Basically, does a boot off the CD make any files in-use on the hard disks.

---

### Post by sudodus on 2012-04-02
> **shumifan50 said:**
> I would like to know if a backup made, using tar, of the relevant partitions, while booted off an Ubuntu CD, could be used to restore over a new system built (with a proper install off the Ubuntu CD).
Mostly I am interested to know whether this would restore all the 'other' installed software and setting e.g mysql etc. This of course assuming all partitons have been backed up by mounting them and the backing them up using tar.
I used to use PING, but it does not support (PARTImage) ext4 file systems and is now useless as I built my server using ext4.

Basically, does a boot off the CD make any files in-use on the hard disks.

A boot off the CD ***does not*** make any files in-use on the hard disks.

The way I have been using tar, it is only saving the content of the partitions, not the partition table and and not the file systems. So if you have not changed the partitions and their file systems, you can restore linux from your tarball. If you have changed that, you might have to restore grub too. But I'm not sure it works for Windows (I don't think tar can backup Windows, correct me if I am wrong).

For the future I would suggest that you use Clonezilla. I used PING, and when I started to use ext4, I found Clonezilla, that is using Partclone to image partitions. It can clone/image ext4 (as well as what PartImage can manage). Clonezilla is much faster than PING. But for my data partition with many big files I use Unison to sync it with a directory on the backup drive. Unison is using rsync. Rsync itself is a good alternative to tar.

---

### Post by CharlesA on 2012-04-02
+1 to what sudodus has said. I used to use PING as well, but switched to Clonezilla when I started using ext4 (and haven't looked back).

I use rsync to backup my home server to external media, which works fine for data.

---

### Post by shumifan50 on 2012-04-02
Hi Guys,
Thanks for the very quick response. I will look at clonezilla, but the thing about a tarball is that i can be moved between file systems (ext4 to ext3 for example) as it only restores files. So I guess there is romm for each depending on requirements.
Thanks again.

---

### Post by Jahid65 on 2012-04-02
You can use fsarchiver. You can use it instead of tar (with savedir option)
 

 **Advantages**
 

 
[LIST=1]
[*]Mulch-threaded
[*]Do check-sum of your archive 	during backup
[*]can create password-protected 	archive
[/LIST]
 

 

 **Disadvantages**
 

 
[LIST=1]
[*]Archive Can not be viewed with any 	types of apps
[*]If you use savefs option during 	backup, then after restoring the root partition ( with resfs option) you may have to 	restore the grub
[*]Need to use live cd (having 	fsarchiver installed) or other Linux distro installed in your PC to 	restore root partition(iif you use savefs option)

[/LIST]
**similar to tar**
```
fsarchiver -j4 -o -vv -L 'opensuse-root' savedir /windows/E/Backup/opensuse_sys_backup_tar$(date +%d-%m-%Y).fsa / --exclude=/home --exclude=/lost+found --exclude=/proc --exclude=/sys --exclude=/media --exclude=/mnt --exclude=/windows --exclude=/tmp
```

**For restoring**
```
fsarchiver -j4 -o -vv restdir source_of_backup_arfchive.fsa /
```


**With savefs option**
```
fsarchiver -j4 -o -vv -A -L 'opensuse-root' savefs /windows/D/Backup/opensuse_sys_backup$(date +%d-%m-%Y).fsa /dev/sda7
```


**restore with restfs option**
```
fsarchiver -j4 -o -vv -A restfs /windows/D/Backup/opensuse_sys_backup$(date +%d-%m-%y).fsa id=0,dest=/dev/sda7
```
type the following command in terminal for more help
```
man fsarchiver 
```

---

### Post by CharlesA on 2012-04-02
> **shumifan50 said:**
> Hi Guys,
Thanks for the very quick response. I will look at clonezilla, but the thing about a tarball is that i can be moved between file systems (ext4 to ext3 for example) as it only restores files. So I guess there is romm for each depending on requirements.
Thanks again.
True, perhaps. The same can be said for rsync, but you'd need to copy the files to the new file system.

---

### Post by shumifan50 on 2012-04-03
Restoring the tarball causes a boot problem as it overwrites the grub configuration and the UUID of the disks don't match, so booting fails with disk not found. So at least /boot/grub/menu.lst must be saved from the original install on the new target disk to ensure the UUIDs match.
Fixng this after the event seems more difficult than I expected as entering 'e' to edit the menu allos editing but after hitting 'CTRL-s' and 'CTRL-x' the file reverts back to the orginal UUIDs even though I had changed them to reflect the new install UUIDs and not the ones restored from the tarball.

Are there any other files that affect the boot process?

Note on Maverick I could not find menu.lst only grub.cfg that should not be editied.

---

