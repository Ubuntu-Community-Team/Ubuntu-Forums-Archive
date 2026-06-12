---
title: "HOW TO: Find the UUID for your partitions"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Patrick K on 2007-04-21
Type "blkid" in a terminal. It returns the UUID for all partitions.

---

### Post by jdong on 2007-04-21
Also, **vol_id -u /dev/real_name** returns the UUID of any block device

(blkid fails on NTFS drives)

---

### Post by Patrick K on 2007-04-21
I tried your command and got this in return:

"error open volume"

Both with properly mounted partitions and unmounted volumes. Nothing was visibly running that would have these partitions open. Although I don't know that that should matter.

---

### Post by Rui Pais on 2007-04-21
> **Patrick K said:**
> I tried your command and got this in return:

"error open volume"

Both with properly mounted partitions and unmounted volumes. Nothing was visibly running that would have these partitions open. Although I don't know that that should matter.

with the vol_id you need administrative powers. Run it with sudo.

---

### Post by Dirty Ole on 2007-04-21
I was looking for this. :guitar:

---

### Post by Patrick K on 2007-04-21
With sudo I get "unknown vloume type".

---

### Post by chakkaradeep on 2007-04-21
> **Patrick K said:**
> With sudo I get "unknown vloume type".

I think you are doing some mistake, Here is my output,

```

chaks@chaks-laptop:~$ sudo vol_id /dev/sda4
ID_FS_USAGE=filesystem
ID_FS_TYPE=ext3
ID_FS_VERSION=1.0
ID_FS_UUID=961c6d4f-79c9-4edf-a774-d394c7384fa7
ID_FS_LABEL=
ID_FS_LABEL_SAFE=

```

---

### Post by chakkaradeep on 2007-04-21
> **Patrick K said:**
> Type "blkid" in a terminal. It returns the UUID for all partitions.

I think it does not return UUID for Windows Partition. To be more clear, here is the output,

```

chaks@chaks-laptop:~$ **sudo blkid **
/dev/sda1: TYPE="ntfs" 
/dev/sda3: UUID="faff795a-7767-4e57-bc84-4ea62fd4c2f1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda4: UUID="961c6d4f-79c9-4edf-a774-d394c7384fa7" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: TYPE="ntfs" 
/dev/sda6: TYPE="ntfs" 
/dev/sda7: UUID="f6ba4a42-67e2-4d68-acc5-a1424e1d5082" TYPE="swap" 
/dev/sda8: UUID="b4456ccd-3ae9-44fd-9499-0a33fbae8683" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb1: SEC_TYPE="msdos" UUID="0000-0000" TYPE="vfat" 
chaks@chaks-laptop:~$ **sudo vol_id /dev/sda1**
ID_FS_USAGE=filesystem
ID_FS_TYPE=ntfs
ID_FS_VERSION=3.1
ID_FS_UUID=46E435E7E435D9BF
ID_FS_LABEL=
ID_FS_LABEL_SAFE=

```

The **vol_id** does give UUID for /dev/sda1 than **blkid**

---

### Post by Patrick K on 2007-04-21
With vol_id I still just get > pk@pk-desktop:~$ sudo vol_id /dev/sda5
/dev/sda5: unknown volume type


With blkid this is what I get
```
pk@pk-desktop:~$ blkid
/dev/sda1: LABEL="WIN98" UUID="0000-0E54" TYPE="vfat" 
/dev/sda5: LABEL="ELF" UUID="0000-0E74" TYPE="vfat" 
/dev/sda6: LABEL="FACTOID" UUID="0000-0E75" TYPE="vfat" 
/dev/sda7: LABEL="GADZOOKS" UUID="0000-0E5F" TYPE="vfat" 
/dev/sda8: UUID="e1484135-3eb4-4f17-b03c-5e1e0d88b480" TYPE="swap" 
/dev/sdb1: LABEL="DIONYSUS" UUID="0000-0ED9" TYPE="vfat" 
/dev/sdb6: LABEL="JOVE" UUID="0000-0D8B" TYPE="vfat" 
/dev/sdb7: LABEL="FAVS" UUID="0000-0ED9" TYPE="vfat" 
/dev/sdb8: LABEL="FAVS2" UUID="0000-0D85" TYPE="vfat" 
/dev/sdb9: LABEL="MOVIES" UUID="0000-0D47" TYPE="vfat" 
/dev/sda9: LABEL="HAM" UUID="4598-9D46" TYPE="vfat" 
/dev/sda10: UUID="063da081-4ed5-4c75-a789-81de30b946bb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="9f8d6e0b-f3b0-40e3-9e26-b3dcc3f84410" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: SEC_TYPE="msdos" LABEL="TEMP" UUID="0000-0DAA" TYPE="vfat" 

```

