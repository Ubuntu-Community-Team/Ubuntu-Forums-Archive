---
title: "Lucid Button Positions"
date: 2010-03-06
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Meep3D on 2010-03-06
I have to say I am disappointed by the proposed change in button position, and quite frankly surprised that it is getting any support.  So here's my run-down of why I think it's a bad idea (after screenshot):



1. It's not like Windows or OSX. E.G.

OSX = [x][min][max][====bar====]
Lucid = [min][max][x][====bar====]
Windows = [====bar====][min][max][x]

It's not going to be an easy transition from any platform to this as it stands.  There are literally decades of ingrained history of 'close is in the top right/left corner'.  Now is it in a seemingly arbitary position.  It is possible to get used to it, but it brings no benifits making it confusing change for the sake of confusing change.

2. Usability

OSX supports a unified file menu, meaning the existing file menu is in the very top left of the screen.  Ubuntu doesn't, putting the file menu immediatley below the window title bar.  This means the chance of mis-clicks of people going for 'file' or 'edit' and accidentally hitting min/max/close increases greatly.

The Fitts law arguments also make no sense - it doesn't apply here.  I also refute the argument that grouping the controls makes it easier to go from one to the other for two reasons.

[LIST=1]
[*]File menus are drop downs, meaning by the time you have interacted with them your cursor will be far enough away as to not make a difference (and the subsequent interaction with the title buttons will then require a lot more care and precision)
[*]The chances of you using the two groups of buttons in serial is extremely low - grouping them makes no real advantage.
[/LIST]

3. Looks

It looks very visually unbalanced to have such tightly packed controls cluttered on the left yet large amounts of nothing on the right.  The always red close button that isn't in the corner also looks a bit strange and 'abandoned'.  With such a large amount of unused space on the right it raises the question of if that space can be used more efficiently.  There have certainly been motions on other platforms to use this space more efficiently, ala:
[IMG]http://cache.techie-buzz.com/images/stories/Firefox4.0HasItsEyesOnGoogleChrome_12500/firefox_4_mockup_tabs_on_top.png[/IMG]
If there was a serious departion here to save screen space (always a good thing) It would be good - but there isn't.

4. Reason

There is no point to this.  It doesn't bring any actual improvements in looks or usability.  There is no technical need for it.  While I am all behind improving things and willing to re-learn if there is an improvement in efficiency at the end there is no such case here.  It's change for the sake of it.

I have a keyboard where the creator saw fit to replace the pause/break key with a 'power' key (and move the pause/break key down).  I ended up physically removing the key from the keyboard as I kept accidentally shutting it down and I believe we'll have the same effect here.

</rant>

---

### Post by blueshiftoverwatch on 2010-03-06
This is the first I've heard of this. They're going to include an option for changing it back to the default I hope though.

---

### Post by appier on 2010-03-06
My concern here is support for all of my users who have just recently figured out where the power button is and now gotten used to the idea of controls.  Unnecessary changes are not good when dealing with implementations whose users are not that computer savvy!

---

### Post by magneze on 2010-03-06
[http://ubuntuforums.org/showthread.php?t=1422422](http://ubuntuforums.org/showthread.php?t=1422422)

There's another thread on this. I agree though.

Does anyone know if there's any supporting documentation behind this change? Usability studies for example?

---

### Post by chucky chuckaluck on 2010-03-06
It'll probably still be easily changed (if you can ever find it in the gconf registry). I'm just curious about the reason behind doing this.

---

### Post by swoll1980 on 2010-03-06
It drove me nuts on the left. Did a gconf-editor apps>metacity>general look for button configuration, double click it.You just have to stick a : colon at the beginning of the line, and swap min and max. Not something I would expect a non technical person would want to deal with. I think I heard they will be on the right when the final version is released.

---

### Post by skymera on 2010-03-06
You can just move it back to the right.. i did.

---

### Post by swoll1980 on 2010-03-06
> **skymera said:**
> You can just move it back to the right.. i did.

New comers aren't going to know how. It will cause a flood of "How do I switch the buttons" threads.

---

### Post by Uncle Spellbinder on 2010-03-06
> **swoll1980 said:**
> New comers aren't going to no how. It will cause a flood of "How do I switch the buttons" threads.
Exactly. 

I still have heard no explanation as to the reasoning behind this change. I'm leaving it on the left for now to see if I can get use to is.

---

### Post by skymera on 2010-03-06
What i find MORE annoying is the fact the order of the buttons has changed.

It was: Minimise, Maximise, Close
It's now: Maximise, Minimise, Close

The amount of time i've gone to maximise and window and it's minimised *sigh*

---

### Post by BigSilly on 2010-03-06
I don't mind the change and I'm sure I'll get used to it, but I do hope they stick an easy way to change it in there somewhere. It couldn't hurt.

---

### Post by Ozor Mox on 2010-03-06
I don't like it either. I'm hoping they put it back as it was, since I think it's a better default. If not then I guess I'll just figure out how to change it right after I install 10.04.

---

### Post by squilookle on 2010-03-06
There is no reason the buttons have to be on the right, other than the fact that most of us coming from Windows or most Linux distributions with the default settings are used to the buttons being on the right, but I'm struggling to see the benefit or the point of this change.

---

### Post by kaldor on 2010-03-06
To be honest I like the new button layout.

My only problem is that other people are going to whine about it non-stop. Just like people who first try OS X whine about it. 

People hate change.

---

### Post by Madspyman on 2010-03-06
> **kaldor said:**
> To be honest I like the new button layout.

My only problem is that other people are going to whine about it non-stop. Just like people who first try OS X whine about it. 

People hate change.

How do you think Mac users would feel if Apple moved the buttons to the right?

---

### Post by octesian on 2010-03-06
For those of us that hate and fear change, I fixed the buttons with a little gimp-work and file-renaming for the Ambiance theme.  They're it the attached tarball.

Should be able to just extract it and copy to /usr/share/themes and it'll over write the one thats all funky.

---

### Post by AllRadioisDead on 2010-03-06
Window controls are overrated.

---

### Post by Nburnes on 2010-03-06
I think this change is a pretty nice one. I am getting used to it rather quickly.

---

### Post by vevel on 2010-03-11
> **kaldor said:**
> To be honest I like the new button layout.

My only problem is that other people are going to whine about it non-stop. Just like people who first try OS X whine about it. 

People hate change.

I think that the issue shouldn't be whether or not people can accurately be described as hating change, but whether or not the content of a given change is worth advancing despite resistance, and whether or not the resistance is a reasonable thing.

In this case, I think any 'whining' is in fact reasonable.

Here's why: I just don't see the point of changing the button layout.  It seems needlessly confusing for most users.  And what is being gained?  It's an arbitrary design choice -- functionality is not lost, but the mechanism to trigger a function is unyoked from established practice.

Sure, an option is great (and I favor a mechanism to give the option easily), but I don't want someone's "think[ing] different[ly]" foisted upon me.  (And as others have pointed out, it's not even quite the OSX UI logic we're seeing.)

---

### Post by Madspyman on 2010-03-11
> **vevel said:**
> Sure, an option is great (and I favor a mechanism to give the option easily), but I don't want someone's "think[ing] different[ly]" foisted upon me.  (And as others have pointed out, it's not even quite the OSX UI logic we're seeing.)

The reason Mac's buttons work on the left is because of a global file menu. Ubuntu copied this difference without the reason for it. Not only that, but they did it wrong. Lucid isn't just an OS X clone it's a broken OS X clone.

---

### Post by grandtoubab on 2010-03-11
to switch back to the ancient look
```
gconftool-2 --type string --set /apps/metacity/general/button_layout "menu:minimize,maximize,close"
```

---

### Post by cariboo on 2010-03-11
I moved the close button to right right and left the min/max buttons on the the left.

---

### Post by spangaer on 2010-03-21
I probably won't be adding anything new, but part of the open community is expressing your opinion so I will do that.

Look I'm not opposed to progress, if I was, why on earth would I mind installing a beta OS. But the concept behind progress is that there is actual improvement. Changing things for no good reason is simply unproductive.

Window management buttons have been on the right side since the dawn of time, if I may believe Wiki. The first XServer implementations have it there, Windows has them there and so did previous versions of Mac OS. If Apple wants to put them on the other side to show how different they think, thats great for them. But I see no that much value in that kind of logic. (Yes, I do believe previous writers pointed out some valid reasons may exist for Apple to do so)

And what kind of reasoning is people being whiny because they oppose change. Look, why would you oppose change in this case. Because it forces us to change habits, more specifically in this case automatisms. Automatisms allow us to live life without having to think about trivial tasks. They aren't there when you're born, but are built with experience, which takes time. By forcing people to change automatism (for no good reason) your actually forcing people to waste "thinking time" on trivial actions. It's like changing the order of the throttle and the break in a car, just because the designer liked it better that way.

That's my 2 cents

---

### Post by cadkins on 2010-03-21
I was really disappointed in seeing the buttons change.  Like others have said, there's no good reason to move them.

A lot of people that I have turned onto Linux, I've shown them Ubuntu because I feel they can get used to it easily enough.  With the window buttons the same (right now) as Windows, it makes it a little easier to get used to.

Couple this and the "me menu", and I am not really finding Lucid that appealing.

---

### Post by shobon on 2010-03-21
> **cariboo907 said:**
> I moved the close button to right right and left the min/max buttons on the the left.

I like this!

---

### Post by seenthelite on 2010-03-21
Simple Solution

---

### Post by nubalci on 2010-03-21
Dear octesian: by any chance do you have a similar modification for "Radiance" theme?

---

### Post by QwUo173Hy on 2010-03-21
It now feels to me like the buttons should have been on the left all along! I've only ever used Windows, Gnome and KDE. I'm very happy with the new interface.

---

### Post by Seventh Reign on 2010-03-21
I think we are all forgetting that GNU/Linux is all about choice.  You can have your buttons on the top left or the top right or dead center in the middle or on the bottom (not sure if thats actually possible, but you get the point).  Canonical has forced this change on us and barely asks our opinion AFTER the majority have complained.  

The change may be better or it may be worse.  I havent been able to use my Lucid system lately, so I havent been able to gather an opinion about it.  A change like this would have been better done by a focus group, and not forced on all of us without warning.  Some might say that we as alpha/beta testers ARE a focus group, but the problem is that Canonical doesnt listen to us.  Whether we like the change or not, they are going to do what they want, how they want.

Shuttleworth was right it is not a democracy.  It is a Totalitarian sytem.
"Rule by a single political party. 
People are forced to do what the government tells them." 

Chalk up another Win for Linux Mint.  Although I dont agree with the way Mint keeps their Alpha systems behind a locked door.  Everything else that Clem and his team does is in the best interest for the distribution and its users.  That is something Canonical and Ubuntu have never been able to claim.

---

### Post by raymondh on 2010-03-21
> **cariboo907 said:**
> I moved the close button to right right and left the min/max buttons on the the left.

nice

---

### Post by QwUo173Hy on 2010-03-22
> **Seventh Reign said:**
> 
Shuttleworth was right it is not a democracy.  It is a Totalitarian sytem.
"Rule by a single political party. 
People are forced to do what the government tells them." 

....

Everything else that Clem and his team does is in the best interest for the distribution and its users.  That is something Canonical and Ubuntu have never been able to claim.

Complete contradiction there. We're 'forced' to do things a certain way by the evil Canonical, and yet someone was free enough to modify Ubuntu into a style that you like, namely Mint.

Forced? You're not even billed.

---

### Post by jeffus_il on 2010-03-22
Doing a "cost/benefit analysis", I can see the costs, but no benefits.
Breaking standards for no real important reason is a bit pointless.

Users often use more than one system, at home at work, on a laptop, netbook,
Why shouldn't the close button just be there on the top right, when the mouse automatically makes his sweep there.

I can see windows users who try Ubuntu saying "What the f.. is this?"

and then reverting to windows.

---

### Post by ndefontenay on 2010-03-22
Apparently it's paving the way for some more control on the right hand side in 10.10.

There's more to come.

---

### Post by Mercury_Alpha on 2010-03-22
There's [a widely distributed Python script](http://www.omgubuntu.co.uk/2010/03/easy-gui-window-button-switcher-for.html) that allows you to make the switch in about five seconds. No reboots necessary. Don't even have to reload X.

Personally, I found it by Googling "ubuntu lucid window buttons" (without the quotes). The title of the key search result is "Easy GUI Window Button Switcher for Lucid (and Karmic) users," which looks pretty straightforward to me, and easy to distinguish from search results that are not what I am looking for. Perhaps more effort required than raging on the Internet, but I can't be responsible for that, nor how much your mother hugged you when you were growing up.

This is the kind of thing you can do on an open platform: *Experiment with it*. Canonical is experimenting with some buttons in Gnome windows. They were not obligated to tell you because you are not obligated to listen. Because you are usually a Google search away from reverting cosmetic changes.

If you want the stable, white-picket-fence version of Linux, you've come to the wrong distribution. Try Debian or Red Hat Enterprise. This is frontier land, where we change buttons. And change them back.

---

### Post by Kevin on 2010-03-22
Hey everyone, I spent a bit of time writing a patch for metacity that adds support for themes to specify the button layout.  This would mean that at least if Ubuntu decided to keep the buttons on the left, it would only apply to their themes.  It also adds some functionality in gconf to ignore theme's layouts. The patch should apply to compiz as well, it would just need to be recompiled against the patched metacity AFAIK.

Its my first real experience with Gnome programming so I'm sure there are some rough edges on it, but it works for me!

If someone with more experience looked a bit into my patch I think it would be a good solution, and also allow more flexibility in theme design.

The patch is attached to this bug report: [https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/533758]("https://bugs.launchpad.net/ubuntu/+source/metacity/+bug/533758")

---

### Post by KrazyPenguin on 2010-03-22
Too bad we couldn't get these threads merged!!!

Anyway in the other thread I explain as to why the buttons were moved.
I got the information off of Distrowatch Weekly.
Goto go.
good luck!!!
;-)

---

### Post by forcecore on 2010-03-22
as i said here it is solution for everyone thats it

