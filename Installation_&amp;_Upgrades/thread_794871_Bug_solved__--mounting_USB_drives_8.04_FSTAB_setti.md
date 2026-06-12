---
title: "Bug solved  --mounting USB drives 8.04 FSTAB setting"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by u18b on 2008-05-15
There have been several threads about how when people upgraded to Hardy 8.04, suddenly, they could no longer access any USB drives.  This is a VERY disastrous bug.

I'm a newbie,  but after studying a lot of documents and doing a LOT of experimenting for a week, I figured it out.  Maybe this is old news.  But if it is something new, please pass this on.

The problem was-  I installed the Hardy 8.04 Live CD upgrade from a USB stick.  Yep!  That's where the bug is.  I like the fact that you could place the CD on a USB stick.  It made testing much faster- right?

HOWEVER!!!!  When I decided I liked Ubuntu and committed to installing it onto my hard drive, that is where the problem creeps in.  You see,  the install program ASSUMES that the install device will always be a CD-ROM.  But that is not the case here.

I had installed with a USB stick.

And when I did that,  with Ubuntu all loaded on my hard drive, now every single USB drive will not load.  What I eventually found was that there was a line in FSTAB that had SDB1 drive listed as a CD-ROM and the drive media as 9660 iso.  What the heck???

That was my clue.

Now, since I'm a newbie and know nothing, I did this the long and hard way.  So what I did was erase my Linux partition and start over.  I loaded Hardy again.  But this time I did it from the CD-Rom.

The end result was perfection.  All USB sticks work perfectly now.

When I open my FSTAB now and see how it looks differently from before, the only difference I can see is that there is NO  SDB1  line  at all.   

Therefore,  I conclude (though I can't try it)  that the solution that I could have tried before would have been to simply  comment out  the  SDB1  line  by adding a  “#”  in front of it (what we in the USA call a pound sign).

And to fix this bug,  the developers need to correct the install program to NOT automatically assume that the program will always be installed from a CD-Rom.

Now, I'm a Newbie.  Experts,  please correct me at will.  I'm sure I said something wrong.

---

### Post by oliwek on 2008-07-24
I did experience exactly the same issue : after having tested hardy from a liveusb thumb drive and after install on hard drive, any usb key inserted (sdi1 in my case) was recognised as an external cd drive and would not automount (manual mount from command line was still possible)

commenting out the offending line in /etc/fstab/ solved the issue

(# /dev/sdi1                                  /media/cdrom0   udf,iso9660  user,noauto,exec,utf8       0  0)

congrats for your expertise, u18b  =D>

---

### Post by netdevil on 2008-09-16
thanx a lot man it helped me

---

### Post by howardf42 on 2008-09-22
Sadly, this fix hasn't worked for me.  The USB drive shows up in the Computer list of drives, but it doesn't mount.

HELP!

---

