---
title: "Deleted Bootloader files by mistake ((not GRUB)"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by engti on 2010-03-26
I cannot boot into by Ubuntu 9.1 machine....

Trying either GUI or rescue mode gives me the following error messages (which i copied by hand since they were in cli)

```
mount : mounting /dev/disk/by-uuid/64e5cb0d-058a-4a4c-af4b-7afb6427a72e3 on root failed : invalid argument

mount : mounting /sys on /root/sys failed : no such file or directory 
mount : mounting /dev on /root/dev failed : no such file or directory 
mount : mounting /proc on /root/proc failed : no such file or directory 

Target doesnt have /sbin/init
```

The only thing i remember doing before this is deleting some bootloader files... but they were on another disk so I didn't think that it would affect my ubuntu install. Guess I was wrong ](*,)

Any idea how I can recover my system? Help please, desperate out here....

---

### Post by oldfred on 2010-03-27
Lets run this from a liveCD to see what is there.

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

If you deleted your root files, you are in trouble, but if you did something that just forced a UUID change it may be possible to recover easily. It also may be possible to chroot into system and do major updates if enough is still there.

---

### Post by engti on 2010-03-27
Thanks Oldfred for yur tip.

I urgently needed a working system so I just went ahead and did a reinstall.

Thankfully I had kept all my data on separate partitions... I'm no stranger to complete wipeouts....


Cheers :)

---

