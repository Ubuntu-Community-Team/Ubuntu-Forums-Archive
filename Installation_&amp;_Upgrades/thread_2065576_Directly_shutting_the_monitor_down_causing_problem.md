---
title: "Directly shutting the monitor down causing problems at resuming...."
date: 2012-10-02
forum: Installation &amp; Upgrades
---

### Post by satyamM on 2012-10-02
When I suspend the monitor by clicking on Suspend button on right top corner, then it suspends pretty FINE.

BUT when I try to suspend by directly shutting the monitor down, when certain processes are running in it, it causes problems at resuming and **REQUIRES HARD BOOT** at many times.....When I move screen up, there comes a dim light on screen, but nothing appears(black screen) and then it does nothing........This was not the problem in 10.04, but in 12.04 this is one of many problems I am facing....Somebody please help...!!


#still coursing myself for upgrading to 12.04...... :(

---

### Post by 2F4U on 2012-10-02
You should look into /var/log/pm-suspend.log, which is the dedicated log file for suspend/resume actions. Compare the content for both alternatives of suspend and see if there are differences.
My understanding would be that it shouldn't matter whether you suspend from the menu or by shutting down the lid of the laptop, but who knows?
Does this happen only when particular programs are active or if any programs are active?

---

