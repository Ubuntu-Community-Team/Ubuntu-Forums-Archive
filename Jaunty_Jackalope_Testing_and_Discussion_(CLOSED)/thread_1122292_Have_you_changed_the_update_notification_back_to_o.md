---
title: "Have you changed the update notification back to old notification icon?"
date: 2009-04-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ktp on 2009-04-10
Wondering how many people are using the default update notification system, which will popup update manger a day after for security updates or seven days for regular updates.  Or people have changed back to old notification icon using gconf option.
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```  Do you find the notification icon confusing?

---

### Post by Languid Heap on 2009-04-10
I like the update notifications in the system tray, but I haven't switched back yet. I figured I should give the new system a try before making a decision. But, during betas I usually update at least once a day on my own so I haven't had a chance to see the new style in action yet :p

---

### Post by fondle-em on 2009-04-11
> **ktp said:**
> Wondering how many people are using the default update notification system, which will popup update manger a day after for security updates or seven days for regular updates.  Or people have changed back to old notification icon using gconf option.
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```  Do you find the notification icon confusing?

Rolled back to the old, sensible behavior.  There's nothing confusing about a bright notification icon in your notification area that tells you how many updates are available when you hover the cursor over it.  The wording of the message you get when you hover over it should be made slightly more specific as to the nature of the updates - "Ubuntu Updater has 23 application and 2 system updates" or something, but that's the extent of it.  This change seems counter-intuitive.

---

### Post by kansasnoob on 2009-04-11
> **ktp said:**
> Wondering how many people are using the default update notification system, which will popup update manger a day after for security updates or seven days for regular updates.  Or people have changed back to old notification icon using gconf option.
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```  Do you find the notification icon confusing?

I go one step beyond enabling the old tray icon:

[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

---

### Post by autocrosser on 2009-04-11
> **kansasnoob said:**
> I go one step beyond enabling the old tray icon:

[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

I have gone the same way---Martin has been vocal on dev-list about this un-needed change & I agree with him.

---

### Post by cariboo on 2009-04-11
I'm an update junky, I usually update at least 3 times a day. I haven't seen the new update notification yet. :)

Jim

---

### Post by michaelzap on 2009-04-11
> **languid heap said:**
> i like the update notifications in the system tray, but i haven't switched back yet. I figured i should give the new system a try before making a decision. But, during betas i usually update at least once a day on my own so i haven't had a chance to see the new style in action yet :p

+1

---

### Post by tawmas on 2009-04-11
> **ktp said:**
> Wondering how many people are using the default update notification system, which will popup update manger a day after for security updates or seven days for regular updates.  Or people have changed back to old notification icon using gconf option.
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```  Do you find the notification icon confusing?

I didn't know I could do that, so I'm now back to the old system.

I was doing manual updates from the command line, and I was quite disturbed by the "system restart required" popup that the new notifications were throwing in my face. Not as vocal as Windows', but a first step in the wrong direction nonetheless.

---

### Post by binbash on 2009-04-11
I am using the new system, it is better in my opinion.

---

### Post by phenest on 2009-04-11
> **tawmas said:**
> I didn't know I could do that, so I'm now back to the old system.

I was doing manual updates from the command line, and I was quite disturbed by the "system restart required" popup that the new notifications were throwing in my face. Not as vocal as Windows', but a first step in the wrong direction nonetheless.

Ditto. Mark has not thought this notification system through. When he first mentioned it, I thought he was trying to improve the existing system. But, alas, he has not.

I use AWN, and use AWN's applet for notifications.

---

### Post by ktp on 2009-04-11
> **Languid Heap said:**
> I like the update notifications in the system tray, but I haven't switched back yet. I figured I should give the new system a try before making a decision. But, during betas I usually update at least once a day on my own so I haven't had a chance to see the new style in action yet :p

That is reasonable thing to do.  I have it a try, but having seven days late updates when I thought I set it to check and notify for updates daily didn't seem right to me.

