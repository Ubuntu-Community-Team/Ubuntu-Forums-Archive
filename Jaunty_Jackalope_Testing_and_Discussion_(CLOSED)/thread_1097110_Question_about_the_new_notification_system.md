---
title: "Question about the new notification system"
date: 2009-03-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by tad1073 on 2009-03-15
Is there a way to get the notifications to follow where the notification area is placed?

I have my task bar at the bottom and deleted the top bar so I could put my 2 line conky up top.

---

### Post by kurros on 2009-03-15
> **tad1073 said:**
> Is there a way to get the notifications to follow where the notification area is placed?

I have my task bar at the bottom and deleted the top bar so I could put my 2 line conky up top.

Notification bubbles have no relation to the Notification Area applet...

---

### Post by tad1073 on 2009-03-15
> **kurros said:**
> Notification bubbles have no relation to the Notification Area applet...

I think it would be a good idea if it did.

---

### Post by mariner09 on 2009-03-15
There used to be a tool that allowed you to configure where the pop-ups were displayed, but in the updates between alpha 5 and alpha 6, it seemed to go away.

Maybe something in gconf-editor will allow that modification...

---

### Post by RAOF on 2009-03-16
I don't know if the screen corner is choosable, but I'm pretty sure the top-right corner was chosen because there's generally nothing interesting there - it's mostly where close buttons end up.  As such the justification for the positioning doesn't depend on where the notification area is, or even whether there is a notification area.

---

### Post by ktraub on 2009-03-16
I have the same problem. 
I've combined the task & launch bars into a single bar located at the bottom of the screen.
If I'm working with network-manager and waiting for it to re-establish a connection the NM icon is active and animating at the bottom right.
However, the Notification occurs at the top right which, on a large display, can be out of the field-of-view.

Is there any way to manually change the notifications location?

---

### Post by Kow on 2009-03-16
The app for changing the location is called notification-properties and its broken.

---

### Post by ktraub on 2009-03-16
Is there a config file I can edit to change the notification location?

---

### Post by tad1073 on 2009-03-16
> **ktraub said:**
> is there a config file i can edit to change the notification location?

+1

---

### Post by phenest on 2009-03-22
There is a Pop-Up Notification thingy in Preferences. I tried choosing a different position, but it stays put in the top-right.

---

### Post by andrewabc on 2009-03-22
> **phenest said:**
> There is a Pop-Up Notification thingy in Preferences. I tried choosing a different position, but it stays put in the top-right.

Where is that menu item? I don't see it.

I even went into
system->preferences->main menu, and didn't see it listed there.

---

### Post by phenest on 2009-03-22
Also available in the Configuration Editor under /apps/notification-daemon.

---

### Post by ktp on 2009-03-22
> **andrewabc said:**
> Where is that menu item? I don't see it.

I even went into
system->preferences->main menu, and didn't see it listed there.

Try executing **notification-properties**.  You can also use **alacarte** to edit System->Preferences menu to enable Pop-up Notification.  

FYI, I had not luck setting the values..at least the Test always came up on top right.

---

### Post by cdEWoozy on 2009-03-23
> **phenest said:**
> There is a Pop-Up Notification thingy in Preferences. I tried choosing a different position, but it stays put in the top-right.

The notification position is hardcoded into notify-osd as far as I know. The utility to set the position for the notifications works only for the old notification system.

---

### Post by tghe-retford on 2009-03-23
The notification position does indeed have its position fixed into the top right area and after someone posted a bug to ask if it can be configured to be placed elsewhere and was told quite swiftly it will not be fixed. So sorry, it looks as if unless you compile notify-osd yourself, you'll have to put up with it being in the top right of the screen.

Source: [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095)

A bit annoying, because I only have one panel and the notification area at the bottom of the screen which notify-osd does not respect. We can only hope someone recompiles notify-osd to be configurable and places it in a PPA.

---

### Post by andrewabc on 2009-03-24
> **ktp said:**
> Try executing **notification-properties**.  You can also use **alacarte** to edit System->Preferences menu to enable Pop-up Notification.  

