---
title: "HAL.dll corrupt/missing - tried everything"
date: 2007-01-05
forum: Installation &amp; Upgrades
---

### Post by coma_ on 2007-01-05
Hi - I've recently installed Ubuntu 6.10 and whenever I try to boot into Windows now, I get an error saying HAL.dll is corrupt or missing..

Now, I've tried to go to the Windows recovery console and do "expand d:\i386\hal.dl_ c:\windows\system32\"...
That didn't help. So I followed the guide at [http://www.ubuntuforums.org/showthread.php?t=78509](http://www.ubuntuforums.org/showthread.php?t=78509) and changed the partition(1)s in my boot.ini to partition(3) (my C: drive in windows is /dev/sda3)...
using partition(4) like the guy who wrote that reply says gives me a 'hardware error', and 3 or 1 give me the hal.dll error, which actually makes more sense..

Help? :/

Here's my current boot.ini:
```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /fastdetect
```

fdisk -l outputs:
```
coma@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/sda2               7         267     2096482+  82  Linux swap / Solaris
/dev/sda3   *        2552       14593    96727333+   7  HPFS/NTFS
/dev/sda4             268        2551    18346230   83  Linux
```

Thanks in advance!

---

### Post by coma_ on 2007-01-05
(sorry) bump.. still stuck :/

---

### Post by bulldog on 2007-01-05
Take a look at this link,maybe there's something of use to you.

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Windows_Booting_errors)

---

### Post by coma_ on 2007-01-05
Thanks, but it doesn't actually give any instructions about finding out the partition number (or, recommend some software to use to 'move' the partition back to number 1.. or if in gparted, then how/where to do it) :\

Could you give me a few pointers please?

---

### Post by bulldog on 2007-01-05
If you have the gparted live cd,

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

Boot from it and delete the swap file.
With a little luck you can create an extended partition as big as the swap was.
Do so and create in the extended partition a logical swap file from the space.

I only hope the extended isn't gonna be the first partition.

Another option is to delete the swap and add the space to your windows,this will be the first partition.
Then make some space for the swap and put it into an extended partition.
You just have to try what works best.

---

### Post by coma_ on 2007-01-05
Is using the gparted that comes with Windows good too? (after using swapoff)

Also, if I do those, I have to change my boot.ini back to partition(1), right?

---

### Post by bulldog on 2007-01-05
You mean comes with ubuntu I suppose.
Well it should do the trick **if you boot from the live ubuntu cd** you can't do anything with a mounted hard disk.

Yes if you manage to get windows back on the first partition,you should make it default again.

---

### Post by coma_ on 2007-01-05
Er, yeah I meant ubuntu ;p

Thanks!

---

### Post by coma_ on 2007-01-05
One more thing, is the partition number the number after /dev/sda, like in /dev/sda1 it would be 1?

Also, I have 2.05 GiB unallocated (I'm on from the live cd now) and it won't let me resize the windows partition (/dev/sda3)

[http://img507.imageshack.us/img507/2064/gparted2jv0.png](http://img507.imageshack.us/img507/2064/gparted2jv0.png) :<

---

### Post by bulldog on 2007-01-05
Yes sda1 is the first partition don't mess it with (hd0,0] which indicates the same.

You have unallocated space,but where is it?
If right in front of windows you should be able to add it to windows,but if there's a partition between it,you can't.
As I look at your partitions your swap is at the wrong place,it should be after windows.

If you delete the swap and make from this unallocated space an extended partition,would it be sda1 again?

---

### Post by coma_ on 2007-01-06
I just deleted all the ubuntu partitions and now it works (though I did have to reinstall windows.. and loose my registry etc ;p)

Well, the problem is that I can't get it to make the new partitions AFTER the windows partitions, because the unallocated space is before the Windows partition, and I can't add it to the Windows partition.

Once I add a new partition, the Windows partition goes /dev/sda2 and so on

---

### Post by bulldog on 2007-01-06
Bummer,well it keeps you off the streets, anyway if it all works you have learned something :D

---

