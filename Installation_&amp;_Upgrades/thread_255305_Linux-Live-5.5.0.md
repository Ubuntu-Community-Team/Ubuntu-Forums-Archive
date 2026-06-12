---
title: "Linux-Live-5.5.0"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by SimooZ on 2006-09-11
Has anybody got them working with Dapper?

I'm stuck a few days now. The building of the iso works without any problems. But unfortunately the booting process's aborting with this message:  
```
Fatal error occured -
LiveData not found. Searching for livecd.sgn file, but the file was not found. You are maybe using an unsupported boot device (e.g. SCSI or PCMCIA CD-ROM). Try to copy all data from CD/USB to your IDE harddis, for example to /mnt/sda1/ in Linux or C:\ in Windows. Then boot again.
```

I made some research and I think it's a problem in mounting the root fs. Output of mount:
```
/dev/root on / type ext2 (ro,nogrpid) 
proc on /proc type proc (rw,nodiratime)
sysfs on /sys type sysfs (rw)
```

I think the root fs has to be mounted rw and not ro. 

Maybe somebody in here has already used the linux-live-scripts and was more successful. I hope you can help me out here. Many thanks in advance.


[http://www.linux-live.org](http://www.linux-live.org)

---

### Post by crane on 2006-09-11
I plan on giving this a try tonight when I get home. I can't see why it would need to mout the OS as RW. Doesn't this just create an image of the filesystem in the home directory? Not sure if letting it write to the root filesystem is needed.

---

### Post by SimooZ on 2006-09-12
That would be great, thanks very much!

I don't think so. The rootfs needs to be writable for letting the boot script dynamically set up the mount points. As far as I remember is the trick of unionfs that it is possible to mount a read-only fs and all changes will be written directly into the ram.

---

