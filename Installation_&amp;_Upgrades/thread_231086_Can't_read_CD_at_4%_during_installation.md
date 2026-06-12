---
title: "Can't read CD at 4% during installation"
date: 2006-08-06
forum: Installation &amp; Upgrades
---

### Post by tripwire45 on 2006-08-06
I got everything prepared (I thought) and was ready to blow away Windows XP Pro on my Dell Inspirion 8200 and install Ubuntu 6.06. I put the CD in the drive and rebooted.

The ubuntu install menu came up and I selected start or install. The CD got to 4% and I got an I/O error saying that the CD couldn't be read and offering a reboot button. I rebooted thinking it might be a random error but no luck.

When it reboot again, I selected check CD for damage but the result was the same. After another reboot, I chose Boot in Graphics safe mode but no joy there, either. 

I tried searching for the error but only came up with an Ubuntu Forums archive where the error was can't read CD at 12%. No one posted an ultimate solution so I'm at a loss. 

I'm tempted to toss in my [killdisk](http://www.killdisk.com/) CD and blow everything away, then install from scratch...but that's a last resort. 

Any ideas?

---

### Post by tripwire45 on 2006-08-06
A little more information. The message at the top of the screen when the error message comes up reads as follows:

Loading /casper/vmlinuz....isolinux: Disk error BB, AX = 4280, drive 82

Also, the laptop's fan revs up right before the error occurs. This disk isn't one I downloaded and burned...it's commercially produced. I used it to install Ubuntu in VMware and that installation went like a dream.

---

### Post by tripwire45 on 2006-08-07
Looks like there's a clue here:

[http://www.fedoraforum.org/forum/archive/index.php/t-47526.html](http://www.fedoraforum.org/forum/archive/index.php/t-47526.html)

Close...but not an exact match.

---

### Post by tripwire45 on 2006-08-07
I tried upgrading my BIOS as suggested by [this](http://www.linuxsolved.com/forums/ftopic1759.html)
thread but my BIOS is the newest edition. Anyone know how to do an install from the hard drive?

---

### Post by tripwire45 on 2006-08-07
After all of that, it turns out that two small smudges on the install disk were at fault. I wiped them off with a soft cloth and BAM! ...the install went like a dream.

I smelled a rat when I tried to explore the disk on both Windows and my VMware Ubuntu machine and they both locked up. 

Anyway...I'm at the "Installing System" phase watching the orange bar slowly crawl across the screen (currently at 22% and rising). Glad I got this one whooped and that it turned out to be so simple.

Cheers. :D

---

### Post by -deadcats on 2006-08-07
Quite often a disc will exhibit these symptoms when burnt at high-speed. 4x or whatever the lowest speed the CD burner will handle seems to work out better.

Glad you're up and running.

regards,
-dc

---

