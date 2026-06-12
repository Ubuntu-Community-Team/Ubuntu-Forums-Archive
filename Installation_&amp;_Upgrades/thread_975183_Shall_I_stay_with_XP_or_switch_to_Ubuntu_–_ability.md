---
title: "Shall I stay with XP or switch to Ubuntu – ability to use Promise TX4310 the issue"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by rhfc2812 on 2008-11-08
OK, I’m impressed with what I’ve seen of Ubuntu 8.10 and I’ve even got as far is running the CD version of the OS.  However, what concerns me about going any further is due to the fact that whilst XP happily utilises a Promise TX4310 card to provide access to two hard disks (which are currently mirrored as a large single NTFS drive, but I would like to shortly setup in a RAID 5 configuration), it is unclear in my mind if Ubuntu can use this hardware, and if it can, as a complete novice the prospects of trying to get this to work scares me.

Is there anybody out there who can assist?

---

### Post by rknoesel on 2008-11-18
I also recently tried to install Ubuntu 8.10 on my server with a Promise tx4310 fakeraid card and 4 Samsung 500GB drives.  When I set up RAID 10 using the Promise BIOS, Ubuntu did not recognize the drive.  In order for Ubuntu to see anything, I had to configure the Promise BIOS to treat the drives as individual drives.  I believe that your only RAID option at this point is to use software RAID, which for me is still too much of a pain to configure during installation (In order to get a fail-safe software RAID 10 to boot, I would have to make a dedicated boot partition using RAID 1, etc, etc... too much hassle.)

Sadly, I had to go back to using XP for my server, since it simply asks for a driver disk during installation, after which everything is smooth.

I'll give the tx4310 another shot when the next version of Ubuntu is released.  :)

---

