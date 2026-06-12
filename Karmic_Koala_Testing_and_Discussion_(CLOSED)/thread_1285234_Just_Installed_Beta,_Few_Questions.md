---
title: "Just Installed Beta, Few Questions"
date: 2009-10-07
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by seanUSXIII on 2009-10-07
So I just installed the Beta last night, and so far, I am loving it! The new boot look (not sure what it is called) is awesome! Very well polished and attractive! Wireless support has improved greatly, with the new network manager! Also, Ubuntu One is awesome!

My question, though, relates to Empathy. When I used Pidgin on previous releases, I could minimize it to the "system tray" area, so I didn't take up screen space with the buddy list. I notice that Empathy does not have this feature, or I can't find it. Does Empathy support this feature? Seems like a silly feature to leave out.

All in all, though, I love the new look and feel, I'm glad they're getting away from the bright orange look, I actually use the Human theme now! :)

Thanks

---

### Post by ikisham on 2009-10-07
I perceived that Transmission is also not set to reside in the system tray anymore. I'm not in Ubuntu now but these settings usually are just a matter of ticking a checkbox under Preferences.

---

### Post by philinux on 2009-10-07
> **seanUSXIII said:**
> So I just installed the Beta last night, and so far, I am loving it! The new boot look (not sure what it is called) is awesome! Very well polished and attractive! Wireless support has improved greatly, with the new network manager! Also, Ubuntu One is awesome!

My question, though, relates to Empathy. When I used Pidgin on previous releases, I could minimize it to the "system tray" area, so I didn't take up screen space with the buddy list. I notice that Empathy does not have this feature, or I can't find it. Does Empathy support this feature? Seems like a silly feature to leave out.

All in all, though, I love the new look and feel, I'm glad they're getting away from the bright orange look, I actually use the Human theme now! :)

Thanks

Regarding Empathy,
just uncheck "Use message indicators" under Edit->Preferences->Notifications

Not intuitive is it.

---

### Post by seanUSXIII on 2009-10-07
OK, I tried that and it did solve it. Thanks guys! Although I do think that needs to be more intuitively labelled.

---

### Post by Keyper7 on 2009-10-07
> **seanUSXIII said:**
> OK, I tried that and it did solve it. Thanks guys! Although I do think that needs to be more intuitively labelled.

"Message indicators" refers to the indicator-messages applet, the little envelope you see next to the clock. This applet replaces the tray icon: when you close the Empathy window, you're not closing Empathy but minimizing it to indicator-messages. That's why the checkbox is labeled this way: its purpose is not enabling/disabling the tray icon, but enabling/disabling the usage of indicator-messages. Changing it to something like "enable tray icon" would give the impression that nothing is replacing it, which is not true.

The i-m applet is also responsible for notifying and listing all messages you receive through Empathy and other programs registered with it. Give it a shot and see if you like it. It also works with Evolution, Pidgin and Gwibber. It's part of the Ubuntu project for uncluttering the tray.

Oh, and before I forget, if you also use the Empathy tray icon for changing status, this funcionality is present in the indicator-session applet (the applet with your username next to a balloon-shaped icon).

---

