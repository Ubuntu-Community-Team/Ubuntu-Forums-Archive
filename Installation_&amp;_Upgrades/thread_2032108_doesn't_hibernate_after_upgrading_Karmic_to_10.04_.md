---
title: "doesn't hibernate after upgrading Karmic to 10.04 LTS"
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by PhL38F on 2012-07-23
Hi!

I found I cannot hibernate any more on the desktop after upgrading from Karmic to Lucid.
NB:  I may be bit too much conservative but I waited until long after the alert that the version I used would not get any more support to turn to an LTS version. Keep it as long as it works! Prefering not to directly switch to 12.04, I used the 10.04 (Lucid Lynx) one.
I see a message saying that there is an issue in setting the state an usb device during that hibernation process, that involves the kernel routine *rt73usb_set_device_state*, and seems to cause moreover an  issue with swap (NB:  I have 2.8GB of ram and 7.5GB of swap!)[I].
[/I]The message looks very much alike the bug reported at [https://bugzilla.redhat.com/show_bug.cgi?id=700787](https://bugzilla.redhat.com/show_bug.cgi?id=700787) but the issue is that there is no such 2nd chance in my system as in his own (hit the key twice) and the system just hangs instead.
A guy posted a proposal for fix at [http://www.spinics.net/lists/linux-usb/msg19444.html](http://www.spinics.net/lists/linux-usb/msg19444.html) but it looks like the kernel has to be touched and this is something I would not like to do myself and expect that the Ubuntu developers take care in the context of an LTS.
Am I missing something?
Is there some (relatively) fresh kernel upgrade that I should download?
I tried to find on this forum someone having had this kind of message but could not.

Thanks in advance to any kernel expert to reply.

---

### Post by mastablasta on 2012-07-23
hibernaiton is connetced with drivers that are part of kernel.
i am not kernel expert, but i do know there are kernel PPA's that would install newer kernel.
 
i found that i have issues on hibernating in 12.04 and i also found it is a kernel bug so hopefully it will be resolved soon. still if it doesn't work for me it doesn't mean that it won't work for you. perhaps you should give 12.04 a try (maybe on a separate partition or install on USB stick/disk).
 
also your /swap size is a bit big.

---

### Post by PhL38F on 2012-07-23
What astonishes me is that this is a clear regression vs Karmic where I never faced this behaviour. I was under the impression that the non-regression verification work was the basis of the software package development work... Primum non nocere, as would the old motto go for medicine doctors.
And no, I don't want too much to switch to 12.04 so more since it seems it's not ripe yet. On the other hand, I saw a demo and it does not much look like I'm gonna like the evolution...

Thanks for the advice. BTW, I can't see why having a big swap would be an issue.

---

