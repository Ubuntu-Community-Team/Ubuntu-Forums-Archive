---
title: "Kernel regression: what options can I try to build a kernel that works?"
date: 2010-03-31
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Irihapeti on 2010-03-31
I can't boot Lucid on my desktop machine unless I use the Karmic kernel. If I use any later Ubuntu kernel, boot gets as far as mounting partitions and swap, and then freezes totally, as in, the keyboard doesn't work. If I boot to busybox, I can use the keyboard, but as soon as I exit it, lockup ensues. 

I have a bug report open (499399). Maybe it will get fixed in time for release, maybe it won't. Either way, there's not much I can do about it.

I don't like being dependent on something that may or may not be fixed, so I'm looking at plan B: compile a kernel that will work. I have tried compiling a 2.6.33.1 kernel using the karmic config file - big thanks to [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158) - and nothing much has changed, except that on lockup I get a coloured screen. Just for fun, I installed the kernel on my ancient Toshiba Satellite A10 laptop and it does seem to work properly.

I can get other distros that contain the 2.6.32 kernel to boot on this machine. That suggests to me that it can be made to work. I think that the problem is a combination of the later kernel, my hardware and the Ubuntu configuration. I'm noticing that other people with similar hardware are having problems that are similar but not identical (e.g. bug 518623). There's some suspicion that the graphics chip may be the culprit.

Output of lspci is attached as an archive. (It exceeds the size limit for txt files on this forum, unfortunately.)

So, the question is, what could I change in the configuration? Can one take the config file from another distro that's working on this machine, for instance? What other ideas do the knowledgeable folks have?

---

