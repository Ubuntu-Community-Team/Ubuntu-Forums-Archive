---
title: "Mounting an already existing partition but can't write to it?"
date: 2009-12-24
forum: Installation &amp; Upgrades
---

### Post by Haitoyou on 2009-12-24
Hi! I have a problem with mounting a partition during my installation of ubuntu 9.10.

When I install, I set a separate partition for the root (/), home (/home), boot (/boot), and my permanent storage partition located on my second drive that's ext4 (/home/username/videos).

So, It mounts just fine to my username and I can read from it and transfer videos off of it into other folders, BUT, it does not let me write to it. It tells me I do not have permission to do so. Now, I can get around this problem by going into the terminal and doing individual "sudo cp FILEDIRECTORY /home/username/videos" but as you can imagine, this is a pain in the behind to do for everything I want to write into the folder!

Can someone tell me what I have to do? I have a feeling it will have something to do with chmod or maybe chown? BEEP BEEP!

---

### Post by mikewhatever on 2009-12-24
You should post the content of your fstab:

cat /etc/fstab

---

### Post by Haitoyou on 2009-12-24
Here it is:

> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda3 during installation
UUID=7240da9b-e128-4cc4-9025-8451c0fd4834 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
UUID=b078ac5c-2fb8-4eb7-9966-eb9554aa36f8 /boot           ext4    defaults        0       2
# /home was on /dev/sda2 during installation
UUID=6b997570-446a-41ee-bec3-a4afd9742458 /home           ext4    defaults        0       2
# /home/cobalt/videos was on /dev/sdb1 during installation
UUID=d0f007f8-6a08-4dcc-a6d5-b5a14c4718ba /home/cobalt/videos ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=95f80292-c738-4bb9-8f43-0ae7fc0b5e73 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


---

### Post by mikewhatever on 2009-12-24
Can you check the ownership of /home/cobalt/videos with <ls -l | grep -i videos>. The problem may be that the mount point is owned by root, and all you need to do is change the ownership.

---

### Post by oldfred on 2009-12-24
I do mine slightly different as I mount to a location and link into my home. This is my fstab that works:

# Entry for /dev/sdc6 :
UUID=a55e6335-616f-4b10-9923-e963559f2b05  /usr/local/fred/data    ext3         auto,users,rw,relatime               0  2  

relatime includes defaults which I thought included the rw & auto so they are duplicated. Users lets me own it.

ln -s /usr/local/fred/data/Music
ln -s /usr/local/fred/data/Documents
etc for all directories in home

---

### Post by Haitoyou on 2009-12-24
WOOT GOT IT!
so "ls -l grep -i videos" produced:
```
drwxr-xr-x. 3 cobalt root    4096 2009-12-24 17:39 videos
drwxr-xr-x  2 cobalt cobalt  4096 2009-12-23 01:54 Videos
```

the partition was owned by root so all I did was

```
chown -R cobalt /home/cobalt/videos
```

and poof! It works yay!

---

