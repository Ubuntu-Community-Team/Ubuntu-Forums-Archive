---
title: "Possible to Install Ubuntu on SSD part of Hybrid Drive, Dual Boot?"
date: 2016-03-04
forum: Installation &amp; Upgrades
---

### Post by satan3 on 2016-03-04
Hi everyone,

So i'm reinstalling Ubuntu Mate alongside Windows 8.1 on a Dell Inspiron 7537, which has a 1TB Seagate Hybrid Drive with 8GB Solid State cache.  Up until they've coexisted peacefully.

This time I'm thinking of installing Ubuntu on the 8 GB Solid State drive.  I've read that it's possible to do this without making a pigs mickey of your windows installation if you turn Intel Rapid Storage Technology off in windows.  Is this a good idea or should i just steer well clear?

And is 8 GB enough for ubuntu mount point "/"?  Think Mate requires at least 6.6 gigs...

Thanks in advance for your responses....

---

### Post by yancek on 2016-03-04
Pre-installed windows 8 and later use UEFI, if that's the case with your machine read the link below.  You can't mix UEFI and MBR installs.  Well, you can but one of them won't boot.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

8GB is probably too small unless you don't do any updates, install new kernels or new software.  If you get 90-95% full on the hard drive, it won't likely boot.

---

### Post by satan3 on 2016-03-05
Thanks for your reply, i was thinking it would be tight, but just wanted to see if it was a *really* bad idea, which by the looks of it, it is.  

Thanks again for the info Yancek!

---

