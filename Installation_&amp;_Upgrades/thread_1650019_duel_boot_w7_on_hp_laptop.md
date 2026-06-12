---
title: "duel boot w7 on hp laptop"
date: 2010-12-20
forum: Installation &amp; Upgrades
---

### Post by Paul Barnett on 2010-12-20
I need advice on duel booting windows 7 and ubuntu on an hp laptop. All 4 partitions are taken up. I know i need to delete one partition to make room for ubuntu. Should I delete the windows recovery or hp partition? Or is there another option?

---

### Post by PhantmKllr on 2010-12-21
How did you end up with 4 partitions, from a previous installation of Ubuntu?

---

### Post by Quackers on 2010-12-21
I know that some people have deleted the HP Tools partition, then shrunk the C: drive to get some unallocated space for Ubuntu to install into.
I believe the HP Tools partition is used for diagnostic tools, which can be downloaded from HP again. But that would be something for you to check first.

---

### Post by PhantmKllr on 2010-12-21
When I set up my Laptop, I deleted all the partitions except the Windows partition (backup, windows recovery). Then I installed Ubuntu into the free space.

---

### Post by oldfred on 2010-12-21
Some have said that with HP the creation of the recovery DVD is a one time event. If it does not work, you still have to buy a copy. I would make the recovery DVD and if it lets you make a repair CD, which may be of  more use. I do not think I would want to ever use the recovery after more than a few months of changes, updates, etc. as I would not want to have to redo all that in windows. But then I like Ubuntu.

Since the tools partition is usually small, you can back it up and then reinstall in a new separate logical partition, if you really want to keep it on your system.

---

### Post by Paul Barnett on 2010-12-25
I deleted the hp partition and expanded it to accommodate ubuntu. I had to use the windows install disk (repair) to restart windows. I than installed ubuntu on the free space. Works great.:P

---

