---
title: "Koala+1 &amp; Gnome 3"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by vaibhav on 2009-04-05
Hi,

How will the Gnome 3 development affect Koala+1? I suppose Koala+1 would be LTS. KDE 4 was released during previous LTS which caused lots of problems (deciding which version to ship). So just wondering, given the major changes in Gnome 3 and stability requirement for an LTS, seems tough times for Koala+1?

---

### Post by gnomeuser on 2009-04-05
GNOME 2.30 will be the first candidate for renaming to GNOME 3.0, however if it is not deemed to be up to snuff then the renaming gets pushed back (e.g. we could have a major problem getting GTK3 out or the overall feature set might not be as desired just yet). In that case 2.32 becomes the 3.0 candidate. 

As for the influence on Koala and Koala+1, it's mainly upstream work which Canonical aren't contributing much to, the process is evolutionary as it's the platform we know and love with changes that have been underway a long time. So for you the user, expect these cycles to feel the same, though you get the chance to see new interface ideas like the GNOME shell run in parallel with the desktop shell you have today. 

GNOME 3 is not going to be one huge step, it is an evolutionary improvement across the board as well as setting us up for the next maybe 4-5 years of the desktop. It is going to incrementally improve over it's lifetime just like the GNOME 2.x cycle allowed us.

---