---

### Post by andrewabc on 2009-04-11
I've been using Jaunty since Alpha 4 and I've never once seen the update notification. I always go to system->update manager

Update manager is also worse. When there is a list of updates, it shows the total mb to download, but doesn't list the number of updates to download.

The new update notification is not better than previous one.

Basically, it still checks for updates every day, but doesn't bother to notify you if you have updates (until 7 days later)!? That is stupid.

The poll sucks. I'm not using the new update notifications, because I've never seen it before. And I havn't switched back to old notification.

---

### Post by phenest on 2009-04-11
> **andrewabc said:**
> I've been using Jaunty since Alpha 4 and I've never once seen the update notification....The new update notification is not better than previous one....The poll sucks. I'm not using the new update notifications, because I've never seen it before. And I havn't switched back to old notification.

Er, how do you know if the new system is worse if you haven't seen it?

The poll doesn't suck. You simply don't have to vote.

---

### Post by andrewabc on 2009-04-11
> **phenest said:**
> Er, how do you know if the new system is worse if you haven't seen it?

The poll doesn't suck. You simply don't have to vote.

Well, if I havn't seen it, then there must be something wrong if I have 50 updates and several security updates available in update manager, but I have to wait several days to be notified otherwise?

With the old way, if you had updates it would tell you, and not wait 7 days to tell you. Pretty simple.

And it still checks for updates in the background? But doesn't bother telling you when it finds updates? What's the point of checking for updates in background then? Maybe it should only check for updates every 7 days, and notify you if it sees any on its weekly checkin.

I'm not sure how the new way is better than the old way. What are the benefits? I heard people saying after the 7 days it automatically opens update manager without telling you (it just pops up whenever)?

---

### Post by phenest on 2009-04-11
What I was trying to say was, if you haven't seen them, how do you know the dalayed updates notification is anything to do with it, or for that matter, if it's installed. You may just have a problem with the Update Manager.

---

### Post by andrewabc on 2009-04-11
> **phenest said:**
> What I was trying to say was, if you haven't seen them, how do you know the dalayed updates notification is anything to do with it, or for that matter, if it's installed. You may just have a problem with the Update Manager.

I have no idea :P
All the other notifications (black popups) work fine.

Heck, do people have screenshots of the update notification?

---

### Post by SketchyClown on 2009-04-11
I'm the kind of person who runs the update manager daily, so this hasn't affected me much personally. But I think that for new users and learning users, having a prompt update notification system in place is important. The right direction would be to have a system that:

1) You can enable/disable if you like & maybe set time to check.
2) Shows a very visible notification icon in the Panel with OSD.
3) Shows the number/kind of updates in the OSD.
4) Shows if restart will be required.

Very simple, very useful.

Why make system updates less accessible by hiding them from people for 7 days???

Ridiculous.

---

### Post by Incognito-Here on 2009-04-11
So, the conclusion is simple: despite of the fact new notification system is the default, more than a half of users disable it. This fact proves notify-osd should be closed as a dead idea.

---

### Post by tawmas on 2009-04-11
> **Incognito-Here said:**
> So, the conclusion is simple: despite of the fact new notification system is the default, more than a half of users disable it. This fact proves notify-osd should be closed as a dead idea.

I'm sorry but I fail to see how that conclusion follows. Even if the 57 respondents so far were a representative sample of the Ubuntu users, and they're not, update notifications is only one aspect of the new notification system, and probably not the primary aspect.

I do agree there's a fault with update notifications (see my reply above), but I don't think the whole of the system needs to be trashed because of this. For example, I like notification bubbles, and after being initially very skeptical I even like the fact that they are not clickable. I see some value in the ideas behind the notification applet, although the current incarnation sucks in many ways.

It's just the update notifications that need to be reworked (or restored to original behaviour). Further, we still have to see how well they work after the release, which is the usage scenario for which they were designed (I still expect they will not do well, but let's wait and see).

