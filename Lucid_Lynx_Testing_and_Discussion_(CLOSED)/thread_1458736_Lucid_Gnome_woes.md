---
title: "Lucid Gnome woes"
date: 2010-04-20
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by TheNessus on 2010-04-20
First thing I did after installing Lucid is to uninstall Gwibber and anything relating to DesktopCouch. Gwibber is nice and all, but why does it have processes running in the background even when I didn't even start the application? Removing these two cut memory consumption by HALF, from 400 on login to 200.

Another issue is the Indicator Applet. The Indicator applet took some important things out from the Notification Area, such as as volume indicator, battery indicator, and message indicator. Fine by me. But now it left an incomplete Notification Area which only has a wireless indicator, and of course whatever programs you have running in the background using a Notification Area icon.

I find this to be redundant dualism; if you took the battery and sound indicators to the Indicator applet, you could have also added the wireless indicator! So now it's like having two incomplete things that are doing the same job. 

Also, I don't use evolution (and gwibber) so the notification applet is useless for me, it only uses Empathy. I would like to remove the Indicator applet and use Empathy's Notification Area icon instead. Easy? no, not really; because then I would lose the battery and sound indicators. So I am actually forced to use two incomplete applets that do the same job.

It's a shame that such a great release has these silly GUI inconveniences.

---

### Post by swoll1980 on 2010-04-20
How much RAM do you have?

---

### Post by TheNessus on 2010-04-20
> **swoll1980 said:**
> How much RAM do you have?
1500
but this is irrelevant, had I had 4gb it would still annoy me :)

---

### Post by madjr on 2010-04-20
did you reported the bug or papercut (usability issues)?

you still in time before final release

also i dont get the notification area thing, can you show a screeny?

---

### Post by TheNessus on 2010-04-20
> **madjr said:**
> did you reported the bug or papercut (usability issues)?

you still in time before final release

also i dont get the notification area thing, can you show a screeny?
Where could I report a papercut? in the lucid testing forum?

I'm on KDE now, give me some minutes.

---

### Post by swoll1980 on 2010-04-20
> **TheNessus said:**
> then I would lose the battery and sound indicators. So I am actually forced to use two incomplete applets that do the same job.

You can uninstall just the messaging part of the indicator. You might also be able to install a wireless indicator. They are all different packages even though they use the same indicate applet. It really is a cool thing people just have to learn to use it, and Ubuntu has to put out defaults that make more sense. Give them time.

---

### Post by TheNessus on 2010-04-20
here, a screenshot of only what's bothering me

