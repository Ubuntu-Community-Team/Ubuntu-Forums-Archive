---
title: "New gen notifications"
date: 2009-01-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by klim8 on 2009-01-19
Did anyone notice the new Popup Notifications entry in the Preferences menu?

Is any application already using this new notifications implementation?

---

### Post by chrisccoulson on 2009-01-19
That's just a new preferences capplet for what is still the old notification-daemon. Although it is a slightly newer version of the notification-daemon, it is still the same notification system that is in older Ubuntu versions

---

### Post by MacUntu on 2009-01-19
Still ugly, I may add.

---

### Post by andrewabc on 2009-01-19
Is there a reason why notifications is difficult to implement?

With Miranda IM, the popup/notification modules are only a couple 100kb at most (YAPP is 100kb). And they are very customizable (right/left click action, timing, actions, themes, transparency, images etc).

I'm no programmer, but I don't see how it can be difficult to create a decent popup program to work with software (or better yet make it easy for other software to use it).

How is creating notification software for linux more difficult than windows? How can that be solved?

---

### Post by cdekter on 2009-01-20
I second that - libnotify is ugly, has certain components that simply don't work, and the documentation is extremely poor (especially for python-notify). For such a basic desktop component, surely we could have something of a bit better quality and sophistication. This is one area where GNOME could learn a thing or two from KDE (check out the new notifications in KDE 4.2!)

---

### Post by Quikee on 2009-01-20
Implementing framework for notifications isn't hard, but achieving consensus over what notifications should be like is hard (for example should there be actions on notifications) and that it serves everybody's needs and visions (+ designing it in a acceptable form for everybody to use).

The idea is not only to write an application for notifications but to extend or finish the "freedesktop.org" specification for notification. The specification will then be used on many desktop environments (not only KDE and Gnome) and it should at least address their needs. 

It is good that Ubuntu will work on notifications and experiment with their usage and usability. I hope the outcome of this will be added to Gnome as a replacement for the current one and that it will push the specification completion.

---

### Post by andrewabc on 2009-01-20
> **Quikee said:**
> Implementing framework for notifications isn't hard, but achieving consensus over what notifications should be like is hard (for example should there be actions on notifications)

Make actions on notifications an option. Make everything have an option. If someone wants notification to be a certain colour, transparency, timeout, action, size, let the user be allowed to edit it. Have a nice defaults for people who don't want to mess with it, but for people who want the notification to do certain things, let them have options

---

### Post by Quikee on 2009-01-20
> **andrewabc said:**
> Make actions on notifications an option. Make everything have an option. If someone wants notification to be a certain colour, transparency, timeout, action, size, let the user be allowed to edit it. Have a nice defaults for people who don't want to mess with it, but for people who want the notification to do certain things, let them have options

This is not enough. You have to think what are the "nice" defaults because you want to achieve that most of the people won't want to change the defaults. Additionally there may be settings that just don't make sense and you don't want to include those.

To know what makes sense and what not you have to know exactly what you want to achieve with notifications and what purpose they serve, when to show a notification, do they have severity levels, which are this severity levels, what are the scenarios that a notification will be used in.

---

### Post by andrewabc on 2009-01-20
I installed alpha3 with ext4 on an old pentium 4 computer. Works great so far. I have noticed the new notification which is nice. When I start computer and it gets to desktop it says that a wireless connection has been found and click here (on popup) to connect. I click on popup and it does nothing. It does not connect to it. Maybe it means to click on network icon to connect to it? I have to click on network icon to connect and it works. But odd that it tells me to click on popup to connect but that does nothing.

I have the wireless network set to automatically connect, but for whatever reason on startup it does not connect even though it is there and showing, and able to connect when I tell it too. I think it tries to connect to a wired connection even though there is none.

EDIT: wireless connects automatically now on startup.

---

