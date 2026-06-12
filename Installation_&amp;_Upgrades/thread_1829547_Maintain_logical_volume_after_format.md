---
title: "Maintain logical volume after format"
date: 2011-08-20
forum: Installation &amp; Upgrades
---

### Post by jant90 on 2011-08-20
I'm currently on Ubuntu Server 11.04 x86_64 and have configured a logical volume that contains 2x 2TB HDD's and mounted that volume in /data. The OS is installed to the first HDD (a 500GB one). So the system has 3 HDD's in total (1x 500GB OS disk and 2x 2TB data disks).

**I want to do a fresh install of Ubuntu Desktop on the system without losing the data in the 4TB logical volume currently mounted in /data. Is this possible and if so, how?**

Thanks.

---

### Post by Basher101 on 2011-08-20
It is ofcourse. Simply make a new partition for it. A question - do you have Swap space? run ```
free -m
``` in a terminal and paste the output. If you have swap you should make a custom installation, because otherwise it would create a new swap partition, and you dont need 2...

---

### Post by jant90 on 2011-08-20
So I would make a new partition and install Ubuntu Desktop (or even Windows 7, is that possible without screwing up bootfiles like MBR?) to that? Sounds like the logical thing to do indeed.

Now what I'm wondering is where the information about the LVM is stored, in case I wasn't clear: I want the /data mount (the 4TB LV) to be accessible on Ubuntu Desktop as well.


I do have swap space (but I don't think it's ever used as I have 4GB of RAM), but the output of free -m shows:
             total       used       free     shared    buffers     cached
Mem:          3686       1969       1716          0         52       1280
-/+ buffers/cache:        636       3049
Swap:         3815          0       3815

---

### Post by Basher101 on 2011-08-20
When you install ubuntu desktop, every storage device that is connected is accessable. Ofcourse the only issue you then could have are permissions on your server files, but this can easily be resolved. And you will need a custom installation then to avoid creating a new swap partition and just letting your ubuntu Desktop edition use it too. If you dont know how to do that, i will gladly provide screenshots for help

---

### Post by YesWeCan on 2011-08-20
> **jant90 said:**
> Now what I'm wondering is where the information about the LVM is stored, in case I wasn't clear: I want the /data mount (the 4TB LV) to be accessible on Ubuntu Desktop as well.
Hi and welcome.
So you made each 1TB disk an LVM physical volume, then concatenated them by adding both of them to a volume group?

If so, the LVM info is stored on the disks. So you could take your two 1TB disks and put them in another computer that is running Ubuntu, install LVM, and it will see your volume group and logical volumes.

---

### Post by jant90 on 2011-08-21
> **YesWeCan said:**
> Hi and welcome.
Thank you :).
> **YesWeCan said:**
> So you made each 1TB disk an LVM physical volume, then concatenated them by adding both of them to a volume group?
Not that it matters but they are 2TB disks, and indeed I put them both in the same volume group and then created one big (4TB) logical volume and created a filesystem on that.

> **YesWeCan said:**
> If so, the LVM info is stored on the disks. So you could take your two 1TB disks and put them in another computer that is running Ubuntu, install LVM, and it will see your volume group and logical volumes.
Somehow I thought to remember (I feel that I read it somewhere) that one of the downsides of LVM was that it gave problems with data safekeeping when formatting the system because the LV or volume group would not be recognized anymore after a format, but I guess I remember wrong.


But if the information about the LV's is indeed stored on the disks themselves I guess all I need to to after a format remounting the filesystem?

Thanks!

---

### Post by YesWeCan on 2011-08-21
4GB - err, indeed.
To gain more confidence with an upgrade to 11.04, you might like to boot a 11.04 live CD/USB and then install lvm2 and activate your LVM volume group. Then you can mount your logical volume(s) and check your data can be accessed properly:

```
sudo apt-get install lvm2
sudo vgchange -ay
```

---

