---
title: "Boot Errors - Broken System - No operating System"
date: 2014-05-25
forum: Installation &amp; Upgrades
---

### Post by charles29 on 2014-05-25
Okay so lets do a run-down of the story.

- Windows 8, Pre-load, Automatic Repair Fail
- Buy a 2nd HD, install Ubuntu 14.04 
- Get things going fine, attempt to repair Windows 8 HD
- Boot-repair up and running, run command to delete boot so I can re-install 
- 2nd HD (still has Ubuntu 14.04 on it) now will not start with "Missing operating system error".
- Boot from USB, attempt to try and fix, no luck.

Sometimes will get a grub menu load other times "missing operating system".

So After all this I formated the 1st Hard Drive in an attempt to completely remove windows from hard drive and only run Ubuntu. 

Only way I can get Ubuntu up is to run off USB. 
I've attempted to Re-install, Un-install and then re-install.
Nothing seems to be working.

So my question is how do I get Ubuntu up and running again?

Everything I've searched/read for in forums either:
a) Isn't what I'm looking for
b) Will not help (Can't run from certain areas, requires a working OS)
c) Does not work (Things remotely similar but not exact same issues).

---

### Post by LastDino on 2014-05-25
So your goal is to have Ubuntu as the only running OS on this system?

Judging by how it originally had W8, as you might have seen in many of other threads, it is likely to be UEFI system. Have you tried tinkering with those settings in BIOS? UEFI doesn't let you install anything else than MS W8, unless you work on workaround. 

You might find this helpful.
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

However, if you're looking for dual boot, try to get that W8 recovered and working first.

---

### Post by charles29 on 2014-05-25
Hey LastDino,

Thanks for the quick reply and the links.

While that works to an extent it creates other issues (Have to start ubuntu with advanced options and choose the third option) 
Starting Ubuntu normally will cause me to have no mouse/keyboard/wireless adapter support.
Choosing first option in advanced options, the mouse/keyboard works but no wireless adapter.
Thus opening a can of worms on issues over all.

Ill mark as resolve because following the link did get this issue itself to correct. 

Thank You,
Charles

---

### Post by LastDino on 2014-05-26
You should post different thread about that, there might be someone here who can help you on those particular problems.

---