---

### Post by Stupendoussteve on 2009-04-11
> **cariboo907 said:**
> I'm an update junky, I usually update at least 3 times a day. I haven't seen the new update notification yet. :)

Jim

Me neither. I did go in and reset the time period that it will alert me to new updates, so it only waits 1 day not 7. The key to change this in gconf-editor is /apps/update-notifier/regular_auto_launch_interval. If you set it to 0 it will pop up when updates are available, 1 does it daily etc. It is supposed to popup instantly when there are security updates.

---

### Post by Darkshade on 2009-04-11
> **cariboo907 said:**
> I'm an update junky, I usually update at least 3 times a day. I haven't seen the new update notification yet. :)

Jim

+1 I have disabled the update notifier from the startup applications menu - what's the point if I manually update every 2-3 hours anyway? :lolflag:

---

### Post by kansasnoob on 2009-04-11
I'm liking the results of this poll!

Hopefully someone pays attention!

---

### Post by go7Ul1ai on 2009-04-11
> **Darkshade said:**
> +1 I have disabled the update notifier from the startup applications menu - what's the point if I manually update every 2-3 hours anyway? :lolflag:

I thought I was the only one ^_^

---

### Post by Simian Man on 2009-04-11
This poll is ill-formed because the thread title is "Are you using the new update notification" and the poll title is "Have you changed the update notification back to old notification icon?"

So basically they are asking opposite things which is confusing.  I wouldn't be surprised if a few people voted the wrong way.

---

### Post by FuturePilot on 2009-04-11
I used the gconf command to change it back to the old behavior. I like to be notified of updates when they are available, not a week later.

---

### Post by kansasnoob on 2009-04-12
> **Simian Man said:**
> This poll is ill-formed because the thread title is "Are you using the new update notification" and the poll title is "Have you changed the update notification back to old notification icon?"

So basically they are asking opposite things which is confusing.  I wouldn't be surprised if a few people voted the wrong way.

I dunno' when I read the title and the **full** post it seems clear to me.

---

### Post by lamalex on 2009-04-12
I think the current implementation would be sane behaviour post release; making people wait up to 7 days during the testing phase is madness though, in alpha/beta/rc we need updates immediately so that the maximum amount of testing can happen.

I certainly preferred the notification area icon, but the current system is not as wretched as some of the people in this thread would like to make it sound, it's also important to make sure people understand what this thread is about. It sounds like some people are confusing notify-osd with the new update behaviour. They're different, although the behaviour change of updates is related to notify-osd.

---

### Post by phenest on 2009-04-12
One thing I notice is everyone says that they DO eventually see the update notifications, but only after 7 days. This is configurable in the Configuration Editor under /apps/update-notifier/regular_auto_launch_interval which has 7 days as default. This value should really follow what you would set in Synaptics, for example, and vice versa.

---

### Post by ktp on 2009-04-12
> **Iamalex said:**
> I think the current implementation would be sane behaviour post release; making people wait up to 7 days during the testing phase is madness though, in alpha/beta/rc we need updates immediately so that the maximum amount of testing can happen.

I don't know.  I mean seven days late is seven days late...specially when the options imply that you will be notify when there is an update.  There is nothing that says it will be seven days later.  It just seems to give false positive that you will be notified when there are updates.

Post release, I would rather like to know update when its there, even the non-critical ones.  I know there are config keys that can change the behavior, but how many non-export users will know that your updates will be seven days late and you can change it by changing this key.

---

### Post by bruce89 on 2009-04-12
> **kansasnoob said:**
> I go one step beyond enabling the old tray icon:

