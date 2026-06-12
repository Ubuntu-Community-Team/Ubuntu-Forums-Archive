---
title: "Getting &quot;hand-built&quot; modules to play well with update mechanism"
date: 2008-11-15
forum: Installation &amp; Upgrades
---

### Post by R3M3 on 2008-11-15
It looks like the current stock version of Intrepid doesn't support my TV tuner (grrr...), but the upstream version of the v4l-dvb drivers do. I could download and install the most recent versions of the v4l-dvb drivers from the third-party originators, but I'm concerned about how that will interact with the current (slightly older) version of the v4l-dvb drivers, and how this will affect applying future updates.

Is there an officially accepted way of building out-of-repo kernel modules so that they interact well with the current repository and future updates?

---

### Post by cariboo on 2008-11-15
If you build a module that is not part of the kernel you are using, you will have o recompile it every time a kernel is updated. I had to do the same thing with my webcam module until the driver was included in the latest kernel. During Intrepid testing, when there were no nvidia drivers, Every new kernel meant reinstalling the drivers until about 2.6.27.2 when the the latest method of compiling the driver was enabled.

Jim

---

### Post by R3M3 on 2008-11-15
Is there a good way of managing the process? That is, is there a way of making sure that temporary inconsistencies due to updates don't mess up the system? Is there a way of being automatically notified when the kernel is about to be updated, or do I just need to scrutinize everything before I hit the "update" button? Is there a way to make sure that I don't leave random old modules lying around when I recompile for a new kernel? Is there a way to tell the package management system about what I'm doing?

The other issue I'm trying to wrap my mind around is that I'm not looking at *adding* a module that isn't in kernel, I'm looking at updating a module that is *already in* the kernel package to a *newer* version which has not yet made it to the Ubuntu tree. How is that going to affect things?

---

