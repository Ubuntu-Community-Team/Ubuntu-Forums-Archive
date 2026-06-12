---
title: "Was running 14.04 fine this morning... after update, things broke."
date: 2014-06-06
forum: Installation &amp; Upgrades
---

### Post by gfxguy on 2014-06-06
So the only odd thing about my installation is custom built NVIDIA drivers; however, I do not think the issue was from upgrading the kernel and having the drivers no longer work.

So I used my computer for a couple of hours this morning, and when I reached a stopping point in my work, I did an update (as the update manager was there on the launcher, indicating updates available).  After updating, the computer will not fully boot into Linux.

I get a 14.04 splash screen for a moment, then it goes to the login prompt, which disappears to just a blinking underline cursor in the upper left.  All of this happens at a speed which leaves me no way to do anything.

Virtual terminals are all blank.

Edited the boot options to remove "quiet splash $vt_handoff" replaced with "--verbose single," the system stops at "init: Handling started event."

I can use recovery options and start networking, get the root command line, etc., but don't know what to do to fix it.

EDIT: Additional info: my usual check for complete system lock is trying num-lock and cap-lock keys to see if the lights on the keyboard will change.  If that were the case, I might give it more time; however, when it gets to the "init: Handling started event," even caps-lock and num-lock don't work.

---

### Post by gfxguy on 2014-06-06
I am back to a working state.  I'm not sure what did it; it may have been the nvidia module, even though I wasn't using X at the time.  From the root prompt (using recover mode), I ran the nvidia install script again with the "--update" option to grab the latest version, and that seemed to fix it.

---

