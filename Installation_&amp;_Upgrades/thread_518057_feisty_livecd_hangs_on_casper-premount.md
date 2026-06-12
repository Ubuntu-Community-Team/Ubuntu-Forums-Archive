---
title: "feisty livecd hangs on casper-premount"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by jhoward23 on 2007-08-05
Attempting to boot Feisty via the LiveCD fails on my vanilla desktop machine, but works flawlessly on my Dell Latitude D400.

After removing "quiet" from the list of boot options, the last thing I see before it hangs is "Running /scripts/casper-premount   Ok".  After that it hangs and the system repeatedly accesses the CD and floppy drives.

Is there a boot parameter I can add to get more detailed information?

The machine is a P4 Northwood w/ Intel-brand 845 motherboard and a Radeon 9600.  Nothing especially exotic.

---

### Post by confused57 on 2007-08-05
You could try some or all of the parameters mentioned in this thread:
[http://ubuntuforums.org/showthread.php?p=3129680](http://ubuntuforums.org/showthread.php?p=3129680)

---

### Post by jhoward23 on 2007-08-05
Yep, I found that thread before posting and tried those.  Didn't seem to make a difference.  The weird thing is that I've installed Linux on this machine before (older version of Fedora, older version of MEPIS, older version of Gentoo) and everything was detected just fine.  The only thing I can think of that might have changed since then is that I swapped video cards, but at first glance this doesn't appear to be video-card-related.

Is there a boot param I can add to give more detailed output, so I can see exactly what it's doing when it hangs?

---

### Post by Pumalite on 2007-08-05
If you cannot install with the 'Live CD' at all, go with the Alternate CD; it's text based, gives you more control and you can see everything that's going on. You end up with the same system, while avoiding graphical interface or other hardware problems.

---

### Post by jhoward23 on 2007-08-05
Will try that next.  Though, I really don't think this is a graphics problem.  Could be wrong.

An update:  removing the "quiet" and "splash" boot options results in me being dumped to an "initramfs" prompt where I can view casper.log.  It contains the following:

mount: Mounting /dev/sda1 on /cdrom failed: no such device
/init: /init: 1: cannot open /dev/sr0: no such file
/init: /init: 1: cannot open /dev/sr0: no such file
mount: Mounting /dev/sda1 on /cdrom failed: no such device
stdin: I/O error
stdin: I/O error
Unable to find a medium containing a live filesystem.

So it looks like the problem is that it can't mount my CD-RW drive?

---

### Post by Pumalite on 2007-08-05
Some people have stuck a floppy in and voilá. Don't ask me how or why; I don't know.

---

### Post by jhoward23 on 2007-08-05
Another update:  This guy seems to have experienced something similar:

[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591/comments/8](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/84591/comments/8)

If I read his text correctly, then the script is trying to mount my *internal hard drive* (which is NTFS formatted and contains XP) instead of the CD-drive.  So somehow I need to get the CD-RW to show up as /dev/sda1 instead of the internal HDD.  Maybe I'll just disable the HDD entirely in BIOS.

---

### Post by jhoward23 on 2007-08-05
Ignore that last post.  When I turn off "splash" and actually look at the output as it scrolls by, I see a number of errors related to ata2 (my CD-RW drive).  There's an exception, a retry, a soft reset, then it just gives up.  So apparently that's the problem.  The drive is a Samsung CD-RW/DVD Combo Model# SN-324B.

Since I've installed Linux before w/ the same drive, I'm guessing something changed in the kernel that broke support for it.

---

### Post by jhoward23 on 2007-08-05
Okay, apparently I'm having the exact same problem as this guy:

[http://ubuntuforums.org/showthread.php?p=3138857](http://ubuntuforums.org/showthread.php?p=3138857)

According to him, this drive is supported in Edgy but not in Feisty.  Regression!  Boo!  :)

---

### Post by jhoward23 on 2007-08-06
Apparently my problems are caused by the fact that the kernel used by Feisty install uses libata for PATA devices, which causes my DVD/CD-RW drive to not be recognized properly.  This was fixed in subsequent kernels, then broken again, then fixed again.

I'm able to boot Gutsy Alpha-3 on this box and Edgy as well.  There are a number of open tickets against 2.6.20, but here's a representative one:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109706](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/109706)

Anybody know if there's a way to make the LiveCD use the "piix" module instead of "ata_piix"?  Can that be done via boot params?

---

### Post by 2newBuntu on 2007-08-13
I'm a total Linux newbie, but here is what I took from getting another Linux install to work after having the same problem:

press f6 at the startup screen, after the "--" type in "ide=nodma"  without the quotes of course.
So it looks like this:

 -- ide=nodma

I also like to erase "splash" and "quiet"

This seems to help it get by with older CD drives.  It seems to work on a lot of Linux installs.

Hope it helps.

---

### Post by Pumalite on 2007-08-13
In some BIOS you can set IDE Cofiguration to 'Enhanced Support for PATA+SATA' or 'Enhanced PATA Only' and it fixes the problem. That's how I fixed the problem myself. ( with Feisty I mean).

---