FYI, I had not luck setting the values..at least the Test always came up on top right.

I typed that in:
```
~$ notification-properties
The program 'notification-properties' is currently not installed.  You can install it by typing:
sudo apt-get install notification-daemon
bash: notification-properties: command not found

```
So I have notifications, but it says I don't have it installed?
Do you need this installed to get the notification options?

> Also available in the Configuration Editor under /apps/notification-daemon. 
No idea how to get to there or what to do (where is configuration editor?).

---

### Post by scaine on 2009-03-24
Looks like recent updates have removed notification-settings, but as a previous poster noted, it didn't work anyway.

The command for gconf editor is just gconf-editor.  But again, since the notification daemon has been removed now and since notify-osd is non-configurable, there's no reason to run it as there are no keys to configure...

I've added my 2 cents to that bug report.  There's an undercurrent of arrogance in that thread that I haven't seen since the days of the gnome-screensaver debacle.  Storm's a-coming!  ;)

---

### Post by TrueTom on 2009-03-24
> ktp420, you're quite correct to point out that the average user is not going to want to recompile software. But that's fine, because they are not going to want to configure the bubble placement either. We could be wrong about that; the beauty of Free Software is that if we are wrong, you can make your own variant and it will be wildly popular.

Well, they wanted to compete with Apple. With the arrogant attitude they are doing are pretty good job already. Fortunately, Apple usually doesn't make such crappy software, so there is still some space for improvement left...

---

### Post by macogw on 2009-03-24
```
apt-get install gnome-stracciatella-session
```
Then choose that session when you login.  No Notfy-OSD stuff on there, k?

---

### Post by castrojo on 2009-03-24
There is a "vanilla gnome" session available in Jaunty if you want the old-style notifications.

[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

---

### Post by scaine on 2009-03-24
Don't you think it's a little strange to throw the new notify-osd stuff into Jaunty at the last minute, then, instead of fixing the subsequent outcry, just offer a vanilla session?

Isn't just as odd that we have to download a vanilla session to get back what some people might see as "basic functionality", instead of pushing notify-osd back to Karmic until better testing is complete?

I think Shuttleworth and the team are using their Ubuntu fan base here as guinea pigs for notify-osd.  It's a brave move, because it could conceivably push people away from Ubuntu, or at least gnome (how is KDE taking this change?).

I should clarify, notify-osd isn't bad enough to push me away from Ubuntu personally and I doubt too many would argue that, but the attitudes about it are pretty hard to take (from both sides...).

It's the first time I've really seen Ubuntu act like Gnome with the whole "our way is the only way" attitude.

---

### Post by KCG102282 on 2009-03-24
> **scaine said:**
> Don't you think it's a little strange to throw the new notify-osd stuff into Jaunty at the last minute, then, instead of fixing the subsequent outcry, just offer a vanilla session?

Isn't just as odd that we have to download a vanilla session to get back what some people might see as "basic functionality", instead of pushing notify-osd back to Karmic until better testing is complete?

I think Shuttleworth and the team are using their Ubuntu fan base here as guinea pigs for notify-osd.  It's a brave move, because it could conceivably push people away from Ubuntu, or at least gnome (how is KDE taking this change?).

I should clarify, notify-osd isn't bad enough to push me away from Ubuntu personally and I doubt too many would argue that, but the attitudes about it are pretty hard to take (from both sides...).

It's the first time I've really seen Ubuntu act like Gnome with the whole "our way is the only way" attitude.
KDE doesnt seem to have all of the new notifications like Ubuntu does. I personally like them.

---

### Post by castrojo on 2009-03-24
> **scaine said:**
> Don't you think it's a little strange to throw the new notify-osd stuff into Jaunty at the last minute, then, instead of fixing the subsequent outcry, just offer a vanilla session?

Both notify-osd and the vanilla session were uploaded before feature freeze. That's why there are release schedules and milestones.

> I think Shuttleworth and the team are using their Ubuntu fan base here as guinea pigs for notify-osd.

You're running a development version of Ubuntu, of course you're a guinea pig. :p

---

### Post by brownknight on 2009-03-25
> **whiprush said:**
> 

you're running a development version of ubuntu, of course you're a guinea pig. :p

+1 :)

