---
title: "gnome system tray confusing and cumbersome"
date: 2010-04-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ffi on 2010-04-05
In the upstream gnome 2.30 system tray works very differently and better than in ubuntu, in ubuntu the behaviour is very confusing, right clicking does not bring up a menu and clicking an icon does not (un)minimize the app(eg. rhythmbox or transmission), instead you have to go through a menu!?

How can I use the upstream system tray?

---

### Post by 23meg on 2010-04-05
[QUOTE=ffi]How can I use the upstream system tray?[/QUOTE]

Remove "Indicator Applet" from your panel, and applications should fall back to using the notification area.

---

### Post by TrueTom on 2010-04-05
You also have to setup gnome-volume-control-applet to start automatically.

---

### Post by splicerr on 2010-04-05
Doesn't seem to work here with Rhythmbox,  it will not show in the notification-area. When I put the indicator-applet back to the panel, Rhythmbox will show there again.

---

### Post by castrojo on 2010-04-05
If it's not falling back then that's a bug, please file a bug against "indicator-applet"

---

### Post by Killigrew on 2010-04-06
Rhythmbox has an extra Plugin for the Tray Icon, perhaps it is just wrongly configured?
i thing standart setting is "not showing"

greetings

---

### Post by ffi on 2010-04-06
> **TrueTom said:**
> You also have to setup gnome-volume-control-applet to start automatically.
how do i do this? I can't find it anywhere

edit: neither rhythmbox nor transmission show in the tray after removing the indicator applet eventhough it is enabled

---

### Post by 23meg on 2010-04-06
> **ffi said:**
> how do i do this? I can't find it anywhere

Add gnome-volume-control-applet to your startup applications.

---

### Post by ffi on 2010-04-06
it's not there, it seems not to be installed and I do not see it in the package list either

---

### Post by ffi on 2010-04-06
okay I found out how to get the volume applet back and transmission and rhythmbox now show BUT still the icons still do not behave  correctly (they still behave like described above and not like they behave normally, right clicking does nothing, left clicking brings up a menu)

---

### Post by 23meg on 2010-04-06
> **ffi said:**
> BUT still the icons still do not behave  correctly (they still behave like described above and not like they behave normally, right clicking does nothing, left clicking brings up a menu)

That's the intended behavior. It's more "normal" than the inconsistent, unpredictable behavior of notification area icons.

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators)

---

### Post by ffi on 2010-04-06
Is there no way to fix it, this new behaviour is clumsy and counterintuitive

---

### Post by Luke has no name on 2010-04-06
I need both the indicator applet and the notification applet to have all the proper icons show up. I don't have the 'no left click' issue you're having, though.

---

### Post by luckylukeskywalker on 2010-04-06
> **ffi said:**
> Is there no way to fix it, this new behaviour is clumsy and counterintuitive

Apparently this behaviour is intented, and won't be fixed. For me this is the main point that's preventing me to upgrade from Karmic. I open Rhythmbox through that icon like once a minute, all day long.

Is there any way, hack, package, guide, tutorial, upstream something or whatever to change this behaviour?

---

### Post by ffi on 2010-04-06
Yes, something which used to be 2 clicks and no mouse movement (unmimize and minimize again) now takes: 4 clicks and 3 mouse movements! And it goes against all computer conventions which use left click to activate/select and right click for context interactions...

---

### Post by 23meg on 2010-04-06
> **ffi said:**
> Yes, something which used to be 2 clicks and no mouse movement (unmimize and minimize again) now takes: 4 clicks and 3 mouse movements! And it goes against all computer conventions which use left click to activate/select and right click for context interactions...

Do you not have a dedicated task switcher or dock? That's what should be used for minimize/unminimize/switch to by default, and it still takes the same amount of clicks. The notion of notification area icons "owning" entire application windows was a misplaced one to begin with, and was utilized arbitrarily by *some* applications, creating inconsistency with others.

If you were used to the old behavior of certain applications, you'll have to change some habits at worst. It really is easier done than said, and you get some nice side effects as well.

---

### Post by ffi on 2010-04-06
> **23meg said:**
> Do you not have a dedicated task switcher or dock? That's what should be used for minimize/unminimize/switch to by default, and it still takes the same amount of clicks. 

