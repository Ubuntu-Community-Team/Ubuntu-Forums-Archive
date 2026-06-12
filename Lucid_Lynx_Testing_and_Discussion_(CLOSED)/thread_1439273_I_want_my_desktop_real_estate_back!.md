---
title: "I want my desktop real estate back!"
date: 2010-03-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by bornagainpenguin on 2010-03-26
Why is Canonical seemingly insisting on making me waste every inch of the desktop they can?  Compare the following:

My Lucid Desktop:


My Hardy netbook:


The biggest offender are the indicator applets, they remain completely unconfigurable!  At least in earlier versions of Ubuntu there were ways to turn things off, I could choose to show just the icon instead of my user name, which at seventeen characters eats up a *lot* of space!  Telling me to change my user name is a joke--why should I have to?

Then there's the indicator applet which requires that I display the evolution email and empathy instant messaging icons just so I can keep my volume controller!  Really smart use of resources Canonical!  Not only do I waste pixels on the panel, I chew up RAM and processing power running an email client I don't ever use...

And what about all those programs that want to run their icons in the system tray as well?  Banshee, OpenOffice.org, Gnome-mplayer, etc!  That doesn't even begin to address the less space available to my shortcuts, now that the system tray is inching its way to the left...

Enough already!  I understand the need for "sane defaults" and I wouldn't really mind any of this if it were configurable. but it seems like with each new release of Ubuntu I lose more and more control over the way my system looks and behaves...

I left behind Microsoft because they insisted on trying to own my computer, I can leave Canonical behind too if they want to play these types of games!

--bornagainpenguin

---

### Post by nhasian on 2010-03-26
yes i see what you mean.  I don't know why monochrome icons are all the rage now.  I prefer nice big colorful icons like on the mac OS dock.

---

### Post by 23meg on 2010-03-26
> **bornagainpenguin]Then there's the indicator applet which requires that I display the evolution email and empathy instant messaging icons just so I can keep my volume controller![/QUOTE]

It doesn't said:**
> Not only do I waste pixels on the panel, I chew up RAM and processing power running an email client I don't ever use...

The messaging menu being on your panel doesn't mean that Evolution is running, unless you launch it.

[QUOTE=bornagainpenguin]And what about all those programs that want to run their icons in the system tray as well? Banshee, OpenOffice.org, Gnome-mplayer, etc! That doesn't even begin to address the less space available to my shortcuts, now that the system tray is inching its way to the left...[/QUOTE]

Disable their icons in their preferences if you don't want them.

---

### Post by bornagainpenguin on 2010-03-26
> **23meg said:**
> It doesn't; just remove the indicator-messages package.

Really?  I'll give it a try then.  What about removing my username from the system tray without losing the new functionality?

**EDIT - Okay that indeed worked.  Thanks!  I was skeptical but I tried it and it worked.**

> **23meg said:**
> Disable their icons in their preferences if you don't want them.

Some of them I do want.  I would just like to be able to pick and choose *which* icons are allowed to appear on my desktop.  It still is my desktop right?  Then let me CONFIGURE the dang thing already!!!!!1111

--bornagainpenguin

---

### Post by bornagainpenguin on 2010-03-26
I just removed the "indicator applet session" and substituted the "shutdown" applet.  So I have my real estate back quite a bit now, but at the cost of reduced functionality.

Why can't there simply be a check in a list box somewhere that allows me to choose whether or not my user name shows in the tray, allowing me to still use the indicator applet session and have the ability to shutdown, log off etc from a menu instead of being forced to use a popup?

--bornagainpenguin

PS: Thanks for those who replied and offered me help with the other half of this issue.

---

### Post by 23meg on 2010-03-30
> **bornagainpenguin said:**
> Some of them I do want.  I would just like to be able to pick and choose *which* icons are allowed to appear on my desktop.  It still is my desktop right?  Then let me CONFIGURE the dang thing already!!!!!1111