### Post by olskar on 2009-04-05
What I have seen from Gnome Shell so far looks terrible :(

[http://live.gnome.org/GnomeShell/Screenshots](http://live.gnome.org/GnomeShell/Screenshots)

---

### Post by MacUntu on 2009-04-05
> **olskar said:**
> What I have seen from Gnome Shell so far looks terrible :(
Indeed.

---

### Post by go7Ul1ai on 2009-04-05
Anyway I can run the devel version of GNOME Shell?

---

### Post by olskar on 2009-04-05
> **lee.jarratt said:**
> Anyway I can run the devel version of GNOME Shell?

Yep, [http://live.gnome.org/GnomeShell#building](http://live.gnome.org/GnomeShell#building)

---

### Post by go7Ul1ai on 2009-04-05
> **olskar said:**
> Yep, [http://live.gnome.org/GnomeShell#building](http://live.gnome.org/GnomeShell#building)

Thanks man :)

---

### Post by issih on 2009-04-05
On the assumption that it will be skinnable, so that the look is a bit irrelevant, I think the user interface ideas of gnome shell are pretty interesting...

Not sure I like the menu layout with the more button, but then I guess most of the time launching would be done by something more akin to do or deskbar.

I'm certainly not writing it off yet.

---

### Post by gnomeuser on 2009-04-05
> **issih said:**
> On the assumption that it will be skinnable, so that the look is a bit irrelevant, I think the user interface ideas of gnome shell are pretty interesting...

Not sure I like the menu layout with the more button, but then I guess most of the time launching would be done by something more akin to do or deskbar.

I'm certainly not writing it off yet.

GTK3 will have a very powerful theming system, I believe the plan is to allow the use of CSS to do much of it. Aside that we are in early alpha, don't expect it be polished yet there are many areas that haven't yet gotten any attention. Finally you should try it once it is ready for testers and then judge it, going by some mockups and screenshots is not a very good reference for an interactive UI.

It is written mainly in JavaScript so I assume it will be extendable in all manners of fun ways. I look forward to seeing where people take it, even if personally I would have preferred something done in Silverlight.

---

### Post by issih on 2009-04-05
Mostly I just watched the video mockups... I like a lot of the ideas, and I have no doubt it will be highly theme-able and extend-able.

In particular I like that it is moving away from the current paradigm somewhat. Its nice to see something new come along.

Hopefully it will introduce new ideas and ways of using the desktop, either way, its good that you guys are being bold.

---

### Post by autocrosser on 2009-04-05
OK--I have it built & I must say that I think it's quite cool---I'll try to get a screenshot & put together a script to make it work a bit nicer....

Just a note---make sure that you do the Control-c in the term window that you started the app in....you will be left with no Nautilus or gnome-panel if you don't :)

---

### Post by BwackNinja on 2009-04-05
Tried Gnome-shell on and off over the past few days. RGBA isn't working for me though I'd normally expect it to. I also wish I could find some way to configure some aspects of it, the things that bug me are:

-It is difficult for me to use my own bottom panel (I use an xfce4-panel)

-The animations, though smooth, are a bit on the slow side - I'd just like a speed increase there.

-The top bar is a bit thick... I tend to go a bit minimal.

-The new alt+f2 run application dialog is nice and transparent, but rounded corners would be nice.

All in all though, it works well and gets the job done in a clean way that makes sense, and I'm sure (given the amount of time left) that this will be polished and able to work how most people would want. Sorta debating on whether I'm okay with the such integration of the window manager and desktop environment.

---

### Post by autocrosser on 2009-04-05
Yes--I can't wait until it can be configured more---it looks ok right now but not great--I'm not having problems with speed, but my system is up-to-date--i7 920 & 6G of ram. I can't use my lower panel either :( & it would be nice to custom-choose the main apps that show up first.....

All-in-all, it shows promise & I think it is a good direction to go.

---

### Post by plun on 2009-04-06
> **autocrosser said:**
> 

All-in-all, it shows promise & I think it is a good direction to go.

Yup... tested and it works.

A **compiz-clutter** backend is on my wish-list....):P:-$:twisted:

edit
and removing of the lower panel....terrible, AWN or Gnome-do...

---

### Post by raggari on 2009-04-06
> **olskar said:**
> What I have seen from Gnome Shell so far looks terrible :(

[http://live.gnome.org/GnomeShell/Screenshots](http://live.gnome.org/GnomeShell/Screenshots)

You are looking wrong link. It actually looking very promising:
[http://live.gnome.org/GnomeShell/Screencasts](http://live.gnome.org/GnomeShell/Screencasts)

---

### Post by uBeer on 2009-04-06
Wow, that looks kinda cool!
With at least a year to straighten is out it is gonna be an interesting new way of working with a desktop.

---

### Post by gnomeuser on 2009-04-06
> **uBeer said:**
> Wow, that looks kinda cool!
With at least a year to straighten is out it is gonna be an interesting new way of working with a desktop.

I am worried about one thing. It seems very focused on managing workspaces and yet they haven't really shaped out how workspaces should fit into peoples work patterns in this new world. Looking at how I use them currently it's "not at all". I don't put things else where since I keep relatively few programs open at one time and moving them to other places leads to the path to my work being longer and I tend to forget that I have things open.

I know they have some ideas in this space but I am not convinced it is fundamentally the right approach. I will have to play extensively with it to be won over. I do like the simplification though, but I am more a fan of the task oriented interface than the application oriented one we have now. I have some idea in this space but nothing fully formed.

---

### Post by Incognito-Here on 2009-04-06
> You are looking wrong link. It actually looking very promising:
[http://live.gnome.org/GnomeShell/Screencasts](http://live.gnome.org/GnomeShell/Screencasts)
don't think so. Looks inconvenient and unpredictable. I mean with current Apllications-Places-System you always know where to find things. I'm sure it's a daydreaming and lead to failure. Have no doubt about it. It's sad.

---

### Post by Yashiro on 2009-04-06
This is a plot to move us all to KDE isn't it?

---

### Post by Taiebot65 on 2009-04-06
What about all the little project who are actually based on gnome 2.0 one of the compiz developper is already talking about leaving the gnome desktop developpement

> 
Maybe it's finally time we put some serious consideration into a Compiz Desktop Environment. With GNOME pretty much throwing us aside on support and with KWin replicating our features left and right, it's hard to stay on board. This all comes on top of the numerous issues we've always had with the two big ones.
So, I figure it's time we look a bit bigger. As 0.9.0 starts to build back to the status of 0.8.* in plugins, we should look at things we need to build a solid, effect-filled DE. Sam mentioned the possibility of forking GNOME, but do we really want to go that route? I can see the backend systems in GNOME being reused in the "CompDE", but I don't see us forking their panel and desktop: we don't need to. Compiz has always been an add-on to existing DEs, and we need to consider that: We can build the basics, we already have. We have numerous panels, and we're working on a deskop. The rest is integration systems.

Hm. I'm limited on time here, so I need to wrap it up. I'll try and make a more suitable argument later when I have time.


---

### Post by Merk42 on 2009-04-06
> **Incognito-Here said:**
> don't think so. Looks inconvenient and unpredictable. I mean with current Apllications-Places-System you always know where to find things. I'm sure it's a daydreaming and lead to failure. Have no doubt about it. It's sad.

Because you're used to it.

This is really the same 'problem' with Windows 7 (and I guess years ago from Mac OS 9 to OS X).  There are people that will be dissatisfied with ANYTHING because it isn't what they're used to.

---

### Post by zekopeko on 2009-04-06
the only thing that bugs me is my perception that Gnome Shell is pretty closed off for 3rd party addons. and i don't mean the ones that are going to be made for gnome shell but the ones we have today.

a number of people here said that they have problems with adding their favorite panel/dock to gnome shell. and the week earlier there was that compiz situation.

---

### Post by ELD on 2009-04-06
I think it looks fracking terrible, i don't see why they need radical changes, make small decent changes to the already stable and decent gnome.

Besides i don't use those spaces, i have never seen a need for them ugh.

---

### Post by Incognito-Here on 2009-04-06
> Because you're used to it.
they are very usefull when you are working with many windows, but some of them are uses rarely and some are often. The proposed concept brings nothing to the current state, because it brings additional complexity to the user - navigating through variable "activities", while with workspaces you are stick to the specific layout. EG I always have two terminals in workspace #2, Evolution at the #3, Firefox and Emacs at #1, as well as the constantly launching and closing apps. #4 usually use for the apps that should work a long time.

---

### Post by pulpo69 on 2009-04-06
i would like to work with different workspaces in gnome, but it's annoying
that all workspaces have the same background. i don't want different backgrounds as eyecandy, but for orientation it's useful (for knowing in which workspace you are).

---

### Post by Incognito-Here on 2009-04-06
> Because you're used to it.
I'm not. I easily adopts to new **good** things. For example, I easily switched to Linux from windows, because found out gnome is much better than windows DE. But I don't think this approach is a good one. See explanation above. In addition, I can't see any suitable and convinient way to control these things from the keyboard.

---

### Post by Incognito-Here on 2009-04-06
> i would like to work with different workspaces in gnome, but it's annoying
that all workspaces have the same background. i don't want different backgrounds as eyecandy, but for orientation it's useful (for knowing in which workspace you are).
You are too captious. The fact you see background in the workspace means you shouldn't switch to another one. I haven't even noticed this thing before (and won't pay any attention after).

---

### Post by BwackNinja on 2009-04-06
Regardless of whether or not having different backgrounds is useful, it shouldn't be a limitation, especially when multiple things already allow you to have them.

I think that they mentioned multiple wallpapers at least as comments on the wiki.

Compiz has spoiled me with so much configuration :3

---

### Post by Merk42 on 2009-04-06
I'm not too familiar with workspaces, but I don't see how you couldn't accomplish your setup on the GNOME 3 shell.

Also, how do you navigation workspaces now via keyboard and how would what has been shown of GNOME 3 be any different?

---

### Post by vaibhav on 2009-04-06
Seems Gnome-Shell is a getting quite a bit of negative feedback from users. I hope the things get sorted out before any major changes are force onto the users. User is king. Developers, please listen to the users. If Gnome-Shell is not giving any significant improvement in usability, there is no reason to have a significant effort for developers and change of paradigm from user's perspective.
Gnome 2 is solid. Gnome 2 is stable. Gnome 2 rocks. Gnome 2 users will have HIGH expectations from Gnome 3. Please give the users what they deserve.

---

### Post by Incognito-Here on 2009-04-06
I know I have firefox at #1. I press Ctrl+Alt+1. I want to see what's happening at the terminal: just pressing Ctrl+Alt+2, etc. But gnome-shell replace the concept of workspace with more general concept of "activity". But more general doesn't mean better, especially in this case, the usecase doesn't need activity, the workspace is quite enough. And since there are no fixed activities, I don't know exactly where to switch to find my terminals. I need to use mouse to look throught activities. It's fuck1ng annoying - if I have my hands on the keyboard, it's inefficient to move them to the mouse. The same situtation with moving hand from mouse to keyboard: old good gnome menu has very clear structure, so I don't need to input any filter string to find Empathy - I'm just going Applications->Internet->Empathy. But they suggest: move mouse to the "activity", click, then move hands to the keyboards and begin to input Empathy - it's just stupid. This guys from gnome didn't pass really usefull, but simple things, like split windows, nautilus split view, etc with explanation that is "too hard for average user". But now they are preparing to introduce things without any premature research. The worst thing is this research proved the idea is sh1t.
So, I'm upset: these guys instead of making simple things that would significantly improve desktop experience (I said what would they are: split windows in windows manager, split view nautilus mode, performance), they are getting into daydreaming. I'm afraid they would even include strange notify-osd into upstream :(

---

### Post by uBeer on 2009-04-06
So basically what you're saying is that right now your keyboard shortcuts don't work.

I think that this menu/panel/thingy will listen to something like Alt-F1 (when more finished: right now it's pre-alpha!) and if you then type "ep" right away and press enter you'll probably launch an Epiphany window and in that it'll become a bit like Gnome-do: which is awesome! That would seem like a logical step to me.

So I think there's still hope for this new thing.

And if it doesn't work I'll just have Gnome-do to assist me in everything that I want to do :D

---

### Post by Reiger on 2009-04-06
First thing I thought was that it looked (also in intended feature set) a *lot* like Kicker (the KDE) menu, with a pager added for bonus points. (OK, that's not entirely fair because those of us who do use workspaces or desktops or whatehaveyouhereinplural will see the benefits).

---

### Post by autocrosser on 2009-04-06
OK--I've muddled thru a couple of things--try launching the shell with /home/(your_home)/gnome-shell/install/bin  instead of the /source/gnome-shell/src....that way you can modify the .js files that are at /gnome-shell/install/share/gnome-shell/js/ui. I changed the appDisplay.js file--very early on is the .desktop files--you will find several that won't work in Ubuntu & you can just look in your usr/share/applications for the ones you really want.  Next I modified the panel.js file--changed the default name to "Applications" instead of "Activities" & reduced the panel sizes.... I'll get a screenshot within the next couple of minutes...

Still don't know why the tray icons don't display...need to look more at the "tray-manager"

---

### Post by Methuselah on 2009-04-06
> **Yashiro said:**
> This is a plot to move us all to KDE isn't it?

Really!?
I thought all the KDE users had thrown a hissy fit and left after KDE4.
Maybe the people who are resistant to change should move to wm2 or some 
other stagnant project where no development is going on and nothing will ever change.
Meanwhile the KDE4 series continues to improve and all the angst proved unnecessary.

Aside: while I think KDE is a fine desktop I always dislike how it 'feels'.
It's very difficult to describe but it feels cold to me.
I always find myself returning to gnome or xfce.
Changes to gnome and GTK excite me.

---

### Post by plun on 2009-04-07
> **autocrosser said:**
> OK--I've muddled thru a couple of things--try launching the shell with /home/(your_home)/gnome-shell/install/bin  instead of the /source/gnome-shell/src....that way you can modify the .js files that are at /gnome-shell/install/share/gnome-shell/js/ui. I changed the appDisplay.js file--very early on is the .desktop files--you will find several that won't work in Ubuntu & you can just look in your usr/share/applications for the ones you really want.  Next I modified the panel.js file--changed the default name to "Applications" instead of "Activities" & reduced the panel sizes.... I'll get a screenshot within the next couple of minutes...

Still don't know why the tray icons don't display...need to look more at the "tray-manager"


Nice....and thanks.;)


I have no experience with jhbuild and is this a static build ??

If not how is it updated  ???

Normal procedure for SVN is just a "svn up" and then recompile.

---

Its better to run it then just discuss...):P

---

### Post by FuturePilot on 2009-04-07
> **plun said:**
> Nice....and thanks.;)


I have no experience with jhbuild and is this a static build ??

If not how is it updated  ???

Normal procedure for SVN is just a "svn up" and then recompile.

---

Its better to run it then just discuss...):P

Yep, it's a static build and everything is installed into a directory in your home directory. Nothing is installed into the system.

---

### Post by plun on 2009-04-07
> **FuturePilot said:**
> Yep, it's a static build and everything is installed into a directory in your home directory. Nothing is installed into the system.

Yes I know how it is installed. I am running GnomeShell.

What I was trying to figure out was if this build goes to a SVN repo which is updated.

Just to avoid building everything from scratch every time.

But maybe the jhbuild script does that "automagic", have not tested ;)

---

### Post by FuturePilot on 2009-04-07
> **plun said:**
> Yes I know how it is installed. I am running GnomeShell.

What I was trying to figure out was if this build goes to a SVN repo which is updated.

Just to avoid building everything from scratch every time.

But maybe the jhbuild script does that "automagic", have not tested ;)

Oh I see. Sorry I misunderstood your question ;)
But I don't have an answer to it :(

---

### Post by plun on 2009-04-07
> **FuturePilot said:**
> Oh I see. Sorry I misunderstood your question ;)
But I don't have an answer to it :(

Well... I have  ;)

This works

```
plun@plun:~/gnome-shell$ jhbuild build
```


Everything seems to be done automagic.....

If something is broken:

```
jhbuild build -f -a -c

```


Testing....;)

---

### Post by autocrosser on 2009-04-08
Plun---there is a problem with todays build---there is a new add-on that should go in /gnome-shell/install/share/gnome-shell/js/ui that is not being pulled from the build side...look for gtkutil.js in /gnome-shell/source/gnome-shell/js/ui & copy/paste it to the install side for things to run right....also, if you have made custom files of appDisplay.js & panel.js, you will need to modify the new files--the old ones are missing data....I did the mods to the new stuff & it is working very nice.......

There is now a "real" applications menu that can be accessed--see screenshot.  Still a few bugs in it (line stays highlighted after it has been clicked on--but showing progress!!!)

---

### Post by macvr on 2009-04-09
> **pulpo69 said:**
> i would like to work with different workspaces in gnome, but it's annoying
that all workspaces have the same background. i don't want different backgrounds as eyecandy, but for orientation it's useful (for knowing in which workspace you are).

u can use _wallpapoz_ >>> it allows u to have different wallpapers for different desktops

---

### Post by Mr. Picklesworth on 2009-04-09
Bear in mind, please, that this is early in development and basically an experiment with reusable code at this point in time.

Also, Compiz never had anything to do with GNOME; it's a window manager, which worked nicely with GNOME 2 because the window manager was a detachable module but less likely to be useful in GNOME 3 since the window manager is being closer tied to the rest of the platform.

---

### Post by Reiger on 2009-04-09
Which means that Metacity 3 (or whatever it will be called) will in every respect be more like KWin?

---

### Post by plun on 2009-04-09
> **autocrosser said:**
> I did the mods to the new stuff & it is working very nice.......

There is now a "real" applications menu that can be accessed--see screenshot.  Still a few bugs in it (line stays highlighted after it has been clicked on--but showing progress!!!)

Okidok...

Where is the lower panel controlled ?....I cannot find it..blind ?:oops:

AWN works just fine and its perfect for controlling my favorite apps so this panel must be thrown out..):P

