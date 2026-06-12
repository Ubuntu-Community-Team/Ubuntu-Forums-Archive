---
title: "Only main drive in Computer File Browser"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by dpeteual on 2008-02-09
I made a clean install of 7.10. I partitioned the drive into 4 partitions. If I then boot from the live 7.10 CD, I  see the partitions in the Computer file browser. If I double click a partition it mounts. If I boot from the installed partition, I don't see the other partitions in the Computer File Browser. Why and what do I do about it? I know that I could possibly use the terminal to modify the fstab file but I didn't need to do this on previous installs of Ubuntu 6.

---

### Post by sigmarhophi on 2008-02-09
Did you format the partitions?  If the partitioned did not get formated for what ever reason, the auto mounter may not recognize the partition as anything.  

You can also add the partions in your fstab and have them mount every boot.  Plus you will have the advantage of calling the partitions what ever you wish IE backup, movies, music or what ever.

---

### Post by dpeteual on 2008-02-09
Thanks for the quick response. I did format the partitions. Also the Live 7.10 CD sees and mounts the partitions fine. Only the installed 7.10 does not see the partitions.

---

### Post by dpeteual on 2008-02-10
Solved. The problem was the mount point. In my 6.10 installation, the mount point for my shared FAT32 partition was /media. in the 7.10 the mount point was /Windows. By reinstalling and setting the mount point to /media, it appears on the desktop.

---

