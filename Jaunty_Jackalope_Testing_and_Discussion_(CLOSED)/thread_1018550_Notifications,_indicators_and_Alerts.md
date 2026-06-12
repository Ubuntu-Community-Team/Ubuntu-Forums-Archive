---
title: "Notifications, indicators and Alerts"
date: 2008-12-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Kosimo on 2008-12-22
Here's a very interesting article from Mark:

[http://www.markshuttleworth.com/archives/253](http://www.markshuttleworth.com/archives/253)

What do you think about it?

I would love to see this notifications on Jaunty. As now everything is a mass.

---

### Post by gnomeuser on 2008-12-22
I would love it if Mark actually practiced what he preached, all this talk of carrying a delta to have something to present for debate sounds un-open source'y to me. The correct approach would definitely be working with upstream, via FreeDesktop.org. It is not to run off an implementing a complete replacement for existing technologies then hoping to lean on everyone to gain adoption. Work with the rest of us all the way, in an open fashion, it helps you and it helps us. Additionally doing things that way means everyone gets to provide input so corner cases which might have been missed in the original design might get covered.

That being said, I look forward to a code release of this. Bonus points given if it's on freedesktop.org.

---

### Post by salsafyren on 2008-12-22
I want to see it to believe it.

Not to sound overly negative but I want to see some action not cheap words.

Can Ubuntu really deliver these notifications when they couldn't deliver the gdm face browser and sound that just works?

---

### Post by Bou on 2008-12-22
I hate it and hope it never comes to life. I love being able to open a dowloaded file from Transmission just clicking the notification button. and hey, guess what? I can also NOT click on it, how wild is that??!!

---

### Post by gnomeuser on 2008-12-22
> **salsafyren said:**
> I want to see it to believe it.

Not to sound overly negative but I want to see some action not cheap words.

Can Ubuntu really deliver these notifications when they couldn't deliver the gdm face browser and sound that just works?

It's my impression that the gdm work was actaully passed the prototyping point but it was dependant on the new gdm which was not deemed stable for the release. It needs about a months worth of work to be updated to the changes that has happened since then.

But see how this got lost because it was not done in the open, just a public git repo would have been great and everyone could have been looking at it now.

---

### Post by plun on 2008-12-22
> **Bou said:**
> I hate it and hope it never comes to life. I love being able to open a dowloaded file from Transmission just clicking the notification button. and hey, guess what? I can also NOT click on it, how wild is that??!!

It was the same discussion within this "Bazaar vs the Cathedral" blog post during UDS...

[http://blogs.gnome.org/awalton/2008/12/10/new-notifications-for-jaunty/](http://blogs.gnome.org/awalton/2008/12/10/new-notifications-for-jaunty/)

Neil J Patel can for sure do it....including _"intelligent" _notifications :)

Or if the Cathedral just doing it instead of endless "Debian discussions" about non issues.

KDE 4.2 is a surprise... :)

---

### Post by mangar on 2008-12-22
Getting information without an ability to act on it is simply noise. The system keeps telling me stuff, that according to Mark, can be safely ignored. If that's the situation, why steal the user's focus? Because it's pretty?

What's the use case?

---

### Post by gnomeuser on 2008-12-22
> **mangar said:**
> Getting information without an ability to act on it is simply noise. The system keeps telling me stuff, that according to Mark, can be safely ignored. If that's the situation, why steal the user's focus? Because it's pretty?

What's the use case?

Something like S.M.A.R.T warnings would definitely be nice to have ones attention drawn to "Hello, your harddrive is about to experience immient fail".

Aside that I would like notifications on my daily workflow, when people send me IMs, when I have updates that need to be applied, when long duration background tasks finish and so on.

---

### Post by Kosimo on 2008-12-22
> **gnomeuser said:**
> something like s.m.a.r.t warnings would definitely be nice to have ones attention drawn to "hello, your harddrive is about to experience immient fail".

Aside that i would like notifications on my daily workflow, when people send me ims, when i have updates that need to be applied, when long duration background tasks finish and so on.

+1

---

### Post by ronacc on 2008-12-22
good lord what were they spiking the punchbowl with at UDS ? a notification that allows no action, goes away by itself and doesn't matter if you miss it is absurd and should not exist in the first place , instead I propose little penguins that periodicly run across your desktop .

---

### Post by gnomeuser on 2008-12-22
> **ronacc said:**
> good lord what were they spiking the punchbowl with at UDS ? a notification that allows no action, goes away by itself and doesn't matter if you miss it is absurd and should not exist in the first place , instead I propose little penguins that periodicly run across your desktop .

