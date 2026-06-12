---
title: "spinning cursor over desktop on first login"
date: 2009-10-19
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joee92 on 2009-10-19
If I use autologin, the mouse cursor changes to its spinning "busy" state whenever it is over bare desktop or my gnome-panel.

When the cursor is in an application window, it appears normal.  If I log out and back in again, the problem goes away.  If I don't use the "log in as <me> automatically" feature, the problem never appears.

Anyone have advice for tracking this down?

---

### Post by VMC on 2009-10-19
> **joee92 said:**
> The first time I log in (autologin, FWIW) the mouse cursor changes to its spinning "busy" state whenever it is over bare desktop or my gnome-panel.

When the cursor is in an application window, it appears normal.  If I log out and back in again, the problem goes away.

Anyone have advice for tracking this down?

Using [FONT="Courier New"]top[/FONT] and see if anything changes when you move from desktop to app.

---

### Post by joee92 on 2009-10-19
> **VMC said:**
> Using [FONT="Courier New"]top[/FONT] and see if anything changes when you move from desktop to app.

I don't think there's any correlation between the spinning cursor and CPU usage.  My CPU usage is low and I can't discern any difference in "top" when I move from root window to app.

---

### Post by VMC on 2009-10-19
> **joee92 said:**
> I don't think there's any correlation between the spinning cursor and CPU usage.  My CPU usage is low and I can't discern any difference in "top" when I move from root window to app.

I didn't say anything about cpu usage. TOP may reveal what's trying to open during the "spinning" cursor.

---

### Post by joee92 on 2009-10-19
> **VMC said:**
> I didn't say anything about cpu usage. TOP may reveal what's trying to open during the "spinning" cursor.

I don't follow.  How would I use "top" to reveal what's trying to open?  Normally it shows a list of processes, sorted by CPU usage.  In that view, I see nothing remarkable (Xorg, gnome-terminal, top itself, ...) and no discernible change whether I'm hovering over the root window or an app.

I have used "pstree <user>" to see all processes I own.  I even tried killing a bunch of them, but none of the killing had any effect on the spinning cursor.

---

### Post by NCLI on 2009-10-19
I think it's probably a bug caused by xsplash not stopping properly... Does Xsplash show up in top and/or what happens if you uninstall xsplash and try booting without it?

---

### Post by joee92 on 2009-10-19
> **NCLI said:**
> Does Xsplash show up in top and/or what happens if you uninstall xsplash and try booting without it?

Xsplash does not show up on in top or even in ps.  Uninstalling it and rebooting did not fix the problem.

---

### Post by joee92 on 2009-10-19
The problem is specific to my account.  If I create a new account and set that one to auto-login, the problem does not occur.

Since I have two cases where the problem doesn't occur, I'll examine the .xsession-errors diffs among the cases...  Is there anything else I should examine to find what might be causing it?

---