---

### Post by autocrosser on 2009-04-09
Not sure--I would start looking thru the panel.js file...am going to work, so I can't look until this evening.....

---

### Post by JPorter on 2009-04-09
> **olskar said:**
> What I have seen from Gnome Shell so far looks terrible :(

[http://live.gnome.org/GnomeShell/Screenshots](http://live.gnome.org/GnomeShell/Screenshots)

You realize that that's the new workspace switcher view, and not the main interface, right?

---

### Post by autocrosser on 2009-04-11
Plun---I got a reply back from one of the Gnome developers (SHOCK!!) and the lower panel is hard-coded right now--so we can not change it until the shell is more mature---

I'm going to keep this updated as I get more info---

The reply looks like:

Hey!

I moved the expanded view mockups to
[http://live.gnome.org/GnomeShell/DesignerPlayground/ExpandedViewMockups](http://live.gnome.org/GnomeShell/DesignerPlayground/ExpandedViewMockups)
because as Jon pointed out they were not discussed at the hackfest. These mockups were instrumental in implementing the expanded view for applications and documents, but we are currently not using the scrollbar that is shown on them, and are doing paging instead.

Dean, lower panel is hard-coded at present, but it is our goal to replace it with something more convenient and interesting. There are no current plans for how we'll be able to allow different panel types, add-ons, or incorporate GNOME Do, but this will be addressed in the future.

We'd like to enable having a different wallpaper for each desktop. Here is a mockup from Brian Fleeger that captures the idea:
[http://www.flickr.com/photos/26671354@N05/3334338024/sizes/o/in/photostream/](http://www.flickr.com/photos/26671354@N05/3334338024/sizes/o/in/photostream/)

While no work has been done so far to enable different wallpapers, the idea from this mockup to use a zoomed in and fuzzed out wallpaper image for the overlay wallpaper is currently being implemented by Sander Dijkhuis:
[http://bugzilla.gnome.org/show_bug.cgi?id=578584](http://bugzilla.gnome.org/show_bug.cgi?id=578584)

You can definitely file bug reports in Bugzilla or add your design ideas to the wiki. You can also use the IRC channel to get quick feedback about the bugs you are encountering.

Thanks,
Marina

---

### Post by plun on 2009-04-11
> **autocrosser said:**
> Plun---I got a reply back from one of the Gnome developers (SHOCK!!) and the lower panel is hard-coded right now--so we can not change it until the shell is more mature---

I'm going to keep this updated as I get more info---



Thanks autocrosser, I wasnt "blind"...;)

Well... these gnome-boys and girls and hard-coding....:^o


I think AWN is the best choice....):P

---

### Post by autocrosser on 2009-04-11
Plun---doing some reading, there is another branch of Gnome-Shell that is "allowing" separate wallpaper per space--look at:  [http://github.com/sander/gnome-shell/tree/wallpaper](http://github.com/sander/gnome-shell/tree/wallpaper)

I'm giving it a whirl to see how it works...............

---

### Post by plun on 2009-04-11
> **autocrosser said:**
> Plun---doing some reading, there is another branch of Gnome-Shell that is "allowing" separate wallpaper per space--look at:  [http://github.com/sander/gnome-shell/tree/wallpaper](http://github.com/sander/gnome-shell/tree/wallpaper)

I'm giving it a whirl to see how it works...............


Huh !!... a fork directly.. ;)


Testing.

---

### Post by autocrosser on 2009-04-11
> **plun said:**
> Thanks autocrosser, I wasnt "blind"...;)

Well... these gnome-boys and girls and hard-coding....:^o


I think AWN is the best choice....):P


Have never tried AWN (might give it a try soon)---I use a really modded standard panel & was hoping to just use it instead of the (bad) panel that comes with......pity that it is hard-coded, but it looks like that will change---I hope very soon!!!!!;)

---

### Post by plun on 2009-04-11
> **autocrosser said:**
> Have never tried AWN (might give it a try soon)---I use a really modded standard panel & was hoping to just use it instead of the (bad) panel that comes with......pity that it is hard-coded, but it looks like that will change---I hope very soon!!!!!;)

