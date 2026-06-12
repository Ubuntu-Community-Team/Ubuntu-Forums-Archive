---
title: "What it takes..."
date: 2004-11-30
forum: Installation &amp; Upgrades
---

### Post by alcibiades on 2004-11-30
This is what I've done so far in the effort to get working on our second linux box.

1)  Create partitions using Acronis (the installer didn't work properly, and its default would have been to wipe the hard drive).

2)  Add the windows partitions by
            mkdir in    /mnt
            editing fstab    ...with quite a string of stuff, of course.

3)  edit hotplug blacklist to get rid of pciehp and shpchp errors which prevented booting on the first attempt.

4)  add noacpi to the grub boot file, also using the editor, in the effort to get it to shutdown and power off - doesn't in fact work

5)  tried to get dial up networking working using modemlights, kppp (downloaded), wvdial....  The problems (unresolvable) fall into two categories
      - if I get a connexion, then dns doesn't work, because something is overwriting etc/resolv.conf. 
      - if I try to use Kppp, then I can't start pppd because of permissions.

In fact, even trying to use the modem via a router mostly fails, because etc/resolv.conf is always being blanked or (once) turns into a broken link.

Yes, I have checked the permissions and they are by the book.  Yes, I have tried manually configuring etc/resolv.conf.  Yes I have used the network config panel.   Yes I have tried pppconfig as root.   I have also tried getting resolvconf, which seemed to make it worse, so I took it out again.  

I can only see one thing to do:  Mandrake.

I am sure this is all perfectly resolvable by someone with a more detailed knowledge of Unix administration.  I am just a dumb user who has happily chugged along on mandrake for a few years.  But this distro is being handed out in provincial city bookstores across the UK, and probably elswhere.  What are we doing to those poor people?

As for me, Kppp was my last shot.  Its Mandrake now.  It is a most noble idea and a most noble set of ambitions.  The problem is the execution.

Al

---

