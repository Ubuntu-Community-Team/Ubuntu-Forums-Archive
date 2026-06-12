---
title: "Wireless not working"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by Hannibal-King on 2010-04-30
Simple problem. Just installed UNR on my CompaQ Mini 730EO and the wireless isn't working.

I've played around with Ubuntu back in 2008, but can't really remember anything anymore.

So how do I install updates for the network card? Something with apt-get? How do I do this in UNR?

Basicly how do I get my wireless working on UNR.

---

### Post by Hannibal-King on 2010-04-30
Anyone?

---

### Post by pauljwells on 2010-04-30
I'm guessing you have a broadcom wireless chip - seems pretty standard on netbooks, mine has.

If you can plug into a wired ethernet cable to get online that makes things easier, otherwise you might be able to work with just the install CD, in which case In System, find 'software sources' and tick the checkbox for CD to allow you to get updates off the CD

Then look for 'hardware drivers' and let it look for appropriate drivers. Should come up with one called BCSTA or something like and one called BCM43. Try the BCM43 one. That worked for me.
YMMV Good luck

---

