---
title: "What on earth were the &quot;Desktop Experience&quot; team thinking?"
date: 2009-02-18
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by bruce89 on 2009-02-18
There was a large influx of things the "Desktop Experience" team came up with today:

[LIST]
[*]Replacing notification-daemon with a different daemon
[*]Auto-launching update-manager every 2 days
[*]Indicator applet
[/LIST]

The new notification daemon displays notifications in a black box which looks really ugly when compositing is off, and not much better when it is on.

Update Manager now appears without warning every 2 days. This is completely barmy.

The indicator applet plan is to get rid of all applets in the notification area, and replace them with one. Clearly upstream had no input on this decision.

I have been using Ubuntu for 4 years, and I have never seen changes this bad.

---

### Post by OliW on 2009-02-18
I'm not saying any of the changes are particularly well executed at the moment, but this is alpha software! I think it's fair to say that what you see today isn't going to be what you see in a couple of month's time.

And I'd rather they played around with this stuff rather than leaving everything stagnating. So yes, all in all, I think these changes are completely reasonable.

If they were pushed out to II users, that would be another matter.

---

### Post by castrojo on 2009-02-18
> **bruce89 said:**
> 
Update Manager now appears without warning every 2 days. This is completely barmy.

Do you really think that's expected behavior? Calm down, it's not finished.

---

### Post by bruce89 on 2009-02-18
> **whiprush said:**
> Do you really think that's expected behavior? Calm down, it's not finished.

I assumed it was when I saw the line in the changelog:
```

  * make "auto_launch" update-manager mode the default (as asked
    for by the DX team)
```

I also get a bit excited about this sort of thing, but looking back at the other development versions, equally mad stuff was trialled in them (and then got rid of).

---

### Post by pferraro on 2009-02-18
What is this black box the poster mentioned?  I'm not seeing anything of this sort.  For example, when evolution triggers new mail notifications, I actually get a pop up window now (with ok, cancel buttons).  All of my other notifications seem to get swallowed, e.g. wireless connection established, vpn connection established, etc.  Adding the indicator applet to the panel does seem to do anything either.

---

### Post by philinux on 2009-02-18
My software sources still says update daily as before.

---

### Post by inportb on 2009-02-18
C'mon over to KDE; the grass is greener on this side. I'm lovin' the improvements ;)

---

### Post by rockin_goliath on 2009-02-18
Could we have a screenshot of the ugliness, both with compositing on and off?

---

### Post by bruce89 on 2009-02-18
> **pferraro said:**
> What is this black box the poster mentioned?  I'm not seeing anything of this sort.  For example, when evolution triggers new mail notifications, I actually get a pop up window now (with ok, cancel buttons).  All of my other notifications seem to get swallowed, e.g. wireless connection established, vpn connection established, etc.  Adding the indicator applet to the panel does seem to do anything either.

The new notification daemon, I forget what its name is.

> **inportb said:**
> C'mon over to KDE; the grass is greener on this side. I'm lovin' the improvements ;)

No, this is not GNOME's fault, it's Ubuntu's.

