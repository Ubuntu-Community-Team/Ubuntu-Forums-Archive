---
title: "Dual boot Windows 7 / Ubuntu"
date: 2010-02-02
forum: Installation &amp; Upgrades
---

### Post by vpn2010 on 2010-02-02
Hi all,
Just got my new brand laptop ASUS with Windows 7 on it. I would like to add Ubuntu amd64 9.10 in order to get a dual boot Win7/Ubuntu.

What's the safe way to do that ? Do I need any 3rd tool to resize current partition ?

Thanks in advance,

---

### Post by skymera on 2010-02-02
I've resized NTFS using Ubuntu tools many times. Though i always worry in case it goes wrong :(
I'd suggest resizing a Windows partition with a Windows tool. Not sure what there is now, but years ago i used Parititon Magic for XP.

Once you have some free space, whack in your Ubuntu CD and install :D

---

### Post by darkod on 2010-02-02
Since vista, windows disk management can do a resize of partitions. It is usually best to resize win7 system partition with it. DO NOT create any partition into the newly created unallocated space from windows. After that boot win7 few times to make sure it's happy after the resize. Then proceed with installing ubuntu into the unallocated space.

In case you have problems finding disk management, windows button + R, type diskmgmt.msc, hit Enter.

---

### Post by Mark Phelps on 2010-02-02
> **vpn2010 said:**
> ... What's the safe way to do that ? 

The "safest way" by far is using the already mentioned Win7 Disk Management utility to shrink the NTFS partition.  Using anything else runs the risk of filesystem corruption that will render Win7 unbootable.

Also -- and this is IMPORTANT --  before you start, use the Win7 built-in capability to create and burn a Win7 Repair CD.  You will need that later if you encounter Win7 boot problems after the dual-boot install.

---

