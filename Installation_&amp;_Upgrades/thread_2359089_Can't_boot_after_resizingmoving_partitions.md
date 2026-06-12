---
title: "Can't boot after resizing/moving partitions"
date: 2017-04-20
forum: Installation &amp; Upgrades
---

### Post by ckbcowboy on 2017-04-20
I resized and moved a few partitions, then followed the instructions in both of these places, with no luck:

[http://gparted.org/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem](http://gparted.org/display-doc.php?name=help-manual&lang=C#gparted-fix-grub-boot-problem)
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I see the GRUB menu and can boot into Windows ("Windows Boot Manager (on /dev/nvme0n1p1)" in GRUB) just fine, but when I try to boot into "Ubuntu" ("*Ubuntu" in GRUB), it sits for a while and then I get the "Welcome to emergency mode!" prompt.

There are also a bunch of new GRUB options that didn't exist before I changed my partitions.

My pastebin from Boot-Repair is here [http://paste2.org/WtKpgjmh](http://paste2.org/WtKpgjmh)

Help? Thanks!

---

### Post by TheFu on 2017-04-20
Welcome to the forums.

Need to see the **fstab file** and **blkid** output. Please use code tags for both.  Didn't see the fstab in the paste2.org stuff.
I suspect that the partition changes were sufficient to either change the order and/or alter the UUIDs.
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab) explains how the fstab file works.

---

### Post by ckbcowboy on 2017-04-20
I figured it out! I had actually deleted a partition to make space for the move, and didn't realize I also had to remove it from /etc/fstab. Once I did that, the computer booted just fine.

Thanks!

---

### Post by RobGoss on 2017-04-21
If you have resolved your issue you can mark this thread as solved by using the **Thread tool** at the top of this post

Thanks so much

---

### Post by Jim_in_Germany on 2017-05-31
> **ckbcowboy said:**
> I figured it out! I had actually deleted a partition to make space for the move, and didn't realize I also had to remove it from /etc/fstab. Once I did that, the computer booted just fine.

Thank you! I had exactly the same problem and this solved it for me. You saved me hours worth of work.

---

