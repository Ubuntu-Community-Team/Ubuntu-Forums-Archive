---
title: "Wubi and/or GRUB problems in Karmic"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by Seadog01 on 2010-04-03
Apologies if this has already been covered (multiple times) before (I did spend some time lurking).  I upgraded my Karmic Koala installation, and now it won't boot!  It just drops me into the sh:grub command line.  After a little while searching the Google, I found this:  [http://www.omaregan.com/?p=583](http://www.omaregan.com/?p=583).  It seems that Wubi is, in fact, the problem (although I'm the first to admit I'm a newbie, so I could be wrong).  It also seems like that link has a nice solution.  The problem is that in the first, command, 

sh:grub> linux /boot/vmlinuz-(Your version of the kernel) root=/dev/(Your Windows partition) loop=/ubuntu/disks/root.disk ro

I can't seem to find my Windows partition.  I know it's on hd0,2, but that doesn't show up in /dev or anywhere else for me (/dev for me contains a bunch of stuff involving ram, stdin, stdout, tty, that sort of thing).  Also, all I see with an ls -l command is a listing of my partitions and their descriptions, not a path to where they're located.

Any advice would be *greatly* appreciated!

---

### Post by oldfred on 2010-04-03
This is a very common problem.

Fix for grub2 problem with wubi
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by Seadog01 on 2010-04-03
Oh, excellent -- that's way less work than I expected!  Thanks very much!  As an added bonus, those new kernels I couldn't run for mysterious reasons now work as well.  Strange this doesn't come up in a God... er, Google, search...

---

