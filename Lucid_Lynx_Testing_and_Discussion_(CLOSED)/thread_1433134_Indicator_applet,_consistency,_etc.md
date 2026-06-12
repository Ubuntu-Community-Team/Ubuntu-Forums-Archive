---
title: "Indicator applet, consistency, etc"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Bochonok on 2010-03-18
I don't feel that's a good idea. I noticed I'm frequently can't find the item I need (rhythmbox, message applet) instantly but need to look for the it in the indicator area.
IMO, they didn't use their brain well when designing this stuff. I see they tried to make it looking nice instead of improving usability. The mac-like appearance isn't reasonable at all, such apps (RB, Empathy, Mail client) aren't shown in Mac notification area but in dock.
So, I suppose it's hard to find certain item because of their too unified view in the indicator applet. It's sound to use indicator applet for tasks like tomboy, network connection control, power control. It's also good IMO in showing new messages/emails (I love that applet). But using it as taskbar/dock replacement is painful.
Another claim is they affirmed indicator applet brings better consistency. But the current statement of this stuff demolished  this argument. The simple example: we have one simple way to open an app window with notification area by just clicking it. But we don't have it with indicator applet. And it looks highly unlikely they will invent something that will improve the issue.
So, my proposal is to abandon indicator applet as an badly minded idea.

---

### Post by Keyper7 on 2010-03-18
> **Bochonok said:**
> I don't feel that's a good idea. I noticed I'm frequently can't find the item I need (rhythmbox, message applet) instantly but need to look for the it in the indicator area.
IMO, they didn't use their brain well when designing this stuff. I see they tried to make it looking nice instead of improving usability. The mac-like appearance isn't reasonable at all, such apps (RB, Empathy, Mail client) aren't shown in Mac notification area but in dock.
So, I suppose it's hard to find certain item because of their too unified view in the indicator applet. It's sound to use indicator applet for tasks like tomboy, network connection control, power control. It's also good IMO in showing new messages/emails (I love that applet). But using it as taskbar/dock replacement is painful.

Aren't you talking more about the icon theme than the indicators themselves here?

> **Bochonok said:**
> Another claim is they affirmed indicator applet brings better consistency. But the current statement of this stuff demolished  this argument. The simple example: we have one simple way to open an app window with notification area by just clicking it. But we don't have it with indicator applet. And it looks highly unlikely they will invent something that will improve the issue.

The "consistency" aimed for is between different indicators, not between the current notification icons and the indicators.

---

### Post by icek on 2010-03-18
What I don't like about indicators is, that there is no indication when new mail arrived, or new tweet is on my twitter page...

---

### Post by Keyper7 on 2010-03-18
> **icek said:**
> What I don't like about indicators is, that there is no indication when new mail arrived, or new tweet is on my twitter page...

You mean in Lucid? Because in Karmic I get indications for new mail, new tweets and new chat messages.

---

### Post by Bochonok on 2010-03-18
> **Keyper7 said:**
> The "consistency" aimed for is between different indicators, not between the current notification icons and the indicators.
There's no consistency between indicators menus: old right click notification area ones, without any common idea. Sadly, these menus are the only way to communicate with respective apps. So, what consistency you are talking about? Unified view? They could reach it by replacing icons. So, instead of improving consistency they broke it.

---

### Post by Bochonok on 2010-03-18
> Aren't you talking more about the icon theme than the indicators themselves here?
Yes. But I'm not a geek who loves customizing things, I always use default configurations (change it, actually, but very rarely).

---

### Post by icek on 2010-03-18
Keyper7: Yes Lucid, if there is new tweet, i get bubble notification, but  what if I miss it? There is no indication that this new tweet is there. And when new email arrive, nothing happens at all.

---

### Post by Keyper7 on 2010-03-18
> **Bochonok said:**
> There's no consistency between indicators menus: old right click notification area ones, without any common idea. Sadly, these menus are the only way to communicate with respective apps. So, what consistency you are talking about? Unified view? They could reach it by replacing icons. So, instead of improving consistency they broke it.

If you are talking about the fact that there are old styled icons and new styled ones at the same time, every replacement proposal has to go inevitably through a transition phase. Yes, it's not ideal now, but the idea is full replacement in the future.

> **Bochonok said:**
> Yes. But I'm not a geek who loves customizing things, I always use default configurations (change it, actually, but very rarely).

What I meant is that your complaints should be against the icon theme, not the indicator applet. The applet does not control the icons it uses, it simply pulls them from the theme.

> **icek said:**
> Keyper7: Yes Lucid, if there is new tweet, i get bubble notification, but  what if I miss it? There is no indication that this new tweet is there. And when new email arrive, nothing happens at all.

Yes, the current lack of indicators in Gwibber is a known bug and is being worked on. I don't know about Evolution, though, as I'm not using it under Lucid. It's supposed to work, if it doesn't you should file a bug report.

---

### Post by icek on 2010-03-18
Well, it shows me that I have new emails, but only if evolution is running... I think there should be some evolution-service that will show new emails even if evolution isn't running.

---

### Post by Keyper7 on 2010-03-18
> **icek said:**
> Well, it shows me that I have new emails, but only if evolution is running... I think there should be some evolution-service that will show new emails even if evolution isn't running.

Ah yes, indeed. The [bug is reported](https://bugs.launchpad.net/evolution-indicator/+bug/460483) but there are some major technical difficulties in fixing it, due to limitations of the plugin API.

---

### Post by puurokauha on 2010-03-23
> The simple example: we have one simple way to open an app window with notification area by just clicking it. But we don't have it with indicator applet. And it looks highly unlikely they will invent something that will improve the issue.

Now I know why rhythmbox icon shows menu and not the application when clicked. I think this behavior is horrible, in karmic I had to press once on icon to open rhythmbox from panel but now I have to click move and click again to bring up the application window. :(

---

### Post by matera.ttp on 2010-04-02
I fully agree that restoring application using single left click is very useful and there is a bug about it [https://bugs.launchpad.net/indicator-application/+bug/549910](https://bugs.launchpad.net/indicator-application/+bug/549910)
Current behaviour is terrible.
Please add your comments to this bug report.

---