What are those, I am not talking about the taskbar, I don't want my torrent program or music player in the taskbar, I want it in the system tray.

> The notion of notification area icons "owning" entire application windows was a misplaced one to begin with, and was utilized arbitrarily by *some* applications, creating inconsistency with others.

If you were used to the old behavior of certain applications, you'll have to change some habits at worst. It really is easier done than said, and you get some nice side effects as well.

Well it should be left to the applications, so people can choose applications which behave the way they like


Anyway I really don't want to discuss I just want to fix the problem, how can I do that?

---

### Post by 23meg on 2010-04-06
[QUOTE=ffi]I don't want my torrent program or music player in the taskbar, I want it in the system tray.[/QUOTE]

Then either use the indicator (if you're using Transmission), or if you must have the old behavior, and the fallback doesn't work for some reason (upon removing the indicator applet; which would be a bug) run your torrent client with Alltray.

---

### Post by ffi on 2010-04-06
There is an in icon in the "Notification Area 2.30.0 Copyright © 2002 Red Hat, Inc." but the behavior is different from other distros, ie no right click. Is this a bug?

---

### Post by 23meg on 2010-04-06
> **ffi said:**
> There is an in icon in the "Notification Area 2.30.0 Copyright © 2002 Red Hat, Inc." but the behavior is different from other distros, ie no right click. Is this a bug?

No, it's most likely a "feature", that is, an inconsistency that's inherent to the notification area. The behavior has been entirely left to the application, and it has chosen to behave that particular way. If you find the behavior inconsistent, you should choose an entire other application (in your own words) :)

That's one thing the indicator applet fixes.

---

### Post by ffi on 2010-04-06
No because it works correctly in mandriva with the exact same versions of indicator applet and transmission

---

### Post by 23meg on 2010-04-06
Is that indicator applet, or notification area?

---

### Post by ffi on 2010-04-06
> **23meg said:**
> Is that indicator applet, or notification area?

sorry I meant notification area

---

### Post by 23meg on 2010-04-07
> **ffi said:**
> sorry I meant notification area

Could you post a screenshot of what you see when you left-click the Transmission icon?

---

### Post by Mr. Picklesworth on 2010-04-07
Obligatory rush-to-defense-of-cool-new-stuff follows ;)

The reason for that fallback not doing what you desire is because all indicator applet / notification icons in that application run through libindicate with the same set of data, so they behave pretty well the same. In most cases the behaviour diverges from upstream and is a patch specifically applied in Ubuntu's package.

With that in mind, there isn't much of a strategy to revert the behaviour. Part of me is a bit frustrated that you gave up on it seamingly quickly :(
I really recommend you stick back the indicator applet and give it a fair shot! May seem a tad crazy at first, but there is a lot of strong incentive for the behaviour it presently has. One practical thing people appreciate is that you can scrub through the indicator applets; click one, and just like a menu bar change to another without clicking again.

In general, this part of the desktop is being distanced from window management, thus the focus of the indicators is not on hiding / showing a giant window. This was a conscious decision to make the concept easier for new users to understand and interact with (since, really, I don't think many people besides power users understand the system tray in most OSs, and I don't think ANYONE can understand a conventional system tray without a lot of agonizing trial and error).

Now all indicators behave the same. Clicking an indicator is not a mysterious action with unforseeable consequences but something learnable and discoverable. There is only one menu for an indicator with all relevant information contained within; we don't have different left and right click menus.

---

### Post by QLee on 2010-04-07
[QUOTE=ff] And it goes against all computer conventions which use left click to activate/select and right click for context interactions...[/QUOTE]

I wonder how Apple computer users feel about the right click "convention" you mention. It sounds like you want to characterise methods you are familiar with as "the correct" method and it seems you're doing so without giving a fair try to the Ubuntu developers' choices. There is nothing wrong with having your own favourite way of working but, if you can't make changes to setup a system as you want it you should probably choose a distro that works as you desire and/or make your complaints part of a wish list on launchpad. Since the behaviour you don't like is by design and Lucid is getting close to release, I doubt many people have time to spare to help you make Lucid more like Mandriva.

---

### Post by ffi on 2010-04-07
> **Mr. Picklesworth said:**
> Obligatory rush-to-defense-of-cool-new-stuff follows ;)

