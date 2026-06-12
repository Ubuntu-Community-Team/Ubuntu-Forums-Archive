---
title: "Theme Settings Not Applying"
date: 2010-04-02
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by &#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1095;&#1077; on 2010-04-02
Hello everyone, 

I recently updated to Ubuntu 10.4 and have the following problem with it:
I cannot change themes - no matter which one I choose, all that happens is that the Appearance window changes. Colours, icons, menus and buttons have the standard GNOME looks. The only item I can successfully change is windows frames. The appearance window, however,  remembers all the changes applied to it. 

What should I do? 

Please excuse me, should I be posting on the wrong forum - I have yet not had a full look around. I was also unable to find threads concerning the same issue - in case such a topic or topics already exist, please excuse me and give me a link. 

Thank you!

---

### Post by CompyTheInsane on 2010-04-02
I've had this happen a few times on my laptop. Every time, this has happened just by gnome-settings-daemon crashing during login. I had to restart that for the theme settings to come back.

Try checking to see if gnome-settings-daemon is running
by going to System > Administration > System Monitor.
Look inside the processes tab to see if gnome-settings-daemon is running.
If it isn't, run it by pressing ALT+F2 and typing
```

gnome-settings-daemon

```
Does this solve your issue?

---

### Post by &#1041;&#1098;&#1083;&#1075;&#1072;&#1088;&#1095;&#1077; on 2010-04-02
Thank you for replying. 

Unfortunately, the problem wasn't solved.
I found the process running, then restarted it. Nothing happened.

---