I've even managed to grab Mark Shuttleworth's attention on the bug I filed about not autolaunching ([https://bugs.edge.launchpad.net/ubuntu/+source/update-notifier/+bug/331054](https://bugs.edge.launchpad.net/ubuntu/+source/update-notifier/+bug/331054)).

---

### Post by Simian Man on 2009-02-18
Hopefully, like the new theme they talked about, they will never get it completed.

---

### Post by kurros on 2009-02-18
Will link to Mark's post on this back in December explaining the reasoning for this experiment for those that missed it.

And it is in an experiment guys. A work in progress one. Non inflammatory feedback welcome and all.

[http://www.markshuttleworth.com/archives/253](http://www.markshuttleworth.com/archives/253)

---

### Post by bruce89 on 2009-02-18
> **kurros said:**
> Will link to Mark's post on this back in December explaining the reasoning for this experiment.

And it is in an experiment guys. A work in progress one. Non inflammatory feedback welcome and all.

[http://www.markshuttleworth.com/archives/253](http://www.markshuttleworth.com/archives/253)

I think that it should be left for GNOME themselves to dictate this sort of thing.

---

### Post by inportb on 2009-02-18
> **bruce89 said:**
> No, this is not GNOME's fault, it's Ubuntu's.

This may be so... however, the Ubuntu guys have done lots of *right* things regarding the kubuntu-desktop variety. Notice how I'm not finding fault with anyone here.

---

### Post by amano on 2009-02-18
> **inportb said:**
> C'mon over to KDE; the grass is greener on this side. I'm lovin' the improvements ;)

And the trolls are much more vibrant. They even had a company called Trolltech (before selling out to Nokia). Now we know, how they got choosing that name :p


And in the case of notifications the truth is that it will hit (or did already hit?) Kubuntu as well. Just stay tuned.

---

### Post by amano on 2009-02-18
> **bruce89 said:**
> I think that it should be left for GNOME themselves to dictate this sort of thing.

GNOME upstream will look at how this works out in Ubuntu before deciding on this notifications re-design. Thus GNOME decided NOT to make any decision now.

---

### Post by Mr. Picklesworth on 2009-02-18
I'm all for rethinking notifications, and I really hope Canonical's fix doesn't just perpetualizing the breakage.

We Need A Centralized Application Summary System. Think Telepathy for notifications. The window list, system tray, and notification bubbles all spouting in to a single organized tool. They provide the same general information, so if one tool handles it all we avoid redundancy and can generate really rich, at a glance "what is happening" type information for the user. Not just "what windows are open" in one place and "who chooses to speak in system-tray-ese today," but "who just said something on Twitter, whether that document is downloaded, what is consuming all the resources..." that kind of stuff.

I get the feeling that what they are doing could go both ways, because it *isn't* a full solution; more a bumper that will hopefully push developers in the right direction toward building a more cohesive solution.

As for it looking ugly, have faith folks. It's a WIP.

---

### Post by no1wantdthisname on 2009-02-18
> **pferraro said:**
> What is this black box the poster mentioned?  I'm not seeing anything of this sort.  For example, when evolution triggers new mail notifications, I actually get a pop up window now (with ok, cancel buttons).  All of my other notifications seem to get swallowed, e.g. wireless connection established, vpn connection established, etc.  Adding the indicator applet to the panel does seem to do anything either.

Try changing the volume via keyboard shortcut.  I think it's a good change.

---

### Post by Mr. Picklesworth on 2009-02-18
Indeed, I am loving the volume indicator. That is one beautifully natural progression :)

Running it in a VM so can't tell... is the screen brightness indicator like that, too, or still its own beast?

---

### Post by mc4100 on 2009-02-18
> **no1wantdthisname said:**
> Try changing the volume via keyboard shortcut.  I think it's a good change.
Doesn't seem to work with metacity (with compositing enabled), but does with compiz.

---

### Post by no1wantdthisname on 2009-02-18
> **Mr. Picklesworth said:**
> Indeed, I am loving the volume indicator. That is one beautifully natural progression :)

Running it in a VM so can't tell... is the screen brightness indicator like that, too, or still its own beast?

Brightness is still using the old indicator.

You can also test using notify-send.

> **mc4100 said:**
> Doesn't seem to work with metacity (with compositing enabled), but does with compiz.

Also works fine without compositing.

---

### Post by mc4100 on 2009-02-18
Try turning on Rhythmbox notifications as well, looks great:

---

### Post by MadsRH on 2009-02-18
Can anyone tell me why I can get it working? :(

I installed all updates and tried notify-send, but I still get the same old notification.

---

### Post by bruce89 on 2009-02-18
> **mc4100 said:**
> Doesn't seem to work with metacity (with compositing enabled), but does with compiz.

Therein lies the problem.

I don't mind the notification thing quite as much, but I'd rather the work was done upstream.

---

### Post by mc4100 on 2009-02-18
> **MadsRH said:**
> Can anyone tell me why I can get it working? :(

I installed all updates and tried notify-send, but I still get the same old notification.

Updating ubuntu-desktop installed a new package 'alsdorf', is this installed?
> The Desktop Notifications framework provides a standard way of doing
passive pop-up notifications on the Linux desktop.  These are
designed to notify the user of something without interrupting their
work with a dialog box that they must close.  Passive popups can
automatically disappear after a short period of time.

---

### Post by MadsRH on 2009-02-18
Thanks for the reply mc4100

ubuntu-desktop is version 1.133. I don't know about the new package 'alsdorf'?

---

### Post by mc4100 on 2009-02-18
> **MadsRH said:**
> Thanks for the reply mc4100

ubuntu-desktop is version 1.133. I don't know about the new package 'alsdorf'?
I'm at 1.134, seems like you just need to wait a while (are you using a mirror?)

---

### Post by MadsRH on 2009-02-18
> **mc4100 said:**
> I'm at 1.134, seems like you just need to wait a while (are you using a mirror?)

Yes, that was it ;)


Thanks :D (*Now where is that thank you button!*)

---

### Post by chrisccoulson on 2009-02-18
My understanding is that update-manager will only autolaunch every 2 days when there are updates. Whilst this may be irritating during a development release, there will not be updates every 2 days once Jaunty is released. This change is not so bad really, and if you don't like it, you can just disable it in gconf-editor. It won't be that disruptive once Jaunty is final though.

I like the new notifications. The volume and Rhythmbox pop-ups look beautiful on my system. They're in the wrong corner for me though (I have my notification applet on the bottom panel, which is where I prefer all my pop-ups to appear), so that is probably a bug

---

### Post by bruce89 on 2009-02-18
> **chrisccoulson said:**
> My understanding is that update-manager will only autolaunch every 2 days when there are updates. Whilst this may be irritating during a development release, there will not be updates every 2 days once Jaunty is released. This change is not so bad really, and if you don't like it, you can just disable it in gconf-editor. It won't be that disruptive once Jaunty is final though.

Having a window appear (apparently it's not supposed to be in the background) at all is disruptive and confusing.

---

### Post by philinux on 2009-02-18
> **mc4100 said:**
> Try turning on Rhythmbox notifications as well, looks great:

Mines still using the old notification area for rhythmbox.

---

### Post by chrisccoulson on 2009-02-18
> **bruce89 said:**
> Having a window appear (apparently it's not supposed to be in the background) at all is disruptive and confusing.

If you read Mark's response in the bug you reported, you'll see that it is actually meant to be opened in the background

---

### Post by TaTaE on 2009-02-18
For the current state of Ubuntu desktop, ANY CHANGE IS REASONABLE.

---

### Post by TaTaE on 2009-02-18
For the current state of ubuntu desktop, ANY change is reasonable. I'm waiting for the jaunty, hardy, feisty, edgy desktop. It is still not here.

---

### Post by Chrisj303 on 2009-02-18
> **TaTaE said:**
> For the current state of Ubuntu desktop, ANY CHANGE IS REASONABLE.

^THIS.

I hope there are many more releases from these guys for 9.04.

---

### Post by rockin_goliath on 2009-02-18
I am VERY impressed with the Rhythmbox notification. I think this is a positive change, much better than those beige boxes. With a bit more work, I think it will look fantastic across all notifications and give something for Windows/Mac users to be jealous over.

---

### Post by Eclipse. on 2009-02-18
Remember the feature freeze is tomorrow so everything thats going to ship has to be there (working or not), bug fixing now becomes the main priority now so I wouldnt worry yet.

---

### Post by bruce89 on 2009-02-18
> **chrisccoulson said:**
> If you read Mark's response in the bug you reported, you'll see that it is actually meant to be opened in the background

That's not the point, especially if you don't have any windows displayed at the time.

> **Eclipse. said:**
> Remember the feature freeze is tomorrow so everything thats going to ship has to be there (working or not), bug fixing now becomes the main priority now so I wouldnt worry yet.

That explains the sudden rush of half-baked ideas.

---

### Post by inportb on 2009-02-18
> **amano said:**
> And the trolls are much more vibrant. They even had a company called Trolltech (before selling out to Nokia). Now we know, how they got choosing that name :p

And in the case of notifications the truth is that it will hit (or did already hit?) Kubuntu as well. Just stay tuned.

It has already hit -- KDE has a very nice unified notification system. It has been polished thoroughly since its early/buggy introduction. It would be great if this could be implemented within the Ubuntu/Gnome desktop environment.

Call me a troll if you want; kubuntu-desktop is as much a part of the Ubuntu project as the rest of Ubuntu is, so the discussion is valid.

---

### Post by MacUntu on 2009-02-18
As long as I can turn it off it's great! :)

---

### Post by sirdilznik on 2009-02-18
> **MacUntu said:**
> As long as I can turn it off it's great! :)

That's my feeling too.  **If** I were to upgrade to Jaunty my first step would be to disable update-manager or better yet, rip it out all together.  That being said I probably won't upgrade to Jaunty at all since my only reason would be to give btrfs a try and since Jaunty is sticking with 2.6.28 then it looks like I'll be sticking with Intrepid and giving Fedora 11 a spin on a separate partition for s*its & giggles.

---

### Post by PRGUY85 on 2009-02-18
I am right now updating my Ubuntu Jaunty distro so I will talk about that soon.  Yet, I would also like to give a shoutout to the Kubuntu Jaunty current state desktop.  The notification system is great and unified as well.  IM, system notifications, everything works off the same applet.  I am a Gnome guy but KDE 4.2 is consistently making me consider the KDE route for the next 6 months.

---

### Post by Eclipse. on 2009-02-18
> **bruce89 said:**
> 
That explains the sudden rush of half-baked ideas.

Its not been a "sudden rush" the notification system has been in the wings for a few months now, infact I can remember Mark showing it off on his blog (prototype).At this stage of development things are not expected to work without problems, if they did I dare say I would be more bothered.Jaunty is not due for anohter 2 months, only if these features are half-baked at that point would I be worried.

---

### Post by mpt on 2009-02-18
Hi, I&#8217;m from Canonical&#8217;s Design team, the people responsible for the design of the new [Notify OSD]("https://launchpad.net/notify-osd") notification system. (So don&#8217;t blame the Desktop Experience team &#8212; they just did the implementation. ;))

_[bruce89]("http://ubuntuforums.org/showpost.php?p=6755592&postcount=1")_: Rest assured that Update Manager will not open by itself every two days in Ubuntu 9.04! In 9.04, when security updates are issued, Update Manager will display these within a day; for other updates, though, it will open *at most* once per week.

We recognize this is a bit awkward for those of you testing Jaunty during its development, because if you were installing updates only once a week, your testing wouldn&#8217;t be nearly as useful. So the frequency is set to once every two days during Jaunty development. It will be changed to once a week just before 9.04 is released.

_[pferraro]("http://ubuntuforums.org/showpost.php?p=6755852&postcount=5")_: Evolution&#8217;s alert boxes are temporary. _[We plan]("https://wiki.ubuntu.com/NotifyOSD#Evolution")_ to integrate Evolution with a message status menu that provides quick access to new mail and instant messages from Evolution, Pidgin, and other programs.

pferraro and _[mc4100]("http://ubuntuforums.org/showpost.php?p=6756549&postcount=19")_: you&#8217;re probably not getting the bubbles you expect because Notify OSD _[doesn&#8217;t work yet with Metacity composited]("http://launchpad.net/bugs/323101")_.

_[bruce89]("http://ubuntuforums.org/showpost.php?p=6756273&postcount=12")_:
> I think that it should be left for GNOME themselves to dictate this sort of thing.

Who do you mean by &#8220;GNOME themselves&#8221;, exactly? Do you mean that Ubuntu&#8217;s graphical software should be developed by Red Hat, Novell, Sun, Imendio, etc, and by volunteers, but not by Canonical? That would be very strange. Others have complained in the past that Canonical should do *more* upstream development, and now we are.

_[Mr. Picklesworth]("http://ubuntuforums.org/showpost.php?p=6756473&postcount=16")_:
> We Need A Centralized Application Summary System. Think Telepathy for notifications. The window list, system tray, and notification bubbles all spouting in to a single organized tool.

That&#8217;s an interesting idea, but we think it&#8217;s not really appropriate, for a couple of reasons. First, it would be clumping notifications about completely different things, with completely different priorities, together into a single list as if they&#8217;re related when they&#8217;re not. (This was also the main problem with _[Mathusalem]("http://live.gnome.org/Mathusalem")_.) And second, many of the tasks that generate notifications (e-mail, instant messaging, downloads) already have their own dedicated lists that present items much better than a generalized interface could.

> I get the feeling that what they are doing could go both ways, because it isn't a full solution; more a bumper that will hopefully push developers in the right direction toward building a more cohesive solution.

Indeed, notification bubbles aren&#8217;t &#8212; and shouldn&#8217;t be &#8212; the only mechanism for notifying people of things. (They&#8217;ve been a bit overused in Gnome up till now.) I&#8217;ve written some _[design guidelines]("https://wiki.ubuntu.com/NotificationDesignGuidelines")_ on which mechanism to use in different situations.

_[bruce89]("http://ubuntuforums.org/showpost.php?p=6756656&postcount=23")_:
> I don't mind the notification thing quite as much, but I'd rather the work was done upstream.

We *are* the upstream for this work.

Finally, it&#8217;s good to see that _[most of you like the changes]("http://ubuntuforums.org/poll.php?do=showresults&pollid=4714")_. But keep in mind that Notify OSD is still under heavy development, so you can expect it to become more refined over the next few weeks. Thanks for your comments!

---

### Post by PRGUY85 on 2009-02-18
After update, I see Rhythmbox notifications but the Volume indicator only shows the black glossy box and nothing inside.

@ MPT :  IT's great to have a member of the team come here and discuss it with the testers and early adopters.  Keep up the good work.  I prefer innovation to a stable system right now.  If not I would be using 8.10 still.

---

### Post by go7Ul1ai on 2009-02-18
Loving the new notification system so far.. Any chance it will work with Banshee (as it is my preffered player).

Lee

---

### Post by medeshago on 2009-02-18
I also love the new notifications, but my main problem is pidgin:
[ATTACH]103817[/ATTACH]
fugly.

---

### Post by PRGUY85 on 2009-02-18
medeshago: MTP said they were still working on Pidgin integration so my guess is it will be complete before release.

---

### Post by go7Ul1ai on 2009-02-18
> **medeshago said:**
> I also love the new notifications, but my main problem is pidgin:
[ATTACH]103817[/ATTACH]
fugly.

This also happens when Banshee goes to the next song.

Lee

---

### Post by Jay_Bee on 2009-02-18
I guess that is how the system handles notifications with actions.
Same happens when network manager connects/disconnects.
All those apps will probably need to be patched in the following weeks.

---

### Post by PRGUY85 on 2009-02-18
Right now I have seen the following using the latest updates and new notification system:

-Rhythmbox track changes 
-Gnome-Do notifications (like new Twitter posts)
-Volume Indicator (black box but nothing on right now for me)

I haven't seen anything from Pidgin, Network Manager or Power Management on the new notification system.  Is it my configuration?  I know the volume empty box is specific to me since I have seen other users post pics of the new volumen indicator on notification black bubbles.

---

### Post by andrewsomething on 2009-02-19
Just to put this into perspective... The entire idea behind the new notification system is that notifications should be ephemeral. They should be used for things like a song change or email coming in. Things that you want to be simply "notified" about. You then can take action on them if you want, but the notifications shouldn't get in the way of what you are doing at the moment. If the system is telling you something that is important enough that you really should do something about it (either acknowledge and put off till later or take action at that moment), then it should use a dialog.

Until now, update-manager had been using notifications that have actions in them. Now it will show the window. Either way, if you don't use update manager at all, I would think this is annoying. You should just turn it off. The reality is that the vast majority of Ubuntu users do use update-manager. As keeping your system up-to-date is important, I think it is valid to put something in the users face every once and awhile. With the new notification system, if a notification of an update were to pop up while you are away from the computer it would disappear in seconds never to be seen again. So a solution was needed. Might not be the best fix, but that's what alphas are for. To try this all out...

The whole thing really points to the exact problem with the old notification system (besides not being very pretty). There was never any real coherent way it was used across different applications. Many different applications used notifications differently. This is an attempt to set up a unified way for desktop apps to work and feel.

---

### Post by loell on 2009-02-19
> **andrewsomething said:**
>  I think it is valid to put something in the users face every once and awhile. 


I agree, but updates aren't once in a while thing. 

while **mpt** said > it will open at most once per week

will there be an assurance that this will be consistent?  i mean who gets to decide that there will be no updates for this week because we already did it twice or thrice and deploying another will most likely be annoying?

---

### Post by Jay_Bee on 2009-02-19
> **PRGUY85 said:**
> I know the volume empty box is specific to me since I have seen other users post pics of the new volumen indicator on notification black bubbles.
I get that too so it's not just you.

---

### Post by carlholmberg on 2009-02-19
I would argue that information like new email-messages should be more like it is on Mac OS X. Don't tell me -- if I want to know I just look at the icon.

With this new system it would tell me but if I wasn't paying attention just then I wouldn't know I've gotten a new message until i check my email-application. Kind of useless because email isn't irc... And who needs to know that the song has changed in my musicplayer -- I'm not deaf...

I feel that this is trying to fix something without enough background on what's really important, what use cases there are and without a solid scientific foundation. I remember reading a blog post from a KDE-UI-designer/developer that argued, with support from current scientific papers, that the rationale for the implementation was flawed and that more work needs to be done. Url: [http://weblog.obso1337.org/2009/response-to-the-proposed-canonical-notification-system/]("http://weblog.obso1337.org/2009/response-to-the-proposed-canonical-notification-system/")

I don't think this will be the envy of Mac OS X and Windows users unless it actually provides added usability and productivity and not just bling.

---

### Post by olskar on 2009-02-19
> **no1wantdthisname said:**
> Try changing the volume via keyboard shortcut.  I think it's a good change.

That looks very nice indeed, good work to whom ever responsible!

---

### Post by TrueTom on 2009-02-19
How do you disable this crap anyway?

Every time a song changes in Banshee a dialog pops up with "Skip element", "Cancel" and "Ok"...

---

### Post by MacUntu on 2009-02-19
> **carlholmberg said:**
> if I want to know I just look at the icon
Icons aren't intuitiv. Interpreting icons is something you have to learn. Trying different approaches doesn't hurt so why don't let the devs complete their work and judge then?

[Again: I don't like it and I don't want it, but that doesn't mean it's bad.]

---

### Post by Starks on 2009-02-19
Wow.

The apport reminder is non-X'able.

**HOW ****ING ANNOYING!**

---

### Post by kurros on 2009-02-19
> **Starks said:**
> Wow.

The apport reminder is non-X'able.

**HOW ****ING ANNOYING!**


They are all "non X-able". that is the point. Apport still needs to be updated (I assume its a candidate for indicator-applet)

---

### Post by Starks on 2009-02-19
> **kurros said:**
> They are all "non X-able". that is the point. Apport still needs to be updated (I assume its a candidate for indicator-applet)

1 flash per error = 100+ flashes for a buggy jaunty install

---

### Post by son on 2009-02-19
> **PRGUY85 said:**
> 
I know the volume empty box is specific to me since I have seen other users post pics of the new volumen indicator on notification black bubbles.
It's not only you. I have empty black boxes for volume control, brightness, power events (at least). 

And I'm expecting notify-send to provide popup bubbles similar to the old notification-daemon, which is not the case actually.

---

### Post by Starks on 2009-02-19
Will the policykit prompts (ie: synaptic asking for your password) be a part of the new desktop experience?

---

### Post by olskar on 2009-02-19
> **Starks said:**
> Will the policykit prompts (ie: synaptic asking for your password) be a part of the new desktop experience?

Good idea, that would certainly be desirable

---

### Post by plun on 2009-02-19
> **PRGUY85 said:**
> 
I haven't seen anything from Pidgin, Network Manager or Power Management on the new notification system.  Is it my configuration?  I know the volume empty box is specific to me since I have seen other users post pics of the new volumen indicator on notification black bubbles.

Nop, I have the same...

Lets hack it  ;)

[http://packages.ubuntu.com/jaunty/notify-osd](http://packages.ubuntu.com/jaunty/notify-osd)

This can be good but it seems to hard coded, nothing inside gconf and to use
gcont-editor.  (maybe its is  ???)

:D

---

### Post by Mr. Picklesworth on 2009-02-19
Awesome post, mpt. Thanks!

> **mpt said:**
> Indeed, notification bubbles aren&#8217;t &#8212; and shouldn&#8217;t be &#8212; the only mechanism for notifying people of things. (They&#8217;ve been a bit overused in Gnome up till now.) I&#8217;ve written some _[design guidelines]("https://wiki.ubuntu.com/NotificationDesignGuidelines")_ on which mechanism to use in different situations.
I like those guidelines. I wonder about popping up windows whenever action is required, though. Is there some way it can be made less... intrusive? Phones seem to do it right (Android, Palm WebOS). Have you taken into account what is different there?
There are other details, but from the top of my memory they often have a notification bar *just like* your new libnotify but optimized for smaller screens (so this is the right way). Incoming messages, however, are presented as modal windows (much like gksudo). This way they'll never drop to the bottom of the stack.

Libnotify keeps track of the urgency of notifications, so this could even handle a lot of your guidelines automatically (as a temporary measure). It would be a *great* feature since GNOME's existing notification bubbles don't seem to care.
Maybe Low urgency notifications with actions could get some unique treatment - maybe just eaten - , critical ones could get a modal window, regular ones with actions get the morphing window. Or something like that ;)

The morphing window thing sounds neat. Is that a window manager feature, (for example a shaded window) or does it have to be implemented manually?

As for actions... there is probably a perfectly sound reasoning here (you seem sane so far! :P), so why didn't those get placed (temporarily) aboard the new panel applet for a short period? On a similar thought... When unfocussed, why not iconify the actiony notification windows to the new applet? This way they stay out of the way and we get something *reasonably* like the New Messages interface for free. (Okay, not as cool, but similar enough to be in the same place).
The reason I'm asking isn't because I think that should be the way (although for my own odd use case I would find it a nice thing); I'm just curious where this is all going for backwards compatibility.

Add me to the list of people that thinks enforcing normal windows instead of notifications is definitely a good idea. Notifications may *look* super pretty, but it doesn't help the interface much when we have to tell a user to find the little icon that arbitrarily appeared on one corner of the screen. If the task needs interaction, it needs to ask for it; it shouldn't hide. It doesn't help the user if he has to know to look for it; that task should come to him. So kudos to you guys for having the vision to make it happen!

---

### Post by mpt on 2009-02-19
> **loell said:**
> will there be an assurance that this will be consistent?  i mean who gets to decide that there will be no updates for this week because we already did it twice or thrice and deploying another will most likely be annoying?

update-notifier will take care of that. So for example if you last saw Update Manager last Wednesday, it won’t open automatically until next Wednesday at the earliest (unless there are security updates before then).

> **carlholmberg said:**
> I would argue that information like new email-messages should be more like it is on Mac OS X. Don't tell me -- if I want to know I just look at the icon.

That’s person-specific. For example, someone I know gets only one or two e-mail messages a day, and quite often they’re potential business opportunities that depend on her replying quickly. At the other extreme, I get hundreds of messages a day, and I don’t want a bubble popping up for every one! So it will be configurable within Evolution (and, hopefully, later within Thunderbird and KMail and other e-mail programs).

> With this new system it would tell me but if I wasn't paying attention just then I wouldn't know I've gotten a new message until i check my email-application.

There will be a message status menu in the panel that persists after the notification bubble has gone — like the envelope icon on many mobile phone screens.

> And who needs to know that the song has changed in my musicplayer -- I'm not deaf...

Again, that’s person-specific — it’s appropriate for some people but not for others. This is why the various music players in Ubuntu already make it optional, and we’re not going to change that. We’re just changing the way the bubble is presented (and yes, Banshee is [on the list of programs to fix]("https://wiki.ubuntu.com/NotifyOSD#Banshee")).

> I feel that this is trying to fix something without enough background on what's really important, what use cases there are and without a solid scientific foundation. I remember reading a blog post from a KDE-UI-designer/developer that argued, with support from current scientific papers, that the rationale for the implementation was flawed and that more work needs to be done. Url: [http://weblog.obso1337.org/2009/response-to-the-proposed-canonical-notification-system/]("http://weblog.obso1337.org/2009/response-to-the-proposed-canonical-notification-system/")

If you take the time to look through all those scientific papers (as I have), you’ll realize that they don’t really have much relevance to notifications in general-purpose operating systems like Ubuntu, which is a shame. It seems there hasn’t been much published research on this topic. We invited Celeste to participate in writing the [notification design guidelines]("https://wiki.ubuntu.com/NotificationDesignGuidelines"), but she’s been too busy.

> **Starks said:**
> Will the policykit prompts (ie: synaptic asking for your password) be a part of the new desktop experience?

For 9.04 we have our hands full just doing notifications and a couple of other small things. I am [interested in improving the PolicyKit prompts]("http://bugzilla.gnome.org/show_bug.cgi?id=529195#c3"), though, so if anyone here knows their way around the PolicyKit code and wants to help out, find me on IRC. :)

---

### Post by carlholmberg on 2009-02-19
Thank you mpt for answering to my previous message. I will just have to see when I get the chance to try the new system.

*I run Ubuntu on my wifes laptop, which she needs for her work. I use my computer (with Mac OS X) for work and can't risk it becoming unstable. So I'll probably try Jaunty when it enters a late beta or rc -- can't wait!*

---

### Post by mpt on 2009-02-19
> **Mr. Picklesworth said:**
> I like those guidelines. I wonder about popping up windows whenever action is required, though. Is there some way it can be made less... intrusive? Phones seem to do it right (Android, Palm WebOS). Have you taken into account what is different there?
There are other details, but from the top of my memory they often have a notification bar *just like* your new libnotify but optimized for smaller screens (so this is the right way). Incoming messages, however, are presented as modal windows (much like gksudo). This way they'll never drop to the bottom of the stack.

With a phone you’re much less likely to be multitasking, so there’s less of a risk of being interrupted by other things. But even on my own non-smart-phone, occasionally I end up either viewing a message I didn’t want to look at right now, or not seeing who a newly-arrived message is from, because the message notification appeared a fraction of a second before I pressed the “View” or “Back” keys for some completely different purpose. Avoiding that kind of error in Ubuntu is one of the reasons we’ve made the bubbles non-interactive in the first place.

> Libnotify keeps track of the urgency of notifications, so this could even handle a lot of your guidelines automatically (as a temporary measure). It would be a *great* feature since GNOME's existing notification bubbles don't seem to care.
Maybe Low urgency notifications with actions could get some unique treatment - maybe just eaten - , critical ones could get a modal window, regular ones with actions get the morphing window. Or something like that ;)

Unfortunately from what we’ve seen so far, Gnome programs don’t do a consistent job of choosing those urgency levels. For example, when you add a printer but the drivers aren’t installed, system-install-packages puts up a notification marked as critical. Sure, it’s important, but critical? Hardly.

Now that poor choice might be *because* “GNOME's existing notification bubbles don't seem to care”, so developers can’t see any difference. But even if it is, it means we can’t use urgency as a reliable way of choosing fallback mechanisms (at least not without patching *many* more programs than we have time for).

So if you look at [our spec]("https://wiki.ubuntu.com/NotifyOSD"), you’ll see we do [three different things]("https://wiki.ubuntu.com/NotifyOSD#Animations%20and%20durations") for critical notification bubbles: (1) show them first, (2) show them for longer, and (3) show them even in “do-not-disturb” mode. For the long run, though, we’re undecided as to whether urgency should exist for notification bubbles at all. Maybe if something really is critical, you should be using a different mechanism.

> The morphing window thing sounds neat. Is that a window manager feature, (for example a shaded window) or does it have to be implemented manually?

Manually: it involves hiding and showing stuff inside the window that the window manager knows nothing about. Hopefully we’ll get a mockup or two on that page by the end of the week.

> As for actions... there is probably a perfectly sound reasoning here (you seem sane so far! :P), so why didn't those get placed (temporarily) aboard the new panel applet for a short period?
On a similar thought... When unfocussed, why not iconify the actiony notification windows to the new applet? This way they stay out of the way and we get something *reasonably* like the New Messages interface for free. (Okay, not as cool, but similar enough to be in the same place).


A couple of reasons. First, it would make developers less likely to bother fixing them. ;) But also it would confuse people about what the message menu is intended for. For now we think it should be reserved for messages from human beings.

> Add me to the list of people that thinks enforcing normal windows instead of notifications is definitely a good idea. Notifications may *look* super pretty, but it doesn't help the interface much when we have to tell a user to find the little icon that arbitrarily appeared on one corner of the screen. If the task needs interaction, it needs to ask for it; it shouldn't hide.

Exactly. All the notification bubbles that say “Click the icon to…” (or “Click this bubble to…”) are facepalm-worthy. Actually, you can say the same about pretty much any interface that prints the word “click” anywhere; it’s a good sign that something isn’t visually obvious or automatic enough.

---

### Post by mc4100 on 2009-02-19
> **mpt said:**
> All the notification bubbles that say &#8220;Click the icon to&#8230;&#8221; (or &#8220;Click this bubble to&#8230;&#8221;) are facepalm-worthy. Actually, you can say the same about pretty much any interface that prints the word &#8220;click&#8221; anywhere; it&#8217;s a good sign that something isn&#8217;t visually obvious or automatic enough.
Maybe. I don't think notifications instruct you to click them because they know they're not obvious enough (at least not all of them), but simply because the authors know that to *make* or show something which could be identified as obvious (such as an unfocused window) is plainly intrusive. 
I don't think a single person couldn't say Firefox's little notification is less intrusive than:
> ... the Downloads window to open unfocused (if it is not open already), scroll to the bottom of its list (if it is not scrolled to the bottom already), and request attention.

I do think there's something to be said for being conservative with interactive notifications, which of course isn't the case now, and that most should be non-interactive (track change, volume, brightness, etc.,) However, the by-force non-interactive approach would solve the problem *at the expense of things like Firefox, Transmission, Bluetooth*, et al, where interactivity is clearly beneficial and **non-intrusive**.
I don't want to end up with one notification system over there, hassling me to click it's yellow bubbles for trivial things, and another one (admittedly better looking) over there, doing the same thing with unfocused windows.
I'm curious to see how this plays out. I don't think this is the right approach, nor do I say it's the former one, I think the answer is somewhere inbetween ... but who knows?

---

### Post by no1wantdthisname on 2009-02-19
> **son said:**
> It's not only you. I have empty black boxes for volume control, brightness, power events (at least). 

It seems notify-osd looks for the icons in your current icon theme.  

Right now it doesn't actually switch between different icons depending on current brightness/volume level, but I'd rather have any icon than a black box so here's how you can do it.

```

cp /usr/share/icons/Human/scalable/status/notification-* ~/.icons/(THEME NAME HERE)/scalable/status/

```

---

### Post by nyarnon on 2009-02-19
> **inportb said:**
> C'mon over to KDE; the grass is greener on this side. I'm lovin' the improvements ;)

ROTFL you would think that wouldn't you, anything on kde4 is an improvement, ask Linus :lolflag:

---

### Post by tawmas on 2009-02-19
> **no1wantdthisname said:**
> Try changing the volume via keyboard shortcut.  I think it's a good change.

It's solid black here... No graphics at all! :-(
(compiz is enabled, btw)

---

### Post by mempf on 2009-02-19
> **tawmas said:**
> It's solid black here... No graphics at all! :-(
(compiz is enabled, btw)

Same here, compiz and metacity result in the same thing.

nvidia-glx driver.

---

### Post by no1wantdthisname on 2009-02-19
> **tawmas said:**
> It's solid black here... No graphics at all! :-(
(compiz is enabled, btw)

Yeah.  There are no graphics because it can't find the icons.

> **no1wantdthisname said:**
> It seems notify-osd looks for the icons in your current icon theme.  

Right now it doesn't actually switch between different icons depending on current brightness/volume level, but I'd rather have any icon than a black box so here's how you can do it.

```

cp /usr/share/icons/Human/scalable/status/notification-* ~/.icons/(THEME NAME HERE)/scalable/status/

```

---

### Post by tawmas on 2009-02-19
> **mpt said:**
> _[bruce89]("http://ubuntuforums.org/showpost.php?p=6755592&postcount=1")_: Rest assured that Update Manager will not open by itself every two days in Ubuntu 9.04! In 9.04, when security updates are issued, Update Manager will display these within a day; for other updates, though, it will open *at most* once per week.

We recognize this is a bit awkward for those of you testing Jaunty during its development, because if you were installing updates only once a week, your testing wouldn’t be nearly as useful.

I'm sorry, but this looks a bit awkward for release too, for at least two reasons. If a bug which is critical for my work is fixed, I want to get hold of the fix as soon as possible, not once in a week. And, I surely don't wont any application window opened on me by the system, including the update manager.

> **mpt said:**
> _[pferraro]("http://ubuntuforums.org/showpost.php?p=6755852&postcount=5")_: Evolution’s alert boxes are temporary. _[We plan]("https://wiki.ubuntu.com/NotifyOSD#Evolution")_ to integrate Evolution with a message status menu that provides quick access to new mail and instant messages from Evolution, Pidgin, and other programs.

I hope you'll consider implementing notifications for new messages in folders other than the inbox. This is currently lacking in Evolution.

---

### Post by tawmas on 2009-02-19
> **no1wantdthisname said:**
> Yeah.  There are no graphics because it can't find the icons.

Yeah. Should've read the whole thread before posting. Anyway, the file /usr/share/icons/notify_osd/icons/notification-volume.svg is not there, so the fix is not working.

---

### Post by MadsRH on 2009-02-19
I think the new notification bubbles looks very slick and I'm very much looking forward to testing it when Jaunty is released (though development properly won't slow down until Jaunty+1 ).

