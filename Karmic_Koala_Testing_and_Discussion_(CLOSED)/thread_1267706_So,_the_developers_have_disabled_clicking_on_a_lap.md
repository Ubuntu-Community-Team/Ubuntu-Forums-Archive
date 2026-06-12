---
title: "So, the developers have disabled clicking on a laptop's touchpad by default..."
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by talkingwires on 2009-09-16
In every previous version of Ubuntu, you could tap your laptop's touchpad and "click". A double tap was a "double click". You can also do this in Windows and Mac OS X.

The Ubuntu developers, in their infinite wisdom, have decided that this is not a good thing, and have disabled it by default. The discussion first started on [a bug report that is now closed]("https://bugs.launchpad.net/bugs/404219"). The developers felt that if anybody felt strongly about about it, they should bring it up in the mailing lists.

So, does anybody feel strongly enough about it to navigate the murky and uncharted depths of the developers' mailing list?

---

### Post by TDK800 on 2009-09-16
It was pain upgrading from 9.04 to 9.10 and then having to research how to get to the mouse control panel in startup menu without being able to click (laptops on move do not have mouse attached)... who came up with this ingenious idea of usability hell, microsoft agents?

---

### Post by phenest on 2009-09-16
What about those that prefer it disabled? It's not difficult to enable/disable it using the option provided. And you're not going to please everyone by getting the default changed, so leave it be.

---

### Post by talkingwires on 2009-09-16
What about people with newer Mac laptops that don't even have physical buttons?

---

### Post by psyke83 on 2009-09-16
Damn. I thought that tap-to-click wasn't working because of infrastructure changes; I had put "synclient TapButton1=1" as a startup item to compensate.

Replying to mac_v's penultimate post on the bug report, tap-to-click is actually enabled by default on Windows, even with the generic Microsoft mouse driver that is used by default. It is a fundamental feature of touchpads. The only times in which I would want to see it disabled is on older generation touchpads where keyboard interrupts cause the cursor to move wildly (thus losing focus as you type). I saw this on an old Dell Inspiron 8000 laptop, for example. Newer touchpads don't have this kind of problem, though.

It seems that I'll have a lot of "registy tweaks" to perform when Karmic hits final (such as this, and re-enabling icons for buttons and menus).

---

### Post by ffi on 2009-09-16
> **phenest said:**
> What about those that prefer it disabled? It's not difficult to enable/disable it using the option provided. And you're not going to please everyone by getting the default changed, so leave it be.

It might be easy in gnome but in kde4 there is still no way to configure the touchpad: tap to click and side scrolling should be enabled by default else people might think that it just doesn't work for their touchpad under linux

---

### Post by cyberkilla on 2009-09-16
Everybody expects this functionality. If they come from an OS X or Windows laptop, they will not understand why they can't click with the touch pad.

People who dislike the tap-to-click feature will already expect to disable it themselves, as they had to in other operating systems.

---

### Post by hanzomon4 on 2009-09-16
Actually I hate the tap to click, I prefer to use my actual button(even in the new macs a button is there) Two finger+ Click is what I use in osx to right click. It less frustrating then tapping due to less unintentional clicks.

---

### Post by slakkie on 2009-09-16
> **phenest said:**
> What about those that prefer it disabled? It's not difficult to enable/disable it using the option provided. And you're not going to please everyone by getting the default changed, so leave it be.

The same could be said for changing the default like they did. 

I find it very ignorant, since to my knowledge you were ALWAYS able to tap on your touchpad and have the clicking ability. It is a default everywhere.. 

I use it frequently because tapping does not bother my sleeping girlfriend (it makes less sound). I probably don't experience any difference, since I use KDE, but if I would use Gnome I would definitely comment on the change of the default value. It makes no sense.

---

### Post by 23meg on 2009-09-16
> **talkingwires said:**
> What about people with newer Mac laptops that don't even have physical buttons?

