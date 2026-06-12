---
title: "accidentally re-formatted lvm2 partition to ntfs - any recovery possible?"
date: 2010-09-14
forum: Installation &amp; Upgrades
---

### Post by whoops2010 on 2010-09-14
I can't believe I did this but I'm fairly new to Linux and gparted and yesterday I misinterpreted /dev/sda5 (what was really a large lvm2 partition where Ubuntu was installed as well as my data!) as unused space and accidentally reformatted it to ntfs.

I know I know - dumb!  What I wouldn't give for a time machine!

My questions:

1.  I was reading about recovery software such as photorec - in my situation should I hope to at least be able to recover files off that reformatted partition?

2.  I'm surprised the machine doesn't even get to the grub menu anymore - yet I can mount /dev/sda1 and see the files for grub are still there (/dev/sd5 was under /dev/sda2 which is shown as "extended", and /dev/sda1 is shown as ext2/"boot").  Does it make sense that I clobbered that in reformatting /dev/sda5?

3.  Barring me being able to recover the files, and then reinstalling Ubuntu from scratch - there's no shorter path to resolution is there?  i.e. When I (stupidly) did the reformat of that partition it returned *really* fast, making me wonder there's no way for me to reformat /dev/sda5 *back* to lvm2, and actually "undo" what i did and even still have the old files is there?

Feeling really dumb today (thanks for any advice)...

---

### Post by Rubi1200 on 2010-09-14
See here for options:
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Testdisk is often used for tasks like this.

Read the information and warnings carefully please.

Good luck!

---

### Post by whoops2010 on 2010-09-14
Thanks I'm trying photorec it appears to be working, but a question:  Is it typical that none of the original directory names or files names are able to be restored (I'm getting generated file names with numbers on them).

Maybe this is the best it can do since my reformatting wiped out the directories and file names is that what happened?

In the link given I also see the descriptions of using testdisk to restore "lost partitions" - but I guess that's not possible for me since I actually reformatted the partition?  (just wanted to confirm - it would be nice to recover the original directory structures and file names - but I'm guessing it's not possible because of what I did...)

Thanks again.

---

