---
title: "importing /home from external disk"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by Freddie.Ruddick on 2006-02-20
Hi everyone,

I've just reinstalled Breezy, with /boot /home and / partitions. Now, my old installation was all on one partition, so before I formatted the HDD, I copied my entire home directory onto a USB Hard Drive. I now want to copy it onto the new install, but I can't for the life of me work out how to do it. 

Any ideas, anyone? 

Thanks

Freddie

---

### Post by linuxden on 2006-02-20
You could mount the USB drive and TAR your home directory into a file called Homedir.tgz (or whatever you wanna call it) and then copy that file over to your new drive....

then untar it and you should have an exact copy of your old home dir...

---

