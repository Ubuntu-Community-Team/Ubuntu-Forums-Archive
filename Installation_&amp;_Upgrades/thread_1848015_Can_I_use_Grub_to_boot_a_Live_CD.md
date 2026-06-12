---
title: "Can I use Grub to boot a Live CD?"
date: 2011-09-21
forum: Installation &amp; Upgrades
---

### Post by wgn on 2011-09-21
I've got an old (1998 vintage) computer that I had running Xubuntu for my daughter to play games on.  I'm going to try to recycle it again as a print/file server.

This computer will not boot from a CD by itself.  I was able to use Smart Boot Manager a couple of years ago to by able get the Xubuntu Live CD to boot.  That isn't working any more.  The CD-ROM drive I was using back then has crapped out (won't open up with anything short of a crow bar), but luckily (I thought) I had an old CD burner installed too.  I've tried all of these solutions, [https://help.ubuntu.com/community/SmartBootManager]("https://help.ubuntu.com/community/SmartBootManager")  but none of them will "see" the CD burner.

Xubuntu on the other hand has no problem "seeing" the burner.  So I was wondering if it is possible to put an entry in Grub to load from the Live CD?  And if it is possible, what file on the CD do I need to point Grub to?

---

### Post by drs305 on 2011-09-21
I may have both good and (maybe) bad news for you. The good news is that Grub 2 can boot an ISO image. In fact, you can install the OS as well from the booted ISO.

The bad news is that Grub 2 can accomplish this but Grub legacy (0.97) cannot. Depends on which Grub you are running. You can check the Grub version with "grub-install -v". Grub 2 is 1.96 or later.

So if you have G2, refer to the following:

How to Boot an Ubuntu ISO with Grub 2:
[http://ubuntuforums.org/showthread.php?t=1549847]("http://ubuntuforums.org/showthread.php?t=1549847")

How to Install Grub 2 from an ISO on your hard drive:
[http://ubuntuforums.org/showthread.php?t=1599293]("http://ubuntuforums.org/showthread.php?t=1599293")

You can check the Grub version with "grub-install -v". Grub 2 is 1.96 or later.

---

### Post by wgn on 2011-09-22
Thanks.  I know it's Grub legacy because it's Xubuntu 8.04 (it's an old computer that wasn't hooked up to a network connection).

I'll have to search for instructions to upgrade to Grub2.  I think I've seen that in here before.  Hopefully I'll get some time tonight after work to keep playing with it.

Update:
[https://help.ubuntu.com/community/Grub2]("https://help.ubuntu.com/community/Grub2")

---

