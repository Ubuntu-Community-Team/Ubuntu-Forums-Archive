---
title: "Install alongside Windows option no longer available."
date: 2013-03-11
forum: Installation &amp; Upgrades
---

### Post by Malo Kingi on 2013-03-11
Hello everyone, 

While attempting to install Ubuntu, I chose to allow it to resize my partitions automatically. During the resize operation, there was an unspecified error (it looks like it simply hung). I then tried to complete the installation again, but the option to "install alongside windows" was no longer available. So I guess I'm not sure if I should attempt to resize my partitions manually, or if there is another option. Thanks in advance for any help. 

Acer Aspire
P6000
8GB ram
250GB HDD

---

### Post by darkod on 2013-03-11
If the resize stops for any reason, it can get messy. Does windows boot right now?

Also, it's best to resize the windows partition using windows Disk Management, not the ubuntu installer. Since Vista windows has this option to resize partitions.

You might need to recover the old partition table with tool like testdisk in order not to lose any data. I don't think you can try another resize right now, if the partition table is a mess because of the stopped resize operation.

---

### Post by Malo Kingi on 2013-03-11
Darko, I checked and windows does not boot anymore, and I don't even see it POST anymore. I'm using my ubuntu usb installation to access the internet right now. I guess that's why the "install alongside windows" option is no longer available. I hope I didn't just lose my windows partitiion. I'm not famillar with testdisk, but I'll do a little reading on it now. Thanks.

---

### Post by darkod on 2013-03-11
[www.cgsecurity.org/wiki/TestDisk_Step_By_Step](www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Just be careful and read everything twice. Especially before writing the new table, make sure all partitions you expect are shown.

---

### Post by Malo Kingi on 2013-03-11
Well, all is well. I unplugged my laptop, and took the battery out for awhile. When I restarted it, windows was able to correct the problem itself. Thanks for the assistance. I'll just try partition my laptop manually next time.

---

