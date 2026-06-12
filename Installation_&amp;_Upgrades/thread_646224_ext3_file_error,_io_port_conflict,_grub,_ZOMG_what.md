---
title: "ext3 file error, i/o port conflict, grub?, ZOMG what do I do?"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by snorlax22 on 2007-12-20
Hi,

I received a 600 mhz Pentium 3 box running Win NT Service Pack 6a with 670 MB RAM.  It has a Western Digital Caviar 313000 13 GB EIDE drive that was partioned into 2GB and an 11GB pieces.

I got the Ubunto 7.1 CD in the mail and fired it up.  It ran.  I decided to install.

I walked through the screens and answered the questions.  

I selected "Guided" for the partioning because I don't know what I'm doing.

The installation did its thing and then came back and said "The ext3 file system creation in partition #1 of IDE master (hda) failed."

I tried to select some partition sizes myself and tried to use the / thing correctly to identify my start point.  Got the same error.  

Now when I fire it up it says "Conflict I/O ports:  2F8" on what I think is a BIOS screen.

If I continue I get OS Loader v4.0 and I can select Ubuntu.  I select that and it blows up.  

"find --set -root --ignore-floppies /ubuntu/install/boot/grub/menu.lst
error 17
file not found"

Hit any key.

I get a GRUB4DOS menu.

ZOMG.  It won't boot into Linux and now it won't boot back into Win NT.

I think I must have a partial installation that has gone awry and I don't know what to do to recover from it.

Any help at all appreciated, including pointers to relevant and important stuff to read.

Mike

---

### Post by snorlax22 on 2007-12-21
I am downloading the alternate install iso thing and going to try and see if I can burn it to CD and make it work.

What is an ext3 file error anyway?

---

### Post by snorlax22 on 2007-12-22
WOOT!  Go me! Go  me!

I still don't know what went wrong or what any of this means but dig this:

I went "commandline" in the grub4dos thing. Cool huh?

I hit

cdrom --init
map --hook
chainloader (cd0)
boot

and I was there, baby!

Ran the install again and it went fine.

I type this to you, dear reader, in Firefox on my new Ubuntu box.

Pssshht.  It's Miller time!

Go me!

 :guitar:

---

