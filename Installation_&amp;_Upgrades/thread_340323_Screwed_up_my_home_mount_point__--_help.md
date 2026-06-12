---
title: "Screwed up my /home mount point  -- help??"
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by richardq on 2007-01-17
Ok, I'm well in over my head here:

I have a drive with an ntfs partition(hdb1) and an ext3 partition(hdb2) containing my /home.

I shrunk the ntfs partition and created a new ext3 partition(hdb5) in the freed up space.

So far so good. But I followed some instructions to mount the new partition (which is just intended as file storage space) which involved changing the fstab file and now it seems that the new partition (which is empty) is being mounted as /home. And I can't figure out how to change it back.

I've gone back to the original fstab file, and but it doesn't change anything, it's still mounting the hdb5 partition as /home. I know all my data is still in the hdb2 partition, but I can't figure out how to get at it, nevermind change it back so that it mounts hdb2 as /home. I think this has something to do with the change to uudev with Edgy (?) I thought setting the fstab file back to it's original form and restarting would do it. Nope.

What follows are my original (working perfectly) fstab, and the modified one. If anyone can help me out I'd really appreciate it.

Here's the original fstab prior to the screwup:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb2 -- converted during upgrade to edgy
UUID=a0dd2e3f-788d-4342-95aa-a5f91fc01070 /home ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
UUID=A67411EA7411BE4D /media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=68F044B7F0448D6E /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=2573-6CC2 /osshare vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=fbdd0a57-3ddc-4c35-b8cd-c128d9e09655 none swap sw 0 0
/dev/hda5       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