OK....
```

sudo apt-get install avant-window-navigator
```

Awn&#347; creator NeilJPatel has been involved in this new look.

[http://www.markshuttleworth.com/archives/223](http://www.markshuttleworth.com/archives/223)

;)

---

### Post by phaed on 2009-04-11
I keep getting a bunch of errors during build like:

> *** error during stage configure of gnome-shell: ########## Error running ./autogen.sh --prefix /home/martin/gnome-shell/install --libdir '${exec_prefix}/lib'  --disable-static --disable-gtk-doc  *** [6/6]

*** error during stage clean of gnome-shell: ########## Error running make   clean *** [6/6]

make: *** No rule to make target `install'.  Stop.
*** error during stage install of gnome-shell: ########## Error running make install *** [6/6]

---

### Post by autocrosser on 2009-04-12
It is likely that the build is "barfed-up" this evening---it is pre-alpha & sometimes comits will cause a cascade of problems---I'll look & see if it is build-able this evening or tomorrow morning---currently doing system cleanups in prep for Karmic.......

---

### Post by autocrosser on 2009-04-12
Hmmmm.... there have been no comits for about 3 days & I got a clean build (have built it on both 32 & 64 bit)--Do you have all the depends for it? I got python-all & python-dev-all just to make sure...You also might try running the install with   jhbuild build -f -a -c  just to make sure...

---

### Post by plun on 2009-04-12
> **autocrosser said:**
> Hmmmm.... there have been no comits for about 3 days & I got a clean build

Yup the same for me....

```
plun@plun:~/gnome-shell$ jhbuild build
*** Checking out gobject-introspection *** [1/6]
git fetch
git stash save jhbuild-build
No local changes to save
git checkout
git rebase origin master
Already on "master"
Current branch master is up to date.
*** Skipping gobject-introspection (not updated) *** [1/6]
*** Checking out gir-repository *** [2/6]
git fetch
git stash save jhbuild-build
No local changes to save
git checkout
git rebase origin master
Already on "master"
Current branch master is up to date.
*** Skipping gir-repository (not updated) *** [2/6]
*** Checking out clutter *** [3/6]
git fetch
git stash save jhbuild-build
No local changes to save
git checkout
git rebase origin master
Already on "master"
Current branch master is up to date.
*** Skipping clutter (not updated) *** [3/6]
*** Checking out metacity-clutter *** [4/6]
git fetch
git stash save jhbuild-build
No local changes to save
git checkout clutter
Already on "clutter"
git rebase origin/clutter clutter
Already on "clutter"
Current branch clutter is up to date.
*** Skipping metacity-clutter (not updated) *** [4/6]
*** Checking out gjs *** [5/6]
git fetch
git stash save jhbuild-build
No local changes to save
git checkout
git rebase origin master
Already on "master"
Current branch master is up to date.
*** Skipping gjs (not updated) *** [5/6]
*** Checking out gnome-shell *** [6/6]
git fetch
git stash save jhbuild-build
No local changes to save
git checkout
git rebase origin master
Already on "master"
Current branch master is up to date.
*** Skipping gnome-shell (not updated) *** [6/6]
***** success *** [6/6]**