The reason for that fallback not doing what you desire is because all indicator applet / notification icons in that application run through libindicate with the same set of data, so they behave pretty well the same. 

anyway to remove the patch, it there a ppa?

> With that in mind, there isn't much of a strategy to revert the behaviour. Part of me is a bit frustrated that you gave up on it seamingly quicky :([I really recommend you stick back the indicator applet and give it a fair shot! May seem a tad crazy at first, but there is a lot of strong incentive for the behaviour it presently has.

I tried it a few weeks and I really hate it, like I said what took me 2 clicks not takes me click (tray icon), mouse movement (to menu item), click (menu item), mouse movement (back to tray icon), click (tray icon to bring back up the menu again!), mouse movement (to menu item) click All this to just unminimise from tray and minimize again!

This is so awkward that I would seriously contemplate switching.

---

### Post by null_pointer_us on 2010-04-07
The notification/status stuff has been a mess for a while now. It's unfortunate the transition to a consistent, aesthetically pleasing interface has to be done over the course of several releases, but at least the work is being done. I can see the potential, and I'm confident the finished product will be worth it. Thank you!

---

### Post by luckylukeskywalker on 2010-04-08
Is there any insight in whether Network Manager and the clock applet will be adapted to this new way as well? At least then it's consistent on a default boot :)

---

### Post by oOarthurOo on 2010-04-09
Is this why I can't minimize rhythmbox to the tray anymore? It always stays in my list of running apps. This is true whether I use the system tray or the indicator applet.

---

### Post by oOarthurOo on 2010-04-09
Oh nevermind. Apparently for rythmbox to minmize to tray you have to hit close.

That's intuitive and consistent behaviour, isn't it?

Apps used to give you an option to control that behaviour, "close to tray" it was usually called, but I'm glad I no longer have any control over that. I'd hate to think it was causing the developers to lose sleep over its inconsistency.

I'm sure once I get used to being treated like a child I'll learn its much preferable to the old way.

Darn, mis-spelled some words but couldn't left click to correct them. Had to right-click first. This is going to be harder than I thought...

---

### Post by 23meg on 2010-04-09
> **oOarthurOo said:**
> Oh nevermind. Apparently for rythmbox to minmize to tray you have to hit close.

That's intuitive and consistent behaviour, isn't it?

Not unless you're willing to get rid of the mental construct of "minimizing things to tray", and embrace "applications indicating status and providing basic controls in a panel applet" instead.

> **oOarthurOo said:**
> Apps used to give you an option to control that behaviour, "close to tray" it was usually called, but I'm glad I no longer have any control over that. I'd hate to think it was causing the developers to lose sleep over its inconsistency.

I'm sure once I get used to being treated like a child I'll learn its much preferable to the old way.

Edit > Plugins > Status Icon > Configure > Status icon: Always visible.

---

### Post by oOarthurOo on 2010-04-09
> Not unless you're willing to get rid of the mental construct of "minimizing things to tray", and embrace "applications indicating status and providing basic controls in a panel applet" instead.

First of all, I don't even... what? That's what minimizing things to the tray provided. At a quick glance you could get info on the status, point at it for some more info, and click on it for basic controls. I really don't see what "mental constructs" have to do with it, or how your new "mental construct" is all that different from the old one.

None of which goes to my point: Hitting close doesn't close Rhythmbox, instead it minimizes it to the, err... it creates a panel applet indicating status and providing basic controls. That is unusual. Used to be the case that you had to specifically request an application to exhibit that behaviour.

Now it is going to be a bit of experimentation to find out which apps create panel mental contruct zones of awesomeness, and which just close. Which is sort of my whole point as it relates to previous claims of consistency. Nothing to do with intuitiveness and learning new things, it's all about the consistency, or in this case, the lack thereof.

---

### Post by 23meg on 2010-04-09
> **oOarthurOo said:**
> First of all, I don't even... what? That's what minimizing things to the tray provided. At a quick glance you could get info on the status, point at it for some more info, and click on it for basic controls. I really don't see what "mental constructs" have to do with it, or how your new "mental construct" is all that different from the old one.

You're focusing on a single example, Rhythmbox, whereas I was talking about the broader issue of notification icons "owning" application windows, and providing arbitrary controls, or no controls at all, with varying implementations most of which are problematic (look up XEmbed and related bugs), and non-standard clicking behavior, which are characteristics of the notification area.

