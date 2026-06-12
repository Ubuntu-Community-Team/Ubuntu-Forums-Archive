---
title: "partition resize ubuntu 15.10"
date: 2016-03-04
forum: Installation &amp; Upgrades
---

### Post by net_tech on 2016-03-04
Hi,

I have Ubuntu 15.10 installed on a 40GB HDD, however only 20GB was initially allocated. Is there a way to extend the boot and logical volume partitions?

GParted is showing 20GB of unallocated space, but only allows me to size the LVM partition down. 

Thanks

---

### Post by Dennis N on 2016-03-04
> GParted is showing 20GB of unallocated space, but only allows me to size the LVM partition down.

Are you confusing LVM partition with logical partition? If its a logical volume, you don't use gparted to make it bigger, you need to add more space from the volume group it's in. **lvextend** will do that and extend the file system as well.

```
dmn@Roxanne:~$ sudo lvextend --resizefs --size +5G /dev/files_vg/data1

```
adds 5 gB to logical volume data1 and resizes the file system as well.

---

### Post by net_tech on 2016-03-04
Thanks

just came back to post that I was able to follow the steps from this post

[http://www.geoffstratton.com/2013/08/resize-disk-ubuntu-lvm/](http://www.geoffstratton.com/2013/08/resize-disk-ubuntu-lvm/)

---

### Post by Dennis N on 2016-03-04
Yes, good link. I skipped over the first part: if necessary, getting more space for the volume group by adding a new PV created from the unallocated disk space. BTW, don't see many questions on working with LVM.

---

