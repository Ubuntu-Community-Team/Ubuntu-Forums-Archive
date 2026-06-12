---
title: "Pan flakier than French pastry!"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by IanW on 2009-03-29
Pan just keeps dying at random intervals.

Sometimes when I ask it to fetch headers, 
sometimes when I change groups, 
sometimes when I just try to scroll the window! ](*,)

Bug needs love [#341953](https://bugs.launchpad.net/ubuntu/+source/pan/+bug/341953)

It seems from dmesg that the true culprit is libc-2.9.so, which keeps segfaulting with "error 6" (Whatever that is?)

---