[https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators](https://wiki.ubuntu.com/DesktopExperienceTeam/ApplicationIndicators) and [http://gould.cx/ted/blog/Having_a_tidy_systray](http://gould.cx/ted/blog/Having_a_tidy_systray) can also help you understand the rationale.

> **=oOarthurOo said:**
> None of which goes to my point: Hitting close doesn't close Rhythmbox, instead it minimizes it to the, err... it creates a panel applet indicating status and providing basic controls. That is unusual. Used to be the case that you had to specifically request an application to exhibit that behaviour.

If you find it unsuited, you can revert it easily the way I described in my last post.

> **oOarthurOo said:**
> Now it is going to be a bit of experimentation to find out which apps create panel mental contruct zones of awesomeness, and which just close. Which is sort of my whole point as it relates to previous claims of consistency. Nothing to do with intuitiveness and learning new things, it's all about the consistency, or in this case, the lack thereof.

My claim of consistency had to do with consistency among applications that use application indicators, but anyway, that's a general downside of the non-ideal world we live in, in which you can't just rub a magic lamp and summon indicator support patches for the dozens of applications that (ab)use the notification area, and get them upstream within seconds. It's naive to expect a transition of this scale to reach perfection overnight; however, note that almost all default applications are now covered. If you're willing to help with [the remaining work]("https://bugs.edge.launchpad.net/ubuntu/+bugs?field.tag=indicator-application"), it would be appreciated.

---

### Post by Mr. Picklesworth on 2010-04-09
> **oOarthurOo said:**
> Oh nevermind. Apparently for rythmbox to minmize to tray you have to hit close.

That's intuitive and consistent behaviour, isn't it?

Apps used to give you an option to control that behaviour, "close to tray" it was usually called, but I'm glad I no longer have any control over that. I'd hate to think it was causing the developers to lose sleep over its inconsistency.

I'm sure once I get used to being treated like a child I'll learn its much preferable to the old way.

Darn, mis-spelled some words but couldn't left click to correct them. Had to right-click first. This is going to be harder than I thought...

What you intend is done by going to the leftmost menu in the window (usually File, Music, Media, Picture or something like that) and choosing Quit, which is conventionally a secondary option affecting an application as a whole. The close button you are using is for closing windows; not applications.

In my eyes, this is quite consistent and hasn't changed with the indicator applet. (Granted, that particular factor hasn't really improved except for the new capacity for it to become better if others adopt the underlying standard). With your web browser, for example, closing a window (thankfully) does not kill the process; it closes the window. The process goes away when you aren't using it.

Unfortunately, an app like Rhythmbox can't just go away naturally when you aren't using it because, when it is first started, it begins babysitting an extension to the desktop which appears separate from the rest of what the user interacts with. If "not using the application" causes the disappearance that other, detached thing it happens to control (the Rhythmbox indicator), it's going to be confusing and frustrating.

Instead, either that Rhythmbox indicator — and all others like it — needs to be a permanent fixture (see indicator-messages), or one of the many things we already have referring to the application needs to be vastly improved.

No solutions at the moment; that is just something which needs considerable love and attention.

---

### Post by oOarthurOo on 2010-04-09
It's going to take a little while to sift through those two posts, because they were quite dense with information that I can't honestly claim to understand at one read through. Thanks for the info though; I look forward to understanding it all better.

---

### Post by HoboJ on 2010-04-09
> **23meg said:**
> Could you post a screenshot of what you see when you left-click the Transmission icon?

Here's a picture of the transmission rightclick menu. Granted this is with vanilla gnome 2.30. I've yet to run into a single application with a notification area icon that doesn't have a right click menu or the ability to left click hide show. So the removal if this from ubuntu is extremely baffling and seemingly arbitrary.

---

### Post by null_pointer_us on 2010-04-09
> **Mr. Picklesworth said:**
> What you intend is done by going to the leftmost menu in the window (usually File, Music, Media, Picture or something like that) and choosing Quit, which is conventionally a secondary option affecting an application as a whole. The close button you are using is for closing windows; not applications.