[http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/](http://martinpitt.wordpress.com/2009/02/23/the-stracciatella-gnome-session/)

Same here.

Perhaps I may move to Debian.

> **Incognito-Here said:**
> So, the conclusion is simple: despite of the fact new notification system is the default, more than a half of users disable it. This fact proves notify-osd should be closed as a dead idea.

No, the update-manager behaviour is a different madness to notify-osd.

---

### Post by zorkerz on 2009-04-12
I think there is very different desired behavior for all of us using pre-final jaunty and the majority of people using jaunty. 

Me personally I had no idea about the issue until reading this thread because I update as procrastination (meaning many many times a day). I think that it is essential that a warning happens immediately for critical updates. I would just assume be notified immediately for all updates and have now set it that way. 

There is a whole segment of people using ubuntu that this does not cover though. I have about 5 friends who have recently picked up ubuntu mostly due to windows problems. I notice that each and every one of them completely ignores the update notification. This as a big problem for the security and reliability of their computer. 

In windows the notification area gets so filled with crap that people get used to ignoring it. This carries over to ubuntu especially when updates happen all the time. I have tried to convince my friends that haveing new updates every few days should be reassuring them that ubuntu is getting safer and better all the time. Instead they just ignor updates. If people only get warned about updates once a week it might be just what it takes to get people to actually update their system. This would be an extremely good thing.

---

### Post by gfe on 2009-04-13
I think the thing to do is to give the user the ability in the GUI to set the notification method. I think an automatic application launch is annoying; the tray icon makes more sense to me. When I couldn't find a way to implement the icon, that's when I looked for and found this topic. I don't care what the default method is as long as it can easily be changed.

---

### Post by zorkerz on 2009-04-13
I agree a gui method for customization is crucial. I did not realize that update manager is actually opening now rather than having the notification area icon. Thats interesting ill have to not update for a bit and see what I think of it when it happens.

---

### Post by sadicote on 2009-04-13
Hi, I am not sure, i had used the gconf fix before because i was not getting any update notifications, and then after an upgrade when i stopped getting the notifications again, but then this caused my sources list to be messed up with duplicates, which i had to comment out, and then revert with "true" option. Now i would really like to have those notifications displayed so that i know when to update. Is there a way to find out what state my computer is in as far as this notification icon business is concerned, without messing it up like before?:-k

---

### Post by ktp on 2009-04-13
> **sadicote said:**
> Hi, I am not sure, i had used the gconf fix before because i was not getting any update notifications, and then after an upgrade when i stopped getting the notifications again, but then this caused my sources list to be messed up with duplicates, which i had to comment out, and then revert with "true" option. Now i would really like to have those notifications displayed so that i know when to update. Is there a way to find out what state my computer is in as far as this notification icon business is concerned, without messing it up like before?:-k

You can use **gconf-editor** to see what the value is.

---

### Post by cdude on 2009-04-14
> **cariboo907 said:**
> I'm an update junky, I usually update at least 3 times a day. I haven't seen the new update notification yet. :)

Jim

Same here, in fact I thought the update notification was broken.:D

---

### Post by melalcoolique on 2009-04-14
Err, i voted yes but i meant no.

---

### Post by MacUntu on 2009-04-14
I've enabled the old behaviour and hope we will see a better solution for this in Karmic than in Jaunty.

> **melalcoolique said:**
> Err, i voted yes but i meant no.

That's actually not your fault. ;)

---

### Post by zorkerz on 2009-04-14
So I finally got the new update manager behavior for the first time. i.e. it just opens out of nowhere. I must say its a little odd I think many people will not know why its there and just close it in which case I think an updates available icon should be put in the notification area like it used to. In the long run I think I would like update manager to integrate with notify-osd. A bubble would popup saying you have updates (critical or not) and then to open update manager you would click on the indicator-applet icon and select update manager it open it.

---

### Post by xeddog on 2009-04-14
You're still getting update notifications???   I haven't received any notifications for weeks.  I have to Start>Administration>Update Manager to get all of my updates.

xeddog

---

