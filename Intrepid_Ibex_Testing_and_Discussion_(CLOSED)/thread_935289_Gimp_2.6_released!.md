---
title: "Gimp 2.6 released!"
date: 2008-10-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by olskar on 2008-10-01
Part of the Release Notes: [http://gimp.org/release-notes/gimp-2.6.html](http://gimp.org/release-notes/gimp-2.6.html)


It is my secret dream to see it in Intrepid ;)

---

### Post by jfernyhough on 2008-10-01
It's in Christoph Korn's PPA.

```
## Christoph Korn - various apps (VLC, GIMP and others)
deb http://ppa.launchpad.net/c-korn/ubuntu intrepid main
# deb-src http://ppa.launchpad.net/c-korn/ubuntu intrepid main
```

---

### Post by olskar on 2008-10-01
Yay! My dream came true, kind of! Thanks!

---

### Post by talkingwires on 2008-10-01
Huh, it looks like they *finally* made some effort to clean up the Gimp's bizarro interface. I haven't used the new version, but from the description of the changes, it sounds like the main window and toolbars will act similarly to Photoshop on OS X. Now if they could just shrink the toolbars and palettes down so they don't take up half the screen, they might have a usable interface!

It's probably too late for Intrepid, but that's what Backports are for.

---

### Post by stormelf on 2008-10-01
Does this version have a "normal" user interface or is it still the jumble of loose application windows that seem to scare away Photoshop users?

EDIT: Screenshots anyone?

---

### Post by taavikko on 2008-10-01
Has anyone made freeze exception request?
Or is it too late?

---

### Post by jfernyhough on 2008-10-01
Quick screeny for you. Guess how long I've had that particular image for? :)

It feels quite a bit nippier than 2.4.1.

---

### Post by plun on 2008-10-01
> **taavikko said:**
> Has anyone made freeze exception request?
Or is it too late?

I don't think its too late for a few important apps.

OO-3.0 is the same.

But reasons for an exception must be good.... what gives a new version ?? etc..

---

### Post by stormelf on 2008-10-01
> **jfernyhough said:**
> Quick screeny for you.

Thanks!

To me it looks like it still suffers from the "everything is a separate window" issues. 

Or is there some new optional setting where you can say "please put this jumble of components inside one single unified application window instead of spreading them all over the desktop"?

---

### Post by snova on 2008-10-01
There's a name for this kind of interface, but I don't remember what it's called. I have no idea how many Gnome applications suffer from this awful interface concept, but that really turned me off the first time I saw it.

Qt Designer looks like that too, by default. But at least Trolltech had the brains to make it optional.

---

### Post by Sephoroth on 2008-10-01
Personally I like the seperate window interface.  Makes windows feel more "dynamic" when dealing with seperate work spaces.  I see how the interface could be more annoying on MS Windows due to the lack of multiple work spaces though.

---

### Post by meborc on 2008-10-01
> **Sephoroth said:**
> Personally I like the seperate window interface.  Makes windows feel more "dynamic" when dealing with seperate work spaces.  I see how the interface could be more annoying on MS Windows due to the lack of multiple work spaces though.

+1

i like the way it feels... i am so used to it and i feel i am more productive on it than on photoshop... (it might be also because i have 1680x1050 resolution and all the windows fit nicely on screen)

i don't understand why people want to change everything to match windows counterparts... if you like photoshop, use gimpshop... or fork the current gimp yourself... i mean :) it is a great program... and all i hear is "i hope they change the gui..." ... if you  don't like it, don't use it... it is all about the choice, isn't it?

---

### Post by olskar on 2008-10-01
You can choose ;)


This is how I have it on my computer, more photoshoplike

Enjoy!

---

### Post by smartboyathome on 2008-10-01
I had had it so that it was a psuedo one window interface, but I haven't reinstalled E17 yet so I can't get the "borderless" function.

---

### Post by Cyrus XIII on 2008-10-01
Playing around with the getdeb.net release now and I can't seem to get the secondary windows to stay on top of the image window, when the latter is selected - unless of course, I manually set them to always stay on top through my window manager, but this is hardly ideal. Moreover, when I move the image to another virtual desktop, the tools don't follow suit.

I don't mean to flame, but what's exactly new here, did they just suppress the taskbar entries for the tools? Or am I missing an option in the preferences that provides the interface, [this screenshot from the release notes]("http://gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg") hints at?

---

