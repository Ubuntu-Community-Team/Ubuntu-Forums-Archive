---
title: "RAMFS issue: reporting zero size by df -ha"
date: 2011-04-05
forum: Installation &amp; Upgrades
---

### Post by uyuy on 2011-04-05
I am trying to use ramfs, basically mounting RAM as a folder.

```
# sudo mount -tramfs -o size=2000m ramfs RAMFS/
```it showed OK in mount command:

```
none on /proc/fs/vmblock/mountPoint type vmblock (rw,relatime)
ramfs on /home/user/RAMFS type ramfs (rw,relatime,size=2000m)
```but df -ha reported it's size being zero:

```
# df -ha                                                                                                      
Filesystem            Size  Used Avail Use% Mounted on                                                                       
rootfs                 14G  6.0G  6.7G  47% /                                                                                
devtmpfs              7.6G  276K  7.6G   1% /dev                                                                             
tmpfs                 7.7G   16M  7.6G   1%                                                                                                                 
ramfs                    0     0     0   -  /home/user/RAMFS 
```The issue caused my intended application unable to use the mounted folder and showed messages of "**no space left in ....(folder)**":(

I tested this in more than one linux kernels with the same outcome. Kubuntu 9.04 7 10.10 both.
vmlinuz-2.6.35-28-generic inclusive.

Then I tested tmpfs instead of ramfs, **this issue does not exist in tmpfs**. However I prefer to use ramfs if I can resolve the zero size issue, because there are some differences between ramfs vs tmpfs, basically tmpfs uses swap while ramfs does not.
;)

---