Well, right, you can pick and choose them, like you've always been able to. Go to the preferences of the application whose icon you want to remove, and remove it.

> **bornagainpenguin said:**
> Why can't there simply be a check in a list box somewhere that allows me to choose whether or not my user name shows in the tray, allowing me to still use the indicator applet session and have the ability to shutdown, log off etc from a menu instead of being forced to use a popup?

If you just want the session functionality, remove the indicator-me package.

---

### Post by sles on 2010-03-30
> **23meg said:**
> Go to the preferences of the application whose icon you want to remove, and remove it.


Quite obvious, imho, is to have preference menu for such things in applets.
If it is user-friendly OS.
If it is linux, then, I think one program (applet) have to do one thing, not be strange combined thing...

---

### Post by veko on 2010-03-30
Glad to see that I'm not alone.

I myself prefer to use only one panel. With a laptop with 15.6" widescreen, all the vertical space is really needed. One panel should be quite sufficient, but it can easily become too packed with all the icons, notifications, window lists, etc. Therefore I use only the single "Main menu", not the default "Applications and Places", remove the user menu (or whatever it's called) and all the extra notifications.

I'd really like developers to take single panel users into accout: Check how the desktop looks like with one panel only and do that sufficiently often. Make sure it looks equally elegant than the two-panel version, will not be too packed with notification icons, and that the panel does not contain anything that cannot be easily removed and/or placed into menus. Moreover, the size and spacing of panel icons should be easily configurable.

I was going to put this into Ubuntu Brainstorm, but it seems such a trivial idea.

---

### Post by mrsurb on 2010-03-30
As with the original poster, I am running a netbook. This means only one panel, 1024 pixels across.

I find the spacing between the indicator icons annoying. I understand why they are there and why it might be a preferable default, but I wish there were some way to change them.

I also don't think that the advice to apt-get remove indicator-* packages to remove indicator icons is really acceptable if it remains until the release, since this will impact all users of the system, not just the one trying to customise their panel.

A simple "Preferences" option when you right-click on the indicator applet would be useful. You could have checkboxes to display or hide each indicator and an option to change the size of the padding.

---

### Post by emarkay on 2010-03-30
Even us "Big Scren" people hate the "dumbing it down" (removing choices and options and easy configuration tools) and all that wasted space for frilly fluff.  

Fine, put all the goofy things you think we want on our screens, but allow us to easily remove them too!  :)

---

### Post by zekopeko on 2010-03-30
> **emarkay said:**
> Even us "Big Scren" people hate the "dumbing it down" (removing choices and options and easy configuration tools) and all that wasted space for frilly fluff.  

Fine, put all the goofy things you think we want on our screens, but allow us to easily remove them too!  :)

You are having problems figuring out "dumbed down" tools? Really?

---

### Post by zekopeko on 2010-03-30
> **bornagainpenguin said:**
> The biggest offender are the indicator applets, they remain completely unconfigurable!  At least in earlier versions of Ubuntu there were ways to turn things off, I could choose to show just the icon instead of my user name, which at seventeen characters eats up a *lot* of space!  Telling me to change my user name is a joke--why should I have to?

Those options didn't make it into Lucid but they are in the spec.

> Then there's the indicator applet which requires that I display the evolution email and empathy instant messaging icons just so I can keep my volume controller!  Really smart use of resources Canonical!  Not only do I waste pixels on the panel, I chew up RAM and processing power running an email client I don't ever use...

23meg showed you how to remove the messaging menu. Evolution Mail doesn't run and take your precious RAM and CPU. It is in the menu for easy access to it. The same applies to Empathy. Application that are running have an arrow next to their entry in the Messaging menu.[/QUOTE]

> And what about all those programs that want to run their icons in the system tray as well?  Banshee, OpenOffice.org, Gnome-mplayer, etc!  That doesn't even begin to address the less space available to my shortcuts, now that the system tray is inching its way to the left...

