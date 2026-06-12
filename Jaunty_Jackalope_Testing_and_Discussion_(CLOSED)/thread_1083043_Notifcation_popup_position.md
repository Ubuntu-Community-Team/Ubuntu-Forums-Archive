---
title: "Notifcation popup position"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nimbrant on 2009-02-28
How do you change the position of the notification box?

I tried the option in system->Preferences->Pop-Up Notifications
but it always shows up in the top right corner.

I use dual monitors and it kind of sucks that it always shows up on the right screen when I use the left screen as my primary.

---

### Post by zekopeko on 2009-02-28
you should file a bug. the Pop-Up Notifications is for the old notifications so it won't work.

---

### Post by nimbrant on 2009-03-01
I found a bug report on launchpad regarding this issue

[https://bugs.launchpad.net/ubuntu/+source/notification-daemon/+bug/332014]("https://bugs.launchpad.net/ubuntu/+source/notification-daemon/+bug/332014")

---

### Post by nimbrant on 2009-03-31
A recent update has placed the notifications on the same screen as the panel with notifications.
This seems partially to resolve my issue.
I still see no way of changing the popup from top right to a different corner, but at least it shows up on the correct monitor.

I suppose this thread can be closed, (I don't remember how to do it).

---

### Post by tghe-retford on 2009-03-31
> **nimbrant said:**
> I still see no way of changing the popup from top right to a different corner...
Sadly there is no likely fix to allow you to change the position of the notifications in notify-osd. The position is hard-coded and it has been decided that it will remain in the top-right of the screen and only there. You'll have to compile your own version of notify-osd if you wish for it to move elsewhere.

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095)

There is another thread around here about the likelihood of a storm coming when Jaunty is released to the wider community, particularly for those whose panel and notification area is, like mine, at the bottom of the screen.

---

