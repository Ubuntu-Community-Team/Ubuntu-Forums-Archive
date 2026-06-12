---
title: "Vista Partition not recognized"
date: 2008-11-30
forum: Installation &amp; Upgrades
---

### Post by dev3 on 2008-11-30
While Installing Ubuntu (when Partitioning was going on), I had a power faliure, and the installation stopped. After that I could not boot into the Vista OS. I reinstalled Ubuntu, but still cannot see the Vista Disk.

The output of fdisk is:
> 
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7b5046a5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18797   150986871   83  Linux
/dev/sda2           18798       19457     5301450    5  Extended
/dev/sda5           18798       18798        8001   82  Linux swap / Solaris
/dev/sda6           18799       19422     5012248+  83  Linux
/dev/sda7           19423       19457      281106   82  Linux swap / Solaris


When I go to fstab, this is what I see:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=df292131-0eab-4a64-8611-e2aece3126ec /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=62137fd6-37ec-4787-a330-431c571a4847 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

When I run, gparted, I can see the 150 GB partition, but it is unrecognized.

What can I now do??

---

### Post by lptr on 2008-12-01
Does only partially fit here, so I will keep it short:

Try using Vista boot CD to recover your Vista environment (repair option - you will find lots of descriptions in the net, how to been done). Then I would try reinstalling Ubuntu again.

Partition not accessible: This is just a shot in the dark - you are using Vista Bitlocker? After you disabled EFS using NTFS you may use the Vista partition from Linux, too.

Hope this helps

rob*

---

### Post by dev3 on 2008-12-01
well.. that's what I'm gonna do. The only problem is that this laptop, is one of those that comes  only with a recovery partition, not a Install disk.
So I'm bugging my friends for a Vista disk.

Till then, I was hoping, there was some way to do something, via Ubuntu, itself.

---

### Post by Mark Phelps on 2008-12-01
According to your fdisk listing, Vista is gone!  You only have Linux now.  You wiped out Vista when you installed Ubuntu.

If you want Vista back, your best bet would be to do the recovery option and then, either install Ubuntu inside Vista (using Wubi) or be more careful about installation next time so you can have a dual-boot system with both Vista and Ubuntu present.

Also, once Vista is restored, do NOT use Gparted (or any other Linux utility) to shrink the Vista partition to make room for Ubuntu.  It might work, but if it doesn't, you will have to repair the Vista installation using a Vista DVD -- which you already said you don't have -- or Vista won't boot after that.

---

### Post by dev3 on 2008-12-01
> **Mark Phelps said:**
> According to your fdisk listing, Vista is gone!

so just for my understanding, fstab says that the linux is on sda6
not sda1.
 What has then happened to sda1?

---

### Post by jimv on 2008-12-01
I don't think Vista is gone, but the partition table somehow got f'd up when the computer powered off.  You can try using Testdisk (you can install it through Synaptic) to try and recover the partition info.

This page has some info about using Testdisk:

[http://www.users.bigpond.net.au/hermanzone/p21.html](http://www.users.bigpond.net.au/hermanzone/p21.html)

---

### Post by Mark Phelps on 2008-12-01
I'm only going by your fdisk listing ... but according to that, there is NO Vista installation because, if there was, there would be an "NTFS" entry in your fdisk results -- and there is not.  

It's possible that Vista is still there inside the first partition, and testdisk might fix that -- but I wouldn't hold out hope, primarily because MS does weird things with Vista and NTFS that Linux utilities have a hard time figuring out.

If it does recover it, I hope you have a Vista DVD or Vista Recovery Disk handy, because you'll most probably have to boot into that and do a Startup Repair.

---

