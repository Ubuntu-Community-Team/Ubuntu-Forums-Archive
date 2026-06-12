---
title: "Attack of the Clones..."
date: 2012-06-20
forum: Installation &amp; Upgrades
---

### Post by RogerDavis on 2012-06-20
This is the new post suggested in the quote below.  I want to upgrade the hard drive without re-installing Ubuntu.  Since Windoze can do this, I'm guessing there is a way to do this in Ubuntu.

Of course, the idea is to start at first with the old hard drive (small), and end up with the new hard drive (much larger).

After that, it would be to clone the larger hard drive to another one exactly the same size and type for backup purposes.

Thanks!

================================
Quote:
Originally Posted by RogerDavis View Post

If I clone the hard drive to a larger one, will Ubuntu pick this up, adjust, and start normally - or must I do something special?

Thanks!
If you'll make a separate thread, me or someone else will happely give you the exact instructions to do this because the cloning only works on identical sized drives. It's not too complex, it just involves some steps to adjust the system. Burn a livecd beforehand because you'll need it for this.

---

### Post by papibe on 2012-06-21
Hi RogerDavis.

IMHO the right tool for the job is [Clonezilla]("http://clonezilla.org/"). It's a liveCD that allow you to clone your small HD into one of the same space or a bigger one.

In order to have a workable HD, you would have to take this additional steps (using the Ubuntu LiveCD):
[LIST]
[*]Edit your /etc/fstab and adjust the new partitions' UUID (use fdisk, and blkid).
[*]Update grub on the new bigger HD (take a look at [Boot Repair]("https://help.ubuntu.com/community/Boot-Repair")).
[/LIST]
Lastly, you should get into your BIOS and change the boot order so that your machine boots from the new bigger HD.

As for using the rest of the free space on the bigger HD, there are 3 options (they are discussed [here]("http://drbl.org/faq/fine-print.php?path=./2_System/26_resize.faq#26_resize.faq")). I would use the gparted (since it is the one I know best).

I hope that points you in the right direction.
Regards.

---

