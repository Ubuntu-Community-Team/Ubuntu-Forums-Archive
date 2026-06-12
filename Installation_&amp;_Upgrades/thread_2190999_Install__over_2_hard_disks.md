---
title: "Install / over 2 hard disks?"
date: 2013-11-30
forum: Installation &amp; Upgrades
---

### Post by spupazza on 2013-11-30
As per title, I'd like to install Ubuntu over 2 hard disks.
I mean in a way that the OS and its applications (including /home) use both disks.

Is that possible without having to use raid configuration (my 2 disks have not the same capacity)

---

### Post by deadflowr on 2013-11-30
Of course it is possible.
Set one disk as the root(/) partition and then set the second as the /home partition.
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

It is quite common for users to do this.
In fact you could say that the linux/unix file system is designed to use this method of spreading out the various directories across multiple disks, if needed.

---

### Post by heir4c on 2013-11-30
you could even use 20 drives for each folder under / like /boot; /etc; /var; /home... But that will do nobody, I think. :)

---

### Post by steeldriver on 2013-11-30
If you really want to span multiple disks as a single logical volume, there's also LVM or possibly unionfs

---

