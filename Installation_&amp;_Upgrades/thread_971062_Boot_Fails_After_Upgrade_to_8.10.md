---
title: "Boot Fails After Upgrade to 8.10"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by rfdeshon on 2008-11-04
I just upgraded to 8.10 from 8.04. My system is set up with full disk encryption using LVM. Now, suddenly, when I try to boot it fails. If I boot into single user mode, it boots fine (prompts for password, no problems at all and I can get in and use my system) however the standard boot option stops after displaying the following message and never goes any further:

```

8139cp 0000:01:01.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
8139cp 0000:01:01.0: Try the "8139too" driver instead.

```

I've already blacklisted the 8139cp driver. I've also gone so far as to move the 8139cp.ko module out of the lib directory, I have no idea why it's still trying to load. Regardless, how can I resolve this issue? Is 8139cp even causing the real problem? Why is it I can boot into single mode just fine in the same kernel?

---

### Post by rfdeshon on 2008-11-05
I really hate to do this, but I'm bumping my own post. This is a REALLY annoying issue and I haven't been able to Google up any information to help resolve it. Please... anyone... even if you just have an idea, throw it out there.

I would also like to point out that the 8.04 kernel is still installed. If I boot that kernel in normal (not single-user) mode... it boots just fine. It appears to be an issue ONLY with the current 8.10 kernel and only when booting into normal mode.

---

### Post by tarps87 on 2008-11-06
Have you tried the solution at the end of this post?
[http://ubuntuforums.org/showthread.php?t=70213](http://ubuntuforums.org/showthread.php?t=70213)
If you have the other driver installed to should set it to use it

---

### Post by rfdeshon on 2008-11-07
> **tarps87 said:**
> Have you tried the solution at the end of this post?
[http://ubuntuforums.org/showthread.php?t=70213](http://ubuntuforums.org/showthread.php?t=70213)
If you have the other driver installed to should set it to use it

Actually yes, those instructions are outdated and don't seem to work. I finally managed to figure out what the problem was though and it wasn't the driver. Apparently the new kernel doesn't like the custom grub splash screen I was using for some reason. I booted into single user mode and changed my splash screen back to the Ubuntu default, now it boots. I can't believe something so stupid would cause a complete boot hang.

---

