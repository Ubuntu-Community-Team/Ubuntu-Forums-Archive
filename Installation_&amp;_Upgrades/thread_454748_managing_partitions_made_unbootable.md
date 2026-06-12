---
title: "managing partitions made unbootable"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by souzacds on 2007-05-25
I`ve been resizing the partitions using gParted at liveCD, and it changed the partitions names, then the ubuntu is unbootable. 
Also I think that the /home is still pointing to older place.
/ is /dev/hda5, and /home is /hda6 now.

how do I fix it  ?

thanks

---

### Post by confused57 on 2007-05-25
> **souzacds said:**
> I`ve been resizing the partitions using gParted at liveCD, and it changed the partitions names, then the ubuntu is unbootable. 
Also I think that the /home is still pointing to older place.
/ is /dev/hda5, and /home is /hda6 now.

how do I fix it  ?

thanks
You'll need to boot the live cd, open a terminal & post the output of:
```
sudo fdisk -l
```
the -l is a small "L"

Give us a little more detail of how you repartitioned...did you create a new separate /home, which version of Ubuntu you're using?   Anything else you can think of that might help you find a solution.

---

### Post by souzacds on 2007-05-25
hi,
I`m using kubuntu 704.
I read the ubuntu-guide, and fixed the grub, it`s booting right now.
but it didn`t find the /home partition (it was out of / partition yet)
the /etc/fstab partially looks like this:

```


# /dev/hda5
UUID=ce66b1b5-d6cd-4a4f-ac72-bde8cea98022 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda6
UUID=d0614651-6b84-42da-9afa-7481dfea53c3 /home           ext3    defaults        0       2

```
the sudo fdisk -l printed it (partially ):

```
)
/dev/hda5             724        1997    10233342   83  Linux
/dev/hda6            1998        2841     6779398+  83  Linux

```


thanks lot for helping me.,

---

### Post by merlinus on 2007-05-25
Here are a couple of ideas.

In a terminal, get your /home UUID and compare it to the one in fstab.

```

 sudo vol_id -u /dev/hda6


```

Also, here is my fstab for /home:

```

UUID=a961b624-ed15-4878-b66f-bb2d007b74a4 /home ext3 defaults,errors=remount-ro 0 1

```

I have an entry for Places/Home Folder that opens Nautilus, and in Thunar my username (home folder) is at the top of the tree.

hth....

-merlin

---

### Post by confused57 on 2007-05-25
merlinus is right, it's probably that your UUID's have changed...Herman suggests this command to see the UUID's of all your partition filesystems:
```
blkid
```

You might also want to check the UUID's in your kernel entries in your /boot/grub/menu.lst, as well as your /etc/fstab & make sure they're correct...you can probably just copy & paste the new UUID's into your menu.lst & fstab.

---

### Post by souzacds on 2007-05-25
> **confused57 said:**
> merlinus is right, it's probably that your UUID's have changed...Herman suggests this command to see the UUID's of all your partition filesystems:
```
blkid
```

You might also want to check the UUID's in your kernel entries in your /boot/grub/menu.lst, as well as your /etc/fstab & make sure they're correct...you can probably just copy & paste the new UUID's into your menu.lst & fstab.

Hi,
I used the blkid command and pasted output in the uuid of the partition on fstab, and everything is right now.


thanks lot everybody;

---