[It's (supposed to be) enabled for those]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/404219/comments/23").

---

### Post by krazyd on 2009-09-16
I hope this is reverted. This is basic functionality for me!

---

### Post by 23meg on 2009-09-16
> **cyberkilla said:**
> Everybody expects this functionality.

How do you know? Did you ask or test with "everybody"?

[QUOTE=cyberkilla]If they come from an OS X or Windows laptop, they will not understand why they can't click with the touch pad.[/QUOTE]

Is it enabled by default on those systems? If it depends on vendor configuration on the Windows platform and there are no guidelines on whether it should be on by default, that's going to be hard to figure out. Can someone come up with a rough survey of the situation in other platforms (including different supported versions, their approximate percentage of use etc.)?

---

### Post by mister_pink on 2009-09-16
> **23meg said:**
> How do you know? Did you ask or test with "everybody"?



Is it enabled by default on those systems? If it depends on vendor configuration on the Windows platform and there are no guidelines on whether it should be on by default, that's going to be hard to figure out. Can someone come up with a rough survey of the situation in other platforms (including different supported versions, their approximate percentage of use etc.)?

If this wasn't already known then it should never have been changed. Why should someone have to do research to show that it should be changed back? It should have been done before they changed it in the first place!

This really is an odd default to choose, I can't really understand it at all.

---

### Post by aethralis on 2009-09-16
I usually try to see sense in the changes in the defaults that are made, but this time I really wonder. I never use the buttons, only tapping. I certainly can't vote for "everybody" but introducing such a big usability inconsistency between different OSes is definitely a bad thing. I would hope that they describe the decision it in the introduction, plus some really easy way to enable it. Lots of people I know use only touchpad with laptops (not a mouse) and as far I have noticed never use the buttons either.

---

### Post by cyberkilla on 2009-09-16
> **23meg said:**
> How do you know? Did you ask or test with "everybody"?
Yes, everybody in the whole world - just like the person who changed it in the first place.

---

### Post by psyke83 on 2009-09-16
> **23meg said:**
> How do you know? Did you ask or test with "everybody"?

I understand the point you are trying to convey, but it's a weak point nonetheless. Have the Xorg or Ubuntu developers asked "everybody"? Of course they haven't, and it probably wouldn't matter anyway. 

> Is it enabled by default on those systems? If it depends on vendor configuration on the Windows platform and there are no guidelines on whether it should be on by default, that's going to be hard to figure out. Can someone come up with a rough survey of the situation in other platforms (including different supported versions, their approximate percentage of use etc.)?

At least on Windows, emphatically yes.

All Synaptics touchpads use tap-to-click by default on retail Windows installations (XP, Vista, 7RC and I assume 7 final). This applies both to the third-party drivers (downloaded from Synaptics' site), and Microsoft's generic "PS/2 compatible mouse" driver that is used by default.

It's possible that certain OEM configurations of Windows may ship with tapping disabled (along with other OEM junk and trialware), but that would account for a definite minority. All laptops I have bought in the last 5 years came with tapping enabled on the default Windows installation.

I can't speak for Mac, because I'm poor ;).

---

### Post by vinegaroon on 2009-09-16
This seems like a very silly decision... Everyone I know with a laptop uses tap to click.
People who don't like it can still disable it, I find it hard to believe that they are in the majority.

---

### Post by MacUntu on 2009-09-16
Look, it's the "too confusing" train!

---

### Post by pranavdagrawal on 2009-09-16
> **aethralis said:**
> "I certainly can't vote for "everybody" but introducing such a big usability inconsistency between different OSes is definitely a bad thing. I would hope that they describe the decision it in the introduction, plus some really easy way to enable it. Lots of people I know use only touchpad with laptops (not a mouse) and as far I have noticed never use the buttons either."

Definitly, I and some of my friends just made a shift from ubuntu. We had assumed that the cliclking does not work in here and this certainly would be the case for most new comers, who might then decide to go back.
It is these small issues that hold linux back from becoming The OS. Brightness issue is yet another example.

I agree there are people who use the pad buttons, but 
1. I am sure more people are moving for tapping the touch pad...
2. They are used to having to change the settings, while those who dont use the pad, would find it surprising...

I would definitly vote for the return of the pad.

PS: Can't we have a poll in the community for such decisions? It may not act as the last word but it would certainly be a good guideline.

---

### Post by cyberkilla on 2009-09-16
> **MacUntu said:**
> Look, it's the "too confusing" train!

Very constructive; much like this response.

---

### Post by 3rdalbum on 2009-09-16
Tap-to-click is horrible on netbook touchpads, because they are so sensitive.

For those of you saying "I never use the buttons"... how do you right-click then?

---

### Post by issih on 2009-09-16
Personally I can't stand tap to click...its just annoys the hell out of me. That said, as long as it is simple to turn on and off I don't really care whether it is on by default. We should probably follow the de facto standard, which, I concur, is to ship with it enabled.

---

### Post by 23meg on 2009-09-16
> **cyberkilla said:**
> Yes, everybody in the whole world - just like the person who changed it in the first place.

> **psyke83 said:**
> I understand the point you are trying to convey, but it's a weak point nonetheless. Have the Xorg or Ubuntu developers asked "everybody"? Of course they haven't, and it probably wouldn't matter anyway. 

They also probably didn't claim it suits "everybody" very well, as opposed to the poster I quoted, who did - "This is a better default" doesn't mean "This is what everybody wants/expects". I intended to comment on the wording.

> **psyke83 said:**
> At least on Windows, emphatically yes.

All Synaptics touchpads use tap-to-click by default on retail Windows installations (XP, Vista, 7RC and I assume 7 final). This applies both to the third-party drivers (downloaded from Synaptics' site), and Microsoft's generic "PS/2 compatible mouse" driver that is used by default.

It's possible that certain OEM configurations of Windows may ship with tapping disabled (along with other OEM junk and trialware), but that would account for a definite minority. All laptops I have bought in the last 5 years came with tapping enabled on the default Windows installation.

I can't speak for Mac, because I'm poor ;).

Thanks, if we can support that with more examples and some independent (such as vendor-provided) data, it's going to be supportive of changing the default.

---

### Post by cyberkilla on 2009-09-16
[Deleted by user]

---

### Post by gradinaruvasile on 2009-09-16
> **3rdalbum said:**
> Tap-to-click is horrible on netbook touchpads, because they are so sensitive.

For those of you saying "I never use the buttons"... how do you right-click then?

At least on  Dell C640 and D630 if u tap on the lower right corner its a right click. Ubuntu 8.10 and 9.04.

So... this way u right click.

I too find puzzling this decision to disable tapping by default. I definitely use it. Its just a natural movement i guess.

---

### Post by psyke83 on 2009-09-16
> **23meg said:**
> They also probably didn't claim it suits "everybody" very well, as opposed to the poster I quoted, who did - "This is a better default" doesn't mean "This is what everybody wants/expects". I intended to comment on the wording.

Ok. For the record, I don't believe that everybody wants to use tap-to-click (for example, some touchpads are too sensitive and interpret wrist movements during typing as clicks). However, I would hazard a guess that a healthy majority would prefer tapping enabled by default. How to demonstrate my opinion as fact is another task ;).

> Thanks, if we can support that with more examples and some independent (such as vendor-provided) data, it's going to be supportive of changing the default.

Which vendor? The computer OEM or the touchpad manufacturer (Synaptics/Alps)? In the latter case, see the driver brief: [http://www.synaptics.com/sites/default/files/driverpb.pdf](http://www.synaptics.com/sites/default/files/driverpb.pdf)

You can also [download]("http://drivers.synaptics.com/Synaptics_Driver_v10_1_8_XP32.exe") the driver, extract its contents and examine the synpd.inf file. You will be able to see that "Enable Tapping" is enabled by default.

---

### Post by Linux&amp;Gsus on 2009-09-16
I personally can't stand the touchpad at all, with or with out clicking. But that's just me. Besides my touchpad is just so freaking sensitive that I often click when typing.
So, I personally don't mind it disabled by default. Non the less I think there should be an easy and obvious option to turn it on/off for those who prefer what ever option.

Having said that. The laptop I had before my current one (never re-installed Windows on this one so don't know about it) came with touchpad click enabled by default. There was an option to turn it off the touchpad all together (not only the clicking, all or nothing) but it didn't remember that setting. So, every freaking day I had to turn that thing off. Not exactly a happy thing.
Anyways, after I had to re-install Windows I discovered that the touchpad to work properly actually needed a driver. It only sort-of worked while plainly plugging in whatever mouse worked perfectly fine. My first thought was that something was broken. I would not have cared really but the option to turn off the touchpad was only working with that driver installed.

So, while people are most likely used to the fact that clicking on the touchpad works by default chances are that you run into this kind of trouble when you re-install Windows.
From that point of view you could argue that installing Linux is no different to installing Windows, you just don't know if everything works the same like when it came factory installed. On the other hand, this is what most people are used to.

IMHO the best thing really would be to have an obvious and easy way to change (permanently) the setting to what you prefer. No matter the defaults.

---

### Post by Paqman on 2009-09-16
Madness. Every touchpad i've used for years has had tap-to-click. It's a great feature, and should be the default, or at least easily enabled (ie: not by diving into gconf).

I'd like to see a more open framework for making big usability decisions like this. If this default was changed on the basis of usability testing, i'd like to see the actual results of that testing.

---

### Post by psyke83 on 2009-09-16
> **3rdalbum said:**
> Tap-to-click is horrible on **some** netbook touchpads, because they are so sensitive.

There, fixed that for you.

I have three aging laptops around - a Dell Inspiron 8000 (circa 2001), Dell Inspiron 510m (2004) and a HP/Compaq NX9010 (2003).

The Inspiron 8000's touchpad is quite erratic, and the cursor tends to jump erratically while typing.

The NX9010* and Inspiron 510m touchpads are a joy to use, on the other hand, and there are no jumping cursors or tapping false-positives whist typing.

Aside from personal preference and habit, I think that the design of your laptop/netbook and the type of touchpad - as well as its placement - matters.

> For those of you saying "I never use the buttons"... how do you right-click then?

It's possible to scroll and right-click on a touchpad (it varies depending on the driver). Personally, I never use scrolling on a real mouse or touchpad, and use the physical right mouse button on touchpads. Tapping to left-click feels much more fluid and intuitive for me.

*The NX9010 touchpad feels too sensitive for my taste by default, but changing the sensitivity in the options completely fixes that problem.

---

### Post by MacUntu on 2009-09-16
> **cyberkilla said:**
> Very constructive; much like this response.

Well, that's the "explanation" in the bug report. _**I don't know how the ppl behind this make their decisions**_ (maybe flip a coin), so how should I give constructive criticism?

There is only one way to get an idea of what the majority wants: ask the users. Add a data collecting app that users can run once they've set up their systems. Devs will argue that since that could only be done opt-in, results would be skewed... and then jump the "too confusing" train again. :P

> **23meg said:**
> Thanks, if we can support that with more examples and some independent (such as vendor-provided) data, it's going to be supportive of changing the default.

That's what I expect to happen before changing such a noticeable default.

---

### Post by gnomeuser on 2009-09-16
When upstream changed this some time ago I complained mostly since it was a regression (and when the default changed without notice I honestly thought it was broken). Now however it is easy to change back since we have a gui for it which is integrated with the mouse configuration application.

I think the vital thing given that is to get hard data on what the default should be.

Users are different, my mother would never be able to figure out how to reverse the option if it was illsuited to her needs and expectations. I could though be expected to customize for my needs and have the ability to do so.

We need to determine what the segments of users are who expect this, who expect this but disabled during typing and who expect it to be off. 

When we know that we can make a decision, it does not appear that upstream had hard data outside what is claimed to be a 50/50 split between lovers and haters of the tab click. 

My personal experience tells me that the users who have a hard time configuring their desktop are the ones who enjoy tap click but disabled during typing. More hardcore users may be annoyed by it but these are capable of turning it off whereas the previous group should be expected to do this. 

It is about who we make the desktop for and their skill level but also about making the default experience as nice as possible for as many people as possible.

I would like to see this enabled by default with the disable while typing option enabled as well. My experience shows me that this is the sanest default but I have little in terms of hard data.

Another approach might be to have a little tweaker wizard monitor your desktop use after your first 2 weeks of use, if a lot of spurious clicking has taken place we might offer the user to reduce click speed or disable it. This would be a useful technic in exposing the configurability of the desktop and using metrics based on the users actions to make recommendations. Other places it might be useful could be uninstalling applications that haven't been used in say 3-6 months. There would be problems of different natures involved with basically monitoring the user though, while it might be a good idea to allow this kind of thing as an opt in locally.. resisting the temptation to mine for data by collecting it while useful and done with good intention it opens up some privacy issues we will need to face with honesty.

---

### Post by psyke83 on 2009-09-16
> **MacUntu said:**
> That's what I expect to happen before changing such a noticeable default.

Correct me if I'm wrong, but I believe that 23meg was referring to the Canonical/Ubuntu folks changing the default setting of tapping from disabled back to enabled; remember, it was the Xorg (or was it GNOME?) developers who recently set tapping to disabled by default.

---

### Post by MacUntu on 2009-09-16
> **psyke83 said:**
> Correct me if I'm wrong, but I believe that 23meg was referring to the Canonical/Ubuntu folks changing the default setting of tapping from disabled back to enabled; remember, it was the Xorg (or was it GNOME?) developers who recently set tapping to disabled by default.

Sure, my answer was more directed to those who changed it in the first place. They had to have reasons for it but all I've read so far is "too confusing" - a reason that shouldn't be enough for Canonical to adopt such drastic upstream changes.

---

### Post by meborc on 2009-09-16
if tap-click is disabled, a lot of people new to ubuntu will believe it to be a bug or a broken system

the best way to handle this is in the installer... if installer identifies a netbook, it can prompt the user to disable tap-click by default

---

### Post by talkingwires on 2009-09-16
> **23meg said:**
> Is it enabled by default on those systems? If it depends on vendor configuration on the Windows platform and there are no guidelines on whether it should be on by default, that's going to be hard to figure out. Can someone come up with a rough survey of the situation in other platforms (including different supported versions, their approximate percentage of use etc.)?Here's a survey for you: Go down to whatever passes as your local computer store and go to the laptop section. Observe how every single one of them has "tap to click enabled".

I (unknowingly) tried it out at my local Best Buy last month when I was thinking of buying a laptop and fiddled with most of their systems. Not once did I run into one where I had to use the physical buttons. If I had, I probably would've assumed it was broken, made mental note never to buy that brand, and moved on.

---

### Post by Seventh Reign on 2009-09-16
Try using an Acer Aspire One with the buttons on the SIDE of the touchpad without the click feature.  Its a pain in the @$$.

The Karmic Netbook Remix has a tool in the system menu that will allow you to instantly turn on/off clicking with the touchpad.  I just added it to my favorites, because it seems that EVERY time you plug a USB mouse/keyboard into the laptop it disables the touchpad.

As for how to right click?  I'm not sure which is which but I know that some laptops/distros have 2 finger and 3 finger touch.  One is for middle click and one is for right click.  I tried it with my Aspire One, but it didnt work for me.

---

### Post by jlacroix on 2009-09-16
No offense, but this probably one of the lamest things I have heard of in Ubuntu since the removal of the screen resolution utility in a previous release.

Even worse, there is a bug that causes a blinking black cursor on the top left corner of my screen and prevents X from starting, and this bug has been going on at least two months now with no resolution in sight. The fact that attention has been given to such a trivial thing as tap to click instead of major issues like the one I have makes me really question the priorities here...

Edit: And what about us Kubuntu people with no way of enabling or disabling this option? What will we do?

---

### Post by blur xc on 2009-09-16
> **phenest said:**
> What about those that prefer it disabled? It's not difficult to enable/disable it using the option provided. And you're not going to please everyone by getting the default changed, so leave it be.

+2

I LOATHE tap to click.  And thankfully, my laptop has three buttons, and very nice vertical and horizontal sliders on the touch pad.  I feel sorry for everyone that doesn't have this nice of a touch pad.

BM

---

### Post by tghe-retford on 2009-09-16
Well done - I had a huge roll of bubble wrap that I was going to save, until I read this and have since started to pop the bubbles.

I can't wait until next month and the inevitable call once my Girlfriend upgrades to Karmic that "I can't click anything - it's broke". I personally prefer clicking on a touchpad, feels more comfortable to the touch than using the buttons.

I just hope that like with the disappearing Gnome icons and non-customisation of notify-osd that this isn't going to turn into another situation where "we know better than you and its either our way or the highway".

---

### Post by SveinT on 2009-09-16
What on earth? This is really a silly decision, seeing as it's a expected behaviour on new computers. One thing is an experienced user who can change it back, but what about the new users who expect this behavior and wouldn't know or care where to look?

And where is the reason behind the decision? What arguments backs it up? I really hope this is not two-three developers who have crappy hardware and so they think finger tapping must suck on everyone else's. I have actually never clicked when I didn't mean to...

---

### Post by Zorael on 2009-09-16
I tap to click. It's convenient.

I also use two fingers to middle-click, but my pad is too small to conveniently fit three (for the right-click) so I resign to using the key for that.


edit: As an anecdote, my Advent 4211 netbook came with a Sentelic "Finger-sensing pad", which doesn't have drag-to-scroll functionality at all, as Synaptics has the patent for that. I ended up buying a spare Synaptics pad from a competitor (ASUS), breaking open the netbook and replacing the stupid Sentelic one to get the functionality I'm used to. I was /so/ disgusted with the machine until I figured out what the problem was (and how to fix it).

So, please don't scratch that feature off as "something too confusing for the user", too. Both that and tap-to-click are cornerstone features in my book.

---

### Post by jlacroix on 2009-09-16
I think by the majority of the posts here we can safely say that this is a STUPID idea and should be reversed. The ratio of people for this decision and those against are too great. For anybody that hates tap to click, they can turn it off, just as they have for the past five or so years.

---

### Post by 23meg on 2009-09-16
> **psyke83]Which vendor? The computer OEM or the touchpad manufacturer (Synaptics/Alps)? [/QUOTE]

I was actually thinking in the lines of guidelines provided by Microsoft to manufacturers, if any.

[QUOTE=talkingwires said:**
> Here's a survey for you: Go down to whatever passes as your local computer store

*My local computer store* passes as my local computer store.

> **talkingwires] and go to the laptop section. Observe how every single one of them has "tap to click enabled".[/QUOTE]

That's a good idea for gathering a good amount of anecdotal data - I pledge to do that if five more people are also willing to.

[QUOTE=MacUntu]That's what I expect to happen before changing such a noticeable default.[/QUOTE]

Remember that this is the development branch, where tweaking defaults just as an experiment is fair game said:**
> I just hope that like with the disappearing Gnome icons and non-customisation of notify-osd that this isn't going to turn into another situation where "we know better than you and its either our way or the highway".

"System > Preferences > Mouse > Touchpad > Enable mouse clicks with touchpad", and (emphasis mine):

[QUOTE=Sebastien Bacher]When not having a button the tap on click should be actived automatically, **for users having a button that can be discussed** but better to use mailing than a bug report about that.[/QUOTE]

---

### Post by jlacroix on 2009-09-16
> **23meg said:**
> System > Preferences > Mouse > Touchpad > Enable mouse clicks with touchpad", and (emphasis mine):

I'll ask again, how do you do that under Kubuntu?

---

### Post by 23meg on 2009-09-16
> **jlacroix said:**
> I'll ask again, how do you do that under Kubuntu?

I don't know, since I don't test Kubuntu. Is tap to click also disabled by default in Kubuntu?

---

### Post by infamousrev on 2009-09-16
The first thing I do on a new installation is disable tab to click.

I like this new update, good work!

---

### Post by Keyper7 on 2009-09-16
> **jlacroix said:**
> I think by the majority of the posts here we can safely say that this is a STUPID idea and should be reversed. The ratio of people for this decision and those against are too great. For anybody that hates tap to click, they can turn it off, just as they have for the past five or so years.

Honestly, I don't see what the fuss is all about. I use tap to click and I like it. When I booted Karmic and saw it wasn't working, I simply followed a sequence of logical thoughts:

1) "Hmm... no tap to click. I *prefer* having tap to click... Maybe I should check the... *Preferences*?"

2) "Okay, now let's see... The touchpad is a kind of... what was it called again? Oh, yeah, a *mouse*. Hey, there's an item called *Mouse* in the *Preferences* menu! Maybe if I click that, some sort of... uhh... window or something will appear, allowing me to change the *preferences of the mouse*. Yeah, kinda makes sense.

