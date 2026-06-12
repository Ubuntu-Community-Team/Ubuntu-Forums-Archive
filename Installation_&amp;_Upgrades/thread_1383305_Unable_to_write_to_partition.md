---
title: "Unable to write to partition"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by ferdi_t on 2010-01-17
Hello,

I used gparted to format and merge two partitions to a single 150gig partition. However, after mounting the partition (and entering my password) I am unable to write any files to it.

I tried looking at its permissions. Both its owner and group is root.

Could anyone help me by telling me how I could change this through gparted, the terminal, or any other way?

Thanks!

---

### Post by ajgreeny on 2010-01-17
If the partition is mounted manually after boot, rather than at boot by /etc/fstab, you probably need to change the ownership of the folder to which the partition is mounted.

However, the easiest way to do all this is probably to edit the /etc/fstab file, adding a line in order to get the partitio mounted at bootup.

Run ```
sudo fdisk -l
``` in terminal, which will show the format type (ext3, ntfs etc), and the device name of the partition (sdx#).  Then run ```
sudo blkid
``` to show the UUID of the partition and it will then be possible to tell you what line to add to fstab to both mount and give you read/write permissions to the partition as well

---

### Post by ferdi_t on 2010-01-17
Thanks for the reply. The partition shows up as expected:

```
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc51904e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1323    10626966    5  Extended
[COLOR="Red"]/dev/sda2            1324       20119   150978870   83  Linux[/COLOR]
/dev/sda3           20120       38914   150961152    7  HPFS/NTFS
/dev/sda5               1        1261    10128919+  83  Linux
/dev/sda6            1262        1323      497983+  82  Linux swap / Solaris
ferdi@ferdi-desktop:~$ sudo blkid
[COLOR="Red"]/dev/sda2: LABEL="meukschijf" UUID="901b66b0-9d00-4502-97bb-db6c74c02277" TYPE="ext2" [/COLOR]
/dev/sda3: UUID="220015C300159EBB" LABEL="DATA" TYPE="ntfs" 
/dev/sda5: UUID="c0a912f5-5683-42bf-b703-5157d30e6800" TYPE="ext3" 
/dev/sda6: UUID="565150f9-023a-4cd7-b2a1-144c7cc47b21" TYPE="swap" 
ferdi@ferdi-desktop:~$ 



```

So the second step is to edit etc/fstab, which seems doable, only that I don't know what to change. Any ideas?

```

# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sda5 :
UUID=c0a912f5-5683-42bf-b703-5157d30e6800 / ext3 relatime,errors=remount-ro 0 1
# Entry for /dev/sda6 :
UUID=565150f9-023a-4cd7-b2a1-144c7cc47b21 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda3 /media/sda3 ntfs-3g defaults,locale=en_US.UTF-8 0 0
/dev/sda2 /media/sda2 ext2 errors=remount-ro,users,user 0 0
```

---

### Post by ajgreeny on 2010-01-17
make sure you have a /media/sda2 folder ```
sudo mkdir /media/sda2
``` and then change the line in fstab to ```
/dev/sda2 /media/sda2 ext2 defaults, relatime 0 1
```  The *relatime* option is newer than the ones you were using.  You can change the **/dev/sda2** to 
[COLOR=Black]**UUID=901b66b0-9d00-4502-97bb-db6c74c02277** if you prefer, as it will be more in keeping with the new fstab format of using UUIDs.[/COLOR]  Try that and hopefully it will work for you.

---

