---
title: "Can't switch VT after Hardy upgrade"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by peter.marks on 2008-05-06
After upgrading to Hardy, I can't switch to a console using CTRL-ALT-F1 to F4. Strangely F5 and F6 work, but then I can't switch back to X with CTRL-ALT-F7!

Any ideas?

Whilst I'm trying to figure this out, is there any way to switch VTs from the command line?

TIA


Peter

---

### Post by peter.marks on 2008-05-07
In case anyone is interested:

This is caused by some quite bazaar decisions taken by the kernel team to make my Apple keyboard behave like it would if I was running OS X. See [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/201887)

If I was running OS X, I might find the media keys more useful than the function keys, but in linux this is simply not the case.


Peter

---

