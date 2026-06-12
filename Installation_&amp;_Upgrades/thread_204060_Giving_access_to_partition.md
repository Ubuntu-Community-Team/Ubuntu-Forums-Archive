---
title: "Giving access to partition"
date: 2006-06-26
forum: Installation &amp; Upgrades
---

### Post by vincente on 2006-06-26
[IMG]http://img311.imageshack.us/img311/9875/screenshotdisksmanager8ry.png[/IMG]

Im trying to map the access path to that particular partition. This partition is to be shared between Windows XP and Ubuntu.

Is this correct?

[IMG]http://img321.imageshack.us/img321/5677/screenshot14ky.png[/IMG]

I change to root and i try to give access to that path but whenever i click on Write permission it unchecks immediately. It doesn;t allow me to check the Write permission.

Any advice?

Thanks

---

### Post by x64Jimbo on 2006-06-26
You'll need to change the write permissions on the partition as root, since root is the only one that has permission on it right now. This will probably require that you use the chmod command. Use man chmod for more info.

---

### Post by aysiu on 2006-06-26
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by vincente on 2006-06-26
i think i screw up the /etc/fstab file..


Now im having problems booting up and i landed in the terminal as root. 

i have a backup copy as /etc/fstab_backup

i try to do something

cp /etc/fstab_backup /etc/fstab

But they says Read only filesystem..something like tt..

How do i replace with the old fstab?

---

### Post by aysiu on 2006-06-26
```
sudo cp /etc/fstab_backup /etc/fstab
```

---

### Post by vincente on 2006-06-26
I boot into recovery mode and i've tried

```
sudo cp /etc/fstab_backup /etc/fstab
```

sudo: cmd not found

```
cp /etc/fstab_backup /etc/fstab
```

When i do this they prompt, Cannot create regular file '/etc/fstab': Read-only file system

Any advice?

---

### Post by aysiu on 2006-06-26
That's weird. Read-only filesystem... maybe because there's some kind of error it's trying to protect you from?

Do you have a live CD?

---

### Post by vincente on 2006-06-26
[QUOTE=aysiu]That's weird. Read-only filesystem... maybe because there's some kind of error it's trying to protect you from?

Do you have a live CD?[/QUOTE]

I have the live cd.
How should i deal with it?
Hopefully i dont have to reinstall the entire ubuntu :???:

---

### Post by aysiu on 2006-06-26
[QUOTE=vincente]I have the live cd.
How should i deal with it?
Hopefully i dont have to reinstall the entire ubuntu :???:[/QUOTE]
Well, boot the live CD.

Assuming that the partition you want to mount is /dev/hda1, open a terminal and do this: ```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab
``` If that doesn't work, try this ```
gksudo nautilus
``` and navigate to the /recovery/etc directory and see if you can copy the backup file that way.

---

### Post by vincente on 2006-06-26
I boot up using the Live cd now.

> Assuming that the partition you want to mount is /dev/hda1

You are saying hda1 is the previous Ubuntu installation?

```
sudo mkdir /recovery
sudo mount -t ext3 /dev/hda1 /recovery
sudo cp /recovery/etc/fstab_backup /recovery/etc/fstab
```

You mean i open a terminal now and do this? and after that reboot?

Sorry, im kind of paranoid now, dont wanna screw up anymore files..

---

### Post by aysiu on 2006-06-26
I'm saying--not being at your computer myself--I have no idea where your previous Ubuntu installation is. I would assume it's /dev/hda1, but I don't know. You would know better, I'd think.

And, yes, I do mean type that in the terminal *now*, when you have the live CD running. Do not reboot until you're confident that the original /etc/fstab was restored.

---

### Post by vincente on 2006-06-26
Thanks a lot 

I think i know what i am doing now

Manage to replace the fstab with the back up one..

Now gonna reboot.

God bless me

---

### Post by vincente on 2006-06-26
Rebooted...

Same problem..

I notice the messages have some error saying bad sector blah blah

Damn...it can't be so coincidental that my harddisk is having bad sector

argh.

---

### Post by aysiu on 2006-06-26
Which may be why you had a read-only filesystem when you booted into recovery mode.

---

### Post by vincente on 2006-06-27
ok im not gonna give up so i reinstall the entire Ubuntu and recreate the partitions

```
sudo fdisk -l 

Disk /dev/hda: 20.5 GB, 20547841536 bytes
255 heads, 63 sectors/track, 2498 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        2497    20057121    7  HPFS/NTFS

Disk /dev/hdb: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1912    15358108+  83  Linux
/dev/hdb2            1913        2167     2048287+  82  Linux swap / Solaris
/dev/hdb3            2168        4998    22740007+   b  W95 FAT32
```

i would like to share /dev/hdb3 between my windows system (/dev/hda1) and linux system (/dev/hdb1)
```

sudo mkdir /home/cj/share                (create a mount point)
sudo cp /etc/fstab /etc/fstab_backup (backup the fstab file)
sudo nano /etc/fstab                          (edit the tab file)
```

Added this entry in /etc/fstab  
```
/dev/hdb3 /home/cj/share vfat iocharset=utf8,umask=000 0 0
```

Remount the drive 
```
sudo mount -a
```

This is working so far..

Correct me if there is anything wrong..

---

### Post by aysiu on 2006-06-27
Looks good to me. No bad superblocks error...?

---

### Post by vincente on 2006-06-27
so far so good

no bad superblocks error..

thanks for your advice earlier on...

hopefully now i can start exploring further on Ubuntu :)

---

