---
title: "Koala GUI very slow; wrong kernel?"
date: 2009-11-19
forum: Installation &amp; Upgrades
---

### Post by bigred1 on 2009-11-19
I just upgraded from 9.04 to 9.10 using the update manager.

Jaunty was fine, but in Karmic the is GUI is *very * show; all applications are almost unusable.

Maybe the update manager did not update my kernel correctly? *uname -r* tells me that the kernel version is 2.6.28-14-generic.

What can I do about this?

---

### Post by issih on 2009-11-19
Most likely you have run into this little gem:

[http://www.ubuntu.com/getubuntu/releasenotes/910#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version](http://www.ubuntu.com/getubuntu/releasenotes/910#GRUB%20menu.lst:%20install%20the%20maintainer%27s%20version%20vs.%20keep%20the%20local%20version)

If that is the case, then hopefully that link will give you enough info to fix it

---

### Post by bigred1 on 2009-11-19
By gum, you've got it.

And in fact, I [had the same problem]("http://ubuntuforums.org/showthread.php?t=1241161") when I upgraded to Jaunty earlier.

---

### Post by issih on 2009-11-19
Its a tricky one...they don't just write over a modified grub config in case the modifications were done for good reason.

Instead they ask you what you want to do...keep the old grub configuration or accept the new version.

But sometimes if you keep the old version the new kernel isn't picked up and you end up a bit screwy. If they just made it overwrite the config, you would probably be fine, but some people would not be able to boot (because they need their specific grub modifications to get the kernel to support their hardware)

Whatever they do, they'll piss someone off :s

---

### Post by bigred1 on 2009-11-19
Yes. But in any case, the behavior of the system after bootup was unacceptable-- a mysterious slowness. There should have  been  a clear warning somewhere saying that my kernel did not match my apps. 

In addition, they should find a way to upgrade the situation, perhaps by parsing and "understanding" menu.lst as an object model rather than opaque textual lines.

I configured my system for a very simple dual boot of my two harddisks; all on commodity hardware. This scenario is not so complex, but Ubuntu does not support the upgrade.

---

### Post by issih on 2009-11-19
I'm afraid that you're understanding of the complexity of these things is somewhat wrong..

Its very very very hard to make things work perfectly for everyone. You are wanting them to parse a file that supports every single possible kernel flag, in such a way that it can work out which of the flags for any given installed kernel (bearing in mind grub can support many many kernels belonging to different distros) it should be messing with. It would have to work out if it is a line it should be messing with at all, then work out which of those parameters were the ones that the user needs to keep, and which were specific workarounds for features/bugs that were only required for the previous kernel.

Just about the only computer in existence capable of that level of understanding and discrimination is the one in your head...sorry.

As for a warning of a none matching kernel...that would be quite a good idea, except for the fact that some users run non standard kernels for good reasons, and as a general rule, the applications will run regardless of kernel unless their happens to be some incompatibility (which presumably is what happened to you)...

Nonetheless, I think that a default of warning that the kernel is wrong, and expect users doing non standard things to disable it somehow might be a good idea.

---

