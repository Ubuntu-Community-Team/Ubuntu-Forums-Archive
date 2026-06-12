---
title: "Installer wont properly partition disk"
date: 2006-06-03
forum: Installation &amp; Upgrades
---

### Post by modestmelody on 2006-06-03
I have a 24gb unused space on my SATA harddrive and despite my best wishes the Dapper setup will not create an EXT3 partition.  It doesn't mention any errors per se, but I cannot select that partition to install the root file system on, it does not come up on the drop down list on step 6 of 6 of the initial installer off the live CD.

---

### Post by catlett on 2006-06-03
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) gparted live cd is my favorite partitioner. It's a small download, 30mb. The best thing is it's a live cd so the hard drive isn't mounted and you can perform the partitioning without rebooting.
Since your having issues try deleting the partition first. Then choose to make a new partition from the deleted space. Sometimes this works when reformatting an existing partition doesn't.

---

### Post by modestmelody on 2006-06-03
Well that did it.  Thanks.

---

### Post by catlett on 2006-06-03
You work fast:D  Glad it worked. I've had nothing but good results with it.

---