23meg, again, explained the basic concept of going to the app specific preferences and toggling the option there. How did you survive with all those notification icons before is beyond me.

> Enough already!  I understand the need for "sane defaults" and I wouldn't really mind any of this if it were configurable. but it seems like with each new release of Ubuntu I lose more and more control over the way my system looks and behaves...

Then perhaps another distro is for you? Ubuntu is catering to a specific segment of users. Perhaps you have out-grown Ubuntu?

> I left behind Microsoft because they insisted on trying to own my computer, I can leave Canonical behind too if they want to play these types of games!

--bornagainpenguin

Now this is just pathetic. Temper tantrums of a petulant child.

---

### Post by emarkay on 2010-03-30
> **zekopeko said:**
> You are having problems figuring out "dumbed down" tools? Really?

No, no probs here, just sticking my 2 pence in regarding the erosion of options; making it hard to customize things.

---

### Post by ktp on 2010-03-30
I was going to post similar thing...find it funny that few release ago, when update icon was removed, it was made a big deal that notification area was being abused by application and such...but now there is more icons/area being used up by default then ever before.  I never use the messaging or email stuff.  In past i would just remove the indicator applet but now i can't do that since other icons are in there.  Oh well...

---

### Post by 23meg on 2010-03-30
> **emarkay said:**
> No, no probs here, just sticking my 2 pence in regarding the erosion of options; making it hard to customize things.

It would help if you took a few minutes to read the threads you post your two pence to; in this case, if you actually read about application indicators replacing the notification area, you'd find out that there's no "erosion of options" or "making it hard to customize things" going on. Applications themselves decide what to do with their indicators, as defined by the spec, and you can disable their indicators just like you could disable their notification area icons. And you can remove the individual indicator applet components that you don't care about, even though the current way may not be optimal (applies to all users). This is a gradual transition and you shouldn't expect things to be perfect overnight.

---

### Post by emarkay on 2010-03-30
> **23meg said:**
> It would help if you took a few minutes to read the threads you post your two pence to; in this case, if you actually read about application indicators replacing the notification area, you'd find out that there's no "erosion of options" or "making it hard to customize things" going on. Applications themselves decide what to do with their indicators, as defined by the spec, and you can disable their indicators just like you could disable their notification area icons. And you can remove the individual indicator applet components that you don't care about, even though the current way may not be optimal (applies to all users). This is a gradual transition and you shouldn't expect things to be perfect overnight.

Semantics, but the point, and not to belabor, is that there are to many "one button does all ideas" and then "no one uses it that way, so let's eliminate that option".  Plus, the gradual shift to the Apple "they'll learn to use our way eventually" mindset is too prevalent, too....

---

### Post by 23meg on 2010-03-30
> **emarkay said:**
> Semantics, 

Facts.

[quote=emarkay]but the point, and not to belabor, is that there are to many "one button does all ideas" and then "no one uses it that way, so let's eliminate that option".  Plus, the gradual shift to the Apple "they'll learn to use our way eventually" mindset is too prevalent, too....[/QUOTE]

And how does that point relate to application indicators vs. the notification area? Right, it doesn't.

<rant>

It would make this forum 100000% more rewarding to participate in for me if people refrained from taking every opportunity to make their opinions on broad issues known in the context of small, specific issues, spreading misinformation and insulting other people's efforts in the process.

Your post is (and frankly, most of your recent posts concerning user-visible changes of any sort are) a prime example of that. So are the posts of the OP in this thread (getting lambasted for taking time to explain things to people is *lovely*!) You're weaving unrelated issues together into an imaginary conspiracy, hijacking other people's threads on specific issues, misinforming the uninitiated, and causing lots of uncalled for negativity.

It would be a welcome change if at least some of the more experienced, frequent posters avoided the above.

</rant>

---