I would argue that the interaction should be with the object that notifies me not the notification itself. This propose graphically shows me what calls my attention and it implements "buckets" for important interactions of non desktop applications (new mail, smart warnings, e.g.)

Also xpenguin I believe implements your proposal.

---

### Post by Bou on 2008-12-22
> **gnomeuser said:**
> I would argue that the interaction should be with the object that notifies me not the notification itself.

I thought the object that notifies you was the notification. What's the difference?

---

### Post by ronacc on 2008-12-22
> **gnomeuser said:**
> I would argue that the interaction should be with the object that notifies me not the notification itself. This propose graphically shows me what calls my attention and it implements "buckets" for important interactions of non desktop applications (new mail, smart warnings, e.g.)

Also xpenguin I believe implements your proposal.

xpenguin was what I was thinking about when I ( tongue in cheek ) proposed the "little penguins" and they are just as useful as a notification that comes and goes while you are "out getting coffee" (marks example) actualy more useful since they are mildy amusing rather than just another annoyance.

---

### Post by gnomeuser on 2008-12-22
> **Bou said:**
> I thought the object that notifies you was the notification. What's the difference?

Typically a notifcation would be something like:
Empathy registers that your buddy David comes online and issues a notification to catch your attention. You still want to actually chat with David through empathy, not the notification.

Notifications are not meant to enable interaction, you could do this but then the most interesting thing would not be to allow closing or links but to embed some application data there. Say a pop up for a buddy coming online might have an input line for starting the chat, an icon for calling him e.g. 

That however brings bad unfunny memories of bonobo and I think everyone should still have a reason to live so let's avoid this.

---

### Post by Bou on 2008-12-22
> **gnomeuser said:**
> You still want to actually chat with David through empathy, not the notification.

Actually I just want to chat with David, or I don't. I do NOT care about the tool.

-If I do, I want to do it with the least possible hassle (that is, number of clicks and time spent). Clicking the notification button to open an (Empathy) chat window is handier and faster than opening the buddy list, browsing my friends for Dave and double-click the contact, then close the list.

-If I don't I can safely ignore the notification, so what's the point?

---

### Post by mangar on 2008-12-22
Yeah, but not only my friend David, but also my colleague Matt, my aunt Sarah, my cousin Billie and that annoying prick Jimmy I was trying to avoid for the last decade.

In short, it's just a way for the system to show it's working, and seems to serve nothing but to overwhelm the user with junk.

Take for example the S.M.A.R.T hdd notification - your hdd is about to melt, but you were at the kitchen making coffee. Now what? Lets assume you where at that very moment in front of the computer - you get a notification: " DANGER! DANGER! your hdd is about to melt! Log out of every application, save your work, and press system->logout->poweroff, than call a technician!" Wouldn't you want the machine to take care of the whatever it can, instead of popping out, telling you something you may or may not understand (not you specifically, but a random end user), and than going away for good, without giving you an option to do anything about it?

It's a lame idea, unless Mark wasn't too clear as to what he actually meant.

---

### Post by salsafyren on 2008-12-22
Actually, notification bubbles are a lame idea. They come from Windows XP and a lot of people hate them for a good reason.

Only notify the user if something has failed. This would decrease the number of notifications to zero (updates ready, rhythmbox music changes) and the user would only need to act on important ones - eg. no internet connection etc.

Why overload the user with information he doesn't need? Keep it simple, stupid.

I find this is a grand failure stemming from lack of leadership in the Gnome camp.

---

### Post by plun on 2008-12-22
This is a "intelligent" notification for me including interaction

[IMG]http://www.ubuntu-pics.de/bild/7512/gpk_updates_warning_4U81RI.png[/IMG]

But...we must start somewhere, I can live with just eye-candy...:)