3) "OH MY GOD, THAT'S EXACTLY WHAT HAPPENED!!!"

4) "Oh dear, so many tabs... Wait, this one has *Touchpad* written on it. Maybe if I click on it..."

5) "JESUS CHRIST, THERE'S AN OPTION CALLED "Enable tap to click" HERE, THAT'S EXACTLY WHAT I WAS LOOKING FOR!!! HOW COULD THEY READ MY MIND THIS FAR???"

6) "Hey, tap to click is working now. Cool."

All this took five to seven seconds. I do agree that the most popular/natural option should be the default, but while we don't reach a consensus about which one is it, please stop treating this as the most tragic usability disaster of the last century, or something.

---

### Post by Sashin on 2009-09-16
No, I think logically tap to click should be the default setting. As more people would prefer that functionality being used to it, and those that aren't are more likely to know how to change it.

Also, people with very sensitive touch pads can reduce sensitivity.

---

### Post by hanzomon4 on 2009-09-16
> **23meg said:**
> [It's (supposed to be) enabled for those]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/404219/comments/23").

But they have a button.. I've clicked it my self. 

I fail to see how this is bad.. you have a button(s) it's kinda redundant to have two ways to click on by default. Perhaps I'm spoiled by mac trackpads with one big button, or one big invisible button. I've used a few windows pc trackpads and they are awkward to use especially right clicking.

---

### Post by MacUntu on 2009-09-16
> **23meg said:**
> Is tap to click also disabled by default in Kubuntu?

No. :)

