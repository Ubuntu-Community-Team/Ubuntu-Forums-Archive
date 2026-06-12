---
title: "Lost Add/Remove Applications [Resolved]"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by mgaskell on 2007-01-21
Hello All,

Don't know what I did but I lost the "Add/Remove Applications" option from the Applications drop down menu. What did I do? How can I get it back?

Thanks,
Mike

---

### Post by mgaskell on 2007-01-21
BTW I'm using Edgy 6.1

---

### Post by aysiu on 2007-01-21
Paste these commands into the terminal: ```
sudo aptitude update
sudo aptitude install gnome-app-install gksu
gksudo gnome-app-install &
``` If that works, all you have to do is right-click the menu and add a new launcher with that last command (and whatever you think is the most appropriate icon).

---

### Post by mgaskell on 2007-01-21
Thank very much Aisyu! That did the trick. I'm new to this - trying to learn. Can you think of anything I did that may have caused this to disappear in the first place? I would like to be able to fix things myself.

Thanks again for the help.

Mike

---

### Post by aysiu on 2007-01-21
No. I don't know why it would have been removed, but I can also tell you this isn't the first time I've seen it happen. I've seen at least three or four other threads about this same problem. It's a mystery...

---