[http://ubuntuforums.org/showthread.php?p=9008122#post9008122](http://ubuntuforums.org/showthread.php?p=9008122#post9008122)

---

### Post by Sandsound on 2010-03-22
> **ndefontenay said:**
> Apparently it's paving the way for some more control on the right hand side in 10.10.

There's more to come.

Yes... lets fill every empty space with something :rolleyes:

If we are going to have another set of controls (sometime in the future... maybe...), why not just put THEM on the left?

I don't see this helping Ubuntu with bug#1 at all.
It's just one more thing to fix every time I install Ubuntu, and the list seams to get longer with every release :sad:

---

### Post by Nightstrike2009 on 2010-03-22
Hiya 

I have tried to make it easier from newcomers to swich back with my thread [http://ubuntuforums.org/showthread.php?t=1436020]("http://ubuntuforums.org/showthread.php?t=1436020") the credit goes to Free Trader Beowulf, Gericom and the Ubuntu Tweak team though (I just searched yahoo for it LOL) he also mentions Ubuntu Tweak 0.5.3 has this option too.

---

### Post by rahilm on 2010-03-22
I bet the next improvement in the next LTS they make is moving the titlebar to the bottom//
it will be so cool..won't it??..a great scope of improvement

---

### Post by reiki on 2010-03-22
I swear I've seen the answer to this but now I can't find it. 

I ran the command line entry as suggested to move the buttons back over to the right side. 
How do I put them back over on the left where they were?

I guess I'm just one of those people that doesn't feel this is a big deal :) and having them on the left is OK. I just have to get used to the new position. I have caught myself putting the cursor to the upper right corner (when the buttons were on the left), and then went, "DOH!", and moved to the left upper. Probably motor memory, but I think even at age 57 I can be retrained. :) ..... or at least I like to THINK so. What the heck, I'm running linux.... so I SHOULD be retrainable.

---

### Post by Nightstrike2009 on 2010-03-22
If you wish to revert back with gconf-editor use:

> Then navigate to &#8216;apps / metacity / general&#8217; look for the button layout and change it to read:

"menu:maximize,minimize,close"

seems to correct the graphical glitches but I don't know how to get back to left

---

### Post by QwUo173Hy on 2010-03-22
> **Sandsound said:**
> 
If we are going to have another set of controls (sometime in the future... maybe...), why not just put THEM on the left?

Id imagine thats because the space on the right is twice bigger than the tiny space above the File menu.

---

### Post by reiki on 2010-03-22
> **Nightstrike2009 said:**
> seems to correct the graphical glitches but I don't know how to get back to leftto put them back that line reads "maximize, minimize, close"

note that the word "menu" is not there.
This puts them back to the left as they were in the default install.

---

### Post by WeaponsTheyFear on 2010-03-22
I've been using Ubuntu for awhile now, even dropped Win7 in favor of 9.10.  I find Ubuntu more pleasurable as a development environment and in general as an everyday OS alternative to the big players.

However, I tried Lucid the other day and had to revert back to 9.10.  There was a lot I liked about Lucid (and I do mean a lot).  The one thing however that completely drove me mad was the placement of the window controls.

About every major OS is consistent with their placement of these controls, which allows some sense of familiarity across different OS'.  Lucid however, decided it was going to be different and break out of the box, which also makes the entire left upper corner of the window look like a complete crowded mess.

If yall are gonna change things like this up, we should at least be able to control if we want the controls on the left or right side rather than being forced to keep it in it's current location.

Devs, please, please, please fix this.  Everything else about Lucid is perfect (the theme and color scheme, the updated software center), leaving this as the one and only thing left to do.

---

### Post by bug67 on 2010-03-22
With Linux, there's always a solution:

