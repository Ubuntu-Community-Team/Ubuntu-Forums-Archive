---
title: "Laptop brightness resetting on kubuntu?"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mindless Automata on 2009-02-18
Something with the brightness controls seems borked in kubuntu.  For example, when I play with the brightness fn keys or the slider in the battery plasmoid, the screen changes its brightness appropriately... but in 3 seconds or so, it automatically goes back to the lowest brightness setting.  The slider remains on the brightest setting, and this happens even if the power saving features are off.  

Any ideas?

---

### Post by Mindless Automata on 2009-02-18
It's apparently related to the power-saving settings because simply hitting apply after changing nothing on the Power Management section in the system settings will also put it at max brightness until it shifts back to minimum setting a few seconds later.

---

### Post by Tich666 on 2009-02-18
Sounds to me like "Dim Display when idle" is ticked and the setting gets applied despite power-saving being disabled.

Does this occur when you move the mouse or press keyboard keys too?

---

### Post by Mindless Automata on 2009-02-18
> **Tich666 said:**
> Sounds to me like "Dim Display when idle" is ticked and the setting gets applied despite power-saving being disabled.

Does this occur when you move the mouse or press keyboard keys too?

Nope.  It's unchecked--I'm on performance.  Unchecking it on the rest to see what happens does the same thing.  Yes, it happens even if I type or move the mouse--it happens within 2-3 seconds of the setting being changed.  Always reverts to dimmest.

---

### Post by Mindless Automata on 2009-02-18
Anyone have any ideas?  I'll file a bug report, but I want to investigate this as much as I can.  I don't know very much about Linux on laptops particularly mucking around with brightness.  Jaunty is otherwise running well despite this rather annoying bug.

---

### Post by Mindless Automata on 2009-02-18
It appears this is caused by the screensaver--apparently, this bug has been reintroduced:

[http://ubuntuforums.org/showthread.php?t=790543](http://ubuntuforums.org/showthread.php?t=790543)

I'll file a bug report when I have time.  Kind of a silly bug, no idea how the other guy discovered it.

---

### Post by Mindless Automata on 2009-02-19
Hmm..  Some apps also reset the brightness.  Examples include Neverball, VLC, and Dragon Player.

---

