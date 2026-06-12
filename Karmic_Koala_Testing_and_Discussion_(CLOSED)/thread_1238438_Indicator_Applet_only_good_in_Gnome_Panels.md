---
title: "Indicator Applet only good in Gnome Panels?"
date: 2009-08-12
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by phenest on 2009-08-12
As some one who uses AWN instead of the gnome panels, will this applet replace existing notifications? The applet is a nice idea, but of no use if you don't use gnome panels. Currently it only supports Evolution, which isn't a problem for me as I use Thunderbird (which has no persistent notification at all).

---

### Post by taavikko on 2009-08-12
At this stage of indicator-applet i must say that it's useless.
It would be useful if it was able to minimize the evolution out of window list.

Or any other app that will likely to be supported by it.

As I understood it's idea is to clean system tray... (too bad that evolution doesn't use it atm, nor likely ever...)

---

### Post by phenest on 2009-08-12
What I need to know is (and I see no information on this), will this be a replacement for the existing notifications, or an alternative? If it's a replacement, I won't get any notifications at all, because I don't use gnome panels.

---

### Post by taavikko on 2009-08-12
> **phenest said:**
> What I need to know is (and I see no information on this), will this be a replacement for the existing notifications, or an alternative? If it's a replacement, I won't get any notifications at all, because I don't use gnome panels.

You mean replacement for notify-osd?
Those are two different things, notify-osd is used for notifications from apps
indicator applet is something for visible programs?

though, might be wrong

```
indicator-applet is an applet to display information from various applications consistently in the
 GNOME panel. 
```

Just removed indicator-applet and started RB, and it displayed the notifications via notify-osd.

Who can tell more from this indicator-thingy?

---

### Post by wayne_cat on 2009-08-12
Yes, it is useless at the moment ... and it floods /var/log/auth.log with useless
error messages

[https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/346513](https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/346513)

I have removed it.

---

### Post by phenest on 2009-08-12
> **taavikko said:**
> You mean replacement for notify-osd?

No. That one I simply removed and got the old style back.

I'm talking about the indicator applet in the gnome-panel. Can I just remove it, and get the old style back? Maybe currently, but will I always be able to do this?

---

### Post by zekopeko on 2009-08-12
AWN can embed gnome-panel applets. Just needs some glue to work.

---

### Post by phenest on 2009-08-12
> **zekopeko said:**
> AWN can embed gnome-panel applets. Just need some glue to work.

Are you just trying to be funny, or do you actually know of a way to do this?

---

### Post by phenest on 2009-08-12
[MessagingMenu/]("https://wiki.ubuntu.com/MessagingMenu/")

It does look as though this is to be a replacement for the existing notification method. It suggests that apps, such as Pidgin, will be hardcoded to not show a system tray icon. Now that I would have to protest against.

---

### Post by zekopeko on 2009-08-12
> **phenest said:**
> Are you just trying to be funny, or do you actually know of a way to do this?

hmmmm.... I can't find it now but I remember that when AWN was young they ported some gnome-panel applets.

---

### Post by phenest on 2009-08-12
> **zekopeko said:**
> hmmmm.... I can't find it now but I remember that when AWN was young they ported some gnome-panel applets.

Porting is a lot different to embedding.

---

### Post by zekopeko on 2009-08-12
> **phenest said:**
> Porting is a lot different to embedding.

By porting I mean they used some code "glue" to embed (ie. have applets in a more AWN like container).

EDIT: looks like some porting is needed. But I remember somebody hacking a gnome applet directly into AWN.

---

### Post by uBeer on 2009-08-12
The indicator applet certainly does not replace notify-osd, it is there to complement it. Messages (like from Pidgin and Evolution) where you might want to undertake action, are available from the applet.

Say a friend signs on: you get the notification bubble, and the indicator applet will light up. If you click it you will see a menu with an entry at the bottom with the name of your friend. If you click that you will start a conversation.

That is the way it worked (last time I checked, the last few months I have not used IM...)

---

### Post by phenest on 2009-08-13
> **uBeer said:**
> The indicator applet certainly does not replace notify-osd, it is there to complement it. Messages (like from Pidgin and Evolution) where you might want to undertake action, are available from the applet.

You haven't read the thread title have you? I know it doesn't replace notify-osd. It has nothing to do with notify-osd. It replaces the icons in the notification area (system tray), which is a problem if you're not using a gnome panel.

---