```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

---

### Post by thatguruguy on 2010-03-22
> **WeaponsTheyFear said:**
> 
About every major OS is consistent with their placement of these controls, which allows some sense of familiarity across different OS'.  Lucid however, decided it was going to be different and break out of the box, which also makes the entire left upper corner of the window look like a complete crowded mess.

OSX, which is the only "major OS" (at least for desktops) other than Windows, places the controls on the left.

---

### Post by jacobmh on 2010-03-22
> No. This is not a democracy. Good feedback, good data, are welcome. But we are not voting on design decisions.

-Mark Shuttleworth


This came from this [message]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633/comments/167") where Mark relates to us why users don't get a say when it comes to the blatant, inappropriate, and functionally useless Mac fanboyism inherent in moving the buttons in Lucid Lynx to the upper left of the window. 

For those of you who have not yet upgraded, I think you will find this to be a bigger deal than you realize. For those of us who grew up on Windows (and considering it still has majority OS market share, that would be most of us) it presents a counterintuitive change that reduces productivity by increasing the time it takes to realize that the X button is **not** where it has been for our entire lives.

Mark's point about the Ubuntu Meritocracy is only relevant when their decisions actually have merit. Otherwise "Ubuntu Meritocracy" becomes an oxymoron.

Shuttleworth: For the love of Linus, change the buttons back.

---

### Post by asmoore82 on 2010-03-22
A little over the top there, just put *your* buttons where *you* want them.

I agree with the design decision, but I have chosen to split my buttons up as attached.

---

### Post by pastalavista on 2010-03-22
Nobody I know uses the default setup anyway. Change it to how you want it to be. That's one of Ubuntu's biggest selling points. This just shows it can appeal to everyone... not just you.

---

### Post by jacobmh on 2010-03-22
I did, I installed emerald. My point is that this changes one of the reasons that Ubuntu became so widely used- that it attracts Windows users to free, usable and familiar-feeling Linux software. I am a Computer Science student that regularly uses bash and tcsh to scoot myself around, but I still use the GUI out of familiarity, and having to mess around with it because some dipstick moved stuff, then have Shuttleworth present an elitist, Microsoftish I-don't-care-what-the-user-wants attitude about the entire thing **irritates me to no end**.

---

### Post by derekeverett on 2010-03-22
> **jacobmh said:**
> I did, I installed emerald. My point is that this changes one of the reasons that Ubuntu became so widely used- that it attracts Windows users to free, usable and familiar-feeling Linux software. I am a Computer Science student that regularly uses bash and tcsh to scoot myself around, but I still use the GUI out of familiarity, and having to mess around with it because some dipstick moved stuff, then have Shuttleworth present an elitist, Microsoftish I-don't-care-what-the-user-wants attitude about the entire thing **irritates me to no end**.

Seems like you are asking Shuttleworth to be less "Microsoftish" by putting the buttons back in a "Microsoftish" position...

I agree that most people change all the defaults anyway so who really cares? 

Windows users aren't going to stay with Ubuntu or not stay with it based on button placement. New users are struggling with app incompatibility and file system issues etc. They aren't going to survive that process and then leave because the default button placement wasn't the same as Windows.

---

### Post by uRock on 2010-03-22
> **thatguruguy said:**
> OSX, which is the only "major OS" (at least for desktops) other than Windows, places the controls on the left.

In your opinion.

---

### Post by thatguruguy on 2010-03-22
No, OSX really DOES place the buttons on the left. That's a fact.

---

### Post by aysiu on 2010-03-22
> **thatguruguy said:**
> OSX, which is the only "major OS" (at least for desktops) other than Windows, places the controls on the left. But OS X didn't decide to randomly switch them to the right in Snow Leopard. OS X also has the close button on the outside of the window (far left). OS X has a universal toolbar that's separate from each window inside the application. OS X doesn't quit the application when you close the last window in that application (even by accident).

---

### Post by tad1073 on 2010-03-22
[http://gnome-look.org/content/show.php/Pint+-+Ambiance+%26+Radiance?content=121143](http://gnome-look.org/content/show.php/Pint+-+Ambiance+%26+Radiance?content=121143)

Is what I use

---

### Post by Jay Car on 2010-03-22
> **asmoore82 said:**
>  "...I agree with the design decision, but I have chosen to split my buttons up as attached."

I like the way you've arranged the buttons. What's interesting to me, after observing some of the reactions to "The Moved Button Issue" (including my own), is that prior to this, it never occurred to me to move those buttons.  I actually never thought about them at all.

Some might find the moved buttons to be as annoying as I did. But the cool part is that I not only learned how to put them back, but it actually made me think about where I'd prefer them to be, and why.  

Maybe it's good to shake things up sometimes and make people pay attention, rather than just take stuff for granted and assume things will always stay the same.

Hmmm, I'm not sure I've articulated it very well, but I did find the process (from annoyance, to whining - yes, I whined - to accepting that change isn't a bad thing, to exploring ways of changing things on my own) to be fascinating. 

I may not have a voice in how Ubuntu is designed, but MarkS also has no voice in how I change things on my own computers...and that's the real beauty of it.

:)

---

### Post by aysiu on 2010-03-22
> **pastalavista said:**
> Nobody I know uses the default setup anyway. Nevertheless, [defaults matter](http://www.psychocats.net/ubuntucat/defaultsmatter/)

No one uses the default for *everything*, but also no one avoids the default for *everything*. The fewer things you can have as default that people won't change, the better... otherwise, you should rethink your defaults.

---

### Post by k3lt01 on 2010-03-22
> **thatguruguy said:**
> No, OSX really DOES place the buttons on the left. That's a fact.Methinks you missed iRocks point.

---

### Post by uRock on 2010-03-22
> **thatguruguy said:**
> No, OSX really DOES place the buttons on the left. That's a fact.

I was commenting on the "major" part. I know Mac is n the left. Gotta give credit to HP and the other OSes that run our Banks and keep our money safe.

And in _my_ heart Ubuntu is now a major OS. I have too many friends running it nowadays.

---

### Post by tad1073 on 2010-03-22
> **jacobmh said:**
> This came from this [message]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633/comments/167") where Mark relates to us why users don't get a say when it comes to the blatant, inappropriate, and functionally useless Mac fanboyism inherent in moving the buttons in Lucid Lynx to the upper left of the window. 

For those of you who have not yet upgraded, I think you will find this to be a bigger deal than you realize. For those of us who grew up on Windows (and considering it still has majority OS market share, that would be most of us) it presents a counterintuitive change that reduces productivity by increasing the time it takes to realize that the X button is **not** where it has been for our entire lives.

Mark's point about the Ubuntu Meritocracy is only relevant when their decisions actually have merit. Otherwise "Ubuntu Meritocracy" becomes an oxymoron.

Shuttleworth: For the love of Linus, change the buttons back.

alt+F2>gconf-editor>apps>metacity>general>button_layout>menu:maximize,minimize,close

---

### Post by k3lt01 on 2010-03-22
> **asmoore82 said:**
> A little over the top there, just put *your* buttons where *you* want them.

I agree with the design decision, but I have chosen to split my buttons up as attached.I like that, well done, I may have a play and see.

---

### Post by aysiu on 2010-03-22
> **tad1073 said:**
> alt+F2>gconf-editor>apps>metacity>general>button_layout>menu:maximize,minimize,closeI have a better idea: keep the buttons where they were by default. Let those who want it on the left side (with the close button on the inside) can use *gconf-editor* to move it over there.

---

### Post by uRock on 2010-03-22
> **aysiu said:**
> Nevertheless, [defaults matter](http://www.psychocats.net/ubuntucat/defaultsmatter/)

No one uses the default for *everything*, but also no one avoids the default for *everything*. The fewer things you can have as default that people won't change, the better... otherwise, you should rethink your defaults.

That is a good philosophy. I hope Mark has a really cool idea for the right side that will leave people scratching their heads, saying, "Why didn't Gates think of this first, this is amazing?"

---

### Post by tad1073 on 2010-03-22
> **bug67 said:**
> With Linux, there's always a solution:

```
gconftool-2 --set /apps/metacity/general/button_layout --type string [SIZE=3][COLOR=Red]**menu:minimize,maximize,close**[/COLOR][/SIZE]
```

should be...
```
*[FONT=Arial][SIZE=3][COLOR=Red]**menu:maximize,minimize,close**[/COLOR][/SIZE][/FONT]*
```

because of the way the buttons were designed

---

### Post by uRock on 2010-03-22
> **tad1073 said:**
> should be...
```
*[FONT=Arial][SIZE=3][COLOR=Red]**menu:maximize,minimize,close**[/COLOR][/SIZE][/FONT] 			*
```

Nah, if we're gonna imitate Windows, we gotta do it right.

---

### Post by JamezQ on 2010-03-22
> alt+F2>gconf-editor>apps>metacity>general>button_layout>menu:ma ximize,minimize,close

This is not how it should be, changing it should be like this.

System > Appearance > Theme > Customize > Window Border(Which should have the option to change the button placement.)

---

### Post by thatguruguy on 2010-03-22
> **k3lt01 said:**
> Methinks you missed iRocks point.

No I didn't.

> **iRock said:**
> I was commenting on the "major" part. I know Mac is n the left. Gotta give credit to HP and the other OSes that run our Banks and keep our money safe.

And in _my_ heart Ubuntu is now a major OS. I have too many friends running it nowadays.

I use Ubuntu on my computer. My kids use Ubuntu on their computer. My sister (and her kids) use Ubuntu on her computer. My wife uses Ubuntu on her computer.  However, Ubuntu isn't really an OS; it's a distribution of Linux, and Linux only has a market share of about 1% on the desktop. The fact that you, I, and other people we know use Ubuntu or some other distribution of Linux does not, in and of itself, make Linux a "major OS".

Furthermore, I don't think that the specialized workstation OS created by HP for banking applications can be considered a "desktop OS"; to the extent that it IS a "desktop OS", I'm pretty sure it's used on less than 1% of all the desktops in the world.

---

### Post by tad1073 on 2010-03-22
> **jamezq said:**
> this is not how it should be, changing it should be like this.

System > appearance > theme > customize > window border(which should have the option to change the button placement.)
+1

---

### Post by X1R1 on 2010-03-22
I like the new design, its about time ubuntu did something to the design because actual design isnt very good IMO, wayy better the new one.

I like the buttons on the new position better also. And i dont think that the buttons being in a different position will make a MS windows user switch back just because of this, because you are LEARNING a new OS, like learning a new language it takes time and dedication.

Firefox became so succesfull because it is DIFFERENT, introduced tabbed browsing and extensions to give users power. Ubuntu is going the same way, being different, of course, different doesnt mean always better, but new/different stuff is what drag me down to try ubuntu in the first place.

just my 2c here

---

### Post by pihbar on 2010-03-22
> **tad1073 said:**
> should be...
```
*[FONT=Arial][SIZE=3][COLOR=Red]**menu:maximize,minimize,close**[/COLOR][/SIZE][/FONT]*
```

because of the way the buttons were designed

What, why?

---

### Post by tad1073 on 2010-03-22
> **iRock said:**
> Nah, if we're gonna imitate Windows, we gotta do it right.

lol

---

### Post by splicerr on 2010-03-22
> **jacobmh said:**
> the blatant, inappropriate, and functionally useless Mac fanboyism inherent in moving the buttons in Lucid Lynx to the upper left of the window. 
...  it presents a counterintuitive change that reduces productivity by increasing the time it takes to realize that the X button is **not** where it has been for our entire lives.


I disagree, It took me 2 days to get fully used to. Really you are making a big deal out of nothing. Furthermore I really like the new theming, this is without a doubt the slickest looking Ubuntu version ever.

:popcorn:

---

### Post by praveenmarkandu on 2010-03-22
i know most of you dont really care that the buttons are switched around. the reason why you dont care is because it is so trivial to switch them back. i think you guys are missing the point, when canonical do make a change and it is not easily undone everyone of you will be singing a different tune

and what i want to see is how they came about the decision to move the buttons around in the first place. every design choice should be a result of a proper case study and critical analysis on what works and what doesnt and how to fix the problem. the weird thing is, there isnt any problem to begin with!

> This is a difference between Ubuntu and several other community distributions. It may feel less democratic, but it's more meritocratic, and most importantly it means (a) we should have the best people making any given decision, and (b) it's worth investing your time to become the best person to make certain decisions, because you should have that competence recognised and rewarded with the freedom to make hard decisions and not get second-guessed all the time. 
*--Mark Shuttleworth*

i find it hard to believe that this design "improvement" wasnt passed by shuttleworth and approved by him. so if ubuntu is meritocratic, what does shuttleworth know about design?

---

### Post by uRock on 2010-03-22
It doesn't need to be undone. Mine are still on the left and they work perfectly. Ubuntu isn't Windows.

---

### Post by tad1073 on 2010-03-22
> **thatguruguy said:**
> No I didn't.



I use Ubuntu on my computer. My kids use Ubuntu on their computer. My sister (and her kids) use Ubuntu on her computer. My wife uses Ubuntu on her computer.  However, Ubuntu isn't really an OS; it's a distribution of Linux, and Linux only has a market share of about 1% on the desktop. The fact that you, I, and other people we know use Ubuntu or some other distribution of Linux does not, in and of itself, make Linux a "major OS".

Furthermore, I don't think that the specialized workstation OS created by HP for banking applications can be considered a "desktop OS"; to the extent that it IS a "desktop OS", I'm pretty sure it's used on less than 1% of all the desktops in the world.

Any one with any sense would use RHEL. IMO, RHEL is more secure than any Windows server on the market.

---

### Post by thatguruguy on 2010-03-22
Even in free software there are market forces.

Kvetching on a forum or a blog doesn't really change anything. If the button position is really a deal-breaker, people will stay away from lucid in droves. Polls don't matter; voting with your feet does.  If Ubuntu loses market share because of the change in the button position, Canonical will have to re-think the issue.  Otherwise, there is no incentive to change things back to the more Windows-like layout.

---

### Post by ronacc on 2010-03-22
@ X1R1 Opera had tabs years before firefox  .

Note to shuttleworth . I don't give a hoot if you own canonical flaunting your arrogance in our faces does not win friends and in fact influences people unfavorably.

---

### Post by uRock on 2010-03-22
> **thatguruguy said:**
> No I didn't.



I use Ubuntu on my computer. My kids use Ubuntu on their computer. My sister (and her kids) use Ubuntu on her computer. My wife uses Ubuntu on her computer.  However, Ubuntu isn't really an OS; it's a distribution of Linux, and Linux only has a market share of about 1% on the desktop. The fact that you, I, and other people we know use Ubuntu or some other distribution of Linux does not, in and of itself, make Linux a "major OS".

Furthermore, I don't think that the specialized workstation OS created by HP for banking applications can be considered a "desktop OS"; to the extent that it IS a "desktop OS", I'm pretty sure it's used on less than 1% of all the desktops in the world.

You forget about all of the phones running Linux that probably out numbers the number of devices running Windows.

---

### Post by J_Stanton on 2010-03-22
> **tad1073 said:**
> should be...
```
*[FONT=Arial][SIZE=3][COLOR=Red]**menu:maximize,minimize,close**[/COLOR][/SIZE][/FONT]*
```

because of the way the buttons were designed

not if you want to keep it the way ubuntu has always been.

---

### Post by deanjm1963 on 2010-03-22
I actually like the new position of the buttons, at first it was strange, but after 24 hours of usage it's no different to their "original" position. I think it's no different to buying a new keyboard, it takes a day or two to get used to it ...

---

### Post by thatguruguy on 2010-03-22
> **iRock said:**
> You forget about all of the phones running Linux that probably out numbers the number of devices running Windows.

No I didn't. Phones aren't desktops.

---

### Post by uRock on 2010-03-22
> **thatguruguy said:**
> No I didn't. Phones aren't desktops.

Numbers are still numbers. Those MS numbers count only the installs sold not the installs that have been written over with Linux. I consider an OS to be major when they are not easily broken or hacked, which just dropped your #1 to the bottom.

---

### Post by tad1073 on 2010-03-22
[SIZE=2][COLOR=Red]**menu:maximize,minimize,close**
[IMG]http://ubuntuforums.org/picture.php?pictureid=5822&albumid=1710&dl=1269312459&thumb=1[/IMG]

[B]

menu:minimize,maximize,close
[IMG]http://ubuntuforums.org/picture.php?pictureid=5823&albumid=1710&dl=1269312459&thumb=1[/IMG]
[/B][/COLOR][/SIZE]

---

### Post by praveenmarkandu on 2010-03-22
> **thatguruguy said:**
> Otherwise, there is no incentive to change things back to the more Windows-like layout.

what was the incentive of changing the buttons in the first place. everyone was complaining about the themes and colour schemes of ubuntu, not the button placement. all i want is proof that they had a reason to change it in the first place.

---

### Post by k3lt01 on 2010-03-22
> **thatguruguy said:**
> No I didn't.

So why did we have this little conversation then?
> **thatguruguy said:**
> OSX, which is the only "major OS" (at least for desktops) other than Windows, places the controls on the left.
> **iRock said:**
> In your opinion.
> **thatguruguy said:**
> No, OSX really DOES place the buttons on the left. That's a fact.iRock was talking about the "major OS" part not the button placement.

Lalalalala

---

### Post by aysiu on 2010-03-22
> **iRock said:**
> It doesn't need to be undone. Mine are still on the left and they work perfectly. Ubuntu isn't Windows. [Linux can be Windows sometimes, can’t it?](http://www.psychocats.net/ubuntucat/linux-can-be-windows-sometimes-cant-it/)

---

### Post by J_Stanton on 2010-03-22
> **ronacc said:**
> @ X1R1 Opera had tabs years before firefox  .

Note to shuttleworth . I don't give a hoot if you own canonical flaunting your arrogance in our faces does not win friends and in fact influences people unfavorably.

feel free to use another distro. i seriously doubt he will read your hissy fit.

about the change, i really don't care about the buttons. i have way more important things in life to worry about.

---

### Post by emarkay on 2010-03-22
Mods -please merge or lock this post.

There are too many more important issues that button locations; especially when it is so easy to change them to their* **correct** *place...   :)

---

### Post by ronacc on 2010-03-22
why should we object to looking like OSX and not object to looking like Windows ?

---

### Post by emarkay on 2010-03-22
Oh no, not  another one!

Please merge or lock this one too.

Folks, there are too many other issues to be wasting time on this; fixing it is easy, and no one knows why it was done anyway.

---

### Post by uRock on 2010-03-22
> **aysiu said:**
> [Linux can be Windows sometimes, can’t it?]("http://www.psychocats.net/ubuntucat/linux-can-be-windows-sometimes-cant-it/")

But that takes the fun out of it.

---

### Post by jrusso2 on 2010-03-22
I think this whole thing about the dumb buttons is a waste.  In a week you will be used to it.  I got used to them on the mac pretty fast.

---

### Post by X1R1 on 2010-03-22
> **ronacc said:**
> @ X1R1 Opera had tabs years before firefox  .


True, forgot that, But opera was a PAID browser years ago, and still closed source, firefox isnt any of the :D

---

### Post by k3lt01 on 2010-03-22
Isn't it time these threads got put in "Recurring Discussions"?

---

### Post by uRock on 2010-03-22
> **emarkay said:**
> Mods -please merge or lock this post.

There are too many more important issues that button locations; especially when it is so easy to change them to their* **correct** *place...   :)

That's the thing, we don't have to change them to get them to the correct place. They really look nice over to the left. The designers even colored them red to make them hard to miss.

---

### Post by uRock on 2010-03-22
> **k3lt01 said:**
> Isn't it time these threads got put in "Recurring Discussions"?

No doubt. I wish people would search for threads that are already open on the subject. 

I feel like a broken record here.

---

### Post by k3lt01 on 2010-03-22
> **iRock said:**
> No doubt. I wish people would search for threads that are already open on the subject. 

I feel like a broken record here.If they can't find a button how will they find a search function?

---

### Post by thatguruguy on 2010-03-22
> **k3lt01 said:**
> So why did we have this little conversation then?


umm... because it was funnier to pretend I missed his point? I realize it takes a certain level of intelligence to appreciate humor.  I'm sorry if, by being funny, I have somehow discriminated against you.

---

### Post by ronacc on 2010-03-22
seeing eye penguin ?

---

### Post by bug67 on 2010-03-22
> **tad1073 said:**
> should be...
```
*[FONT=Arial][SIZE=3][COLOR=Red]**menu:maximize,minimize,close**[/COLOR][/SIZE][/FONT]*
```

because of the way the buttons were designed

Hey, looky there, you can put however the frak you want!  :P

---

### Post by tad1073 on 2010-03-22
@bug67

> **tad1073 said:**
> [SIZE=2][COLOR=Red]**menu:maximize,minimize,close**
[IMG]http://ubuntuforums.org/picture.php?pictureid=5822&albumid=1710&dl=1269312459&thumb=1[/IMG]

[B]

menu:minimize,maximize,close
[IMG]http://ubuntuforums.org/picture.php?pictureid=5823&albumid=1710&dl=1269312459&thumb=1[/IMG]
[/B][/COLOR][/SIZE]

IMO, the top image w/its button placement looks better, but, to keep with windows standard button placement the bottom image is correct.

---

### Post by ElSlunko on 2010-03-22
I like the new position.

---

### Post by k3lt01 on 2010-03-22
Lolololololol

---

### Post by k3lt01 on 2010-03-22
> **thatguruguy said:**
> umm... because it was funnier to pretend I missed his point? I realize it takes a certain level of intelligence to appreciate humor.  I'm sorry if, by being funny, I have somehow discriminated against you.You need to move to Bollywood.

Say what you mean, try it sometime.

---

### Post by 23meg on 2010-03-22
Recurring threads on button placement merged. 

Note that posting here is not going to have an effect on the decision. If you want to affect it, post in a polite manner with data on how the change affected you to [the bug report]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633/").

---

### Post by ElSlunko on 2010-03-22
> **tad1073 said:**
> [SIZE=2][COLOR=Red]**menu:maximize,minimize,close**
[IMG]http://ubuntuforums.org/picture.php?pictureid=5822&albumid=1710&dl=1269312459&thumb=1[/IMG]

[B]

menu:minimize,maximize,close
[IMG]http://ubuntuforums.org/picture.php?pictureid=5823&albumid=1710&dl=1269312459&thumb=1[/IMG]
[/B][/COLOR][/SIZE]
Left or right, they sure do look sexy. It must be unhealthy to find software sexy.

---

### Post by chargersfan420 on 2010-03-22
I have a quick question about this... I seem to be missing the point about where this change is being made in the code.  Is this change being made to a default theme?  To metacity?  Or an even lower level?  As an Emerald user, will I be affected?

---

### Post by lidex on 2010-03-22
> **tad1073 said:**
> @bug67



IMO, the top image w/its button placement looks better, but, to keep with [COLOR="Red"]windows standard button placement[/COLOR] the bottom image is ***correct***.

Whaaa? The Windows default is the "standard"? Ubuntu is "correct" only if it adheres to that standard. No, now they have to be on the left :rolleyes:

---

### Post by deanjm1963 on 2010-03-22
My second 2 cents worth - buttons are like hair colour - if you don't like it change it - L'Oreal, Clairol et al are just aching for your business - change your distro if you prefer "the windows standard" ... I'm so over the negativity regarding the placement of the buttons - I congratulate Mark Shuttleworth on doing something different and making Ubuntu stand out from the crowd - change is good, change is progress. Enough said.

---

### Post by bug67 on 2010-03-23
I do like the simplicity and look of the design what/where/which ever place/position/order they are placed.  I also greatly appreciate the fact that I have the power to put them where ever in whatever order I want.  I just can't wait to see what happens when Mint throws their spin on Lucid.  I'm already seeing a lot of similarities.

---

### Post by cariboo on 2010-03-23
I like the new button placement, I've been waiting 12 years for a default installation that looks different from Windows, and it's finally coming. I'm really looking forward to Lucid+1, I've already got a couple of blank partitions waiting for it. :)

---

### Post by uRock on 2010-03-23
> **23meg said:**
> Recurring threads on button placement merged. 

Note that posting here is not going to have an effect on the decision. If you want to affect it, post in a polite manner with data on how the change affected you to [the bug report]("https://bugs.launchpad.net/ubuntu/+source/light-themes/+bug/532633/").

Thanks for the link. I think there are a lot of good comments there and I hope if others post there, they think before posting so as to not look like they aren't just being temperamental.

> **cariboo907 said:**
> I like the new button placement, I've been waiting 12 years for a default installation that looks different from Windows, and it's finally coming. I'm really looking forward to Lucid+1, I've already got a couple of blank partitions waiting for it. :)

+1 I am really wanting to write over Karmic on my production machine, but with school going, I can't afford a breakage in the middle of a project.

---

### Post by dcstar on 2010-03-23
Does anyone else see the irony of this change - and the whole reasoning for it - in a release called "Lucid"?

Has Ubuntu now adopted the philosophy of "Newspeak"?

---

### Post by dcstar on 2010-03-23
> **cariboo907 said:**
> I like the new button placement, I've been waiting 12 years for a default installation that looks different from Windows, and it's finally coming. I'm really looking forward to Lucid+1, I've already got a couple of blank partitions waiting for it. :)

Anyone who** wanted** to change the button layouts could have done it ages ago - I am looking at the Gconf key right now in my 9.04 system.

Pity it is being **forced** on all new 10.04 users, with only those currently able to use the Configuration Editor or the command line with the option to change it.

---

### Post by uRock on 2010-03-23
> **dcstar said:**
> Anyone who** wanted** to change the button layouts could have done it ages ago - I am looking at the Gconf key right now in my 9.04 system.

Pity it is being **forced** on all new 10.04 users, with only those currently able to use the Configuration Editor or the command line with the option to change it.

It isn't the end of the world. It's a couple of buttons. If they decide after Beta1 to keep the buttons on the left for the Light themes, a simple theme change will put them back on the right. Also if all goes well, the design team will create a way to easily change the buttons in the Appearance applet.

---

### Post by JavaNut13 on 2010-03-23
If they do move them *please* let there be an option to move them back!!!!! Otherwise I'll stick with 9.10.

The majority of people use Windows, so having the buttons on the right makes sense (To them.... and me)
--
***JavaNut***

---

### Post by dcstar on 2010-03-23
> **J_Stanton said:**
> 
........
about the change, i really don't care about the buttons. i have way more important things in life to worry about.

Lots of other people also have "way more important things in life to worry about", and they probably won't want to learn a whole new way of doing things if they happen to look for an alternative to the way they have doing things ever since they started using Windows.

This issue is the single most disappointing thing I have experienced with Ubuntu since I started using it in late 2004.

---

### Post by dcstar on 2010-03-23
> **iRock said:**
> It isn't the end of the world. It's a couple of buttons. If they decide after Beta1 to keep the buttons on the left for the Light themes, a simple theme change will put them back on the right. Also if all goes well, the design team will create a way to easily change the buttons in the Appearance applet.

Which - even "**if**" these things happen - should have been done before the change.

The mindset that has firstly initiated this change and now is bitterly fighting the uproar over it may well be the "*end of the world*" for Ubuntu, at least if it is ever expressed in this way again.

It is beyond any sort of technical argument now as to which way is better or how hard/easy it is to change, it now comes to the whole reason for a distro like Ubuntu's existence - does it exist so developers can force changes essentially because **they** like them?, because I want to know when this changed from creating a distro that allowed normal people to use Linux in the easiest possible way.

I can see big signs on freeway exits that say "Wrong Way - Go Back" for those that can't get driving right, do Ubuntu developers see the same things as they hurtle against the flow of traffic because "this is the way **we** like it"?

---

### Post by ElSlunko on 2010-03-23
> **dcstar said:**
> 
This issue is the single most disappointing thing I have experienced with Ubuntu since I started using it in late 2004.

You're very lucky then :).

---

### Post by uRock on 2010-03-23
> **dcstar said:**
> Which - even "**if**" these things happen - should have been done before the change.

The mindset that has firstly initiated this change and now is bitterly fighting the uproar over it may well be the "*end of the world*" for Ubuntu, at least if it is ever expressed in this way again.

It is beyond any sort of technical argument now as to which way is better or how hard/easy it is to change, it now comes to the whole reason for a distro like Ubuntu's existence - does it exist so developers can force changes essentially because **they** like them?, because I want to know when this changed from creating a distro that allowed normal people to use Linux in the easiest possible way.

I can see big signs on freeway exits that say "Wrong Way - Go Back" for those that can't get driving right, do Ubuntu developers see the same things as they hurtle against the flow of traffic because "this is the way **we** like it"?

Maybe the plan they have for the space on the right is a good plan. I am anxious to see it.

---

### Post by ElSlunko on 2010-03-23
> **dcstar said:**
> Which - even "**if**" these things happen - should have been done before the change.

The mindset that has firstly initiated this change and now is bitterly fighting the uproar over it may well be the "*end of the world*" for Ubuntu, at least if it is ever expressed in this way again.

It is beyond any sort of technical argument now as to which way is better or how hard/easy it is to change, it now comes to the whole reason for a distro like Ubuntu's existence - does it exist so developers can force changes essentially because **they** like them?, because I want to know when this changed from creating a distro that allowed normal people to use Linux in the easiest possible way.

I can see big signs on freeway exits that say "Wrong Way - Go Back" for those that can't get driving right, do Ubuntu developers see the same things as they hurtle against the flow of traffic because "this is the way **we** like it"?

It's the way I like them too (to the left). Originally I voted right in that closed pole because I didn't really have time to test it & just went with my first instinct. I can only imagine this will be most people's first reactions as well and whether or not this will deter new users is something that is quite difficult to estimate. It may even attract instead of deter.

---

### Post by k3lt01 on 2010-03-23
Well, I just changed mine back to the left, why? because I can. I do however have a different order, mine are now a mirror image of the right. Close, Maximise, Minimise.

I'll test it for week or so and see how I go.

---

### Post by mcooke1 on 2010-03-23
> **dcstar said:**
> Anyone who** wanted** to change the button layouts could have done it ages ago - I am looking at the Gconf key right now in my 9.04 system.

Pity it is being **forced** on all new 10.04 users, with only those currently able to use the Configuration Editor or the command line with the option to change it.

Ubuntu Tweak also can be used.

---

### Post by kansasnoob on 2010-03-23
I know I have a sick sense of humor but I was looking to see if the Gnome version of PCLinuxOS 2010 Beta2 was available yet and almost couldn't stop laughing when I saw this:

> 
PCLinuxOS
Our window buttons are right

Check it out (upper left hand corner):

[http://pclinuxos.com/](http://pclinuxos.com/)

Don't get me wrong. Ubuntu is still, by far, my much preferred OS but I still thought it was funny.

---

### Post by sonicb00m on 2010-03-23
I can't stand the buttons being left. It's not a natural position for me to have the mouse resting at either. I always have the cursor nearer the right hand side (maybe because i am right handed?) but that's also to do with the fact the scroll bar is there too.

---

### Post by mcooke1 on 2010-03-23
Using Kubuntu 10.04 Beta 1 at the moment all buttons are on the right. (an oversight maybe)

---

### Post by octesian on 2010-03-23
> **tad1073 said:**
> [SIZE=2][COLOR=Red]**menu:maximize,minimize,close**
[IMG]http://ubuntuforums.org/picture.php?pictureid=5822&albumid=1710&dl=1269312459&thumb=1[/IMG]

[B]

menu:minimize,maximize,close
[IMG]http://ubuntuforums.org/picture.php?pictureid=5823&albumid=1710&dl=1269312459&thumb=1[/IMG]
[/B][/COLOR][/SIZE]


I fixed this with in post 16.  Its quick n' sloppy but it looks a lot better.
[http://ubuntuforums.org/showpost.php?p=8928097&postcount=16]("http://ubuntuforums.org/showpost.php?p=8928097&postcount=16")

> **nubalci said:**
> Dear octesian: by any chance do you have a similar modification for "Radiance" theme?
Sorry, I haven't gotten around to it.  Its not too hard to do it yourself in GIMP if you want to give it a shot :)

---

### Post by Madspyman on 2010-03-23
> **kansasnoob said:**
> I know I have a sick sense of humor but I was looking to see if the Gnome version of PCLinuxOS 2010 Beta2 was available yet and almost couldn't stop laughing when I saw this:

> PCLinuxOS
Our window buttons are right

Check it out (upper left hand corner):

[http://pclinuxos.com/](http://pclinuxos.com/)

Don't get me wrong. Ubuntu is still, by far, my much preferred OS but I still thought it was funny.

Ouch, even PCLinuxOS is taking shots at Ubuntu. #-o :-k Double Facepalm.

---

### Post by kansasnoob on 2010-03-23
> **Madspyman said:**
> Ouch, even PCLinuxOS is taking shots at Ubuntu. #-o :-k Double Facepalm.

Yeah, and even DistroWatch. And they don't finish with, "it's easily reverted", or something like that but rather:

> for those who just cannot accept the button revolution in Ubuntu, well, you are on the right web site to find an alternative

[http://distrowatch.com/weekly.php?issue=20100322#news](http://distrowatch.com/weekly.php?issue=20100322#news)

That one didn't make me laugh. Their link just takes you to their "top ten" list.

---

### Post by Madspyman on 2010-03-23
> **kansasnoob said:**
> Yeah, and even DistroWatch. And they don't finish with, "it's easily reverted", or something like that but rather:



[http://distrowatch.com/weekly.php?issue=20100322#news](http://distrowatch.com/weekly.php?issue=20100322#news)

That one didn't make me laugh. Their link just takes you to their "top ten" list.

Did you read the Crunchbang part after it?

>  "Unlike the Ubuntu project, Debian does not have a commercial sponsor with any commercial interests. This was never an issue for myself, until recently when Canonical seems to have become less of a sponsor and more of a governing party; I know this is debatable, but I believe that some of their recent decisions might not necessarily have been made with the best interest of their users/community at heart. From a less political perspective, the Ubuntu project is geared towards producing a polished end-user system. The Ubuntu developers make changes to Debian packages to achieve this goal. These changes often cause problems for derivative projects such CrunchBang. Therefore, the obvious thing to do to negate these problems was to make the switch to Debian." - Philip Newborough, founder of Crunchbang Linux

---

### Post by kansasnoob on 2010-03-23
> **mcooke1 said:**
> Using Kubuntu 10.04 Beta 1 at the moment all buttons are on the right. (an oversight maybe)

I tried the Xubuntu Beta1 and the same is true there, so far.

I've built over 30 computers for seniors that were mostly still stuck on Win98 and ME, and they've always been pleased with Ubuntu after I apply a few tweaks. But not a single one of them likes the new button position or notify-osd.

It's just a matter of usability for people that have no desire to learn something "new", they just want things simple. Thus I'm considering Xfce as a viable alternative.

---

### Post by kansasnoob on 2010-03-23
> **Madspyman said:**
> Did you read the Crunchbang part after it?

Let's not get too far off-track. I don't want to get this thread closed.

Maybe more of a water cooler type discussion:

[http://ubuntuforums.org/forumdisplay.php?f=175](http://ubuntuforums.org/forumdisplay.php?f=175)

---

### Post by konqueror7 on 2010-03-23
its a good argument that most windows changing users will have difficulties, but migrating to a different system, change is is expected. having a mac user using the 10.04 will have no problem, but then going to windows, will present the same problem.

personally, i too don't like my buttons on the left, its just that most of us are already too comfortable with being on the right side, hopefully they will really include the option to change it...

---

### Post by ronacc on 2010-03-23
this is all easily solved , delete the buttons and the mouse too , the keyboard is the only RIGHT way to use a computer, mice are only for games .

---

### Post by 3Miro on 2010-03-23
There is another solution to the button problem: use KDE. That is what I will probably do, I have been using the kubuntu beta and it works great. I should try Ubuntu, just to see the buttons and probably rant about it.

---

### Post by lidex on 2010-03-23
> **sonicb00m said:**
> I can't stand the buttons being left. It's not a natural position for me to have the mouse resting at either. I always have the cursor nearer the right hand side (maybe because i am right handed?) but that's also to do with the fact the scroll bar is there too.

It's really just what you're used to. Maybe the scroll bar should go left as well. For me personally, I would prefer the highly used items be left and center as it seems I only go right because the buttons and scroll bar are there. But I hardly use the scroll bar now, instead opting for the mousewheel. In my Mozilla apps my main toolbar buttons are in the middle - even the menu bar.

---

### Post by lidex on 2010-03-23
> **cariboo907 said:**
> i like the new button placement, i've been waiting 12 years for a default installation that looks different from windows, and it's finally coming. I'm really looking forward to lucid+1, i've already got a couple of blank partitions waiting for it. :)

+1

---

### Post by uRock on 2010-03-23
> **Madspyman said:**
> Did you read the Crunchbang part after it?

That part about changing to Debian made me laugh so hard I almost blew coffee through my nose. Debian and user friendly aren't related. The time it would take for a newb to get an nVidia driver installed, he/she could have ubuntu fully tweaked and buttons where ever their hearts desired.

@3Miro- I gave Kubuntu a try for about 2-3 weeks and it just wasn't my thing. Maybe when they make it to version 5.0 I might give it another go.

Lubuntu is looking great, too, but from reading the launchpad page, they may be making the button change to all 4 versions.

---

### Post by carolinason on 2010-03-23
i love putting my mouse over something that got moved to the other side of the window, NOT!! this is extremely annoying. 

if i wanted to get this annoyed i would have bought a mac!

---

### Post by magneze on 2010-03-23
> **aysiu said:**
> But OS X didn't decide to randomly switch them to the right in Snow Leopard. OS X also has the close button on the outside of the window (far left). OS X has a universal toolbar that's separate from each window inside the application. OS X doesn't quit the application when you close the last window in that application (even by accident).:) I admire your persistence. You keep making these great points on the threads and then repeating them as more people come up with a "brainwave" that's been mentioned dozens of times before. Kudos to you.

---

### Post by kevin2849 on 2010-03-23
I have used ubuntu since warty, as well as several other distros and I always experiment with my themes. I really like the Lucid themes and other than some font changes and my favorite background will stick with it.

I have always moved my window buttons to the left in both gnome and kde, but in a different order than Lucid. I am leaving them as installed for now and not having any problems so far.

---

### Post by uRock on 2010-03-23
It is nice to see someone that has been with Ubuntu for a long that isn't throwing a tantrum. I like the thought of Ubuntu boldly going where no other Linux has gone. I think Mark is keeping his new feature under raps so that nobody can beat him to it and claim to be the first to do what he has planned. I just hope it is something worth the trouble.

---

### Post by reiki on 2010-03-23
> **carolinason said:**
> i love putting my mouse over something that got moved to the other side of the window, NOT!! this is extremely annoying. 

That's called "motor memory". You can be retrained. :)

Seriously, it's just your training that has you going to the old location. If you USE the new location for a while you'll probably learn to hate them on the right :)

---

### Post by aysiu on 2010-03-23
> **reiki said:**
> That's called "motor memory". You can be retrained. :)

Seriously, it's just your training that has you going to the old location. If you USE the new location for a while you'll probably learn to hate them on the right :) Retraining'd be great if there was an actual good reason for it.

---

### Post by uRock on 2010-03-23
> **aysiu said:**
> Retraining'd be great if there was an actual good reason for it.

What better reason than doing it for good mental health.

---

### Post by djchandler on 2010-03-23
> **reiki said:**
> That's called "motor memory". You can be retrained. :)

Seriously, it's just your training that has you going to the old location. If you USE the new location for a while you'll probably learn to hate them on the right :)

Now you are joking that change just for the very sake of change is a good idea. For those of us who've had injury or illness that have forced such re-training, this could even be traumatic. You may think that's far-fetched until you have actually had to do it. Trying to make it humorous is not funny.

If you really need to, you can become left-handed if you were right-handed before and for some reason you lose the use of your right hand, or vice-versa. The least traumatic manner would be due to stroke although that's debatable. If you have a stroke on the right side of your brain, all bets may be off off and retraining is a lesson in grief for those left behind. Right?

And if you lose the use of both hands you can use your feet.

If you become a quadraplegic...

You get the idea.

I'm right-handed, and have only recently regained most of the use of it  back. I learned to do a lot of things left-handed that otherwise  wouldn't get done over a period of about 10 years, but as soon as the right hand became available again after a couple of surgeries and recovering with physical therapy, it was back to doing everything I can on the right. Sometimes necessity makes you change your thinking or skill set. It's great that we humans are bilaterally symmetrical. When it's only for aesthetics and it makes it harder to get work done, change whatever it is back. In this instance it's easy.

As for the aesthetic factor, everything jammed up on the left side just looks and feels unbalanced to me. All of the application drop-down menus are already on the left. The buttons being placed on the right when all else is on the left provides functionality from either upper corner of the window. What's wrong with that, especially when it's just a huge bare space? Restore the "menu" button on the left and you have the best of both.

Open gconf-editor. Go to apps>metacity>general>button_layout. Move the colon where it needs to be for your comfort.

Current Lucid Default > maximize,minimize,close:

How I like it > menu:minimize,maximize,close

This is incredibly simple. Why we are making a huge deal out of this is beyond my comprehension. Gnome (and Compiz) is built to be tweaked.

---

### Post by 23meg on 2010-03-23
> **djchandler said:**
> 
This is incredibly simple. Why we are making a huge deal out of this is beyond my comprehension. Gnome (and Compiz) is built to be tweaked.

In the final release, it's hopefully going to be even more incredibly simple: Go to System > Preferences > Appearance, pick another theme.

---

### Post by Madspyman on 2010-03-23
> **23meg said:**
> In the final release, it's hopefully going to be even more incredibly simple: Go to System > Preferences > Appearance, pick another theme.

I like this idea, but I fear it's still bound to break something for someone. What about folks who like the current theme and want it with right sided buttons? Or how about the folks who like the left sided buttons but not the theme?

Sure there's is always gconf-editor, but most new users aren't gonna know that. The only way everybody wins if there is a choice when installing Ubuntu, and a user friendly way to change it, included by default.

---

### Post by k3lt01 on 2010-03-23
Removed a post. Need to sleep so I can think before typing something dumb.

---

### Post by 23meg on 2010-03-23
> **Madspyman said:**
> I like this idea, but I fear it's still bound to break something for someone. What about folks who like the current theme and want it with right sided buttons? Or how about the folks who like the left sided buttons but not the theme?

Sure there's is always gconf-editor, but most new users aren't gonna know that. The only way everybody wins if there is a choice when installing Ubuntu, and a user friendly way to change it, included by default.

It *might* be a good compromise to include right-hand button versions of the default themes for that purpose. Failing that, a well-advertised (maybe in the technical overview) PPA. 

It would be a better solution than providing hacky scripts or adding options to tweak a GConf key (that will affect *all themes* again): no extra non-upstream code to maintain, easy to find, not affecting different themes.

---

### Post by davepoth on 2010-03-23
Interestingly Microsoft toyed with sort of going completely the other way with office 2007, and removing the control box in the top left. Here's a developer blog about what happened.

[http://blogs.msdn.com/jensenh/archive/2006/06/08/621757.aspx](http://blogs.msdn.com/jensenh/archive/2006/06/08/621757.aspx)

The upshot of which is that they figured out after polling literally tens of thousands of beta testers that actually they wanted to be able to control their windows from both the top left and top right corners. Which sort of makes sense if you think about it.

---

### Post by 23meg on 2010-03-23
> **aysiu said:**
> But OS X didn't decide to randomly switch them to the right in Snow Leopard. 

However, the switch from OS 9 to OS X did bring about a major change in window control order, at the same time as a general UI overhaul and major architectural changes. The same goes for Windows 3.x to Windows 95. And, as it happens, Ubuntu 9.10 to Ubuntu 10.04, which is a shift of LTS cycles, in which a new branding was introduced.

---

### Post by lidex on 2010-03-23
> **magneze said:**
> :) I admire your persistence. You keep making these great points on the threads and then repeating them as more people come up with a "brainwave" that's been mentioned dozens of times before. Kudos to you.

fawn much? :rolleyes:

---

### Post by Madspyman on 2010-03-23
> **23meg said:**
> However, the switch from OS 9 to OS X did bring about a major change in window control order, at the same time as a general UI overhaul and major architectural changes. The same goes for Windows 3.x to Windows 95. And, as it happens, Ubuntu 9.10 to Ubuntu 10.04, which is a shift of LTS cycles, in which a new branding was introduced.

It seemed to me the decision on the the part of the button order both in Win 95, and OS X (even though it took longer) had to do with putting the buttons all on one side for ease of access. 

Before both had the buttons split between the left and right. Windows moved all theirs on the right side as to not interfere with the file menu, and OS X moved to the left, to be below the global menu.

Ubuntu already had chosen a side that worked. Moving the buttons serves for no apparent gain (that I can see) in functionality. We already had them on one side and things worked fine.

---

### Post by djchandler on 2010-03-23
> **23meg said:**
> ...no extra non-upstream code to maintain, easy to find, not affecting different themes.

The departure from the upstream (Debian) is the real issue here, isn't it?

> In the final release, it's hopefully going to be even more incredibly  simple: Go to System > Preferences > Appearance, pick another  theme.Even if it is easy to change with gconf, I agree with your earlier post. That's the way it should be, make the theme itself alter the way Metacity works. Then provide separate themes that are right buttoned or left buttoned, just like the difference between the way men's and women's shirts are buttoned, even if cut from the same bolt of cloth.

---

### Post by pastalavista on 2010-03-23
This simple change is nothing. I have often moved things (furniture, file solders, the way my shoes go in the closet) for no other reason than I was tired of the status quo. It is a very conservative mind that prefers habitual activities and is offended by "change for the sake of change". Therefore, Ubuntu has allowed us all to make a change for whatever reason we want, whenever we want. Habits are fine if you're of a mind to keep them, but we all need to be shaken up now and then. It's not like we are helpless to do anything about it as we surely would have been if implemented by Microsoft or Apple. 

Like my girlfriend always says, "Notice anything different about me?"
I like that. I know she's still the same old girl underneath.

---

### Post by kansasnoob on 2010-03-23
> **djchandler said:**
> The departure from the upstream (Debian) is the real issue here, isn't it?

Even if it is easy to change with gconf, I agree with your earlier post. That's the way it should be, make the theme itself alter the way Metacity works. Then provide separate themes that are right buttoned or left buttoned, just like the difference between the way men's and women's shirts are buttoned, even if cut from the same bolt of cloth.

Bingo! If I want a certain Gnome them to look like the virgin Gnome theme - it just should!

---

### Post by kansasnoob on 2010-03-23
> **pastalavista said:**
> This simple change is nothing. I have often moved things (furniture, file solders, the way my shoes go in the closet) for no other reason than I was tired of the status quo. It is a very conservative mind that prefers habitual activities and is offended by "change for the sake of change". Therefore, Ubuntu has allowed us all to make a change for whatever reason we want, whenever we want. Habits are fine if you're of a mind to keep them, but we all need to be shaken up now and then. It's not like we are helpless to do anything about it as we surely would have been if implemented by Microsoft or Apple. 

Like my girlfriend always says, "Notice anything different about me?"
I like that. I know she's still the same old girl underneath.

You're obviously NOT legally blind!

Both the decisions on notify-osd and this button placement show a horrendous disregard for those with visual impairment. In that regard Mark Shuttleworth needs an education.

---

### Post by lidex on 2010-03-23
> **Madspyman said:**
> It seemed to me the decision on the the part of the button order both in Win 95, and OS X (even though it took longer) had to do with putting the buttons all on one side for ease of access. 

Before both had the buttons split between the left and right. Windows moved all theirs on the right side as to not interfere with the file menu, and OS X moved to the left, to be below the global menu.

Ubuntu already had chosen a side that worked. Moving the buttons serves for no apparent gain (that I can see) in functionality. We already had them on one side and things worked fine.

I'm having a hard time understanding how the buttons on the left interferes with the file menu. It's more likely MS threw them right just to fill up empty space - or provide visual symmetry. I don't think it makes any sense to jump all over the screen to accomplish anything.

---

### Post by pastalavista on 2010-03-23
> **kansasnoob said:**
> You're obviously NOT legally blind!

Both the decisions on notify-osd and this button placement show a horrendous disregard for those with visual impairment. In that regard Mark Shuttleworth needs an education.
If I was legally blind, I would probably be using the screen magnifier and it would seem the new button layout would be preferable by keeping all the controls in the same screen area. But then, what do I know about being blind? Sorry if I offended any handicapped people...

---

### Post by k3lt01 on 2010-03-23
> **pastalavista said:**
> Like my girlfriend always says, "Notice anything different about me?"
I like that. I know she's still the same old girl underneath.If your gf has to ask that then you obviously aren't giving her the attention you should be.

> **kansasnoob said:**
> You're obviously NOT legally blind!Nope but if the quote above you is reality then he does lack visual perception and he may get a surprise oneday from his gf!

---

### Post by pastalavista on 2010-03-23
> **k3lt01 said:**
> If your gf has to ask that then you obviously aren't giving her the attention you should be.

Nope but if the quote above you is reality then he does lack visual perception and he may get a surprise oneday from his gf!

She doesn't HAVE to ask, but I like the fact that she does... and the fact that she is always full of surprises.

---

### Post by mc4man on 2010-03-23
> Failing that, a well-advertised (maybe in the technical overview) PPA. 
To some extent there is a ppa for a very easy to use editor for any config. It also   has atm 3 presets.
 
Not packaged right now though easily could be.  (installed here to pref's.

[Ex. and link]("http://ubuntuforums.org/showthread.php?p=9008909#post9008909")

edit: though I guess this could fall under the term 'hacky script' though I don't consider it so.

---

### Post by zengeos on 2010-03-23
OK here's my 2 cents...worth about 10% of that....


I have no problem with the buttons being on the left..really.

However, here's something I am noticing...the scrollbar is on the right and bottom. So, to control my window functions I have to move the mouse from right to left nd up and down....the buttons being on the left do NOT i,prove mouse moving efficiency as some people here have been suggesting it does.

Still, I don't think, overall, having the buttons all left is necessarily a bad thing.

---

### Post by k3lt01 on 2010-03-23
Hmmmmm, 1 day since I put the buttons back where Mr Shuttleworth wants us to try them I am slowly stopping making silly mistakes. I have the menu button on the right so I can still go to either side and do whatever I want to. This is in both Lucid and Karmic, yes I am testing it out on them both because that forces me to use it and not to cop out early.

The one thing that I am finding annoying is the title in the title bar is now off-centre. When the buttons are on the right side the title is centred properly but with them on the left it isn't. I think if the title was centred properly the screen wouldn't appear screwy, or as screwy.

Soooooooo, is there a simple way like gconf, which I haven't looked at yet but I will now, to properly centre the title?

---

### Post by uRock on 2010-03-23
> **k3lt01 said:**
> centre?

What the.. Just kidding, There is a bug report for the title and it has been triaged. I don't know when the fix will be out though.

---

### Post by asmoore82 on 2010-03-23
> **thatguruguy said:**
> I use Ubuntu on my computer. My kids use Ubuntu on their computer. My sister (and her kids) use Ubuntu on her computer. My wife uses Ubuntu on her computer.  However, Ubuntu isn't really an OS; it's a distribution of Linux, and Linux only has a market share of about 1% on the desktop. The fact that you, I, and other people we know use Ubuntu or some other distribution of Linux does not, in and of itself, make Linux a "major OS".
Don't pull your market share statistics straight from the mouths of Micro$oft's Buddies.

[http://www.w3schools.com/browsers/browsers_os.asp](http://www.w3schools.com/browsers/browsers_os.asp)

[http://digg.com/linux_unix/GNU_Linux_Desktop_Market_Share_is_4_Gartner](http://digg.com/linux_unix/GNU_Linux_Desktop_Market_Share_is_4_Gartner)

[http://blogs.zdnet.com/ITFacts/?p=5334](http://blogs.zdnet.com/ITFacts/?p=5334)

[http://blog.linuxtoday.com/blog/2009/05/1-linux-market.html](http://blog.linuxtoday.com/blog/2009/05/1-linux-market.html)

---

### Post by djchandler on 2010-03-24
> **zengeos said:**
> ...the scrollbar is on the right and bottom. So, to control my window functions I have to move the mouse from right to left nd up and down....the buttons being on the left do NOT improve mouse moving efficiency as some people here have been suggesting it does....

> **lidex said:**
> ...MS threw them right just to fill up empty space - or provide visual  symmetry. I don't think it makes any sense to jump all over the screen  to accomplish anything.     

> **k3lt01 said:**
> The one thing that I am finding annoying is the  title in the title bar is now off-centre. When the buttons are on the  right side the title is centred properly but with them on the left it  isn't.

These 3 ideas cover my view on this topic very well.

Speculative reasoning follows, but bear with me and consider this in an evolutionary sense.

The point about empty space and some degree of symmetry are valid criteria for design  consideration. Complete bilateral symmetry is boring; we see it all the time. But it can't be so imbalanced it gives us a sense of unease. We have an innate need to see things in balance. Things looking balanced means safety. When something looks off balance, we sense that danger may be nearby.  Consider rock overhangs, teetering rocks, huge snow drifts on the side of a mountain. Is it possible that these asymmetrical visual cues signal lurking danger, awakening an instinctual response, perhaps as deep as in the limbic system, that we need to do something, either move away, or in the case of a sentient being, do something to fix it? This applies to both the off-center title and the button placement. I realize we are not talking about real danger here, but the desire to see things in balance, to feel that comfort, is nonetheless in play.

I [sarcastically suggested]("http://ubuntuforums.org/showthread.php?p=9005611#post9005611")  in "Poll: Have You 'Tested' New UI Elements" that maybe we should consider putting the scrollbar over to the left too. The vertical scroll bar is on the right because we read left to right in most western languages. If the scroll bar was on the left and you are right handed, it's a virtual given that would feel awkward. Left-handed readers of western languages have been dealing with this inconvenience their whole lives. Yet we don't make left-handed books or newspapers. Putting other window controls on the right side makes sense in terms of ergonomics and economy of motion when it's necessary to leave the scrollbar on the right.

---

### Post by uRock on 2010-03-24
> **djchandler said:**
> [s]snip[/s]
Your kitten looks depressed.

---

### Post by k3lt01 on 2010-03-24
> **djchandler said:**
> I [sarcastically suggested]("http://ubuntuforums.org/showthread.php?p=9005611#post9005611")  in "Poll: Have You 'Tested' New UI Elements" that maybe we should consider putting the scrollbar over to the left too.That is an option in certain other OSs with certain other Browsers. I used to right click often and accidentally click reverse and all of a sudden the scroll would be on the left.

---

### Post by crankyfuzz on 2010-03-24
I suddenly have no buttons for Min,Max of Close and I cant move any windows anyone else having this problem

---

### Post by kansasnoob on 2010-03-24
> **pastalavista said:**
> If I was legally blind, I would probably be using the screen magnifier and it would seem the new button layout would be preferable by keeping all the controls in the same screen area. But then, what do I know about being blind? Sorry if I offended any handicapped people...

You'll notice I also mentioned notify-osd. How do you use the screen magnifier to see a message that disappears before you can focus?

Having been impaired for several years due to meningoencephalitis I can guarantee you that "change" is the enemy!!!!

Of course sometimes change is worth the effort but I certainly don't see that being the case here.

I'm already looking at Xubuntu as an alternative because I don't really like any of the other distro's that use Gnome either.

Or maybe I'll figure out how to really do pure Gnome on top of a minimal Ubuntu :D

---

### Post by k3lt01 on 2010-03-24
> **crankyfuzz said:**
> I suddenly have no buttons for Min,Max of Close and I cant move any windows anyone else having this problemAlt> F2 and type in gconf-editor and redo your button selction making sure you don't have any spaces between anything and also don't forget the : on one side or the other.

```
menu:minimize,maximize,close
``` or ```
maximize,minimize,close:menu
```

---

### Post by lidex on 2010-03-24
> **k3lt01 said:**
> That is an option in certain other OSs with certain other Browsers. I used to right click often and accidentally click reverse and all of a sudden the scroll would be on the left.
Anyone know how to do that in gnome?

---

### Post by crankyfuzz on 2010-03-24
> **k3lt01 said:**
> Alt> F2 and type in gconf-editor and redo your button selction making sure you don't have any spaces between anything and also don't forget the : on one side or the other.

```
menu:minimize,maximize,close
``` or ```
maximize,minimize,close:menu
```


I checked and that is what it says I also can not move windows from the position they open in I tried restarting and every time I do I have to re enable the driver for my video card which is a NVidia

---

### Post by djchandler on 2010-03-24
> **iRock said:**
> Your kitten looks depressed.

It's probably a picture of a zoo specimen. I was going for good color,  sharpness and well developed specific traits when I chose the photo to work from. Now that you mention it, he does look a little down. Maybe he's just sleepy.

[http://commons.wikimedia.org/wiki/File:Canadian_Lynx.jpg](http://commons.wikimedia.org/wiki/File:Canadian_Lynx.jpg)

---

### Post by sonicb00m on 2010-03-24
> **lidex said:**
> It's really just what you're used to. Maybe the scroll bar should go left as well. For me personally, I would prefer the highly used items be left and center as it seems I only go right because the buttons and scroll bar are there. But I hardly use the scroll bar now, instead opting for the mousewheel. In my Mozilla apps my main toolbar buttons are in the middle - even the menu bar.

Yes it's true but also consider that the other stuff that make my mouse lean towards the other side of the screen isn't being moved. And why should i have to be used to something else just because Ubuntu wants me to? What about when i use the plethora of other computers and OS installations then i'm having to retrain to use both directions.

I also use the mouse wheel a lot but the mouse wheel isn't great when scrolling large texts and you know you want to be in the middle quickly. 

I could , however , quite happily use the min,max,close in the centre of the bar.

As long as  I have the option to put the buttons back where iwant them manually I don't really care what the default is.

---

### Post by k3lt01 on 2010-03-24
> **crankyfuzz said:**
> I checked and that is what it says I also can not move windows from the position they open in I tried restarting and every time I do I have to re enable the driver for my video card which is a NVidiaNot being smart here but if it was on the left side it wouldn't say that because I changed my order around to suit me. I also added the menu to mine as it wasn't there originally. So may I suggest you copy what is in the cod box I posted and paste it into your gconf-editor and make sure you hit enter because it wont change unless you do. Then before you close gconf-editor check they are how you want them and if thy are close it.

---

### Post by knarf on 2010-03-24
> **crankyfuzz said:**
> I suddenly have no buttons for Min,Max of Close and I cant move any windows anyone else having this problem
Do you have any window decoration (borders) at all? If not it sounds like you don't have a window manager...

If that is the case you can try...

```
metacity --replace &
```...in a terminal window - if you can get one of those to appear and you can enter text in it. Do you have controls now?

If you can not get a terminal window you can always switch to the console (Ctrl-Alt-F1/2/3/4/5/6), login and try...

```
DISPLAY=:0 metacity --replace &
```Now switch back to X (Alt-F7) and see if you have controls...

---

### Post by magneze on 2010-03-24
> **lidex said:**
> fawn much? :rolleyes:eh?

---

### Post by uRock on 2010-03-24
> **magneze said:**
> eh?

I didn't get that either.

---

### Post by omkrasu on 2010-03-27
It looks more alright with the darker look.

---

### Post by QwUo173Hy on 2010-03-27
One great thing about the new buttons is that if I'm on a Karmic machine (or god forbid a Windows one), I can still use the menu on the top-left there. It was only when I realized that that I really got into the swing of it.

---

### Post by DeMus on 2010-03-28
> **swoll1980 said:**
> It drove me nuts on the left. Did a gconf-editor apps>metacity>general look for button configuration, double click it.You just have to stick a : colon at the beginning of the line, and swap min and max.

Great, works perfectly. Thanks so much. One step less for not wanting to skip to Lucid.

---

### Post by mirach on 2010-03-28
Not sure what's going on but I just installed Lucid Beta and noticed the button switch Then last night I installed all updates and now the buttons are where they used to be?!?

I'm not sure if the update switched them back or what happened...

---

### Post by goldsniper on 2010-03-28
yup.. i just did the update. and the buttons are all back to the old position ( on the right)

---

### Post by Sandsound on 2010-03-28
> **goldsniper said:**
> buttons are all back to the old position ( on the right)

Great news \\:D/

I hope they stay there

---

### Post by ElSlunko on 2010-03-28
> **goldsniper said:**
> yup.. i just did the update. and the buttons are all back to the old position ( on the right)

For which themes?

---

### Post by mirach on 2010-03-28
All of them...

---

### Post by QwUo173Hy on 2010-03-28
Gutted...

---

### Post by ElSlunko on 2010-03-28
> **mirach said:**
> All of them...

Strange. My Ambiance & Radiance are still to the left with no updates left.

---

### Post by QwUo173Hy on 2010-03-28
Oh...  stop PlaYInG wITh \My MiNd pLeEzE!#! :)

---

### Post by magneze on 2010-03-28
> **ElSlunko said:**
> Strange. My Ambiance & Radiance are still to the left with no updates left.Same here.

---

### Post by foxy123 on 2010-03-28
I sort of like it on the left. The upper-right conner is nice and clean without it.

---

### Post by praveenthivari on 2010-03-28
> **ElSlunko said:**
> Strange. My Ambiance & Radiance are still to the left with no updates left.

It works only for other themes.

---

### Post by lidex on 2010-03-28
Been using Emerald for a long time. Went and changed the buttons to the left to see what the fuss was all about. Took a couple of days to get used to but I think I'll keep it. As far as the menu button goes, I don't even have one - I can right-click anywhere in the titlebar to get it.

---

### Post by blacknymph on 2010-03-28
> **praveenthivari said:**
> It works only for other themes.

How fix this? I want window buttons on the left corner other in other themes.. Because I can't save when I took them on the left

---

### Post by realzippy on 2010-03-28
No buttons:
[ATTACH]151746[/ATTACH]

---

### Post by bcbc on 2010-03-28
> **foxy123 said:**
> I sort of like it on the left. The upper-right conner is nice and clean without it.
You can set buttons to the left with this command (also works on Karmic).
```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu,minimize,maximize,close:
```
If you want them back on the right:
```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```

---

### Post by fenian on 2010-03-28
> **bcbc said:**
> You can set buttons to the left with this command (also works on Karmic).
```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu,minimize,maximize,close:
```
If you want them back on the right:
```
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close
```
You're missing some "" marks,it should be like this...

```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"

