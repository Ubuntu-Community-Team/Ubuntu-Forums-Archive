---
title: "Ubuntu's Kernel Fiasco --Shizzle!!!"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by baustiech on 2006-10-18
You know, Linux is already tough enough.

Then along comes Ubuntu, which, while otherwise quite good, creates its own major fiasco in special kernel numbering and packaging.  Years later, I'm still at a loss.

What is the bottom line here, people?

uname -a reports 2.6.12-10-386 on my current test box

This is what installed from my bone stock dapper 6.6.

I absolutely can not figure how to get the headers and/or source for this kernel --they're just not there.  So, I'm running a kernel that I can't get headers or source for, as part of the package system.  What good is that?  No good.

More broadly: In a world where single missing semicolons can halt everything, I think it's fantastically ludicrous to cavalierly changeup and toss around invented and meaningless names like dapper and breezy and 'meta-packages' called 'linux-source' and 'linux-headers'.

My vote for sanity is let's return to the exact numbering, plain old names that are clear and unconfusable, dotting all the i's, keeping us all on the same page, calling a spade a spade, etc.

The cutesy ubuntish names only seem to confound people who don't have time to fiddle-faddle with invented baloney.

Think of how mercilessly you'd slam microsoft for producing something call dapper drake or hoary hedgehog.  Admit it, the global abuse would be legendary.

Everyone on the planet understands "kernel-2.6.12-10-386."  No one, as evidenced by these very forums, can master the needless confusion brought about by the bandied, abstract nonsense names such as dapper and linux-source.

Return to the source, Luke.

My present understanding is that apt-get install kernel-source-x.y.z installs the "original" (as in, I hope, from kernel.org) source.  However, for whatever yet-to-be-explained inane reasons, ubuntu does something special and calls its stock kernels linux-x.y.z-ver-cpu

I'm still mightily confused on how stock dapper 6.6 can install 2.6.12-10-386 yet not have the headers and source for that exact same kernel available.  Am I the only one?

Is there a way to force just the kernel to update to, say, 2.6.15-23-386?

,incredulously

---

### Post by bulldog on 2006-10-18
I'm not sure if you want a reply on that.................:D

Well if there's a new kernel available you should get it automaticly.

But a ```
sudo aptitude dist-upgrade
``` can help a little.

And ```
sudo aptitude install linux-headers-2.6.12-10-386
``` won't do a thing?

And maybe you can take a look at this link,

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

