---
title: "Prepare Partitions"
date: 2010-05-24
forum: Installation &amp; Upgrades
---

### Post by SDSL on 2010-05-24
[IMG]http://img3.imageshack.us/img3/4702/screenshotcrr.png[/IMG]


[SIZE=5]Picture tells than words[/SIZE]
I've followed this post [http://ubuntugeek.com/forum/index.php?topic=237.0](http://ubuntugeek.com/forum/index.php?topic=237.0)
but still same issue appears
Laptop information: Toshiba Satellite L510

your help is much appreciated

---

### Post by srs5694 on 2010-05-24
See [my Web page on this problem.](http://www.rodsbooks.com/missing-parts/index.html) I make no promises that the cause is the same, but there's a good chance it'll at least put you on the right track. Post back with more details -- especially the output of "sudo fdisk -lu" -- if you need more help.

---

### Post by arrange on 2010-05-24
Yes, please provide the output of```
sudo fdisk -l
sudo parted -l
```

---

### Post by SDSL on 2010-05-24
```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9fd6479e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       12749   102302918+   7  HPFS/NTFS
/dev/sda4           12750       38914   210170362+   5  Extended
/dev/sda5           12750       17109    35021668+  83  Linux
/dev/sda6           17110       17375     2136613+  82  Linux swap / Solaris
/dev/sda7           17376       25496    65231901    7  HPFS/NTFS
/dev/sda8           25497       38914   107774657    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo parted -l
Error: Can't have a partition outside the disk!                           

Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label                                  

ubuntu@ubuntu:~$ 

```

---

### Post by SDSL on 2010-05-24
> **srs5694 said:**
> See [my Web page on this problem.]("http://www.rodsbooks.com/missing-parts/index.html") I make no promises that the cause is the same, but there's a good chance it'll at least put you on the right track. Post back with more details -- especially the output of "sudo fdisk -lu" -- if you need more help.
```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9fd6479e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   204812684   102302918+   7  HPFS/NTFS
/dev/sda4       204812685   625153409   210170362+   5  Extended
/dev/sda5       204812748   274856084    35021668+  83  Linux
/dev/sda6       274856148   279129374     2136613+  82  Linux swap / Solaris
/dev/sda7       279129438   409593239    65231901    7  HPFS/NTFS
/dev/sda8       409604096   625153409   107774657    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


```
i'll consider your webpage for this problem, but first i would like to give the Text mode installer a try since i already downloaded it

---

### Post by SDSL on 2010-05-24
> **srs5694 said:**
> See [my Web page on this problem.](http://www.rodsbooks.com/missing-parts/index.html) I make no promises that the cause is the same, but there's a good chance it'll at least put you on the right track. Post back with more details -- especially the output of "sudo fdisk -lu" -- if you need more help.

after i made the calculation into your page i found the size of the extended partition is correct, which is end-start+1
hence it's still not working even tried the "Text mode" installer

---

### Post by arrange on 2010-05-24
> **SDSL said:**
> ```

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total [COLOR="Red"]625142448[/COLOR] sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9fd6479e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      206847      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2          206848   204812684   102302918+   7  HPFS/NTFS
/dev/sda4       204812685   625153409   210170362+   5  Extended
/dev/sda5       204812748   274856084    35021668+  83  Linux
/dev/sda6       274856148   279129374     2136613+  82  Linux swap / Solaris
/dev/sda7       279129438   409593239    65231901    7  HPFS/NTFS
/dev/sda8       409604096   [COLOR="Red"]625153409[/COLOR]   107774657    7  HPFS/NTFS
ubuntu@ubuntu:~$ 


```
As you can see, the last partition exceeds the total number of sectors (and similarly for cylinders in *fdisk -l*).

You could try using more basic tools (than parted) to repair this, but I have never done this myself, so I'll just give you a few links to look at :) 
[http://ubuntuforums.org/showthread.php?t=352723](http://ubuntuforums.org/showthread.php?t=352723)
[http://ubuntuforums.org/showthread.php?t=1038943](http://ubuntuforums.org/showthread.php?t=1038943)

---

### Post by SDSL on 2010-05-24
thank you arrange for the hint

i missed getting the total number of sector
your links was helpful

also the webpage of srs5694, describes your links in more details

will let you know when I've something

---

### Post by SDSL on 2010-05-24
fantastic,
i used Hrien's boot CD to fix the partition table which exceeds the total harddist sectors
just used Partitioning GUI application from within the hrien's BootCD then resized the last partition little bit smaller 

and now everything works fine,

Thank you everyone for your help

---

### Post by srs5694 on 2010-05-24
My Web page provides the solution, with one major caveat: That last logical partition extends past the end of the disk. If it contains no important data, I recommend you delete it using fdisk; then you'll be able to proceed as described on my Web page. If the partition contains important data, the best and safest option is probably to back the data up to another disk or partition, then delete the offending partition. If that's not practical, you may be tempted to attempt to resize the partition and filesystem; however, this type of error could well trigger bugs in partition manipulation tools, and those bugs could have very serious consequences (like trashing everything on your disk). I can't promise that such bugs will manifest, but this is a case of "garbage in, garbage out" -- even normally trustworthy programs sometimes misbehave when they're fed nonsensical data, which I'm afraid your partition table is. I therefore strongly recommend you back up that partition and delete it, even if doing so means you've got to buy another disk for use as temporary storage. Having such a disk as a permanent backup disk may be a good investment in any event. After you back it up and resize the extended partition, you should be able to re-create that final partition (just a little smaller) and copy your files back.

Edit: Oops; I somehow missed your last post. I'm glad you found a utility that fixed it. These situations *can* be dangerous, though. I've lost entire sets of partitions in the past because of partition table corruption.

---

