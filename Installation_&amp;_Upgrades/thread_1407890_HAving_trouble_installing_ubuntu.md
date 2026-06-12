---
title: "HAving trouble installing ubuntu"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by Tadcrazio on 2010-02-15
I want to dualboot with Windows 7, i didnt get the option to install step by step so in windows 7 i created a new partition. When i go to install ubuntu, still no step by step install. I figured i try it manually, didnt work. Took screen shots to show you what was going on more clearly.

---

### Post by Satoru-san on 2010-02-15
WOW, that is all kinds of wrong. Your swap it 77 gigs, and sda1 and sda2 are both ntfs o_O

You will have to do it manually.

/boot should be first and around 32-64 megs ext2 
swap should be 1.5x amount of RAM swap
/  should be the remainder of your drive ext4 (or 3)

---

### Post by darkod on 2010-02-15
Boot windows and delete the partition you created, in ubuntu called /dev/sda3. Windows can only create it as ntfs and linux doesn't work on ntfs. Deleting the partition will leave unallocated space on the hdd which is what you need.
Then start the ubuntu installer and it will offer another option, Use Largest Available Free space. Just use that or create your own partitions into the unallocated space using manual partitioning.
But you need at least 2 partitions, / and swap. It's better to let ubuntu do the default install into the unallocated space with the option I mentioned, if you are new to all this.

---

### Post by Tadcrazio on 2010-02-15
Thanks, deleted it and used unallocated space =) all set now!

---