```

---

### Post by bcbc on 2010-03-28
> **fenian said:**
> You're missing some "" marks,it should be like this...

```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"

```

I'm not saying you're wrong, but it works without them. ;)

---

### Post by candtalan on 2010-03-28
FWIW I am finding this configuration to be more usable than the beta1 default:

(gconf-editor ...... etc etc)

close,spacer,minimize,maximize,spacer,menu:

---

### Post by uRock on 2010-03-28
> **fenian said:**
> You're missing some "" marks,it should be like this...

```
gconftool-2 --set /apps/metacity/general/button_layout --type string "menu:minimize,maximize,close"

```

With the quotation marks the command doesn't work.

---

### Post by Roasted on 2010-03-28
At least give it a shot and force yourself to use it. I did, and now I find it kind of stupid to have it on the right. However, that's just my opinion. But all of my machines still running older versions of Ubuntu I've tweaked to have the buttons on the left. I digggg eeeeet.

---

### Post by djchandler on 2010-03-29
> **realzippy said:**
> No buttons:
[ATTACH]151746[/ATTACH]

Ah, the "Solomon" approach to settling the controversy. You can certainly live without them. Unlike a child there's no reason to be emotionally attached to buttons.

+1

---

### Post by realzippy on 2010-03-29
> **djchandler said:**
> Ah, the "Solomon" approach to settling the controversy. You can certainly live without them. Unlike a child there's no reason to be emotionally attached to buttons.

+1

...it's just much faster  ;-)

---

### Post by robertneville777 on 2010-03-29
> **lidex said:**
> Been using Emerald for a long time. Went and changed the buttons to the left to see what the fuss was all about. Took a couple of days to get used to but I think I'll keep it. As far as the menu button goes, I don't even have one - I can right-click anywhere in the titlebar to get it.

Holy crap! That's the same one I used before upgrading to Lucid! 

If you change the title font to regular instead of **bold**, it looks a lot nicer. (in my humble, unbiased opinion).

---

### Post by robertneville777 on 2010-03-29
At first I was all opposed to the buttons placed on the left, but now it makes more sense. 

You have all your options on the left side, and for most people who read left to right, you're naturally going to see these options first, so it actually makes it faster to close, maximize, and minimize windows since you naturally scan the screen left to right (if I was Hebrew or something, I would have this the exact opposite). Plus your options (file, edit, view, etc.) are already there so there's less space and time to move  the cursor from window option to program option.

My only complaint with moving the buttons to the left is that they should be moved in a mirror like fashion to the left, rather than just ripping the buttons off the left and placing them on the right. So you would end up with close, maximize, minimize (similar to Mac OS X). But I don't have any hard evidence to support this as more functional to the average user, that's just my two cents.

Unless somebody sees an advantage and agrees with me?

---

### Post by robertneville777 on 2010-03-29
Actually, gnome-global-menu makes for a MUCH cleaner window, but that's beside the point.

---

### Post by Cushie on 2010-04-02
> **chucky chuckaluck said:**
> It'll probably still be easily changed (if you can ever find it in the gconf registry). I'm just curious about the reason behind doing this. 


It is easy to change back to the traditional top RHS.

Alt +F2 to open launcher

**gconf-editor**

select: apps/metacity/general/button_layout

Place 'spacer, after 'menu:'

**menu:spacer,maximize,minimize,close**

Q.E.D.
;)

---

### Post by k3lt01 on 2010-04-02
> **Cushie said:**
> It is easy to change back to the traditional top RHS.

Alt +F2 to open launcher

**gconf-editor**

select: apps/metacity/general/button_layout

Place 'spacer, after 'menu:'

**menu:spacer,maximise,minimise,close**

Q.E.D.
;)There is no need to put "spacer" anywhere at all. Also the "traditional" RHS is menu:minimize,maximize,close. Note the order and also the spelling. I haven't been able to get it to work with "s" I can only get it to work with "z".

---

### Post by Cushie on 2010-04-03
> **k3lt01 said:**
> I haven't been able to get it to work with "s" I can only get it to work with "z".

Sorry correction made, not used to typing english(US).

---

### Post by Doctor Mike on 2010-04-03
You know I've got to laugh. I found the button switch to be a pain, but I've been trying to get use to it. After about two weeks I decided to switch everything back. Now I find myself reaching to the left on occasion, but only about half as many errors (right) as when the buttons were moved to the left.

The two scripts from this thread: 

gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close

&

window_controls.py

could be merged with a few minor changes and shipped with the final release of Lucid and nobody need be unhappy about anything. However, there may be a reason for the switch that has not been revealed, but I doubt it.

---

### Post by squiddie on 2010-04-03
I'll send a shell script to the users i'm supporting when this hits live which will look something like this (use on your own risk :p)

```

