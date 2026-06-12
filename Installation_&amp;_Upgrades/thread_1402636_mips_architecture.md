---
title: "mips architecture"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by conradin on 2010-02-09
Hi all,
I have some Indy 500 pizza box style work stations with the MIPS architecture running at about 300 MHz with 4MB of ram. Can anyone point me to a version of ubuntu compatible with this architecture / system? 

currently its running IRIX 5.3 and I hate it.

---

### Post by anglican on 2010-02-10
> **conradin said:**
> Hi all,
I have some Indy 500 pizza box style work stations with the MIPS architecture running at about 300 MHz with 4MB of ram. Can anyone point me to a version of ubuntu compatible with this architecture / system? 

currently its running IRIX 5.3 and I hate it.

The only linux distro I've ever come across for the (now defunct) mips/SGI computers is this:

[http://www.gentoo.org/proj/en/base/mips](http://www.gentoo.org/proj/en/base/mips)

I'm not sure how much (if any) activity there is on this project. You have a computer that's probably 15 years old! You might prefer the latest IRIX (6.5.22 for that box), try ebay for the CD's. Running 6.5 would open up quite a few modern applications (firefox, thunderbird etc..) from:

[http://www.mechanics.citg.tudelft.nl/~everdij/nekoware/]("http://www.mechanics.citg.tudelft.nl/%7Eeverdij/nekoware/")

There isn't, and never will be, a version of ubuntu that will run on that hardware. Sorry.

H

---

### Post by gmargo on 2010-02-10
Go to the mothership - **Debian** supports big- and little- endian MIPS architectures.  

[http://www.debian.org/releases/stable/releasenotes](http://www.debian.org/releases/stable/releasenotes)

---

### Post by cascade9 on 2010-02-10
Well, if its 4MB then fat chance of running any current distro. BTW OpenBSD and ROCK Linux also support mips.

---

### Post by conradin on 2010-02-10
Hey Thanks everyone! I'll check out the mother-ship and gentoo. I was also reading a book, that mentioned redhat having mips support but I haven't found much on that. Maybe ill just retire those boxes anyhow. Thanks everyone!

---

### Post by Simian Man on 2010-02-10
Yeah Debian and Gentoo are the only real Linux distros to consider when it comes to fringe architectures.

BTW I wish I had one of those :).

---

