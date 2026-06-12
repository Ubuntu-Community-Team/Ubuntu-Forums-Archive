---
title: "Primary or logical????"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by srikar on 2008-03-01
I dual boot windows and xp. When i install ubuntu it gives primary drive or logical drive option.

What exactly is the difference between them.Plzz explain in an understandable manner.

---

### Post by Pumalite on 2008-03-01
You can have up to 4 primary partitions in a hard drive. Windows needs primary partition and likes to be sda1. If you are going to install Ubuntu, have up to 3 primary and then create an extended partition, within which you can have multiple logical partitions. Ubuntu is quite happy working with logical partitions.

---

### Post by srikar on 2008-03-01
ok got it.But does setting ubuntu drive a primary drive(rather than logical) bring in some advantage???

---

### Post by Pumalite on 2008-03-01
None.

---

### Post by srikar on 2008-03-01
then why did the ubuntu developers giv that option when ubuntu works well wid logical partitions.??

---

### Post by Pumalite on 2008-03-01
Just because Ubuntu is great. It works where you put it.

---

### Post by srikar on 2008-03-01
clever answer :lolflag: .

---

### Post by regbsn on 2008-03-03
What's the difference between primary and logical?

Am I wrong:
You extend a primary partition to place logical drives on.

What needs a primary partition? What can use a logical partition?
GRUB
"/"
" / home"
Linux-swap
NTFS as a shared data partition

If I want to have a separate "/" and "/ home" and of course Linux swap, what type can each be for me to be able to reinstall Ubuntu and leave the "/ home and Linux-swap alone?

Links are welcome also for further reading...:-D

---

### Post by Pumalite on 2008-03-03
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://ubuntuforums.org/showthread.php?t=464425](http://ubuntuforums.org/showthread.php?t=464425)

---

### Post by regbsn on 2008-03-03
My problem with the [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) site is that I don't get an answer to ext3 - vs- NTFS for shared partition...pros and cons. Does it really only come down to which programs (XP or Linux) that I will more likely to need to overflow into the data partition.

Does ext3 fragment with program additions and deletions like NTFS does? I read somewhere that ext3 self defrags every 30 mounts. If so then this would solve that. If I could figure all this out then I could decide what partitions need to be primary and which could be logical off an extended partition?

Or am I just confused.

---

### Post by K.Mandla on 2008-03-04
> **regbsn said:**
> My problem with the [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning) site is that I don't get an answer to ext3 - vs- NTFS for shared partition...pros and cons. Does it really only come down to which programs (XP or Linux) that I will more likely to need to overflow into the data partition.
More or less. Since it's possible to work with either OS on either filesystem, it's really just a matter of convenience for you. If you think you'll use Ubuntu more, use the native filesystem for it. If you think Windows will be your workhorse, go with NTFS.
> **regbsn said:**
> Does ext3 fragment with program additions and deletions like NTFS does?
No. 
> **regbsn said:**
> I read somewhere that ext3 self defrags every 30 mounts.
No, it does a filesystem check every 30 mounts. It's not the same thing. You shouldn't ever need to defragment your Linux drive, although it is possible to do so, if you really, really want to.

---

### Post by housam on 2008-03-04
> **srikar said:**
> I dual boot windows and xp. When i install ubuntu it gives primary drive or logical drive option.

What exactly is the difference between them.Plzz explain in an understandable manner.

All here about partitions [[COLOR="Red"]_http://www.linux.com/base/ldp/howto/Partition/index.htmlt_[/COLOR]]("http://www.linux.com/base/ldp/howto/Partition/index.htmlt")

---

### Post by regbsn on 2008-03-29
> **K.Mandla said:**
> More or less. Since it's possible to work with either OS on either filesystem, it's really just a matter of convenience for you. If you think you'll use Ubuntu more, use the native filesystem for it. If you think Windows will be your workhorse, go with NTFS.

No. 

No, it does a filesystem check every 30 mounts. It's not the same thing. You shouldn't ever need to defragment your Linux drive, although it is possible to do so, if you really, really want to.


Even with frequent file deletions and additions?

---

