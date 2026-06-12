---
title: "Server 10.4 LVM encrypted?"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by Zeophlite on 2010-05-05
Hello, this is my first installation of any form of *nix so forgive my lack of knowledge.
I burnt an Ubuntu Server 10.4 LTS iso to a CD and have started installing to my system: ASRock ION330, 4GB RAM, 320GB HDD.  I'd be using it for web hosting, maybe mail, and programming.  And possibly watching video (by HDMI into TV).

When I get up the the LVM part, I'm having trouble deciding what option to take.  Some of them:
[I]"Guided - use the entire disk and setup LVM"
[/I]*"Guided - use entire and setup encrypted LVM"*
*"Manual"*

After using google fu, I think I get the basic idea of LVM, that it abstracts the partitioning so I can change the size of them on the fly.  This means I can change it later, but the installer also mentioned that once I choose something, I couldn't turn back or something, which made me panic.

Also, if I choose encrypted, how does that affect my day-to-day usage?  Do I have to type in my password every time I access a file or save one?  That doesn't seem right.  Then what's the point of encrypting?  Is encryption worth it?  Google isn't telling me this sort of information (and I can't find it in help on the ubuntu website).  Keep in mind that I'm really just guessing.

Given my above hardware, and usage, should I just take *"Guided - use the entire disk and setup LVM"*?  Is encrypted a good idea?

Cheers,

Daniel

---

### Post by darolu on 2010-05-05
I wouldn't use encrypted for my very first linux installation; encrypting adds another layer of security to your files in case your computer is stolen or accessed by someone you don't want to see your files, other common case is when the wonderfully useful courteous and kind [TSA]("http://www.tsa.gov/") ask for your laptop and you don't want them to see your files. If this cases don't concern/apply to you, then don't use it, it can be problematic if something goes wrong (like forgetting your password, reinstalling).

I always choose the "Manual" option, that way you have total control, but if you don't feel comfortable doing it manual yet go for the guided LVM with no encryption. Again, is what I'd do for my first Linux installation, either way should work for you.

---

