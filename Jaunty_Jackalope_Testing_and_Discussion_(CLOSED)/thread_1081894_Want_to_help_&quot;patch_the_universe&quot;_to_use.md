---
title: "Want to help &quot;patch the universe&quot; to use notify-osd?"
date: 2009-02-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MacSlow on 2009-02-27
Greetings everybody!

Do you like the new notifications? Do you like hacking? Do you want to help out with the jaunty jackalope?

Here's your kickstart for adapting the software of your choice to correctly use the new notification system:
[LIST]
[*][COLOR="Blue"]**_[notification development guidelines]("https://wiki.ubuntu.com/NotificationDevelopmentGuidelines")_**[/COLOR]
[/LIST]

If that isn't enough and you want to dive even deeper into the subject, reading these here will help:
[LIST]
[*][COLOR="Blue"]**_[notification design guidelines]("https://wiki.ubuntu.com/NotificationDesignGuidelines")_**[/COLOR]
[*][COLOR="Blue"]**_[notify-osd - the spec]("https://wiki.ubuntu.com/NotifyOSD")_**[/COLOR]
[/LIST]

Happy hacking!

Best regards ...

Mirco "MacSlow" Müller

---

### Post by plun on 2009-02-28
a big *bump*.....

Lets hack :guitar:


(instead of votings)

---

### Post by BackwardsDown on 2009-02-28
This seems to be something I could do :P

I'll think I'm going to start hacking to day, altough I'm not familiar with working with big projects, or even dbus.

---

### Post by hexion on 2009-02-28
I'm using notify-send in a music application so when the song changes it shows the title and artist.
Is there any way to set the expiration time of the box so it will expire when another notify-send is launched?

I mean, leaving the default expiration time but in the event of a new message coming, it'll be prematurely expired. This would be really useful, and even more if we can set 'event types' so i.e. if applicationX uses the event type 'applicationX' its messages will only be prematurely expired by that application's events.

---

### Post by MacSlow on 2009-02-28
> **BackwardsDown said:**
> This seems to be something I could do :P

I'll think I'm going to start hacking to day, altough I'm not familiar with working with big projects, or even dbus.

You don't need to know anything about dbus to be able to make use of the notification system. What good would it be, if it was hard to use? Have a look at the supplied guideline document mentioned in the initial post of this thread. Using the notification system can be as simple as:
```
notify-send "Take note" "Using notifications is as simple as 1 2 3, thanks to libnotify and its tools." -i info 
```
Do this in a terminal or via the dialog that opens up hitting Alt-F2.

Best regards ...

Mirco "MacSlow" Müller

---

### Post by MacSlow on 2009-02-28
> **hexion said:**
> I'm using notify-send in a music application so when the song changes it shows the title and artist.
Is there any way to set the expiration time of the box so it will expire when another notify-send is launched?

No, the expire-timeout is deliberately ignored. After 5 seconds a normal (asynchronous) notification bubbles closes. notify-osd takes care to protect the user from a spam-flood of notifications this way.

> **hexion said:**
> I mean, leaving the default expiration time but in the event of a new message coming, it'll be prematurely expired. This would be really useful, and even more if we can set 'event types' so i.e. if applicationX uses the event type 'applicationX' its messages will only be prematurely expired by that application's events.

You can do that in a way. Just update the notification. So if notification 1 is being displayed you can update it with the content of notification 2. If notification 1 was already displayed and timed out (read: closed again) notify-osd will automatically create a new bubble with the contents of notification 2. Your application just pushes out what it wants to be displayed. notify-osd takes care of the rest.

Which reminds me that I have not finished the "How to update a notifiaction"-part in the notification development guidelines. *sigh*

Best regards ...

Mirco "MacSlow" Müller

---

### Post by hexion on 2009-03-01
> **MacSlow said:**
> 
You can do that in a way. Just update the notification. So if notification 1 is being displayed you can update it with the content of notification 2. If notification 1 was already displayed and timed out (read: closed again) notify-osd will automatically create a new bubble with the contents of notification 2. Your application just pushes out what it wants to be displayed. notify-osd takes care of the rest.

I believe that can only be done within an application currently, is there any plan to add such functionality to the command notify-send (i.e. to use in scripts)?

---

### Post by MacUntu on 2009-03-16
What would the proper way of using notify-osd with a perl-script be?

---