The only thing I don't like is the brightness/volume OSD. Sure it looks slick and great, but with the Apple-like design the notification was placed in the center of the screen and was bigger. Of course I understand this change and it has to be there for consistency, but it just feels strange looking in the top corner of the screen. I know it's details - anyway, that's my 2 cent.

---

### Post by no1wantdthisname on 2009-02-19
> **tawmas said:**
> Yeah. Should've read the whole thread before posting. Anyway, the file /usr/share/icons/notify_osd/icons/notification-volume.svg is not there, so the fix is not working.

Sorry it's /usr/share/notify_osd/icons/notification-volume.svg.  I also fixed my post.

---

### Post by mempf on 2009-02-19
To anyone having problems with the volume icons. Try restarting. That fixed the problem for me on two different computers.

---

### Post by PRGUY85 on 2009-02-19
I was using the Breathe icon set.  I switched it to Human icons and the volume indicator notification is showing up now.

---

### Post by zekopeko on 2009-02-19
> **bruce89 said:**
> The new notification daemon, I forget what its name is.



No, this is not GNOME's fault, it's Ubuntu's.

I've even managed to grab Mark Shuttleworth's attention on the bug I filed about not autolaunching ([https://bugs.edge.launchpad.net/ubuntu/+source/update-notifier/+bug/331054](https://bugs.edge.launchpad.net/ubuntu/+source/update-notifier/+bug/331054)).

and mark shot you down , oh so nicely. this is a work in progress. treat it as such. and just because you like being in your comfort zone doesn't mean that your comfort zone doesn't suck.

---

### Post by bruce89 on 2009-02-19
> **mpt said:**
> 
_[bruce89]("http://ubuntuforums.org/showpost.php?p=6755592&postcount=1")_: Rest assured that Update Manager will not open by itself every two days in Ubuntu 9.04! In 9.04, when security updates are issued, Update Manager will display these within a day; for other updates, though, it will open *at most* once per week.

I don't want to have it open at all.

> **mpt said:**
> Who do you mean by &#8220;GNOME themselves&#8221;, exactly? Do you mean that Ubuntu&#8217;s graphical software should be developed by Red Hat, Novell, Sun, Imendio, etc, and by volunteers, but not by Canonical? That would be very strange. Others have complained in the past that Canonical should do *more* upstream development, and now we are.

Is any of this work being done upstream (either in Subversion, or by patches on the bugzilla)? No, I didn't think so. Has there been any discussion in the GNOME mailing lists? Again, no, I didn't think so.

> **andrewsomething said:**
> Just to put this into perspective... The entire idea behind the new notification system is that notifications should be ephemeral. They should be used for things like a song change or email coming in. Things that you want to be simply "notified" about. You then can take action on them if you want, but the notifications shouldn't get in the way of what you are doing at the moment. If the system is telling you something that is important enough that you really should do something about it (either acknowledge and put off till later or take action at that moment), then it should use a dialog.

Dialogues appearing randomly is visually distracting, and potentially confusing ("why did this dialogue suddenly appear?", "I wonder if it's a virus [or some other malware]?").

> **zekopeko said:**
> and mark shot you down , oh so nicely. this is a work in progress. treat it as such. and just because you like being in your comfort zone doesn't mean that your comfort zone doesn't suck.

Thanks for being so condescending.

I don't really mind the new notification daemon (but I don't see the improvements over the old one), but I hate dialogues popping up. System-wide dialogues should only be used in the case of an error in something major (gnome-panel, Nautilus etc.).

---

### Post by zekopeko on 2009-02-19
> **bruce89 said:**
> I don't want to have it open at all.



Is any of this work being done upstream (either in Subversion, or by patches on the bugzilla)? No, I didn't think so.



Dialogues appearing randomly is visually distracting, and potentially confusing ("why did this dialogue suddenly appear?", "I wonder if it's a virus [or some other malware]?").



Thanks for being so condescending.

I don't really mind the new notification daemon (but I don't see the improvements over the old one), but I hate dialogues popping up.

