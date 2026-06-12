---
title: "How to Do cmp / diff on 2 partitions ?"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by just_ken_here on 2013-03-02
Hi

I have about 20gb of (18gb filled) ext4 SDA6 partition ---- which I wanted to retire and archieve.

I archieved into another drive (sdb8) :
I created new sdb8 on another drive with about 1mb of more space using gparted.
And used dd to copy the partition over.

I plan to remove the 20gb the SDA6 drive (to be used for other purpose).

But I would like to make sure if the files are the same (-- and perhaps the modified date attribute etc).
I look over with Nautilus, everything looks the same.

But is there any way that I can recursively diff / cmp thru the files and make sure each files are the same ?

---------------------------

I mounted both drives :
#mount -o ro /dev/sda6 /mnt/tsda6
#mount -o ro /dev/sdb8 /mnt/tsdb8

then did :#diff -r /mnt/tsda6 /mnt/tsdb8

But I get crap outputs like : [http://paste.ubuntu.com/5580503/](http://paste.ubuntu.com/5580503/)
and so on if I did not ^C it.

perhaps it seems because diff tries to read lines by lines of a file .. ?

----------------------------
I would like to use cmp recursively over the mounted drives. But this is just not possible ... not at least without a script or something to go recursive & do all files ...that I know of.

---------------------------
There is [http://www.linuxforums.org/forum/miscellaneous/158910-can-i-compare-two-partitions.html](http://www.linuxforums.org/forum/miscellaneous/158910-can-i-compare-two-partitions.html)
that suggested using md5sum on both partitions.

But I am not too sure if this is a quick and sure way. 
Although it seems that the script would do the job and md5sum the files only... But I am not too sure of how this works and also the speed of this.
And md5 would produce huge amount of files ?? ---over the 2x 20gb of stuffss on my drive.
(I only have less than 5gb left on current running partition.)

I did the dd transfer of almost 20gb for about 2 hrs or so..
I would like to do recursive cmp on all available files & binaries on both partitions ...

What's the good way to do this ?

Can anybody gives his/her take

Thx

---

### Post by just_ken_here on 2013-03-02
I have tried :

```
 

mkdir ~/comparedir
 sudo mkdir /mnt/test_sdb1
 sudo mkdir /mnt/test_sdc1

sudo mount -o ro /dev/sdb1 /mnt/test_sdb1
 sudo mount -o ro /dev/sdc1 /mnt/test_sdc1

find -type f /mnt/test_sdb1 -exec md5sum {} 2>/dev/null \; >~/comparedir/tmp_sdb1_hashes
 find -type f /mnt/test_sdc1 -exec md5sum {} 2>/dev/null \; >~/comparedir/tmp_sdc1_hashes

sudo umount /mnt/test_sdb1
sudo umount /mnt/test_sdc1
 sudo rm -r /mnt/test_sdb1
 sudo rm -r /mnt/test_sdb1

sort -k2 ~/comparedir/tmp_sdb1_hashes > ~/comparedir/sdb1_hashes
sort -k2 ~/comparedir/tmp_sdc1_hashes > ~/comparedir/sdc1_hashes
 rm ~/comparedir/tmp_sdb1_hashes ~/comparedir/tmp_sdc1_hashes
diff ~/comparedir/sdb1_hashes ~/comparedir/sdc1_hashes

```

from the linux forum website : [http://www.linuxforums.org/forum/miscellaneous/158910-can-i-compare-two-partitions.html](http://www.linuxforums.org/forum/miscellaneous/158910-can-i-compare-two-partitions.html)
but the tmp_hashes are files of 0 bytes.
I am not sure what's wrong yet, I have made sure that the naming, spaces etc were right.

 find -type f /mnt/tsda6/ -exec md5sum {} 2>/dev/null \; >~/comparekaron/tmp_sda6
 find -type f /mnt/tsdb8/ -exec md5sum {} 2>/dev/null \; >~/comparekaron/tmp_sdb8

but tmp_sda6 & tmp_sdb8 are both 0bytes .

---

