---
title: "Heron hangs in &quot;loading hardware drivers&quot;"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by mev on 2008-05-02
I have an EPIA 800 AG motherboard with Via C3 processor and integrated graphics.  I was previously running Ubuntu 6.06 on this machine.  Aside from having to specify "vga=791" on the boot line, everything worked fine.

I decided to reinstall this system with Ubuntu 8.04.  I got the alternate install CD because of the Via processor.  The installation process worked, again providing a vga=791 code.

However, after the system is installed and started to boot up, it reaches the point of "Loading Hardware Drivers".  The screen gets a greenish tint before it seems like something hangs or at least stops sending a signal to the monitor.  I don't seem to be able to do anything further at this point.  I was initially installing xubuntu but when that hung, I did the cli only version instead with the same hanging results.

Has anyone seen similar issues or have suggestions on how to best trouble shoot this issue other than trying to switch to another distribution?

---

### Post by steveneddy on 2008-05-31
I am also having this issue.

I am currently searching for the answer.

Any help appreciated.

---

### Post by wildyoot on 2009-12-07
Hello,

I see that problem also, on an EPIA VIA C3 system, but after my screen goes to a greenish tint it will turn blue with garbled characters until eventually (most times) it brings up the login screen (and works thereafter).

I did not specify the extra boot option.

It seems that whatever is happening during the boot up sequence will mess with the video mode after the "loading hardware drivers" message. I'm still on 8.04 LTS and haven't tried newer versions of Ubuntu yet. Would be nice to know if anyone found out what the problem/solution was. I have found in the past that a fresh reinstall of Ubuntu can improve but not completely stop it happening.

---

