---
title: "Black screen after kernel update."
date: 2011-03-02
forum: Installation &amp; Upgrades
---

### Post by soulster on 2011-03-02
This morning I updated Ubuntu 10.04 (Lucid) automatically.  The update included the latest kernel update.  When I rebooted, the computer hung while shutting down (happens every once in a while).  I used the power button to manually reset.  The computer started to boot, loaded the kernel choice screen, followed option 1 for the new kernel after the timer expired, showed the "Starting..." message, and then froze with a totally blank screen (monitor went to sleep for lack of signal).

Five attempts to manually reset met the same results.  One attempt six, the system showed a "mutex_lock_slowpath" error.

Posts elsewhere suggested this was caused by hard drive problems ([see here]("http://serverfault.com/questions/238551/linux-kernel-crash-mutex-lock-slowpath-blocked-for-more-than-120-seconds-what") for example).  So I unplugged a USB External HD (500GB Maxtor OneTouchPlus) and Ubuntu booted fine (tried this one first out of 3 HDs because it was easiest to get to).

If I plug the drive in now that Ubuntu is up, it mounts fine and seems to cause no issues.  Will leave it plugged in for a while and see if any more issues occur.

---

