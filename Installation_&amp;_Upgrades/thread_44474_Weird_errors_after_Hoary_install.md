---
title: "Weird errors after Hoary install"
date: 2005-06-26
forum: Installation &amp; Upgrades
---

### Post by zee on 2005-06-26
Hi.
   After a fresh install of Hoary I get the following errors:
VFS: Can't find ext3 filesystem on dev hda5.
VFS: Can't find an ext2 filesystem on dev hda5.

   hda5 is the root (/) partition. After the above mentioned errors, the system boots normally:
ReiserFS: hda5: found reiserfs format "3.6" with standard journal
ReiserFS: hda5: using ordered data mode
ReiserFS: hda5: journal params: device hda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: hda5: checking transaction log (hda5)
ReiserFS: hda5: Using r5 hash to sort names

  The /etc/fstab is set up correctly.

thanks in advance,
zee

---

### Post by jasmuz on 2005-06-26
[QUOTE=zee]Hi.
   After a fresh install of Hoary I get the following errors:
VFS: Can't find ext3 filesystem on dev hda5.
VFS: Can't find an ext2 filesystem on dev hda5.

   hda5 is the root (/) partition. After the above mentioned errors, the system boots normally:
ReiserFS: hda5: found reiserfs format "3.6" with standard journal
ReiserFS: hda5: using ordered data mode
ReiserFS: hda5: journal params: device hda5, size 8192, journal first block 18, max trans len 1024, max batch 900, max commit age 30, max trans age 30
ReiserFS: hda5: checking transaction log (hda5)
ReiserFS: hda5: Using r5 hash to sort names

  The /etc/fstab is set up correctly.

thanks in advance,
zee[/QUOTE]
 Ubuntu likes the root partition to be Ext3, not ReiserFS..

---

### Post by zee on 2005-06-26
[QUOTE=jasmuz]Ubuntu likes the root partition to be Ext3, not ReiserFS..[/QUOTE]

Is there a way to change this behaviour?

---

