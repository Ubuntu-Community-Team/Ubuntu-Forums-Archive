---
title: "Free disk space cannot be used"
date: 2014-09-06
forum: Installation &amp; Upgrades
---

### Post by blackpearljack on 2014-09-06
I tried to dual boot windows 8.1 and ubuntu 14.04 i followed eac and every step given in the following website
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

but in the list of all partitions it shows whole space i created by shrinking c drive turns to be unused one i don't know why this is happening
so please help me

---

### Post by Vladlenin5000 on 2014-09-06
When you shrink a partiotion lefting some unused, non partitioned space, it is supposed that space to be marked exactly as unused/unallocated. So, what is your problem exactly?

---

### Post by Bashing-om on 2014-09-06
blackpearljack; Hello.

The guide looked good to me. But, a couple of things the author did not cover that is often recommended.
a) In Windows run the defrag uility twice before shrinking the partition
b) Once the Windows partition is shrunk, run Windows check disk utility at least twice. That updates the partition table and makes sure the numbers add up.

Now at this point one may proceed to install ubuntu, per the direction -> "something else" .

[INDENT][INDENT]all I have to say
[INDENT][INDENT][INDENT]should workie great, last long time[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

