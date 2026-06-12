---
title: "asking ubuntu devs to include a kernel patch on Intrepid"
date: 2008-09-29
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eldragon on 2008-09-29
my laptop (and several other models) has some acpi bug that makes some devices conficlt with each other. unless they are forced to load on some other memory range. this bug makes linux imposible to boot from live cds, and lots of tweaks are needed in order to have ubuntu installed on them.

i was wondering if there are any proper channels to ask ubuntu kernel devs to include this fix in the upcoming intrepid release.

the bug in question is: [http://bugzilla.kernel.org/show_bug.cgi?id=9905](http://bugzilla.kernel.org/show_bug.cgi?id=9905)

and the working temp fix is: [http://bugzilla.kernel.org/attachment.cgi?id=17945&action=view](http://bugzilla.kernel.org/attachment.cgi?id=17945&action=view)

---

### Post by xubcel on 2008-09-29
Hello.  I have an unanswered acpi problem too (posted on this forum), as do other people.  I spent two weeks on the problem with no result and might go back to windows if there is no Linux solution.

[http://ubuntuforums.org/showthread.php?t=928098](http://ubuntuforums.org/showthread.php?t=928098)

---

### Post by eldragon on 2008-09-29
> **xubcel said:**
> Hello.  I have an unanswered acpi problem too (posted on this forum), as do other people.  I spent two weeks on the problem with no result and might go back to windows if there is no Linux solution.

[http://ubuntuforums.org/showthread.php?t=928098](http://ubuntuforums.org/showthread.php?t=928098)

well, ive posted in your relevant thread about a thread that managed to help me save lots of power. (doing aroun 12~13Wh) which equals to aproximatly 4 hs with a standard battery pack

---

### Post by markbuntu on 2008-09-29
If you want that fixed in the kernel, you need to go to Launchpad and file a bug or support an existing one about your problem. Complaining here will not help you as the devs do not have either the time or inclination to wade through all the threads in these forums. 

But they do look at every single bug report in Launchpad.

---

### Post by eldragon on 2008-09-29
> **markbuntu said:**
> If you want that fixed in the kernel, you need to go to Launchpad and file a bug or support an existing one about your problem. Complaining here will not help you as the devs do not have either the time or inclination to wade through all the threads in these forums. 

But they do look at every single bug report in Launchpad.

you got the message the wrong way. ive already subscribed to the launchpad bug, to the kernel bug, but want to know if it will be enough, not for my sake, i can deal with the issue as you might have already figured that out.

i know there will be a proper patch submited to the kernel when there is a proper patch, but till then, this 'quirk' is good and stable enough to be added to the ubuntu kernel.

---

### Post by markbuntu on 2008-09-30
It will get fixed. Since it is a real bug, it will probably get backported in a kernel update if it is possible to incorporate it without causing breakage. When that will happen is very difficult to say.

---