And here's the modified fstab that f$#!ed it up:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb2 -- converted during upgrade to edgy
UUID=a0dd2e3f-788d-4342-95aa-a5f91fc01070 /home ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
UUID=A67411EA7411BE4D /media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=68F044B7F0448D6E /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=2573-6CC2 /osshare vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=fbdd0a57-3ddc-4c35-b8cd-c128d9e09655 none swap sw 0 0
/dev/hda5       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb5 /storage ext3 defaults 0 0
```

---

### Post by randomnumber on 2007-01-17
I do not have a complete answer but I am at the point of finding a cmd I think will help.

sudo vol_id /dev/hda1

where hda1 is replaced with the volume you want to know.

---

### Post by randomnumber on 2007-01-17
I also found this thread I thought may be relavent

[http://www.ubuntuforums.org/showthread.php?t=223182&page=3&highlight=uuid](http://www.ubuntuforums.org/showthread.php?t=223182&page=3&highlight=uuid)

Apparently they changed /etc/fstab and everyone is trying to figure it out again.

---

### Post by bapoumba on 2007-01-17
> **richardq said:**
> 
Here's the original fstab prior to the screwup:

```
...
[B]# /dev/hdb2 -- converted during upgrade to edgy
UUID=a0dd2e3f-788d-4342-95aa-a5f91fc01070 /home ext3 defaults 0 2[/B]
...
```

And here's the modified fstab that f$#!ed it up:

```
...
[B]# /dev/hdb2 -- converted during upgrade to edgy
UUID=a0dd2e3f-788d-4342-95aa-a5f91fc01070 /home ext3 defaults 0 2[/B]
...
```

I may not be reading this correctly, but looks like hdb2 is /home in both fstab.
Did you edit fstab to change /home mount point in runlevel 1 (single user, root) ?
Have you mounted the the partition (**sudo mount -a**, or **mount -a **if in runlevel 1) ?

---

### Post by richardq on 2007-01-17
> **bapoumba said:**
> I may not be reading this correctly, but looks like hdb2 is /home in both fstab.

I restarted the machine this morning (I swear I had done that last night as well) and it seems like /home is now back on hdb2. I said the same thing - both fstabs look the same.

Anyway, so now I have the following on that drive:

ntfs--hdb5--hdb2

hdb2 is mounted as /home, but /hdb5 is not mounted. What is the easiest way to get that /hdb5 to be automatically mounted as say /storage ?

---

### Post by floke on 2007-01-17
I posted a thread on trying to do something like this here

[http://ubuntuforums.org/showthread.php?t=338553](http://ubuntuforums.org/showthread.php?t=338553)

Was given (and discovered) some advice that you might find useful

Good luck

---

### Post by bapoumba on 2007-01-17
> **richardq said:**
> I restarted the machine this morning (I swear I had done that last night as well) and it seems like /home is now back on hdb2. I said the same thing - both fstabs look the same.
Booting mounted your partitions according to fstab (sudo mout -a would have done it too, without rebooting).

> **richardq said:**
> 
hdb2 is mounted as /home, but /hdb5 is not mounted. What is the easiest way to get that /hdb5 to be automatically mounted as say /storage ?

Make up a new mount point :
```
sudo mkdir /storage
```

Get /hdb5 uuid :
```
sudo vol_id -u /dev/hdb5
```

Edit your fstab to change /hdb5 mount point :
```
#/dev/hdb5
UUID=<hdb5_UUID-here> /storage     ext3    defaults,errors=remount-ro   0       2
```

Mount it, should be okay ;)

---

### Post by richardq on 2007-01-17
Ok, this is getting too weird.

This morning (when I last replied) the machine booted normally, mounting hdb2 as /home. I saw the replies to my message while checking at work (thanks guys). I get home tonight, boot up the machine and it mounts hdb5 as /home. (huh!)

So I reboot the machine and IT MOUNTS hdb2 as /home !!! I then apply the instructions given by bapoumba and modified my fstab. As soon as I type in "sudo mount -a" and hit enter, I notice the icons in my status bar change slightly. The exit button changes from the red power button to the open-door icon and there are a few different icons up there! So I decide to power down the machine and restart to see what happens...

So when I boot up again (and now I've tried it twice) it's booting with hdb5 mounted as /home and no access to my normal hdb2 /home partition. Aaargh!

I run Beryl - maybe that has something to do with it? Maybe I should switch to Metacity before doing those changes and remounting?

Anyways, here's the fstab file again just to prove I'm not going wacko.. it shows hdb2 to be mounted as /home and hdb5 to be mounted as /storage. But that's not what's on my system right now!

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2 -- converted during upgrade to edgy
UUID=23b7dbeb-e33f-49d6-b913-614dafe1bcf5 / ext3 defaults,errors=remount-ro 0 1
# /dev/hdb2 -- converted during upgrade to edgy
UUID=a0dd2e3f-788d-4342-95aa-a5f91fc01070 /home ext3 defaults 0 2
# /dev/hdb1 -- converted during upgrade to edgy
UUID=A67411EA7411BE4D /media/hdb1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=68F044B7F0448D6E /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=2573-6CC2 /osshare vfat defaults,utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=fbdd0a57-3ddc-4c35-b8cd-c128d9e09655 none swap sw 0 0
# /dev/hdb5
UUID=a0dd2e3f-788d-4342-95aa-a5f91fc01070 /storage ext3 defaults,errors=remount-ro 0 2
/dev/hda5       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



```

---

### Post by bapoumba on 2007-01-18
Hi,
from the fstab above, /hdb5 and /hdb2 have the same UUID, which they should not. You may have mixed the two in your fstab. Please check UUID for both partitions and correct fstab accordingly (the command is in my previous post).
UUID is a universal unique identifier, set up when the file system is created.

---

### Post by richardq on 2007-01-18
> **bapoumba said:**
> Hi,
from the fstab above, /hdb5 and /hdb2 have the same UUID, which they should not. You may have mixed the two in your fstab. Please check UUID for both partitions and correct fstab accordingly (the command is in my previous post).
UUID is a universal unique identifier, set up when the file system is created.

For some strange reason the 'sudo vol_id -u' command is giving the same uuid for both hdb2 and hdb5 (?) I checked the backup copy of fstab I made before getting into this and the uuid it's giving me is the same as it was for hdb2 before. So it's not giving me a unique id for hdb5 for some strange reason.

```
richard@ubuntu:~$ sudo vol_id -u /dev/hdb2
a0dd2e3f-788d-4342-95aa-a5f91fc01070
richard@ubuntu:~$ sudo vol_id -u /dev/hdb5
a0dd2e3f-788d-4342-95aa-a5f91fc01070
```

