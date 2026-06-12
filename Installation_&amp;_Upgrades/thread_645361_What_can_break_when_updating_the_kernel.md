---
title: "What can break when updating the kernel?"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by rainwalker on 2007-12-20
My dad is still way back on Dapper, and he never updates because he's afraid it will break things (he used Fedora Core 6 or something like that for a long time because he got tired of messing with broken things after updates) but I know updating has come a long way since then.
My question is, what can kernel upgrades break? I'm on an up-to-date Gutsy install, but I know that kernel updates are pretty important.
FYI, I'm asking all this under the assumption that "linux-headers-2.6.22-14", "linux-headers-2.6.22-14-generic", and "linux-image-2.6.22-14-generic" are kernel updates. Please correct me if I'm wrong.

---

### Post by kidders on 2007-12-21
Hi there,

In theory, a kernel update can break pretty much anything, because you're essentially installing an entirely new build of the core of the Linux OS.

Apple, for example, does this sort of thing all the time, but because OSX has to deal with such a small hardware set, and tends to take a "low-level OS hackers be damned" attitude, kernel updates very rarely cause any trouble. Neither of these is the case in the Linux world however, so the effect of kernel updates can often be difficult to predict. Potential gotchas include...
[LIST]
[*]Your kernel suddenly loses the ability to talk to your hard disks.
[*]Bootloader modifications or initrd generation, etc. get mishandled.
[*]An obsolete kernel feature your hardware has been relying on gets removed.
[*]The kernel developers change the way something critical is done for no reason.
[*]Closed source software (eg proprietary graphics drivers) misbehaves or stops working.[/LIST]These sorts of things only happen in a minority of cases, and 9 times out of 10, they can be circumvented by simply reverting to your previous kernel ... which is why Ubuntu won't uninstall a kernel unless you explicitly tell it to.

In my opinion, on a home PC, keeping up to speed with kernel updates is not terribly important. If you're not the sort of user who can find his way out of a botched kernel update in 3 or 4 minutes, then I would strongly recommend waiting a few weeks before installing any new kernel. Having said that, it's important not to fall too far behind ...
[LIST]
[*]Certain software may require reasonably current kernels.
[*]You may be missing out on important bugfixes or security updates.
[*]Sometimes, experimental new features get added that you might like.
[*]Ubuntu may have altered the way the kernel is configured, to improve I/O performance, or some other optimisation.[/LIST]If you're curious about the specifics of the changes between one version & the next, I would suggest looking up what they are. Documentation released by Ubuntu or kernel.org is best.

Anyhow, I hope this post doesn't come off as being too discouraging! It's important to keep your kernel *reasonably* current at all times. In the unlikely event something goes pear-shaped -- and it _is_ quite unlikely -- there are many people here willing to help. :-)

---

### Post by jingo811 on 2007-12-21
Kernel updates have made a fully functional HP printer and Canon scanner of mine to stop working one day.  I never had the time and energy to fix it.  There is usually fixes for printers but scanners don't seem to be so high priority in the Linux community.  And I've forgot how to fix certain things so the problems usually remains for each kernel upgrade I do.

So I solve it by simply going back to my Windows XP partition whenever I need to use those 2 important devices.

Also if you have yet another Linux distro along side with your Ubuntu distro then if one kernel upgrade breaks a certain distro then you still have another distro to keep you up and operational.  Giving you enough time to fix the problems at your own desired pace.

---

### Post by lvleph on 2007-12-21
The best way to test a knew version of your distributiion would be to have a test partition. This way you can install it to that partition and see what breaks. However, any of the fixes that made it work previously may need to be redone. But that could be easy, since you have done it before. However, when I moved to gutsy there was no way to get my sound to work again without compiling a kernel or waiting for the backport. Got the backport and my sound works.

---

### Post by rainwalker on 2007-12-21
I talked to someone on #ubuntu (the IRC channel) and he said that this kernel update replaces the current one, rather than providing a new one (i.e. replacing the current kernel with a "2.6.22-14" kernel rather than adding a "2.6.22-14.1 kernel") so I wouldn't be able to revert to a working kernel. Correct?

---

### Post by mneisen on 2007-12-21
Unfortunately yes. Plus, the upgrade I did this morning broke my laptop installation, it just will not boot anymore. Well, I guess I just have to find out what went wrong ... :-)

---

