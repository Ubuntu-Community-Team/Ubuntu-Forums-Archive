---
title: "no swap after upgrade to edgy"
date: 2006-11-20
forum: Installation &amp; Upgrades
---

### Post by Max_Might on 2006-11-20
I upgraded dapper to edgy a few weeks ago. This morning when i started ubuntu it performed error check (normal in every 30 startups) and i saw that there was message that ubuntu cant "load" the swap partition.

My swap partition is hdb1 and is 512 MB

What do i have to do to make the system load the swap partition?
I gues it is smthing in /etc/mtab but i`m not sure.

---

### Post by geekchic9 on 2006-11-20
Whoops! I misread your post. I thought you said your hard drive was 512 MB, not your swap partition.

---

### Post by taurus on 2006-11-20
Actually, it's in /etc/fstab.  So, open a terminal, Applications -> Accessories -> Terminal, and paste the output of this command here.

```
cat /etc/fstab
```

---

### Post by Max_Might on 2006-11-20
here is the outputh:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb3 -- converted during upgrade to edgy
UUID=ebddbb17-2fff-486c-9109-e4259d4d5b2d / ext3 defaults,errors=remount-ro 0 1
# /dev/hda1 -- converted during upgrade to edgy
UUID=EA001EC0001E9423 /media/hda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hda5 -- converted during upgrade to edgy
UUID=C2E88C7FE88C7387 /media/hda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdb5 -- converted during upgrade to edgy
UUID=1444D9D644D9BAA6 /media/hdb5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

# /dev/hdb1 -- converted during upgrade to edgy
UUID=db878897-9ed4-4201-9c77-74abcf103116 none swap sw 0 0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0


i think fstab looks ok, but ... how can i get the error outputh during the startup process ?

---

### Post by Max_Might on 2006-11-22
How do I get my swap partition back ?

---

### Post by taurus on 2006-11-22
What about

```
sudo fdisk -l
```

---

### Post by etienne.navarro on 2006-11-24
The same thing happened to me. The problem was that the UUID of the swap partition was incorrect.

What you can do is either correct the UUID of the swap. To find it out type:
```
ls /dev/disk/by-uuid/ -alh
```
and look for the UUID code for **hdb1**.
Then edit your fstab:
```
sudo gedit /etc/fstab
```
and replace the swap part with the new UUID.

Another method would be to just not use the UUID numbers and have this in your fstab
```
/dev/hdb1 none swap sw 0 0
```

---

### Post by Niomi on 2006-11-30
Have you found a solution to this problem yet? I had the same issue, I'm pretty sure I found a solution at #ubuntuforums on freenode.

My problem is the UUID I got with this command:
```
sudo vol_id /dev/hda5
```

Didn't match the UID I had in /etc/fstab

```
## /dev/hda5 -- converted during upgrade to edgy
#UUID=dd971194-9c48-4894-acf9-0d845b58ff08 none swap sw 0 0
```

```
niomi@Lore:~$ sudo vol_id /dev/hda5
ID_FS_UUID=0cc280a9-aade-4913-91b9-f3a274d9cd70
```

Once I pasted the UUID from vol_id /dev/hda5 into fstab, it seemed to mount okay. Of course, replace hda5 with whatever your swap space happens to be.




Check to see if your swap is mounted using this command:
```
cat /proc/swaps
```

---

### Post by Sef on 2006-11-30
If you can't get swap back with the above directions, I recommend downloading [GParted]("http://gparted.sourceforge.net/livecd.php").  I recently lost my swap after the electricity went out and used [GParted]("http://gparted.sourceforge.net/livecd.php") to reinstall it.

---