Blkid shows vfat volumes on my system.

---

### Post by mcduck on 2007-04-21
One more way to do this is 'ls -la /dev/disk/by-uuid'
```
$ ls -la /dev/disk/by-uuid/
total 0
drwxr-xr-x 2 root root 180 2007-04-21 11:01 .
drwxr-xr-x 6 root root 120 2007-04-21 11:01 ..
lrwxrwxrwx 1 root root  10 2007-04-21 11:01 10f09c96-b5c3-4992-a1cb-d7d314cc3204 -> ../../sda1
lrwxrwxrwx 1 root root  10 2007-04-21 11:01 365d417b-a50b-4df9-8249-f17f37a542aa -> ../../hda3
lrwxrwxrwx 1 root root  10 2007-04-21 11:01 4533-DAA2 -> ../../sda2
lrwxrwxrwx 1 root root  10 2007-04-21 11:01 5eb2a44a-b765-4cd2-abe9-751ff3aa0046 -> ../../hda5
lrwxrwxrwx 1 root root  10 2007-04-21 11:01 66280a28-42cb-4664-ad19-0a0753ebda3a -> ../../hda6
lrwxrwxrwx 1 root root  10 2007-04-21 11:01 9877-489A -> ../../hda1
lrwxrwxrwx 1 root root  10 2007-04-21 11:01 B043-DF50 -> ../../hda2

```

---

### Post by chakkaradeep on 2007-04-21
> **Patrick K said:**
> With vol_id I still just get 

With blkid this is what I get
```
pk@pk-desktop:~$ blkid
/dev/sda1: LABEL="WIN98" UUID="0000-0E54" TYPE="vfat" 
/dev/sda5: LABEL="ELF" UUID="0000-0E74" TYPE="vfat" 
/dev/sda6: LABEL="FACTOID" UUID="0000-0E75" TYPE="vfat" 
/dev/sda7: LABEL="GADZOOKS" UUID="0000-0E5F" TYPE="vfat" 
/dev/sda8: UUID="e1484135-3eb4-4f17-b03c-5e1e0d88b480" TYPE="swap" 
/dev/sdb1: LABEL="DIONYSUS" UUID="0000-0ED9" TYPE="vfat" 
/dev/sdb6: LABEL="JOVE" UUID="0000-0D8B" TYPE="vfat" 
/dev/sdb7: LABEL="FAVS" UUID="0000-0ED9" TYPE="vfat" 
/dev/sdb8: LABEL="FAVS2" UUID="0000-0D85" TYPE="vfat" 
/dev/sdb9: LABEL="MOVIES" UUID="0000-0D47" TYPE="vfat" 
/dev/sda9: LABEL="HAM" UUID="4598-9D46" TYPE="vfat" 
/dev/sda10: UUID="063da081-4ed5-4c75-a789-81de30b946bb" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda11: UUID="9f8d6e0b-f3b0-40e3-9e26-b3dcc3f84410" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sdb5: SEC_TYPE="msdos" LABEL="TEMP" UUID="0000-0DAA" TYPE="vfat" 

```

Blkid shows vfat volumes on my system.

Ofcourse vol_id is correct. Becoz, for your partition entries, **/dev/sda5** should be the starting of the extended partition.

Can you please post the output of **sudo fdisk -l**

---

### Post by Patrick K on 2007-04-21
Sda5 is the E:\ drive in windows. It isn't the ext partition, sda2 is the ext partition.```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         610     4899793+   b  W95 FAT32
/dev/sda2             611       19457   151388527+   f  W95 Ext'd (LBA)
[COLOR="Magenta"]/dev/sda5             611        5325    37873206    b  W95 FAT32[/COLOR]
/dev/sda6            5326       10040    37873206    b  W95 FAT32
/dev/sda7           10041       14749    37825011    b  W95 FAT32
/dev/sda8           19327       19457     1052226   82  Linux swap / Solaris
/dev/sda9           14750       15532     6289416    b  W95 FAT32
/dev/sda10          15533       17559    16281846   83  Linux
/dev/sda11          17560       19326    14193396   83  Linux