---

### Post by Schendje on 2009-09-16
> **tghe-retford said:**
> I just hope that like with the disappearing Gnome icons and non-customisation of notify-osd that this isn't going to turn into another situation where "we know better than you and its either our way or the highway".

I know one of the best things of Linux (and open source in general) is that you can customize basically everything. But most "average Joe" users don't care much about customizing, except when something is wrong. Because IMHO, a perfect design shouldn't *have* to be customized. Of course a perfect design doesn't exist (and we all have our own preferences) which is why options are a good thing.

However, designing something is making choices. Good choices makes a good design. You make these choices so the user doesn't have to. (How many people do you know who use custom themes or taskbars for Apple's OSX? I don't know many, because Apple is *great at design* and users don't *have* to modify it.)

So basically, if Ubuntu's design team (or DX, or whoever) makes good default choices, the amount of customization a user has to do should be minimal. So instead of "our way or the high way" it would be "trust our way, because we've thought this through and we think this is best".

I'm not disagreeing with you, your post just sparked these thoughts. :)


Having said that, this does look like a strange choice to make by the developers. I won't freak out yet though before I've seen the final release. :D

---

### Post by 23meg on 2009-09-16
> **MacUntu said:**
> No. :)

I thought so.

---

### Post by rondackcpu on 2009-09-16
WOW!  Having never found the way to disable the "tap-to-click" function on the touch pad, I can now remove the 10 layers of cardboard I have taped over the touchpads on all the computers which have a touch pad.  My thumb is ALWAYS hitting the touchpad while I type -- moving the cursor to some terribly inconvenient place without my wanting it moved. Much cleaning up of the typed material follows.  HURRAY for the guy(s) who helped me out immensely!!!

---

### Post by Sashin on 2009-09-16
You realize that you can have the touchpad disabled whenever you type.

---

### Post by jlacroix on 2009-09-16
> **infamousrev said:**
> The first thing I do on a new installation is disable tab to click.

I like this new update, good work!
Just because this option fits you personally, doesn't mean that it fits the majority. This update may be good for you, but for others it will wreak havoc and people won't understand at first why it's not working. No offense but I see praising such a thing just because it fits your personal style without thinking of the majority is a VERY selfish statement!

Not everyone knows about where to find this option, and not every touchpad has buttons on it. If you don't like this option you can turn it off, it takes all of ten seconds or less. However, having it disabled as default is not a wise choice for others because it was doing no harm in the first place, and as mentioned its the default in all laptops purchased at retailers. The general public WILL NOT understand.

I'll emphasize this again: For the developers to spend any actual amount of time on fretting over tap-to-click being default or not shows a SEVERE lack of priorities on their part. Why not leave it alone and tend to the things that actually matter, like stability and making the release solid? Spending any amount of time on this issue is extremely sad. Let's fix the important stuff first, and then worry about the smaller issues! 

I suggest making the default as it was and then holding a poll for everyone to vote on, and then the decision can be made after the important stuff is fixed. That is if any amount of time should be spent on this at all, I'm very disheartened that this debate even exists with boot issues and stability issues all over the place.

---

### Post by scaine on 2009-09-16
So somebody has changed the default, now we have to bend over backwards in an attempt to prove that they were wrong and have the default changed?  Sounds fishy.  There's almost always more to it than that.  Or at least, I'd very much hope there is.

Can anyone link to the original mailing archives that led to this decision?

Incidentally, anyone who cites that they don't like tap-to-click because they activate their mouse click while typing, [look here]("http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html").  It's an old article, and I don't believe you need to do the editing xorg.conf part anymore.  So basically, add a new start up item - simple as that.  Then, you'll find that you automatically disable your touchpad during typing and for 1 second after you've finished typing.

[EDIT] In fact, here's a much better link on the subject : [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig)

---

### Post by PC_load_letter on 2009-09-16
This is really a joke. I mean how much time was wasted, collectively, for people to respond one way or another just in this thread. I guess the developers of Gnome or at Canonical aren't wise enough, or connected enough to their communities, to change a feature like this just on a whim.....this is absurd!
Gnome developers, repeat after me: **IF IT AIN'T BROKEN, DON"T FIX IT!**

I totally agree, it's a flip-a-coin kind of decision in the sense that you can change it later, so it doesn't really matter what's the default. But I also seem to agree about what's been mentioned earlier, that the 1st time users and people switching from Windows & Macs will perceive it as a bug and may as well be a deal breaker for some. 

As for netbooks, don't you usually install Ubuntu remix on them, so why not just change this setting in the remix version? And leave it as it is (tapping = clicking) for everyone else. Is it that hard? 

+1 vote for keeping things as they were for quite some time, that is (tapping = clicking). 

Jeez.

---

### Post by scaine on 2009-09-16
> **PC_load_letter said:**
> This is really a joke. I mean how much time was wasted, collectively, for people to respond one way or another just in this thread. I guess the developers of Gnome or at Canonical aren't wise enough, or connected enough to their communities, to change a feature like this just on a whim.....this is absurd!
Gnome developers, repeat after me: **IF IT AIN'T BROKEN, DON"T FIX IT!**

I think it's important to establish who made the decision and why, before fretting about it too much more.  Both Gnome and Xorg developers have been mentioned now.

[EDIT : Found MacUntu's post from a different thread : [http://ubuntuforums.org/showpost.php?p=7316820&postcount=3]](http://ubuntuforums.org/showpost.php?p=7316820&postcount=3])

---

### Post by scaine on 2009-09-16
(Sorry for the two-in-a-row post)

To summarise, this was disabled by either xorg developers or possibly even the synaptic driver developers (one and the same?) at some point mid way through Jaunty development.  At that time, Debian created a patched package which reverted the new default.

Some time ago, debian decided to rename that package, which also had the side-effect of clobbering the reverted default back to "true" upstream default, so everyone on the bleeding edge (ie Karmic testers) lost tap-to-click.

Now, it appears that debian have [created a news file]("http://git.debian.org/?p=pkg-xorg/driver/xserver-xorg-input-synaptics.git;a=commitdiff;h=598ae3fe8592f80e97f58a1c54822754dcd5378e"), which explains how to revert this change, and appear to have to dropped the reversion from their package.

So an Ubuntu bug was filed and since that says "fix released", I believe (but might be wrong) that Ubuntu will shortly be restoring tap-to-click functionality.


Correct me if I'm wrong.

---

### Post by PC_load_letter on 2009-09-16
It's not like I'm making a case in a court, I'm sure there is someone is to blame for this nonsense, but I don't particularly care where to lay the blame as much as to ridicule the decision itself.

There are many many things that developers (Gnome or Ubuntu) can spend their time doing. Spending time on changing an option a to option b is like repainting a house with a different color instead of connecting it to the electrical grid. The developers need to focus on what's really important here.

---

### Post by mister_pink on 2009-09-16
I did have a funny feeling that this might turn out to be a misunderstanding. I really hope it does.

It is funny when you see threads full of complaints about something that turns out to not even be true!

---

### Post by scaine on 2009-09-16
> **PC_load_letter said:**
> It's not like I'm making a case in a court, I'm sure there is someone is to blame for this nonsense, but I don't particularly care where to lay the blame as much as to ridicule the decision itself.

There are many many things that developers (Gnome or Ubuntu) can spend their time doing. Spending time on changing an option a to option b is like repainting a house with a different color instead of connecting it to the electrical grid. The developers need to focus on what's really important here.

Well, each developer focusses on what's important to *them.*  In this case, the authors of the synaptic driver decided to disable tap-to-click (who knows why but there might have been valid reasons for them) and as a result, debian and ubuntu developers have had to scrabble around to compensate.

Obviously not ideal, but this has nothing to do with gnome developers and until I've been proven wrong, I believe that the Ubuntu devs are on your side in this (see my previous summary post).

This is testing after all.  These things happen.

---

### Post by williamts99 on 2009-09-16
Do I think that tap to click should be enabled by default, YES.  Will I bother to go and post in the mailing list, after reading through this thread, no.  Will it probably hurt new users, absolutly.  I was even wondering why it wasn't working.  In my opinion it wasn't a well thought out change.

---

### Post by MacUntu on 2009-09-16
> **scaine said:**
> [EDIT : Found MacUntu's post from a different thread : [http://ubuntuforums.org/showpost.php?p=7316820&postcount=3]](http://ubuntuforums.org/showpost.php?p=7316820&postcount=3])

Oh dear, I can't even remember things I've written some months ago... I'm getting old. #-o Good find anyways! :)

---

### Post by novafluxx on 2009-09-16
While I think disabling it by default is an inconvenience, I don't really care because I know where to go to enable it.

I've NEVER, not ONCE, seen a computer sold, that has this option disabled by default... so I'm not sure what the developers who decided this were thinking, however, its a small inconvenience and I can enable it in just a few seconds.

I have the same issue with Microsoft Windows. After a clean install there are a dozen or so small changes I make (eg. launch each window in a separate process, disable automatic restart on error) to get it exactly how I want it, and having to do this routine after a clean install of Ubuntu won't be that drastic. Just an inconvenience...

If the developers of FOSS want to take more of the market, and bring freedom to more people with open source software and operating system, they'll need to stop thinking like computer nerds (like me!), and start thinking like end-users.

Until then, my dad is going to keep using Windows XP because its what he is comfortable with, and he knows how to use it.

If someone like my father or mother even gave Ubuntu a chance, they'll immediately become confused as to why things they are used to just working in Windows or even Mac OS X don't work in *NIX. Granted, *NIX and Ubuntu are NOT trying, and should not attempt to BECOME Windows clones, there are a few basic usability things that should remain default, in my opinion.

---

### Post by dizzie on 2009-09-17
I have disabled my touchpad in BIOS, i hate it, its ultra sensitive, sometimes even when i drag stuff with it, it thinks "ohh he want to doubleclick".... :£

---

### Post by compat on 2009-09-17
as stated before, windows users/endusers feels that linux fails by default so it will be interpreted as a bug no matter what. this is a freaky change.

the next improvement could be to swap 'Ctrl' with 'Alt' key by default but tweak-able, of curse. I feel that 'Alt' key fits better in 'Ctrl' key button. that would be a another great move to expand even more the ubuntu distro. :P

seriously, tap should be enabled with the 'disable touchpad while typing' enabled by default.

---

### Post by 23meg on 2009-09-17
> **jlacroix]No offense, but this probably one of the lamest things I have heard of in Ubuntu since the removal of the screen resolution utility in a previous release.[/QUOTE]

Do you even know why it was removed?

[QUOTE=jlacroix]Even worse, there is a bug that causes a blinking black cursor on the top left corner of my screen and prevents X from starting, and this bug has been going on at least two months now with no resolution in sight. The fact that attention has been given to such a trivial thing as tap to click instead of major issues like the one I have makes me really question the priorities here...[/QUOTE]

Even if we assumed that software development was a zero-sum game where preventing a certain amount of effort from going into a certain area necessarily caused that amount of effort going into other areas, which it isn't, it takes a developer one minute to change a default gconf key from "true" to "false" and do an upload, so in other words you wanted one more minute spent on fixing your unknown pet bug. Well...

[QUOTE=jlacroix]Just because this option fits you personally, doesn't mean that it fits the majority. This update may be good for you, but for others it will wreak havoc and people won't understand at first why it's not working. No offense but I see praising such a thing just because it fits your personal style without thinking of the majority is a VERY selfish statement![/QUOTE]

The same could be said about the opposite said:**
> Not everyone knows about where to find this option, and not every touchpad has buttons on it. 

Read post #10.

> **scaine]Incidentally, anyone who cites that they don't like tap-to-click because they activate their mouse click while typing, [look here]("http://www.ubuntugeek.com/disable-synaptics-touchpad-while-typing-in-ubuntu.html").  It's an old article, and I don't believe you need to do the editing xorg.conf part anymore.  So basically, add a new start up item - simple as that.  Then, you'll find that you automatically disable your touchpad during typing and for 1 second after you've finished typing.

