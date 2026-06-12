---
title: "wake up is not working"
date: 2010-03-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by sartic on 2010-03-20
Toshiba notebook, can not wake up after I close it widthout shutdown.
What should I try or this is known bug in beta?

ps: finally my atheros after karmic regression (jaunty was ok)

---

### Post by sartic on 2010-03-23
still doesn't work. i have to manual initiate before closing lid.

---

### Post by TrueJournals on 2010-03-23
Are you using the fglrx ATI driver?  This seems to break sleep.

---

### Post by sartic on 2010-03-23
no i have intel vga. after last big update i am having menu (low graphic options, restart x, etc) but still can not wake up my notebook.

---

### Post by sartic on 2010-03-29
now, it works when i initiate sleep from menu.
closing lid .... same bug.

---

### Post by infestor on 2010-03-29
I have the samae problem and i use **lenovo sl500** laptop

---

### Post by infestor on 2010-03-29
Is there a fix for this bug yet?

---

### Post by fondle-em on 2010-03-29
*Seriously*.

Every time there's a big batch of updates the first thing I do is install them, reboot, and then after everything's fully loaded, I close the lid on my laptop.  Sometimes it goes into suspend and sometimes it doesn't, but the one sure thing is that X crashes when I open it again.  Now, if I put it into suspend from the menu THEN close the lid, it wakes right back up when I open the lid and X is none the worse for wear.  Since I *can* put it into suspend from the menu, it's not the end of the world - but it's a nuisance.

Dell Inspiron 1420n, Intel graphics, 64-bit Lucid.

---

### Post by enceladus47 on 2010-03-29
ok same problem here on toshiba with intel graphics, when i close the lid for a while then open it it sometimes gives me the option to run ubuntu in low graphics mode, or sometimes the computer just restarts when I open the lid

---

### Post by infestor on 2010-03-29
well i hope they are gonna fix this serious bug, otherwise rollback is inevitable

---

### Post by poodlepatrol on 2010-03-29
Mine will not awaken after a lid close, either. Sony Vaio/i86/
Thinking about fixes...
A recent post elsewhere:"Apparently changing the backlight level triggers the screen to come back on. I can probably... work around..."
Also, a mention (again) that manually suspending results in successful restart, so, suspend before closing the lid.
Would this bug likely be in X, or in Gnome? How would I tell...n00b...

---

### Post by zoomy942 on 2010-03-29
mine does nothing when i close the lid.

---

### Post by sartic on 2010-04-04
After big update it works now on my notebook. This is great. Lucid is stable now for me.

---