you're welcome.

do you have a better solution? their rational is quite solid. and nobody likes pop-ups but how do you propose we get the users attention when it's immediately needed?

---

### Post by bruce89 on 2009-02-19
> **zekopeko said:**
> do you have a better solution? their rational is quite solid. and nobody likes pop-ups but how do you propose we get the users attention when it's immediately needed?

Windows has dialogues that appear when it wants to reboot, which are very annoying. Ubuntu now doing this is thus a bad idea.

Can anyone give me a concrete example of when a dialogue is better than a notification? I'm not a slave to my computer, so I can decide what I want it to do, not the other way round.

---

### Post by Triggerhapp on 2009-02-19
> **zekopeko said:**
> you're welcome.

do you have a better solution? their rational is quite solid. and nobody likes pop-ups but how do you propose we get the users attention when it's immediately needed?

Was personally pretty happy with what we had. Change will be nice when it doesnt do things like throw windows in my way.

---

### Post by zekopeko on 2009-02-19
> **bruce89 said:**
> Windows has dialogues that appear when it wants to reboot, which are very annoying. Ubuntu now doing this is thus a bad idea.

Can anyone give me a concrete example of when a dialogue is better than a notification? I'm not a slave to my computer, so I can decide what I want it to do, not the other way round.

this is all true but you still don't know how to "fix" this. wait... just had an idea. what if we use the notification dialog and put it in the middle top of the screen but with buttons? 
and the dialog would still fade out when you hover over it and you could click through it but the buttons (since the premise is that you need to urgently do something with the notification) would be of higher opacity and you could click them (by hovering over the button and that would also give it 0 transparency so that you can read and act on the info). 
even better would be to make the notification pop-up in the middle of the screen and then settle in the middle-top part of the screen. when it pop's up it should not interfere with your work but just nicely pass on the top of the screen.

