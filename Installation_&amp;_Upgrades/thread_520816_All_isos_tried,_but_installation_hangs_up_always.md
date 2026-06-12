---
title: "All isos tried, but installation hangs up always"
date: 2007-08-08
forum: Installation &amp; Upgrades
---

### Post by paullus on 2007-08-08
Dear All,

I have tried all available isos at Ubuntu and Xubuntu sites, but none works -- the installation hangs up at certain point. Any ideas?

Thanks in advance,

Paul

---

### Post by upthelum on 2007-08-08
What's the spec of your machine? Order the Live cd and give that a try, it wont take long for delivery, then you can at least rule out a problem with downloading it.

---

### Post by Pumalite on 2007-08-08
256 MB RAM or less> Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by paullus on 2007-08-08
> **upthelum said:**
> What's the spec of your machine? Order the Live cd and give that a try, it wont take long for delivery, then you can at least rule out a problem with downloading it.

Thanks.

I have confirmed that the checksums match; so, no need to order the Live CD. 

My hardware:

* 1GB RAM;
* 3 IDE disks;
* Pentium Dual Core;
* motherboard: GigaRAID ATAPI BIOS v 1.71.

Paul

---

### Post by Pumalite on 2007-08-08
When you say: 'I've tried all available isos'; does that include Alternate CD's?

---

### Post by paullus on 2007-08-08
> **Pumalite said:**
> When you say: 'I've tried all available isos'; does that include Alternate CD's?

Yes, I have also tried alternate CDs.

Paul

---

### Post by Pumalite on 2007-08-08
Check your BIOS. Make sure your IDE's are set to 'Auto'. It would help if you can tell us what error messages you encounter on installation. The more specific, the better. Particularly with the Alternate CD's.

---

### Post by paullus on 2007-08-08
> **Pumalite said:**
> Check your BIOS. Make sure your IDE's are set to 'Auto'. It would help if you can tell us what error messages you encounter on installation. The more specific, the better. Particularly with the Alternate CD's.

Tried now with IDE's set to 'Auto' and with the 7.0.4 Alternate CD, but getting something like the following:

ata1.01: SET of native returned 218103822; expected 234441648

Paul

---

### Post by Pumalite on 2007-08-08
Try then: 'Enhanced support for PATA+SATA' if you have it in your BIOS.

---

### Post by paullus on 2007-08-08
> **Pumalite said:**
> Try then: 'Enhanced support for PATA+SATA' if you have it in your BIOS.

Just did that, but unfortunately no progress. Again,

ata1.01: SET of native returned 218103822; expected 234441648

Paul

---

### Post by Pumalite on 2007-08-08
We'll have to think of other things then. Do you have a Linux installed? If so, then post fdisk -l ( small L)( or equivalent)

---

### Post by paullus on 2007-08-08
> **Pumalite said:**
> We'll have to think of other things then. Do you have a Linux installed? If so, then post fdisk -l ( small L)( or equivalent)

# fdisk -l
bash: fdisk: command not found
[root@mypc paulus]# /sbin/fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9965    80040960    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        3187    25597952    6  FAT16
/dev/hdb2            3188        3200      104422+  83  Linux
/dev/hdb3            3201       14593    91514272+  8e  Linux LVM

Disk /dev/hde: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1       10000    80324968+  83  Linux
/dev/hde2           10001       19457    75963352+  8e  Linux LVM
#

Paul

---

### Post by vexorian on 2007-08-08
does it always freeze in a certain stage? If so what's the stage in which it freezes?

---

### Post by paullus on 2007-08-08
> **vexorian said:**
> does it always freeze in a certain stage? If so what's the stage in which it freezes?

Yes, it freezes always some seconds after I click on the first option of the installation menu. 

Can the following bug 

[https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=242229](https://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=242229)

of the latest kernels be related?

Paul

---

### Post by vexorian on 2007-08-08
I've seen some computers take a lot of time during that first stage, and it was during an ubuntu seminar in which part of it was installing ubuntu on a computer that already got ubuntu.

You seem to have Linux already so I am thinking that these three experiences are related.

The thing is, that stage of installation took plenty of time but it did finish, try leaving it over night or when you have time, and check if it truly froze.

I'll see if google might help me find a good explanation for this issue.

---

### Post by Pumalite on 2007-08-08
I'm going to investigate it further too. I'll get back yo you if I find a solution.

---

### Post by paullus on 2007-08-09
> **vexorian said:**
> I've seen some computers take a lot of time during that first stage, and it was during an ubuntu seminar in which part of it was installing ubuntu on a computer that already got ubuntu.

You seem to have Linux already so I am thinking that these three experiences are related.

The thing is, that stage of installation took plenty of time but it did finish, try leaving it over night or when you have time, and check if it truly froze.

I'll see if google might help me find a good explanation for this issue.

I left the computer on overnight and no progress. Indeed, it freezes.

Paul

---