[EDIT] In fact, here's a much better link on the subject : [https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig](https://help.ubuntu.com/community/SynapticsTouchpad#Enabling%20SHMConfig)[/QUOTE]

In fact, you don't need to do any of that any longer said:**
> So an Ubuntu bug was filed and since that says "fix released", I believe (but might be wrong) that Ubuntu will shortly be restoring tap-to-click functionality.


Correct me if I'm wrong.

[You're wrong]("https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/404219/comments/19"). The bug you mention was about a Debian source package name change clobbering Ubuntu changes (not limited to tap to click).

---

### Post by MaX on 2009-09-17
Ok I didn't read page 6... but here goes.

Why don't have it "disabled" by default but when the user taps on the touchpad (that would normaly have triggered a click) the first time we ask. "It seems like you are trying to tap the touch pad, this feature is disabled by default. Do you want to enable it?" "No/Yes".

That way, all of us who doesn't use touchpad tapping need to say No, ONCE. And all of you who actually use it need to say Yes, ONCE.

This would of course be a User preference not a system wide preference.

---

### Post by MacUntu on 2009-09-17
> **MaX said:**
> Why don't have it "disabled" by default but when the user taps on the touchpad (that would normaly have triggered a click) the first time we ask. "It seems like you are trying to tap the touch pad, this feature is disabled by default. Do you want to enable it?" "No/Yes".

That's how Opera sets up its mouse gesture preference - I like it.

---

### Post by NCLI on 2009-09-17
I agree, asking the user sounds like the best possible solution.

---

### Post by mrboojive on 2009-09-17
I don't know what things are going to be like come release day, but, to me, disabling tap to click by default doesn't make any sense. It would be like muting the speakers by default. I might want to turn the sound off myself, but I don't expect it to be turned off for me. I expect all the functionality of my hardware to be enabled by default.

---

### Post by Arand on 2009-09-17
My thoughts:

The result of disabling touch to click will be that the majority of users thinks that ubuntu has broken their touchpad drivers.

TTC is something that everyone expects on a touchpad, those who are annoyed by it will be used to turning it off, those who use it will not be used to turning it on.

- Arand

---

### Post by novafluxx on 2009-09-17
> **Arand said:**
> My thoughts:

The result of disabling touch to click will be that the majority of users thinks that ubuntu has broken their touchpad drivers.

TTC is something that everyone expects on a touchpad, those who are annoyed by it will be used to turning it off, those who use it will not be used to turning it on.

- Arand

Next they should make the default brightness to 0, to keep from hurting peoples eyes on first boot. Next they can, as you suggest, mute speakers on first boot, by default. After that, they can...

---

### Post by psyke83 on 2009-09-17
> **23meg said:**
> I was actually thinking in the lines of guidelines provided by Microsoft to manufacturers, if any.

No such guidelines exist. However, I would interpret Microsoft's recommended guidelines from the configuration of their RTM (Release to Manufacturing) releases, which enables tapping by default.

> **23meg said:**
> The same could be said about the opposite; doing a web search for "disable tap click" returns millions of results, which shows that many people are annoyed by the feature and want to turn it off.

On Google, the search "disable tap click" results in 10,100 results - not quite "millions". Conversely, "enable tap click" results in 3,280 results (which I would imagine is lower because most operating systems have it enabled by default, unless they are using older operating systems whose generic drivers do not support advanced touchpad features).

Tap to click may be irritating to quite a few people, but they are most certainly the minority. If you insist that I am wrong, I would suggest that the burden of proof is upon your shoulders ("you" being Canonical, and/or whomever will ultimately decide to disable tapping in Ubuntu).

---

### Post by mudi on 2009-09-17
Tap-to-click needs to be on by default.  With some touchpads that don't even have mouse buttons out, and with great improvements in the linux touchpad drivers that seem to have curbed false clicks considerably (I remember back in the Dapper and Edgy days...) I see much more harm in disabling it than having it enabled by default.

Those who want to disable it will be able to find it.  People who need it enabled may not be able to get to it easily.

---

### Post by Stex on 2009-09-17
So, the people defending this option demanding mystical facts... Does anyone have any reason for changing it to be turned off by default above "it annoys ME" or, the barely less selfish, "it annoys me and other people"?

If something happens that annoys you you seek a way to turn it off, if something doesn't work and it used to you file a bug report.

On one laptop I use tap to click, on another I have it disabled but whatever way you look at it you should be able to tap to click by default.

Changing a default should not be looked at lightly, let alone changing it to something no-one else is used to. You say we can't speak for "everyone" but, tell me, did any of your laptops come with tap to click disabled?

Utterly ridiculous decision from upsteam to disable it, why do the ubuntu devs have to follow in their footsteps?

I try to avoid needless confrontation like this, but this is just stupid stupid stupid. It's right out of a troll's handbook...
Rant over :KS

---

### Post by NCLI on 2009-09-17
> **psyke83 said:**
> No such guidelines exist. However, I would interpret Microsoft's recommended guidelines from the configuration of their RTM (Release to Manufacturing) releases, which enables tapping by default.



On Google, the search "disable tap click" results in 10,100 results - not quite "millions". Conversely, "enable tap click" results in 3,280 results (which I would imagine is lower because most operating systems have it enabled by default, unless they are using older operating systems whose generic drivers do not support advanced touchpad features).

Tap to click may be irritating to quite a few people, but they are most certainly the minority. If you insist that I am wrong, I would suggest that the burden of proof is upon your shoulders ("you" being Canonical, and/or whomever will ultimately decide to disable tapping in Ubuntu).
Searching for "disable tap"gives me 49.300.000 results in Google, most of the related to the touchpad.

I still disagree with this decision though, seems stupid not to do the same as every single other OS! It's called expected hardware behavior people, most people don't even know you can turn it on or off!

---

### Post by psyke83 on 2009-09-17
> **NCLI said:**
> Searching for "disable tap"gives me 49.300.000 results in Google, most of the related to the touchpad.

I still disagree with this decision though, seems stupid not to do the same as every single other OS! It's called expected hardware behavior people, most people don't even know you can turn it on or off!

Very odd, perhaps it's a regional difference.

Using default Google search (Ireland):

In quotes:
[LIST]
[*]"disable tap" - 10,100
[*]"disable tap click" - 10,100
[*]"disable tap-to-click" - 10,100
[*]"disable tapping" - 3,190
[*]"enable tap" - 11,000
[*]"enable tap click" - 3,680
[*]"enable tap-to-click" - 3,680
[*]"enable tapping" - 1,980
[/LIST]

Without quotes:
[LIST]
[*]disable tap - 912,000
[*]disable tap click - 905,000
[*]disable tap-to-click - 1,140,000
[*]disable tapping - 331,000
[*]enable tap - 1,980,000
[*]enable tap click - 1,910,000
[*]enable tap-to-click 16,300,000
[*]enable tapping - 1,990,000
[/LIST]

As you can see, there is no conclusive evidence from a simple Google search to support* or deny the popularity of touchpad tapping. In most of the unquoted "enable" cases, the results vary from 1.9m to 16m, whilst the "disable" cases never exceed 1.14m.

*The raw numbers support the idea that tapping is more popular, but I would suggest that the unquoted search results are inaccurate. Most instructions to disable tapping would probably mention a step to "enable" a checkmark in a control panel/preferences application, for example. Therefore, quoted search results are probably more accurate in isolating the results we're looking for (assuming that you take *any* stock in a Google comparison).

---

### Post by Arand on 2009-09-17
Is the disabling even intentional in ubuntu?
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/378391)
^Seems to indicate not.
- Arand

