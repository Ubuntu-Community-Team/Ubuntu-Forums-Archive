---
title: "Workaround for random crash bug on gdm 2.26"
date: 2009-07-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dinxter on 2009-07-07
I'll just put this here to make it easier to find for those with problems
if you have [bug #396226]("https://bugs.launchpad.net/bugs/396226"), its still in progress but can be worked around with,

           either,
- "sudo stop tty1" after logging into your gnome session
or,
- boot kernel without the splash option to stop it using usplash by either,
      * pressing e at the grub2 boot prompt and removing it manually then ctrl-x
      * or removing it from the line GRUB_CMDLINE_LINUX_DEFAULT="quiet     splash" line in file "/etc/default/grub" and then "update-grub"

[EDIT} added grub2 instructions for people having problems

---

### Post by wayne_cat on 2009-07-07
> **dinxter said:**
> I'll just put this here to make it easier to find for those with problems
if you have [bug #396226]("https://bugs.launchpad.net/bugs/396226"), its still in progress but can be worked around with,

           either,
- "sudo stop tty1" after logging into your gnome session
or,
- boot kernel without the splash option to stop it using usplash

Maybe an information that should be added to the sticky thread?

 [URL="http://ubuntuforums.org/showthread.php?t=1205763"]```
Next karmic gdm upgrade WILL BREAK your system
```[/URL]

edit: you have added it ... thanks

---

### Post by camper365 on 2009-07-09
> **wayne_cat said:**
> Maybe an information that should be added to the sticky thread?

 [URL="http://ubuntuforums.org/showthread.php?t=1205763"]```
Next karmic gdm upgrade WILL BREAK your system
```[/URL]

edit: you have added it ... thanks

Maybe this should be made sticky :P

---

### Post by taavikko on 2009-07-09
> **camper365 said:**
> Maybe this should be made sticky

There's no need, since the latest gdm upgrade has a fix(hack) for this issue.

---

