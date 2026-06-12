---
title: "Icons missing from menus and user switch applet"
date: 2009-07-31
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2009-07-31
Anyone else seen icons go missing? I'm trying to determine if it is a problem from a recent update from last night or something else amiss on my setup. Icons have gone missing from the System and Places options in the Gnome menu, from all drop down menus in all GTK programs and the icon has gone from my user switch applet (even though the icon still exists on my computer and shows up in my personal information).

---

### Post by terry_gardener on 2009-07-31
yes i have noticed this also. would like them back

---

### Post by tghe-retford on 2009-07-31
Started a bug report:

[https://bugs.launchpad.net/ubuntu/+bug/407474](https://bugs.launchpad.net/ubuntu/+bug/407474)

---

### Post by Jay_Bee on 2009-07-31
I think that's the intended behavior.
You can change it in System>Preferences>Appearance>Interface (check Show icons in menus)

---

### Post by tghe-retford on 2009-07-31
> **Jay_Bee said:**
> I think that's the intended behavior.
You can change it in System>Preferences>Appearance>Interface (check Show icons in menus)
That fixed the problem, but its never been intended in the past, an update has caused that check box to be unchecked. Surely this is a step backwards if it was intentional?

---

### Post by phenest on 2009-07-31
In fact, hiding menu icons in Jaunty hides all the icons in the menu and not just Places & System.

So it is a bug.

---

### Post by Jay_Bee on 2009-07-31
Yes but that is a different issue. My Places and System icons are showing up fine, I just don't have icons in the right click and dropdown menus and GDM applet.

EDIT: Removing icons from the menus was discussed before, but I don't remember what the decision was, I believe that Ubuntu will follow whatever upstream suggests. For example, you might also notice that the toolbar button label is now beside the button, not under it.
It's nice to see some experimenting, these alphas were kind of boring.

---

### Post by phenest on 2009-07-31
> **Jay_Bee said:**
> Yes but that is a different issue. My Places and System icons are showing up fine, I just don't have icons in the right click and dropdown menus and GDM applet.

EDIT: Removing icons from the menus was discussed before, but I don't remember what the decision was, I believe that Ubuntu will follow whatever upstream suggests. For example, you might also notice that the toolbar button label is now beside the button, not under it.
It's nice to see some experimenting, these alphas were kind of boring.

Text beside icons is available in Jaunty too. They've only changed the default.
But the missing icons in menus is still an issue. And appears to refer to any menu.

---

### Post by kiddo on 2009-07-31
Rejoice. It's intended behavior by the upstream gtk developers now. I have to say, this decision is moronic. I argued tooth-and-nail against removing icons from menus, and they did it anyway.

Here is the bug report that caused this: [http://bugzilla.gnome.org/show_bug.cgi?id=557469](http://bugzilla.gnome.org/show_bug.cgi?id=557469)

---

### Post by ranch hand on 2009-08-01
Graven images are evil, Evil, EVIL!!!!!!!!

---

### Post by mrsurb on 2009-08-01
I could have lived with it, except that it also disappeared the icons beside my menu items in my Firefox (Shiretoko) bookmarks and history menus! In other places the icons might just be window dressing, but they're really useful visual cues in long lists of web sites.

---

### Post by deathsshadow77 on 2009-08-01
I definitely dont think this should be default behavior. Smaller icons would be nice but no icons isnt useful.

---

### Post by dino99 on 2009-08-01
gtk designers & the pre-historic cavemen artists:

remenber that cavemen , in their sweat home, already had icons.

Is that the crisis result ?

---

### Post by phenest on 2009-08-01
So, this has happened to follow suit with OSX and Windows? That should never be a reason for anything!

Nobody should be experiencing a performance hit because of some icons.

I will switch mine on.

---

### Post by Jay_Bee on 2009-08-01
I'll give their idea a chance and see how it goes. 
I think I'll be fine as long as it's easy do change the option if I choose to do so.

---

### Post by tghe-retford on 2009-08-01
At least we still have the option to switch icons back on if we wish. If they decide to remove that option in future (and looking through the Gnome bug report, there are people who want to do this!), and tell us "it's our way or the highway". I would seriously consider going back to KDE. I stopped using Pidgin and started using Emesene because of a similar unfathomable reason to not allow the text entry to be resized and because of the developers solid stance that they would not consider adding an option to change that behaviour.

Going through the Gnome bug report makes for interesting reading. Mozilla are also considering a bug report to remove all of their icons too, or at the very least, scale them back, and OpenSUSE is also considering disabling all icons for their 11.2 release (although at least they are still giving you a choice to re-enable them). They're also requesting KDE/QT respect what has been done by Gnome and also disable icons.

[http://bugzilla.gnome.org/show_bug.cgi?id=557469](http://bugzilla.gnome.org/show_bug.cgi?id=557469)

Icons in buttons have also been disabled. To get those back, do this:

```
gconftool-2 --type bool --set /desktop/gnome/interface/buttons_have_icons true

```

I still think this is a step backwards, and if they disable icons totally, I will seriously consider using KDE as a desktop environment in future, who at least still have icons as default. Although I fear, as things do, icons could be a thing of the past if the rhetoric of developers is true.
 
EDIT: And now my bug report is marked as invalid and a duplicate to a **_later_** report. What's going on? :-x

---

### Post by tghe-retford on 2009-08-01
> **phenest said:**
> In fact, hiding menu icons in Jaunty hides all the icons in the menu and not just Places & System.

So it is a bug.
Looking on the Gnome report, and the linked video to the said behaviour, that's intentional too. In fact, if you see from my screenshot of the Gnome menu, mine hasn't done that for some reason (well, until I turned icons back on).

---

### Post by phenest on 2009-08-01
> **tghe-retford said:**
> Looking on the Gnome report, and the linked video to the said behaviour, that's intentional too. In fact, if you see from my screenshot of the Gnome menu, mine hasn't done that for some reason (well, until I turned icons back on).

Well done Gnome team! What genius thought of that? Pointless and a waste of effort and time. The whole idea of having a graphical environment, is to have graphics. They really should start thinking of competing with KDE more, and less with MS and Apple. I use AWN because Gnome panels are so dull. If performance is an issue: use XFCE!

---

### Post by dino99 on 2009-08-01
first i've modified System/preference/apparence/interface to true,
second run "gconftool-2 --type bool --set /desktop/gnome/interface/buttons_have_icons true"

but no more icons with firefox: nightmare with bookmarks (need to rewrite the properties of most url to know on which one i click)

What happens in the Gnome world & some distro ?
<snip>

Do they promote next: remove menu, green letters on black background or only command line console ?

---

### Post by tghe-retford on 2009-08-01
> **dino99 said:**
> but no more icons with firefox: nightmare with bookmarks (need to rewrite the properties of most url to know on which one i click)
This may be of interest:

[https://bugzilla.mozilla.org/show_bug.cgi?id=504275](https://bugzilla.mozilla.org/show_bug.cgi?id=504275)

---

### Post by Marat89 on 2009-08-01
oh my god, whats going on with Gnome devs?? WTF sry..

Instead of wasting time they could fix bugs, provide more functions and eyecandy.


Im thinking of switching to KDE now.
I think we have a bunch of regressions, like volume-control applet? wtf why use the new one, it has fewer options/functions-->Ugly

FUSA=Regression all the way. 

Im very sorry of this post, but every time I look on the development I get headaches. Now you could say, make it better. But I cant, because im not a dev. Some Devs dont concentrate on the real problems, real UI issues, paper-cuts.

No icons= Papcercut No 1.

What is the matter of performance boost? Wow 0.00001 ms boost . Wow.. really this beats all.

---

### Post by Kazade on 2009-08-01
Actually, I quite like it...

I was all ready to rant about how this is another stupid default change *cough*update notifier*cough*. But actually, the menus do look a lot cleaner without the icons. I do agree that icons in menus are needed sometimes, like in the Firefox bookmarks menu, if they fix that, then I am quite happy with this change.

P.S. Please tell me that they are restoring the update notification icon for Karmic! Worst. Decision. Ever.

---

### Post by Durden on 2009-08-01
If this stays I'm done with gnome. As much as I hate KDE at least they aren't constantly regressing their features to pre-1995 standards.

---

### Post by Marat89 on 2009-08-01
+1 for Durden

---

### Post by tghe-retford on 2009-08-01
Already have switched to Kubuntu.













<---

---

### Post by Marat89 on 2009-08-01
NOW switched to kubuntu ..

---

### Post by buzzmandt on 2009-08-01
switched to kubuntu about 2 weeks ago. 

Almost makes me wonder if what they're doing is setting it up to make gnome 3 look good.

---

### Post by Mr. Picklesworth on 2009-08-01
Well, in fairness, the reason for removing icons (in SOME cases) was that they were mainly for the stock widgets, but custom menu items that don't have stock icons to choose from generally go completely without. This draws the user's attention to common menu items like Undo or Copy, instead of to things that are important for the task at hand. That results in a very distracting, jumpy interface where the user's focus is meant to be on things that are given less prominance.

I thought the plan was more finely tuned, including a change to the HIG and a movement towards *simplified* icons in menus for applications. Right now, this is more of a lazy solution.

Guys, if you want this to be solved right, don't just drop threats, please. Instead, you can help do it right by contributing what needs to be done. Primarily that'll be bug reports and realistic mockups: where specifically do we not need icons and where specifically do we need them?

Also, please don't jump to conclusions. I'm not following this very closely; it's quite possible that the change is to test the waters, as a mass experiment to see just how important menu icons are in a practical sense.

---

### Post by Durden on 2009-08-01
Sorry but no. The gnome devs have pulled this crap on us too many times. The time for tolerance and patience is over. I'm switching to Kubuntu. Gnome devs think they know what's best for everyone. I'm tired of fighting against the interface. I don't need that crap.

---

### Post by Mr. Picklesworth on 2009-08-01
> **Durden said:**
> Sorry but no. The gnome devs have pulled this crap on us too many times. The time for tolerance and patience is over. I'm switching to Kubuntu. Gnome devs think they know what's best for everyone. I'm tired of fighting against the interface. I don't need that crap.

Durden, do you realize that this is a development release? The goal is to be constructive. We're the guinee pigs. By running this, you are *asking* to be a guinee pig. Isn't it awesome that the developers are bouncing ideas off of us instead of jamming them in at the last second; that the people doing the testing are those who asked, instead of end users?
Who else is going to test this if not the testers?

The GNOME devs aren't fighting you. Yes, the overarching goal here is to relocate interface prefs to an optional tweak-ui kind of app, but this is upon a valid realization that the reason the interface preferences exist is due to bad defaults. People go to change toolbar styles because text under icons looks ugly, but because it's default lots of apps (Olive, for example) don't work any other way. Lots of users stick with the defaults and never see the far better looking GNOME (via nicer toolbar settings).
Hence the goal of finding new defaults.

If you don't want to contribute to these kinds of experiments, I suggest that you run a stable release and wait until this is stable.

---

### Post by psyke83 on 2009-08-02
> **Mr. Picklesworth said:**
> Durden, do you realize that this is a development release? The goal is to be constructive. We're the guinee pigs. By running this, you are *asking* to be a guinee pig. Isn't it awesome that the developers are bouncing ideas off of us instead of jamming them in at the last second; that the people doing the testing are those who asked, instead of end users?
Who else is going to test this if not the testers?

The GNOME devs aren't fighting you. Yes, the overarching goal here is to relocate interface prefs to an optional tweak-ui kind of app, but this is upon a valid realization that the reason the interface preferences exist is due to bad defaults. People go to change toolbar styles because text under icons looks ugly, but because it's default lots of apps (Olive, for example) don't work any other way. Lots of users stick with the defaults and never see the far better looking GNOME (via nicer toolbar settings).
Hence the goal of finding new defaults.

If you don't want to contribute to these kinds of experiments, I suggest that you run a stable release and wait until this is stable.

Karmic being in development has no bearing on this issue. The decision to change this behaviour was made by the GNOME developers - it's up to the distributions to customize these settings (though I fear that's not going to happen).

---

### Post by phenest on 2009-08-02
Personally, If all the Gnome devs are going to do is change a default setting, then I'll just change it back. I may have said something earlier about moving to KDE, but not for the sake of a default setting.

Although I do feel that the change should not be in the form of an update. If the Live CD or a new install has that setting switched off, that's fine. But to change my settings by way of an update, is outrageous.

---

### Post by dino99 on 2009-08-02
you forget one thing:

last upgrades (gnome-setting i guess) have drop all favicons without any users choice !!!

These devs decide by themselves on irc a no way back change, are they dreaming about the early 80's and comes to promote a basic interface removing menu, html & so on ? 
Who can believe seriously on such choice ?

Community dont need "charia" managing our future.
Long time ago, cavemen already had icons on theirs sweat home.

If devs are building something better, it's good but they might let users make the choice for themselves.
They act like terrorists & i dont follow these silly decisions and distro following them.

---

### Post by tghe-retford on 2009-08-02
To be honest, it's not just this issue which has me going back to Kubuntu:
[LIST]
[*]Ubuntu's Notify OSD is beautiful, but it doesn't respect my panel being at the bottom of the screen - and this is in a stable release. I could have gone back to the old notifications, but KDE manages to have a beautiful notification system which respects where my panel is.
[*]I originally switched to Gnome because KDE 4.0 was too bug ridden and crippled to do anything with, and KDE 3 had been removed. KDE 4.3 RC3 still has a few faults (sound!!!), but it is now far more stable than it used to be (well, for a release candidate and a development version of Ubuntu it is!).
[*]I'm getting a distinct feeling we're going down the "it's our way or the highway" approach to this issue, particularly if other distributions and programs are to be encouraged, if not told to remove icons from their applications, as I get the feeling from the Gnome bug report. I'm a person who works better with graphical representations of actions and programs, and will only drop down to command line if I need to. It feels to me this is aiming to be a repeat of the Pidgin text box issue where they told users to either put up with a non-resizable text box or go elsewhere. It wasn't a case of it's free software and you should be thankful, but the attitude to the changes and people who were affected and suggesting rational solutions feeling ignored. Even the suggestion of adding an option to bring back the old behaviour was dismissed outright by the developers. I left Pidgin after that and went to Emesene because I exclusively use MSN, as do my friends. Back to the icons, we have had suggestions that the option to switch icons back on should be removed and this idea enforced on all users, so phenest's idea to switch the icons back on wouldn't work then.
[/LIST]

My choice to switch to Kubuntu now is a personal one, considering I have already used KDE originally in the past.

---

### Post by Kazade on 2009-08-02
I do think people are over-reacting slightly to this particular issue, the more I think about it, the more I think it makes sense. Read this blog post: [http://www.andreasn.se/blog/?p=103](http://www.andreasn.se/blog/?p=103) GNOME aren't removing ALL of the icons, just cutting down on them. The first step is to turn them all off then developers can override that setting in their programs. I think it's a very good long term decision, but a bit of notice in more places would have been nice!

However, I totally agree with the worry that there is a very "our way or the high way" vibe coming from Ubuntu in relation to the Notification system. It should be possible to change the location of the OSD and it would be nice to be able to customize the colour to match the desktop theme also. It was definitely the wrong decision to start popping up (pop-under whatever) the update window. Thankfully, you can turn off the pop-under behaviour AND I guarantee that if in Karmic notify-osd doesn't allow customization someone will come along, fork it and provide a PPA. It's bound to happen.

---

### Post by Mr. Picklesworth on 2009-08-02
> **phenest said:**
> Although I do feel that the change should not be in the form of an update. If the Live CD or a new install has that setting switched off, that's fine. But to change my settings by way of an update, is outrageous.The way this works is that the system-wide *default* setting has been changed. Because you never explicitly stated a preference for your account, gconf picks up that default and uses it. This is ordinary behaviour and is not touching user folders or doing anything outrageous. It happens all the time.

And that's a good thing, because the experiment wouldn't work without that functionality.

Would be pretty cool if it notified about gconf settings changes automatically, though.

> **dino99 said:**
> They act like terrorists & i dont follow these silly decisions and distro following them.
You are being completely hostile towards experimentation. You are abusing developers for experimenting with (working with) their unstable development snapshots; no different from complaining about unfinished in-progress features in an unreleased product. That is not cool.

---

### Post by phenest on 2009-08-02
> **Mr. Picklesworth said:**
> The way this works is that the system-wide *default* setting has been changed. Because you never explicitly stated a preference for your account, gconf picks up that default and uses it. This is ordinary behaviour and is not touching user folders or doing anything outrageous. It happens all the time.

And that's a good thing, because the experiment wouldn't work without that functionality.

Would be pretty cool if it notified about gconf settings changes automatically, though.

Hmmm, ok. Thanks for explaining that. Then notification would, as you say, be cool!

---

### Post by Durden on 2009-08-02
Rationalize it all you want. Make all the blog posts you want. Tell us it's "better for us" all you like. It doesn't make it true.

I don't give a rats *** what the gnome devs do anymore. They are their own worst enemy. I've dealt with their ignorance for almost 12 years. Screw them, I'm done.

Gnome isn't the only show in town and if Ubuntu intends to hitch all their wagons to this dying pony then they are in for a sorry surprise. Kubuntu is a far better option now.

---

### Post by Jay_Bee on 2009-08-02
Durden nobody is forcing you to use Gnome (let alone for 12 years), so if that setting is so difficult for you to change and you are happy with KDE then go use Kubuntu and be happy. Kubuntu probably needs more testers.

---

### Post by Durden on 2009-08-02
> **Jay_Bee said:**
> Durden nobody is forcing you to use Gnome (let alone for 12 years), so if that setting is so difficult for you to change and you are happy with KDE then go use Kubuntu and be happy. Kubuntu probably needs more testers.

Thank you Captain Obvious. That's exactly what I did if you hadn't been following the farking thread. Go troll elsewhere.

---

### Post by Jay_Bee on 2009-08-02
I really think you should read this before you post like that again -> [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

---

### Post by Durden on 2009-08-02
Did I hurt your feelings? Poor you.

---

### Post by ranch hand on 2009-08-02
OK, I have been watching this thread with a grin.  It is getting a little too heated for humor.

Maybe someone would tell me what the hysteria is about.  Yes, none of my right clik menus have icons.  All other menus do.

To tell the truth I could not tell you if the right click menus ever HAD icons.  I certainly never remember an icon for "save image as" or "bookmark this page" or "create document" or "Change Desktop Background".

I am currently on a fresh install, on 2 partitions, of A3, updated daily.

---

### Post by lonniehenry on 2009-08-02
The tone of this thread has changed and has gotten uncivil.  Time for a moderator to remind everyone that the forums are to help users solve problems and guide users to be better informed.  It is not a place for personal attacks. The main reason that I came to Ubuntu was the usefulness of the forums and the respect that was given to all users no matter if they were noobs or experienced users.

---

### Post by wayne_cat on 2009-08-02
The Ubuntu gnome version loses more and more features. Is there a good "source" for information about the design ideas of Gnone 2.27.

---

### Post by 23meg on 2009-08-02
Please keep it civil. Flat out refusing to make an effort to understand the rationale of people you disagree with is your problem, but if you top that with personal attacks, it becomes a broader problem. 

I've edited out some of the extreme remarks. Unless people keep it civil, the thread will be closed.

---

### Post by zekopeko on 2009-08-02
Here is what Gnome developers want:

[Apple UI guidelines]("http://developer.apple.com/documentation/UserExperience/Conceptual/AppleHIGuidelines/XHIGMenus/XHIGMenus.html#//apple_ref/doc/uid/TP30000356-TPXREF116")

Disabling menu icons is just the first step in a greater scheme of things to come.

I truly don't understand the negative attitude from some people here. This is a development release. User testing is a part of it. If you don't like it then use a stable release.

A far greater (user visible) change happened in Hardy with setting the dark theme as default. And guess what? A bunch of bug reports against GTK+ were filed and that helped the devs improve theming.
Testing Ubuntu is a privilege not a right.

---

### Post by tghe-retford on 2009-08-02
There is also discussion ongoing to remove the Interface tab of the Appearance capplet, so the suggestion to re-enable icons from that tab may soon be unavailable:

[http://mail.gnome.org/archives/gnomecc-list/2009-July/msg00015.html](http://mail.gnome.org/archives/gnomecc-list/2009-July/msg00015.html)

---

### Post by zekopeko on 2009-08-02
> **tghe-retford said:**
> There is also discussion ongoing to remove the Interface tab of the Appearance capplet, so the suggestion to re-enable icons from that tab may soon be unavailable:

[http://mail.gnome.org/archives/gnomecc-list/2009-July/msg00015.html](http://mail.gnome.org/archives/gnomecc-list/2009-July/msg00015.html)

gconf/dconf FTW!

---

### Post by ranch hand on 2009-08-02
> **tghe-retford said:**
> There is also discussion ongoing to remove the Interface tab of the Appearance capplet, so the suggestion to re-enable icons from that tab may soon be unavailable:

[http://mail.gnome.org/archives/gnomecc-list/2009-July/msg00015.html](http://mail.gnome.org/archives/gnomecc-list/2009-July/msg00015.html)
And they all seem to agree that "text beside ICONS" is the way to go.  I still see no reason to get in a lather about this.

If there is real concern here, the thing to do is contact those involved and let them know what you prefer.  This will be more effective with out invective phrasing.

---

### Post by phenest on 2009-08-02
> **tghe-retford said:**
> There is also discussion ongoing to remove the Interface tab of the Appearance capplet, so the suggestion to re-enable icons from that tab may soon be unavailable:

[http://mail.gnome.org/archives/gnomecc-list/2009-July/msg00015.html](http://mail.gnome.org/archives/gnomecc-list/2009-July/msg00015.html)

And seeing as I got upset about the default setting changing, I guess I've never used it anyway.

---

### Post by wayne_cat on 2009-08-02
> **zekopeko said:**
> Here is what Gnome developers want:

[Apple UI guidelines]("http://developer.apple.com/documentation/UserExperience/Conceptual/AppleHIGuidelines/XHIGMenus/XHIGMenus.html#//apple_ref/doc/uid/TP30000356-TPXREF116")

Disabling menu icons is just the first step in a greater scheme of things to come.

I truly don't understand the negative attitude from some people here. This is a development release. User testing is a part of it. If you don't like it then use a stable release.

A far greater (user visible) change happened in Hardy with setting the dark theme as default. And guess what? A bunch of bug reports against GTK+ were filed and that helped the devs improve theming.
Testing Ubuntu is a privilege not a right.

zekopeko, I'm a little bit confused after reading the Apple UI guidelines

```
If you do include icons in your menus, include them only for menu items for 
which they add significant value; don’t include them for every menu item. A menu 
that includes too many icons (or poorly designed ones) can appear cluttered and 
be hard to read.
```I agree to this ... but I think the icons in front of the group name in the "application menu" / application names in the sub menus add a significant value.

It is hard to tell if it was a good idea to remove them ... maybe I will understand it after the first release of the new design (August 27th Artwork First Drop).

---

### Post by Mr. Picklesworth on 2009-08-02
Here's another point against having icons for everything: Right now, a menu item can either have an icon or a check box; it can't have both. Broken, eh? :P

It works better for Apple because icons are in line with text (instead of in their own column to the left), which is possible because there is way more order in which menu items have icons and which don't. If that happened as things are in GTK, it would be hard to read menus with the starts of the text labels zig-zagging.

---

### Post by tghe-retford on 2009-08-02
> **zekopeko said:**
> I truly don't understand the negative attitude from some people here. This is a development release. User testing is a part of it. If you don't like it then use a stable release.
Considering its support from developers, some users and one article I have read reporting the change tonight, I fear this will become a permanent change. Now, someone could downgrade to Jaunty, but that kind of defeats the purpose of testing and of course, when Karmic is released, the same problem will re-occur. My concerns are that the options to re-enable the icons are being taken away and I have a niggling feeling about whether we would still be able to use the configuration editor or the command line to re-enable the icons in future.

As I mentioned, I was a Kubuntu user pre KDE4, and this has been a good time to re-evaluate KDE or Gnome, and I have personally decided to go back to KDE considering the progress with KDE4. But that's my own decision, others will feel differently. I just fear the potential of some backlash come October when Karmic is released as stable and users ask in good faith where the icons have gone.

---

### Post by phenest on 2009-08-02
Now we all know this behaviour is intended, this thread is really now only about personal preference.

I don't see this as a bad move at all. It's all about keeping things clean and tidy. But remember, Gnome isn't about being configurable. That's what KDE is there for.

To Gnome or not to Gnome? That is the question.

---

### Post by BwackNinja on 2009-08-02
Hmm... what bothers me about menus with both icons and no icons or checkboxes and no icons, etc is that each menuitem isn't the same size.

---

### Post by zekopeko on 2009-08-02
> **wayne_cat said:**
> zekopeko, I'm a little bit confused after reading the Apple UI guidelines

```
If you do include icons in your menus, include them only for menu items for 
which they add significant value; don&#8217;t include them for every menu item. A menu 
that includes too many icons (or poorly designed ones) can appear cluttered and 
be hard to read.
```I agree to this ... but I think the icons in front of the group name in the "application menu" / application names in the sub menus add a significant value.

It is hard to tell if it was a good idea to remove them ... maybe I will understand it after the first release of the new design (August 27th Artwork First Drop).

Here is a proposal as to what should have icons:

[http://bugzilla.gnome.org/show_bug.cgi?id=557469#c1](http://bugzilla.gnome.org/show_bug.cgi?id=557469#c1)

So applications, users, devices (and I guess bookmarks).
Application menu just has to be fixed.

The best thing to do would be to follow the Apple UI guidelines. That means fixing the applications so as to show only the important menu entries and making menu entries with icons align with the rest of the menu items as seen in the Apple UI.
This is just a hard nudge to the app developers to consider what are important UI elements and fix apps.

Here is an example of menu icon overload: [http://gnomefx.mozdev.org/blue-file.png](http://gnomefx.mozdev.org/blue-file.png)

---

### Post by buzzmandt on 2009-08-02
I have (at least almost always) prefered kde, I really really started liking kde4 at 4.1 but was really buggy and have been using gnome, 4.2 was more stable but still not there.  4.3 is really good and I've made the decision to return to my fav DE. 

My decision to switch WAS in part because I think the gnome devs are going a bit too far with the KISS (keep it simple stupid) philosophy.  I will probably always have both gnome and kde on each of my machines, just always have, always have liked both.  I'm also keeping gnome on here to continue testing/feed back for the development process, That's what I signed up for and I enjoy the surprises whether good or bad.

BUT:  the last few replies have made me think they have a "copy Apple's guidelines philosophy".  I also think that some of the decisions made now have got to be a lead into gnome 3.  

I have no problem with the default being no icons but it should be a changeable option to icon or not to icon.  One of the things I've heard said is if ubuntu is in stores on display, it will be on display with the default settings.  I don't think this is a good "show off" strategy.

---

### Post by zekopeko on 2009-08-02
> **buzzmandt said:**
> My decision to switch WAS in part because I think the gnome devs are going a bit too far with the KISS (keep it simple stupid) philosophy.  I will probably always have both gnome and kde on each of my machines, just always have, always have liked both.  I'm also keeping gnome on here to continue testing/feed back for the development process, That's what I signed up for and I enjoy the surprises whether good or bad.

One thing I don't like with KDE philosophy is the overabundance of UI options for tweaking. In KDE4 they are trying to unify Gnome and Windows design philosophy and they aren't doing a great job IMO. One thing I like about Gnome is that they don't disable your options but put them in gconf if they aren't going to be used in 95% of the cases. Makes for a less cluttered UI while having the flexibility.

> BUT:  the last few replies have made me think they have a "copy Apple's guidelines philosophy".  I also think that some of the decisions made now have got to be a lead into gnome 3.

Vista/7 also apply the same design for menus. If you are going to copy somebodies design it should be Apple's. They are pretty much leaders in design usability.

> I have no problem with the default being no icons but it should be a changeable option to icon or not to icon.  One of the things I've heard said is if ubuntu is in stores on display, it will be on display with the default settings.  I don't think this is a good "show off" strategy.

One thing that most people in this thread missed was that this is only the first step toward general menu redesign. Icons will still be present but not in such abundance. Look at the screenshot in my post above. Would you say that having an icon for every menu entry is not cluttering the menus?

---

### Post by wayne_cat on 2009-08-02
this is a screenshot of firefox on Mac OS 10.5 ... the menu looks much cleaner 
without the icons. (zekopeko's example is loaded in firefox ... to compare both
looks)

edit: forgot to mention ... look at the keyboard shortcuts in the menu

[[IMG]http://ubuntu-pics.de/thumb/20787/1_gLKB5t.png[/IMG]]("http://ubuntu-pics.de/bild/20787/1_gLKB5t.png")

---

### Post by buzzmandt on 2009-08-02
goog examples, I think I like it.

---

### Post by zekopeko on 2009-08-02
Here is a history menu from firefox on mac: [http://farm4.static.flickr.com/3155/2563206888_53a5b07965_o.png](http://farm4.static.flickr.com/3155/2563206888_53a5b07965_o.png)

Notice that the favicons of websites are aligned with the rest of the menu items. That way you can easily have a check box next to a menu entry that has an icon.

The best thing for Gnome to do is take the Apple approach on menus.

offtopic: I love that the menu corners are curved. MacSlow was hacking on this at one point but don't know what happened of it.
EDIT: found it, [https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish](https://wiki.ubuntu.com/DesktopTeam/Specs/SpitAndPolish)

---

### Post by wayne_cat on 2009-08-02
> **zekopeko said:**
> 
Notice that the favicons of websites are aligned with the rest of the menu items. That way you can easily have a check box next to a menu entry that has an icon.


This is what Apple does ... did not find a better example ... not many icons in
the Mac OS menus 

[[IMG]http://ubuntu-pics.de/thumb/20796/2_75g19c.png[/IMG]]("http://ubuntu-pics.de/bild/20796/2_75g19c.png")

---

### Post by wayne_cat on 2009-08-03
The discussion goes on ... on OSnews:

[http://www.osnews.com/story/21935/GNOME_To_Drop_Icons_in_Buttons_Menus](http://www.osnews.com/story/21935/GNOME_To_Drop_Icons_in_Buttons_Menus)

---

### Post by psyke83 on 2009-08-03
> **wayne_cat said:**
> The discussion goes on ... on OSnews:

[http://www.osnews.com/story/21935/GNOME_To_Drop_Icons_in_Buttons_Menus](http://www.osnews.com/story/21935/GNOME_To_Drop_Icons_in_Buttons_Menus)

Let me summarise that link: "Yes, the decision to remove icons from dialog buttons is great, because it makes the theme more compact".

Before considering the proposal in that link, test the latest version of the Human theme which is not officially released yet (but is available in Kenneth Wimer's PPA, see my signature). We already reduced the default button icon size, which makes the theme more compact **without** sacrificing the use of icons.

For a comparison, see [this]("http://ubuntuforums.org/showpost.php?p=7597314&postcount=37") post.

---

### Post by zekopeko on 2009-08-03
> **psyke83 said:**
> Let me summarise that link: "Yes, the decision to remove icons from dialog buttons is great, because it makes the theme more compact".

Before considering the proposal in that link, test the latest version of the Human theme which is not officially released yet (but is available in Kenneth Wimer's PPA, see my signature). We already reduced the default button icon size, which makes the theme more compact **without** sacrificing the use of icons.

For a comparison, see [this]("http://ubuntuforums.org/showpost.php?p=7597314&postcount=37") post.

The number of icons in the menus is an overkill. I don't have that much in Windows and I never missed them. Look at the Firefox menu in one of my above posts and you will see that it's just overkill.

---

### Post by psyke83 on 2009-08-03
> **zekopeko said:**
> The number of icons in the menus is an overkill. I don't have that much in Windows and I never missed them. Look at the Firefox menu in one of my above posts and you will see that it's just overkill.

Please read my post again. I'm talking about the buttons, not menus.

---

### Post by zekopeko on 2009-08-03
> **psyke83 said:**
> Please read my post again. I'm talking about the buttons, not menus.

Whoops! My bad. Read the bug report. There was a mention of coloring the OK and Cancel buttons. For the rest it's not needed.
And yes, Win and Mac also don't have icons on buttons.

---

