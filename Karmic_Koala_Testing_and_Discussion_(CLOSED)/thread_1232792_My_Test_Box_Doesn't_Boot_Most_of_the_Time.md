---
title: "My Test Box Doesn't Boot Most of the Time"
date: 2009-08-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jlacroix on 2009-08-05
This really doesn't make any sense. Most of the time my box boots to a blank screen with a blinking cursor and it sits there forever. 

Here's what happens in detail. When the Kubuntu usplash shows up, the progress bar fills up to about an inch, it freezes, then about a minute later starts filling up again. After it fills up, it goes to a blank screen with a blinking cursor. At this point, nothing happens.

If I SSH into my box, it accepts the connection, and then the connection immediately freezes and I am unable to enter any commands. All of the shortcut keys I know do not work. The only way is to forcefully shut the machine off.

One in five times my machine will boot with no issues.

Anyone else have this problem?

---

### Post by budluva04 on 2009-08-05
well you should take a look at your log directory.../var/log

/var/log/dmesg
/var/log/syslog
/var/log/messages
/var/log/Xorg.0.log

start looking for Warnings or Errors you could pastebin your logs and post the links here so we could look at them also.

---

### Post by jlacroix on 2009-08-06
> **budluva04 said:**
> well you should take a look at your log directory.../var/log

/var/log/dmesg
/var/log/syslog
/var/log/messages
/var/log/Xorg.0.log

start looking for Warnings or Errors you could pastebin your logs and post the links here so we could look at them also.

I didn't really notice anything incriminating and those files are probably very huge, is there anything specific I should look for?

---

### Post by PatrickVogeli on 2009-08-06
may it be a hardware issue?

---

### Post by jlacroix on 2009-08-06
> **PatrickVogeli said:**
> may it be a hardware issue?

Nope. No problems at all in Jaunty. It happened after I upgraded to Karmic.

---

