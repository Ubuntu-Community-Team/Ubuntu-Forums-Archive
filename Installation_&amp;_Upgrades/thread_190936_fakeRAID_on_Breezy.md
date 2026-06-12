---
title: "fakeRAID on Breezy"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by otaku on 2006-06-06
I know this is the Dapper forum, but I can't find the Breezy forum.  Not sure if this is the right place, if not, I apologize.

I have a fakeRAID on my motherboard (VIA controller).  I dual boot with Windows 2003, so I want to keep the fakeRAID going.  Also, I have an AMD64 processor and am installing the AMD64 k8 install.

I followed the great HOWTO at [http://wiki.ubuntu.com/FakeRaidHowto/](http://wiki.ubuntu.com/FakeRaidHowto/) , but have run into some problems.

I followed the instructions to the letter.  Everything worked out OK.  That is, until I got to running base-config new.  This actually ran OK, but, I assume when it was done, it sent me to a login screen.  When I tried logging in using the username and password I had set up, it would not let me on and was giving me an error.  I was forced to restart the computer.

I went back onto the Live CD and completed the guide, creating my fstab file and such (of course, i had to install dmraid again).  It seemed everything was OK.

When I went to boot into recovery mode to continue the guide, I got a kernel panic while executing the scripts/local-top.  The panic is for "circular dependency".  I made a picture of the dump screen; unfortunately, I haven't received it yet.  I will update once that comes in.

When I boot up into normal ubuntu, I get only as far as "Mounting root file system", and I then get a freeze.

Since it appears to be having a problem mounting the filesystem, here are the contents of my /etc/fstab file:

proc 			/proc 	proc 	rw 0 0
/dev/mapper/via_bfeibeijij7 	/	ext2 	rw 0 1
/dev/mapper/via_bfeibeijij6	none	swap	sw 0 0

This is hopefully a simple and obvious mistake.  I haven't used any *nix flavors since my FreeBSD days many years ago.

Any help would be appreciated.  Please let me know if you need anything else.

---

### Post by otaku on 2006-06-07
I'd really appreciate any help that could be provided.  And if this is the wrong place, please let me know.

Thanks.

---

