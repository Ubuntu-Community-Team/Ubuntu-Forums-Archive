---
title: "possible to start awn earlier?"
date: 2009-11-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by hanlin on 2009-11-28
I'm running awn 0.4 beta, and I'm wondering if there's a way to start it up sooner in the bootup process. The issue with it is that I have my notification icons on it. However, it starts up after a lot of other programs which causes little annoyances. One of them is that pidgin starts up before awn so it doesn't minimize to the tray at start. Also, gnome-do fails to start up properly until the notification tray show up. Any ideas?

---

### Post by plun on 2009-11-28
Why do you mess up the forum with a new thread ?

[http://ubuntuforums.org/showthread.php?t=1331413](http://ubuntuforums.org/showthread.php?t=1331413)

;)

---

### Post by hanlin on 2009-11-28
Yes, I realize that thread exists. In fact, I've read every message in it. Yet I don't see anything in there that helps me.

---

### Post by Toadinator on 2009-11-28
> **hanlin said:**
> Yes, I realize that thread exists. In fact, I've read every message in it. Yet I don't see anything in there that helps me.

I think what he meant is that you should post your bug in that thread instead. Anyways, You seem to have a lot starting up every time you boot. Disabling pidgin on boot would help speed things up a LOT if I remember correctly. After everything else starts up, just open Pidgin with Gnome-Do.

---

### Post by Toadinator on 2009-11-28
Also, maybe you could try turning off Gnome-Do's visibility in the Notification Area; that might help.

---

### Post by BXCracer on 2009-11-28
Why not just start pidgin and gnome-do with a little delay ?

---

### Post by phenest on 2009-11-28
You could add an entry for AWN in the session startup, /desktop/gnome/session and add AWN as a required_component. Then uncheck auto start in AWN's preferences.

---

