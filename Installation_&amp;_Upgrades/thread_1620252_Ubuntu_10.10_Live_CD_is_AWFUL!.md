---
title: "Ubuntu 10.10 Live CD is AWFUL!"
date: 2010-11-12
forum: Installation &amp; Upgrades
---

### Post by DThurman on 2010-11-12
I have a multi-boot, 2x 2TB drives. Each drive has 15
partitions, both set up the same way; 3 WinOS primaries,
1 extended, 1 Master boot, 1 Swap, 4 Linux OS
distros each with it's separate boot partition, and
1 Win Data partition.  Notice that the Win Data partition
is 1 TB...

Now I am booting off of 10.10 LiveCD, and I am at the
point where there is a purple/pink background with the
words "Ubuntu" with the dots scanning to and fro,
and I notice that it is gathering hard disk/ partition
information long before anything even appears.  Oh, yeah,
the screen saver kicked in - black screen!  Oh... just
hit the shift key and it comes back!  Who hoo!

I discovered that the problem may be with ntfsresize,
it is being used for gathering disk partition size &
information and here I am, waiting for 30-45 minutes
for ntfsresize to complete it's job, 4 times/disc...
and it took a damn long time!

At first I thought LiveCD 10.10 was just brain dead...
but patience won out...  I was able to install 10.10 but
what a freaking wait! :/  45 Minutes of wait just to
get into LiveCD Ubuntu OS!?

Guess what.  After getting into LiveCD 10.10 Install, and
then making selections on the first menu, then clicking the
'Forward' button, ntfsresize flies again - a double whammy!
Another freaking wait!!!

Comparatively, Ubuntu 10.04 is MUCH quicker, it does not
waste any time scanning the disc, it gets right down
to business... entering Live CD.

Unfortunately, 10.04 is really bad - after running it
for 2 weeks, all of a sudden my /home directory was blown
away, and a TON of files were deposited into /lost+found
directory.

There is not a damn thing I did to cause it... no siree.
and no, I did not have any power blackouts either. Notice
that only 10.04 partition was corrupted - no other
partitions were affected.

Seems like a very poor decision was made with LiveCD 10.10.

---

### Post by lemming465 on 2010-11-13
Did you file this as a regression bug in launchpad?  That will up the odds that 11.04 fixes it.

---

