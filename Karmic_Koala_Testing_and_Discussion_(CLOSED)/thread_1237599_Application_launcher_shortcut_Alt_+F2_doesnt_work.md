---
title: "Application launcher shortcut Alt +F2 doesnt work"
date: 2009-08-11
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by hype on 2009-08-11
Hi,
i just upgraded to karmic today and quickly realised that the Alt + F2 shortcut wouldnt start the aplication laucher pop up anymore.

 Is that a know issue? I looked around launchpad and found nothing.

---

### Post by taavikko on 2009-08-11
> **hype said:**
> Hi,
i just upgraded to karmic today and quickly realised that the Alt + F2 shortcut wouldnt start the aplication laucher pop up anymore.

 Is that a know issue? I looked around launchpad and found nothing.

Known bug, edit panel-properties, and take off the "solid-color" option.
and "killall gnome-panel"

EDIT// bug: [https://bugs.launchpad.net/bugs/398826](https://bugs.launchpad.net/bugs/398826)
EDIT// thread: [http://ubuntuforums.org/showthread.php?t=1234697](http://ubuntuforums.org/showthread.php?t=1234697)
which could have bene found by using search ;)

---

### Post by talkingwires on 2009-08-11
Similar to the change made in the last release, where ALT-CTRL-Backspace was disabled because 90% of users complained they were accidentally restarting the X server *all the time*, the developers have decided to disable the ALT-F2 key combination. Everybody knows that X has zero bugs and *never* needs to be restarted anyway, and new users migrating from Windows or OS X may be confused as to what "running" a "command" might entail, so they should just stick to clicking icons.

Also, Canonical has decided to focus on creating a new UI for its netbook variant for the second release in a row. The developers have decided to disable the ALT-Tab combination in Ubuntu, because everyone knows the only thing people do with netbooks is surf the Internet.

---

### Post by taavikko on 2009-08-11
> **talkingwires said:**
> Similar to the change made in the last release, where ALT-CTRL-Backspace was disabled because 90% of users complained they were accidentally restarting the X server *all the time*, the developers have decided to disable the ALT-F2 key combination. Everybody knows that X has zero bugs and *never* needs to be restarted anyway, and new users migrating from Windows or OS X may be confused as to what "running" a "command" might entail, so they should just stick to clicking icons.

Also, Canonical has decided to focus on creating a new UI for its netbook variant for the second release in a row. The developers have decided to disable the ALT-Tab combination in Ubuntu, because everyone knows the only thing people do with netbooks is surf the Internet.

What are you babbling about!?

---

### Post by wayne_cat on 2009-08-11
> **taavikko said:**
> What are you babbling about!?

taavikko, didn't you know that ... they will also block the keyboard keys "B" "I" "T"
and also "C" and "H" to prevent the usage of an offensive word ... but only in the
Ubuntu Netbook Remix.

---

### Post by taavikko on 2009-08-12
> **wayne_cat said:**
> taavikko, didn't you know that ... they will also block the keyboard keys "B" "I" "T"
and also "C" and "H" to prevent the usage of an offensive word ... but only in the
Ubuntu Netbook Remix.

Yeah, i knew about the ZAP being disabled in X upstream.
But the blocked keys came as surprise, been wondering why some keys don't work.
thanks wayne_cat :)
Should we file a bug?

---

### Post by Seren on 2009-08-12
> **taavikko said:**
> Yeah, i knew about the ZAP being disabled in X upstream.
But the blocked keys came as surprise, been wondering why some keys don't work.
thanks wayne_cat :)
Should we file a bug?

How are you supposed to use krunner ? Is this block for real ?

Edit : after playing a bit with the key association, ALT+F2 works again for krunner. I had to change to ALT+Space and then back to ALT+F2.

---