---

### Post by elmago79 on 2009-03-25
> **tghe-retford said:**
> The notification position does indeed have its position fixed into the top right area and after someone posted a bug to ask if it can be configured to be placed elsewhere and was told quite swiftly it will not be fixed. So sorry, it looks as if unless you compile notify-osd yourself, you'll have to put up with it being in the top right of the screen.

Source: [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/346095)

A bit annoying, because I only have one panel and the notification area at the bottom of the screen which notify-osd does not respect. We can only hope someone recompiles notify-osd to be configurable and places it in a PPA.

I gather from reading the bug that this is only a matter of phrasing a reasonable request either as a Wishlist or a Usability issue. I'm new to Launchpad, so I have no idea about how to do that.

I do think there are some usability issues with the standard behavior, for instance:

[LIST]
[*]The top right corner is where close button of maximized windows goes. You can miss a notification when moving the mouse to close a window.

[*]I can place the inotify applet anywhere on the panel and I would expect the notifications to follow that placement.

[*]If I'm using my top right corner for something else, like a desklet, there will be overlapping issues.
[/LIST]

So, what can I do about this problem?

---

### Post by TrueTom on 2009-03-25
> **elmago79 said:**
> So, what can I do about this problem?

Use the stracciatella session (apt-get install gnome-stracciatella-session) or write your own notification library.

---

### Post by elmago79 on 2009-03-25
I mean, really. :)

---

### Post by TrueTom on 2009-03-25
> **elmago79 said:**
> I mean, really. :)

That's the official position. If you don't like don't use it or write your own implementation. But don't complain that it has issues because it doesn't because it was designed that way and therefore is correct. Just read the related bugreports on launchpad. 

:)

---

### Post by RAOF on 2009-03-25
So, I'm not a notify-osd developer, but I think I've got a handle on the design philosophy.  Let me try to give a different perspective on these points.  Either I can convince you that the current design is correct, or you can strengthen your arguments against mine :).
> **elmago79 said:**
> 
[LIST]
[*]The top right corner is where close button of maximized windows goes. You can miss a notification when moving the mouse to close a window.
[/list]

a) The notification will still be shown, it will just be very nearly entirely transparent.  If you're interacting with the top right corner of the screen, that's where your attention will be, and you'll notice the appearance of this near-transparent notification.
b) This is partially the result of a bug/unimplemented feature.  The time that the mouse is over should not count toward the timeout of the notification, so it will always be visible, fully opaque, for the full 5sec (or whatever).
> **elmago79 said:**
> 
[list]
[*]I can place the inotify applet anywhere on the panel and I would expect the notifications to follow that placement.
[/list]

The notification applet has a small amount of space dedicated to it, whereas the notification popups require transient space.  You want the notifications to appear in a deterministic place, but you don't want them to obscure important information.  The top-right of the screen (for LTR languages; RTL languages may want the top-left) rarely contains important information - that's where the window decorations buttons are, but the menus and toolbars are mostly empty by that point.  Every other possible location has a higher interesting information content, so top-right is where the notifications should go.
> **elmago79 said:**
> 
[list]
[*]If I'm using my top right corner for something else, like a desklet, there will be overlapping issues.
[/LIST]

But only transiently, and you can easily interact with such a desklet by simply moving your mouse over it.

---

### Post by TrueTom on 2009-03-25
While the rational for the default position in Ubuntu is fine, it still doesn't justify the unwillingness to export a gconf key to select the corner (and the color for that matter), especially if you want get accepted upstream...

---

### Post by hugmenot on 2009-03-25
Personally, I don&#8217;t like that the volume ramp is shown in the same spot when I use my volume buttons. It always manages to divert my eyes to the top right, grabbing my attention, even though I should know there is nothing to see.

---

### Post by phenest on 2009-03-25
A thought has just occured to me... There is a Gnome Panel Applet. What if I don't use Gnome panels and use AWN instead? I don't even have gnome-panel installed. Is there a notification area icon instead?

---