```

---

### Post by autocrosser on 2009-04-12
I've got some very good responses back from a couple of devs with gnome-shell---looks like they are interested in feedback...somewhat surprised (and a bit pleased) about that---I've made a bug report about the gtkutil.js & notified about the new menu hanging onto highlights---IF you could goto  [http://bugzilla.gnome.org/show_bug.cgi?id=578776](http://bugzilla.gnome.org/show_bug.cgi?id=578776)  & confirm my bug (if you have a bugzilla account), it would help move things along....

---

### Post by phaed on 2009-04-12
I figured out what was wrong.  I had installed jhbuild and was running "jhbuild build" instead of "./jhbuild build" in the bin directory.  This time it was built without errors.

That should probably be changed or made more clear on this page:

[http://live.gnome.org/GnomeShell](http://live.gnome.org/GnomeShell)

---

### Post by autocrosser on 2009-04-13
HI guys!!!

If you look at the commits for the last 8 hours--both of the bugs I commented on have been fixed....Now we need to get them to make allowances for something other than the hard-coded lower panel............;)

---

### Post by phaed on 2009-04-13
BTW, is Gnome Shell supposed to be functional at all right now?  I got it built, but when I tried to use it, whenever I opened an application, I could see a white outline of where the window was supposed to be, but that's it.  I didn't see the application and I couldn't interact with it.

---

### Post by autocrosser on 2009-04-14
Try dragging the app to one of your desktops--that desktop will maximize with the app at front-- Also create several desktops and work with them-- I'm getting a "normal" set for desktops--just a different way to interact with them. 

If you can't use it--there most likely is a bug that has showed up with your hardware..get a account at bugzilla and describe what you are having a problem with & take a close look at your term output--there may be clues as to the problem---I normally take a snip of the term output and include it---you might change the default number of lines that term will record--edit your default profile and increase the scrolling scrollback amount---I normally set it for 1500 lines.....

In Gnome bugzilla, Gnome-shell is in "other" projects.

---