### Post by swoll1980 on 2010-03-30
> **emarkay said:**
> Semantics, but the point, and not to belabor, is that there are to many "one button does all ideas" and then "no one uses it that way, so let's eliminate that option".  Plus, the gradual shift to the Apple "they'll learn to use our way eventually" mindset is too prevalent, too....

So then they should do it your way? Then someone else will bitch about that, so should they do it his way, and then her way, and my way. This is unrealistic. Linux is about choices. If you don't like a specific distro, you move on to the next. If you don't like a specific app, remove it.

---

### Post by Mr. Picklesworth on 2010-03-30
> **23meg said:**
> It would help if you took a few minutes to read the threads you post your two pence to; in this case, if you actually read about application indicators replacing the notification area, you'd find out that there's no "erosion of options" or "making it hard to customize things" going on. Applications themselves decide what to do with their indicators, as defined by the spec, and you can disable their indicators just like you could disable their notification area icons. And you can remove the individual indicator applet components that you don't care about, even though the current way may not be optimal (applies to all users). This is a gradual transition and you shouldn't expect things to be perfect overnight.

I find it interesting that people complain like this is a regression when the functionality, to this end, is **precisely the same** as with the notification area.
Perhaps it's even a little more configurable, because the notification area didn't separate session stuff from other stuff and, before Lucid, many of those notification icons weren't themeable.

(Although it would be a nice addition if the permanent indicator-* packages just registered themselves as startup applications so individual users could remove them for themselves via the Startup Apps preferences without affecting everyone. I suppose there's a good reason, though, and something will happen eventually; the underlying technology is awesome enough that this isn't a dead end, but a magical land full of possibilities...).

As for the notification area being bigger, I should point out that it also looks considerably prettier. Consistent spacing between icons is a big thing :)

---

### Post by bcbc on 2010-03-31
I found it confusing... I left click on the chat client part and I get one menu, if I left click on the shutdown icon, I get another menu. So I figured they're two different things. Then I right click on the chat thing and check to remove, and bang my shutdown icon is gone. 
I had no idea how to undo what I'd done, so I ended up recursive unsetting my gnome changes etc... (maybe I'm a dumb user).

I agree the OP's choice of language is inflammatory (maybe out of frustration), but there's still a valid point hidden within there.

In fact, it's precisely these 'little things' that cause the most frustration in users.

---

### Post by sles on 2010-03-31
> **bcbc said:**
> I found it confusing... 
I agree. Moreovere, I can't understand why different things (I don't see any relations between them) are combined in one applet.

---

### Post by cyberkilla on 2010-03-31
Off-topic, slightly.

---

### Post by 23meg on 2010-03-31
> **bcbc said:**
> I found it confusing... I left click on the chat client part and I get one menu, if I left click on the shutdown icon, I get another menu. So I figured they're two different things. Then I right click on the chat thing and check to remove, and bang my shutdown icon is gone. 
I had no idea how to undo what I'd done, so I ended up recursive unsetting my gnome changes etc... (maybe I'm a dumb user).

I agree the OP's choice of language is inflammatory (maybe out of frustration), but there's still a valid point hidden within there.

In fact, it's precisely these 'little things' that cause the most frustration in users.

That's covered in [bug #519533]("https://bugs.launchpad.net/ubuntu/+source/indicator-applet/+bug/519553"), which Mr. Picklesworth has proposed a branch for.

---

### Post by sandys1 on 2010-03-31
@cyberkilla - do you have any opinions on desktop performance. I see that KDE is much slower than Gnome and takes up much more RAM as well.

---

### Post by 23meg on 2010-03-31
> **sles said:**
> I agree. Moreovere, I can't understand why different things (I don't see any relations between them) are combined in one applet.

Do you see any relation between the Rhythmbox icon, Network Manager, keyboard layout switcher, volume icon and Tomboy, all of which have been combined in one applet in the past (the old notification area), with non-standard interfaces and behavior?