### Post by scaine on 2009-03-25
> **whiprush said:**
> Both notify-osd and the vanilla session were uploaded before feature freeze. That's why there are release schedules and milestones.

Yeah, but these packages were literally thrown in to beat that feature freeze.  Wasn't it like the day before feature freeze these packages went in?  Fair enough, that's Canonical's perogative, but my point is that until that point, these packages were (to my knowledge) otherwise completely untested.  It's a bit rash.  Or "bold" I think is the word I used... :P


> **whiprush said:**
>  You're running a development version of Ubuntu, of course you're a guinea pig. :p

Ah, so notify-osd is coming out before release then, is it?  I don't mind testing the back of beyond while I'm using alpha or even beta software, but I reckon it's going to ship with this stuff in it and that will definitely cause friction, since sure as hell no-one who tries Jaunty once it's released will know about stracciatella.

Unless stracciatella is going to be installed by default?

---

### Post by scaine on 2009-03-25
> **phenest said:**
> A thought has just occured to me... There is a Gnome Panel Applet. What if I don't use Gnome panels and use AWN instead? I don't even have gnome-panel installed. Is there a notification area icon instead?

It doesn't matter if you have gnome-panels or even a notification area, as far as I can tell, notify-osd simply uses the top-right of the screen for notifications and that's that.  AWN, Cairo-dock, Docky, etc won't make any difference here.

---

### Post by marcog42 on 2009-03-25
> **RAOF said:**
> 
The notification applet has a small amount of space dedicated to it, whereas the notification popups require transient space.  You want the notifications to appear in a deterministic place, but you don't want them to obscure important information.  The top-right of the screen (for LTR languages; RTL languages may want the top-left) rarely contains important information - that's where the window decorations buttons are, but the menus and toolbars are mostly empty by that point.  Every other possible location has a higher interesting information content, so top-right is where the notifications should go.


I can think of a problem with this.  When someone has a large enough monitor, why would they be looking at a place that doesn't have anything interesting to look at?  It seems to me that you'd want a notification to come up in a place that DOES get attention, rather than a place people hardly look. I especially notice this when I'm surfing the web and there are different types of animations on the screen, or when I'm watching video of some sort.  The animation distracts me from noticing the notification.  

Often times I've only caught a fleeting glance at a notification as it fades from view because my attention was elsewhere on my monitor.  If i were able to movie to my bottom right, I would probably never miss it.

---

### Post by SushiR on 2009-03-25
The most elegant solution would be, that the user has a config dialog where he can drag the notification-bubble wherever he wants it to appear (like notifications in amarok 1.4). I'm waiting for this...

---

### Post by elmago79 on 2009-03-25
> **RAOF said:**
> 
a) The notification will still be shown, it will just be very nearly entirely transparent.  If you're interacting with the top right corner of the screen, that's where your attention will be, and you'll notice the appearance of this near-transparent notification.
b) This is partially the result of a bug/unimplemented feature.  The time that the mouse is over should not count toward the timeout of the notification, so it will always be visible, fully opaque, for the full 5sec (or whatever).

Just yesterday I was about to close a window when a notification was appearing. The result was that the notification appeared on the back of the window except for the border. It was one of the things that led me to think the placement was not that great. Maybe that is a real bug?

> The top-right of the screen **(for LTR languages; RTL languages may want the top-left)** rarely contains important information - that's where the window decorations buttons are, but the menus and toolbars are mostly empty by that point.  Every other possible location has a higher interesting information content, so top-right is where the notifications should go.

Hey, that's a pretty good argument right there. RTL language users might not find it that great for notifications to obscure whatever it is that they're reading by notifications.  

Also, following your argument, the bottom left corner (right corner for RTL) might be a better spot for placing notifications, since there's usually less going on in those areas.

---

### Post by RAOF on 2009-03-25
> **elmago79 said:**
> Just yesterday I was about to close a window when a notification was appearing. The result was that the notification appeared on the back of the window except for the border. It was one of the things that led me to think the placement was not that great. Maybe that is a real bug?

I'm not sure what you mean by "on the back of the window".  If you mean "behind the window", then I'd say that's a bug, yes.

