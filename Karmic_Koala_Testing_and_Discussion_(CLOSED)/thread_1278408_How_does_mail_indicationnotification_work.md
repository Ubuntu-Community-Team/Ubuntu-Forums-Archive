---
title: "How does mail indication/notification work?"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by atrus on 2009-09-29
I've been unclear on this for a while. Mail checking has been integrated into the "indicator" since jaunty at least, but it's never worked for me.

What I'd like:
[LIST]
[*]Notification popups when I receive new mail (Including From/Subject/Folder)
[*]List of folders with new messages, including their counts
[*]Summary of From/Subject/Folder of new messages
[*]Ability to configure which folders I should be notified on.
[*]Ability to use a non-evolution mail client, like thunderbird. (Evolution has major performance issues with IMAP: [https://bugzilla.gnome.org/show_bug.cgi?id=336076](https://bugzilla.gnome.org/show_bug.cgi?id=336076)).
[/LIST]
What I get:
[LIST]
[*]There's always a little "envelope" icon on my panel. Clicking that icon gives me a menu item to launch evolution
[*]I don't get notifications for new messages
[*]I dont have any list of new messages, or folders with new messages, or anything like that.
[/LIST]
I've been using mail-notification for years, but I'd like to move away from it because:
[LIST]
[*]It has to be recompiled for SSL support
[*]It uses notifications only, and apparently this is frowned upon (A large number of new messages will lock up the notification system for minutes or longer while each one displays sequentially)
[/LIST]
What is the jaunty/karmic desktop experience supposed to be like with respect to a "new mail indicator"?

---

### Post by moviemaniac on 2009-09-30
I second your wishlist!

I've been using mail-notification with the evolution-plugin for years but in Karmic it's totally unusable - it crashes the notify-osd-thingy all the time.

And the built-in notification sucks. I can get it to display "x new messages" for the inbox folder but that's about all it can do :(

---

### Post by tjeremiah on 2009-09-30
they need to change the icon. Oh and mines just crashed on startup.

---

### Post by scragar on 2009-09-30
[http://brainstorm.ubuntu.com/idea/3738/](http://brainstorm.ubuntu.com/idea/3738/)

[http://brainstorm.ubuntu.com/idea/6983/](http://brainstorm.ubuntu.com/idea/6983/)

There are numerous suggestions for this functionality already, why not improve on what they suggest?

---

### Post by atrus on 2009-09-30
Good idea, I've posted:

[http://brainstorm.ubuntu.com/idea/21618/](http://brainstorm.ubuntu.com/idea/21618/)

---

