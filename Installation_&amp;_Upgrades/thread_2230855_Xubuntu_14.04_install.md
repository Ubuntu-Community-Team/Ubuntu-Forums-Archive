---
title: "Xubuntu 14.04 install"
date: 2014-06-21
forum: Installation &amp; Upgrades
---

### Post by Autodave on 2014-06-21
Trying to install on a Dell optiplex, 3.3 quad core with 4 gig RAM.  I have tried using the DVD and USB stick.  Keep coming up with same error:

Kerenel panic - not syncing: VFS: unable to mount root fs on unmnown-block(2,0)

Bios was reset and is in legacy mode.

Any ideas?

---

### Post by squakie on 2014-06-21
To me at least, if sounds like a bad download.  I would download it again and check the md5sum when done, then burn to DVD at a slower rate instead of the usual default of maximum.

Regarding the BIOS - are you planning to dual-boot, or is this going to be an Ubuntu-only box?

EDIT:  did some searching on the net for the error message, which leads me to a couple of other questions:

- is the hard disk full?
- how did you create theUSB flash, and what size is the flash drive?

If you haven't already, you may want to try searching the net with the following search string:

ubuntu Kernel panic - not syncing: VFS: unable to mount root fs on unknown block

It returns a lot of hits - some old, some new.  I really don't think I can help on this, so you may want to read through those and see if you find anything that helps.

Hopefully someone with more knowledge than me (believe me - that's not hard) can come along and give you better guidance.

Sorry I couldn't be of more help!

---

### Post by Autodave on 2014-06-21
Single boot.  This is a machine that was discarded where I work.  I got it with no memory or HD.  After putting a 4 gig strip (new) and a good, used HD in it, I proceeded to d-l 14.04 and try to install.  I had already installed 14.04 from same disk to another machine and it worked on there.  And, it was burned at a very slow speed, too.  However, I was thinking the same as you, because as I type this, 12.04 is installing without a hitch.

I will d-l another copy and see what happens.

---

### Post by squakie on 2014-06-21
Did you by chance download the 64-bit version (the default) and is perhaps this machine 32-bit?  Wish I could think of more.

---

### Post by Autodave on 2014-06-22
32 and 64 bit both tried.  It is a 64 bit machine: 3.3 quad core w/8gig RAM.  I am beginning to think possible prob with machine.

However, I pulled a HD out of another Xubuntu machine and stuck it in and it runs fine.

---

### Post by squakie on 2014-06-22
Does sound like a bad drive or some other type of incompatibility.  Glad you found it!

Sorry I couldn't have been of more help!

---

