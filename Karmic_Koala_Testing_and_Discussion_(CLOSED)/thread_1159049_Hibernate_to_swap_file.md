---
title: "Hibernate to swap file"
date: 2009-05-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Jimbob0i0 on 2009-05-14
These days swap files are not any slower than swap partitions but are far more flexible. Although Ubuntu will quite happily run with a swap file the hibernate support current will only work with swap partitions.

There has been work done within the kernel already to update swsusp and uswsusp to work with swap files as well as swap partitions for hibernation but an improved implementation of the whole hibernation behaviour seems to have been worked on with TuxOnIce...

[https://launchpad.net/~tuxonice](https://launchpad.net/~tuxonice)
[http://www.tuxonice.net/](http://www.tuxonice.net/)

I was wondering what the rest of the community thinks about this - I would certainly like a flexible swap file over a dedicated swap partition (and all the pains involved in adjusting partition sizes) in karmic but that would be dependant on hibernation behaviour being modified to work with a swap file instead.

---

### Post by taavikko on 2009-05-14
I'm waiting eagerly for dynamically adjusting swapfiles.

Didn't create swap partition for this test machine (it isn't actually :) )
So suspend and hibernation is not available options for me.

tried messing with dd for creating swapwile but obviously it didn't work.

But then again, it might be due to my laptop hp-dv5 and it's hw problems.

---

