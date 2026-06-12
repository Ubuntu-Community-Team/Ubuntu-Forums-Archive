---
title: "New notification system rocks or sucks?"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tgpraveen on 2009-02-28
Well so we have a nice taste of whats coming in ubuntu 9.04 and beyond in the notification system.

one thing everyone agrees is that it looks much better than the old one and a change was needed.
but

there are many controversial decisions like not having actions in  notifications which is leading to a huge increase in no. of popups and alerts.

One comment which sums up well what i want to say is

"Having read through the docs covering the NotifyOSD changes, I have to say I'm pretty lukewarm about it, as are a lot of others in the community, I think. From a users perspective, it seems like the end result will be an increase in the number of modal popup dialog boxes in addition to notification popups which now refuse to follow your chosen theme. I wouldn't consider this to be progress, on the whole. Having said that, the persistence (logging) and queueing stuff sound like a steps forward, although they probably won't show up until 9.10.--DuncanLock
[https://wiki.edubuntu.org/NotifyOSD/Comments](https://wiki.edubuntu.org/NotifyOSD/Comments)


U can check out the wiki of notify-osd 
[https://wiki.edubuntu.org/NotifyOSD](https://wiki.edubuntu.org/NotifyOSD)
to see how they are planning to increase many unfocused popups or alerts so that notifications with actions are avoided.
so what do u think?

---

### Post by MacUntu on 2009-02-28
I think it's a bit early for this poll as the notification system clearly isn't finished yet.

---

### Post by TrueTom on 2009-02-28
If a notification doesn't need an action it shouldn't be there in the first place. So if you start with this idea the whole new notification system is broken by design.

---

### Post by mattm591 on 2009-02-28
A notification by definition is informing you of something. Why does something that you are being informed of have to provide an action?

---

### Post by TrueTom on 2009-02-28
mattm591:

The notion of "needs an action" is used to differentiate between notifications that are necessary and those who aren't.

For example: If I boot my laptop and it connects to a wireless network, the notification "You are connected..." doesn't require an action and is therefore pointless. On the other hand if there is no known network available I have to do something and a notification is justifiable in this case (though I would still argue against that case).

---

### Post by Arlanthir on 2009-02-28
> **TrueTom said:**
> mattm591:

The notion of "needs an action" is used to differentiate between notifications that are necessary and those who aren't.

For example: If I boot my laptop and it connects to a wireless network, the notification "You are connected..." doesn't require an action and is therefore pointless. On the other hand if there is no known network available I have to do something and a notification is justifiable in this case (though I would still argue against that case).

Really? I like transmission to inform me that it's finished downloading something, and I like IM applications to inform me someone has logged in.

Rhythmbox telling me what song has started playing saves me a 5+ second intro recognizing :P

The "Device Connected" is nice, too. Finally I can make my devices do nothing on connect and still know they're properly connected :)

I'm sure there are lots of other examples! 

Whether I should be able to click on the notifications or not is debatable, but they're useful (for me!) anyway.

---

### Post by TenPlus1 on 2009-02-28
I think the new notification system is pretty good, but I would like plenty of control over it to enable/disable fades/shadows etc. so I can speed things up if I have to...

---

### Post by olskar on 2009-02-28
> **mattm591 said:**
> A notification by definition is informing you of something. Why does something that you are being informed of have to provide an action?

I strongly agree.

---

### Post by andrewabc on 2009-02-28
> **mattm591 said:**
> A notification by definition is informing you of something. Why does something that you are being informed of have to provide an action?

Actions should be optional.
People should be able to edit the transparency, text size, font, bold, italics etc. They should be able to edit how long popups stay, if the mouse is hovered over a popup then popups remain there until mouse moved away. Themes for popups should be possible. edit text colour, background colour, images and a whole range of other options.

Popups have been in Miranda IM for years and it is done very nicely because it can be edited to your liking. Plugins for Miranda can make use of the popup plugin service. If Ubuntu did the same thing (but for apps) it could work nicely.

[img]http://img516.imageshack.us/img516/6827/5011172831075popup2100.png[/img]
[img]http://img408.imageshack.us/img408/5909/mirandasetup815b.png[/img]
And if you don't like the look of that, you can completely customize it (everything possible), especially since there are two "competing" popup services. These popup plugins are less than 200kb.
Although Miranda IM is windows only app (opensource), and [YAPP plugin](http://addons.miranda-im.org/details.php?action=viewfile&id=2759) (30kb!) is opensource.

So really I don't see much of an excuse as to why the linux OS community has not developed a decent centralized standardized popup notifier that programs can work with.

---

### Post by scaine on 2009-02-28
> **andrewabc said:**
> Actions should be optional.

I don't think so.  If a notification has an "action", then it should stay on the screen until action is taken.  Then things will get very cluttered.  I hated that NM used to tell you that you're connected to your WIFI connection.  Not because it told me - I wanted to know - but because I then had to click on the damn notification to get rid of it.  Same with battery charged and battery discharging messages.

> **andrewabc said:**
> So really I don't see much of an excuse as to why the linux OS community has not developed a decent centralized standardized popup notifier that programs can work with.

You're talking about a single app - Miranda IM - and then since that *one* app does notifications the way *you* like, you blame the community for not designing a centralised notification system?  That's a leap.

No, it's not perfect right now, but will likely improve before 9.04 and 9.10 come out.

To the people who want size/font/shade/delay options - I'm laughing bitterly.  C'mon, this is gnome.  You know fine well that you'll be lucky if you get a gconf-key to even change the colour of these notifications!  I agree that it should respect DPI and theme though.

Give it time.

---

### Post by Sand &amp; Mercury on 2009-02-28
I really don't see the big deal.

---

### Post by andrewabc on 2009-02-28
> **scaine said:**
> I don't think so.  If a notification has an "action", then it should stay on the screen until action is taken.  Then things will get very cluttered.  I hated that NM used to tell you that you're connected to your WIFI connection.  Not because it told me - I wanted to know - but because I then had to click on the damn notification to get rid of it.  Same with battery charged and battery discharging messages.


I said it should be optional. And by that I mean if someone wants a specific popup to do something, then they can enable it. some people may not like actions or any options at all, but as long as there is an option for people to decide what they want then there is no problem.


> **scaine said:**
> 
You're talking about a single app - Miranda IM - and then since that *one* app does notifications the way *you* like, you blame the community for not designing a centralised notification system?  That's a leap.
Yes, miranda popups is the way I want it, because it has dozens of options that I can choose. As far as I can tell, there are currently no options at all with this current notification popups. Basics such as position, colour, font size, transparency etc are not available. It does it the way whoever sets the defaults and there is no way to change it. Everyone is stuck with the same popups whether they want them or not. Why not add a system->preferences->notifications menu item with options for everything possible?

> **scaine said:**
> To the people who want size/font/shade/delay options - I'm laughing bitterly.  C'mon, this is gnome.  You know fine well that you'll be lucky if you get a gconf-key to even change the colour of these notifications!  I agree that it should respect DPI and theme though.

Give it time.

Exactly, they should be laughed at for not coming up with a decent notification system. I'm not saying the current one is bad, but they are far behind everyone else.

---

### Post by talkingwires on 2009-02-28
> **scaine said:**
> C'mon, this is gnome.  You know fine well that you'll be lucky if you get a gconf-key to even change the colour of these notifications!Well, actually, this is something Ubuntu is doing on it's own, though it may work its way upstream.

I can the both sides of the issue, and am not sure how I feel about the new system. But not having to manually close three or four notifications piled on top of each other informing me about wireless connections and battery status is a big plus.

---

### Post by Name change on 2009-02-28
Now I haven't tried 9.04 yet (at least extensively, I did checked one of alpha builds from LiveCD). But I still believe that new notification system sucks.
Why?
Well I'm a KDE user, and KDE has its own notification system, provided that it's not so advanced as the Ubuntu (it dosen't support everything yet), but I don't want to have two systems just because one of them was developed by my distro. I want the one that is better integrated and that's KDEs.
OK for now I can't really say if it will even be implemented in it's full extent in Kubuntu 9.04, but I can see part of it when I get new updates and a little cloud (like those in comics) appears and says you have 2 updates available. I don't mind that it appears and all I would just like that it would use native KDE notification system.
I hope that it will be implemented in Jaunty or at least Karmic Koala...

That's why I voted sucks, because I have to point out that I as an KDE users don't want it and wish to have a native KDE notification system.

---