> **elmago79 said:**
> 
Hey, that's a pretty good argument right there. RTL language users might not find it that great for notifications to obscure whatever it is that they're reading by notifications.  

Also, following your argument, the bottom left corner (right corner for RTL) might be a better spot for placing notifications, since there's usually less going on in those areas.

That'd be an argument for putting the bubble in the top-left in RTL locales, yes.  Not necessarily for having it configurable ;).

Also, I don't think your facts are correct.  At least for me, there's almost always something in the bottom-left corner for me - the status bar text of a maximised window, if nothing else.  I'd find it really annoying if the url of the link my mouse is over was obscured, for example.  Some form of study would be useful here, but I'm pretty sure that there's less interesting *information* presented in the top-right than any other screen corner.

---

### Post by Bakon Jarser on 2009-03-25
> **RAOF said:**
> 
Also, I don't think your facts are correct.  **At least for me**, there's almost always something in the bottom-left corner for me - the status bar text of a maximised window, if nothing else.  I'd find it really annoying if the url of the link my mouse is over was obscured, for example.  Some form of study would be useful here, but I'm pretty sure that there's less interesting *information* presented in the top-right than any other screen corner.

Exactly, for you there's something going on there.  Not for me, which is why it would be better for it to be there.  I don't see why they are so opposed to giving us options.  Bottom left happens to be where my amarok osd is and it would be great to have my notifications there to.

---

### Post by elmago79 on 2009-03-26
> **RAOF said:**
> I'm not sure what you mean by "on the back of the window".  If you mean "behind the window", then I'd say that's a bug, yes.

Yep, that's what I meant.

> **RAOF said:**
> That'd be an argument for putting the bubble in the top-left in RTL locales, yes.  Not necessarily for having it configurable ;).

You got me there, but it's a start.:P I would assume that making it configurable would be the easy way to that, but I have no idea.

Also, as Bakon notes, it's the "at least for me" that's problematic. Conky users like the OP (I don't see the point of Conky, but many seem to live by it) want the notifications somewhere else, because Conky tends to live there. Just as you would be it really annoyed if the url of the link your mouse is was obscured, I got similarly annoyed a few hours ago when the notifications kept appearing over my Pidgin conversation, only to reproduce the exact same thing that was appearing below and obscuring the window! In doing that, those notifications slows my work.

> I don't see why **they** are so opposed to giving us options.

There's no "they" in Ubuntu. Only us :). I know that developers and end-users talk a completely different language and view Ubuntu with entirely different eyes (and both think they know better), but I'm sure there is a way to work things out.

---

### Post by RAOF on 2009-03-26
> **Bakon Jarser said:**
> ...
I don't see why they are so opposed to giving us options.
...

Generally because one or more of:
[list]
[*] They don't particularly want to do that work right now.
[*] Implementing it would be not entirely trivial.
[*] You'd need to design a UI for the configuration.
[*] The scope for bugs doubles for each option available.
[/list]

Options have a non-zero cost, for the developers, the testers, and the users.  You want to have as few as possible - first work out if you can design it to Just Work.  If you can't, work out whether the option is worth it.

---

### Post by Cloud79 on 2009-03-26
The biggest problem right now with notifications.

Top right corner with dual 24" wide monitors. I never see the notifications because they are to far away. Is there a launchpad bug filed for this?

---

### Post by taavikko on 2009-03-26
> **Cloud79 said:**
> The biggest problem right now with notifications.

Top right corner with dual 24" wide monitors. I never see the notifications because they are to far away. Is there a launchpad bug filed for this?

Yes, there is one at [https://bugs.edge.launchpad.net/ubuntu/+source/notify-osd/+bug/331369](https://bugs.edge.launchpad.net/ubuntu/+source/notify-osd/+bug/331369)

---

### Post by scaine on 2009-03-26
I hate to be the voice of doom, but I don't think I've ever seen so many bugs filed about something so trivial.  I know some of the attitudes about notify-osd have been... strong, but why is there such resistance to this?  It's early doors yet, surely.  It will improve over time.

And hell, notify-osd is at least a hell of a lot prettier than the old lib-notify system.

[https://bugs.edge.launchpad.net/notify-osd/+bugs?search=Search&field.status=New&field.status=Incomplete&field.status=Confirmed&field.status=Triaged&field.status=In+Progress&field.status=Fix+Committed](https://bugs.edge.launchpad.net/notify-osd/+bugs?search=Search&field.status=New&field.status=Incomplete&field.status=Confirmed&field.status=Triaged&field.status=In+Progress&field.status=Fix+Committed)

Man, that's a lot of bugs.

---

### Post by TrueTom on 2009-03-26
> **scaine said:**
> I know some of the attitudes about notify-osd have been... strong, but why is there such resistance to this?

I can see three points:

0) The design is so fundamentally broken that you have to question the sanity of everyone involved.

1) As a result of this it renders the notification system practically useless and creates only a constant source of distractions.

2) An attitude of "Yeah, we know, we will look into that when we have time" would be more helpful then "We designed it that way and if you have a problem with that, do your own!".

