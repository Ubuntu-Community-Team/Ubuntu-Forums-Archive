---
title: "Interacting with notify-osd"
date: 2009-03-29
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Crushyerbones on 2009-03-29
One of the features I liked the most in the old notification system was that when i received a new message in emesene for example, I could easily click the notification and change to that window. 
Likewise, I now have to open emesene and search for someone who just went online to find him, when I previously could have just clicked the notification bubble.

Is this functionality gone forever?

---

### Post by Crushyerbones on 2009-03-29
I hate double posting, but I've been searching around for it and would like confirmation before filling a bug.

---

### Post by mc4100 on 2009-03-29
> **Crushyerbones said:**
> 
Is this functionality gone forever?
Canonical's notify-osd is, by design, non-interactive (and they seem pretty set on keeping it that way).
[More info]("https://wiki.ubuntu.com/NotifyOSD")

---

### Post by Crushyerbones on 2009-03-29
Well, no offense but I find it rather poor by design then. It's meant to replace individual applications notifying the user by themselves but it doesn't let you immediately see what's "wrong" and forces you to search for it. 

I've been trying to make old apps work with it but as time goes on I keep finding more and more reasons to go back to the old way.

---

### Post by mc4100 on 2009-03-29
> **Crushyerbones said:**
> Well, no offense but I find it rather poor by design then. It's meant to replace individual applications notifying the user by themselves but it doesn't let you immediately see what's "wrong" and forces you to search for it. 
I quite agree. But their rationale is that if something is "wrong", then a notification should not be the way to inform a user (as they should be passive); an alert box should. [Example]("https://wiki.ubuntu.com/NotifyOSD#gnome-settings-daemon")

---

### Post by castrojo on 2009-03-29
If you have a message there should be a green dot on the envelope in your panel, if you click on that it shows you a list of the people who have messaged you, then clicking on them will take you to the message.

(That's how it works with pidgin, maybe emesene isn't updated to work with it yet?)

---

### Post by olskar on 2009-03-29
> **whiprush said:**
> If you have a message there should be a green dot on the envelope in your panel, if you click on that it shows you a list of the people who have messaged you, then clicking on them will take you to the message.

(That's how it works with pidgin, maybe emesene isn't updated to work with it yet?)

Emesene updated? You got to be kidding? ;)

---

### Post by Polygon on 2009-03-29
so i guess that is why i cannot click the 'Here' when kerneloops tells me that the bug report has been submitted successfully and i can click 'here' to see it.

---

### Post by Crushyerbones on 2009-03-29
Oh I see how it works now then. I'm sorry but ever since the re-sizable message box fiasco I refuse to use pidgin. When they fixed the notification plugin for emesene I thought that was all the dev could do to make it notify-osd compatible. Thanks a lot :)

By the way, olskar: Emesene now has webcam support on svn! It's just the main repo that keeps 1.01.

---

### Post by Kareeser on 2009-03-29
I always thought the "notifications" plugin in emesene wasn't related to notify-osd, or the previous Ubuntu notifications...

Hence Jaunty's adoption of notify-osd shouldn't have affected it??

---

### Post by olskar on 2009-03-29
> **Crushyerbones said:**
> 
By the way, olskar: Emesene now has webcam support on svn! It's just the main repo that keeps 1.01.

Nice! Will try it out!

---

### Post by ktp on 2009-03-29
> **Polygon said:**
> so i guess that is why i cannot click the 'Here' when kerneloops tells me that the bug report has been submitted successfully and i can click 'here' to see it.

Hehe I have ran into similar things...which just makes the UI look bad.

---

### Post by Crushyerbones on 2009-03-29
Sorry about the notifications thing, I meant libnotify.

---

