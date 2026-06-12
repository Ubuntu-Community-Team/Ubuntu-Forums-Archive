---
title: "running out of space in / 22.04 LTS"
date: 2023-02-05
forum: Installation &amp; Upgrades
---

### Post by gian2 on 2023-02-05
Hello All,

My boot disk is 250GB, and thanks to snaps I'm running out of disk space in /.

Can I 'dd' the disk, put the image on another disk twice the size, and then increase the / partition, or it's not as simple as that?

Now there is a ton on /dev/loop partitions on the disk, and when I install my systems, I always separate / and /home partitions.

Thanks for reading, and for your help,

-Gian

---

### Post by Impavidus on 2023-02-06
The storage in /dev/loop isn't real. The real storage for snaps is in /var/lib/snapd/snaps. They are ridiculously large, but not so large that a 40GB root partitions wouldn't be enough (unless you really have a lot of them).

---

### Post by gian2 on 2023-02-06
thanks Impavidus,

```
Device     Boot    Start       End   Sectors   Size Id Type
/dev/sda1  *        2048    999423    997376   487M ef EFI (FAT-12/16/32)
/dev/sda2       39063552  50782207  11718656   5,6G 82 Linux swap / Solaris
/dev/sda3       50782208 488396799 437614592 208,7G 83 Linux
/dev/sda4         999424  39063551  38064128  18,2G 83 Linux
```

sda3 is /home
sda4 is /, which includes /var....

---

### Post by ajgreeny on 2023-02-06
Oh dear!
18.2G for your root partition is probably too small but before doing anything drastic to sort this out we need to see how much space is available in your partitions so please run command ```
df -h
``` and post the result back here using Code-tags please.
There is a **Code-tags** how-to in my signature below.

---

### Post by gian2 on 2023-02-06
```

gian@intragnola:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
tmpfs           1,6G  2,2M  1,6G   1% /run
/dev/sda4        18G   16G  1,6G  91% /
tmpfs           7,8G   76K  7,8G   1% /dev/shm
tmpfs           5,0M  4,0K  5,0M   1% /run/lock
/dev/sda1       487M  5,3M  481M   2% /boot/efi
/dev/sda3       206G  157G   38G  81% /home
/dev/md0        3,6T  911G  2,6T  27% /home/gian/Pictures/Archivio
tmpfs           1,6G   88K  1,6G   1% /run/user/127
tmpfs           1,6G   76K  1,6G   1% /run/user/1000

```

---

### Post by ajgreeny on 2023-02-06
Well, you do seem to have a bit of a problem here as your /home partition is shown as 206G  157G used,   38G free, ie  81% used.
This means you could in theory "move" a bit of space from /home to add to your /root but that is a bit short-sighted as you will then be close to overloading or over-filling your /home, currently 81% used and I think you need 10-15% available space for the partitions to run well.

What currently is occupying the /dev/md0 which still has masses of space available? I assume that it is what it says in its mountpoint, ie, an archive of pictures or photos. Nevertheless there is 2.6T available space there so you could choose to move some or all of the data folders from your current /home to that huge disk and then use symbolic links to those moved folders in your current, but now less full /home partition. If I were in your shoes that is probably what I would do; those moved folders will still appear to be sitting in your /home even though they are now actually on a completely different disk.

Snaps are causing many problems to users in many different ways which is why I have none on my systems, and for users like you with small disks the space utilisation can be a problem.  Perhaps you would have been OK if originally you had allocated 25G to /root but with many snaps maybe even that would not be enough.

Come back again if you need more help and we'll manage to sort this out some way or other.

---

### Post by gian2 on 2023-02-06
Ajgreeny,

thanks for your kind help.

Given the cheap price of a new ssd, I'd opt for a new system disk.
I only install LTS, and having a separate /home allows me to rebuild the system every two years without touching my files.
When I installed this disk, I erred in sizing the system partitions.
So the option is reinstall the system on a new larger disk, or dd the disk and resize the partitions, if that is possible at all.
I haven't done that before, so this is why I'm asking.
The mirrored drives are a backup of a picture library, and for the reasons above, I'd like to keep it as that.

-G

---

### Post by ajgreeny on 2023-02-06
That may indeed be the better answer, and although I have used dd for other purposes I have never cloned from one disk to another. Many do that so I know it can work but I will have to leave others to advise you on details of that and what else may be necessary, such as a rewrite of /etc/fstab as a result of changes to UUIDs of partitions.

Once done I also can't see any obvious reason why you can not enlarge the partitions assuming the new disk is large enough to contain the sizes you want.
Good luck with making these changes and the reinstall of your OS.

---

