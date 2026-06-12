---
title: "Installation hangs at &quot;Switched to clocksource tsc&quot;"
date: 2014-02-25
forum: Installation &amp; Upgrades
---

### Post by Rhemat on 2014-02-25
Heya All,

  I have recently got a new laptop, and I have attempted to install a few different OSes onto it since yesterday, however, I've run into problems.  I've tried installing Linux Mint 16, and Ubuntu 13.04, and Windows 7 (not going to go into that right now), on a laptop I got from zareason.com (since I wanted to make sure that the GPU works for Linux).  However, when attempting to install the Linux distros, it hangs in a terminal, with the message [7.152041] Switched to clocksource tsc.

  Unfortunately, I've only been able to find topics/threads online relevant after installation, not before.

  The only other relevant info I can offer, is that the main board supports UEFI boot, but also has a dual boot option in BIOS (it is set to dual boot, not UEFI in BIOS).

  I'm going to try some other distros, as well as contacting support at zareason.com.  Any help I can receive here, would be most appreciated though.  Thanks in advance.

---

### Post by Rob-e on 2014-07-11
This is probably the issue you're running into. [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1308264](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1308264)

You can try adding some boot parameters like some replies suggest. Here's how to do that: [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

I was having the same issue although my computer would simply freeze at that message for about 50 seconds, then would boot normally.

Good luck!

---

