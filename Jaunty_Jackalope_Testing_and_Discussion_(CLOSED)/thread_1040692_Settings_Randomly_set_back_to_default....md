---
title: "Settings Randomly set back to default..."
date: 2009-01-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by BwackNinja on 2009-01-15
Okay, so X crashed, and then my background, theme, and startup programs are now at their defaults... I have no idea how this happened. Crazy. I have no window manager running, compiz won't run, firefox-3.2 won't run (but firefox 3.0.5 will) even my panel layout is back to the original. I'd definitely say that this would be some corruption of the gconf database (assuming there is such a thing) because that's the only thing that would be linking all of this together.

Insights?

EDIT: My .fonts.conf was deleted too and my .local was regenerated. I don't think my settings are coming back... I'm trying a hard boot just so it doesn't save anything and maybe magically everything will be back to normal.

EDIT2: After a reboot I realized that it deleted all of my Pictures, Documents, Videos, and Music in the default folders as well as my Desktop. That kinda sucks, but at least I didn't have anything important there...

EDIT3: Of all the random things to delete, my emerald themes? C'mon, that doesn't even pretend to be related to anything. I'd expect at least my icons and my themes to go missing.

---

### Post by ruik on 2009-01-16
See this: [http://ubuntuforums.org/showthread.php?t=1040199](http://ubuntuforums.org/showthread.php?t=1040199)

It sounds like there are some serious issues..

---

### Post by BwackNinja on 2009-01-16
Not the same, the folders were cleared entirely of everything that was in them not files set to 0 bytes, and I'm not using ext4.

---

### Post by tghe-retford on 2009-01-16
> **BwackNinja said:**
> Not the same, the folders were cleared entirely of everything that was in them not files set to 0 bytes, and I'm not using ext4.
Sounds similar to a problem I had (hopefully your log files are still on your disk) when I was using a previous installation of Jaunty and ext3:

[http://ubuntuforums.org/showthread.php?t=1038371](http://ubuntuforums.org/showthread.php?t=1038371)

No-one else had the problem at the time so others suggested a hard drive fault.

---

### Post by BwackNinja on 2009-01-18
Crap

bad news: happened again, and took more out, mostly annoyed about my bookmarks being gone

good news: I found the trigger, it happens when I empty my trash >.<

this sucks, not just a little bit. And here I was using jaunty like it was perfectly stable xD and complaining that it wasn't breaking.

currently looking for a bug report on this.

---

