---
title: "[SOLVED] failed to mount NTFS drives"
date: 2008-09-10
forum: Installation &amp; Upgrades
---

### Post by Louis de Broglie on 2008-09-10
Hi,

I am a ubuntu user and I do not use windows. But for some reason, i needed to install xp yesterday. So i formatted ubuntu drive and installed xp there but my xp system crashed so I reinstalled ubuntu. Now i see that i can't mount any drive. I suspect it might be a virus problem for which xp crashed( again it's only my guess, i have no idea why it crashed :-p ).

Here is the error message i receive from ubuntu : 

[http://i38.tinypic.com/8z38l0.png](http://i38.tinypic.com/8z38l0.png)

---

### Post by iaculallad on 2008-09-10
Probably you have an unclean shutdown on your windoze OS (If you're dual booted) thus it produce this  kind of error:

On your terminal, as the message displayed:

```
sudo mount -t ntfs-3g /dev/sda8 /media/Others -o force
```

---

### Post by Louis de Broglie on 2008-09-10
I did not dual boot . I did a clean install of windows . Then after the crash i formatted windows and install ubuntu there.

Here is the output of that command : 

> 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/Others: No such file or directory


---

### Post by iaculallad on 2008-09-10
Huh, I'd copied the mount point on your error message and it's not present in your system. Try posting the result of the command below:

```
cat /etc/fstab
```

and

```
sudo fdisk -l
```

---

### Post by Louis de Broglie on 2008-09-10
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=2c79bd70-e27d-4065-9a91-8b2a90ef48a0 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=182f0cd7-26ec-4acd-92f5-01c7b931e27b none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0


here they r :
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0cd70cd6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3562    28611733+  83  Linux
/dev/sda2            3793       19457   125829112+   f  W95 Ext'd (LBA)
/dev/sda3            3563        3792     1847475   82  Linux swap / Solaris
/dev/sda5            3793        7757    31848831    7  HPFS/NTFS
/dev/sda6            7758       11722    31848831    7  HPFS/NTFS
/dev/sda7           11723       15687    31848831    7  HPFS/NTFS
/dev/sda8           15688       19457    30281728    7  HPFS/NTFS

Partition table entries are not in disk order


---

### Post by iaculallad on 2008-09-10
Ow. I forgot, do include what displays with this command:

```
ls -l /media
```

---

### Post by Louis de Broglie on 2008-09-10
Output :

> 
total 8
lrwxrwxrwx 1 root root    6 2008-09-10 20:39 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-09-10 20:39 cdrom0
drwxr-xr-x 2 root root 4096 2008-09-10 20:39 cdrom1


---

### Post by iaculallad on 2008-09-10
On your terminal:

-Create a mount point:

```
sudo mkdir /media/Others
```

and do the mounting:

```
sudo mount -t ntfs-3g /dev/sda8 /media/Others -o force
```

---

### Post by Louis de Broglie on 2008-09-10
Wha ! Man it worked :):):):):):):)

Can you explain what those codes do ? 

The first one creates a directory in /media/Others i think. But what is the necessity ?

I don't understand the second command . Never used so many options when mounting :-p

---

### Post by iaculallad on 2008-09-10
> **Louis de Broglie said:**
> Wha ! Man it worked :):):):):):):)

Can you explain what those codes do ? 

The first one creates a directory in /media/Others i think. But what is the necessity ?

I don't understand the second command . Never used so many options when mounting :-p

The first command will create a mount point for your device ( sda8 ).

```
sudo mkdir /media/Others
```

The seconds command forces the mount command even if errors are incurred.

```
sudo mount -t ntfs-3g /dev/sda8 /media/Others -o force
```

For more info on mount, you could:

```
man mount
```

------------------------------------------------------------------------

If you like you could auto mount your sda8 partition everytime you boot your computer. You have to include it in your fstab file.

Unmount the partition:

```
sudo umount /media/Others
```

Then open fstab for editing:

```
gksudo gedit /etc/fstab
```

and insert the lines of text below on the bottom-most part of the file (Copy and Paste it).

```
/dev/sda8 /media/Others     ntfs    defaults,umask=007,gid=46 0       1
```

Save and Close the file. And, on your terminal again:

```
sudo mount -a
```

---

### Post by Louis de Broglie on 2008-09-10
So if I want to mount all of my ntfs drives when I boot ubuntu , I just add lines for all of them in the fstab ? 

For example if I want to mount drive Backup ( which is sda7 i think ) the required line will be :

> 
/dev/sda7 /media/Backup     ntfs    defaults,umask=007,gid=46 0       1



Btw, do I need to create a mount point for device sda7 too ? :)

And do I need to force mount when mounting first time ? :)

**Sorry for the confusion -> There are no drive named Nash( don't ask me why I said there was :) )**

---

### Post by iaculallad on 2008-09-10
> **Louis de Broglie said:**
> So if I want to mount all of my ntfs drives when I boot ubuntu , I just add lines for all of them in the fstab ? 

For example if I want to mount drive Nash ( which is sda7 i think ) the required line will be :



Btw, do I need to create a mount point for device sda7 too ? :)

And do I need to force mount when mounting first time ? :)

Each partition requires a unique mount point. So yes, you do need to create 'Nash'. No, you don't need to force mount partitions. Force mount can only be applied on partitions that did not have a 'clean shutdown' status.

---

### Post by Louis de Broglie on 2008-09-10
All of my NTFS partitions got that status.:(

---

### Post by iaculallad on 2008-09-10
> **Louis de Broglie said:**
> All of my NTFS partitions got that status.:(

You could force mount it with the given commands above (The one you successfully used). That would solve the problem. Just follow the steps we did on your first posts.

---

### Post by Louis de Broglie on 2008-09-10
OK. It works. But now none of the mounted drives unmounts from gui.

So i will have to use terminal from now on to mount or, unmount ?

---

### Post by iaculallad on 2008-09-10
> **Louis de Broglie said:**
> OK. It works. But now none of the mounted drives unmounts from gui.

So i will have to use terminal from now on to mount or, unmount ?

No, the drives will automatically mount on Ubuntu startup. That only happens if you add the partition on the fstab file.

---

### Post by Louis de Broglie on 2008-09-10
Ok. Everything seems ok. thanks for your support and time.:)

---

### Post by iaculallad on 2008-09-10
> **Louis de Broglie said:**
> Ok. Everything seems ok. thanks for your support and time.:)

Ok. Glad to have helped. If problem arises in your Ubuntu usage, you can always come back, the forum's got plenty of helping hand to help you sort your problem. Goodluck and Go Ubuntu.

---

### Post by vanadium on 2008-09-11
> No, you don't need to force mount partitions. Force mount can only be applied on partitions that did not have a 'clean shutdown' status.
A small additional remark: you should never "permanently" use force mount. You should use force mount only temporarily, in an emergency, for example to retrieve the data before reformatting the drive. There is a reason why Ubuntu won't automount "unclean" volumes: it is because you risk corrupting the file system further. You risk major data loss.

For this reason, you'd better not maintain ntfs volumes if you do not have MS Windows. Linux cannot fully check and repair them. Therefore, use ntfs only if you also have ready access to MS Windows. Otherwise, reformat them in ext3 or another Linux file system.

(That said, I *have* an ntfs volume. However, it is a Lacie Multimedia disk and the data are stored elsewhere (in duplicate). If anything goes wrong, I will just reformat the drive in ntfs to "repair" the file system and copy the data back).

---