In my eyes, this is quite consistent and hasn't changed with the indicator applet. (Granted, that particular factor hasn't really improved except for the new capacity for it to become better if others adopt the underlying standard). With your web browser, for example, closing a window (thankfully) does not kill the process; it closes the window. The process goes away when you aren't using it.

I hate this behavior in any app on any platform. You actually have two different sets of semantics, between your browser window close and closing, say, a media player or messenging window.

Closing the browser window does just what I expect: even if some process stays in memory, all actions related to the closed window cease when I hit the close button.

Closing a media player, downloader, or other app with significant background activity does just the opposite: it keeps the operation in that window going. This annoys me to no end because I have to remember a different (and more complicated) behavior to do the same thing: File/<anything-else> -> Quit/Exit/Close/<anything-else> to stop whatever was happening in that window.

> Unfortunately, an app like Rhythmbox can't just go away naturally when you aren't using it because, when it is first started, it begins babysitting an extension to the desktop which appears separate from the rest of what the user interacts with. If "not using the application" causes the disappearance that other, detached thing it happens to control (the Rhythmbox indicator), it's going to be confusing and frustrating.

Windows 7 has two sections: (1) for "common" system-related applets that are either always there or conditional on some piece of hardware being present, and (2) for all other app-specific stuff with completely inconsistent (and sometimes usefully extended) behavior.

I'm just throwing this out there -- not advocating copying.


> Instead, either that Rhythmbox indicator — and all others like it — needs to be a permanent fixture (see indicator-messages), or one of the many things we already have referring to the application needs to be vastly improved.

No solutions at the moment; that is just something which needs considerable love and attention.

I don't see anyway to handle everything. Maybe an "app" area (color icons) to the left of the date/time applet plus a "system" area (monochromatic icons) to the right of the date/time applet. Sort of like it is now, except a few things like network manager should really be moved over to the "system" side of things.

/out-of-time

---

### Post by 23meg on 2010-04-09
> **Mr. Picklesworth said:**
> 
Instead, either that Rhythmbox indicator &#8212; and all others like it &#8212; needs to be a permanent fixture (see indicator-messages), or one of the many things we already have referring to the application needs to be vastly improved.

A somewhat out-there example: Docky's Rhythmbox helper comes close. Left click to launch, left click to show/hide, right click to access controls, all on the same icon. I wonder if I can make it display track information upon hovering..

---

### Post by Mr. Picklesworth on 2010-04-09
> **null_pointer_us said:**
> Closing a media player, downloader, or other app with significant background activity does just the opposite: it keeps the operation in that window going. This annoys me to no end because I have to remember a different (and more complicated) behavior to do the same thing: File/<anything-else> -> Quit/Exit/Close/<anything-else> to stop whatever was happening in that window.

I'm actually advocating quite the opposite. File›Quit is a horrible kludge from a time when we expected users to care about processes and files. No, I agree that you should never need to touch that menu option. (Heck, it shouldn't exist!).
I think the environment can be designed in a way where it is natural for processes to start and stop automatically in a sensible fashion. With that happening properly, windows become just that: transient views into resources that exist elsewhere. (And those resources should simply exist; they shouldn't cause any drain on the system unless they are actually being accessed).

---

### Post by null_pointer_us on 2010-04-09
> **Mr. Picklesworth said:**
> I'm actually advocating quite the opposite. File›Quit is a horrible kludge from a time when we expected users to care about processes and files. No, I agree that you should never need to touch that menu option. (Heck, it shouldn't exist!).
I think the environment can be designed in a way where it is natural for any processes to start and stop automatically in a sensible fashion. With that happening properly, windows become just that: transient views into resources that are not directly influencing them.

Cool, thanks for clarifying this. (I had to run before editing my response and was worried that it came off as being too angry and/or personal.)

Just to throw out another "out there" view (not for lucid), I have always wondered why no OS has a sort of task viewer, a single place to which applications can visually queue any task using major resources (e.g. burning a dvd, large file transfer, installing packages, etc.).

This is fundamentally different from a process/thread viewer, a dock, or an indicator applet. By "task" I mean an abstract, user-understandable concept that could be anything from a simple file download to a multiprocess file encoding job.

Currently, any desktop environment has its own slew of apps with special progress windows that can get lost on a different workspace or buried under larger windows, when in reality those are temporary, system-wide tasks that the user should always be able to see at a glance, in a predictable location.

