---
title: "notify-osd disregards position setting"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tekstr1der on 2009-08-27
Regardless of what I set for the position option under Preferences > Pop-Up Notifications, notify-osd now only displays about 2/3 down the screen vertically along the right edge of my screen.

Anyone else seeing this?

---

### Post by taavikko on 2009-08-27
> **tekstr1der said:**
> Regardless of what I set for the position option under Preferences > Pop-Up Notifications, notify-osd now only displays about 2/3 down the screen vertically along the right edge of my screen.

Anyone else seeing this?

Not on my Gnome-laptop now, so cannot test, but is it changed, that menu used to change notification-daemons settings, instead of notify-osd related stuff.

---

### Post by tekstr1der on 2009-08-27
Filed: [https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/419928](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/419928)

---

### Post by rudenko_ruslan on 2009-08-27
> **tekstr1der said:**
> Regardless of what I set for the position option under Preferences > Pop-Up Notifications, notify-osd now only displays about 2/3 down the screen vertically along the right edge of my screen.

Anyone else seeing this?
Yup, after updates position of NotifyOSD has changed. Is it a bug or feature? :confused:

---

### Post by NCLI on 2009-08-27
It also happens here, screenshot attached. I wonder whether this is some experiment by the Desktop Experience Team, or just a bug...?

---

### Post by aamukahvi on 2009-08-27
> **taavikko said:**
> Not on my Gnome-laptop now, so cannot test, but is it changed, that menu used to change notification-daemons settings, instead of notify-osd related stuff.
Yeah I don't think it's supposed to be configurable.

---

### Post by tekstr1der on 2009-08-27
> **aamukahvi said:**
> Yeah I don't think it's supposed to be configurable.

Well it was still properly configuring the display position of notify-osd up until today.

Regardless, the new behavior is incorrect. That just can't be by design. Can it?

---

### Post by Jay_Bee on 2009-08-27
That is the experimental change in positioning, to try it out for a while.
And no, the position was never supposed to be configurable.

---

### Post by tekstr1der on 2009-08-27
> Matthew Paul Thomas  wrote 1 minute ago:

"Preferences" > "Pop-Up Notifications" is installed along with, and applicable only to, notification-daemon. It has nothing to do with Notify OSD.


That was quick. Looks like I was wrong. I can only hope that they decide to change it back to previous behavior.

---

### Post by NCLI on 2009-08-27
> **tekstr1der said:**
> That was quick. Looks like I was wrong. I can only hope that they decide to change it back to previous behavior.
I don't know, this position makes the notifications way more obvious on my 24" widescreen monitor, and I don't think I've missed a single one yet. With the notifications appearing in the top-right corner, I often missed new IM notifications, so I don't think this is such a bad idea...

Anyway, the optimal solution would be to have notifications pulse, or appear 2/3rds up the screen and quickly gliding to their final position in the top-right corner.

---

### Post by kaitwospirit on 2009-08-27
The current setting is pretty obnoxious. I thought the point of notify-osd was to get this stuff out of the way?

---

### Post by NCLI on 2009-08-27
But certainly not so much that we miss it entirely?

I do agree though, this position is too obnoxious to use.

---

### Post by isecore on 2009-08-27
I'm experiencing this as well. Started earlier today I think, not sure. I install updates as they come along.

Having the notification halfway down the screen is _NOT_ optimal in my opinion. Upper right corner was just fine, I'd prefer it that way.

Also, I don't have the menu option for Preferences - Popup Notifications. What is this, is it good to have, and if so, what package installs it?

---

### Post by taavikko on 2009-08-27
Guys, chill out, it might just a be small typo in source, and will be fixed ASAP.
Pretty certain that placing the notifications in the middle of right side, isn't intentional.

---

### Post by tekstr1der on 2009-08-27
> Pretty certain that placing the notifications in the middle of right side, isn't intentional.

Oh, but it is! Though it should be configurable for sure.

[https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble](https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble)

---

### Post by taavikko on 2009-08-27
> **tekstr1der said:**
> Oh, but it is! Though it should be configurable for sure.

[https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble](https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble)

I stand corrected. Thanks, that doesn't look kewl though, must agree.

---

### Post by Kazade on 2009-08-27
> **taavikko said:**
> I stand corrected. Thanks, that doesn't look kewl though, must agree.

It wouldn't surprise me if it stays like this no matter what we (i.e. the users) think... anyone remember the update-notifier and auto-launch?

---

### Post by kansasnoob on 2009-08-27
> **tekstr1der said:**
> Oh, but it is! Though it should be configurable for sure.

[https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble](https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble)

+1!

The need for configurability is very important for me since I'm legally blind. To have any momentary pop-up notifications that disappear before I have time to focus on them just plain stinks.

I wouldn't care if they had to be configured using config editor rather than a gui but both position and amount of time displayed should be configurable.

Rather reminds me of the old joke, "this ain't Burger King, you'll get it my way or no way at all".

---

### Post by tekstr1der on 2009-08-27
> The need for configurability is very important for me since I'm legally blind.

