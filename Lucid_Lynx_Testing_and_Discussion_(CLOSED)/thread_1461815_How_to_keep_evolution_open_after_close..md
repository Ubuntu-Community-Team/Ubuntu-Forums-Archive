---
title: "How to keep evolution open after close."
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by alket on 2010-04-24
When I close empathy and gwibber they are in tray-like in inditicator applet (envelope thing in top panel) and when someone talks to me or posts in twitter the notification bar appears but when I close evolution it really closes and it does't show notifications. I don't want to keep evolution in taskbar all the time.

---

### Post by dcstar on 2010-04-24
> **babaroga said:**
> When I close empathy and gwibber they are in tray-like in inditicator applet (envelope thing in top panel) and when someone talks to me or posts in twitter the notification bar appears but when I close evolution it really closes and it does't show notifications. I don't want to keep evolution in taskbar all the time.

Start it in another panel.

---

### Post by alket on 2010-04-24
> **dcstar said:**
> Start it in another panel.

You know that what I was asking for. To act same as empathy and gwibber.

---

### Post by dcstar on 2010-04-24
> **babaroga said:**
> You know that what I was asking for. To act same as empathy and gwibber.

It doesn't matter what you are asking for, Evolution does not do what you want, so if you "don't want to keep evolution in taskbar all the time" then **it won't** if it is in another panel.

---

### Post by x-shaney-x on 2010-04-24
I find this a pain as well because I am trying to work with Evolution (never got on with it) and this is another annoyance.

As the OP said, other items in the messaging menu hide the window but don't close it whereas Evolution closes directly.
I thought this new system was supposed to be a replacement for the "inconsistent"  notification area/systray, yet it already has it's own inconsistencies from the start?

The other option would be to use Evo with alltray but of course that would be useless if you actually launch it from the messaging menu.

Not sure what starting it in another panel means?

---

### Post by Gourgi on 2010-04-25
> **babaroga said:**
> When I close empathy and gwibber they are in tray-like in inditicator applet (envelope thing in top panel) and when someone talks to me or posts in twitter the notification bar appears but when I close evolution it really closes and it does't show notifications. I don't want to keep evolution in taskbar all the time.

please look at this bug report [https://bugs.launchpad.net/evolution-indicator/+bug/460483](https://bugs.launchpad.net/evolution-indicator/+bug/460483)
you can try the ppa mentioned in the comments

---

### Post by x-shaney-x on 2010-04-25
Seems that PPA is a hacky workaround that has it's own problems.
The fact is, this behaviour should be default or it makes the new system pointless.
Like I said before, ubuntu have introduced this new system because they felt the previous one was inconsistent yet it seems the new one will stay inconsistent the devs of a major gnome app (Evolution) which is also the default mail app in ubuntu, are unwilling to introduce that way of working into their app.

Which means ubuntu now have to try to force them into it, change their default email app for one that does work correctly with their system or leave things as they are and swap one inconsistent system for another.

---

### Post by Merk42 on 2010-04-25
> **x-shaney-x said:**
> Seems that PPA is a hacky workaround that has it's own problems.
The fact is, this behaviour should be default or it makes the new system pointless.
Like I said before, ubuntu have introduced this new system because they felt the previous one was inconsistent yet it seems the new one will stay inconsistent the devs of a major gnome app (Evolution) which is also the default mail app in ubuntu, are unwilling to introduce that way of working into their app.

Which means ubuntu now have to try to force them into it, change their default email app for one that does work correctly with their system or leave things as they are and swap one inconsistent system for another.

...or if you read the bug report, introduce the newer 2.30 Evolution in Maverick which uses Dbus which should make porting it to the indicator applet easier.

---

### Post by x-shaney-x on 2010-04-25
> **Merk42 said:**
> ...or if you read the bug report, introduce the newer 2.30 Evolution in Maverick which uses Dbus which should make porting it to the indicator applet easier.
I did read the bug report and yes, one day it may all come together and work properly but the point is (to me) the system does not work as it should, it's not ready yet and shouldn't have been included until it was ready.
But alas, I am hijacking this thread somewhat which is quite wrong and my apologies to the OP.

---

