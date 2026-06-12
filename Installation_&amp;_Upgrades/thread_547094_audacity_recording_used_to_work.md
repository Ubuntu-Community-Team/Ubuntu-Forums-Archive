---
title: "audacity recording used to work"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by drdont on 2007-09-09
Audacity used to work, first under 6.10 when I converted a lot of records to CDs and probably about 6 weeks ago with 7.04 when I tried a new set-up to do the same.

Now it doesn't.  I am not getting a button on the mixer tool bar to select the input source.  None of the suggestions I've seen to fix that seem to be relevant.  At first when I went to do some conversion from tape to CD I had a roaring sound (white noise?).  I tried the simple sound recorder which did not work but after that instead of noise audacity records complete silence.

I am thinking that an upgrade since then, maybe the kernel upgrade from about a week ago changed something.  So is there a nice listing somewhere online of all the things that were changed in this new kernel?  And for that matter is there a list of all the upgrades somewhere?

And the previous kernel 2.6.20-16 from 2007-06-10 is still sitting around in /boot.  I think that was labeled as .29 and the one from a week ago was labeled as .32.  Could I just switch those two around to see what happens?  Or are there more files that need to be switched?

Thanks in advance,

Don Tveter, [email]don@dontveter.com[/email]

---

### Post by Pumalite on 2007-09-09
At the Grub menu you should be able to choose previous kernel

---

### Post by drdont on 2007-09-10
Choosing the last kernel does not work.  It is 2.6.17-11.generic from the 6.10 release.  It just hangs during the boot process, apparently it is incompatible with the 7.04 release.

How is this for a plan:  I set up a new entry in /boot/grub/menu.lst consisting of:

vmlinux-2.6.20-16-generic (from 2007-08-30) with initrd.img-2.6.20-16-generic.bak (from 2007-06-10) instead of using initrd.img-2.6.20-16-generic (from 2007-09-02)?

But again, is there a source listing the details of the kernel changes?

Don

---

### Post by Pumalite on 2007-09-10
What happened with your latest kernel update? (yesterday, I think)

---

### Post by dabl on 2007-09-10
Check first that your mixer is functioning correctly, and doesn't have stuff muted (like the line in, or the sound device).  In other words, the problem may be the mixer, not Audacity.

If the mixer is good to go, then in Audacity make sure that you have the input device selected (usually ALSA) and showing, and don't try to run other apps that use sound (like Firefox) when you're trying to use Audacity.

:)


P.S. In Gutsy, you get Audacity 1.3.3, which is substantially better, especially under kernel 2.6.22-11, which fixes some HDA sound issues.  ;-)

---

### Post by drdont on 2007-09-11
The kernel hasn't changed for a little while, vmlinux is from 8/30 and initrd.img is from 9/2.  In late July or early August before these updates appeared recording was working.  I had just tested a new setup that used a phono preamplifier at that time.

The mixer toolbar is missing the input source selector, none of the remedies for this seems to apply, everything seems to be in order.

From alsamixer: master, line and pcm were all at 100<>100 and I turned up everything else that could be turned up.

Don Tveter, [email]don@dontveter.com[/email]

---

