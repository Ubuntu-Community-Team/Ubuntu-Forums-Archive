---
title: "Encrypted LVM option in CrunchBang Linux installation?"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by Rytron on 2011-03-13
Hi.

I got a few options when installing CrunchBang 10 in VirtualBox {image attached}. Can someone explain in plain English what is Encrypted LVM and why would it be better than the default option?

Thanks.

---

### Post by kagerato on 2011-03-13
First thing to note is this: LVM and encryption are orthogonal concepts.  You can have one and not the other; they're independent.

Encryption refers to the data (in this case, the blocks on the hard disk) being cryptographically obfuscated such that it's very difficult to read their content (assuming you don't have the correct key).  There's much, much more to the cryptography than that, but I don't want to wander off into extreme complexity.  Entire books are regularly written about this.

LVM, on the other hand, refers to the logical volume management.  It's a way to construct multiple "logical" (virtual) storage devices which are composed physically (in reality) of multiple hard disks, flash drives, and whatever else.  There are many features which get laid on top of this essential concept, including RAID for redunancy, snapshots for backup and change tracking, and so forth.

This is one of those cases where if you don't have a compelling reason to think you need the feature, you should opt not to use it.

---

### Post by Rytron on 2011-03-14
Thank you kagerato. You explained it perfectly.

---

