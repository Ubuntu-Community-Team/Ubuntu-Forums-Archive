---
title: "indicator applet after empathy is removed"
date: 2009-09-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by puccaso on 2009-09-17
yea so i removed empathy cos it _SUCKS_ and im using pidgin cos it _ROCKS_

but, now i get this, "null" label in the applet, how do i remove this?

---

### Post by Joe_Bishop on 2009-09-17
they both suck, dude :D

---

### Post by puccaso on 2009-09-17
haha
ok
you got me there

but i just dont want evolution nor do i want empathy ont he indicator
how do i remove it?

---

### Post by forumache on 2009-09-18
> **puccaso said:**
> but i just dont want evolution nor do i want empathy ont he indicator
how do i remove it?

at the moment indicator shows only empathy and evolution. since you want none of them, just remove the indicator applet (right-click on it, then Remove from panel).

---

### Post by puccaso on 2009-09-18
maybe you havent updated recently
i have 
empathy
pidgin
evolution
gwibber

on my indicator list.

---

### Post by forumache on 2009-09-18
> **puccaso said:**
> maybe you havent updated recently
i have 
empathy
pidgin
evolution
gwibber

on my indicator list.

I update like crazy, every two hours ;)

But no update will put pidgin on the indicator when pidgin is not installed by default. Same with gwibber...

Now I understand what you are saying. You need indicator, but it displays Empathy and Evolution although those are not installed. Raise a bug then...

---

### Post by puccaso on 2009-09-18
dude
im telling u
it only shows whats installed..

if u install pidgin and gwibber
u will see them on the indicator.

---

### Post by joey-elijah on 2009-09-18
> **puccaso said:**
> dude
im telling u
it only shows whats installed..

if u install pidgin and gwibber
u will see them on the indicator.

Ditto - i have Gwibber, Empathy, Pidgin & Evolution all showing up in mine.

(I still don't exactly know what indicator applet does, apart from act like a "drawer" applet.)

---

### Post by Keyper7 on 2009-09-18
> **joey-elijah said:**
> (I still don't exactly know what indicator applet does, apart from act like a "drawer" applet.)

It's supposed to act like an universal messaging center. You can open/minimize/restore messaging applications through it, it notifies you of new messages and lists the unread ones.

Full spec can be seen at: [https://wiki.ubuntu.com/MessagingMenu](https://wiki.ubuntu.com/MessagingMenu).

It's main point is uncluttering the tray: it unifies and provides a single interface to things that, previously, were separate tray icons that did essentially the same thing for different programs.

It's part of the Ubuntu Ayatana Project for improving usability.

---

### Post by joey-elijah on 2009-09-18
> **Keyper7 said:**
> It's supposed to act like an universal messaging center. You can open/minimize/restore messaging applications through it, it notifies you of new messages and lists the unread ones.

Full spec can be seen at: [https://wiki.ubuntu.com/MessagingMenu](https://wiki.ubuntu.com/MessagingMenu).

It's main point is uncluttering the tray: it unifies and provides a single interface to things that, previously, were separate tray icons that did essentially the same thing for different programs.

It's part of the Ubuntu Ayatana Project for improving usability.

Wasn't it supposed to be getting all tweaked and made super useful for Karmic a la this: -

[IMG]http://img198.imageshack.us/img198/4075/messagingmenukarmic5.png[/IMG]

I know Gwibber's been kept back from being default this time around, so perhaps Karmic+1 will be social from the start instead?

---

### Post by Keyper7 on 2009-09-18
> **joey-elijah said:**
> Wasn't it supposed to be getting all tweaked and made super useful for Karmic a la this: -

(snip)

I know Gwibber's been kept back from being default this time around, so perhaps Karmic+1 will be social from the start instead?

I think too many changes happened (the switch to the new GDM which required an entire rewrite of the fast-user-switch-applet, for example) that prevented more polishing. And gwibber in Karmic is being upgraded to 2.0, which is still in development. I guess all the polishing will be made for Karmic+1.

---

### Post by puccaso on 2009-09-18
the ui for gwibber2 sucks imo

---

### Post by Keyper7 on 2009-09-18
> **puccaso said:**
> the ui for gwibber2 sucks imo

Can't say I'm a fan, either.

That's probably because Gwibber is trying very hard to be a all-in-one solution for dozens of microblogs at the same time. Since I'm only a Twitter users, I prefer the KISS approach of Gwibber 1.

---

### Post by zorkerz on 2009-09-19
I have two bones to pick with indicator-applet integration at the moment. I have pidgin and empathy installed (im happy to test empathy but it does not have the features I need). They both show up in the indicator-applet. 

However, there does not appear to be a way to minimize either pidgin or empathy to the applet. Both still minimize to their own icon in the notification area (or if you like with pidgin you can remove the indicator icon but if you close the window pidgin closes). This is redundant. 

Also I do not use evolution so it would be convenient to be able to remove it from showing up under the indicator-applet menu.

---

### Post by Keyper7 on 2009-09-19
> **zorkerz said:**
> I have two bones to pick with indicator-applet integration at the moment. I have pidgin and empathy installed (im happy to test empathy but it does not have the features I need). They both show up in the indicator-applet. 

However, there does not appear to be a way to minimize either pidgin or empathy to the applet. Both still minimize to their own icon in the notification area (or if you like with pidgin you can remove the indicator icon but if you close the window pidgin closes). This is redundant. 

Also I do not use evolution so it would be convenient to be able to remove it from showing up under the indicator-applet menu.

I have to agree. If Empathy/Pidgin can not be minimized to the indicator-applet, and the indicator-applet ONLY, the very purpose of its existence (uncluttering the tray) is defeated. I hope this is only a temporary situation until the actual Karmic release.

And yeah, I wouldn't mind configuring which apps appear in it and which do not, either.

---

### Post by jeremdow on 2009-09-21
Install pidgin-libnotify and the old Jaunty behavior will return for Pidgin - minimizes to indicator applet.

Since Pidgin is no longer default, I guess neither is this package.

---

### Post by retr0virus on 2009-09-23
After an update one or two days ago empathy no longer has its own icon but uses the indicator-applet instead.
I don't know if pidgin behaves so too.

---

### Post by rajeev1204 on 2009-09-24
Guys there is indicator applet and indicator applet sessions ,two of them which can be added to the panel.

The latter seems to behave like the FUSA applet from yore.

Try it .Lots of work being done to improve the user interaction as promised.

Not sure if any of it is useful though.

---

