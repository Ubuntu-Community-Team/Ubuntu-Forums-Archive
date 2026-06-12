---
title: "Can't mount fs after 8.04 &gt; 9.10 upgrade"
date: 2010-03-24
forum: Installation &amp; Upgrades
---

### Post by usquared on 2010-03-24
My server is on a virtual machine using Xen.  I was on 8.04 for a couple years, and decided to upgrade.  I went version by version with mostly no problems, but when I got to 9.10, the filesystem wouldn't mount.

One solution I've read is to try a paravirt kernel, which I did, and got the same results.  Below is an exerpt of what I get when booting.

I don't even know where to start - any ideas?

```
NET: Registered protocol family 17 
NET: Registered protocol family 15 
Bridge firewalling registered 
Ebtables v2.0 registered 
ebt_ulog: out of memory trying to call netlink_kernel_create 
802.1Q VLAN Support v1.8 Ben Greear <greearb@candelatech.com> 
All bugs added by David S. Miller <davem@redhat.com> 
SCTP: Hash tables configured (established 8192 bind 8192) 
registered taskstats version 1 
 unknown partition table 
blkfront: xvdb: barriers enabled 
 xvdb: unknown partition table 
XENBUS: Device with no driver: device/console/0 
md: Waiting for all devices to be available before autodetect 
md: If you don't use raid, use raid=noautodetect 
md: Autodetecting RAID arrays. 
md: Scanned 0 and added 0 devices. 
md: autorun ... 
md: ... autorun DONE. 
kjournald starting.  Commit interval 5 seconds 
EXT3-fs: mounted filesystem with writeback data mode. 
VFS: Mounted root (ext3 filesystem) readonly on device 202:0. 
Freeing unused kernel memory: 496k freed 
Write protecting the kernel read-only data: 7192k 
init: ureadahead main process (991) terminated with status 5 
mount: mount point /dev/pts does not exist 
mountall: mount /dev/pts [1001] terminated with status 32 
mountall: Filesystem could not be mounted: /dev/pts 
mount: mount point /dev/shm does not exist 
mountall: mount /dev/shm [1002] terminated with status 32 
mountall: Filesystem could not be mounted: /dev/shm 
mount: mount point /dev/pts does not exist 
mountall: mount /dev/pts [1006] terminated with status 32 
mountall: Filesystem could not be mounted: /dev/pts 
mount: mount point /dev/shm does not exist 
mountall: mount /dev/shm [1007] terminated with status 32 
mountall: Filesystem could not be mounted: /dev/shm 
init: mountall main process (996) terminated with status 4 
Mount of root filesystem failed. 
A maintenance shell will now be started. 

```

---

### Post by usquared on 2010-03-24
I found the answer on another forum:
[http://www.linode.com/forums/viewtopic.php?p=28115#28115](http://www.linode.com/forums/viewtopic.php?p=28115#28115)

---

