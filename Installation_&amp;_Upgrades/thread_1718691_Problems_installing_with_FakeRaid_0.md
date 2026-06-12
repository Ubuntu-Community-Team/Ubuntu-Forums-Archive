---
title: "Problems installing with FakeRaid 0"
date: 2011-03-31
forum: Installation &amp; Upgrades
---

### Post by ericchile on 2011-03-31
I have two identical hard drives installed in a system with an Intel Controller. I set up the logical volume in the Bios and installed 10.04. I was able to partition just fine but grub had an issue installing. It said it could not be installed to /dev/sda even though I told it to install under /dev/mapper/...  

So I followed the instructions here 
[http://ubuntuforums.org/showthread.php?t=1584760](http://ubuntuforums.org/showthread.php?t=1584760)

And no matter what I do I can not seem get the system to boot off the Raid Volume... It just says no bootable device (have checked to make sure it is first in the boot order in the bios)

Any ideas?


More information

```
ubuntu@ubuntu:~$ ls -l /dev/mapper/
total 0
crw-rw---- 1 root root  10, 59 2011-03-31 22:09 control
brw-rw---- 1 root disk 252,  0 2011-03-31 22:09 isw_dgcbgiheje_Volume0
brw-rw---- 1 root disk 252,  1 2011-03-31 22:09 isw_dgcbgiheje_Volume01
brw-rw---- 1 root disk 252,  2 2011-03-31 22:09 isw_dgcbgiheje_Volume05

```

I also tried the following...
```

 sudo grub-install --root-directory=/mnt/ /dev/mapper/isw_dgcbgiheje_Volume0
You have a memory leak (not released memory pool):
 [0x1c041e0]
You have a memory leak (not released memory pool):
 [0x21131e0]
You have a memory leak (not released memory pool):
 [0x101b4f0]
You have a memory leak (not released memory pool):
 [0x1e2a4f0]
You have a memory leak (not released memory pool):
 [0x146c510]
Installation finished. No error reported.

```

---

### Post by ericchile on 2011-03-31
Ok this looks like it is an issue with my machine's bios as when I hit f12 and tell it to use the Raid Volume it boots correctly now.

---