---

### Post by Maheriano on 2009-09-17
I set up a Dell D600 laptop for my brother and by default the tap to click wasn't enabled so I thought the laptop was too old for it. I checked under the options to be sure and found that I could enable it so I did.

Then I bought my own laptop and enabled both the touch and scrolling. Then 4 months later I realized I can enable side to side scrolling as well, awesome!

---

### Post by 23meg on 2009-09-17
> **Stex said:**
> So, the people defending this option demanding mystical facts...

For the record, *I did not at any point defend this change*. If you can quote me to show otherwise, feel free to do so.

---

### Post by Sashin on 2009-09-17
Its already obvious that this change is neither welcome nor of much use, so how is it possible to notify the devs to change it?

---

### Post by scaine on 2009-09-17
> **23meg said:**
> 
In fact, you don't need to do any of that any longer; if you have a touchpad, there should be a "Touchpad" tab in your mouse preferences **by default**, where you can enable or disable tap clicking. I guess you're not testing Karmic. 


I'm testing, just not on my laptop.  As for my link, it doesn't disable tap-to-click in an on/off sense.  It only disables  tap-to-click when a key (on the keyboard) is pressed and for one (configurable) second thereafter.  Here's my startup item :

syndaemon -i 1 -t -d

The -i disables for one second, the -t only disables tap-to-click and scroll, not movement, whle the -d sets the command up to run as a daemon in the background.

I'll possibly upgrade my laptop towards the end of September, around beta time.  Hopefully this will still work.  If someone wants to test in the mean time, that would be cool.

---

### Post by MacUntu on 2009-09-17
Whew, nine pages! Yet still no discussion about tap-to-click found on the mailing lists so I guess no one here feels bugged enough? ;) I'm not saying it's wrong to have discussions in a discussion forum but it won't change a thing.

Get some valid (and objective) arguments and raise your voice at the right place.

---

### Post by scaine on 2009-09-17
> **MacUntu said:**
> Whew, nine pages! Yet still no discussion about tap-to-click found on the mailing lists <snip>

Get some valid (and objective) arguments and raise your voice at the right place.

Good advice, but not something I know anything about.  Are the mailing lists (which I detest, cos I rarely have access to my e-mail) the only way?  Would a bug be appropriate?

I won't be able to raise this personally until I upgrade my lappie, which won't be for another few weeks (it's my main device and I can't risk losing it to breakage).

And being slightly cynical, do you think the mailing list crowd would listen to someone like me, who has no developer experience to speak of?  Aren't the dev mailing lists quite difficult to follow?

---

### Post by 23meg on 2009-09-17
> **scaine said:**
> I'm testing, just not on my laptop.  As for my link, it doesn't disable tap-to-click in an on/off sense.  It only disables  tap-to-click when a key (on the keyboard) is pressed and for one (configurable) second thereafter.  Here's my startup item :

syndaemon -i 1 -t -d

The -i disables for one second, the -t only disables tap-to-click and scroll, not movement, whle the -d sets the command up to run as a daemon in the background.

I'll possibly upgrade my laptop towards the end of September, around beta time.  Hopefully this will still work.  If someone wants to test in the mean time, that would be cool.

You can do that via the GUI too.

> **scaine]Good advice, but not something I know anything about. Are the mailing lists (which I detest, cos I rarely have access to my e-mail) the only way? Would a bug be appropriate?[/QUOTE]

Read my last quote in post #43 said:**
> And being slightly cynical, do you think the mailing list crowd would listen to someone like me, who has no developer experience to speak of? Aren't the dev mailing lists quite difficult to follow? 

It depends mainly on how good a rationale you put forward and how you present yourself, not who you are. This is not to say that your reputation and past work don't influence people's reactions, which is the case everywhere, but it's not the main factor.

---

### Post by 23meg on 2009-09-17
> **MaX said:**
> Ok I didn't read page 6... but here goes.

Why don't have it "disabled" by default but when the user taps on the touchpad (that would normaly have triggered a click) the first time we ask. "It seems like you are trying to tap the touch pad, this feature is disabled by default. Do you want to enable it?" "No/Yes".

That way, all of us who doesn't use touchpad tapping need to say No, ONCE. And all of you who actually use it need to say Yes, ONCE.

This would of course be a User preference not a system wide preference.

That's the same as asking *everyone*, since it's next to impossible to never perform the tapping action accidentally, and that's not a sensible default. 