EDIT: will devote more time to this idea tomorrow. but please try to expand on it if you think it has any merrit.

---

### Post by bruce89 on 2009-02-19
> **zekopeko said:**
> this is all true but you still don't know how to "fix" this. wait... just had an idea. what if we use the notification dialog and put it in the middle top of the screen but with buttons? 
and the dialog would still fade out when you hover over it and you could click through it but the buttons (since the premise is that you need to urgently do something with the notification) would be of higher opacity and you could click them (by hovering over the button and that would also give it 0 transparency so that you can read and act on the info). 
even better would be to make the notification pop-up in the middle of the screen and then settle in the middle-top part of the screen. when it pop's up it should not interfere with your work but just nicely pass on the top of the screen.

Maybe I'm an old fogey, but I found the old system worked quite well.

---

### Post by zekopeko on 2009-02-19
> **bruce89 said:**
> Maybe I'm an old fogey, but I found the old system worked quite well.

but this one's so much more sexier. and i hate when i have to click the f***** X button for every little notification in WinXP.

---

### Post by deathsshadow77 on 2009-02-19
I have to say I love the new notifications. I feel that its a great idea and really useful without being annoying. I feel that the bubbles are extremely annoying. I have to go out of my way to close a notification that I dont care about. My main issue with this is wireless on my laptop or even networking on my desktop. 
With the new system I may even utilize the pidgin notifications now.

