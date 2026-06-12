---
title: "HH freezes but not XP"
date: 2008-07-03
forum: Installation &amp; Upgrades
---

### Post by karrank% on 2008-07-03
Why this should happen is a mystery to me. I thought upgrading from Dapper would solve the freezes but they're worse (more frequent and less prdictable/repeatable) and can't be defeated by keystrokes, only hard reset(power button) 

Does anyone have any idea why, given the very same equip't and situations, Ubuntu should be so much less fault-tolerant than XP?

Considering "downgrading" to Dapper in the hopes of resolving this.

Or am I missing something obvious?

---

### Post by grenadier32 on 2008-07-03
When the machine freezes, can you hit control-alt-F1, 2, 3, etc. to switch to a terminal and log in? Or does the entire machine freeze up? If so, it may be just the GDM or something in the GUI causing the problem instead of the whole machine.

If you can switch to a terminal, perhaps you can hit control-alt-backspace to restart X?

---

### Post by karrank% on 2008-07-03
> **grenadier32 said:**
> When the machine freezes, can you hit control-alt-F1, 2, 3, etc. to switch to a terminal and log in? Or does the entire machine freeze up? If so, it may be just the GDM or something in the GUI causing the problem instead of the whole machine.

If you can switch to a terminal, perhaps you can hit control-alt-backspace to restart X?

Hey thanks, the entire machine freezes, no keyboard, mouse or screen response at all. I really like this OS, but my family thinks it's a  dog for this (understandably good) reason.

---

### Post by grenadier32 on 2008-07-03
Are there any logs you can see from when the crashing takes place? Like maybe in /var/log/syslog, /var/log/dmesg or /var/log/debug even from around when the crashes have occurred? Or do the log files just not have anything from those times?

You'll need root access to view them--you can do it with ```
sudo gedit [filename]
```.

---

### Post by karrank% on 2008-07-03
Thanks,I'll look into it as soon as I return. Anything I should expect to see, or rather look for, in the log files?

---

### Post by transphorm on 2008-07-03
Same thing is happening to me now. Man that's weird. I thought it was comp but xp is fine.

---

### Post by karrank% on 2008-07-03
> **transphorm said:**
> Same thing is happening to me now. Man that's weird. I thought it was comp but xp is fine.
 so do you have a plain vanilla system like ours?

---

### Post by estyles on 2008-07-03
Don't know if this will help or not, but a lot of people were reporting freeze-ups due to compiz.  Have you tried right-clicking the desktop, choosing properties, and setting visual-effects to None?  There's also a way to disable compiz completely, but I believe that disabling visual-effects resolves some problems for some people...

---

### Post by karrank% on 2008-07-03
> **estyles said:**
> Don't know if this will help or not, but a lot of people were reporting freeze-ups due to compiz.  Have you tried right-clicking the desktop, choosing properties, and setting visual-effects to None?  There's also a way to disable compiz completely, but I believe that disabling visual-effects resolves some problems for some people...
already done, before the freezes ( don't need the eye candy), but thanks anyway.

---

### Post by transphorm on 2008-07-04
I've been running hardy since release - no probs. Yesterday it started acting slow. Like pop and locking. Formatted did a clean hardy install - no updates - same thing. Only thing I can think of is that it's a hardware issue - but would XP remain unaffected? I think I'll flash my bios again.

One thing I did notice is that it seems to be the touchpad on my lappy. I noticed a lot of usb errors in the logs. I dunno just trying to help the next guy. ;)

---

### Post by grenadier32 on 2008-07-04
> **karrank% said:**
> Thanks,I'll look into it as soon as I return. Anything I should expect to see, or rather look for, in the log files?

Look for things that look like errors, or the system complaining about something. That might help you narrow down the problem if it's a hardware issue.

---