---

### Post by tghe-retford on 2009-03-26
I really don't like the idea of "our way or the highway" when it comes to the notifications that seems to be coming out. I remember the Pidgin text box fiasco and ended up uninstalling that purely because I wasn't happy at the the attitude of people being told it was their way or the highway.

If notifications are supposed to be at the top of the screen, shouldn't it follow that the panel options be locked down and at least one panel with the notification area should be locked to the top of the screen? I mean, how far do we go with providing as least options as possible and insisting that one way is the only way?

It's a shame that people are not being given a choice because people work in different ways. Whilst I use my web browser and other tools in the left hand side, I keep media players in the top right of the screen, looking at it all, the bottom right of the screen where my notification area is the most logical area for me where there is least action. This will differ for other people. I would feel uncomfortable with having to change what I do because I am being told this is the way we do it.

I'll keep an eye on this discussion and the bugs which have been removed from Launchpad in regard to notification positioning and consider my position.

---

### Post by Denis_Cheremisov on 2009-03-26
Hahaha!
I know it was a bad idea. IMO Mark thought in a wrong way: he doesn't see the situation as a whole, but only in parts. He couldn't understand Mac OS X popularity come not only from it's eyecandies (vista is eyecandy too), but from both eyecandies and consistency. On the other hand vista's interface is very inconsistent. Now gnome is placed between windows and vista in the terms of consistency (I think it's very near to macosx). So, the way Mark had choosen is the worst: canonical doesn't have enough money to employ many good designers (gdm and notification osd prove they have no one :D), and they began to break interface consistency. But there is a chance: they didn't make much in this direction, it's not too late to stop.

---

### Post by Kazade on 2009-03-26
I'd like to reiterate what I've mentioned in other posts. The new notifications IMO look very nice, there are 4 major annoyances with the implementation though:

1. No customization of theme.
2. No customization of location (this is a massive flaw, not everyone uses the default layouts etc. I'd personally prefer bottom-right ).
3. The gun-ho, like-it-or-lump-it, we-know-best-you're-just-uneducated, attitude, flowing out of Canonical.
4. And this is the BIG one, what they did to the update notifier!! ...

I really think that many people haven't cottoned on to this one yet, and when Jaunty is released I guarantee this is the thing that will hit slashdot.org et al. The update notifier has NO icon any more, I can't tell whether my PC is up-to-date or not AND the update-manager window opens BY ITSELF! Firstly, who thinks that opening windows randomly (in the background without focus or not) is a sane idea?

Secondly, the update manager only shows you updates once a week, or every 2 days for security updates IIRC and it does so by opening the window up in the background. Now I don't want windows opening randomly, so I can disable the auto-launch with gconf-editor (good times), but in that case the only way I know there are updates is if I manually run sudo apt-get update/upgrade (bad times).

The update notifier was the one thing that worked perfectly, of all the stuff they could *fix* why this? I want my notifier icon back!!!

---

### Post by KCG102282 on 2009-03-26
> **Kazade said:**
> I'd like to reiterate what I've mentioned in other posts. The new notifications IMO look very nice, there are 4 major annoyances with the implementation though:

1. No customization of theme.
2. No customization of location (this is a massive flaw, not everyone uses the default layouts etc. I'd personally prefer bottom-right ).
3. The gun-ho, like-it-or-lump-it, we-know-best-you're-just-uneducated, attitude, flowing out of Canonical.
4. And this is the BIG one, what they did to the update notifier!! ...

I really think that many people haven't cottoned on to this one yet, and when Jaunty is released I guarantee this is the thing that will hit slashdot.org et al. The update notifier has NO icon any more, I can't tell whether my PC is up-to-date or not AND the update-manager window opens BY ITSELF! Firstly, who thinks that opening windows randomly (in the background without focus or not) is a sane idea?

Secondly, the update manager only shows you updates once a week, or every 2 days for security updates IIRC and it does so by opening the window up in the background. Now I don't want windows opening randomly, so I can disable the auto-launch with gconf-editor (good times), but in that case the only way I know there are updates is if I manually run sudo apt-get update/upgrade (bad times).

The update notifier was the one thing that worked perfectly, of all the stuff they could *fix* why this? I want my notifier icon back!!!
Yes I agree I do like what they did with the new notification system, but they need to fix Update notifier now!

---

### Post by Changturkey on 2009-03-26
> **Denis_Cheremisov said:**
> Hahaha!
Now gnome is placed between **windows and vista** in the terms of consistency (I think it's very near to macosx).

What?

---

### Post by Denis_Cheremisov on 2009-03-26
> **Changturkey said:**
> What?
Lol **** happens. I mean between Mac OS X and Windows.

---

### Post by scaine on 2009-03-26
> **Kazade said:**
> I'd like to reiterate what I've mentioned in other posts. The new notifications IMO look very nice, there are 4 major annoyances with the implementation though:

1. No customization of theme.
2. No customization of location (this is a massive flaw, not everyone uses the default layouts etc. I'd personally prefer bottom-right ).
3. The gun-ho, like-it-or-lump-it, we-know-best-you're-just-uneducated, attitude, flowing out of Canonical.
4. And this is the BIG one, what they did to the update notifier!! ...

I couldn't agree more on point two.  The top right is where I leave my pidgin and skype windows, so ironically when a notify-osd pops up to tell me that someone is calling me, the damn window is obscuring what I want to see in the first place!  Then I have to wait for it to go away, or mouse over to perform an action and then get distracted by that really very annoying "fade out almost completely, but not quite".  Worse, while you've moused-over the damn things, they don't go away until you move the mouse away.

None of which would be so bad, but all I'm hearing from the bug reports is that I just haven't gotten used to it yet, or that it's actually better this way and I haven't quite realised it yet.  Pretty frustrating.  Good luck pushing this upstream...

> **Kazade said:**
>  I really think that many people haven't cottoned on to this one yet, and when Jaunty is released I guarantee this is the thing that will hit slashdot.org et al. The update notifier has NO icon any more, I can't tell whether my PC is up-to-date or not AND the update-manager window opens BY ITSELF! Firstly, who thinks that opening windows randomly (in the background without focus or not) is a sane idea?

I haven't seen update-manager pop-up in the background since about Alpha4, or was it 3, so I think that crazy-*** behaviour is gone now.  But of course, now I have no indication that my system needs updates.  Which is really, really flawed.  I'll need to research the bugs on this and contribute, because there's no way that Jaunty can ship without some form of notification icon.

[EDIT : Oops - swore quite a lot in this post, sorry.]

---

### Post by ktp on 2009-03-27
There is a way to get the icon back:

gconftool -s --type bool /apps/update-notifier/auto_launch false 
 
restart X

---

### Post by xtoudi on 2009-03-27
What about **/apps/update-notifier/regular_auto_launch_interval** (gconf-editor)??

Info says that:

[I]The interval (in days) when auto launching update-manager for normal updates. Please note that it will auto launch for security updates immediately. If you set it to "0" it will also launch as soon as updates become available. 
[/I]
So if I set "0" (default "7") then .... ?? I set this for sure ... with "0".

EDIT:
this option runs a whole update-manager.

---

### Post by ktp on 2009-03-27
That will just popup the update manager.  I want the icon only and let me chose when to open update manager and update.  I don't need more dialogs poping up and stealing focus. =) (notice the rant)

---

### Post by xtoudi on 2009-03-28
> **ktp said:**
> That will just popup the update manager.  I want the icon only and let me chose when to open update manager and update.

Yes I know that and I want that too ... I'm only searching ... and trying to get a workaround or sth.

---

### Post by Pizdec on 2009-03-28
> Good luck pushing this upstream...
They couldn't. Gnome devs are smart enough not to include this crap into upstream. It's both buggy and unusable (by design) as hell.

---

### Post by Kazade on 2009-03-30
This is still bugging me... so I've been thinking about it a lot and I think the design guys have got the update-manager completely wrong..

IIRC, the reason they started to pop-up the update-manager and removed the icon is that the notification system should display things that just happened (e.g. you just changed the volume), and the system tray should show persistent state (e.g. the volume is muted). Because the update-manager/notification-icon was both notification and state(there are updates available AND you are not up-to-date) they opened the window for the latter case (which as most people outside the DX team seem to agree is madness).

So I thought, the easy solution is to ALWAYS show the update-notifier icon, but have a green tick when you are up-to-date, and the orange star / red arrow if you aren't. Each time you log in, if there are updates available you should get a notification which shows the orange-star/red-arrow icon.

That way you have a permanent indicator of the state of your updates, and you are notified when updates are available. I'm almost tempted to patch it myself and set up a PPA...

---

### Post by TrueTom on 2009-03-30
> **Kazade said:**
> So I thought, the easy solution is to ALWAYS show the update-notifier icon, but have a green tick when you are up-to-date, and the orange star / red arrow if you aren't. Each time you log in, if there are updates available you should get a notification which shows the orange-star/red-arrow icon.

Sorry, but this is also a bad idea. It was just fine the way it was.

---

### Post by Kazade on 2009-03-30
> **TrueTom said:**
> Sorry, but this is also a bad idea. It was just fine the way it was.

Yeh, I'm just trying to find a solution that fits in the with rest of those notification guidelines... I just want it back the way it was too :(

---

### Post by aamukahvi on 2009-03-30
> **Cloud79 said:**
> The biggest problem right now with notifications.

Top right corner with dual 24" wide monitors. I never see the notifications because they are to far away. Is there a launchpad bug filed for this?

Seems fixed now:

```
notify-osd (0.9.7-0ubuntu1) jaunty; urgency=low

  * New upstream version:
    - added and improved multihead support,
      notifications stick to panel whatever the monitor it is on (lp: #331369)
    - crashers fixes (lp: #331927, #349133)
    - enable the icon lookup fallback mechanism for fallback icons like
      notification-display-brightness-* (lp: #344385)
    - reworked parts of notify-osd in order to make it adapt dynamically to
      changes of font-face, font-size and dpi (lp: #339731)
    - ensure X errors will not kill notify-osd
    - use HTML- and markup-filter for title- and body-message-text also
      in fallback-dialog
  * debian/patches/correct_service_install.patch:
    - correctly install the dbus service
  * debian/rules:
    - use simple-patchsys rules

 -- Sebastien Bacher < @ubuntu.com>   Sat, 28 Mar 2009 12:45:12 +0100
```

---

### Post by uBeer on 2009-03-30
Yes, it has been fixed. At least at my desktop it shows the notifications in the top-right corner of my left monitor where my panels are.

Only thing is that if you drag the panel to the other monitor, the notifications will still be on the first monitor. But if you leave the panel there and restart the session it will probably work alright. I'll test it in a moment...

Edit: Hmm, a logout and login didn't seem to work. You probably have to restart the notifier and that will work after a restart or when you do it with the terminal.

---

### Post by drs305 on 2009-03-30
Many of the posts mention the location. I'd really like to be able to resize it (smaller) but haven't found a way to do so. I now have the daemon accessible in gconf-editor (apps/notification-daemon) but there is no size parameter.

---

