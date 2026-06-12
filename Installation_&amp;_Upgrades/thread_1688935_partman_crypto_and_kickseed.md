---
title: "partman crypto and kickseed"
date: 2011-02-16
forum: Installation &amp; Upgrades
---

### Post by junk408 on 2011-02-16
I'm working on a kickseed install for a company standard desktop image.  While I'm having a few nitpicky issues here and there, the biggest one right now is setting up whole disk encryption.  I know it can be done (the alternate CD has it as an option) but I can't seem to find any decent documentation on doing full disk encryption.  Anyone know any good docs on the matter?  Something simple that really lays out the options would be ideal.  Ex:

d-i partman-auto/disk string /dev/sda
d-i partman-auto/method string crypto
...

Where do I setup the passphrase?  Do I have to use the expert partitioning method (lay out the partition recipe) or can I have it do a standard (atomic?) partition scheme some how?

Help is appreciated.  I'm really itching to hand off a decent prototype soon.

---