But I wouldn't want to distract from more immediately useful things like finishing the indicator applet.

---

### Post by oOarthurOo on 2010-04-10
Well, since this thread has the attention of those who seems fairly knowledgeable about this sort of thing, perhaps someone can explain the "mail" icon to me. Left clicking on it shows evolution, but closing (hitting the 'x' in the top left of the window) actually shuts it down. Doesn't minimize it or keep it running in the background. 

I understand how RB and Transmission work in the indicator applet, and it seems like the chat thing operates like you'd expect, closing stuff down keeps it going there in the panel. You have to actually say "chat > quit" in the menu to shut it down. 

So what's the deal with evolution behaving differently? Is this a bug, or am not understanding the revolution yet?

---

### Post by sixthwheel on 2010-04-10
> perhaps someone can explain the "mail" icon to me. 

You have a mail icon on the system tray?
I just have a little goldfish. I can right click on it, but left clicking gives me this dialog. "Unable to locate the command to execute"

Could someone tell me if this is normal, and my little fish is ok?

---

### Post by linusr on 2010-04-10
> **oOarthurOo said:**
> 
So what's the deal with evolution behaving differently? Is this a bug, or am not understanding the revolution yet?

should be an bug!! application using indicator applet shouldn't quit when closing application!?

---

### Post by castrojo on 2010-04-10
Hi, I've been helping drive the app indicator work and thought I'd answer some questions.

> **oOarthurOo said:**
> Now it is going to be a bit of experimentation to find out which apps create panel mental contruct zones of awesomeness, and which just close. Which is sort of my whole point as it relates to previous claims of consistency. Nothing to do with intuitiveness and learning new things, it's all about the consistency, or in this case, the lack thereof.

Yeah there's still a long tail of apps that we all need to look at. There's probably a ton of apps out there that probably don't need to even have an icon on the panel.

> **HoboJ said:**
> Granted this is with vanilla gnome 2.30. I've yet to run into a single application with a notification area icon that doesn't have a right click menu or the ability to left click hide show. So the removal if this from ubuntu is extremely baffling and seemingly arbitrary.

It's not arbitrary. The KDE folks came up with with something called KStatusNotifierIcon and we thought it was a good idea. Basically app indicators are a port of this to GNOME. It's been proposed to both XDG and on the GNOME devel list. We've taken the apps on the CD and ported them to use app indicators. We've asked people to kick the tires on libappindicator and it's come up with some nice things, and some things that I didn't expect. 

In the current area it's you can have right click menus with stuff in them; left click menus with stuff in them. The idea is to have one way to do menus; left click. As a bonus we get the same consistent experience, you don't have to remember if invoking the app prefs should be a right or left click, it's always the same! 

As a bonus we get some nice features. My personal favorite has been that the app indicator menu can be scrubbed. Hit the keyboard shortcut (Super-M), and then hit the right and left arrows. I'm a heavy keyboard user and the inability to easily get up there in the past has always frustrated me. 

There's some cross-desktop wins here too: KDE4 apps (except the ones not finished) support KStatusNotifierItem, so when you run a KDE app on GNOME it not only behaves the same way but even THE MENUS are rendered properly so they don't look like crap. This is important for third party application developers that might not be familiar with how to make their app look right on linux. At the very least it will look more native and be in the proper place.

> **null_pointer_us said:**
> I hate this behavior in any app on any platform. You actually have two different sets of semantics, between your browser window close and closing, say, a media player or messenging window.

Yes, this drives bonkers, I'm glad I'm not the only one!

> **null_pointer_us said:**
> Windows 7 has two sections: (1) for "common" system-related applets that are either always there or conditional on some piece of hardware being present, and (2) for all other app-specific stuff with completely inconsistent (and sometimes usefully extended) behavior.

Heh, people keep saying this but keep missing that under the "Proposed Changes" on the wiki page there is a picture that shows a box for system indicators and a box for application indicators. That being said I think Win7's solution to solve this problem is terrible, they just shove all the icons in a drawer and called it a day.

> **oOarthurOo said:**
> Well, since this thread has the attention of those who seems fairly knowledgeable about this sort of thing, perhaps someone can explain the "mail" icon to me.

