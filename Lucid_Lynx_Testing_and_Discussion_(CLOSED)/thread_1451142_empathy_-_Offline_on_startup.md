---
title: "empathy - Offline on startup"
date: 2010-04-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by pabc on 2010-04-10
Am I being a bit thick here. Whenever I startup Empathy has it's status as 'Offline' until I interact with it - if I click 'chat' int he indicator a few seconds later the status changes to available.

However, if I have Empathy start from startup applications rather than as an indicator app it starts as connected without any action from me.

But of course I end up with 2 'chat's int he indicator.

I suspect I could just start it via startup apps and remove the /usr/share/applications/empathy.desktop file from /usr/share/applications/ as a work around but is there a better way?

---

### Post by Gorgapor on 2010-04-23
I'm having the same issue. How do I get empathy to log in on startup?

---

### Post by mloskot on 2010-04-23
IMHO, in spite of availability from the Me menu, Empathy is not by default launched on startup. It is not launched, unless you [specify it as one of the Sartup Applications]("http://ubuntuforums.org/showthread.php?t=1403848")

Here is related report - [Bug #549723 empathy doesn't autoconnect at startup]("https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/549723")

---

### Post by TrueJournals on 2010-04-23
I was able to remedy this by putting: ```
empathy -h
``` as a startup application.  Empathy starts and logs in when I log in, and it automatically hides itself, so there's no visual feedback.

---