### Post by zorkerz on 2009-04-14
Yesterday I set  /apps/update-notifier/regular_auto_launch_interval to 0 in gconf-editor so that update manager opens immediately it is aware of any updates. It took me until today for update manager to open on its own (during this time there were some updates Im assuming update manager did not open for them because It had not autochecked for updates yet which only happens once a day). 

Its not really a notification the update manager window just opens. Thats why I would like integration with notify-osd and or the old icon in the notification area.

---

### Post by timzak on 2009-04-14
I haven't seen an update notification yet either.  I installed Jaunty about a week ago.  This morning I purposely held off running Update Manager manually to see if anything would pop up.  After about an hour, nothing happened so I ran manually and it came up with half a dozen updates or so.

---

### Post by zorkerz on 2009-04-14
If none of them were critical updates the new default is for update manager to wait 7 days and then popup. This behavior at first seems pretty odd but there are potentially some upsides discussed above in getting users to actually install the updates.

---

### Post by Old Marcus on 2009-04-14
I agree. It's no wonder MS set Windows updates to auto, as your average computer user is too lazy to bother updating themselves.

---

### Post by sistoviejo on 2009-04-14
I have switched back because I hate pop unders. 
That's what MS Windows spyware does and I hate it quite a bit.

---

### Post by erktrek on 2009-04-15
Like others in this thread I never received any notifications that I remember since the update to Jaunty so am not sure about the behavior. 

I really like the "old" update icon in the notification area tho. Informative without being too intrusive. Allows me to quickly update or ignore if needed. 

In my experience (with a small but growing Ubuntu client base) a small percentage actually ignore the alerts but ALL of them know what it is for..

So yes I switched it back and voted same.

Now get off my lawn dammit!

8-)

---

### Post by hufferd on 2009-04-15
> **ktp said:**
> Wondering how many people are using the default update notification system, which will popup update manger a day after for security updates or seven days for regular updates.  Or people have changed back to old notification icon using gconf option.
```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```  Do you find the notification icon confusing?

I went back to the old way like it much better

---

### Post by Copernicus1234 on 2009-04-15
> **cariboo907 said:**
> I'm an update junky, I usually update at least 3 times a day. I haven't seen the new update notification yet. :)

Jim

Me too. ;) In fact, Im updating right now..

---

### Post by zorkerz on 2009-04-15
I think the reason people are not seeing the update manager behavior is because we all update so much.

The fastest you can set ubuntu to check for updates is "daily". There are many things this could mean please explain if anybody has some insight. It could check for updates in the following ways that I can think of.
- first time the computer is on each day
- once each time the computer is turned on
- at a specific time each day (skipping if the computer is off or checking if the time is missed)

I know for me to get the update manager to pop up on its own I had to turn all updates to open update manager immediately and wait an entire day.

---

### Post by FraggedLocust on 2009-04-15
If I understand correctly, notify-osd is called by update notifier which passes update information to the notifier, and we are discussing why the update notifier only runs once a week? 

Personally, I enjoy the new notification icons, though i would like to size them down a bit. They seem a little intrusive to me, whereas when Mark S. envisioned them in his blog, he commented that they would be unintrusive. It's not the speed or act in which they notify, which I assume is what he was trying to emphasize, but it still bugs me.

As for the updates themselves, I'm quite happy with editing the key to change the frequency of notifications. As for the other people who aren't, wouldn't it be 'easy' to link a graphical element like a textbox to that frequency key and have the value update on apply?

---

### Post by sistoviejo on 2009-04-15
> **Simian Man said:**
> This poll is ill-formed because the thread title is "Are you using the new update notification" and the poll title is "Have you changed the update notification back to old notification icon?"

So basically they are asking opposite things which is confusing.  I wouldn't be surprised if a few people voted the wrong way.

