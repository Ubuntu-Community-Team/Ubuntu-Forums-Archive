---
title: "What's this software suspend/resume error message?"
date: 2005-10-19
forum: Installation &amp; Upgrades
---

### Post by greyhound4334 on 2005-10-19
Hi all,

Apologies if this is harmless, but I'm seeing 

```
[4294675.921000] Attempting manual resume
[4294675.930000] swsusp: Suspend partition has wrong signature?

```

in dmesg output.  I haven't done anything to try to enable Software Suspend, and I'm running a stock unbuntu 2.6.12-9-686 kernel, so I'm wondering why I'm seeing this message.  The "attempting manual resume" part seems awfully strange to me.

I just happened to notice it, and I'm battling some other shutdown/startup demons, so I got to wondering if something funky is going on.

Googling on this didn't provide a lot of userland info on what this message means or how to see what might be going on with Software Suspend.

THanks in advance,
john

---

### Post by strawman on 2005-11-08
i have the same messages in my dmesg also, and i'm thinking it might have something to do with my problem of resuming when i try to suspend to ram.  suspend worked a couple of times for me then stopped.  I'm now trying to bak track my steps because i made some changes to my /boot/grub/menu.1st file; i really want suspend to function properly. ;)

---

