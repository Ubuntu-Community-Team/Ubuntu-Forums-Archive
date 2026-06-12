---
title: "Dual install problem. No operating system"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by Bryan55 on 2010-07-07
I am wanting to put Ubuntu on to an Acer aspire One which already has Linpus lite on it.
However when I get to the partitioning stage it says "This computer has no operating system on it" though the partition slider shows there is?? See screenshot.

I'm unsure this will work as a dual boot. Should I proceed ?

Thanks for any help.

Bryan.

---

### Post by stlsaint on 2010-07-07
To be safe i would say to do a manual partition install. You will need to partitions for a install:
1)a swap partition
2) a root (/) partition

---

### Post by Karl10 on 2010-07-07
Hi Bryan

I'm far from an expert, but if I'm reading the screenshot right, the top bar is a "before" shot (Hard drive as the install program sees it,) and the bottom bar is an "after" shot, or how it will look after the install.  What's confusing me is that, as you pointed out, there appears to be no evidence of an existing OS, other than the checkbox that says, in effect, "put 'em in side by side and choose at boot."

"Choose WHAT?  There's no OS, didn't you just say so??? Stupid computer..... grumble grumble..."

Even stranger, to me at least, is that "both" OS's are being put into the first partition (/dev/sda1), and the swapfile on the second partition (/dev/sda2.)  I would expect to see three partitions; one for each OS, and a third for the swapfile (never heard of Linpus until this posting; have no idea if it needs a swapfile, but being Linux at heart, it probably does, and that would be the teeny-tiny little slice of green at the tail end of the top bar, also labeled /dev/sda2.)  Biggest unknown of all is whether the two OS's will peacefully share the swapfile; as shown, there's only one, and it's the same size both before, and after.

I'd be extremely reluctant to pull the trigger until  a few of these questions have answers.  Might be worth contacting Linpus for their take on this, too; I'm sure you aren't the first to have this idea.

Worst possible case; back up the drive, THEN go ahead and try it; if it goes down in flames, you can always wipe it clean and re-install the backup, none the worse for wear.  Just make sure you can boot from your backup disk(s), and that any tools you might need are on it as well (format, fdisk, etc.)

Good luck with it; I'll be following this post, as I've a couple of older laptops that are too puny for a full-blown install of any newer Linux, or Windows for that matter; Linpus sounds like it might be the way to go.

Karl

---

### Post by Bryan55 on 2010-07-08
I have just try the same process on my main PC which has Ubuntu 9.10, for comparison, and the results are exactly the same. See screenshot.
I also tied it on a windows machine but it could identify the OS.

Is it normal for Ubuntu to not recognize another Linus OS???

Bryan.

---