I have posted a new poll to solve this issue.
[http://ubuntuforums.org/showthread.php?t=1126460](http://ubuntuforums.org/showthread.php?t=1126460)

---

### Post by Benbow on 2009-04-15
Until I read this thread I didn't know of the "new system" and I couldn't understand why I had to go into update manager to get my updates. I do now and am about to change back to the old system. I think that besides causing confusion with existing "slightly non-technical" users (moi!) it will cause untold difficulties with people who are new to Ubuntu.

---

### Post by tawmas on 2009-04-15
> **zorkerz said:**
> I think the reason people are not seeing the update manager behavior is because we all update so much.

The fastest you can set ubuntu to check for updates is "daily". There are many things this could mean please explain if anybody has some insight. It could check for updates in the following ways that I can think of.
- first time the computer is on each day
- once each time the computer is turned on
- at a specific time each day (skipping if the computer is off or checking if the time is missed)

I know for me to get the update manager to pop up on its own I had to turn all updates to open update manager immediately and wait an entire day.

As far as I can tell, the download is scheduled via anacron, which means it will check at the first possible occasion after midnight. Which is right at midnight if the PC is on, or on first boot otherwise. Once it has checked, it won't check again until another midnight.

This also means that if you turn on your PC for the first time at 11.50 PM, it will check twice in about ten minutes, then go to sleep for 24 hours at least.

This is how updates are checked for availability, irrespective of how you choose to have updates notified to you.

Under the old system, an icon appears in the tray as soon as the check is finished, if there are updates available.

Under the new system, Update Manager pops up if there are updates available AND no updates were done (manually or otherwise) in the last 7 days, or whichever interval you configure.

---

### Post by ktp on 2009-04-15
> **tawmas said:**
> As far as I can tell, the download is scheduled via anacron, which means it will check at the first possible occasion after midnight. Which is right at midnight if the PC is on, or on first boot otherwise. Once it has checked, it won't check again until another midnight.

I think this is exactly how it works.

---

### Post by fluffynuts on 2009-04-20
Far be it for me to be a UI nazi and dictate how everyone likes their machine to run. It seems that position is already taken  ;p

I, for one, welcomed the original update-notifier with it's little vibrant icon. It was one of the enticing factors that kept me with Ubuntu after years with Debian (that and the fact that Ubuntu actually has regular release cycles and is made in my home land  (:  ). It beat the heck out of popping a term and doing an apt-get update && apt-get upgrade every day. It was actually MORE convenient (and looked nice -- very professional).

I upgraded to Jaunty (actually, for once, just installed new, but that's a long story; suffice to say that I've taken the upgrade path for well over 3 generations of Ubuntu that I can definitely remember, and have been using Ubuntu since Warty) and was a little confused (hey, it's still in RC status!) that there were no updates after a day or two. I manually ran "update-manager -c" and found a plethora of updates! Double-you tee effe! Why did I have to find out the hard way that my system was lying by omission?

The current default behaviour means that security updates are left for as long as 2 days (hey, I want them as soon as I can get them) and updates which are deemed non-critical to some (but which may, as has happened in the past, fix some annoying, daily-occurring bug for me or someone else) are left for up to seven days? Then update-manager is to be automatically launched in the background? Or so I've been told -- haven't seen it happen, to be honest. Perhaps because I've only been on Jaunty for about 4 days...

The behaviour that is supposed to be in effect at the moment is disturbing on a number of levels:
1) I don't actually get a daily notification of updates, DESPITE what the UI of Synaptic suggests that I will (I don't even need to screenshot again, someone has this blatant lie in digital format already: [http://ubuntuforums.org/picture.php?albumid=1043&pictureid=3695](http://ubuntuforums.org/picture.php?albumid=1043&pictureid=3695))
2) I am forced to either accept the timescale that upstream has chosen for me (despite having obviously chosen a timescale of ONE DAY myself) between potential updates, or fall back to the manual, terminal-based approach (which I would do if I were on a server, but I'm not -- this is a desktop, and I like apps which play nice in a desktop environment)
3) I don't know if there is a notification in the shiny new notification system? Even if there was: my machine is on all day -- whilst I'm not here. Some things DO require a persistent notification, Mr Shuttleworth. Updates to critical components and bugfixes make it into that category if you ask me.
4) You want to launch an application at the whim of the OS? This sounds even more annoying than Windows Updates. Hang on -- IT IS. Redmond, for all its faults, at least has this process in a fairly friendly state: notify via an icon in a notification area which the user will see whenever she next sits at her machine, and can respond to on her terms. This is not rocket science -- it's just not all that hip and cool for the youngsters, apparently.

