---
title: "Minimum specs for installation"
date: 2004-11-05
forum: Installation &amp; Upgrades
---

### Post by fjleal on 2004-11-05
Hi all!

I've been having some problems installing Ubuntu on "old" machines, like PII/400 with 128 or 256 MB ram. The setup program fails right on the first phases of installation. One of these machines went through the whole setup, but then didn't boot complaining about a grub error (possibly a disk geometry problem). Another one didn't pass the keyboard recognition phase (?!?). When I ignored the error, the setup then complained it couldn't mount the CD. A third one stopped when copying "bsdutils".

I'd like to know from other users' experience what's the oldest configuration they managed to get Ubuntu running on, and if there are any special minimal requirements (apart from the obvious ones, like memory size) I should be aware of. Thank you. ;)

---

### Post by Rob on 2004-11-05
I've recently installed Ubuntu (Warty RC) on a PII 400 machine with 256 MB ram. I had trouble with the installation too. It would get to the mounting the CDROM part and fail.

In the end I solved this by replacing the CDROM (which was an LG I believe, I can dig out the model number if anyone is interested) with a new one, actually a Phillips CDRW.

Everything is running fine now. I was worried things would be a bit slow, but I've not noticed this so far, although it's early days.

Rob.

---

### Post by az on 2004-11-05
I had to burn the installation cd a second time at a lower speed.  My Tashiba laptop cdrom would not read it properly.  After that, everything went swimingly...

167 MHz
96 Megs of Ram.
2.1 Gig of harddrive.

I Think I ran out of disk space during the install when I told it to download updates from the internet.  It seemed to work when I only downloaded them afterwards.  (The setting up of Ubuntu-Desktop liberates about 350 megs of hard drive space by cleaning the packages cache...)

I actually went back to debian afterwards because Ubuntu although not so bad, was a little sluggish.  I also only have a few hundred megs of disk space left.

I reinstalled sarge with X, Abiword, Rox-filer and Firefox.  It only takes up about 500 megs....

I do run Ubuntu on my real computer, though...

---