Also, will this be used to replace the Firefox notification saying that downloads are complete?

---

### Post by bruce89 on 2009-02-19
> **zekopeko said:**
> but this one's so much more sexier. and i hate when i have to click the f***** X button for every little notification in WinXP.

As I've pointed out before, the dialogues are what I don't like. There shouldn't be any popup dialogues, only notifications.

---

### Post by zekopeko on 2009-02-19
> **bruce89 said:**
> As I've pointed out before, the dialogues are what I don't like. There shouldn't be any popup dialogues, only notifications.

well they should be for unimportant stuff just transient, and we have the indicator applet that takes care of messages and email. but how to do stuff like a VOIP call that needs your attention now or some other alert that requires immediate action?

---

### Post by bruce89 on 2009-02-19
> **zekopeko said:**
> well they should be for unimportant stuff just transient, and we have the indicator applet that takes care of messages and email. but how to do stuff like a VOIP call that needs your attention now or some other alert that requires immediate action?

Perhaps a notification that you have to click to close.

---

### Post by zekopeko on 2009-02-19
> **bruce89 said:**
> Perhaps a notification that you have to click to close.

re-read my idea. i think that it could work rather nicely. i'll try to do some poor man's mockup tomorrow to better visualize what i'm thinking. it would look nice and it wouldn't interfere with the user's work flow so much as dialogs. or we could add some kind of a messaging center for all of the important stuff like email, missed calls. oh and notifications should wait in queue when you have an app in fullscreen (or have and option to allow it to interfere in fullscreen apps if the user wishes it).

---

### Post by mpt on 2009-02-19
> **bruce89 said:**
> Is any of this work being done upstream (either in Subversion, or by patches on the bugzilla)? No, I didn't think so.

Sorry, that question doesn’t really make sense. As [I explained last time you asked it]("http://ubuntuforums.org/showthread.php?p=6758885#post6758885"), we are the upstream for this project. It’s being done [in Bazaar on Launchpad]("https://code.launchpad.net/notify-osd"). Ubuntu hasn’t used Bugzilla for about three years now.

> *Has there been any discussion in the GNOME mailing lists? Again, no, I didn't think so.*

We presented our plans at the Ubuntu Developer Summit last December, and they were widely publicized then. But talk is cheap, ;) and we haven’t had *code* we considered mature enough to present directly to Gnome or KDE so far. That may change in the coming weeks.

> *Dialogues appearing randomly is visually distracting, and potentially confusing … I don't really mind the new notification daemon (but I don't see the improvements over the old one), but I hate dialogues popping up. System-wide dialogues should only be used in the case of an error in something major (gnome-panel, Nautilus etc.).*

Computers — especially those with network connections — are often subject to external events, and some of those are important, so *something* has to pop up by itself sometimes. A dialog or alert box has much more room to explain why it’s appeared than a notification bubble does. And if you want to deal with it in a minute, not right now, you can raise your work back on top of an alert or dialog; you can’t do that with a notification bubble.

