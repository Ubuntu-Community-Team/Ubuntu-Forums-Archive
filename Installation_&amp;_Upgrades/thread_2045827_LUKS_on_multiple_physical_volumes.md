---
title: "LUKS on multiple physical volumes"
date: 2012-08-22
forum: Installation &amp; Upgrades
---

### Post by Fait on 2012-08-22
Hi, Im trying to install Ubuntu 12.04 on two drives with lvm. Im using the alternate install disc. I selected manual partitioning and set up both drives as AES encrypted then added them to a volume group and created a logical volume for root and another for home.  My problem is that I need two passwords, one for each encrypted drive. I just want one password, effectivly I want to encrypt the volume group not have a separate password for each physical volume.                                                  EDIT: I want 1 encryption password. I realize I will have two passwords 1 for encryption and 1 for user. Right now I have 2 encryption passwords and when combined with my user password it makes three.

---

### Post by intel on 2012-08-23
Redo teh setup

put multiple pv/stripes on the two disks
combine all the stripes/pv on all disk into single unencrypted LVM

create an encrypted volume on top of it.
etc etc

Cheers!

---

### Post by DiagonalArg on 2012-08-27
I too have exactly this question.  intel (or someone) could you flesh out your answer?  It's just a bit cryptic for me.

Thanks

/DA

---

### Post by DiagonalArg on 2012-08-28
Ok, I see the problem.  In my case, I don't want to throw everything together into one LVM.  The issue is, I have two RAID devices, one of which has more redundancy than the other.  I want to keep some volumes (root, swap) on a device with more redundancy and one (backup) on a device with less.  If I throw them all together, then I won't be able to control which devices go with which volumes.  Whether there is some way to get around this issue, I'm still not clear.

So far I'm getting no love on the installation & upgrade thread.  I think I'll go over and try on the security forum.

---

