---
title: "write permission hell!!!"
date: 2005-02-26
forum: Installation &amp; Upgrades
---

### Post by Patrick on 2005-02-26
Ok this is what happend

I've put a line in fstab.

/dev/hdb  /mnt/data  ext3 rw,user,auto 0 0

When booting it mount perfect. I can go to it local, and through network, but i cant write to it .


what do i do.........., im so stuck right now.... chmod probably but.........my two braincelss are overloaded

sudo chown luis  /mnt/data -R gave me the change to write, but i can t move the files in new folders

---

### Post by doitashimashite on 2005-02-26
You might try this entry:

/dev/hdb       /mnt/data               ext3    defaults    0    1

---

### Post by alastair on 2005-02-26
[QUOTE=Patrick]
/dev/hdb  /mnt/data  ext3 rw,user,auto 0 0
[/QUOTE]

You mean "/dev/hdb1" (or some partition)?

You probably only need :

/dev/hdbX /mnt/data ext3 defaults 0 0

Replace "X" with your partitoon number.

First - check it is mounted - type :

mount

See the flags etc.

ls -l /mnt

Check perms.

ls -l /mnt/data

Check perms again.

I hate giving too much advice in case you follow it blindly and break something - so be careful.

Perhaps :

sudo chown -R <yourname>.<yourgroup> /mnt/data

---

