---
title: "update manager gone from panel"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Riffer on 2009-04-10
Its that little applet that comes up when you need to do updates.  Well when I did an upgrade to jaunty it broke and now is gone.  Is there any way to rinstall it?

---

### Post by iponeverything on 2009-04-10
It only appears when you have updates waiting.

You can run it from:

System-> Administration -> Update Manager

---

### Post by Seventh Reign on 2009-04-10
I believe it has been disabled in the Jaunty Alphas and Beta.  I'm not sure if it will be re-added for the Final Release.

---

### Post by OliW on 2009-04-10
> **iponeverything said:**
> It only appears when you have updates waiting.

I did an update to jaunty and even when I have a lot of updates available, the notification doesn't show up. Slightly annoying as I tend to miss updates until I've got 300megs of them to download.

---

### Post by lonniehenry on 2009-04-10
By default the update manager indicates updates if you have not updated in 7 days.  If you wait that long it will work.  If you want to change the time that it waits to check you can change it. In terminal gconf-editor,  then apps>update-notifier and change regular_launch_interval to 1 to get the old behavior.

---

### Post by Riffer on 2009-04-10
Yep its that notification applet that I'm talking about.  And yes I do realize (and am using) the update manager in the "System" menu.

Wow lonnie that was it thanks for that.

---

### Post by Kareeser on 2009-04-10
Actually, as far as I know, Ubuntu won't have a update manager notification applet in an attempt to slim down the applications that use the notification area.

---

