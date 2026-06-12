---
title: "Aborted partioning -&gt; unrecognized NTFS?"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by adelaide on 2006-07-06
When I tried resizing partitions to place my Ubuntu installation on my P4's hard drive during installation, I exited installation the step after, while trying to allocate another partition for the Ubuntu installation.  Now my 70GB NTFS /dev/hda2 partition still exists, but its file system is 'unrecognized', and I can't boot XP from it at all anymore.  Is there any way for me to get the partition recognized as NTFS again, or would I have to take the HD in for data recovery?

(Also, it's a bit late for me to be asking, but what's the correct way to allocate an additional partition(s) for Ubuntu on a previously XP drive during installation?)

---

### Post by orb9220 on 2006-07-06
Insert the windows xp cd and boot from that it will give u the option to enter recovery mode select that to enter recovery mode.

Enter into the command line console where u get the Prompt >

And type Fixmbr and hit enter.

This will restore the MasterBootRecord.

But it will also wipe out the grub loader so you will have to manually fix that later.

But should allow you to boot to xp again,

There might be better ways. Search the forums for MBR or Boot or dual boot
for possible alternate solutions.

Hope you suceed

---

### Post by adelaide on 2006-07-07
Thanks so much.  I thought I was screwed.

(But what's the 'grub loader'?)

---

### Post by orb9220 on 2006-07-07
It is installed by linux so u can boot multiple OS'es
Which it modifies the mbr to do it's magic.

Fixmbr has saved my Chee-Chee's a few times.

There should also be a way to get back to dapper then manually rerun the grub
program and reconfig and write the mbr for a dual boot.

Easy way would be to just go thru the dapper install procedure from scratch.

Have fun and don't ](*,) to much.

---