That sure sound like something the devs should have taken into consideration from a usability aspect.

My bug was shot down immediately and marked as invalid. There is another here:

[https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/419894](https://bugs.launchpad.net/ubuntu/+source/notify-osd/+bug/419894)

which specifically targets the middle-screen placement. Feel free to select "this affects me too" and comment on your valid concerns

---

### Post by Kazade on 2009-08-27
If anyone fancies recompiling it, this is the commit that did it: [http://bazaar.launchpad.net/~notify-osd-developers/notify-osd/main/revision/384](http://bazaar.launchpad.net/~notify-osd-developers/notify-osd/main/revision/384)

If you look, they have kept PLACEMENT_OLD changing this line:

        this->priv->placement            = PLACEMENT_NEW;

to 

        this->priv->placement            = PLACEMENT_OLD;

Should revert the behaviour I think. I'm not on Karmic atm, but I might try fixing this later and repackaging and uploading to a PPA, unless someone gets there first.

I might also look into forking it so we can choose the position... I'm getting a little tired of this "We know best so sod off" attitude...

---

### Post by taavikko on 2009-08-27
From changelog:
experiment with centering bubbles vertically, sync. bubble always goes above center-line, async. one always below it

as found in: [http://macslow.net/?p=381](http://macslow.net/?p=381)

---

### Post by Kazade on 2009-08-27
> **taavikko said:**
> From changelog:
experiment with centering bubbles vertically, sync. bubble always goes above center-line, async. one always below it

as found in: [http://macslow.net/?p=381](http://macslow.net/?p=381)

Let's hope it is an experiment...

For those of you who would rather it was still in the top-right, I've built a package with the old behaviour and uploaded it here: [http://www.kazade.co.uk/downloads/notify_osd/notify-osd_0.9.18-0ubuntu2~ppa1_i386.deb](http://www.kazade.co.uk/downloads/notify_osd/notify-osd_0.9.18-0ubuntu2~ppa1_i386.deb)

---

### Post by Brandel Valico on 2009-08-28
Thanks for the package. It didn't want to let me install. So I had to remove the newer version then install yours but it does work and my notifications are now in the upper right hand corner. Now I just have to remember not to upgrades this particular package when doing upgrades.

---

### Post by Leighman on 2009-08-28
I thought it was a bug :(
It's a completely unnatural placement.  Should be configurable at the very least.

---

### Post by Kazade on 2009-08-28
The most annoying thing is that I've looked through the code. It would be a couple of hours work to make it configurable at most! They could have 8 positions around the screen (top-left/middle/right, bottom-left/middle/right, left-middle and right-middle) and just have a gconf key to set it. I actually hacked a version to appear at the bottom right in under 20 minutes which retained the current top-right and middle-right options.

What I'm saying is, making it non-configurable is nothing to do with the complexity of doing it.. the DX team/Mark S have/has just decided it's not going to be configurable. Very frustrating.

---

### Post by Paqman on 2009-08-28
> **Leighman said:**
> I thought it was a bug :(


Me too. It looks really messy. If you've got a visually cluttered web page in a browser window (for example) the notification bubble overlaps it and gets lost. Tucked away in the top right was much neater, and IMO clearer to read than halfway down the screen.

---

### Post by ELD on 2009-08-28
That has to be a bug, the middle of the screen? Riiiiiighhttt....

---

### Post by Brandel Valico on 2009-08-28
Excellent used the package provided above to replace the newer version. Then locked the package in synaptic to prevent the updater from re-installing the package that moves the bubble to the middle of the screen. Thus locking my bubble at the upper right corner. Makes a good work around until they make it configurable to set it where I want it to be set. Thanks again Kazade for the package.

---

### Post by Kazade on 2009-08-28
> **Brandel Valico said:**
> Excellent used the package provided above to replace the newer version. Then locked the package in synaptic to prevent the updater from re-installing the package that moves the bubble to the middle of the screen. Thus locking my bubble at the upper right corner. Makes a good work around until they make it configurable to set it where I want it to be set. Thanks again Kazade for the package.

No worries... apparently there is a more recent package of notify-osd so I'll look it repackaging that one also over the weekend (it's only a 10 minute job).

---

### Post by Kazade on 2009-08-28
From [MacSlow's blog]("http://macslow.net/?p=381"):
> 
"The new position is - like mentioned in the ChangeLog - an experiment. Depending of feedback from users it&#8217;ll stay or be reverted."

...

"There&#8217;s not going to be a configuration UI for notify-osd. We rather want the defaults to be rock solid. That&#8217;s why we collect feedback from users on any issues with notify-osd."

It might well be worth making ourselves heard on his blog (where are we supposed to put this feedback???). The second quote is ridiculous IMO. There will never EVER be a part of the screen that doesn't get in the way for someone or be correct for people with accessibility issues, adding a configuration dialog is not exactly difficult so why not do it or even better, reuse the old one!

---

### Post by ELD on 2009-08-28
I added my feedback to the blog

> 
Adding in my feedback, let us choose position, top, middle or bottom, left, right or centre.

I see no reason for it being hard-positioned and that seems very backwards, ubuntu (and linux) is about openess and ablity to change etc etc, not allowing us to change it is such a stupid thing to do.

Trying new things is great for defaults, but not allowing us to change = rubbish.


---

### Post by zoomy942 on 2009-08-28
im not sure what i think just yet.  beign configurabel would be best, but if i had to pick one, i'd say top corner

---

### Post by Kazade on 2009-08-28
> **zoomy942 said:**
> im not sure what i think just yet.  beign configurabel would be best, but if i had to pick one, i'd say top corner

Funny, I'd prefer bottom right... and this is exactly why the no configuration idea is flawed. 

The whole GNOME desktop is configurable, all the panels move and everyone uses it differently, it makes no sense to make this immovable no matter where they choose. I thought that in Jaunty it was down to time-constraints that there was no configuration and I accepted that... but I don't like this one bit.

---

### Post by tekstr1der on 2009-08-28
From the bug report, if you really want your input heard concerning this issue:

> 

Mirco Müller wrote:
> The best place to discuss such things, like UI-design, is the Ayatana
> mailing-list. Please provide your feedback there
> [https://lists.launchpad.net/ayatana/threads.html](https://lists.launchpad.net/ayatana/threads.html), thanks in advance!
>
>
Also #ayatana on freenode irc.

M.


---

### Post by Kazade on 2009-08-28
> **tekstr1der said:**
> From the bug report, if you really want your input heard concerning this issue:

Thanks, I've posted there.

---

### Post by fondle-em on 2009-08-28
On what planet is it user friendly to not allow notification bubbles to be moved to the position that *best suits the user*?  I don't mind if they want to make the default some zany center-right position, as long as I can change the positioning to someplace where it is useful to me.  This is the OPPOSITE of user friendly.  Or is user friendliness off the table now?

---

### Post by Kazade on 2009-08-28
> **fondle-em said:**
> On what planet is it user friendly to not allow notification bubbles to be moved to the position that *best suits the user*?  I don't mind if they want to make the default some zany center-right position, as long as I can change the positioning to someplace where it is useful to me.  This is the OPPOSITE of user friendly.  Or is user friendliness off the table now?

Sign up to the mailing list and tell them :)

Here's my post: [https://lists.launchpad.net/ayatana/msg00572.html](https://lists.launchpad.net/ayatana/msg00572.html)

---

### Post by Bios Element on 2009-08-28
> **fondle-em said:**
> On what planet is it user friendly to not allow notification bubbles to be moved to the position that *best suits the user*?  I don't mind if they want to make the default some zany center-right position, as long as I can change the positioning to someplace where it is useful to me.  This is the OPPOSITE of user friendly.  Or is user friendliness off the table now?

Exactly. And I fail to understand the "Configuration is bad" Stance. If I wanted configuration removed I'd install Windows...

---

### Post by cyberkilla on 2009-08-28
> **Bios Element said:**
> Exactly. And I fail to understand the "Configuration is bad" Stance. If I wanted configuration removed I'd install Windows...

Less configuration for notifications, less configuration for GDM login screen,....:P

It wouldn't be so bad if the defaults didn't suck. No doubt that will change, to some degree.

---

### Post by Merk42 on 2009-08-28
> **Kazade said:**
> Funny, I'd prefer bottom right... and this is exactly why the no configuration idea is flawed. 

The whole GNOME desktop is configurable...
...for now.

I take it you haven't yet experimented with GNOME Shell.

---

### Post by 23meg on 2009-08-28
> **Bios Element said:**
> Exactly. And I fail to understand the "Configuration is bad" Stance. If I wanted configuration removed I'd install Windows...

"Configuration is bad" would be a misinterpretation of the "Configurability is not a solution to flawed design" stance. The following pieces may help you understand and appreciate it:

[http://www.joelonsoftware.com/uibook/chapters/fog0000000059.html](http://www.joelonsoftware.com/uibook/chapters/fog0000000059.html)
[http://ometer.com/free-software-ui.html](http://ometer.com/free-software-ui.html)
[http://mystilleef.blogspot.com/2005/12/just-add-option-to-turn-it-off-or-on.html](http://mystilleef.blogspot.com/2005/12/just-add-option-to-turn-it-off-or-on.html)

> **Merk42 said:**
> ...for now.

I take it you haven't yet experimented with GNOME Shell.

Please keep your issues with GNOME Shell out of this thread, and make an effort not to derail discussions.

---

### Post by Tibuda on 2009-08-28
> **23meg said:**
> "Configuration is bad" would be a misinterpretation of the "Configurability is not a solution to flawed design" stance. The following pieces may help you understand and appreciate it:

[http://www.joelonsoftware.com/uibook/chapters/fog0000000059.html](http://www.joelonsoftware.com/uibook/chapters/fog0000000059.html)
[http://ometer.com/free-software-ui.html](http://ometer.com/free-software-ui.html)
[http://mystilleef.blogspot.com/2005/12/just-add-option-to-turn-it-off-or-on.html](http://mystilleef.blogspot.com/2005/12/just-add-option-to-turn-it-off-or-on.html)



Please keep your issues with GNOME Shell out of this thread, and make an effort not to derail discussions.

Nice reading, thanks. I have laughed at the Windows help dialog...

---

### Post by Merk42 on 2009-08-28
> **23meg said:**
> Please keep your issues with GNOME Shell out of this thread, and make an effort not to derail discussions.

All I was saying was that a lack of configuration would go along with the changes of GNOME. Like how they remove icons and possibly take out the ability of putting them back in.
I never said the direction was good or bad.

EDIT:
Pretty funny, or sad, that the links you posted are years old and yet still true.

---

### Post by 23meg on 2009-08-28
> **Merk42 said:**
> All I was saying was that a lack of configuration would go along with the changes of GNOME. Like how they remove icons and possibly take out the ability of putting them back in.
I never said the direction was good or bad.

Perhaps that's what you *intended to say*, but you said something quite different:

[QUOTE=Merk42]
...for now.

I take it you haven't yet experimented with GNOME Shell.[/QUOTE]

It's quite hard to infer the above from the below.

Anyway, Notify OSD isn't part of GNOME, so your impressions of GNOME, negative or positive, are off-topic.

---

### Post by ELD on 2009-08-29
Honestly i don't see why it is so much to ask for us to be able to select a position, i don't have my bars the way the default ubuntu install does, i want it to appear where i want it to, not where a few people think it will be well placed, i want options at least for this one thing!

---

### Post by cyberkilla on 2009-08-29
> **ELD said:**
> Honestly i don't see why it is so much to ask for us to be able to select a position, i don't have my bars the way the default ubuntu install does, i want it to appear where i want it to, not where a few people think it will be well placed, i want options at least for this one thing!

You can't skin it either, afaik.

Personally, I'm warming to its new location.

---

### Post by isecore on 2009-08-29
> **cyberkilla said:**
> Personally, I'm warming to its new location.

I'm the opposite. For every time a notification appears, the more awful that location feels. I tend to keep applications right there (Pidgin contact list, calculator, etc) and the notifications become invisible unless you're looking at exactly that place.

---

### Post by cyberkilla on 2009-08-29
> **isecore said:**
> I'm the opposite. For every time a notification appears, the more awful that location feels. I tend to keep applications right there (Pidgin contact list, calculator, etc) and the notifications become invisible unless you're looking at exactly that place.

It's an unnatural position, I agree. However, I often miss the notifications when they are in the top-right.

I'd rather they appeared on the bottom-right or even bottom-center.

---

### Post by Merk42 on 2009-08-29
> **23meg said:**
> Anyway, Notify OSD isn't part of GNOME, so your impressions of GNOME, negative or positive, are off-topic.

I don't want to argue, with you this is a genuine question.

The notification area for GNOME Shell, is that using Notify OSD or something written from the ground up?

---

### Post by 23meg on 2009-08-29
> **Merk42 said:**
> 
The notification area for GNOME Shell, is that using Notify OSD or something written from the ground up?

GNOME, including GNOME Shell, is not using Notify OSD in any way, hence my request.

---

### Post by isecore on 2009-08-29
> **cyberkilla said:**
> It's an unnatural position, I agree. However, I often miss the notifications when they are in the top-right.

I'd rather they appeared on the bottom-right or even bottom-center.

Yes, I think we all can agree that the position should be user-configurable. Locking the notification to a default position is an arrogant attitude towards the user.

However, I personally am perfectly fine with it being locked to the upper-right corner ;)

---

### Post by ELD on 2009-08-29
> **isecore said:**
> I'm the opposite. For every time a notification appears, the more awful that location feels. I tend to keep applications right there (Pidgin contact list, calculator, etc) and the notifications become invisible unless you're looking at exactly that place.

Exactly i tend to keep stuff there too and having it appear in the middle of them would be damn annoying!

> **isecore said:**
> Yes, I think we all can agree that the position should be user-configurable. Locking the notification to a default position is an arrogant attitude towards the user.


The point i was trying to make ealier, i am in total agreement.

---

### Post by Merk42 on 2009-08-29
To those that would like the notification in the lower right, do you also have your panels moved around so the Notification Area is in the lower right?
If so, seems to me notify-osd shouldn't so much be "Upper-right", "Lower Right", etc. but "Wherever the Notification Area is"

---

### Post by ELD on 2009-08-29
> **Merk42 said:**
> To those that would like the notification in the lower right, do you also have your panels moved around so the Notification Area is in the lower right?
If so, seems to me notify-osd shouldn't so much be "Upper-right", "Lower Right", etc. but "Wherever the Notification Area is"

I tend to have it there yes.

---

### Post by taavikko on 2009-08-29
> **Merk42 said:**
> To those that would like the notification in the lower right, do you also have your panels moved around so the Notification Area is in the lower right?
If so, seems to me notify-osd shouldn't so much be "Upper-right", "Lower Right", etc. but "Wherever the Notification Area is"

Well said.

Could some admin add a poll to this thread, so we could have some sort of info how users want this (customizable or hard-coded)?

---

### Post by ktp on 2009-08-29
> **tekstr1der said:**
> Oh, but it is! Though it should be configurable for sure.

[https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble](https://wiki.ubuntu.com/NotifyOSD#Outside%20the%20bubble)

Here we go again :lolflag:

---

### Post by ktp on 2009-08-29
> **Kazade said:**
> The most annoying thing is that I've looked through the code. It would be a couple of hours work to make it configurable at most! They could have 8 positions around the screen (top-left/middle/right, bottom-left/middle/right, left-middle and right-middle) and just have a gconf key to set it. I actually hacked a version to appear at the bottom right in under 20 minutes which retained the current top-right and middle-right options.

What I'm saying is, making it non-configurable is nothing to do with the complexity of doing it.. the DX team/Mark S have/has just decided it's not going to be configurable. Very frustrating.

Join the club.  If you want and have few hours you can read through these two bugs:

notify-osd doesn't honor my preference
[https://bugs.launchpad.net/bugs/346095](https://bugs.launchpad.net/bugs/346095)

Update Notifier icon would provide useful status information
[https://bugs.launchpad.net/bugs/332945](https://bugs.launchpad.net/bugs/332945)

---

### Post by Kazade on 2009-08-29
> **ktp said:**
> Join the club.  If you want and have few hours you can read through these two bugs:

notify-osd doesn't honor my preference
[https://bugs.launchpad.net/bugs/346095](https://bugs.launchpad.net/bugs/346095)

Update Notifier icon would provide useful status information
[https://bugs.launchpad.net/bugs/332945](https://bugs.launchpad.net/bugs/332945)

Trust me... I've read them. Some of the most offensive and worrying bug reports I've ever read. The attitude towards the community from the DX team is quite shocking at times.

The update-notifier decision was ridiculous but at least there is an option to revert it. This "experiment" is even more damaging, because if it becomes permanent, we're stuck with it and the only solution is to fork the project.

Thing is, if these decisions keep getting made in the way they are, then people will fork these projects and set up a PPA and suddenly the DX team's drive to unify the desktop will just make it more fragmented.

I completely appreciate the stroke of genius that notify-osd is, and I appreciate the work that has been put into making it possible. But being arrogant and refusing to listen to any criticism is not the way to go about doing anything. And point blank ignoring the requests of the users is just plain stupid.

---

### Post by Tibuda on 2009-08-29
> **Merk42 said:**
> To those that would like the notification in the lower right, do you also have your panels moved around so the Notification Area is in the lower right?
If so, seems to me notify-osd shouldn't so much be "Upper-right", "Lower Right", etc. but "Wherever the Notification Area is"

Agreed!

---

### Post by 23meg on 2009-08-29
> **Kazade said:**
> Trust me... I've read them. Some of the most offensive and worrying bug reports I've ever read. The attitude towards the community from the DX team is quite shocking at times.

Right: disagreeing with a suggested solution, being slightly late in acknowledging the nature of the problem and one overly busy person neglecting to read the whole long discussion properly - quite shocking.. Because, you know, it never happens in development discussions - especially here in the forums..

> **Kazade said:**
> The update-notifier decision was ridiculous but at least there is an option to revert it. This "experiment" is even more damaging, because if it becomes permanent, we're stuck with it and the only solution is to fork the project.

Forking is not the only way to disagree; maintaining a compatible patchset / branch is much more convenient for everyone, as well as being useful in illustrating why your changes are better. 

If you don't like the results of this experiment, make your voice heard, along with the reasons why you don't like it - why it gets in your way, what it prevents you from doing. That's the entire reason it's rolled out in a development branch: get feedback.

> **Kazade said:**
> Thing is, if these decisions keep getting made in the way they are, then people will fork these projects and set up a PPA and suddenly the DX team's drive to unify the desktop will just make it more fragmented.


Except that there's no decision yet (hence "experiment"), and no "drive to unify the desktop".

> **Kazade said:**
> I completely appreciate the stroke of genius that notify-osd is, and I appreciate the work that has been put into making it possible. But being arrogant and refusing to listen to any criticism is not the way to go about doing anything. And point blank ignoring the requests of the users is just plain stupid.

I agree. Thankfully, there's no "being arrogant and refusing to listen to any criticism" and "point blank ignoring the requests of the users" at play here.

---

### Post by taavikko on 2009-08-29
> **Kazade said:**
> 
The update-notifier decision was ridiculous but at least there is an option to revert it. This "experiment" is even more damaging, because if it becomes permanent, we're stuck with it and the only solution is to fork the project.


We're not stuck with notify-osd, thus not an only solution.
we can always remove it. and fallback to an older notification-daemon.

---

### Post by Merk42 on 2009-08-29
> **Merk42 said:**
> To those that would like the notification in the lower right, do you also have your panels moved around so the Notification Area is in the lower right?
If so, seems to me notify-osd shouldn't so much be "Upper-right", "Lower Right", etc. but "Wherever the Notification Area is"

> **ELD said:**
> I tend to have it there yes.
> **taavikko said:**
> Well said.
Could some admin add a poll to this thread, so we could have some sort of info how users want this (customizable or hard-coded)?
> **danielrmt said:**
> Agreed!

See, 23meg, I can be helpful too.

---

### Post by Kazade on 2009-08-29
> **23meg said:**
> Right: disagreeing with a suggested solution, being slightly late in acknowledging the nature of the problem and one overly busy person neglecting to read the whole long discussion properly - quite shocking.. Because, you know, it never happens in development discussions - especially here in the forums..


The update-notifier report has 31 duplicates, 100s of subscribers and 432 comments, the vast majority of them disagreeing with the change. The bit I find shocking is that not once (that I can see) did the DX team admit that popping up the update window could be a bad idea. I strongly felt and still feel, that the people commenting in the report were just being ignored. 

> 
Forking is not the only way to disagree; maintaining a compatible patchset / branch is much more convenient for everyone, as well as being useful in illustrating why your changes are better. 


Sorry, that was wrong terminology on my part, that's what I meant, but packaged in a PPA somewhere. And I'm thinking about creating such a patch and requesting it be applied to trunk.

> 
If you don't like the results of this experiment, make your voice heard, along with the reasons why you don't like it - why it gets in your way, what it prevents you from doing. That's the entire reason it's rolled out in a development branch: get feedback.


I have on the mailing list.

> 
Except that there's no decision yet (hence "experiment"), and no "drive to unify the desktop".


OK.

> 
I agree. Thankfully, there's no "being arrogant and refusing to listen to any criticism" and "point blank ignoring the requests of the users" at play here.

Well, I hope you are right, but that's how it's coming across to me and quite a few other people that have commented in the reports.

---

### Post by tekstr1der on 2009-09-01
Squeaky wheel gets the grease? gconf key is better than nothing for sure!
 > 
#44   	 Mirco Müller  wrote 3 hours ago:

Support for the gconf-key /apps/notify-osd/gravity is on it's way.
Mirco Müller 28 minutes ago
Changed in notify-osd (Ubuntu):
status: 	In Progress &#8594; Fix Committed
#45 	Sebastien Bacher wrote 1 minute ago:

the new version has been uploaded
Changed in notify-osd (Ubuntu):
status: 	Fix Committed &#8594; Fix Released
Sebastien Bacher 1 minute ago
Changed in notify-osd (Ubuntu):
status: 	Fix Released &#8594; Fix Committed
#46 	Sebastien Bacher wrote 1 minute ago:

the new version is in karmic now
Changed in notify-osd (Ubuntu):
status: 	Fix Committed &#8594; Fix Released

---

### Post by tekstr1der on 2009-09-01
```
notify-osd (0.9.20-0ubuntu1) karmic; urgency=low

  * New upstream version:
    - added support for integer gconf-key "/apps/notify-osd/gravity"
    - supported values are 1 (NorthEast, top-right) and 2 (East, vertically centered at right of screen)
    - switch back default positioning to NorthEast (top-right)

```

Gee, if they just added SouthEast for all the bottom-panel users, I think almost everyone would be happy.

---

### Post by zoomy942 on 2009-09-01
so is that something i can edit with sudo gedit?

---

### Post by aamukahvi on 2009-09-01
> **zoomy942 said:**
> so is that something i can edit with sudo gedit?
Well, yes. But use of gconf-editor is preferred.

---

### Post by zoomy942 on 2009-09-01
> **aamukahvi said:**
> Well, yes. But use of gconf-editor is preferred.

thats what i figured, but im not seeing it listed in there

---

### Post by tekstr1der on 2009-09-01
> thats what i figured, but im not seeing it listed in there

Um... give it a bit. It just hit the repos. You will need to update the notify-osd package once it's available.

---

### Post by Kazade on 2009-09-01
> **tekstr1der said:**
> ```
notify-osd (0.9.20-0ubuntu1) karmic; urgency=low

  * New upstream version:
    - added support for integer gconf-key "/apps/notify-osd/gravity"
    - supported values are 1 (NorthEast, top-right) and 2 (East, vertically centered at right of screen)
    - switch back default positioning to NorthEast (top-right)

```

Gee, if they just added SouthEast for all the bottom-panel users, I think almost everyone would be happy.

+1. Still, this change makes me happy. Looks like I was wrong, perhaps we are being listened to after all :)

---

### Post by aamukahvi on 2009-09-01
> **zoomy942 said:**
> thats what i figured, but im not seeing it listed in there
You can create the key yourself if it isn't created automatically.

---

### Post by tekstr1der on 2009-09-01
> **aamukahvi said:**
> You can create the key yourself if it isn't created automatically.

Patience. The package is being built currently and will be in the repositories shortly. Creating the key manually before getting the upgraded package will do exactly nothing. The current version is unaware of the key or it's value. Upgrading the package when it's available will create the key.

---

### Post by aamukahvi on 2009-09-01
> **tekstr1der said:**
> Patience. The package is being built currently and will be in the repositories shortly. Creating the key manually before getting the upgraded package will do exactly nothing. The current version is unaware of the key or it's value. Upgrading the package when it's available will create the key.

I'm well aware of that. I meant that if after upgrading the package the key still isn't available you can just create it.

EDIT: Just checked, I don't even have the notify-osd path in gconf.

---

### Post by Darkshade on 2009-09-01
> **tekstr1der said:**
> ```
notify-osd (0.9.20-0ubuntu1) karmic; urgency=low

  * New upstream version:
    - added support for integer gconf-key "/apps/notify-osd/gravity"
    - supported values are 1 (NorthEast, top-right) and 2 (East, vertically centered at right of screen)
    - switch back default positioning to NorthEast (top-right)

```

Gee, if they just added SouthEast for all the bottom-panel users, I think almost everyone would be happy.

I have only 1 top panel and Gnome-Do in docky mode on the bottom and I'd still appreciate a SouthEast option (:

---

### Post by shakaran on 2009-09-01
> **Darkshade said:**
> I have only 1 top panel and Gnome-Do in docky mode on the bottom and I'd still appreciate a SouthEast option (:

From Mark Shuttleworth moments ago:
[https://lists.launchpad.net/ayatana/msg00589.html](https://lists.launchpad.net/ayatana/msg00589.html)

> 
Luke Benstead wrote:
> I've just seen this:
>
> "notify-osd (0.9.20-0ubuntu1) karmic; urgency=low
>
>   * New upstream version:
>     - added support for integer gconf-key "/apps/notify-osd/gravity"
>     - supported values are 1 (NorthEast, top-right) and 2 (East,
> vertically centered at right of screen)
>     - switch back default positioning to NorthEast (top-right)"
>
> Just wanted to say thank you to whoever is responsible for providing the choice.
>   

That may not be there in the final version, it's there now to facilitate testing.

Mark

---

### Post by ELD on 2009-09-01
Well someone just need to keep making an alternative PPA most of us can switch to if they release it with a stupid position.

---

### Post by bear24rw on 2009-09-01
i REALLY dont understand why it would be such a problem to let the user configure settings for it, without configurablility it seems like it goes against the open source ideas. the prefrences dont even have to be in a gui just give me a conf file and ill be content..

---

### Post by froggyswamp on 2009-09-01
> **bear24rw said:**
> i REALLY dont understand why it would be such a problem to let the user configure settings for it, without configurablility it seems like it goes against the open source ideas. the prefrences dont even have to be in a gui just give me a conf file and ill be content..
+1
Plus Mark seems to confuse simplicity with usefulness, I need there to be a button to close it immediately if I need, or at least an option to let it have a close button, you know, almost every notification system has such a button which is useful.

---

### Post by bear24rw on 2009-09-01
> **froggyswamp said:**
>  an option to let it have a close button, you know, almost every notification system has such a button which is useful.

Agreed, I would love if you could click and close the bubbles.. dont understand why they choose to go with the "user cant control anything" way of thinking..

---

### Post by Paqman on 2009-09-01
> **bear24rw said:**
> Agreed, I would love if you could click and close the bubbles.. dont understand why they choose to go with the "user cant control anything" way of thinking..

Because it's not supposed to require any interaction. They're just notifications. If the user starts interacting with the bubbles, then the bubble has interupted his/her workflow, which is bad.

---

### Post by bear24rw on 2009-09-02
> **Paqman said:**
> Because it's not supposed to require any interaction. They're just notifications. If the user starts interacting with the bubbles, then the bubble has interupted his/her workflow, which is bad.

I understand, but it would interupt them no more than how it currently is.. the bubbles would be exactly the same (they go away after n seconds) but i personally would like the ability to click on it and have it go away immediately. I find the length of time for some of the bubbles to be to great and they get annoying after ive already read what they have had to say. just my opinion..

---

### Post by kansasnoob on 2009-09-02
> **bear24rw said:**
> I understand, but it would interupt them no more than how it currently is.. the bubbles would be exactly the same (they go away after n seconds) but i personally would like the ability to click on it and have it go away immediately. I find the length of time for some of the bubbles to be to great and they get annoying after ive already read what they have had to say. just my opinion..

Being visually impaired, my situation is just the opposite, I need the notifications to remain until I've had time to focus on and read them.

Thus the need for notify-osd to be user configurable. No one position or length of time displayed will suit every individual.

---

### Post by Kazade on 2009-09-02
> **kansasnoob said:**
> Being visually impaired, my situation is just the opposite, I need the notifications to remain until I've had time to focus on and read them.

This. We need to make sure that Mark et. al. understand it's not just about what people want, it's what they *need* to make use of the notifications. I would suggest that anyone with concerns about this reply to this email thread: [https://lists.launchpad.net/ayatana/msg00589.html](https://lists.launchpad.net/ayatana/msg00589.html)

I don't think anyone from the team reads the forums.

(If you aren't signed up to the ayatana list, sign up then make sure your subject line is "Re: [Ayatana] Notify OSD: Talk about giving the user preferences" and the online threader will understand that it's part of the thread).

---

### Post by bear24rw on 2009-09-02
I just noticed that my notify-osd is back to top right (:)), same for everyone else?

---

### Post by Aries K on 2009-09-02
Yep same here, it's back where it was originally.

---

### Post by isecore on 2009-09-03
> **bear24rw said:**
> I just noticed that my notify-osd is back to top right (:)), same for everyone else?

Affirmative.

---

### Post by Seventh Reign on 2009-09-03
The Notifications should not be at the Top Right, or the Bottom Right, or the Top Left, or the Bottom Left, or the Top, Bottom, Left or Right.

There should be a configuration to let us choose where they appear.  Afteral that IS one of the best things about Linux isnt it .. Choice?

---

### Post by ELD on 2009-09-03
> **Seventh Reign said:**
> The Notifications should not be at the Top Right, or the Bottom Right, or the Top Left, or the Bottom Left, or the Top, Bottom, Left or Right.

There should be a configuration to let us choose where they appear.  Afteral that IS one of the best things about Linux isnt it .. Choice?

Your right, all along i've asked to be able to change it, seems like canonical doesn't want it to be a community anymore...rather what they say, goes.

---

### Post by taavikko on 2009-09-03
> **ELD said:**
> Your right, all along i've asked to be able to change it, seems like canonical doesn't want it to be a community anymore...rather what they say, goes.

There's already a new version which let's you change the place (though pretty minimal choice)

```
notify-osd (0.9.20-0ubuntu1) karmic; urgency=low

  * New upstream version:
    - added support for integer gconf-key "/apps/notify-osd/gravity"
    - supported values are 1 (NorthEast, top-right) and 2 (East, vertically centered at right of screen)
    - switch back default positioning to NorthEast (top-right)

```

They can't wait for the opinion of users, you just can't please everyone.

---

### Post by Kazade on 2009-09-03
> **taavikko said:**
> There's already a new version which let's you change the place (though pretty minimal choice)

Mark himself said that's just there to facilitate testing and may not be permanent.

---

### Post by mapuo on 2009-09-03
```
notify-osd (0.9.20-0ubuntu1) karmic; urgency=low

  * New upstream version:
    - added support for integer gconf-key "/apps/notify-osd/gravity"
    - supported values are 1 (NorthEast, top-right) and 2 (East, vertically centered at right of screen)
    - switch back default positioning to NorthEast (top-right)

```

ok, can someone please explain to me step by step how to use the gconf-editor or whatever tool to change the gravity of the notifications?
i can not see the "/apps/notify-osd/" directory, nor the "/apps/notify-osd/gravity" key in the gconf-editor.
how can i create them?
or should they be created by the package?

---

### Post by unimatrix on 2009-10-02
> **mapuo said:**
> ```
notify-osd (0.9.20-0ubuntu1) karmic; urgency=low

  * New upstream version:
    - added support for integer gconf-key "/apps/notify-osd/gravity"
    - supported values are 1 (NorthEast, top-right) and 2 (East, vertically centered at right of screen)
    - switch back default positioning to NorthEast (top-right)

```

ok, can someone please explain to me step by step how to use the gconf-editor or whatever tool to change the gravity of the notifications?
i can not see the "/apps/notify-osd/" directory, nor the "/apps/notify-osd/gravity" key in the gconf-editor.
how can i create them?
or should they be created by the package?

I Second that.

---

### Post by Forlong on 2009-10-09
Third

---

### Post by dustigroove on 2009-10-15
> **mapuo said:**
> ok, can someone please explain to me step by step how to use the gconf-editor or whatever tool to change the gravity of the notifications?
i can not see the "/apps/notify-osd/" directory, nor the "/apps/notify-osd/gravity" key in the gconf-editor.
how can i create them?
or should they be created by the package?

Here's how to create and utilize the gravity entry for gconf.

Create the directory and entry:
```
mkdir -p ~/.gconf/apps/notify-osd/ && touch ~/.gconf/apps/notify-osd/%gconf.xml
```

Now edit the entry:
```
gedit ~/.gconf/apps/notify-osd/%gconf.xml &
```

Now paste the following into the file and save:
```
<?xml version="1.0"?>
<gconf>
	<entry name="gravity" type="int" value="2"/>
</gconf>
```

Now you should be able to just log out and back in and the entry will appear in gconf-editor. Changing the integer value of the entry will change the position.


The options currently are:

	1 (NorthEast, top-right)
	2 (East, vertically centered at right of screen)

---

### Post by dustigroove on 2009-10-15
Once the instructions from my above post are followed, you can test it use these commands once notify-osd is started:

```
gconftool-2 --set /apps/notify-osd/gravity --type int 1
```

or

```
gconftool-2 --set /apps/notify-osd/gravity --type int 2
```

and send a test message using:

```
notify-send "test" "this is a test"
```


Hope this helps...

---