I agree with you that Windows overuses dialogs and alert boxes, and where it makes sense to use something else instead, we certainly will.

---

### Post by PRGUY85 on 2009-02-19
I finally saw the battery monitor and brightness monitor in effect on the new notification system.  I am beginning to really like the integration and overall sleekness.  

When will we see Wi-Fi intregrated to this system as well?  Also, how will Pidgin get integrated to it?

---

### Post by Mr. Picklesworth on 2009-02-19
I get the feeling that a lot of peoples' problems with dialogs stem from the woes of the floating windows paradigm. It could be really worthwhile for someone to tinker with Metacity's window management stuff in the future, getting it to make more gutsy choices about window positioning based on hints and to borrow some good ideas from tiling window managers. (For example utility windows being attached to their parents, dialogs rolling down from the top of parent windows - resizing or pushing client contents out of the way instead of overlapping, where possible - rather than getting lost in the stack of stuff).

As long as things are *technically accurate*, it can be a lot easier to make them nice via infrastructure goodies.

---

### Post by BwackNinja on 2009-02-19
Basically, notifications shouldn't  be a big deal. If they are, they are used too much. I like this new way (except for how notifications with buttons are handled) its less obtrusive in my opinion than the previous method and looks nicer too.

The point is to get your attentions, even if only long enough to dismiss it as unimportant. Notifications are entirely useless if they can just go unnoticed.

All I would want would be to have the notifications with buttons drawn the same way as the regular notifications. And I want my volume notification to actually show something... :(

This is probably one of the most exciting changes in this release so far.

---

### Post by PRGUY85 on 2009-02-19
> **BwackNinja said:**
> 

All I would want would be to have the notifications with buttons drawn the same way as the regular notifications. And I want my volume notification to actually show something... :(



I solved that by using default Human icon set.  You using any other icon set?

---

### Post by pferraro on 2009-02-20
> **PRGUY85 said:**
> I solved that by using default Human icon set.  You using any other icon set?

Switching to the Human icon theme fixes it here too - which begs the question, why didn't they choose to bundle these icons in the hicolor-icon-theme or gnome-icon-theme packages so that other icon themes will properly inherit them?

---

### Post by medeshago on 2009-02-20
Now pidgin works great with notify-osd:

[ATTACH]104020[/ATTACH]

You can't click it or interact in any way with the pop up, I like it still.

---

### Post by SKLP on 2009-02-20
This notification system sucks with the notifications from Banshee! And also the ones from network-manager (interactive notification).
The non-interactive ones also look a bit buggy (I'm on metacity, compiz ftl imo and dont get me wrong: I like compositing if it's done right (as in OS X))

---

### Post by Marat89 on 2009-02-20
> **medeshago said:**
> Now pidgin works great with notify-osd:

[ATTACH]104020[/ATTACH]

You can't click it or interact in any way with the pop up, I like it still.

Hey that looks nice! How do you set it up in pidigin?

---

### Post by Jay_Bee on 2009-02-20
I also noticed network-manager and evolution notifications are displayed by Notify OSD now :)

Evolution shows the notification and then (indicator applet?) pops up the dialog that says "You have X new message" with buttons OK and Cancel (both buttons close the window and do nothing.)

Note: If you disabled network manager notifications but you would like to enable them again open gconf-editor and uncheck /apps/nm-applet/disable-connected-notifications and /apps/nm-applet/disable-disconnected-notifications

---

### Post by ugkbunb on 2009-02-20
This new notification system worked for about a day on my Xubuntu AMD64 install... at first I was able to test it by 

$notify-send "TESTT" "YES I OWN YOU" -i=totem

However... since some update/reboot the above command no longer pops up a purty lil black box.

> **Marat89 said:**
> Hey that looks nice! How do you set it up in pidigin?

there is a package for it... pidgin-libnotify IIRC

---

### Post by kostkon on 2009-02-20
> **bruce89 said:**
> 
Is any of this work being done upstream (either in Subversion, or by patches on the bugzilla)? No, I didn't think so. Has there been any discussion in the GNOME mailing lists? Again, no, I didn't think so.
If Gnome likes it, they'll use it (like, for example, with *PulseAudio*, where a little of convincing was needed, i think. I may be wrong here), if not, it will be only an Ubuntu thing .

I don't understand what is your problem here, I really don't.

---

### Post by Marat89 on 2009-02-20
> **ugkbunb said:**
> there is a package for it... pidgin-libnotify IIRC

Thanks ;)

---

### Post by bruce89 on 2009-02-20
I think I've changed my mind, but only if there was a better solution than to show dialogues (especially these non-HIG compliant ones).

Auto-opening update-manager is still mad though.

---

### Post by Kazade on 2009-02-20
> **bruce89 said:**
> I think I've changed my mind, but only if there was a better solution than to show dialogues (especially these non-HIG compliant ones).

Auto-opening update-manager is still mad though.

I think forcably opening a window, whether in the background or not, is ridiculous. It'll just annoy people. :/

However, loving the new notifications.. if only they worked with bzr-gtk!

---

### Post by PRGUY85 on 2009-02-20
The new pidgin notifications don't work by default?  Do we have to add the indicator-applet on the top panel to have it?

---

### Post by knarf on 2009-02-20
> **zekopeko said:**
> you're welcome.

do you have a better solution? their rational is quite solid. and nobody likes pop-ups but how do you propose we get the users attention when it's immediately needed?

By opening something like a new gnome panel, positioned underneath the top panel, in a different color (yellow?), containing a description of the problem (update, error, etc) and a button to launch a program to solve it (updatemanager, etc).

Think 'firefox notification bar' but system-wide. It does not even have to be a new bar, it would probably suffice to open a big yellow or red applet which takes up half of the panel.

---

### Post by CarpKing on 2009-02-20
I really like the way the new notifications look, but I question the insistence on non-clickability.  Most of the notifications I can think of could benefit from certain clickable functions.  I also *really* dislike the idea of opening windows in the background.  I will be turning that off.

---

### Post by mpt on 2009-02-20
> **Kazade said:**
> However, loving the new notifications.. if only they worked with bzr-gtk!

bzr-gtk is [on the list of programs to fix]("https://wiki.ubuntu.com/NotifyOSD#bzr-gtk"). If you can help fix it (or suggest a better way to fix it), that’d be awesome.

---

### Post by BwackNinja on 2009-02-20
> **PRGUY85 said:**
> I solved that by using default Human icon set.  You using any other icon set?

Awesome, I just found the icons and added them to the gnome icon theme. Now it works with all icon themes. They should really do that, restricting everyone to the human theme wouldn't be too great.

I like :D

---

### Post by BwackNinja on 2009-02-20
> **PRGUY85 said:**
> The new pidgin notifications don't work by default?  Do we have to add the indicator-applet on the top panel to have it?

look in pidgin Tools>Plugins

enable the libnotify popups plugin

---

### Post by PRGUY85 on 2009-02-20
> **BwackNinja said:**
> look in pidgin Tools>Plugins

enable the libnotify popups plugin

I don't see it.

---

### Post by go7Ul1ai on 2009-02-20
> **PRGUY85 said:**
> I don't see it.

You have installed pidgin-libnotify yes?

---

### Post by mickbuntu on 2009-02-20
Now imagine a fake sleep error occurs. Like it likes to  on Gnome, I get it everytime almost. Right now it is possiblt to tell it never to show again. In the future despite normal sleep resume it will keep popping up.  Might not be getting something, but in this case I doubt it.

---

### Post by bruce89 on 2009-02-20
> **CarpKing said:**
> I really like the way the new notifications look, but I question the insistence on non-clickability.  Most of the notifications I can think of could benefit from certain clickable functions.  I also *really* dislike the idea of opening windows in the background.  I will be turning that off.

They are trying to claim that any programs that uses notifications to get user input are broken. This means that there will be yet another round of patches that won't be going upstream.

---

### Post by mc4100 on 2009-02-20
> **bruce89 said:**
> They are trying to claim that any programs that uses notifications to get user input are broken. This means that there will be yet another round of patches that won't be going upstream.

