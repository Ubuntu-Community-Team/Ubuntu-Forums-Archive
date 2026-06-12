---
title: "Empathy problem"
date: 2009-10-14
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by TheNessus on 2009-10-14
this annoyed me: if I remove the empathy/evolution icon from the panel, I can't being it back. its not there as an applet to be added and there is no option for it to be back from Empathy.

---

### Post by graaant on 2009-10-14
There's an option in Empathy preference for "Use Message Indicators"
You want to untick that to use the "old" systray icon.
Having that ticked will stow Empathy under the message indicator in your tray.

---

### Post by TheNessus on 2009-10-18
> **graaant said:**
> There's an option in Empathy preference for "Use Message Indicators"
You want to untick that to use the "old" systray icon.
Having that ticked will stow Empathy under the message indicator in your tray.

I already deleted empathy and returned to pidgin, but decided re-install it to give it another go... 

Now, since I removed the applet from the gnome-panel, I don't have a way to access Empathy. it's out there somewhere in the background, but since it's not in the systray, it's inaccessible. Quite a feet.

---

### Post by tekstr1der on 2009-10-18
> **TheNessus said:**
> I already deleted empathy and returned to pidgin, but decided re-install it to give it another go... 

Now, since I removed the applet from the gnome-panel, I don't have a way to access Empathy. it's out there somewhere in the background, but since it's not in the systray, it's inaccessible. Quite a feet.

You can check out this bug report:

[https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/435329](https://bugs.launchpad.net/ubuntu/+source/empathy/+bug/435329)

I had a heck of a time with this exact issue. In comment #42 I describe how I got this working properly again.

---

### Post by TheNessus on 2009-10-18
it fixed the empathy start up GUI, but the GUI still is not accessible if you close it; no systray icon and the applet is nowhere to be seen in the add-applet menu.

---

### Post by tekstr1der on 2009-10-18
Uh-huh. Though it's counter-intuitive, you need to have "Use message indicators" checked on the Notifications tab under preferences.

Also, are you using either indicator applet or FUSA? As stated in the bug I linked, I am using neither, so my solution may only work for my use case.

---

### Post by TheNessus on 2009-10-18
ah, it worked when i started empathy again. weird. well thanks; hope Empathy lives up to its expectations.

---

