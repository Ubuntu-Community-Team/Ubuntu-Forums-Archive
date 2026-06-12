---
title: "GRUB error-17, &quot;unrecognized filesystem&quot; -- RESOLVED"
date: 2007-04-11
forum: Installation &amp; Upgrades
---

### Post by dme7 on 2007-04-11
G'day, all ...

Background:

I have a quad-boot system (6.10, OpenBSD, FreeBSD, XP) that suffered the dreaded "GRUB Error 17" upon trying to boot back into 6.10 after patching XP.  The symptoms included:
* LiveCD 'gparted' saw the 6.10 partition as type 'ext3'
* LiveCD 'grub' claimed the partition had an un-recognizable filesystem that couldn't be mounted
* LiveCD could, in fact, mount the partition
* LiveCD 'grub' could not 'setup', because the parition couldn't be mounted.
* LiveCD 'fdisk -l' displayed the problem-partition as being of type 0x93 (Ameoba), when it should have been type-0x83 (ext2/ext3)

Solution: LiveCD 'grub':  
  parttype (hd0,0) 0x83
  root (hd0,0)
  setup (hd0)

Everything's back to normal ... but I have no idea how the partition-type got changed to "Ameoba".

Rgds,
doug

---