This bugs me too, it's a messaging indicator, which means that any app that want's to leave you a message can do so. So like, when I wake up in the morning and people have tried to IM I have them queued up right there, or if someone direct replies to me on Twitter it's right there. For some reason we use a mail icon here so people think it's just for mail. It's doubly frustrating for people who say "oh I don't use Evolution so I can remove this" and then remove the applet which takes all the other indicators with it! Doh! And yeah, it not working when evolution isn't running is annoying.

These bugs are filed and at UDS we'll once again continue to look at ways to improve this interaction for Maverick. Like everything else in OSS, we try to do the best we can in a given amount of time but when doing this kind of work that affects many applications you can't really get them all, so we hit as many core apps as we could to show that it can work and have worked hard on making it easy for application developers to use the new framework; including a fallback mechanism so that for people that don't run app indicators won't have broken trays. 

Sorry this post is long and convoluted, I can continue to answer any questions you might have!

---

### Post by castrojo on 2010-04-10
Oh I forgot to mention the thing I wanted to make clear in that post but got distracted; yeah there some little annoying bugs with the interaction that we need to work but overall it's cleaner and more accessible. By no means are we finished in this area and will continue to work on it during the next few cycles.

---

### Post by bgruber on 2010-04-10
so, i think i understand the motivations being behind the indicator applet. i find it to be horrible.

I too, have always hated "minimize to tray" semantics; if it's running, and it's minimized, it should be in my task list. Other people disagree, and this has caused problems. Some people tried to establish a notification area for, well, notifications. Other people said "oh great, a tray to minimize stuff to." Since there are enough people who like the idea of minimizing long-running apps to a tray, lots of things started getting minimized to the notification area. Then, since writing notification area apps was so easy people started writing things that used to be panel applets (network status, volume control) as notification area icons. Now there are 3 kinds of things in that area, and it's confusing, at least partially because these different things all respond to clicking in different ways. (let me know if i've gotten any of this story wrong in any major way)

From your post above, it sounds like this is the very problem the indicator area was designed to solve. Unfortunately, I would never have guessed that from actually using the indicator applet.

Why? Well, the very first thing that was placed in the indicator applet was message notifications for IM and mail. The second thing to go in the indicator applet? The volume control.

So what goes in this new area? Panel applets? Long running programs? Message notifications? It's like now I have a whole new super confusing place filled with crap.

Of course, we already had three different places for the three different things. Applications in a task list, notifications in the notification area, and applets as applets. You might make the case for a new special area for "long running" applications, but clearly the indicator applet isn't it.

---

### Post by oOarthurOo on 2010-04-10
> **whiprush said:**
> Oh I forgot to mention the thing I wanted to make clear in that post but got distracted; yeah there some little annoying bugs with the interaction that we need to work but overall it's cleaner and more accessible. By no means are we finished in this area and will continue to work on it during the next few cycles.

Appreciate the input Whiprush, and I like that there is a vision that is being worked towards. No one expects these things to be done in a day.

That being said, for me and perhaps others, evolution integration with the indicator applet seems a little more 'core' than twittering.

I don't twitter, or facebook and don't trust the 'cloud' to keep my data secure, so until Ubuntu One has the ability to setup a home server UO thing is first thing I remove. Maybe I'm a corner case, I'm sure you'd have a better idea of that than me. The end result, however, is that the only use I have for the mail icon within the indicator applet is to check evolution; Sadly not there yet. Volume I control with keyboard, so again, don't need the indicator. And I sure miss being able to point at transmission and see the status, speed, etc.

I know I just need to find a way to have transmission and rhythmbox use the old system tray, at least until the day when we have the option to control what apps are allowed to appear in the indicator applet, which I'm quite sure will eventually happen, and when it does, I'll try to be the first to congratulate all the OSSome people who made it happen.

Anyway.. I see the vision, from your post and others' previous posts, and I think it's a good vision. But in its current state this is beginning to look like another pulse audio fiasco. Sure, two or three releases later no one can imagine living without it, and that's probably what's going to happen with the indicator applet, but I sure do wish there was an easy way to get back to the old way until things settle down.

If there is, and I haven't really looked for it yet because I've been giving the new way the old college try, maybe a wiki post on reverting should make it into the release notes. 

Best,
A

---

