---
title: "Reinstall Unity?"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by billWalker on 2011-05-02
Hi,

So I ended up interrupting my upgrade to Natty: I'd left my iPod plugged in during the upgrade, and it hung on reinstalling GRUB.

With great consternation, I kill -9'd the grub configuration, eventually figured out that the iPod was causing the problem, and, via apt-get clean, update, upgrade, managed to get a good copy of GRUB installed (phew).

Now, my PC starts fine, and I know that X is starting, because XBMC starts up and runs with no problem after boot (as I had it set to do).  Also, I can see the mouse cursor and get the usual login screen if I let it sleep.

But I have no desktop.  I just have a cursor on a blank screen.  I've tried sudo apt-get install --reinstall unity, but to no avail.  Is there anything else I can do before I give up and do a clean install?

Thanks,
bW

---

