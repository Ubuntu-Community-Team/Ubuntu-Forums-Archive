---
title: "Video Output Stops During Startup (Boot)"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by aajax on 2008-10-18
I just installed Ubuntu Desktop and just as the system starts booting output to the display stops.  This is accompanied by a message that says, "1: Analog Input - Cannot Display This Video Mode".  I believe this message is actually produced by my monitor.

Everything seems fine while GRUB is processing but once the kernel starts to load the output shuts off.  From observation this appears to be when Ubuntu would normally be showing a full screen graphic which contains an oscillating progress indicator.  This same computer works normally when booting the Ubuntu CD.  This behavior occurs for Ubuntu as well as Kubuntu but seems to be specific to a particular computer (i.e., I haven't seen this problem on other computers).

It looks like the last message that can be seen before output stops displaying is -

"Loading Please Wait"

Then the output resumes with the message -

"Reading files needed to boot"

After this everything seems to work satisfactorily.  I'm thinking the problem must involve something that the installer changes, for the display adapter on this computer, that is only in affect during this phase of startup.  I suppose the obvious question is, "why does the installer change something that seems to work fine on the system used for distribution and which must therefore be pretty benign?".

---

