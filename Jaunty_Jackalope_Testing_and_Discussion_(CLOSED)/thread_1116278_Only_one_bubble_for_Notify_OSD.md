---
title: "Only one bubble for Notify OSD?"
date: 2009-04-04
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by phaed on 2009-04-04
I thought they were going to allow many (a stack of) bubbles to pop up if need be.  I'm only getting one at a time.  It's really useful for following IRC conversations in other channels, but falls rapidly behind using just one bubble.

---

### Post by durand on 2009-04-04
Yeah, they seem to have multiple bubbles for some things like if you change the volume and check your battery level at the same time but it doesn't work if you're using the same program to send the notifications, like pidgin for example. It would also be good if you could dismiss the notifications. I read somewhere that you can use the right mouse button but that doesn't seem to work.

---

### Post by bruce89 on 2009-04-04
In other words, it has no features at all. No actions, no queuing, no widget attaching, no way to close them.

---

### Post by ktp on 2009-04-04
oh don't forget, you can't configure it or change it in anyother way, i.e themes, placement....worst because of it update notification icon is removed.

---

### Post by phaed on 2009-04-04
Well, I used KDE 4.2 for a while and liked the pop up feature in Konversation (the IRC client).  I don't have to switch to other channels unless I see the pop-up and find the conversation interesting.  I can finally do that with GNOME / XChat, but Notify OSD displays each message for a certain amount of time, and if you're in many channels, it falls rapidly behind (I quit Xchat and the messages kept coming for 20 minutes).  If I could get multiple bubbles that would be much more useful.  In Mark Shuttleworth's original demonstration, there were multiple bubbles, so I'm wondering why they took that feature away (even for a single program).

I really like the new notification system. I guess my only complaint is that it should notify even MORE than it does.

---

### Post by phaed on 2009-04-04
Also, re bruce89 and ktp, I remember when Jaunty was in alpha, there was an app that would change the location of the bubbles, but it's gone now.  Of course, it crashed after changing the location a few times, which is probably why they removed it.

My guess is that they're trying to get the basic notification system stable first.  In my estimation, it's stable.  It kept feeding me IRC comments 20 minutes after XChat was closed.  It's time to explore advanced features.  First and foremost, multiple messages from a single process, like Xchat :)

---

### Post by FuturePilot on 2009-04-04
> **phaed said:**
> Also, re bruce89 and ktp, I remember when Jaunty was in alpha, there was an app that would change the location of the bubbles, but it's gone now.  Of course, it crashed after changing the location a few times, which is probably why they removed it.

My guess is that they're trying to get the basic notification system stable first.  In my estimation, it's stable.  It kept feeding me IRC comments 20 minutes after XChat was closed.  It's time to explore advanced features.  First and foremost, multiple messages from a single process, like Xchat :)

It wasn't removed because it was crashing. It was removed because

1. The settings don't affect notify-osd, only notification-daemon
2. Because of #1 it was confusing.

(actually it's not removed, it's just hidden by default now.)

---

### Post by phaed on 2009-04-04
I searched the forums earlier for that app.  It still exists?  How can I access it?

---

### Post by ktp on 2009-04-04
> **phaed said:**
> I searched the forums earlier for that app.  It still exists?  How can I access it?

notification-properties 

or you can edit your system preference menu to show it.

Oh and they don't let you change location of the new system because they think average use would not want to do this and if you the export want to do it then you can always change and build yourself.

---

### Post by phaed on 2009-04-04
Are you sure that's right?  I can't find notification-properties by Alt+F2, terminal apt-cache search, or Synaptic.

I'm using Jaunty Beta

---

### Post by phaed on 2009-04-04
Nevermind, found it...

But it doesn't work.  Top left, bottom right, it all displays top right.

---

### Post by ktp on 2009-04-04
> **phaed said:**
> Nevermind, found it...

But it doesn't work.  Top left, bottom right, it all displays top right.

Yep, it was for the old system not the new.  

The new system is what you see, what you have, like it or not. =)

---

### Post by phaed on 2009-04-05
I like it, just wish it would display multiple bubbles from a single process.

Yeah, we're in Jaunty Beta.  That's my wish for the future.

---

### Post by uBeer on 2009-04-05
I would love it even more if instead of placing more bubbles they would update and enlarge the already displayed bubble. There's a shot of that in the video as well, that would be awesome.

I think though that that won't be a goal for Jaunty but for Koala. They will probably straighten things out through the next development cycle, which I really look forward to!

---

### Post by aamukahvi on 2009-04-05
> **uBeer said:**
> I would love it even more if instead of placing more bubbles they would update and enlarge the already displayed bubble. There's a shot of that in the video as well, that would be awesome.
That depends on the application updating the notification. You can try it for yourself:
[Notification Development Guidelines: How to use the append-hint]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines#How%20to%20use%20the%20append-hint")

---

### Post by Polygon on 2009-04-05
its not a bug, its a feature!

---

