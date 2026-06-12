---
title: "Reading NTFS partitions"
date: 2006-03-13
forum: Installation &amp; Upgrades
---

### Post by aarbear26 on 2006-03-13
I recently installed ubuntu for a friend after finding out about automatix.  I had suse installed for him to play with since it allowed him to read his windows partitions and use the files on it.  I was happy to see that ubuntu allowed me to mount the windows drives in the installation.  However, when we loaded everything and went to play his music, it said we weren't allowed to access the drives.  Meaning it had the big X on the icons and said unauthorized.  I'm still kinda fresh to linux myself and definately to the ubuntu way.  I'd like to know if

1.the drives can't be read by ubuntu
or 
2. i need to enable access to all users since it is a root owned directory
or 
3. i need to install some other packages to allow access to the drives

if i need to enable access how do i do that from a command line? 
and is there a way to allow me to log in as root and just change everything i need to rather than typing sudo all the time.  
I've used chmod before on files  but does it work the same on a  directory?

thank you for any help you may give.

---

### Post by taurus on 2006-03-13
You need to change the permission in /etc/fstab so that everyone can read your NTFS.  There should be a line in there readind something like
```

/dev/hda1  /media/windows  ntfs  defaults 0 0

```
Just add "umask=0222" after the "defaults" thing, i.e.
```

/dev/hda1  /media/windows  ntfs  defaults,umask=0222 0 0

```
Otherwise, post your /etc/fstab here if you're not sure...

p.s.  If you want to edit it, run this from a terminal
```

sudo gedit /etc/fstab

```

---

### Post by aarbear26 on 2006-03-14
Thanks a lot, I think that just might work.  I'll test that when I visit him this week.  If anyone happens to know, I'd still like to know if there is a way to really log into root.  If not, it's not that big a deal.

thanks

---

### Post by TylerH on 2006-03-16
hey Taurus. I tried doing the same thing yet it still tells me that I don't have permission to access the drive. My fstab looks like this:

> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0 1
/dev/hdd5       /media/hdd5     ntfs    defaults,umask=0222 0 	0
/dev/sda1       /media/sda1     ntfs    defaults,umask=0222 0 	0
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0


do i have to restart or remount for it to work or something?
thanks

---

### Post by aysiu on 2006-03-16
Yes.

If you reboot, it'll remount.

You can also unmount and remount the partitions.

---

### Post by hod139 on 2006-03-16
You don't have to restart, you can issue the command 
```

sudo mount -a

```

---

### Post by aysiu on 2006-03-16
Before doing ```
sudo mount -a
``` you may want to do ```
sudo umount /dev/hdd5
sudo umount /dev/sda1
```

---

### Post by klahjn on 2006-03-16
Almost same situation here....very similar.  Not finding a way to mount it.  When i do the 
sudo mount -a it gives me the error.
root@dta-ubuntu:/home/psykosis# umount /dev/hda1
umount: /dev/hda1: not mounted
root@dta-ubuntu:/home/psykosis# mount -a
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
i know it has something to do with the umask=0222.....i remove that and everything else is fine, but with the umask it gives me that error every time.  I'm running Dapper Flight 5 latest updates.  Will probably try to work on it more here soon.

---

### Post by aysiu on 2006-03-16
klahjn, can you post the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by TylerH on 2006-03-16
Case of the disappearing HD.

remember hdd5 from above?
i rebooted and now it tells me it doesn't exist

note that I have ubuntu on my SATA and my music on my old hdd5

managed to get the sata mounted, but the hdd5 disappeared
any ideas?

---

