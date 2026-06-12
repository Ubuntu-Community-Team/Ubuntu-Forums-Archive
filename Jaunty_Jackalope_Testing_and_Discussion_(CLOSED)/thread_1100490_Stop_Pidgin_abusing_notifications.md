---
title: "Stop Pidgin abusing notifications"
date: 2009-03-19
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by OliW on 2009-03-19
For some reason, under the new notification doobrey, Pidgin feels the urge to tell me about the signing-ins of every Tom, Dick and Harry that I've been unfortunate enough to befriend.

Needless to say: I don't want this! I don't care about these people that much that I need a notification! If I did want this behaviour, I'd create a pounce.

So yes. How do I stop Pidgin doing this?

---

### Post by Tich666 on 2009-03-19
+1

Sometimes when my wireless acts up I have to reconnect to the AP, which causes pidgin to lose its connection and consequently telling me that 10+ people are online right now as soon as it comes back.

I've been annoyed about this "feature" ever since it was introduced, but not bothered enough to file a complain.

I would propose to make it configurable with settings such as:
* notifications alway on (current behaviour)
* notifications on, when pidgin is hidden (contact list window not open or minimized)
* notifications off

---

### Post by TrueTom on 2009-03-19
Go to plugins and look for 'libnotify'...

(Oh, and it's not Pidgin's fault btw.)

---

### Post by go7Ul1ai on 2009-03-19
Actually, you can configure Pidgin notifications, just go onto the Pidgin plugins, go down to the notifications plugin and click configure, there you go :)

---

### Post by OliW on 2009-03-19
Silly libnotify plugin! Who thought turning that on by default was a good idea? *grumbles*

---

### Post by TrueTom on 2009-03-19
> **OliW said:**
> Silly libnotify plugin! Who thought turning that on by default was a good idea? *grumbles*

Showcasing new features is more important than usability.

---

### Post by OliW on 2009-03-19
> **TrueTom said:**
> Showcasing new features is more important than usability.

I think you can advertise new features without enforcing them on users. Especially when the method to turn it off is hidden in the depths of Pidgin's plugins.

---

### Post by MacUntu on 2009-03-19
> **OliW said:**
> is hidden in the depths of Pidgin's plugins.
Not really hidden.

---

### Post by OliW on 2009-03-19
> **MacUntu said:**
> Not really hidden.

It's not in preferences, which you'll have to argue with me for a very long time to convince me shouldn't be *the* place where you're given the option to turn them on and off.

To counter any "ohbutit'saplugin" in advance, perhaps it shouldn't be. Sound notifications are core, after all...

---

### Post by gnomeuser on 2009-03-19
> **OliW said:**
> Silly libnotify plugin! Who thought turning that on by default was a good idea? *grumbles*

I find that plugin exceedingly useful, just with a few badly picked defaults. Not that it matters now that I have killed off pidgin in favor of empathy (and.. sigh, amsn since that has webcam support for msn).

---

### Post by cl333r on 2009-03-19
> **OliW said:**
> I think you can advertise new features without enforcing them on users. Especially when the method to turn it off is hidden in the depths of Pidgin's plugins.

+1

For a normal user it is indeed hidden and the defaults are silly

---

### Post by go7Ul1ai on 2009-03-19
I wish there was a unified Notifications Preferences tool so we can configure everything Notify-osd wise all in one place.

---

### Post by int on 2009-03-19
I like a lot the notifications, and the integration with pidgin..

---

### Post by go7Ul1ai on 2009-03-19
> **int said:**
> I like a lot the notifications, and the integration with pidgin..

I agree, it's nice to see some more updates to notify-osd and the indicator applet too. And just noticed on Transmission that it supports the new notifications also :)

---

### Post by Halow on 2009-03-19
> **lee.jarratt said:**
> I wish there was a unified Notifications Preferences tool so we can configure everything Notify-osd wise all in one place.
  Yes. I think this would be loads better than finding the plugins (or not, if there aren't any!) for each and every program that does or will utilize them.

---

### Post by jastonas on 2009-03-21
But is there any way to be able to click on the person that has signed in to open a chat window? That is a bit annoying...

---

### Post by TrueTom on 2009-03-21
> **jastonas said:**
> But is there any way to be able to click on the person that has signed in to open a chat window? That is a bit annoying...

No, this is by design, because it's easier if you have to open the contact list manually...

---

### Post by jastonas on 2009-03-21
In what sense is it easier?
Easier to have to open contact list and go through the 100 contacts?

---

### Post by rudenko_ruslan on 2009-03-21
> **jastonas said:**
> In what sense is it easier?
Easier to have to open contact list and go through the 100 contacts?
Maybe that was sarcasm? :p

---

### Post by TrueTom on 2009-03-21
> **rudenko_ruslan said:**
> Maybe that was sarcasm? :p
Indeed. To make it even more clear: The design of the notification system is fundamentally broken and there is basically nowhere you can go from the current point.

---

### Post by stoffe on 2009-03-21
This is a recurring problem with all the apps that like to put functionality in plugins, even for the most basic stuff sometimes - you can't even get a 24-hour timestamp in pidgin without finding the correct plugin, no matter that a large percent of the world does NOT use the am/pm paradigm...

As for plugins such as libnotify, that many would like to configure, it could probably be solved by having these apps allowing plugins to add preferences to the regular preferences, as it's onw tab or in fitting places.

The whole everything in a plugin is fundamentally broken because it's so hard to use, though it's architecturally sound in many cases.

Otherwise, I think it works really well and the defaults fit me well. The only thing that disturbs me is that these new notifications seem to draw my attention much more, probably due to them being much more prominent on light background, and possibly also by being in the top right corner instead of bottom right where I'm used to having pidgin libnotifications. Maybe I would like to change that...

---

### Post by jastonas on 2009-03-21
What a pity... new notifications look so nice. I hope they can find a way to fix any problems.

---

### Post by techdude3177 on 2009-03-27
The only downside i find turning off this libnotify plugin is that the IM in the window list doesnt flash anymore.  And normally i dont have sound on so the only way i can tell if i get a new message is if pidgin blinks in the notification area.... which i dont always catch all the time... i feel like i am in catch 22!

---

### Post by ThrobbingBrain66 on 2009-03-27
> **techdude3177 said:**
> The only downside i find turning off this libnotify plugin is that the IM in the window list doesnt flash anymore.  And normally i dont have sound on so the only way i can tell if i get a new message is if pidgin blinks in the notification area.... which i dont always catch all the time... i feel like i am in catch 22!

You have to turn on the Message Notification plugin.  libnotify and the "blinking" windows have nothing to do with each other.

---

### Post by techdude3177 on 2009-03-27
awesome didnt see that plugin and that worked

---

