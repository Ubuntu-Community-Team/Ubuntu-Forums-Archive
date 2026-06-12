---
title: "I fancy a script..."
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by manzdagratiano on 2010-02-08
I wish to indulge in writing a script that does what apt does, except not quite:

I wish to check what versions of the packages are installed, and if they are GREATER than the ones in the repositories, to downgrade them. I'm sure the way apt checks for updates is by checking if the installed version is less than the current version in repositories - how does it do that? I wish to do this to perform a kind of "undo" operation - I had naively enabled some karmic sources (by adding a file in the sources.list.d directory) in my jaunty to try to pull the new virtualbox via apt-pinning.... virtualbox would have broken packages, so update it did not, but then some libraries did from karmic, and now everything is in perfect condition, except that my evince is whacked! I like evince... I am sticking around with xpdf now... I will NOT use acroread, and using anything other is just accepting defeat, which I don't easily because I am stubborn.

Any ideas? Shouldn't I be able to merely grab some from apt and make a small change to achieve this? (or maybe I am playing with fire here :))

If that is dangerous, I have another idea - to be able to get the synaptic window in text format, run a small C++ code, and list all packages where the installed version does not agree with the latest version - what file do I need to access to have the package information in it?

EDIT: I should mention that the karmic sources are gone - the updates that were performed with karmic were not major - only a few libraries. My jaunty is up-to-date. I am also assuming that if the installed version > the version in repositories, apt does not bother with the package.

---

### Post by manzdagratiano on 2010-02-11
Well... in the meantime I manually went over all the package versions in synaptic - just some development headers were from kernel 2.6.31 instead of 2.6.28 which I reinstalled with a bunch of other stuff... no luck with evince, but I think the need for the script has been eliminated thanks to an hour of brute force

---

