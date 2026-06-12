---
title: "quad-booting partition"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by smocksturr on 2007-05-26
Hello, I'm planning on buying an Acer laptop in the coming months, and I'd like to quad-boot XP, Vista, Kubuntu, and Mac OSX86, all for versatility and fun times.
This will all be on a 120 or 160 gig drive.
Is there a partition type I could use to make a single 'stuff' partition that all the OSes could easily read and write to?
Also, what's the story on Ubuntu's dual-core support?

---

### Post by ryanVickers on 2007-05-26
For duel-core support, it's better than windows by far, but the way it handels the processor depends on the program.  Mac OS and linux can both use most unix filesystem I think, like raiser, or ext2/3, but windows only uses it's own ones.  Linux is now able to safely write to NTFS, But I'm not sure about mac.  You could make one linux and one NTFS, then put mac and linux on one, and windows's on the other.

By the way, getting mac os to run on a non-mac is not as easy as it sounds - I've tried it, and after alot of trouble, got it to *almost* work.  It needs to be the first partition on the drive, the first drive(must not be sata) and other hardware stuff is picky.  If you can get it to work (or have in the past), great!  I'm just saying if it's your first ime, be ready to learn tons of stuff you don't know about, terms, reconfigurations of stuff, and long hours.  Another thing, I love linux, but if you get Mac OS working, why bother with anything else?

---

### Post by smocksturr on 2007-05-26
thank you for the advice.
i've had a small bit of experience with osx86, but i'd really like to give it more of a shot.
i'm not sure why i'd use all four.
for fun?
beats me.

---

### Post by dbott67 on 2007-05-26
Getting OSX to run on anything but a Mac will be painful.  If you really want to have a multi-boot system, buy a dual-core iBook.  With Parallels you can simultaneously run XP & OSX, or you can multi-boot the system.

You can pick up a 2.16 GHz Core 2 Duo with 1 GB & 120 GB hard drive for 1299.00 US.  They have models for under $1000.00 if your budget is tight.

-Dave

---