### Post by xlinuks on 2008-10-01
Great, the multiple windows are still there, but on top of that you now can't seem to minimize them but close, good work! A big thanks for that from the Photoshop team!

---

### Post by smartboyathome on 2008-10-01
> **Cyrus XIII said:**
> Playing around with the getdeb.net release now and I can't seem to get the secondary windows to stay on top of the image window, when the latter is selected - unless of course, I manually set them to always stay on top through my window manager, but this is hardly ideal. Moreover, when I move the image to another virtual desktop, the tools don't follow suit.

I don't mean to flame, but what's exactly new here, did they just suppress the taskbar entries for the tools? Or am I missing an option in the preferences that provides the interface, [this screenshot from the release notes]("http://gimp.org/screenshots/alternative-2-6-ui-layout-example-two.jpg") hints at?

Preferences > Window Management > Set the Utility Window drop downs to keep above. That worked for me for keeping them above. As for keeping the toolboxes with the window, they seem to have gotten rid of the "Keep utility window transient to main window" option which was in the early 2.5s, which means that I don't think we can keep the toolbars with the image window unless we group them together with compiz. :(

---

### Post by Cyrus XIII on 2008-10-01
This keeps the tools on top, but also brings back their taskbar entries. :(

Incidentally, I just noticed that the torrent detail windows in Transmission behave exactly how I'd like the tools in GIMP to.

---

### Post by olskar on 2008-10-01
> **Cyrus XIII said:**
> This keeps the tools on top, but also brings back their taskbar entries. :(

Incidentally, I just noticed that the torrent detail windows in Transmission behave exactly how I'd like the tools in GIMP to.

Indeed, and I can not see the point

---

### Post by Cyrus XIII on 2008-10-01
Well, obviously I don't want a single application to hog up 3+ taskbar entries by default, that's what most apps have tabs for these days. And I also want the toolbox and docks to be readily accessible without having to manually bring them back to the top all time. Using the default options under Window Management for these elements ("Utility window") I can't even Alt+Tab to them.

---

### Post by bruce89 on 2008-10-01
If you want change, the code is [over there]("http://svn.gnome.org/viewvc/gimp/trunk/").

---

### Post by exploder on 2008-10-01
The changes to the GUI take a little getting used to but there are some new features and it works great! The release notes explain the changes that were made.

[http://gimp.org/release-notes/gimp-2.6.html](http://gimp.org/release-notes/gimp-2.6.html)

---

### Post by Cyrus XIII on 2008-10-01
[QUOTE="GIMP 2.6 release notes"]Toolbox and Docks have been changed to Utility window. This enables window managers to do a much better job of managing the GIMP windows, including omitting the Toolbox and Docks from the taskbar and **ensuring that the Toolbox and Docks always are above image windows**.[/QUOTE]

So the window manager does not (yet) handle this properly?

---

### Post by bruce89 on 2008-10-01
> **Cyrus XIII said:**
> So the window manager does not (yet) handle this properly?

Metacity [handles them]("http://live.gnome.org/Metacity/WindowTypes") correctly anyway.

---

### Post by gaspard.leon on 2008-10-01
Sounds like a case of windowmanageritis

lol

Utility windows as I understand it are exactly what you'd want the toolboxes in GIMP to be...

perhaps a little disclosure as to what manager people are using will determine where bugs should be filed?

I use metacity, and when I get home tonight I'm going to try and find a deb GIMP 2.6 for Hardy and test it out... (that PPA sounds promising)

---

### Post by olskar on 2008-10-01
> **Cyrus XIII said:**
> Well, obviously I don't want a single application to hog up 3+ taskbar entries by default, that's what most apps have tabs for these days. And I also want the toolbox and docks to be readily accessible without having to manually bring them back to the top all time. Using the default options under Window Management for these elements ("Utility window") I can't even Alt+Tab to them.

I meant I can see your point, but not the point of having 3+ taskbar entries by default :)

---

### Post by exploder on 2008-10-01
Here is some more information about the new version.

[http://www.osnews.com/story/20350/GIMP_2_6_0_Released](http://www.osnews.com/story/20350/GIMP_2_6_0_Released)

I changed Utility Windows to Normal Windows until I have a better grasp of how to work with the changes that have been made. So, what it boils down to is that I still have a more feature rich application to use and I can still work with it as I did before.

---

### Post by Sephoroth on 2008-10-01
> **Cyrus XIII said:**
> Well, obviously I don't want a single application to hog up 3+ taskbar entries by default, that's what most apps have tabs for these days. And I also want the toolbox and docks to be readily accessible without having to manually bring them back to the top all time. Using the default options under Window Management for these elements ("Utility window") I can't even Alt+Tab to them.

Heh, for me Kiba-Dock and possibly Compiz tabbing/grouping take care of that XD.

---

### Post by smartboyathome on 2008-10-01
So, I am guessing that Compiz is the culprit here for the Utility windows not working properly.

---

### Post by talkingwires on 2008-10-01
> **meborc said:**
> i like the way it feels... i am so used to it and i feel i am more productive on it than on photoshop... (it might be also because i have 1680x1050 resolution and all the windows fit nicely on screen)Try using it on a laptop with a 1024x768 screen. The toolboxes and palettes take up half the screen.> **meborc said:**
> i don't understand why people want to change everything to match windows counterparts...It's not a matter of wanting it to work like the Windows version of Photoshop, but it needs to have a sane interface. The new version is a step in the right direction. It's not impossible to have a good interface for a graphics program build with GTK. [Check out Inkscape]("http://www.inkscape.org/screenshots/index.php").> **meborc said:**
> or fork the current gimp yourself...That comment is the single most annoying "argument" I hear thrown around in the OS community. It's right up there with "RTFM".> **meborc said:**
> if you  don't like it, don't use it... it is all about the choice, isn't it?Quick, name another OS raster-based image editing program that has comparable features! How about ~any~ comparable program that runs natively on Linux? Well, there's Pixel, but it's been an alpha/beta for years. I'm curious about it, but who pays for beta software?

So I choose to run Photoshop under Wine, or boot into Windows if need be. Then again, I'm a designer/photographer, and Gimp simply doesn't have the features required for working in the field. Sure, I try out new versions occasionally out of curiosity. But as the program stands right now, I'm not even sure who it's made for. It's too complicated for moms who just want to touch up snapshots of their kids, and lacks many key features to be put to professional use. Maybe it's targeted for the Photoshop Elements crowd?

---

### Post by exploder on 2008-10-01
What exactly is wrong with the Utility Windows? I do not have Compiz enabled and I really didn't have any problem. I switched to Normal Windows so that I could minimize the individual windows to the panel.Possibly changing the settings like I have done could solve any Compiz related issues. Just a thought.

---

### Post by nanog on 2008-10-01
Yawn -- wake me up when I can $%#$@**** edit a 16 or 24 bit image. I've been waiting on gegel for 4 years now. 

GIMP is largely used by web page designers -- where an 8 bit compressed png suffices.  AAaaargh!

---

### Post by smartboyathome on 2008-10-01
> **nanog said:**
> Yawn -- wake me up when I can $%#$@**** edit a 16 or 24 bit image. I've been waiting on gegel for 4 years now. 

GIMP is largely used by web page designers -- where an 8 bit compressed png suffices.  AAaaargh!

Can't GEGL do that now? I'm honestly curious.

---

### Post by Mr. Picklesworth on 2008-10-01
> **Cyrus XIII said:**
> Well, obviously I don't want a single application to hog up 3+ taskbar entries by default, that's what most apps have tabs for these days. And I also want the toolbox and docks to be readily accessible without having to manually bring them back to the top all time. Using the default options under Window Management for these elements ("Utility window") I can't even Alt+Tab to them.
The idea is you no longer have to. The utility windows are now raised with the image window by your window manager. If you want to switch to them for keyboard accessibility stuff, you can map Ctrl + Tab or something along those lines to switch between windows in a group :)

Ubuntu should never have started using Compiz, let alone by default. That thing is *not* a window manager; it is a mess of useless tech demos, most of which could easily be placed as external applications. With every common window manager now supporting compositing, it no longer serves any purpose whatsoever except to destroy usability on an otherwise top notch desktop. Every time I am reminded that Ubuntu uses Compiz, my blood starts to boil.

Photoshop also had a multi-window interface until very recently, by the way. I believe it still does on the Mac. For that matter, many successful applications on the Mac involve detached windows. I wonder if there is a plugin for GIMP that will fade out its tool windows when the pointer moves off of them, to make the efficiency more apparent for the uninitiated? (Note for Compiz plugin people: That is not a window manager function unless said window manager is content with causing massive breakage).

"Toolbox is too big". This is where GTK really shines. Resize it. Go ahead and resize ANYTHING however you wish.

As for the tabs people:
GIMP uses tabs on its tool windows. You can drag everything as a tab into the same window. At that point you will all realize that window managers really are quite useful tools and that your precious tabs only give you a quarter of the organization a window manager can. Tabs are one dimensional. A window manager like Metacity organizes by x / y position, workspace and depth with something like the window list applet or the window menu applet (or both!) serving quick one-dimensional shortcuts as you please. Cool, eh? You can even choose a window manager other than Metacity, for example a tiled one or a 3D one to get even *more* organization! (No, Compiz is not a 3D window manager but a wad of 3D effects painted on a broken 2D window manager).
Tabs make sense to group similar functions where space is limited and where there would otherwise be a long list with lots of headers. An example of that is different portions of mouse preferences or brush colour / shapes / settings. Tabs do not make sense to divide different things since they only offer a single visual metaphor, which is why one will NEVER see tabs happening throughout GIMP by default.


Finally, may the "doesn't support 24-bit" people please start being more supportive? The 2.6 series is where GIMP *really *starts integrating GEGL. 2.6 itself has a toggle to turn on the experimental GEGL support and a GEGL tool worth playing with. You *have* your 24-bit support; all you have to do now is help out with bug reports and your problems will be solved. I am sure anyone who has been around open source for a reasonable amount of time can understand "release early release often." GIMP follows the philosophy; what you have here is the first release of many, where the GEGL support is going to happen piece by piece. The purpose of this is that when that support is completely finished, the thing will already be stable and "unofficial" extensions will remain intact.
That is, unless all you really want to do is complain, for which you must only ask and I will forward an incredible list of new problems to babble at. It is worth studying, since the only way fancy GEGL stuff won't happen is if a storm of people start spreading doubts to a degree high enough that the GIMP developers give up on the thing and leave you guys with out *any* high end raster image editor.

---

### Post by kyleabaker on 2008-10-02
I really hope this is going to get added to Intrepid. Off to install and start testing..

---

### Post by BwackNinja on 2008-10-02
^-- Nice Post Mr. Picklesworth

Only thing is that I like compiz, mostly just the fluidity and smoothness that comes with wobbly windows and the desktop cube as a smooth movement and showing of direction and position of multiple desktops. Pretty much everything else that comes with compiz fusion is just for show.

Also - I'd guess you're a spacial nautilus user?

---

### Post by smartboyathome on 2008-10-02
> **kyleabaker said:**
> I really hope this is going to get added to Intrepid. Off to install and start testing..

I can almost guarentee it won't due to the devs not wanting to except major version updates with very little testing, as those new versions will usually have fresh bugs as well. They would probably have if they had used GIMP 2.5 in Intrepid, but since they used 2.4.7, and the deadline has passed, it will most likely not be included.

---

### Post by kyleabaker on 2008-10-02
> **smartboyathome said:**
> I can almost guarentee it won't due to the devs not wanting to except major version updates with very little testing, as those new versions will usually have fresh bugs as well. They would probably have if they had used GIMP 2.5 in Intrepid, but since they used 2.4.7, and the deadline has passed, it will most likely not be included.

Would it not be just as easy to start testing it while we are in alpha still and then if it absolutely can't be added due to too many bugs then revert back? It seems like such a loss if it's not added. I'm sure they are very limited right now trying to get things close to finalized soon with Ubuntu 8.10, but GIMP 2.6 looks much better and more usable than 2.4.7 does.

Unfortunately, chances are you are correct, but we can always be optimistic. :D

---

### Post by smartboyathome on 2008-10-02
> **kyleabaker said:**
> Would it not be just as easy to start testing it while we are in alpha still and then if it absolutely can't be added due to too many bugs then revert back? It seems like such a loss if it's not added. I'm sure they are very limited right now trying to get things close to finalized soon with Ubuntu 8.10, but GIMP 2.6 looks much better and more usable than 2.4.7 does.

Unfortunately, chances are you are correct, but we can always be optimistic. :D

We're in beta as of today/tomarrow (depending on where you live). Even the Kernel will be frozen soon. So it has a very small chance to get in, but if you guys want it you can always file a freeze exception to see.

---

### Post by sintacto on 2008-10-02
I just wanted to say i like the way gimp lets you choose everything from a right click (like fluxbox or e17) I find myself with a image on the full screen and right click for most things but still keep keyboard handy for short cuts (zoom,undo,copy, paste etc.so alt+tab is so handy for the menu when i need it.I did have two monitors for a while with one filled with menus and the other for images and back then i still right clicked most of the time. just saying i love the gimp how it is.

---

### Post by Mr. Picklesworth on 2008-10-02
> **BwackNinja said:**
> Also - I'd guess you're a spacial nautilus user?

OMG Bwack, how did you guess?! :P Spatial (special) Nautilus should set a little key in the browser user agent so that people like me get filtered into our own little dreamland forums, or maybe even Interwebs. It would be a good first step towards world peace.

I have to admit I miss the side bar, which is a sad omission, but the way my window size / position is retained for each individual folder really helps the workflow. (And there's another point for floating windows: you can give everything the perfect size to fit your preferences!)
Having said that, I have come to accept tabs in browser applications for the time being since the surrounding layers currently lack a complete infrastructure to replace them (however much I wish they did). It makes complete sense to let the user group together related things, and tabs are useful for bookmarking and whatnot, so consider me totally tabs-friendly. I just don't want them to get lost :)

---

### Post by Twitch6000 on 2008-10-02
For all those wanting to know here is what is new in gimp 2.6-

[http://www.gimpusers.com/tutorials/gimp-2-6-new-features.html](http://www.gimpusers.com/tutorials/gimp-2-6-new-features.html)

---

### Post by Sephoroth on 2008-10-02
> **BwackNinja said:**
> ^-- Nice Post Mr. Picklesworth

Only thing is that I like compiz, mostly just the fluidity and smoothness that comes with wobbly windows and the desktop cube as a smooth movement and showing of direction and position of multiple desktops. Pretty much everything else that comes with compiz fusion is just for show.

Also - I'd guess you're a spacial nautilus user?

Meh, for me CF provides far more functionality (zoom, window tabbing, compositing, window transparency, window rules, etc).

---

### Post by BwackNinja on 2008-10-02
I'm curious, what does compiz fusion provide that other window managers don't that can be classified as "functionality" rather than "eye-candy"? I can't really think of any beyond the accesibility plugins.

---

### Post by nanog on 2008-10-02
The very limited gegl implementation in gimp 2.6 does not handle 16 bit images. I will donate a vast sum of money to gimp the minute they support 16 and 24 bit. Until then I have cinepaint (dropped by ubuntu) and photoshop.

---

### Post by Sephoroth on 2008-10-02
[quote=BwackNinja]I'm curious, what does compiz fusion provide that other window managers don't that can be classified as "functionality" rather than "eye-candy"? I can't really think of any beyond the accesibility plugins.[/quote]

I had said some of the things in my post.  Zoom (on both the screen level and the "around the mouse" modes), window tabbing, compositing, window transparency, window rules, live previews, "scale" (layout all windows on current workspace), expose (view all workspaces at once), freewins (the ability to modify the x, y, and z coordinates as well as zoom level of windows), etc.

I added two more to that list which I commonly use.  Unfortunately I'm not at my computer so I'm having a hard time remembering what other features unrelated to eye candy there is.

---

### Post by BwackNinja on 2008-10-02
Zoom is an accessibility plugin. Window tabbing is a legitimate answer. Compositing and window transparency can be done by metacity. Window rules is legitimate. Live previews are nice, scale too (though I don't use that). Expose I'd say half, desktop switcher applet does some of the functionality like moving windows between workspaces, but not as well or smoothly. I haven't yet had much use for freewins, but with input redirection I guess it would be useful with some getting used to.

From this list, I'd say 5/9, though it should be 4.5/9 because freewins isn't in the compiz that comes with ubuntu.

CF has a big focus on eyecandy, basically that's why things are toned down in the default ubuntu config. Now compare that to the list of plugins there just to look pretty... :D

@Mr. Picklesworth the "/" key is wonderful. You get to type in a path and it opens in a new window (which I'm sure you already knew) and takes away the one little annoyance that might come from lack of a path bar. I'm a spatial nautilus user too. I used to be gung-ho on tabs for nautilus, but an essay made me try spatial :P. My favorite feature is that the scrollbar is right where you left it.

---

### Post by autocrosser on 2008-10-02
Been a while from the badger.....How many of the lads caught it?


> **jfernyhough said:**
> Quick screeny for you. Guess how long I've had that particular image for? :)

It feels quite a bit nippier than 2.4.1.

---

### Post by olskar on 2008-10-02
wrong post

---

### Post by talkingwires on 2008-10-02
> **Mr. Picklesworth said:**
> ...since the only way fancy GEGL stuff won't happen is if a storm of people start spreading doubts to a degree high enough that the GIMP developers give up on the thing and leave you guys with out *any* high end raster image editor.Judging by how they've carefully listened to and quickly addressed our complaints over the past *ten years*, then we have nothing to worry about. /sarcasm

---

### Post by knarf on 2008-10-02
Instead of {implementing|waiting for someone to implement} fading toolbox windows you can use the Gnome panel with the Swallow applet to create auto-hiding toolbox windows. An [updated version of a script I made for this purpose is attached to the latest addition to the howto]("http://ubuntuforums.org/showthread.php?p=5892195#post5892195").

---

### Post by bash on 2008-10-02
> **talkingwires said:**
> Judging by how they've carefully listened to and quickly addressed our complaints over the past *ten years*, then we have nothing to worry about. /sarcasm

I wonder who reacts quicker to their users, the GIMP developers or the Pidgin one. I think it would be a close one. (Offtopic)

---

### Post by olskar on 2008-10-02
GIMP-developers was offered money by Mark in 2004 (30000 dollar) to  make gimp better, among the things he asked for was GEGL implementation. Four years ago!

[http://www.mail-archive.com/gimp-developer@lists.xcf.berkeley.edu/msg06268.html](http://www.mail-archive.com/gimp-developer@lists.xcf.berkeley.edu/msg06268.html)

[http://dneary.free.fr/gimp_bounties.html](http://dneary.free.fr/gimp_bounties.html)

---

### Post by plun on 2008-10-02
About grouping all Gimp Windows together.  (Compiz challenge)


- Start ccsm

- Enable > "Enable Group and Tab Windows"


- Start Gimp  


-  **Super + s ** on each Gimp window


-  **Super + g**  for grouping these windows


Done....  Gimp main window now minimizes all 3 Windows


But howto save this group.....:confused: :D


EDIT

**Super + t **gives more features

---

### Post by meborc on 2008-10-02
> **talkingwires said:**
> Try using it on a laptop with a 1024x768 screen. The toolboxes and palettes take up half the screen.It's not a matter of wanting it to work like the Windows version of Photoshop, but it needs to have a sane interface.

i don't want to fight, but you have got to see my point :D ... for me it works... for you it does not...

so i am very sorry, but you can't just say that the gui must change the way YOU want it to be... what about me? :D i love it like it is... if the gui gets changed, i will be angry as you are now and you would be happy

:D so you see, the gimp devs chose the way to go with the gui, the gimpshop devs chose another... some like it, some don't... you can't expect everyone to like it?

---

### Post by Sephoroth on 2008-10-02
> **BwackNinja said:**
> Zoom is an accessibility plugin. Window tabbing is a legitimate answer. Compositing and window transparency can be done by metacity. Window rules is legitimate. Live previews are nice, scale too (though I don't use that). Expose I'd say half, desktop switcher applet does some of the functionality like moving windows between workspaces, but not as well or smoothly. I haven't yet had much use for freewins, but with input redirection I guess it would be useful with some getting used to.

From this list, I'd say 5/9, though it should be 4.5/9 because freewins isn't in the compiz that comes with ubuntu.

CF has a big focus on eyecandy, basically that's why things are toned down in the default ubuntu config. Now compare that to the list of plugins there just to look pretty... :D

@Mr. Picklesworth the "/" key is wonderful. You get to type in a path and it opens in a new window (which I'm sure you already knew) and takes away the one little annoyance that might come from lack of a path bar. I'm a spatial nautilus user too. I used to be gung-ho on tabs for nautilus, but an essay made me try spatial :P. My favorite feature is that the scrollbar is right where you left it.

I use GIT builds so whether it is included with Ubuntu or not is irrelevant to me XD.  I forgot to mention.  Another feature I've been using more lately is window ghosting.  The negative plugin has been helpful a few times but those were rather uncommon occurrences (taking a screen shot of a negative of a negative) XD.  I occasionally use firepaint to write notes on my desktop (I don't use screenlets/desklets for some reason).  The last one I remember right now is binds for custom commands; I don't remember if one can create binds for such custom commands in GNOME or Metacity.

Even plugins that are highly aesthetic can provide functionality.  The prime example I can think of is wobbly windows as it can be configured to allow you to "throw" windows.  That brings up the other benefit of CF.  Even if certain features are present elsewhere, they are rarely as easily configurable as in Compiz and allowed for by CCSM.

The eye candy has also been helpful in its own ways.  Besides being aesthetically pleasing for me, it prevents other people who use my computer form complaining about Linux being present :lolflag:.

@Plun, I've never really needed to save such configs but can't you just dedicate all GIMP windows to one desktop and then group/tab each image you open manually (a mouse click and 2 binds)?  I know one can trigger programs to open on certain work spaces.

---

### Post by ssam on 2008-10-02
> **olskar said:**
> GIMP-developers was offered money by Mark in 2004 (30000 dollar) to  make gimp better, among the things he asked for was GEGL implementation. Four years ago!

[http://www.mail-archive.com/gimp-developer@lists.xcf.berkeley.edu/msg06268.html](http://www.mail-archive.com/gimp-developer@lists.xcf.berkeley.edu/msg06268.html)

[http://dneary.free.fr/gimp_bounties.html](http://dneary.free.fr/gimp_bounties.html)

If bounties dont work maybe employment is a better method. are any of the gimp devs employed by a distro? do they all do gimp stuff only in their spare time? i am sure 30k would pay for 6 months or a year of developer time.

the FOSS community could easily raise 30k for this sort of thing if canonical did not want to pay.

---

### Post by Mr. Picklesworth on 2008-10-02
> **olskar said:**
> GIMP-developers was offered money by Mark in 2004 (30000 dollar) to  make gimp better, among the things he asked for was GEGL implementation. Four years ago!

[http://www.mail-archive.com/gimp-developer@lists.xcf.berkeley.edu/msg06268.html](http://www.mail-archive.com/gimp-developer@lists.xcf.berkeley.edu/msg06268.html)

[http://dneary.free.fr/giamp_bounties.html](http://dneary.free.fr/giamp_bounties.html)

Politics hurt.
However, at this point they *are* working on GEGL, and that is what this version is all about! Yes, it takes time to make a massive under the hood modification to an enormous piece of software. Saying "it takes too long" when progress is obviously being made seems a little bit rude, though.

---

### Post by Bou on 2008-10-02
Wow, I filed a [request]("http://bugzilla.gnome.org/show_bug.cgi?id=554613") and a developer actually sent me to hell.

---

### Post by meborc on 2008-10-02
> **Bou said:**
> Wow, I filed a [request]("http://bugzilla.gnome.org/show_bug.cgi?id=554613") and a developer actually sent me to hell.

i see your point... but he didn't actually send you to hell, did he now :D ... well, he did, but really diplomatically... i got the impression he was more sarcastic then trying to be rude

---

### Post by Bou on 2008-10-02
> **meborc said:**
> i see your point... but he didn't actually send you to hell, did he now :D

Well, sorta.

---

### Post by Hairy_Palms on 2008-10-02
theres an option in the 2.5.4 development release to make the windows transient, its gone in 2.6.0, boo :( ill stick with 2.5.4 for now i think :(

---

### Post by olskar on 2008-10-02
Check out [http://www.gimphoto.com](http://www.gimphoto.com) if you want, way better then gimpshop and I heard that work on 2.6 version is being done

Edit: Or don't :)

---

### Post by Hairy_Palms on 2008-10-02
i found gimphoto a horrible hack imo, if you want the docks to be as promising as they looked, run 

> echo "(transient-docks yes)" >> ~/.gimp-2.6/gimprc

now the toolbox and the docsk should stay above the image window and have no taskbar entry and minimise with together :)

---

### Post by CarpKing on 2008-10-02
[This post](http://ubuntuforums.org/showthread.php?p=5892503#post5892503) indicates that GIMP's utility windows should now behave the same in Metacity and Compiz from git.

---

### Post by talkingwires on 2008-10-03
> **Bou said:**
> Wow, I filed a [request]("http://bugzilla.gnome.org/show_bug.cgi?id=554613") and a developer actually sent me to hell.That was a perfectly reasonable request, but the response wasn a bit harsh. Oh, and that little image in the toolbar was the first thing I noticed. "Hey they final got rid of the redundant menubar and freed up some space! Oh, wait."

---

### Post by alienexplorers on 2008-10-03
Running it now and it works like a champ.

---

