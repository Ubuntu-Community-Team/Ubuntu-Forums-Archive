---
title: "Kernel Issue"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by SkonesMickLoud on 2008-05-29
Ahoy hoy!

So I ran kernelcheck the other day to upgrade my old kernel to the new 2.6.25.4 kernel.  All went smooth until the next morning when I shut down and rebooted later at work.  I saw that there were some updates to apply through update manager.  I click it and after the bar fills, I am greeted with this:

```
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package linux-image-2.6.25.4 needs to be reinstalled, but I can't find an archive for it.'
```

I get the same message (minus the first three lines) when doing anything with apt-get, aptitude, and Synaptic.

Thinking that it is the result of an installation glitch, I ran kernelcheck again.  Same message.

Manual reinstallation of the kernel from source didn't fix it either.  (Glad I stayed up late for that!)

When I load GRUB, I have 3 different kernel choices, one is the 2.6.25.4, and the other two are left over from previous upgrades.  However, booting into either of the other two doesn't remedy the problem.

I'm running Ubuntu 7.10 on a 1.4GHz Pentium M, with 1.5Gb of RAM.

Ideas?

[edit] I am thinking that this might be a false bug, so I have not reported it yet.

---

### Post by SkonesMickLoud on 2008-05-30
Bump.

Anyone even have a suggestion?

---

