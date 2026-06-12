---
title: "Trying to get Vista64 back in grub menu"
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by nugz45 on 2008-01-10
So usually every time I installed Ubuntu over a Vista installation, grub did just fine and everything was good in my boot menu.  This time things were a little different b/c I had Vista and Ubuntu installed to 2 different drives. 

Here is my fdisk -l output. 

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5b5d5b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2918     3903795   82  Linux swap / Solaris

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a6e1a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       18242   146521088    7  HPFS/NTFS
```

This time when I boot up, my Vista install doesnt show up at all.  I tried to manually edit my /boot/grub/menu.lst with:

```
title Windows Vista
rootnoverify (hd1,0)
chainloader +1
```

...but this gives me the BOOTMGR not found error.  So I guess this is a good thing.  This means I am telling grub to look in the right place but Vista's bootloader is failing?

I think a solution to this would be to insert my Vista64 DVD and do a Startup Repair, but sadly I dont have the DVD anymore.  Think I can try a Vista 32bit install DVD and it will work the same?  Or even better, can I somehow fix this without a Vista DVD at all by editing my menu.lst someway?  

If my menu.lst Vista section is wrong, please correct me.  Or if you know a way to reach the Vista bootloader and add it to my grub menu so it works, that would be great also!

Thanks in advance.

---

### Post by confused57 on 2008-01-10
See if this entry will work:
```
title Windows Vista
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```
copy & paste this entry into your menu.lst...hopefully, it'll boot Vista.

---

### Post by nugz45 on 2008-01-10
Same error.  :(

BOOTMGR is missing.
Ctrl + alt + del to restart.

There is like a million tutorials online for this but not many of them specify for partitions on separate drives.  A lot of them give me the code you just did but it didnt seem to work either.

At least this is a Vista error I am getting.  Its not grub throwing this error.  Its as if when grub replaced Vista in the MBR it doesnt want to boot anymore.

---

### Post by confused57 on 2008-01-10
> **nugz45 said:**
> Same error.  :(

BOOTMGR is missing.
Ctrl + alt + del to restart.

There is like a million tutorials online for this but not many of them specify for partitions on separate drives.  A lot of them give me the code you just did but it didnt seem to work either.

At least this is a Vista error I am getting.  Its not grub throwing this error.  Its as if when grub replaced Vista in the MBR it doesnt want to boot anymore.
You might try setting your /dev/sdb1 bootflag on(notice there's no * in the boot column)...I think you can do this by booting up the Ubuntu live cd, open Gnome Partition Editor(System---Administration---Gnome Partition Editor), right-click & set active.

---

### Post by nugz45 on 2008-01-10
Still no luck. :confused:

Do you think I could try a Startup Repair from the Vista DVD?  Only problem is I would have to use a 32bit Vista DVD when I have Vista 64 installed.  Think it matters? Or any other ideas?

Here is my new fdisk output anyways:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5b5d5b5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2            2433        2918     3903795   82  Linux swap / Solaris

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7a6e1a58

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18242   146521088    7  HPFS/NTFS
```

---

### Post by confused57 on 2008-01-10
I'm not sure what's going on, but did you happen to have an XP/Vista dualboot before you installed Ubuntu on /dev/sda?:
[http://users.bigpond.net.au/hermanzone/p15.htm#BOOTMGR_is_missing](http://users.bigpond.net.au/hermanzone/p15.htm#BOOTMGR_is_missing)

---

### Post by nugz45 on 2008-01-10
I had an Ubuntu/XP dual boot on that drive, but not a XP/Vista dual bot. 

When I installed Ubuntu this time however, I formated both partitions.  My old XP/Ubuntu installation was cleared on /dev/sda.    

What would happen if I removed /dev/sda from my computer all together?  Think my /dev/sdb would boot all by itself?

---

### Post by nugz45 on 2008-01-10
Ok well I know my bootmgr is there...I just found it on my Vista partition...

[IMG]http://williamberry.net/bootmgr.jpg[/IMG]

Anyone know if this is in the right place? If so, how come Vista cant see it?

---