EDIT  All rights to the PackageKit project
[http://www.packagekit.org/pk-screenshots.html](http://www.packagekit.org/pk-screenshots.html)

---

### Post by mangar on 2008-12-22
I think that several things need to be done about notifications:

1. Use the notification tray for notifications only, and if the user wants to handle the notification, let him, otherwise, let him be. 

2. Use the application icons/ bar whatever to show status information. Stop abusing the notification tray for unrelated stuff (like IM status, background processes, etc). Both Apple and MS (in 7) figured that up.
Example: filer transfer is already a window, with accompanying taskbar entry. Why not show a low contrast "Done" the the entry when the transfer is done? why not change the taskbar icon for pidgin according to connection status?
--Give the programs control over their taskbar entry.

3. If something cannot be acted upon, don't bother the user with it. What's the point?

---

### Post by eNry92 on 2008-12-23
it's only a mockup or it's present in the alpha version??

---

### Post by gnomeuser on 2008-12-23
> **eNry92 said:**
> it's only a mockup or it's present in the alpha version??

A mock up however work is being done by Ted Gould and Mathew Paul Thomas, preliminary work could be ready for the Jaunty release (KDE folks have to wait a bit longer as a suitable KDE developer has yet to be hired for the desktop experience team).

[Ars Technica has an depth article on the project](http://arstechnica.com/guides/other/canonical-linux-notification-system.ars)

---

### Post by Mr. Picklesworth on 2008-12-23
I like the idea in the concept video of handling volume control notification with the same system. I also suddenly thought that we should scrap the notification area stuff entirely and have its contents handled by libnotify alone. It would simplify things and COMPLETELY enforce the eradication of "iconified" applications.

For things like IM programs, we can have the window list display individual applications via small icons, grouped with the windows they have created. (Then those applications could provide their own mouse handlers and menu items in a way similar to our existing "notification" icons).

Such work would make the desktop environment delightfully understandable, organized and productive!
This notification change sounds crazy at first, but it is really a push in the right direction.

(And if Ted / Mathew are as enamoured by that nice concept video as I am, it'll look pretty, too!).

---

### Post by hanzomon4 on 2008-12-24
In OS X Growl does the same thing but allows interaction. Not allowing interaction is a mistake. With Growl say I see that X_user has come online if I click on the popup it opens a chat with that user. No buttons, out of the way if don't need it but not useless if I do.

---

### Post by mer on 2008-12-25
Ok, so a few words in defense of this move. Consider the difference between receiving a pidgin IM notification with libnotify versus this new system. With libnotify, an ugly box appears in the lower right corner of the screen, blocking whatever is there. It's intentionally hard to ignore, and pretty distracting. It has a small button in it allowing you to bring up the window and respond to the message *but* you only have a limited amount of time to press it. If you aren't fast enough, the notification goes away, and you have to redirect your cursor to the window list or the notification area. Under the new system, a pretty and intentionally unobtrusive box appears in the upper right- next to the notification area. If you wish to respond, you will always click on the pidgin notification icon, whether you missed the time frame or not. This removes all the rush and frustration from the experience. The new system doesn't lose interactivity, it just separates it from the time constraints of a notification. Anyway, I don't expect to change many minds, but hopefully we can have a nice discussion here.

---

### Post by Jay_Bee on 2008-12-26
I love that it takes away the obligation to read (and act on) the notification... it makes them safe to ignore and concentrate on the work.
Now I always need to stop what I'm doing to read the notification because it could be something important or not.
In the new system important things don't disappear in some short time, and unimportant (or unessential) things can be ignored because you know you can't act on them so you don't need to inspect the bubble reading it and making a decision to act...
On the other hand, in the current system, some notifications with actions are very useful and the action is quick to access (and also can be ignored).
Example is the Banshee's "skip this song" button on the notification which I'm using very often.
I understand the argument for and against actions on notifications, it is a double bladed sword but it will be a fun experiment to experience, I can't wait to get my hands on it :)

---

### Post by salsafyren on 2009-01-04
After thinking about this and hearing Shuttleworth discuss the plans on Youtube ([http://www.youtube.com/watch?v=DqsYje05JLs](http://www.youtube.com/watch?v=DqsYje05JLs)) I think this is a great opportunity to restart the interest in notifications.

Developers have added notifications for a long time without having any guidelines and so we get spammed frequently on the desktop. This is a chance to remedy the situation.

---

### Post by Mr. Picklesworth on 2009-01-04
I do worry what this will do to the GNOME Screensaver "leave a message" function. This needs functionality for long term notifications (messages), maybe drawn on the desktop, only *above* everything for a brief period of time.

That, or maybe there should be a completely different system for Messages of the type Screensaver leaves.

---

### Post by flyingstar16 on 2009-02-10
I just can't understand why Mark has told us about this, but didn't give us the opportunity to test it :(

---

### Post by olskar on 2009-02-10
> **flyingstar16 said:**
> I just can't understand why Mark has told us about this, but didn't give us the opportunity to test it :(

Perhaps because there never was anything to test, it was just a mockup (as usual with cool features) :(

---

### Post by Jay_Bee on 2009-02-10
I suspect that is going to change in the next week or two, people are working on it :)

---

### Post by Kosimo on 2009-02-10
> **flyingstar16 said:**
> I just can't understand why Mark has told us about this, but didn't give us the opportunity to test it :(

I suppose is under heavy development. It hasn't been implemented yet but I'm pretty sure it'll be implemented very soon before the beta test

---