[[IMG]http://j.imagehost.org/t/0244/Screenshot.jpg[/IMG]]("http://j.imagehost.org/view/0244/Screenshot")


> **swoll1980 said:**
> You can uninstall just the messaging part of  the indicator. You might also be able to install a wireless indicator.  They are all different packages even though they use the same indicate  applet. It really is a cool thing people just have to learn to use it,  and Ubuntu has to put out defaults that make more sense. Give them  time.

But still, don't do two of them do basically the same job? only that one of them also shows programs running in the background. It would make a lot more sense to seperate the two: one for things like power, sound, wireless, language, etc. And one for programs. It's so annoying have two of them. And notice in the screenshot, that the indicator has no handle, and the notification area does (those 3 lines at its left), making it an ugly inconsistency.

---

### Post by swoll1980 on 2010-04-20
> **TheNessus said:**
> here, a screenshot of only what's bothering me

[[IMG]http://j.imagehost.org/t/0244/Screenshot.jpg[/IMG]]("http://j.imagehost.org/view/0244/Screenshot")

You can remove the message indicate package, and still keep everything else. I'm not talking about removing the gnome applet called indicator. I'm talking about removing the package called message indicator or what ever it's called. google it. That will leave the indicator on the task bar but remove the messaging portion of it. You may also be able to ad a wireless indicator, which if it exist would add a wireless icon to the indicator you already have in your task bar.

sudo apt-get remove "name of the message indicator package"

Add: If a wireless package for the indicator doesn't already exist I'm sure someones working on it.

---

### Post by TheNessus on 2010-04-20
> **swoll1980 said:**
> You can remove the message indicate package, and still keep everything else. I'm not talking about removing the gnome applet called indicator. I'm talking about removing the package called message indicator or what ever it's called. google it. That will leave the indicator on the task bar but remove the messaging portion of it. You may also be able to ad a wireless indicator, which if it exist would add a wireless icon to the indicator you already have in your task bar.

sudo apt-get remove "name of the message indicator package"

Add: If a wireless package for the indicator doesn't already exist I'm sure someones working on it.

Ok, both things aren't what the issue is about. To clarify:

If I uninstall the messaging part of the indicator applet, I would still be left with battery and sound indicators in the applet. So far so good. The Wireless indicator (and language input indicator) are in the Notification Area (so basically, two applets doing the same job only with different indicators...). 

It would be best to actually have the battery, sound, wireless, and all the rest of them, all in the notification area, as they always were...  and have an OPTION to have some of them be seperately in the the Indicator applet. 

As it is, after all - two applets showing different indicators; an unexplained split, a confusing and annoying redundancy.

---

### Post by swoll1980 on 2010-04-20
> **TheNessus said:**
> Ok, both things aren't what the issue is about. To clarify:

If I uninstall the messaging part of the indicator applet, I would still be left with battery and sound indicators in the applet. So far so good. The Wireless indicator (and language input indicator) are in the Notification Area (so basically, two applets doing the same job only with different indicators...). 

It would be best to actually have the battery, sound, wireless, and all the rest of them, all in the notification area, as they always were...  and have an OPTION to have some of them be seperately in the the Indicator applet. 

As it is, after all - two applets showing different indicators; an unexplained split, a confusing and annoying redundancy.

I'm sure they will do away with the task manager once everyone is on board with the indicator. Did you check to see if there was a package to add the wireless to the indicator?

---

### Post by TheNessus on 2010-04-20
> **swoll1980 said:**
> I'm sure they will do away with the task manager once everyone is on board with the indicator. Did you check to see if there was a package to add the wireless to the indicator?
well, let's hope; otherwise it's really annoying! :)

Yes, there is none (in Synaptic, at least).

---

### Post by madjr on 2010-04-20
reporting papercuts (small usability bugs):

[http://davidsiegel.org/](http://davidsiegel.org/)

[https://wiki.ubuntu.com/PaperCut](https://wiki.ubuntu.com/PaperCut)
[https://wiki.ubuntu.com/OneHundredPaperCuts](https://wiki.ubuntu.com/OneHundredPaperCuts)

[https://edge.launchpad.net/hundredpapercuts/](https://edge.launchpad.net/hundredpapercuts/)
[https://edge.launchpad.net/hundredpapercuts/lucid](https://edge.launchpad.net/hundredpapercuts/lucid)

:D

---

### Post by TheNessus on 2010-04-20
> **madjr said:**
> papercuts:

[http://davidsiegel.org/](http://davidsiegel.org/)

[https://wiki.ubuntu.com/PaperCut](https://wiki.ubuntu.com/PaperCut)
[https://wiki.ubuntu.com/OneHundredPaperCuts](https://wiki.ubuntu.com/OneHundredPaperCuts)

[https://edge.launchpad.net/hundredpapercuts/](https://edge.launchpad.net/hundredpapercuts/)
[https://edge.launchpad.net/hundredpapercuts/lucid](https://edge.launchpad.net/hundredpapercuts/lucid)
thanks! I have filed a bug report :)

---

### Post by chris4585 on 2010-04-20
I understand you, TheNessus, it is annoying.  Forcing a person to use two things that do the same thing and eat twice as much memory.

---

### Post by swoll1980 on 2010-04-20
> **chris4585 said:**
> I understand you, TheNessus, it is annoying.  Forcing a person to use two things that do the same thing and eat twice as much memory.

No ones forcing you to do anything.

---

### Post by madjr on 2010-04-20
> **TheNessus said:**
> thanks! I have filed a bug report :)

cool

you have a link or links? others may find them annoying too and it gets higher up the queue

it may get fixed by final release day, if not it should come with an update.

the Gwibber is probably much higher priority cause of the memory leak

---

### Post by cariboo on 2010-04-20
This should really be in Lucid Testing & Discussion, IF you check out the threads in the sub-forum your questions will be answered. Moved.

---

### Post by TheNessus on 2010-04-21
> **madjr said:**
> cool

you have a link or links? others may find them annoying too and it gets higher up the queue

it may get fixed by final release day, if not it should come with an update.

the Gwibber is probably much higher priority cause of the memory leak

I don't think Gwibber has a mem leak bug, it's just a heavy appplication using other heavy applications such as DesktopCouch. Its mem usage remains constant (no leak, just uses a lot of memory)

Here is a link to the bug report (marked INVALID, since it is a duplicate bug report; issue will be fixed next release)
[https://bugs.launchpad.net/hundredpapercuts/+bug/567499](https://bugs.launchpad.net/hundredpapercuts/+bug/567499)

---

### Post by areteichi on 2010-04-21
Looks like Mark Shuttleworth posted a new blog at a right time.

He addresses the current segmentation of the indicator applet and the notification area.

From [COLOR="Red"][http://www.markshuttleworth.com/archives/347](http://www.markshuttleworth.com/archives/347)[/COLOR]
> When we set up Project Ayatana to improve the usability of the whole desktop, we called it Ayatana because we were focused on the “sphere of consciousness”, one’s awareness of what’s going on outside  of the current application. There are two key aspects to the work:

   1. Notifications are “awareness distilled” in the sense that you cannot interact with them at all.  We designed them as ephemeral “click-transparent” messages, implemented in Notify-OSD. Their sole purpose is to notify you of transient events.
   2. Indicator Menus combine persistent awareness of a state with a set of options for modifying that state.

In this blog I’ll outline the arc of our work on indicator menus to date, and the trajectory we expect it to follow. We’re about a year into the effort, all told, and I think it will take another 18 months before we can consider it baked. It should be done by 12.04 LTS. This is an iterative process, and things are in flux right now. I hope, when we are happy that we can commit to ABI stability, that Gnome and KDE will adopt the work too. For the moment, the rapid pace of evolution has meant that we’re depending on fantastic upstreams to keep up with us as things move.
Goals of the Ayatana Indicators

The indicators are designed to create a persistent awareness of state, or an awareness of a persistent state. They complement notifications: they are persistent, when notifications are ephemeral. You might miss a notification, but you should always be able to check your indicators. You can interact with indicators, using their menus, in contrast with the un-clickable notifications.
[continues...]


---

### Post by chris4585 on 2010-04-21
> **swoll1980 said:**
> No ones forcing you to do anything.

Obviously if I remove one of the applets I lose part of the functionality.  So I can't remove what I want without losing something else I need.

---

### Post by uRock on 2010-04-21
Lol, wat?

All that stuff is in one place.

---

### Post by chris4585 on 2010-04-21
> **uRock said:**
> Lol, wat?

All that stuff is in one place.

Is that karmic or lucid?

---

### Post by ankspo71 on 2010-04-21
> **TheNessus said:**
> First thing I did after installing Lucid is to uninstall Gwibber and anything relating to DesktopCouch. Gwibber is nice and all, but why does it have processes running in the background even when I didn't even start the application? Removing these two cut memory consumption by HALF, from 400 on login to 200.

Another issue is the Indicator Applet. The Indicator applet took some important things out from the Notification Area, such as as volume indicator, battery indicator, and message indicator. Fine by me. But now it left an incomplete Notification Area which only has a wireless indicator, and of course whatever programs you have running in the background using a Notification Area icon.

I find this to be redundant dualism; if you took the battery and sound indicators to the Indicator applet, you could have also added the wireless indicator! So now it's like having two incomplete things that are doing the same job. 

Also, I don't use evolution (and gwibber) so the notification applet is useless for me, it only uses Empathy. I would like to remove the Indicator applet and use Empathy's Notification Area icon instead. Easy? no, not really; because then I would lose the battery and sound indicators. So I am actually forced to use two incomplete applets that do the same job.

It's a shame that such a great release has these silly GUI inconveniences.

Some of new Gnome features are the reason why I switched to Kubuntu as my primary desktop. The applets were not configurable to use my favorite email and or chat clients, making the MeMenu something I would choose not to use. I didn't like how gibber service continues to run when I only need look at my facebook account once a week. I also have an Ubuntu One account that has no files in it lol. So all in all, at this time, Gnome isn't right for me. Maybe in the near future I will go back after some more features are included up in applets/MeMenu area, but now I'm starting to find KDE4.4 more convenient than Gnome (except for the themes part... there are so many theme options in KDE to experiment with). 

If gnome-shell get as many features as, and gets as customizable as, the current gnome desktop, then I wouldn't mind using it as my window manager when I go back to Ubuntu. I always liked KDE and Gnome, but always preferred to stay with Gnome. Now it seems to be the other way around.

---

### Post by uRock on 2010-04-21
> **chris4585 said:**
> Is that karmic or lucid?
Lucid

---

### Post by chris4585 on 2010-04-22
> **uRock said:**
> Lucid

Ah, but its not the same applet though.

---

### Post by uRock on 2010-04-23
Use what works. Notification Area shows everything I need within it. Battery/Network/Pidgin/Rhythmbox are the ones that normally show there.

---