From [https://wiki.ubuntu.com/UbuntuArchitecture](https://wiki.ubuntu.com/UbuntuArchitecture):

> Applications should work immediately upon installation, without requiring additional steps, whenever possible. This "instant gratification" makes users more productive and allows them to explore the software choices available

---

### Post by mc4man on 2009-09-17
This, in stark contrast to the 'disable desktop scrolling' "fix". actually makes a lot of sense.

The means to enable it are in a visible and logical place, and there is always the mouse button right there to click so there is no loss of fuction when it's disabled.

There will be far more posts once karmic releases about flipping or sliding the desktop than  about this.

---

### Post by michael37 on 2009-09-17
ARGH I almost pulled my hair out before I found this thread.

I don't use touchpad to click, so when I upgraded, I didn't notice.  My wife uses touchpad for clicks, and she and (therefore) I got sooo frustrated. :mad: I assumed that my laptop was getting old and my touchpad just broke down.  I apologized to wife and bought a USB mouse. 

Yes, now I know it's trivial to fix.  Once I knew it's just a software option that was simply disabled in a fit of someones ingenuity.

---

### Post by blakamin on 2009-09-18
And here I was just thinking it was another alpha stuff-up in Karmic (yes, this is just jesting... I love the fun alphas provide me!) :P
Glad it can be sorted easily. Still, not good for the masses.:(

---

### Post by talkingwires on 2009-09-18
> **Sashin said:**
> Its already obvious that this change is neither welcome nor of much use, so how is it possible to notify the devs to change it?As I said in the OP, the developers are going ahead with it and feel that if anybody feels strongly enough about it, they should bring it up in the mailing list. I created this thread to draw attention to it and hope that somebody (ie, not me) would wade in there, because the developer's mailing list comes off more like a Developer's Tree Fort.

---

### Post by Sophont on 2009-09-18
I can see see the nest Linux article already:
"Tried that newfangled Ubuntu Linux. Was easy enough to install, looks actually quite decent. I was impressed by the cool effects and it seems it comes with a lot of software pre-installed. But as long as they can't even get simple details like tap-to-click right - which my windows laptop has offered me for many years - then Linux is clearly not ready for the Desktop yet."

---

### Post by fro1269 on 2009-09-18
> **novafluxx said:**
> While I think disabling it by default is an inconvenience, I don't really care because I know where to go to enable it.

I've NEVER, not ONCE, seen a computer sold, that has this option disabled by default... so I'm not sure what the developers who decided this were thinking, however, its a small inconvenience and I can enable it in just a few seconds.

I have the same issue with Microsoft Windows. After a clean install there are a dozen or so small changes I make (eg. launch each window in a separate process, disable automatic restart on error) to get it exactly how I want it, and having to do this routine after a clean install of Ubuntu won't be that drastic. Just an inconvenience...

If the developers of FOSS want to take more of the market, and bring freedom to more people with open source software and operating system, they'll need to stop thinking like computer nerds (like me!), and start thinking like end-users.

Until then, my dad is going to keep using Windows XP because its what he is comfortable with, and he knows how to use it.

If someone like my father or mother even gave Ubuntu a chance, they'll immediately become confused as to why things they are used to just working in Windows or even Mac OS X don't work in *NIX. Granted, *NIX and Ubuntu are NOT trying, and should not attempt to BECOME Windows clones, there are a few basic usability things that should remain default, in my opinion.


tap-to-click is horrible. get over it

---

### Post by misfitpierce on 2009-09-18
I think you should be able to choose if you want it on during installation in mouse/keyboard setup part for type of keyboard etc that you use. I like having tap to click on and like said with newer macs and laptops that don't have physical buttons. I dunno I just think the option should be offered at bottom like enable tap to click touchpad on laptops... you could check or uncheck if you want it. Thats my 2 cents...

---

### Post by Sashin on 2009-09-18
No its not its very convenient.

---

### Post by Mr. Picklesworth on 2009-09-18
> **Zorael said:**
> 
So, please don't scratch that feature off as "something too confusing for the user", too. Both that and tap-to-click are cornerstone features in my book.

You know, the "scrolling region" isn't actually a hardware feature, except for a little line drawn in the plastic...
The driver just looks for touches to the extreme edges and controls scrolling accordingly.

Granted, if you were using Windows at the time, needing to use a Synaptic touch pad to get that driver feature makes sense :)


Oh, and I may be mistaken, but I am pretty sure Apple doesn't have tap to click enabled on their Macbook Pros, either. (The ones with the full touch pad). The reason for this is that the button (the touchpad itself) is comfortable enough to make that feature unnecessary.

---

### Post by talkingwires on 2009-09-18
> **Mr. Picklesworth said:**
> Oh, and I may be mistaken, but I am pretty sure Apple doesn't have tap to click enabled on their Macbook Pros, either. (The ones with the full touch pad). The reason for this is that the button (the touchpad itself) is comfortable enough to make that feature unnecessary....so, what you're saying is that the Macbook Pros have tap to click enabled.

I kid. Although, since there's no markings on the touchpad to suggest that the bottom part of it functions as the button, it can be confusing. I was checking one out at a pawnshop the other week. Two pawnshop clerks, my girlfriend, and I all tried to "tap to click", to no avail. We assumed it was broken and they pulled it from the display case. It was only later, at a Mac store, that I learned that you can only "tap to click" in one certain area of the touchpad.

---

### Post by screaminj3sus on 2009-09-18
> **phenest said:**
> What about those that prefer it disabled? It's not difficult to enable/disable it using the option provided. And you're not going to please everyone by getting the default changed, so leave it be.

On windows and mac its enabled by default, your just going to piss most people who switch off. It should be on by default.

Any laptop you buy that supports the feature has it on by default.

People expect it to be on by default.

Leave it on by default.

Also horizontal scrolling is disabled by default, this is even stupider, WHY THE HELL would you enable vertical scrolling and not have horizontal scrolling enabled. That is some of the most nonsensical decision making I have ever seen.

---

### Post by psyke83 on 2009-09-18
> **Mr. Picklesworth said:**
> Oh, and I may be mistaken, but I am pretty sure Apple doesn't have tap to click enabled on their Macbook Pros, either. (The ones with the full touch pad). The reason for this is that the button (the touchpad itself) is comfortable enough to make that feature unnecessary.

Perhaps that's because some Macbook Pro models use a glass trackpad which doesn't have the proper tactile feel for tapping? Neverthless, that appears to be the exception and not the rule.

---

### Post by soumali on 2009-09-18
why is it done so???????please explain.
 
 
 
 
 
 
 
[Web Site Promotions](http://www.murs.org.uk)

---

### Post by deathsshadow77 on 2009-09-18
When they disabled it I thought it was because some update broke it. I have never ever experienced a laptop that didnt have it enabled. The people who wont know how to change it are most likely the ones that will expect it to be enabled. The people that want it will have to disable it like they do in any other OS. I think its a pretty bad choice.

On top of that what if your mouse button stops working for whatever reason (like mine has)? It will be very hard to enable tap to click as a work around, especially for someone who doesnt know keyboard shortcuts.

The safe decision is to enable it by default.

---

### Post by Mr. Picklesworth on 2009-09-18
> **psyke83 said:**
> Perhaps that's because some Macbook Pro models use a glass trackpad which doesn't have the proper tactile feel for tapping? Neverthless, that appears to be the exception and not the rule.

Okay, I have confirmed this, and I know this dates back beyond the glass touch pads. The only reason I exhibit doubt is because people here keep claming otherwise, but I have never seen a Macbook do tap to click *by default*, at least in Canada. (And, working part time in computer retail, I happen to see a lot of them).

So, to debaters in general: please stop saying that Macs have tap to click by default just because it suits your argument. They don't.

---

### Post by psyke83 on 2009-09-18
> **Mr. Picklesworth said:**
> Okay, I have confirmed this, and I know this dates back beyond the glass touch pads. The only reason I exhibit doubt is because people here keep claming otherwise, but I have never seen a Macbook do tap to click *by default*, at least in Canada. (And, working part time in computer retail, I happen to see a lot of them).

So, to debaters in general: please stop saying that Macs have tap to click by default just because it suits your argument. They don't.

I wasn't refuting your claim - I was merely suggesting a reason why it may be disabled on Macbook Pro laptops (which seems to be inaccurate, if not all Pro's have glass touchpads).

That doesn't change the fact that Macbooks are the exception and not the rule - they hold a market share of ~10% or so, last time I checked.

---

### Post by jbernardo on 2009-09-19
I just hope kubuntu devs don't follow this - it seems more and more like one of those enlightened decisions on pair with the one by the xorg devs to disable ctrl-alt-bksp at all costs.

---

### Post by meborc on 2009-09-19
if this is a change made only because of macbooks glass track pad, then i would like to know what is the official macbook market share in ubuntu? 

i still think the decision of whether to disable tap-to-click should be made in the installer when the appropriate hardware has been identified (which needs this kind of default setting)

---

### Post by scaine on 2009-09-20
Disabling CTRL-ALT-BS is irrelevant in terms of what other O/S's do - they don't use that combination, so disabling it isn't an issue in terms of cross-O/S user expectation.

Disabling tap-to-click however, when it's the default on just about every laptop you're likely to buy?

Interesting claim that Macs don't have this enabled by default - EVERY mac I've had the displeasure to use has had tap-to-click working as you'd expect.  Note - "as you'd expect" as I suspect every user of laptops expects.

So, if it's not the default on Macs and yet has been on with every Mac I've used, then it's actually been turned on in those cases.

---

### Post by Ric_NYC on 2009-09-20
laptops have touchpads for a reason.

Trying to reinvent the wheel?

---

### Post by talkingwires on 2009-09-22
> **Ric_NYC said:**
> laptops have touchpads for a reason.

Trying to reinvent the wheel?Why reinvent the wheel when you could [just use it for *everything*]("http://www.youtube.com/watch?v=s0Gzq-QEt0s")?

---

### Post by meborc on 2009-09-22
can someone help with finding the "official" explanation WHY the developers decided to turn off the tap-by-click by default?

i would really like to see the actual reasoning (or the lack of it) :D

EDIT: found this brainstorm idea... look at the score :D [http://brainstorm.ubuntu.com/idea/3958/](http://brainstorm.ubuntu.com/idea/3958/)

---

### Post by NCLI on 2009-09-22
My touchpad doesn't work in Ubuntu anway, so meh.

This thread is entertaining though. :popcorn:

---

### Post by cyberkilla on 2009-09-22
:deleted:

---

### Post by SoftwareExplorer on 2009-09-24
> **3rdalbum said:**
> Tap-to-click is horrible on netbook touchpads, because they are so sensitive.

For those of you saying "I never use the buttons"... how do you right-click then?
Well, a three finger tap works on my laptop. Or you can set it right click when you tap a specific corner.



@Everyone/Anyone: Where is the developer mailing list, and I just send an email to it, right?

---

### Post by scaine on 2009-09-24
> **meborc said:**
> can someone help with finding the "official" explanation WHY the developers decided to turn off the tap-by-click by default?

EDIT: found this brainstorm idea... look at the score :D [http://brainstorm.ubuntu.com/idea/3958/](http://brainstorm.ubuntu.com/idea/3958/)

11 votes for disabling, 1 don't care and 84 votes for keeping it active.

But as I mentioned earlier, I think the decision was possibly taken for technical reasons.  I still can't find the original assertions by the x.org/synaptic developers though, only the earlier-posted reaction from the debian/ubuntu devs.

I would be nice to hear why turning it off as a default was even considered against evidence like that brainstorm, let alone implemented in such a core, upstream project.

---

### Post by ode on 2009-09-24
It was the first thing I noticed when I booted the liveCD.

Unless there is a compelling technical reason why it should be disabled I would like it to be on.

---

### Post by jarocooke on 2009-10-02
Firstly I don't mean to offend anyone,... but,...

This is the most ridiculous thread I have ever come across.  Of cause tap-to-click should be on by default.

People who are used to it, coming from the Windows/Mac worlds will expect it and not immediately think to go searching in the menus to get it back.  They just reinstall Windows five minutes later...

A more technical user, more used to Linux and Ubuntu, upon finding that the tap-to-click is enabled, will look for the mouse menu entry in order to disable it.

Surely this is the only sensible conclusion, if Ubuntu is suppose to be a serious Desktop OS?

Oh and one more thing, with this disabled by default, the touchpad becomes almost unusable on the Dell mini 10v.  You know, the one that COMES with Ubuntu from Dell!  (This is because the mouse moves when you click, the touchpad and buttons are one).

---

### Post by Arand on 2009-10-02
@jarocooke: Touchpads which _only_ use tap-to-click are still supposed to have it turned on by default...


But indeed, I myself find it very worrying.

From what I've read on the devel mailing list, it seems they're wanting to try this setting throughout beta and see what kind of response they get.

> As I said, many users find it confusing and hard to use. Users who like
it, tell me that *all* users like it. Users who don't like it tell me
that *no* users like it. Both groups tell me that for the insane users
on the other side of the equation they can easily change the setting.

Not that we are past beta freeze, it is time to take our best guess and
ship the beta and see what kind of feedback comes in from a larger group
of users.
source: [https://lists.ubuntu.com/archives/ubuntu-devel/2009-September/029092.html](https://lists.ubuntu.com/archives/ubuntu-devel/2009-September/029092.html)

Reason given for disabling is to avoid unwanted clicks (which to many are annoying and/or confusing, granted). But I do think the annoyance from the group who thinks ubuntu has broken touchpad drivers will be greater though.

Soo... We'll have to just continue shouting our indignation it seems.

- Arand

---

### Post by benjamimgois on 2009-10-02
I just installed Karmic Beta, and i was about to make a bug report on lauchpad, thinking that my touchpad Tapping doesn't work. Now that i saw that it was a decision from canonical. Who have this !@# idea ?

---

### Post by tommcd on 2009-10-03
Glad I found this thread. I was struggling to figure out why tapping didn't work.
Geez, first they disable killing the X-server with ctrl + alt + backspace, now they disable tapping on the touchpad. I don't think it should be disabled by default. It is a useful feature.

---

### Post by thecow on 2009-10-03
Definitely extremely silly that this is being done.  And if it is being done it should be 'extremely' easy to change.  Meaning if I go into Preferences->Mouse there should be an icon with a man dancing next to it to draw your attention

---

### Post by SoftwareExplorer on 2009-10-03
I sent the following to the ubuntu developer list:
> Subject:Karmic touchpad request	
From what I've read, I sounds like karmic will not have touchpad's tap to click enabled by default. I would like to put my vote in for having it enabled by default and also having the touchpad disabled by default when you are typing. (Such an option does exist in karmic)
Here's why I think it should be that way:
In windows, the default is to click when the touch pad is tapped. That means that most likely new Ubuntu users that try karmic will think that Ubuntu (or Linux for that matter) doesn't work properly with touch pads.
As far as experienced users, some don't like tap to click, but they are experienced users, and are probably used to turning it off.
Also, look at the numbers on this brainstorm idea. Brainstorm Link At the time of writing this email, 88 said they supported having tap to click on by default, 1 person said they didn't care, and 11 wanted it off by default. That's 88 percent in favor of having tap to click on by default!

As far as disabling the touch pad while typing, it will solve the most common reason people turn the touch pad off. At the same time, I think it would be pretty hard physically to use the touch pad and keyboard at the same time and most programs wouldn't require require you to do this anyways. On top of that, this feature could also be turned off by advanced users. So that way, we would (hopefully) have a win-win situation.

Thanks,
Erik

You can see the responses [[COLOR="Blue"]here[/COLOR]]("https://lists.ubuntu.com/archives/ubuntu-devel/2009-September/thread.html#29223") in the email that have karmic touch pad request for the subject.
I'll have to say that the responses were a little disappointing to me, but maybe they can change it now. The main excuse seemed to be that they couldn't change it with the beta still looming, but that goal has been reached, so I think the freeze would be over.
The other thing is that it seems that a lot of the people who don't want to change it back to tap to click by default are complaining about accidental clicking, and they forget about the fact that part of the default could be to disable touchpad clicks with typing, **which is actually available via the GUI in karmic**!
Also, I'll say this, it isn't hard to join the discussion, all you have to do is send your comment to [email]ubuntu-devel@lists.ubuntu.com[/email]. Past that you can subscribe to the list so you see replies at [https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel).

---

### Post by SoftwareExplorer on 2009-10-03
Also, one of the people on the mailing list said: 
[QUOTE=Rick]As I said, many users find it confusing and hard to use. Users who like it, tell me that *all* users like it. Users who don't like it tell me that *no* users like it. Both groups tell me that for the insane users on the other side of the equation they can easily change the setting.

(I think he meant 'Now')-> Not that we are past beta freeze, it is time to take our best guess and ship the beta and see what kind of feedback comes in from a larger group of users.

Cheers, Rick
[/QUOTE]
So it sounds like they are ready to hear your feedback, whatever it may be in support of.

---

### Post by Ellipsis on 2009-10-03
It was a really bad idea to turn it off by default... I mean BAD (as bad as Skydiving without a parachute). Taking away functionality that even 20% of the population uses regularly confuses a lot more people than the feature ever did. 

I am glad someone had the good sense to fix this.

---

### Post by SoftwareExplorer on 2009-10-03
> **Ellipsis said:**
> 
I am glad someone had the good sense to fix this.
So where is it fixed?

---

### Post by petteriIII on 2009-10-03
> **SoftwareExplorer said:**
> So where is it fixed?


ALT and f2 - write:gconf-editor and hit enter - desktop - gnome - peripherals - touchpad - 'tap-to-click'

Hope you can decipher my message

---

### Post by SoftwareExplorer on 2009-10-03
> **petteriIII said:**
> ALT and f2 - write:gconf-editor and hit enter - desktop - gnome - peripherals - touchpad - 'tap-to-click'

Hope you can decipher my message

I get what you are saying, but you can change it at System->Preferences->Mouse and then the touchpad tab. What I'm talking about is what it is set to by default.

---

### Post by jward3010 on 2009-10-03
> **thecow said:**
> Definitely extremely silly that this is being done.  And if it is being done it should be 'extremely' easy to change.  Meaning if I go into Preferences->Mouse there should be an icon with a man dancing next to it to draw your attention
Ha Ha ha aha ha aha ah damn right

---

### Post by tekstr1der on 2009-10-15
And there was much rejoice...

```
gnome-settings-daemon (2.28.0-0ubuntu5) karmic; urgency=low

  * debian/gnome-settings-daemon.gconf-defaults:
    - enable tap_on_click and disable_while_typing on by default,
      it's the less confusing behaviour for user and was the consensus
      during the discussion on the lists


```

---

### Post by talkingwires on 2009-10-15
> **tekstr1der said:**
> And there was much rejoice...

```
gnome-settings-daemon (2.28.0-0ubuntu5) karmic; urgency=low

  * debian/gnome-settings-daemon.gconf-defaults:
    - enable tap_on_click and disable_while_typing on by default,
      it's the less confusing behaviour for user and was the consensus
      during the discussion on the lists


```
Well, thank the heavens for that. I thought I'd have to stick a Post-It note on every Ubuntu disc I handed out with a note saying, "Oh, and your touchpad isn't broken, it just seems that way. Here's how to fix it..."

---

### Post by NCLI on 2009-10-15
Fantastic news. I guess they really do listen to the users!

---

### Post by SoftwareExplorer on 2009-10-15
Yay! =D>

---

