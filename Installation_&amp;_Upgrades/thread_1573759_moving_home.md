---
title: "moving /home?"
date: 2010-09-13
forum: Installation &amp; Upgrades
---

### Post by frncz on 2010-09-13
Hello

I had to reinstall lucid. Originally, I had a partition with a / mount point and a second partition with a /home, plus a swap partition. (No windows, except in a VM). This was great.

When I reinstalled, I placed Ubuntu lucid in the initial partition at mount point /, and did nothing to the 2nd partition at all ( original/home mount point) as I wanted to avoid losing my data.

After re-install, I have unbuntu in the / partition as expected, but my data is in /media/_home/mike, and I have a new, unwanted folder /home/mike which resides in the same partition as /.

This is confusing.  I would like to migrate /home/mike to the 2nd partition, and transfer my data and all my installations from /media/_home/mike to it.

Can I do this, Or should I reinstall again, specifying the /home as the mountpoint of the 2nd partition, as in a fresh install. I did not do this as I feared this would have erased my data.

Thanks for your help.

Mike

---

### Post by linux-hack on 2010-09-13
well one way is to delete the partition on the mount point /home/mike and make a symbolic link to the other parition in /media/_home/mike.
This is a way to do that.

Or something like this : [http://www.go2linux.org/how-to-move-home-directory-to-another-partition](http://www.go2linux.org/how-to-move-home-directory-to-another-partition)

OR [http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/](http://embraceubuntu.com/2006/01/29/move-home-to-its-own-partition/)

Hope this helps :D

---

### Post by frncz on 2010-09-13
Thanks Boogy9. I will try tonight

Mike

---

### Post by oldfred on 2010-09-13
You can follow the procedure to move home, just that you have done the first parts of creating & copying data already.

To move /home uses rsync  
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