I have another physical hard drive in the machine and checked the sudo vol_id output for the sda2 and sda5 partitions and it generates unique id's for both of those. I'm not sure what the problem is with the /hdb2 and /hdb5 case.

**BING** you know what I just thought? I originally created this new partition by using a cut/paste command in gparted. Originally I was going to copy the /home partition, get rid of the original one and then expand the size of the new one and then decided to erase the contents of it to make a separate empty partition. I bet the copy/paste command duplicated the uuid as well. I'll give it a shot and report back.

Thanks for all your help so far.

---

### Post by Pobega on 2007-01-18
I actually have a question myself: Is UUID needed in the /etc/fstab file? I would find it much simpler to use the device names than the UUID myself, and I'm just wondering if it's safe to replace the UUIDs with the device names.

---

### Post by bapoumba on 2007-01-18
> **richardq said:**
> 
**BING** you know what I just thought? I originally created this new partition by using a cut/paste command in gparted. Originally I was going to copy the /home partition, get rid of the original one and then expand the size of the new one and then decided to erase the contents of it to make a separate empty partition. I bet the copy/paste command duplicated the uuid as well. I'll give it a shot and report back.

Thanks for all your help so far.
You're welcome.
UUID are created when you create the file system. May be do it all over again for /dev/hdb5 (from this thread, I'm guessing you do not have anything important on that partition yet ;))

---

### Post by richardq on 2007-01-18
Nope, nothing on it yet. I just corrected the problem by deleting the partition and creating a new empty one. I checked the new uuid and modified the fstab and it all works like a charm. I guess some things you only learn by experience. 

Now the next problem is how to get F-Spot to import photos to the /storage/Photos folder instead of the ~/Photos folder. There doesn't seem to be any preferences to set it. Ahh another challenge. ;)

Thanks again, you helped me out and I also managed to learn something along the way which is always good.

RQ

---

### Post by Pobega on 2007-01-18
> **Pobega said:**
> I actually have a question myself: Is UUID needed in the /etc/fstab file? I would find it much simpler to use the device names than the UUID myself, and I'm just wondering if it's safe to replace the UUIDs with the device names.

I would still like to know the answer to this question, sorry about the shameless and near pointless bump, but this UUID thing is bugging me.

---

### Post by bapoumba on 2007-01-19
From edgy, file systems are now identified by their UUID in fstab. it makes the mount more robust as the partition has now a unique identifier.

```
~ $ ls -l /dev/disk/by-uuid/
lrwxrwxrwx 1 root root 10 2007-01-19 10:25 0A2A-1AD4 -> ../../hda2
lrwxrwxrwx 1 root root 10 2007-01-19 10:25 3007-17F2 -> ../../hda1
lrwxrwxrwx 1 root root 10 2007-01-19 10:25 37efb3c4-8dce-4724-9417-da4ccc45e6a3 -> ../../hda5
lrwxrwxrwx 1 root root 10 2007-01-19 10:25 9dd424b2-c688-4c9e-84ea-f5cfaee02227 -> ../../hda3
lrwxrwxrwx 1 root root 10 2007-01-19 10:25 b679642e-0b62-4622-b5f8-34acdd0438f0 -> ../../hda6

```
```
~ $ sudo vol_id -u /dev/hda3
Password:
9dd424b2-c688-4c9e-84ea-f5cfaee02227

```

For partitions in fstab : **cat /etc/fstab**
For partitions not mounted in fstab : **sudo fdisk -l**

---

### Post by Pobega on 2007-01-19
Even so, I'm just wondering if it's safe to remove the UUID's from fstab. I use the device name for my /home partition, and it really makes reading my fstab much easier when need be (Even though it doesn't matter much).

---

### Post by bapoumba on 2007-01-19
```
# /dev/hda3
UUID=9dd424b2-c688-4c9e-84ea-f5cfaee02227 /  ext3 defaults,errors=remount-ro 0 1
```
/dev/hda3 is my root partition. edgy's install got my fstab this way. # marks the line as a commentary. I know you can use labels, instead of UUID, but I have not looked precisely into it. I'll check for links.

---

