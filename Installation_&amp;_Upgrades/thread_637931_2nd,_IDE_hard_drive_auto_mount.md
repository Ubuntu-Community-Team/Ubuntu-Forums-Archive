---
title: "2nd, IDE hard drive auto mount"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by Evocation on 2007-12-11
I've done a bit of searching around for how to do this, but as I'm completely new to Linux I'd rather run it by some people here just to make sure I'm not about to mess up my computer

The drive mounts fine, but I have to mount it and enter my password every time I want to use it on start up

from the ```
sudo fdisk -l
```
```

Disk /dev/sda: 30.0 GB, 30060527616 bytes
255 heads, 63 sectors/track, 3654 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6cd36cd3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3654    29350723+  83  Linux

Disk /dev/sdb: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd958d958

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       23944   192330148+  83  Linux
/dev/sdb2           23945       24321     3028252+   5  Extended
/dev/sdb5           23945       24321     3028221   82  Linux swap / Solaris
```


So From [http://ubuntuforums.org/showthread.php?t=187816](http://ubuntuforums.org/showthread.php?t=187816)

I'm guessing i use 

```
gksudo gedit /etc/fstab
```
```
/dev/sda1   /media/sda1   ext3   defaults   0   1
```
```
sudo mkdir /media/sda1
```
```
sudo chown -R evo:evo /media/sda1
ls -la /media
```

Only thing is in my /media directory the disk is all disk, not sda1 so was working if i should change /media/sda1 that to /media/disk


Thanks for any help.

---

### Post by taurus on 2007-12-11
Did you reboot?

Then run

```
df -h
```

---

### Post by stainless_steel on 2008-03-16
i got it to automount my second hd just fine with "install the pysdm package (in Gutsy) and then use System-Administration-Storage Device Manager without any manual editing of the fstab file, and disregard most of the instructions that follow."
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions)

---

