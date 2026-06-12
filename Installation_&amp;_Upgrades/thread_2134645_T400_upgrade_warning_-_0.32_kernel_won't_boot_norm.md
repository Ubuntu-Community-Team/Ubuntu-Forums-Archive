---
title: "T400 upgrade warning - 0.32 kernel won't boot normal mode"
date: 2013-04-11
forum: Installation &amp; Upgrades
---

### Post by JSchinnerer on 2013-04-11
Greetings,
Think this is appropriate forum for this - also in hardware perhaps? Not clear to this forum newbie, please advise.
Anyhow...

If you have a ThinkPad T400 laptop, BEWARE of upgrading to 0.32 kernel. Here is what happened to me.
ThinkPad T400, Type 2765-A54, 2.54GHz, 3MB RAM, running 11.10 (oneric) KUbuntu (KDE desktop, not Unity) with all upgrades to date as of yesterday (except of course not to 12.x).

Did some upgrades that included from 0.31 to 0.32 kernel.
After upgrades and restart, machine would not boot. GRUB menu comes up with standard mode 0.32 kernel as default option, I hit Enter, a few more seconds of GRUB blue screen, then screen goes dark with blinking cursor. So far, same as always.
And, after 15-30 sec. of blinking cursor, screen goes entirely dark and that is the end of it, nothing happens after several minutes' wait (previously would get disk activity and then normal boot).
Have to hold power button to do hard reset.
Repeated multiple times - same result.
Was able to boot in recovery mode with 0.32 kernel - chose continue normal boot at prompt during recovery boot process and machine booted all the way to desktop.
This was repeatable - could boot 0.32 in recovery mode but not in standard mode.
However a variety of my system settings were messed up, in particular fonts in system settings -> application appearance.

AND, suspend/resume no longer worked. Was set to "sleep" for all power profiles on close of lid. With 0.32 kernel, closing the lid had expected results, machine goes to sleep and shows moon icon illuminated solid.
Opening lid does nothing, no resume (resume worked as expected with 0.31 and earlier kernels).
Have to hold power button for hard reset.

Reverting to 0.31 kernel in GRUB menu results in boot working as previously and suspend/resume also working as previously, no issues.

Any further info on this appreciated from T400 owners. I gather there are assorted past issues with suspend/resume. That is minor however compared to machine not booting at all after upgrade!

cheers,
John S.

---

