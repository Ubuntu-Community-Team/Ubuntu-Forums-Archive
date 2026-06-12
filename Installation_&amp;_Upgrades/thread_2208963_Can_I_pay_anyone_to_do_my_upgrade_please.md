---
title: "Can I pay anyone to do my upgrade please?"
date: 2014-03-03
forum: Installation &amp; Upgrades
---

### Post by Nick_Harvey on 2014-03-03
the server is running server 8 and needs to go up to the current version. needs to be done in the late US afternoon, as it is a webmin server in the uk, and my clients will start bleating!!
Any offers - I think I am too clueless to do it myself!!

---

### Post by TheFu on 2014-03-03
Welcome to the forums.

You don't want "the current version."  You want 12.04 and in a few months, 14.04.  Avoid 13.xx - for your setup.

For OS upgrades of this level, someone really needs to be physically at the machine OR have RIBLO access to the machine. I've had luck upgrading "Mom's PC" from across town, but ... servers are different.  Apache has changed over the years. I recall issues going from 8 --> 10 --> 12 and there have been reported issues with going to 13.10 - Apache 2.2 --> 2.4 just happened.

There are also some older hardware platforms which cannot be upgraded. The newer Ubuntu releases DO NOT RUN and cannot be made to run on some platforms.  I recall a D380 that wouldn't.

So - while I would offer my help, I cannot in good conscience without knowing that data. Please list:
* the exact hardware
* the major software used
* amount of storage
* the last time it was patched - 8.04 has been out of support for at least a year. VERY DANGEROUS!
* How backups are performed

Sometimes a fork-life upgrade will be better and easier. Newer servers will be
* under hardware support 
* much more power efficient, quieter
* much more capable than any box from 2008. It is like night and day, really.

It would have been easier to do these updates along the way, so the necessary changes would be fresh in our minds. There were some ugly changes in the network stack that I vaguely recall too.

So - anyone who offers to do the upgrade without asking all these questions first is flying by the seat of their pants and may or may not "get lucky".
- **hope is not a plan**.

---