Compare that to the indicator applet, where system indicators and application indicators are grouped separately, use standard menu behavior (no confusion created by right and left click, or icons "owning" application windows at their will), are future-proof (thanks to D-Bus and the standard libraries used; you can write a your own host applet if you don't like the current one), render identically under KDE and GNOME, do not randomly change location when you switch resolutions or rotate your display, and are more accessible (menus are screen reader compatible).

---

### Post by emarkay on 2010-03-31
> **swoll1980 said:**
> So then they should do it your way? Then someone else will bitch about that, so should they do it his way, and then her way, and my way. This is unrealistic. Linux is about choices. If you don't like a specific distro, you move on to the next. If you don't like a specific app, remove it.

My way?  No, the way of the users (remember TRON?)   

Let US decide how we see our data, and allow the OS to facilitate that; albeit maybe with a non-GUI config, but just don't eliminate that choice.

It's all about "screen real estate" as well as "personal choices"...

End of line.

---

### Post by bornagainpenguin on 2010-04-03
> **zekopeko said:**
> Those options didn't make it into Lucid but they are in the spec.

Maybe they need to be in Lucid too then?

> **zekopeko said:**
> 23meg showed you how to remove the messaging menu.

And I did.  You have to admit that this was an incredibly non-obvious way to customize the panels though.  And I feel bad for anyone who wants to customize their panels but isn't an administrator.  "Come to Ubuntu, where you have to be an administrator to change your desktop..."  Somehow I don't think this is the ease of use Cannonical was aiming for...

> **zekopeko said:**
> Evolution Mail doesn't run and take your precious RAM and CPU. It is in the menu for easy access to it. The same applies to Empathy. Application that are running have an arrow next to their entry in the Messaging menu.

I never saw any such arrows, not for lack of trying.  Empathy just kind of disappeared and I could never tell if it was running or not.  The same thing with Evolution, I never really knew if I had mail or not without having to manually check.  It also seemed to only display that I had mail if I left the application open in another desktop, hence my RAM chewing comments.

> **zekopeko said:**
> 23meg, again, explained the basic concept of going to the app specific preferences and toggling the option there. How did you survive with all those notification icons before is beyond me.

Is it dark up there?  It must be hard to see what with your head up your *** like that, right?  See!  I can be sarcastic too!

You missed the entire point of the icons in the system tray, which was to illustrate the folly of overpopulating the system tray, when no one knows what the user will be running and what additional applets will need the space.  That was really more about the foolishness of making it impossible to remove the username from displaying more than it was about notification icons.  It was about the space no longer ***available*** for the user icons.

> **zekopeko said:**
> Then perhaps another distro is for you? Ubuntu is catering to a specific segment of users. Perhaps you have out-grown Ubuntu?

Can you not read?  I said I'm all *for* Ubuntu having sane defaults, I just think it should be easier for users to change those defaults to what suits their needs without having to use administrator privileges to do so!  Or losing basic system functionality!  Go ahead and set the defaults as newbie friendly as you can, just so long as it can be customized just as easily after the install is done.

> **zekopeko said:**
> Now this is just pathetic. Temper tantrums of a petulant child.

No, it is just a statement of fact.  If Cannonical doesn't cater to those who *use* their software, then those users will find some other distro that does.  People left Windows because  they felt the system was becoming to difficult to use the way they wanted and they will leave Ubuntu (Linux) if it becomes too difficult to use the way the want to.  It isn't as if though there are no other options available.

There are multiple operating systems, dozens of desktop environments, there are hundreds of Linux distros.  Ubuntu got to where it is today because of their community, if Canonical chooses to annoy the members of that community enough, then they will leave and Ubuntu will become just another fad Linux distro.

--bornagainpenguin

PS: I confirmed in my earlier post that what 23meg said worked, but failed to thank him for his advice.  Thanks 23meg, I did appreciate it!

---