```I can't say if it shows ntfs since I don't have that file system.

---

### Post by Rui Pais on 2007-04-21
thats strange... i wonder if you get a wrong answer from vol_id because of the layout of your partition table.
Maybe the 1st logical partition being number 5 instead of number 3 (and no 3 nor 4 is available) had confused the tool. 
In that case you would have found a bug...

whats the output of:
```
sudo vol_id -u /dev/sda1
```  or
```
sudo vol_id -u /dev/sdb1
```

---

### Post by chakkaradeep on 2007-04-21
> **Patrick K said:**
> 
/dev/sda2             611       19457   151388527+   f  W95 Ext'd (LBA)
[COLOR="Magenta"]/dev/sda5             611        5325    37873206    b  W95 FAT32[/COLOR]
[/CODE]


Can the start position be same for two partitions ??

I think there is some problem at the start of extendable partition:confused: :confused:

---

### Post by Patrick K on 2007-04-21
> pk@pk-desktop:~$ sudo vol_id -u /dev/sda1
/dev/sda1: unknown volume type
> pk@pk-desktop:~$ sudo vol_id -u /dev/sdb1
/dev/sdb1: unknown volume type
I figured out where vol_id gets in info. From /dev/.udev/db/filename. I just looked and the two partitions that were mounted automatically during the upgrade to Feisty, have the UUID number in thrie files. The ones I mounted manually don't. Here is one that was mounted automatically> pk@pk-desktop:~$ sudo vol_id -u /dev/sdb5
0000-0DAAThis one has a UUID number in its db file.



Chak, I don't think there is any problem with a logical partition starting at the same location as the extended partition. It's that way on both hard drives on this machine and on the drive in my other machine.

---

### Post by chakkaradeep on 2007-04-21
> **Patrick K said:**
> I figured out where vol_id gets in info. From /dev/.udev/db/filename. I just looked and the two partitions that were mounted automatically during the upgrade to Feisty, have the UUID number in thrie files. The ones I mounted manually don't. Here is one that was mounted automaticallyThis one has a UUID number in its db file.


Oh..is that udev bug or vol_id bug of not getting updated with mounted partitions :) 

> **Patrick K said:**
> 
Chak, I don't think there is any problem with a logical partition starting at the same location as the extended partition. It's that way on both hard drives on this machine and on the drive in my other machine.

Oh..if its working, no problem Patrick :)

---

### Post by Rui Pais on 2007-04-21
> **Patrick K said:**
> I figured out where vol_id gets in info. From /dev/.udev/db/filename. I just looked and the two partitions that were mounted automatically during the upgrade to Feisty, have the UUID number in thrie files. The ones I mounted manually don't. Here is one that was mounted automaticallyThis one has a UUID number in its db file.

Hi, you must have found a bug, or some config is broken in your box. vol_id should show the partition informations no matter if it's mounted or not mounted.

You should file a bug report.

---

### Post by linuxguiri on 2007-04-21
For some reason my fstab has identical UUIDs for two different partitions. 

Both /dev/sda1 and /dev/sda5 both have the same UUID.

blkid returns this:
```

/dev/sda1: SEC_TYPE="msdos" LABEL="DellUtility" UUID="07D6-0A19" TYPE="vfat" 
/dev/sda2: TYPE="ntfs" 
/dev/sda4: LABEL="DellRestore" UUID="0000-0000" TYPE="vfat" 
/dev/sda5: LABEL="MEDIADIRECT" UUID="07D6-0A19" TYPE="vfat" 
/dev/sda6: UUID="edf1bb5c-d9be-4f2a-b969-9a92f592e6bc" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda7: UUID="a241564b-e465-424f-a4bf-74997cae5ef1" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda8: TYPE="ntfs" 
/dev/sda9: UUID="292d9827-7ed5-4d5e-99bd-6af09c234b27" TYPE="swap" 
/dev/sda10: UUID="d09ffb9e-5fa4-4eee-986c-f1ad46cfe8da" SEC_TYPE="ext2" TYPE="ext3" 

```

"sudo vol_id -u /dev/sda1" returns the same results.

Also, dev/sda4 doesn't have any UUID associated with it.

Is there another way of looking up UUIDs?

This is after a clean install of Feisty BTW.

---

### Post by Patrick K on 2007-04-21
I might do that. I found a ton of broken links (660 of 694 files) in this directory. I Googled vol_id but understandable info is sparse.

---

