---
title: "changing partition strategy"
date: 2010-01-22
forum: Installation &amp; Upgrades
---

### Post by grcunning on 2010-01-22
I've worked really hard to get my Ubuntu install just the way I like it, and now I want to move it to my new 1TB drive. I don't want to just clone it, because my current install is in one large partition. I would like to move it and modify my partition strategy so that when I do backups, I only have to back up those partitions. That way If the worst happens and I have to reinstall, I can install the base OS and then remount my backed up partitions and have my customized system back. (I'm not sure if this is even feasable). I'm relatively new to Linux, but perfectly comfortable in a terminal.
My questions are these:

1) Which dirs should be in their own partition? (most docs I've read are years old, or not Ubuntu specific)

2)Once I decide on my partitions, and I copy all the files over to the new drive, what other steps do I need to take to make it bootable (grub? fstab? anything else?)

3) Is there a Ubuntu specific(or not, if it doesn't matter) document that describes in detail which files are stored where, and which directories must be backed up to restore a system?

4) Is there a document that describes the Ubuntu boot and init process in detail?

Please forgive me if these documents are in some easily accessible location and I just didn't see them. Thanks.

---

### Post by tachuela on 2010-01-22
For partitions; you need only '/' and '/home'
Look up 'separate /home'

---

### Post by C.S.Cameron on 2010-01-22
Booting from the Live CD or USB, you should be able to cp -a everything but home to a partition labeled / and then cp -a your home folder to a partition labeled /home.
With cp you will need to suitably format the partitions on the target drive and reinstall grub. 

dd can also be used. if so formatting and reinstalling grub should not be required.

[http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/?highlight=dd+file+size+limit](http://www.linuxquestions.org/questions/linux-newbie-8/learn-the-dd-command-362506/?highlight=dd+file+size+limit)

---