Ok, so the behaviour can be reverted via gconftool or gconf-editor. NOT GOOD ENOUGH. This is not clear at all. What happened to the GNOME ethos of keeping things simple and clear? This, quite simply, is not clear. 

If someone were to ask (and I doubt they will, but I'll persevere nonetheless), IMHO, the right thing to do would be to make an option available in Synaptic, perhaps near the option where I chose to have daily notifications? Or, how about this: just respect the user's choice for daily notifications? Have another choice which says something like "Automatically start update manager when the system deems the update worthwhile". This would be a more apt description for the current behaviour.

Like I say, I'm no UI nazi. I love that one of the strengths of the Linux world is the diversity. I can see from the poll that a little over half of the surveyed people haven't reverted the update-manager behaviour. How many of these simply haven't done so because they can't be bothered, are too scared to mess with gconf, don't know how to do the change (before there were instructions) or simply didn't notice a difference, who can tell -- that is, after all, how another major OS has managed to proliferate across the globe: most people just can't be bothered to reload with something better. Still, I stick by my guns: if people are finding the new behaviour useful and/or intuitive, then, by all means, retain it. But please respect the other half of the user base who actually liked the way that it used to work. Put an option into Synaptic (or elsewhere, but Synaptic would make the most sense).

---

### Post by rajeev1204 on 2009-04-21
I agree with you . Its a lie that they check for security updates daily, and if they do i aint seeing it.

I have reverted back to the old behaviour but iam yet to see the icon appear on its own.

This is a no brainer really, and as far as the new notify osd is concerned, i havent seen it tell me of any updates yet on its own unless i manually start update manager.

2 dumb decisions

Disable ctl alt backspace
and disable update notifier icon

Iam going back to hardy.

---

### Post by go7Ul1ai on 2009-04-21
> **rajeev1204 said:**
> I agree with you . Its a lie that they check for security updates daily, and if they do i aint seeing it.

I have reverted back to the old behaviour but iam yet to see the icon appear on its own.

This is a no brainer really, and as far as the new notify osd is concerned, i havent seen it tell me of any updates yet on its own unless i manually start update manager.

2 dumb decisions

Disable ctl alt backspace
and disable update notifier icon

Iam going back to hardy.

You are going to go back to 8.04 just because of two problems (that can be fixed or at least there is work arounds..)?

---

### Post by rajeev1204 on 2009-04-21
> **lee.jarratt said:**
> You are going to go back to 8.04 just because of two problems (that can be fixed or at least there is work arounds..)?


I dont like versions which implement features which are against user opinion.Especially when it looks like a regression or a bug which they call a feature.Also,i dont like dirty fixes or workarounds.

But ,Heron worked well for me and i had fewer issues with it so i want to go back to it.Had no complaints with it.So no problems vs 2 problems , which is better you tell me.

And btw, what is so great about jaunty? So called faster boot times? It still takes the same time to reach the desktop for me.

In fact, just before i started typing my X crashed and hey ! no ctl alt backspace!

The long bug reports about these features (bugs?) says enough.

---

### Post by go7Ul1ai on 2009-04-21
> **rajeev1204 said:**
> I dont like versions which implement features which are against user opinion.Especially when it looks like a regression or a bug which they call a feature.Also,i dont like dirty fixes or workarounds.

But ,Heron worked well for me and i had fewer issues with it so i want to go back to it.Had no complaints with it.So no problems vs 2 problems , which is better you tell me.

And btw, what is so great about jaunty? So called faster boot times? It still takes the same time to reach the desktop for me.

In fact, just before i started typing my X crashed and hey ! no ctl alt backspace!

The long bug reports about these features (bugs?) says enough.

Let me answer your questions one at a time..


No problems versus 2 problems, well the answer to that is obvious, but after these "quick or dirty fixes", the advantages outweigh the disadvantages.

What is so great about Jaunty? Yes the faster boot times; you might not have noticed the faster boot times which could be because of various reasons, you're not using the ext4 filesystem, you upgraded instead of doing a fresh install, or it's just your hardware, I don't know.. but the times are a lot better than Intrepid and earlier, well many people think so anyway.

The other things I like about Jaunty is notification-osd, updated packages, the new artwork, GNOME 2.26.0, the general improvements made to Ubuntu and more.

Have a nice day Sir.

---

### Post by rajeev1204 on 2009-04-21
> **lee.jarratt said:**
> Let me answer your questions one at a time..


No problems versus 2 problems, well the answer to that is obvious, but after these "quick or dirty fixes", the advantages outweigh the disadvantages.

What is so great about Jaunty? Yes the faster boot times; you might not have noticed the faster boot times which could be because of various reasons, you're not using the ext4 filesystem, you upgraded instead of doing a fresh install, or it's just your hardware, I don't know.. but the times are a lot better than Intrepid and earlier, well many people think so anyway.

The other things I like about Jaunty is notification-osd, updated packages, the new artwork, GNOME 2.26.0, the general improvements made to Ubuntu and more.

Have a nice day Sir.

Ext4 is not the default and wont even make it to karmic.Why should i even try it?Actually it does boot quick but its due to the newer kernel.Ext4 is faster yes but jaunty overall will boot faster with ext3 too.But my system slows down when loading X.

As far as artwork is concerned,take a look again at the heron wallpaper then come back.

Which other artwork? Still looks the same doesnt it.New theme will be in only in karmic.Dont tell me looking at a slim usplash makes your day.

Ill agree theoretically every update brings newer packages so ill go with you on that one ,which is also why i upgrade.

Dont want to sound too negative,but notify osd is a copy of the mac.

Ill try having a nice day,thanks and you too. :).

