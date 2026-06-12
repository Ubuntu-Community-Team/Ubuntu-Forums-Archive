---
title: "cant access partitions i created"
date: 2008-08-17
forum: Installation &amp; Upgrades
---

### Post by Breakar on 2008-08-17
When i was installing ubuntu, i made 2 partitions these partitions now show under filesystem, but i cant see any files in them and i can edit them when i try change the premissions by right clicking on the folders it is grayed out and says root only can access.

How can i make it so i can use these partitions, and can i create shortcuts to them and place them on my desktop.

---

### Post by Pumalite on 2008-08-17
Post:
sudo fdisk -lu

---

### Post by Breakar on 2008-08-17
```
sudo fdisk -lu

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bd8bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3903794     1951866   82  Linux swap / Solaris
/dev/sda2   *     3903795    23438834     9767520   83  Linux
/dev/sda3        23438835   140633009    58597087+  83  Linux
/dev/sda4       140633010   312496379    85931685    b  W95 FAT32

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2136e4ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       102398310   488392064   192996877+  83  Linux
/dev/sdb2              63   102398309    51199123+  83  Linux

Partition table entries are not in disk order
```

---

### Post by Pumalite on 2008-08-17
What partitions do you have problems with?

---

### Post by Breakar on 2008-08-17
> **Pumalite said:**
> What partitions do you have problems with?

/dev/sdb1       102398310   488392064   192996877+  83  Linux
/dev/sdb2              63   102398309    51199123+  83  Linux

these to, i have no access to them. I thought i had created them to file system but i guess i am wrong and their not there. Do i need to mount these partitions? or should they show some where i want them to save files on from torrents.

Should i follow this?
[http://www.ubuntux.org/edit-fstab-to-mount-partition-at-startup](http://www.ubuntux.org/edit-fstab-to-mount-partition-at-startup)

---

### Post by Pumalite on 2008-08-17
Normaly they can be mounted from Places>Home Folder. If you want something permanent; use the link.

---

### Post by Breakar on 2008-08-17
> **Pumalite said:**
> Normaly they can be mounted from Places>Home Folder. If you want something permanent; use the link.

even if its anther harddrive? if i go to places>home folder i dont see the partitions i created.

I just right clicked on the partition and went to properties and it says Status: Unmounted.

I tried mounting it using that guide above but i think that it mounted something else.

I recreated the partitions again, do you know how i should be mounting these partitions or should it show after i already created them in gparted


this is where i think i see the harddrive
[http://img123.imageshack.us/img123/3852/screenshottr9.png](http://img123.imageshack.us/img123/3852/screenshottr9.png)

but all it shows is lost+found and not my partitions?

---

### Post by Pumalite on 2008-08-17
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1

---

### Post by Breakar on 2008-08-17
> **Pumalite said:**
> sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1

thanks so is this correct

in terminal
```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
fstab sudo kate /etc/fstab
```

add the following line  /dev/sdb1 /media/sdb1 ext3 defaults 0 0

in terminal
```
 sudo mount -a
```

and for the second partition it will be sdb2?

---

### Post by Pumalite on 2008-08-17
Yes.

---

### Post by Breakar on 2008-08-17
this is annoyin as hell, i still coudlnt get premissions to my hard drive so i tried adding myself in group as root, and gave myself access to /root but iguess that is wrong cos i couldnt access home either, so i had to format!

But at least hopefuly this will solve my problems, i recreated the partitions again using ubuntu live cd and i created the partitions with there own directory for a example i created the 2 partitions mounted already to a dirtory called /torrents and one called /movies.

i hope this works.. :mad:

---

### Post by Breakar on 2008-08-17
Now i can locate the partitions and see them in filesystem, and they are mounted but now i am back to sqaure one trying to get permissions to to write to them.

they are on root only, and i need it to be writable by all.

> 
Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders, total 312500000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000bd8bc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63     3903794     1951866   82  Linux swap / Solaris
/dev/sda2   *     3903795    23438834     9767520   83  Linux
/dev/sda3        23438835   312496379   144528772+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x2136e4ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1       102398310   488392064   192996877+  83  Linux
/dev/sdb2              63   102398309    51199123+  83  Linux

Partition table entries are not in disk order

/dev/sdb1       102398310   488392064   192996877+  83  Linux
/dev/sdb2              63   102398309    51199123+  83  Linux

this is what i have done now

in terminal

```
sudo mkdir /media/sdb1
sudo mount -t ext3 /dev/sdb1 /media/sdb1
sudo gedit /etc/fstab
```

add the following line in the text editor.
```
/dev/sdb1 /media/sdb1 ext3 defaults 0 0
/dev/sdb2 /media/sdb2 ext3 defaults 0 0
```

in terminal
Code:

```
 sudo mount -a
```

i get the following
```
mount: mount point /media/sdb2 does not exist
```

edit;
i probably have to add which im going to try now
```
sudo mkdir /media/sdb2
sudo mount -t ext3 /dev/sdb2 /media/sdb2

```

wow still no permissions to these directory's
i think this is what i want to do but i dont know how to do "chown"
[http://ubuntuforums.org/showthread.php?t=625958](http://ubuntuforums.org/showthread.php?t=625958)

---

### Post by Breakar on 2008-08-17
Omg i finally worked it out after so many hours (9hrs)

sudo chown -R yourname:yourgroup /Your mount name (mine was torrentz)
sudo chmod -R 755 /torrentz

---

