---
title: "Screen saver kicks in already after five minutes, overriding my preference"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by autark on 2010-03-10
With todays's updates, on both of my machines, I experience the following: The (Gnome) screen saver kicks in after five minutes, overriding my 30-minute preference (System -> Preferences -> Power Management -> "Put display to sleep when inactive for:")

---

### Post by zika on 2010-03-10
Try with **xset**. For example, for 30-minute preference I would suggest trying ```
xset -dpms 1800 0 0
```...

---

### Post by autark on 2010-03-11
Thanks, I'll try that if the problem persists. But I've never had to do that before, so if it persists there could be a regression somewhere.

---

### Post by zika on 2010-03-11
> **autark said:**
> Thanks, I'll try that if the problem persists. But I've never had to do that before, so if it persists there could be a regression somewhere.I have that "problem" for a while and that is why I found out that "solution". I put 0 0 0 and do not have to think about that anymore... If I want monitor to be turned off, I do it manually...

---

### Post by autark on 2010-03-11
Today, I'm still getting the screen blanked after five minutes on one machine. On the other machine, the screen saver does not kick in at all, or at least the delay is longer than one hour. On both machines, I have a Gnome preference of 30 minutes.

---

### Post by zika on 2010-03-11
> **autark said:**
> Today, I'm still getting the screen blanked after five minutes on one machine. On the other machine, the screen saver does not kick in at all, or at least the delay is longer than one hour. On both machines, I have a Gnome preference of 30 minutes.Command **xset** does not stick. It'll reset itself after reboot. You can scan current settings with **xset q**. I've put it in StartUpApplications and forgot about that... Anyhow Gnome has to communicate the same settings to X... Eventually it doesn't... Just try it and You'll forget about it...
Update: I forgot. I use simple blank screen screen-saver and I use blank in xset so You might be unsatisfied if You use some non-blank-screen screen-saver...

---

### Post by chrisccoulson on 2010-03-11
> **autark said:**
> With todays's updates, on both of my machines, I experience the following: The (Gnome) screen saver kicks in after five minutes, overriding my 30-minute preference (System -> Preferences -> Power Management -> "Put display to sleep when inactive for:")

Those preferences don't control the screensaver timeout. They only control the timeout for switching off your display

---

### Post by autark on 2010-03-11
> **chrisccoulson said:**
> Those preferences don't control the screensaver timeout. They only control the timeout for switching off your display
You're right about that! To tell the truth, I couldn't find the Screensaver section on the Preferences menu, because the menu is too long for my limited screen size! I now see that this preference indeed says 5 minutes, so I'll change that and see if that changes anything.

---

