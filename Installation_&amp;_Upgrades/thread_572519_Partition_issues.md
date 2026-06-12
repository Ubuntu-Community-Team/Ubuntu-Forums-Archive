---
title: "Partition issues"
date: 2007-10-10
forum: Installation &amp; Upgrades
---

### Post by Skatchoo on 2007-10-10
I currently am setting up a dual boot with windows xp and ubuntu, I have an 80gb part for windows, and I was going to allocate the rest out for linux, but I ran into some problems.

the setup I was going to use was 4gib swap, 40gib root, rest for usr.  th is is a 250GiB HD, that leaves a little more than 100 GiB for usr.  First problem: since I can only have 4 prim parts on the drive, which parts if any would be safe to put on logical parts if i wanted to separate tmp and var.  I probably won't, but I was curious.

My home partion I was going to mount on a second 500GiB that I just got.  Second Problem: when I go to create the partition during setup, it changes to around 70ish gib.  No errors, no messages, just doesn't create for the full 500, and does 70ish instead.

Any help would be appreciated, out of my rant the questions I'd like answered if possible are:

What should/could I do in allocating the remaining 170ish GiB on my primary hd, taking into consideration I can only have 4 primary paritions and one is being used by windows, and

What am I doing wrong that is causing setup to not create the partition for /home for the full 500GiB.  I wish I could give you an error msg of some kind, but it doesn't give me one.

Again, any help is appreciated.  Thanks.

---

### Post by vanadium on 2007-10-10
Leave your first primary partition for windows, and then create an extended partition for the remainder of the drive. In that extended partition, yo can create as many partitions like you want and disk space allows.

Second issue is less clear to me. You should certainly have that second drive formatted as ext3 if you are going to use it as your home partition.

---