#!/bin/sh
find /usr/share/themes -name gconf-settings.sh -type f -exec sed -i 's/maximize,minimize,close:/menu:minimize,maximize,close/g' {} \;
find /usr/share/themes -name index.theme -type f -exec sed -i 's/maximize,minimize,close:/menu:minimize,maximize,close/g' {} \;

```

Ah yes, sudo it of course.

Please have patience if this has already be proposed but I didn't have the time to read 22 pages ;)

cheers o/

---

### Post by Arrgon on 2010-04-03
I really hope they consider a simple toggle option to switch back to the original location.  

Why they feel the need to be different, I dont know, but we should at least have the option to have it look like most every other standard windows based environment if we want it to.

If they don't, I would be willing to bet it will be enough of a headache that many users will either downgrade or switch to another flavor of linux.

I, for one, will not stick with this version in its current shape.  

Almost enough grief to make me wanna switch back to MS Windows. 

Almost.

---

### Post by phoenixmdm on 2010-04-10
I must be crazy or something...I actually like the new positions!

At first, I was outraged that the buttons would be moved to such a weird place, but then I got the hang of it. After about 2 hours, I realized it's great. I now tend to resize windows using the upper-right, where the close used to be. Seems easier to grab than the other corners, for some reason.

---

### Post by BrokeMahPC on 2010-04-10
I am crazy too - I can't see a problem with the new button positions. 
After a few weeks I use them as naturally as I did when they were on the right. It's not a big change really - you get used to it very quickly. 
I have never closed a window by accident but at the beginning I did maximize or minimize when I meant to do the opposite. 
I think it would be best to try to get used to it as I have read that Ubuntu intend to do something with that space in the future. 
When they do whatever it is, it's possible that you may not be able to change the buttons over to the right, or doing that will stop something working?

---

### Post by uRock on 2010-04-10
I am not sure if the others have noticed, but when you select themes other than Ambiance, Dust and Radiance, the buttons are placed on the Windows(left) side.

I have the buttons on the left on my desktop machine and the right on my netbook and I do not have any problems when going from one machine to the other.

Cheers,
Ronnie

---

### Post by speedy1979 on 2010-04-10
> **seenthelite said:**
> Simple Solution

Thanks for the tip seenthelite now I can too.:)

---

### Post by d3drocks on 2010-04-13
dont wanna sound mean or anything, but the new visual theme in 10.04 is really ugly the fact that the close/minimize/maximize buttons have suddenly moved to the left hand side gets annoying as well (i dont know who's idea it was to do that, but it was a really bad idea). I've been using the default ubuntu layout until now.

---

### Post by Crunchy the Headcrab on 2010-04-13
Yeah.  I don't mind the theme itself too much but the gdm (login) screen is hideous.  Had to fix that up myself.

If you'd like a step by step on how to move the window buttons to the other side of the screen, I can give you one.  Most of the other themes still have the buttons on the right side though, so this shouldn't be a problem anyway, if you don't like the default theme.

---

### Post by Merk42 on 2010-04-13
> **d3drocks said:**
> ...the fact that the close/minimize/maximize buttons have suddenly moved to the left hand side gets annoying as well (i dont know who's idea it was to do that, but it was a really bad idea)...

It was Mark Shuttleworth's idea

---

### Post by ronparent on 2010-04-13
I inadvertenly found the buttons moved back to the right if I right clicked on the desktop background and selected another theme! There also appears to be many options for cutomizing.

---

### Post by prodigy_ on 2010-04-13
> **Merk42 said:**
> It was Mark Shuttleworth's idea
Everyone makes mistakes occasionally.

Anyway ```
gconftool-2 --set /apps/metacity/general/button_layout --type string :minimize,maximize,close
``` command fixes this annoying bug with buttons placement. ;-)

---

### Post by JoeWheeler on 2010-04-13
I really like it actually, the buttons have taken a bit of getting used to but im used to it now.

However i do appreciate that i may well be in the minority about that

---

### Post by andrewabc on 2010-04-13
> **prodigy_ said:**
> ```
gconftool-2 --set /apps/metacity/general/button_layout --type string :minimize,maximize,close
``` command fixes the bug with buttons placement. ;-)

Guess I'll have to remember that instead of having my parents relearn where the buttons went.

I'm not sure the reason for doing this. Spend time moving stuff around just in time for a LTS release, Canonical is going to take a lot of heat from users complaining about the max/min/close button placement. Why they couldn't wait until 10.10 to make drastic GUI changes I'm not sure.

Trying too hard to be different? Hoping the bad press will generate more brand awareness anyways?

---

### Post by prodigy_ on 2010-04-13
> **andrewabc said:**
> Trying too hard to be different?

Unfortunately, it's not even so [different](http://en.wikipedia.org/wiki/File:Snow_Leopard_Desktop.png).

---

### Post by hackb0y294 on 2010-04-13
Yeah, I think it's ugly too. I don't know why they moved the buttons (maybe to move farther away from Windows?), but it is weird. I'm just testing 10.04 right now, but when I start using it I'm going to switch the buttons back to normal. :)

---

### Post by JoeWheeler on 2010-04-13
> **andrewabc said:**
> Guess I'll have to remember that instead of having my parents relearn where the buttons went.

I'm not sure the reason for doing this. Spend time moving stuff around just in time for a LTS release, Canonical is going to take a lot of heat from users complaining about the max/min/close button placement. Why they couldn't wait until 10.10 to make drastic GUI changes I'm not sure.

Trying too hard to be different? Hoping the bad press will generate more brand awareness anyways?

I think you hit the nail on the head with the trying to be different thing. At first I thought it was a bit counter intuitive what with most people being right handed but now I quite like it as the min max buttons are near the apllication/place/system menus which I'm quite fond of

---

### Post by mamamia88 on 2010-04-13
crap i'm an idiot and installed karmic in virtualbox by mistake

---

### Post by mcduck on 2010-04-13
> **andrewabc said:**
> Guess I'll have to remember that instead of having my parents relearn where the buttons went.

I'm not sure the reason for doing this. Spend time moving stuff around just in time for a LTS release, Canonical is going to take a lot of heat from users complaining about the max/min/close button placement. Why they couldn't wait until 10.10 to make drastic GUI changes I'm not sure.

Trying too hard to be different? Hoping the bad press will generate more brand awareness anyways?

If the position of window buttons on *two of the available themes* is the worst thing people can think of to complain about, then I think 10.04 will do remarkably fine... :D

And the reason for the change, according to Shuttleworth, is that they have other plans for the right side of the titlebar & the menu bar. Moving the buttons to the left frees lot more space there (and, more importantly, more vertical space). Also you might have noticed that the whole space there can be now used for moving the window (instead of just the titlebar as previously).

And, for anybody who's going to mention how this is copied from OSX, I should tell you that not only did all the Windows versions prior to Win95 have  close button on the left, but also many other operating systems have all, or some, buttons there. It's nothing new or special, unless you have only ever used new versions of Winodws.. ;)

---

### Post by kernco on 2010-04-13
I think the worst part of this change is the artwork that came with it.  The window buttons appear in that "tray" which means you can't change the order of them without it looking horrible.  Yes, you can move them back to the right, but if you want to keep on them the left but move the close button to the outside, then that "tray" is  completely broken apart.  So much for choice in Linux.

Also, with Radiance and Ambiance, you can't make the panels transparent.  I mean, you can, but only the empty areas of the panels actually change.  The clock, menu, system tray, etc. are still shaded with the gradient.  Another choice gone.

---

### Post by mrdoob on 2010-04-13
I think the theme would improve quite a bit by **center aligning the titles of the windows**.

User experience would improve as it takes a few extra milliseconds to visually isolate the text/button/icon you want to read/click.

Design-wise it's not equilibrated, too much visual "noise" on the top-right while the rest of the window is empty.

---

### Post by 23meg on 2010-04-13
Threads merged.

---

### Post by uRock on 2010-04-13
Why do people assume their parents are too ___ to get used to the buttons? People make the switch to Mac everyday and the buttons are on the left. Yes I know they don't close the programs when you close the windows in Mac, but still. After a short period of time I got so used to it that I don't even think about it anymore. And yes I also use systems that have buttons on the right and I do not get confused or slowed down when I switch back and forth.

Another important thing is that you do not have to run a command to move the buttons unless you want to keep the theme. Just open the appearance applet and select a theme other than Ambiance, Dust, or Radiance.

Quit accusing old people of being unable to handle change. I think it is very derogatory to do so.

Cheers,
Ronnie

---

### Post by mrdoob on 2010-04-13
> **23meg said:**
> Threads merged.

Oh, thanks! Now that I was trying to move back the conversation to the original topic. Now my message is out of topic.

---

### Post by d3drocks on 2010-04-13
> **Meep3D said:**
> I have to say I am disappointed by the proposed change in button position, and quite frankly surprised that it is getting any support.  So here's my run-down of why I think it's a bad idea (after screenshot):....

didnt quote the whole thing cause I didnt want to eat up alot of screenspace (i use ubuntu on a netbook with a max resolution of 1024x600).
just wanted to say that you are bang on, and that was very well written.


> **Crunchy the Headcrab said:**
> Yeah.  I don't mind the theme itself too much but the gdm (login) screen is hideous.  Had to fix that up myself.

If you'd like a step by step on how to move the window buttons to the other side of the screen, I can give you one.  Most of the other themes still have the buttons on the right side though, so this shouldn't be a problem anyway, if you don't like the default theme.

i wouldnt mind a refresher on how to do that. I havnt played with button locations since 7.04, so ive completely forgotten how to do it. i agree that the login screen is really ugly.

> **Merk42 said:**
> It was Mark Shuttleworth's idea

has he been using alot of macs?

> **prodigy_ said:**
> Unfortunately, it's not even so [different](http://en.wikipedia.org/wiki/File:Snow_Leopard_Desktop.png).
ewwww

---

### Post by k3lt01 on 2010-04-13
> **mrdoob said:**
> I think the theme would improve quite a bit by **center aligning the titles of the windows**.That was the biggest issue for me, once I got used to the button location I still thought it was yuck because the titles were off-centre (especially on smaller app gui's like Pidgin).

---

### Post by uRock on 2010-04-13
> **k3lt01 said:**
> That was the biggest issue for me, once I got used to the button location I still thought it was yuck because the titles were off-centre (especially on smaller app gui's like Pidgin).

I think I saw a bug report on that somewhere.

---

### Post by lidex on 2010-04-13
> **k3lt01 said:**
> That was the biggest issue for me, once I got used to the button location I still thought it was yuck because the titles were off-centre (especially on smaller app gui's like Pidgin).

Don't know about gnome, but emerald allows you to add 'spacers' of whatever pixel size you need to center the titles

---

### Post by k3lt01 on 2010-04-13
> **lidex said:**
> Don't know about gnome, but emerald allows you to add 'spacers' of whatever pixel size you need to center the titlesSo in essence another application needs to be installed to fix something that shouldn't need fixing.

It doesn't really matter all that much anyway mine reverted back to the traditional side when I updated 2 weeks ago.

---

### Post by JOHNNYG713 on 2010-04-13
The new "Ubuntu Tweak" has an option for changing the buttons and more ! or you can change it in gconf.

---

### Post by k3lt01 on 2010-04-13
> **JOHNNYG713 said:**
> The new "Ubuntu Tweak" has an option for changing the buttons and more ! or you can change it in gconf.This is part of the problem with such large threads, this has already been point out but thanks for bringing it to the fore again.

---

### Post by uRock on 2010-04-14
We must remember that even though some of us have been in the conversation since the beginning, more and more people will be joining in as the release goes through its stages.

I am happy that some people are peacefully throwing in ways to change the buttons to the right, even if I do like them on the left. In the end all of us Linux lovers want our systems our way.

Cheers,
Ronnie

---

### Post by Taoye on 2010-04-14
I certainly don't think they should be making such a drastic change for their users as switching the buttons to the left... but come on, it's not that hard to get used to. I've been a Windows user all my life, and it didn't take me long to get used to the button placement on the left when I bought a mac earlier this year, and getting used to Ubuntu's change hasn't been very difficult either.

I actually prefer 'em on the left, and I don't see a problem with leaving them there, but please make it easy for users to move them.

---

### Post by uRock on 2010-04-14
> **Taoye said:**
> I certainly don't think they should be making such a drastic change for their users as switching the buttons to the left... but come on, it's not that hard to get used to. [COLOR=Red]I've been a Windows user all my life, and it didn't take me long to get used to the button placement on the left when I bought a mac earlier this year, and getting used to Ubuntu's change hasn't been very difficult either.[/COLOR]

I actually prefer 'em on the left, and I don't see a problem with leaving them there, but please make it easy for users to move them.

Thank you for sharing that. It isn't hard at all. And hopefully the changes Mark has in mind for the new release will be icing on the cake. :)

---

### Post by pastalavista on 2010-04-14
Please close this thread already! I can't believe how people have gone over the edge so much about something so trivial. Maybe if it wasn't so easy to change it would matter a little but now it's starting to sound like a bunch of spoiled babies crying because mommy didn't cut the crust off of their sandwich. Get over it people...

---

### Post by Eddie Wilson on 2010-04-14
> **pastalavista said:**
> Please close this thread already! I can't believe how people have gone over the edge so much about something so trivial. Maybe if it wasn't so easy to change it would matter a little but now it's starting to sound like a bunch of spoiled babies crying because mommy didn't cut the crust off of their sandwich. Get over it people...

This thread should be left open. After all this is testing and development for the release of 10.04 so people should be able to give their opinion even if it's a non-issue to most.

---

### Post by k3lt01 on 2010-04-14
> **Eddie Wilson said:**
> This thread should be left open. After all this is testing and development for the release of 10.04 so people should be able to give their opinion even if it's a non-issue to most.
+1

It should be left open but, and this has been happening anyway, threads on this same issue should be merged into this one.

---

### Post by iClouseau88 on 2010-04-14
How about leaving all three buttons on the left to avoid cluttering the right; since Ubuntu adds an IM button and a Close/shutdown/restart button to where the 3 buttons used to be. The only change I would suggest is the sequence from left to right:

Minimize > Maximize > Close

;-))

---

### Post by camiladrian on 2010-04-15
i just try the beta 2.
yeah, it look weird, all that right space unused, and the left full packed.
just try the live cd for an hour, but many times i ended clicking an empty top-right.

i just dont understand that crazy approach about "copying apple, switch mac users to ubuntu" its obvious that ubuntu from day 1, its more like a mac than a windows, release after release increasing the copycat, its pointless, the apple fans are the most hard fans, and the hard fans mostly are idiotic mindless followers, who wont switch no matter what.

going after this market is a waste of time, time and resources wasted in sync iphones, itunes, ipod support, now changing a universal interface, it wont add any users, but sure will lose some.

i dont know, maybe most people will love the change and new users wont be confused, time will tale.

i should thank you, that change make me finally deciding to start my own distribution, better 2 years later than never i guess, thank you.

---

### Post by Merk42 on 2010-04-15
> **iClouseau88 said:**
> How about leaving all three buttons on the left to avoid cluttering the right; since Ubuntu adds an IM button and a Close/shutdown/restart button to where the 3 buttons used to be. The only change I would suggest is the sequence from left to right:

Minimize > Maximize > Close

;-))
:confused: The left side has more stuff in it with "Applications Places System" and "File Edit View..."

---

### Post by magneze on 2010-04-15
So we now have Close, Minimize, Maximize in the latest updates. :lolflag:

---

### Post by aysiu on 2010-04-15
> **magneze said:**
> So we now have Close, Minimize, Maximize in the latest updates. :lolflag:
At least that button order makes sense.

---

### Post by philinux on 2010-04-15
> **magneze said:**
> So we now have Close, Minimize, Maximize in the latest updates. :lolflag:

I've done away with maximise as I just use double click on the window border.

---

### Post by VMC on 2010-04-15
The latest daily-live(Apr15) has moved "close" once again. Anyone else have this?

From "Close, Minimize, Maximize" to "Minimize, Maximize,Close"

---

### Post by Merk42 on 2010-04-15
> **VMC said:**
> The latest daily-live(Apr15) has moved "close" once again. Anyone else have this?

From "Close, Minimize, Maximize" to "Minimize, Maximize,Close"

I just ran updates and you're correct

**Make up your mind Canonical!**

---

### Post by bvanaerde on 2010-04-15
> **aysiu said:**
> At least that button order makes sense.
Actually, minimize-maximize-close made more sense to me :P
It's all about opinion...

I always hated the close button being in the corner, whatever OS we're talking about. It's too easy to click on.

---

### Post by aysiu on 2010-04-15
> **bvanaerde said:**
> Actually, minimize-maximize-close made more sense to me :P It made more sense to me, too... when it was on the right side. > It's all about opinion...

I always hated the close button being in the corner, whatever OS we're talking about. It's too easy to click on. Yeah, my opinion is that it's the most-used button, so it should be in the corner.

---

### Post by magneze on 2010-04-15
> **Merk42 said:**
> I just ran updates and you're correct

**Make up your mind Canonical!**I am imagining some kind of titanic struggle in the UX team. When someone breaks free from the melee they commit a change and go back to the conflict, then someone else breaks free and changes it again.

---

### Post by magneze on 2010-04-15
Close Min Max makes a *little* more sense because it at least mimics the Mac. But it still breaks things with respect to previous Ubuntu users, other Linux users and Windows users and all the other points previously made about this change. Ho hum.

Rest of the theme is coming along - the icons really need to get updated though, purple and orange/brown is not a great combo!

---

### Post by -humanaut- on 2010-04-15
I'm probably a limited minority here but I really like the new button positions it only took me about a day to adapt and to me "it just makes sense" on the left. I'm a big fan of the two new themes as well.

---

### Post by uRock on 2010-04-15
I am a previous version user and Windows user and I have no problem with the switch. I prefer it because it cuts out travel distance between closing one program and opening the next. I don't think that when someone decides to try Linux that they are looking for a replica of Windows.

---

### Post by shae on 2010-04-15
I got that they had changed position too and thought to my self, crap I liked Close/Min/Max.  Well I went to change it and to my amazement it does not mess up the "tray" graphic the window controls are in.  Canonical really patched the you-know-what out of Metacity to get that effect I bet!  Now you can select whichever way you prefer and it will look great!  Furthermore, it properly resizes the tray for when all 3 buttons do not appear.

---

### Post by mcduck on 2010-04-15
> **magneze said:**
> Close Min Max makes a *little* more sense because it at least mimics the Mac. But it still breaks things with respect to previous Ubuntu users, other Linux users and Windows users and all the other points previously made about this change. Ho hum.

Rest of the theme is coming along - the icons really need to get updated though, purple and orange/brown is not a great combo!

Being a Linux user, I'm used to different desktops and window managers having a variable amount of window buttons, arranged in many different combinations on both the left and right side of the titlebar. Quite many Linux window managers do that kind of stuff, it's just Gnome that's pretty much stuck with only the three buttons we have.

...and being a long-time Windows user as well, I'm quite familiar with having Close button in the left corner. Examples: [http://computerworld.name/evolution-of-versions-windows-from-10-to-vista/]("http://computerworld.name/evolution-of-versions-windows-from-10-to-vista/")

What comes to purple&orange, that's just a matter of taste. I bet you'd prefer gray&blue? I'd *hate* that. There simply isn't a theme and colors that everybody would like, and there never will be. Luckily we are able to change the colors and themes as much as we like. :)

---

### Post by benjamimgois on 2010-04-15
> **VMC said:**
> The latest daily-live(Apr15) has moved "close" once again. Anyone else have this?

From "Close, Minimize, Maximize" to "Minimize, Maximize,Close"

Yeah, same here. I still prefer Close, Minimize, Maximize. That makes more sense man. What a mess the button order have become !

---

### Post by amano on 2010-04-15
My favourite Position would be Min-Max on the left and Close on the right.

:popcorn:

---

### Post by Nightstrike2009 on 2010-04-15
> **Originally Posted by swoll1980:**
New comers aren't going to no how. It will cause a flood of "How do I switch the buttons" threads.

Nah won't be that bad I am sure some of the more experienced ubuntu users, will help them out if they really want to know how to put them back to the righthand side. (If they don't, I will!) LMAO#

There is many webpages emerging on how to put them back this is one:[http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/]("http://www.howtogeek.com/howto/13535/move-window-buttons-back-to-the-right-in-ubuntu-10.04/")
PS: If you run "gconf-editor" from the terminal, and know where to look (weblink above) you can change the button layout to anything you want by changing the order (No BS it's true). LOL

PPS: Hope that makes everybody happy, no matter where you like your window gadgets to be placed (just don't ask about bottom or middle I ain't got a clue LOL) I like mine on the right, but thats just my opinion. :-)

---

### Post by Didius Falco on 2010-04-15
> **benjamimgois said:**
> Yeah, same here. I still prefer Close, Minimize, Maximize. That makes more sense man. What a mess the button order have become !

Not for me, pardner.

(blows smoke away from barrel of gconf-editor, twirls it around and puts it back in the holster.) :cool:

---

### Post by Merk42 on 2010-04-15
I've figured it out!

Since you obviously can't please everyone with the button order, they'll just keep randomly changing every week.

---

### Post by aysiu on 2010-04-15
Not that this is even still up for discussion, but it doesn't really matter whether you like a certain button position better than another button position, or even if you could get used to a certain button position you don't like.

You can always customize it however you like.

The debate (which is pointless, since Mark has already decided) makes sense only in terms of thinking about it as a default. What merits (or lack thereof) does it have as a default?

---

### Post by Nightstrike2009 on 2010-04-15
> **Originally Posted by benjamimgois**
Yeah, same here. I still prefer Close, Minimize, Maximize. That makes more sense man. What a mess the button order have become !

Not for me, pardner.

(blows smoke away from barrel of gconf-editor, twirls it around and puts it back in the holster.) 

Yea ha, partner blowing smoke from my gconf-editor too, just told the pilgrims how to do it (post #269), will be interesting to see how many screenshots have em on right rather than left.:-)

> **by aysiu:** The debate (which is pointless, since Mark has already decided) makes sense only in terms of thinking about it as a default. What merits (or lack thereof) does it have as a default?

In my opinion it would make life easier to migrate from mac to linux, but just cause confusion amongst windows migrants and others, I can't see the point in left side default myself, unless a "Killer app" is to appear on the right side of the window bar (as some rumour's are now suggesting)

---

### Post by auh2o on 2010-04-15
> **Roasted said:**
> At least give it a shot and force yourself to use it.

Never. I've had the buttons on the right for over 15 years, and that's where they'll stay. I ain't about to change. There's absolutely no reason to.

I'm not against including the ability to change the buttons to the left as a gconf option. Then it could've been posted as a tweaking tip for those so inclined. But to put them on the left by default, when it serves no real purpose, and no discernible advantage is gained? Stupid. Just take a look at the size of this thread and all the energy wasted for nothing, just trying to move the buttons around.

---

### Post by Nightstrike2009 on 2010-04-15
> [B]
By auh2o[/B] Never. I've had the buttons on the right for over 15 years, and that's where they'll stay. I ain't about to change. There's absolutely no reason to.

I'm not against including the ability to change the buttons to the left as a gconf option. Then it could've been posted as a tweaking tip for those so inclined. But to put them on the left by default, when it serves no real purpose, and no discernible advantage is gained? Stupid. Just take a look at the size of this thread and all the energy wasted for nothing, just trying to move the buttons around.

+1

Amen to that (Linux) Brother

PS: I think we should all change them back to the right and leave them that way in our screenshots, just to "send a message", The new "Tweak UI" package also contains a setting to choose left or right hand side. :-)

---

### Post by andrewabc on 2010-04-15
> **auh2o said:**
> Never. I've had the buttons on the right for over 15 years, and that's where they'll stay. I ain't about to change. There's absolutely no reason to.

I'm not against including the ability to change the buttons to the left as a gconf option. Then it could've been posted as a tweaking tip for those so inclined. But to put them on the left by default, when it serves no real purpose, and no discernible advantage is gained? Stupid. Just take a look at the size of this thread and all the energy wasted for nothing, just trying to move the buttons around.

Don't forget 
pidgin->empathy
[s]gimp[/s]->f-spot
indicator popup that is not configurable
openoffice -> google apps for netbooks (failed).
countdown timer for shutdown
Have no idea if the new scanning software works as good as xsane (I assume uses xsane backend?)
google->yahoo->google

I'm sure there were other 'controversies' that generated lots of posts :P
People got over most of the changes. No reason to close any of these threads as people will spam in other threads about it.

---

### Post by norm7446 on 2010-04-15
Is it just me or have the buttons changed again today ????. I don't mean back over to the right, but just the order. 

I didn't like it to start off with but after clarification of why they have moved and a wee bit of actual using the system, I must admit I am getting used to them being there.

---

### Post by 89c51 on 2010-04-15
> **aysiu said:**
> The debate (which is pointless, since Mark has already decided) makes sense only in terms of thinking about it as a default. What merits (or lack thereof) does it have as a default?

the course that buttons and the theme has taken for lucid makes me wonder why mark hasn't already shut everything down (Canonical) and invest his millions on apple

it seems that what he always wanted is a Mac :confused:

---

### Post by godhika on 2010-04-15
Guys calm down - within the next few hours the buttons will be back to their old (beta 2) position. How do I know? Reading the changelogs. It's a bug not a feature currently.> light-themes (0.1.6.5) lucid; urgency=low

  * Fixing incorrect gconf settings for button layout

The package 0.1.6.5 will be build in about one hour. Look here: [https://launchpad.net/ubuntu/+source/light-themes/0.1.6.5/+build/1694183]("https://launchpad.net/ubuntu/+source/light-themes/0.1.6.5/+build/1694183")

---

### Post by ElSlunko on 2010-04-15
> **89c51 said:**
> the course that buttons and the theme has taken for lucid makes me wonder why mark hasn't already shut everything down (Canonical) and invest his millions on apple

it seems that what he always wanted is a Mac :confused:

Because having them to the right meant he was investing in Windows.

---

### Post by amano on 2010-04-15
The change was just an accident and was reverted soon. It took some time for the fix to hit the repos.

---

### Post by d3drocks on 2010-04-15
> **ElSlunko said:**
> Because having them to the right meant he was investing in Windows.

...like investing in apple is much better lol.

---

### Post by arpanaut on 2010-04-15
> **amano said:**
> The change was just an accident and was reverted soon. It took some time for the fix to hit the repos.

Which change was an accident??? LOL
> 
...like investing in apple is much better lol.

pretty profitable if you bought when it was $129

---

### Post by magneze on 2010-04-18
Ubuntu Netbook Remix 10.04 has the close button on the right when things are maximized. The inconsistencies continue. :(

---

### Post by cariboo on 2010-04-18
After a reboot this afternoon, my buttons are on the right again, even though the settings in gconf-editor show them to be on the left. I'd prefer to have them back on the left.

---

### Post by Artemis3 on 2010-04-18
Did you try **gconftool-2 -t string -s /apps/metacity/general/button_layout "close,minimize,maximize:"** in a terminal?

---

### Post by Nightstrike2009 on 2010-04-29
As promised previously ive informed the newcomers how to change them back to the right hand side [http://ubuntuforums.org/showthread.php?t=1465475]("http://ubuntuforums.org/showthread.php?t=1465475") B-)

So were all free to choose now. :-)

---