---

### Post by Incognito-Here on 2009-04-21
Wallpaper is horrible, the big regression since Hardy and Intrepid. GDM is amateurish and also horrible.

---

### Post by go7Ul1ai on 2009-04-21
> **rajeev1204 said:**
> Ext4 is not the default and wont even make it to karmic.Why should i even try it?

As far as artwork is concerned,take a look again at the heron wallpaper then come back.

Which other artwork? Still looks the same doesnt it.New theme will be in only in karmic.Dont tell me looking at a slim usplash makes your day.

Ill agree theoretically every update brings newer packages so ill go with you on that one ,which is also why i upgrade.

Dont want to sound too negative,but notify osd is a copy of the mac.

Ill try having a nice day,thanks and you too. :).

You can't complain about the faster boot times that you aren't going, when you're not trying the new technologies that help improve the speeds from boot to desktop.

I've had a look at the Hardy Heron wallpaper back when I was using, yes I loved it just as much as the next person but when I say "artwork" I don't just mean the desktop background.. I was also talking about the themes included in this release, now every time I install Ubuntu (I have an OCD and have to format & re-install regularly.. Sad, I know..) I don't have to install the community-themes package anymore, saves another minute of my time. And I do actually like the new usplash theme, it's pretty nice, so is the new GDM theme and the overall look (including the look of the notifications).

Notify-osd is a copy of the mac? Darn, workspace switching is a copy of Linux.. In this world and day & age, everyone copies off everyone to keep up.

---

### Post by ktp on 2009-04-21
notify-osd might look nice, but it has its own issues.

---