I don't think they're saying "broken" per se ... merely, er, *undesirable*.

---

### Post by Mr. Picklesworth on 2009-02-20
Just changed the focus of my Metacity tinkering to make dialog windows (and others) more manageable, since that's the job of a window manager.

This design made me realize something: the old notification area is basically a micro window manager running on top of Metacity because applications can't trust the real window manager to present their notifications effectively. Developers turn to libnotify to carry out the same task as popup windows (even with the same sort of woefully ignored urgency hints) because the window manager does nothing to make dialog boxes friendly. They're just placed and managed like every other window.

What's happening *here* feels like fixing what needs fixing (or at least suggesting the need) instead of stacking crufty workarounds above the problem.

---

### Post by Kazade on 2009-02-21
I think I've found a bug in the notifications... I was look at the mock up on Mark Shuttleworth's blog, and comparing it to the actual thing. So I waited till my friend sent me a message and then I started pressing the volume buttons on my laptop..

So what (I think) is supposed to happen is the pidgin notification should display, then the volume notification below it, then if I keep pressing the mute button or something, the pidgin notification should disappear, then the volume notification should slide up to take its place until I stop fiddling with the volume then that should also disappear.

What actually happens is both notifications stay visible for as long as I change the volume. I kept the pidgin notification up for about 30 seconds (till I got bored of changing the volume ;) )

I'll report it when I find where on launchpad it is (I haven't looked yet).

---

### Post by Wolki on 2009-02-21
> **Kazade said:**
> So what (I think) is supposed to happen is the pidgin notification should display, then the volume notification below it, then if I keep pressing the mute button or something, the pidgin notification should disappear, then the volume notification should slide up to take its place until I stop fiddling with the volume then that should also disappear.

That was only a mockup, the full design can be found at [https://wiki.ubuntu.com/NotifyOSD](https://wiki.ubuntu.com/NotifyOSD) .

The relevant part is this:
[QUOTE=https://wiki.ubuntu.com/NotifyOSD#Animations%20and%20durations]If two bubbles are on a display simultaneously, the first should never disappear before the second; instead it should disappear at its scheduled time or at the second bubble’s scheduled time, whichever is later.[/QUOTE]

From your description it sounds as if it works as designed.

---

### Post by mpt on 2009-02-21
> **bruce89 said:**
> They are trying to claim that any programs that uses notifications to get user input are broken.

[The Desktop Notifications Specification says]("http://www.galago-project.org/specs/notification/0.9/x154.html"):

> Clients should try and avoid making assumptions about the presentation and abilities of the notification server. The message content is the most important thing.

Clients can check with the server what capabilities are supported using the GetCapabilities message.

When you do GetCapabilities on Notify OSD, it does not return the &#8220;actions&#8221; value. This lets programs know that they shouldn&#8217;t treat notifications as being interactive. But because notification-daemon &#8212; where notifications *are* interactive &#8212; has been the primary implementation of this spec for a while, programs often just steamroll right ahead and use actions without checking.

If you&#8217;re familiar with Web development at all, this is rather like a Web page using an Internet-Explorer-only JavaScript function, without first [checking that the browser recognizes it]("http://dev.opera.com/articles/view/using-capability-detection/").

So, we could do [what the spec suggests]("http://www.galago-project.org/specs/notification/0.9/x408.html"): &#8220;actions may still be specified by the client, however the server is free to ignore them&#8221;. Unfortunately, in quite a few cases (probably including privately-distributed software we&#8217;ve never heard of), programs have made interactive notifications the *only* way of doing a particular thing. So rather than just ignoring the actions and breaking those programs completely, we decided putting up an alert box was the next best thing. We&#8217;ll be publishing compatibility guidelines soon to help developers avoid this by following the Desktop Notifications Specification properly.

I agree with your earlier comment that the fallback alert boxes aren&#8217;t quite HIG-compliant yet. We&#8217;ll be fixing them.

> **bruce89 said:**
> This means that there will be yet another round of patches that won't be going upstream.

Banshee upstream has [already accepted our patch]("http://bugzilla.gnome.org/show_bug.cgi?id=571177"), and we expect other projects will follow.

> **Wolki said:**
> From your description it sounds as if it works as designed.

Exactly. That part has changed since the December mockup. We decided that it would be better to have the bubble stay in one place rather than sliding up.

---

### Post by Kazade on 2009-02-21
> 
Exactly. That part has changed since the December mockup. We decided that it would be better to have the bubble stay in one place rather than sliding up.

Awww.. that was the coolest bit! :p

---

### Post by PRGUY85 on 2009-02-21
> **Kazade said:**
> Awww.. that was the coolest bit! :p

Agree I liked that aspect of the mockup design better.

---

### Post by go7Ul1ai on 2009-02-21
I read through the whole Notify-OSD documentation, apparently the notification bubbles will be slighty blurred. When will they implement this? It will look pretty cool IMO

---

### Post by mc4100 on 2009-02-21
> **lee.jarratt said:**
> I read through the whole Notify-OSD documentation, apparently the notification bubbles will be slighty blurred. When will they implement this? It will look pretty cool IMO

I think it already is, and that you just need to be able to enable blur in compiz (which only works with certain drivers). Can anyone confirm?

---

### Post by go7Ul1ai on 2009-02-21
> **mc4100 said:**
> I think it already is, and that you just need to be able to enable blur in compiz (which only works with certain drivers). Can anyone confirm?

That's a shame because enabling blur in Compiz wrecks my system (I just had to use the failsafe terminal to remove compiz and compiz-core, then log in to change my appearance settings to "none", then install compiz again :/).

---

### Post by zekopeko on 2009-02-21
> **mc4100 said:**
> I think it already is, and that you just need to be able to enable blur in compiz (which only works with certain drivers). Can anyone confirm?

you have to have the blur plugin enabled.

---

### Post by mc4100 on 2009-02-21
> **lee.jarratt said:**
> I just had to use the failsafe terminal to remove compiz and compiz-core, then log in to change my appearance settings to "none", then install compiz again.
A quick tip:
I assume you're seeing some kind of black screen (which is what I see with Intel drivers), if that's the case then all you need to do is press Alt+f2 and run the standard:
```
metacity --replace
``` to disable compiz. And then when re-enabled in Appearance should revert back to its defaults (no active blur).

---

### Post by PRGUY85 on 2009-02-22
Even though I have the plugin installed, I can't get pidgin to show New Messages notifications. I was able to get the Buddy Online notification but nothing else.

---

### Post by tgpraveen on 2009-02-22
> **prguy85 said:**
> agree i liked that aspect of the mockup design better.

+1

---

### Post by Wolki on 2009-02-22
> **PRGUY85 said:**
> Agree I liked that aspect of the mockup design better.

I agree that the mockup looked cool, but I think it's a change for the better. By the time notifications fade out, you really shouldn't need to look at them any more, and the human perception system is very sensitive to motion. Users would be inclined to look there again even if it's just the same thing they read already, because the movement makes it seem like something new happened. Directing more attention to the least important part of the notification system does not seem like a good idea if the plan is to make it as non-distracting as possible.

It's great that we're able to do cool animations now, but let's use them where they make the most sense.

---

### Post by Lorenz on 2009-02-22
I upgraded y'day, as this is not really a production system, whatever the definition for this is anyway. Upgrade went smooth without problems, I got problems with graphic drivers, but I assume (and think I read it here somewhere) that the ATI drivers are not available yet. The notifications are fine with me, but: they don't work with skype, they don't work with googlemail (who needs an offline client these days?), they don't work with deluge, they don't work with volume (I only get a black notification) and they don't trigger a response from the brightness adjusting. 

Overall, I think while Skype is not open source, it is one of the most widely used IM messengers out there and it should be supported. Same for googlemail, if that is somehow possible? Anyway, I do like the general idea :)

---

### Post by BwackNinja on 2009-02-22
I mostly just wish that I could have more than one notification open at a time. At best I can have one notification and then changing volume. It would make the libnotify plugin for pidgin much more useful and fun.

---

