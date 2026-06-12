---
title: "Strange instalation problem"
date: 2007-05-17
forum: Installation &amp; Upgrades
---

### Post by Shaikh1 on 2007-05-17
**I started  installing Ubuntu 7.04 and it was  good,but afther  a while the Cd  stopped**

[IMG]http://www.mainardistefano.org/blog/wp-content/uploads/linux/usplash.png[/IMG]

Its like this picture. Started the loading and then stopped in the middle. I waited for 10 minuts no result!

P.S.  I use Laptop and there is microsoft logo here " Designed for Windows XP" . Can be this a problem?

Thanx in advance!

---

### Post by Ub1476 on 2007-05-17
Nop, "designed for Windows XP" is not the problem. Try to check your cd for failures (you get an option bout it in the option screen in live cd). Also try to start from safe graphics mode. Then you can see where it stops loading.

---

### Post by Shaikh1 on 2007-05-17
i tried safe graphics mode but it happens the same.
When i chose any option install,safe graphic mode or other then  Linux kernel is loading and its all fine 
afther that i  ge message " MS -BIOS bug: Timer can not connect to IO-APIC " or something like that im not sure.
Then comes the loading and it goes to the middle then stops,and Cd is not moving . Really  strange :S

---

### Post by jerrylamos on 2007-05-17
I'd suggest a couple things.

1.  On the boot options choice, push F6 and delete the word "quiet".  You'll get a ton of messages perhaps the last few of which may be worth posting.

2.  Another thing to try at boot options choice, push F6 and make these additions to the line ending in "quiet splash", deleting the word "quiet" first

......  splash noapic acpi=off

These are to turn off some of the boot code in areas that are sometimes a problem on certain hardware configurations.  Let us know how what the messages look like.

Cheers, Jerry

---

### Post by Ub1476 on 2007-05-17
Uhm, well I guess it's something about your BIOS, but really I have no clue.:( Try to make some search about the _**exact**_ error message in Google. Good luck.:)

---

### Post by jellyturtle on 2008-01-13
I had the same problem in Gusty (7.10), where the cd drive stopped, and it said there was an i/o error (twice). However, after two minutes and a bit of case-whacking (not recommended), it continued as normal through the whole installation.

---

