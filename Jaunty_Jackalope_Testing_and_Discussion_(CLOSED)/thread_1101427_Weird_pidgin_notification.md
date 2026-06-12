---
title: "Weird pidgin notification"
date: 2009-03-20
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rajeev1204 on 2009-03-20
Hi

Iam getting some notification in panel for pidgin.When i click on it ,it opens the pidgin main window.

What good is that ? Its that envelope icon in the panel.

---

### Post by rudenko_ruslan on 2009-03-20
Indicator applet?

---

### Post by rajeev1204 on 2009-03-20
It looks like a mail notification .This is getting weird.

A notification in panel, indicator applet in panel and a notification display across the screen . huh.

---

### Post by andrewsomething on 2009-03-20
> **rajeev1204 said:**
> It looks like a mail notification .This is getting weird.

A notification in panel, indicator applet in panel and a notification display across the screen . huh.

It collects notifications. If you go away from the computer and receive a message, the notification will be long gone when you get back. The indicator applet will allow you to see them.

I like the indicator applet in theory. My issue is that instead of clearing up clutter, I now actually have much more. If I open pidgin I now have the indicator applet, the pidgin notification area icon, and the FUSA shows pidgin status as well....

---

### Post by andrewsomething on 2009-03-20
> **andrewsomething said:**
>  If I open pidgin I now have the indicator applet, the pidgin notification area icon, and the FUSA shows pidgin status as well....

What do you know! It's fixed now! pidgin can now minimize to the indicator applet.

pidgin (1:2.5.5-1ubuntu2) jaunty; urgency=low

  * Adding debian/patches/11_buddy_list_really_show.patch to make
    it so that the buddy list tries harder to appear. This fixes
    some issues with it not appearing. (LP: #341142)
  * Adding debian/patches/10_docklet_default_off.patch to set the
    default behavior to have no notification area icon. This fixes
    (LP: #340366)

---

