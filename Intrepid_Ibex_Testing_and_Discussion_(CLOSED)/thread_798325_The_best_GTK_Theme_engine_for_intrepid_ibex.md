---
title: "The best GTK Theme engine for intrepid ibex?"
date: 2008-05-18
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by madjr on 2008-05-18
To get working on the new theme, we'll need a good looking engine

right now the engine that has caught my eye is **Aurora GTK engine**

[http://gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438](http://gnome-look.org/content/show.php/Aurora+Gtk+Engine?content=56438)

Ubuntu package:
[http://www.gnome-look.org/content/show.php/Aurora+Ubuntu+Package?content=62227](http://www.gnome-look.org/content/show.php/Aurora+Ubuntu+Package?content=62227)

[IMG]http://gnome-look.org/CONTENT/content-pre3/56438-3.png[/IMG]



examples of use:

[IMG]http://www.gnome-look.org/CONTENT/content-pre1/77377-1.png[/IMG]


nice tooltip:
[IMG]http://www.gnome-look.org/CONTENT/content-pre1/74236-1.jpg[/IMG]



[IMG]http://www.gnome-look.org/CONTENT/content-pre1/76870-1.png[/IMG]





as long as it looks good and gets configured correctly, any engine is good

any other cool engines out there ?

---

### Post by cdekter on 2008-05-18
Aurora is really nice to look at it but it's glacially slow at drawing widgets. It's slow drawing speed is noticeable even on my desktop which has a geForce 7900GT. At work, my workstation has a Quadro NVS running on the legacy nVidia drivers and the speed is so bad I can't use Aurora at all. If you want proof take a look at this benchmark:

[http://gianvito.wordpress.com/2008/02/20/gtk-engines-benchmarks-whats-the-fastest/4/](http://gianvito.wordpress.com/2008/02/20/gtk-engines-benchmarks-whats-the-fastest/4/)

As you can see Aurora is the slowest by quite a substantial margin. So for the purposes of making Ubuntu as flexible as possible (i.e. work well one the widest possible range of PCs), Aurora is pretty much out of the question for a default engine, in its current state.

---

### Post by K.Mandla on 2008-05-18
Moved to II Development.

---

### Post by meborc on 2008-05-18
i suggest murrine... it is what i usually end up with... i try to find something new and exiting, but i always reach this solution - [http://www.cimitan.com/murrine/node/75](http://www.cimitan.com/murrine/node/75)

---

### Post by pferraro on 2008-05-18
Perhaps it would be worthwhile for the devs to work with ECHM (Aurora's author) to address some of the performance issues?

I agree, the Aurora engine's appearance (especially Aurora-Midnight for dark themes) is second to none...

As an alternative, I would suggest looking at the Unity by Cimi, available in the gnome-themes-extras package.  Unity seems to replicate some of the nicer qualities of Aurora using the Clearlooks engine without the same performance sacrifice.

---

### Post by madjr on 2008-05-18
> **pferraro said:**
> 
As an alternative, I would suggest looking at the **Unity** by Cimi, available in the **gnome-themes-extras** package.  Unity seems to replicate some of the nicer qualities of Aurora using the Clearlooks engine without the same performance sacrifice.


cool

---

### Post by plun on 2008-05-19
> **madjr said:**
> 
any other cool engines out there ?

Yup, Murrines SVN version  :)

```
svn checkout http://svn.gnome.org/svn/murrine/trunk/ murrine
cd murrine
./configure --enable-animation
make && sudo make install
```

RGBA patches or already within a app

[http://www.cimitan.com/murrine/rgba-support/list](http://www.cimitan.com/murrine/rgba-support/list)


Cimis blog about this and a global option instead of patches

[http://www.cimitan.com/blog/2008/02/17/rgba-colormap-by-default-in-gtk-call-for-a-coder/](http://www.cimitan.com/blog/2008/02/17/rgba-colormap-by-default-in-gtk-call-for-a-coder/)

Example, patched Exaile and Murrine SVN
[[img]http://pici.se/thumbs/t_iBpPvgdOG.gif[/img]](http://pici.se/267974)

---

### Post by gnomeuser on 2008-05-19
> **cdekter said:**
> 
As you can see Aurora is the slowest by quite a substantial margin. So for the purposes of making Ubuntu as flexible as possible (i.e. work well one the widest possible range of PCs), Aurora is pretty much out of the question for a default engine, in its current state.

The obvious answer would seem to be profiling the code and.. you know getting us free software drivers whose performance we can actually improve. But I'd put my money on being able to improve the performance merely profiling it and odds seem to heavily favor programmers not being perfect and there being a bottleneck.

---

### Post by meborc on 2008-05-19
why spend time on fixing something when we have murrine engine ready and willing? what is so special about aurora that even if it is slow as hell people would like to see it as default? :)

---

### Post by 23meg on 2008-05-19
Aurora is a (mostly, or as the Murrine author would argue, wholly unnecessary) Murrine fork.

As for the question "which engine is best", that depends on what exactly you want to accomplish. Determining an engine and then designing the look on top of that would be an engineering-focused process, and is simply the wrong way to go. It looks like there will be separate theme teams working on multiple themes in this cycle, and they're each looking at using different engines (check out the ubuntu-art mailing list to see what's going on).

---

### Post by plun on 2008-05-19
> **23meg said:**
>  It looks like there will be separate theme teams working on multiple themes in this cycle, and they're each looking at using different engines (check out the ubuntu-art mailing list to see what's going on).

Well.. perhaps its more important to look at  live.gnome...  :)

Cimi is involved in Gnome art work so we will for sure see.

From "somewhere" this picture comes which was published
within a swedish open-source magazine about Gnome 2.24

[IMG]http://pici.se/pictures/awVdbcEJD.png[/IMG]

---

### Post by 23meg on 2008-05-19
I don't see what the default GNOME theme has to do with our artwork process.

---

### Post by plun on 2008-05-19
> **23meg said:**
> I don't see what the default GNOME theme has to do with our artwork process.

Well......

The main reason for waiting for a new Ubuntu theme is of course new Gnome functions.   

Focus on upstream....:)

(there are a few which believes Ubuntu is the world)

The Fedora project has a lot about upstream coordination, I also believe
"sabdfl" wrote about this important fact. 

Also a pre-conference to UDS about this important fact with upstream.
Read about it within Ubuntu Planet.

So skip this isolation or just "the inner circle" should know talk... 


But of course its important to discuss with the community if the main stream community maybe thinks that Gnomes decisions is wrong and wants another solution    8-)

A challenge...  :)

---

### Post by 23meg on 2008-05-19
It's impossible not to care about the GNOME *technologies*; it's being done all the time. I was talking about the GNOME default *artwork*, which is an entirely different thing done by different people, albeit connected to those technologies, but others too, and not necessarily in the sense and to the extent that the Ubuntu artwork process for this cycle will be.

[QUOTE=plun]So skip this isolation or just "the inner circle" should know talk... [/QUOTE]

What isolation?

[QUOTE=plun]But of course its important to discuss with the community if the main stream community maybe thinks that Gnomes decisions is wrong and wants another solution[/QUOTE]

Feel free to start threads to discuss **specifics** (not generalizations, gossip and mudslinging).

---

### Post by meborc on 2008-05-19
now now guys... **[SIZE="5"]"everybody love everybody!"[/SIZE]** - from semi-pro *Will Ferrell*

:)

---

### Post by plun on 2008-05-19
> **23meg said:**
> It's impossible not to care about the GNOME *technologies*; it's being done all the time. I was talking about the GNOME default *artwork*, which is an entirely different thing done by different people, albeit connected to those technologies, but others too, and not necessarily in the sense and to the extent that the Ubuntu artwork process for this cycle will be.


What isolation?


Feel free to start threads to discuss **specifics** (not generalizations, gossip and mudslinging).

Well, Art-Work is mainly a technical question.

Engine, Formats for all components, Window-manager.

That must be stated within a blueprint.

Then in the end its about colours and a wallpaper.

To keep such discussions within "the inner circle" and mailing lists is maybe a bad solution.  


I also prefer open contest for the worlds artists....:) 

(but first must technical issues be stated)


Test it within the Community Cafe....:)

---

### Post by 23meg on 2008-05-19
[QUOTE=plun]Well, Art-Work is mainly a technical question.

Engine, Formats for all components, Window-manager.

[/QUOTE]

My point is that design can't be an afterthought to engineering. Theme engine coders aren't necessarily good theme designers. And "good" theme design does not on its own guarantee a well rounded visual experience in an OS. Of course, what designers can and can't do should be realistically framed within what's possible with the technologies at hand, but I don't see a good argument for choosing an "ideal engine" for whatever reason and building a design on top of that. The question "What is the best GTK engine for Intrepid Ibex?" is completely meaningless without a statement of design goals and criteria for the release. 

[QUOTE=plun]That must be stated within a blueprint.[/QUOTE]

There are multiple blueprints on the theme and visual redesign.

[QUOTE=plun]To keep such discussions within "the inner circle" and mailing lists is maybe a bad solution. [/QUOTE]

First, I would entirely disagree with your notion that "mailing lists" = "the inner circle". They are public, everyone can participate, and the people who participate in them are not any more or less "community" than the people who participate in the forum, or on IRC, or elsewhere. Second, for each success of "design by community" in free software you can point to, I can probably point to ten failures. It just does not work. Too many cooks always spoil the broth. More power to small and focused groups of professionals who know what they're doing, and are open to community input. Just if we had more of them, especially ones with formal design educations, in free software.

[QUOTE=plun]I also prefer open contest for the worlds artists.... [/QUOTE]

I think that's going to be done for the wallpaper in this cycle.

[http://brainstorm.ubuntu.com/idea/384/](http://brainstorm.ubuntu.com/idea/384/)

[QUOTE=plun]Test it within the Community Cafe....[/QUOTE]

As a non-binding test, why not. As a serious and binding discussion, there is no way that can work.

---

### Post by | MM | on 2008-05-20
Aurora is kinda nice at first, but it just has [too many gradients]("http://ubuntuforums.org/attachment.php?attachmentid=70821&stc=1&d=1211260922") everywhere.  I would go as far as to say its garish. Particularly the column headers and the scroll bars!  It makes complex apps like rhythmbox look not very good.

A defualt theme should be attractive but not dominate the whole screen.

IMO the best theme would be to take some of the niceities from aurora and add them to clearlooks which is [simpler on the eye]("http://ubuntuforums.org/attachment.php?attachmentid=70820&stc=1&d=1211260922").

I do however like aurora's [menu's]("http://ubuntuforums.org/attachment.php?attachmentid=70818&stc=1&d=1211260922") and a number of the [widgets]("http://ubuntuforums.org/attachment.php?attachmentid=70819&stc=1&d=1211260922").

---

### Post by durand on 2008-05-20
I vote for murrine because its optimised and looks very nice. But what about [candido]("http://candido.berlios.de/pages/engine.php")? It has some really amazing themes at gnome-look and its pretty fast.

---

### Post by wdaniels on 2008-05-20
> **| MM | said:**
> Aurora is kinda nice at first, but it just has [too many gradients]("http://ubuntuforums.org/attachment.php?attachmentid=70821&stc=1&d=1211260922") everywhere.

Agreed, I have been using Aurora for months now and have noticed the gradients cause problems in quite a few places. See attached of a particular problem I have with the tabstrips (or whatever the relevant GTK widget is actually called) in MonoDevelop - it actually makes it very difficult to use in places.

[IMG]http://temp.willdaniels.co.uk/md-aurora.png[/IMG]
[IMG]http://temp.willdaniels.co.uk/md-aurora2.png[/IMG]

But for dark themes at least, I haven't found anything else that I could live with. (I would prefer not to use a dark theme at all, but I find that anything other than a dark theme and brightness set to zero on my monitor gives me frequent headaches.)

I have to say, also, that I have never received a reply from the author regarding this or any other issue, so I'm not convinced that development of the engine is sufficiently active/responsive to want to have it as an Ubuntu default...

---

### Post by Gina on 2008-05-20
On a personal note - I have an extra pair of glasses for computer use - I used to get headaches.  Even if you don't normally wear glasses, it could be worth checking.  Just a thought for you :)

---

### Post by wdaniels on 2008-05-20
> **Gina said:**
> On a personal note - I have an extra pair of glasses for computer use - I used to get headaches.  Even if you don't normally wear glasses, it could be worth checking.  Just a thought for you :)

Thanks for your advice Gina, but it's a more general problem with light sensitivity and the last time I mentioned it when having an eye test, I was told that it's just "photophobia" and they couldn't see any underlying cause for it - my vision is fine at any distance so the only thing they could offer me was some kind of tinted contact lenses, which is generally my solution to the problem anyway - when I feel a headache coming on I just take some painkillers, switch to candlelight and wear sunglasses.

But I found a dark system theme to be particularly helpful in preventing this in the first place.

(PS: Sorry for being off-topic)

---

### Post by RAOF on 2008-05-22
Finally, someone looked at packaging the Aurora engine for Hardy.  I forget who it was who put it up, but I looked at it on REVU.  There were a bunch of problems with it, of which the one that springs to mind was that the Aurora code was license-less, and that there didn't really seem to be any way to contact the upstream developer.  This makes it unlikely as a default engine for Ubuntu :).

---

### Post by mangar on 2008-05-22
Aurora's author:
[http://www.gnome-look.org/usermanager/search.php?username=ECHM](http://www.gnome-look.org/usermanager/search.php?username=ECHM)

License description:
> Description:
Description:

The Aurora Gtk Engine themes all common Gtk widgets to provide an attractive, complete and consistent look for Gtk applications.

Engine options

• menubarstyle = 1 # 0 = flat, 1 = gradient, 2 = sunken
• curvature = 5 #default widget curvature
• arrowsize = 1 # controls combo_arrow circle size. Diameter set by (11 + 2 * arrowsize)
• old_arrowstyle = FALSE #set to TRUE for original circled arrows (same as arrows in sorted tree columns)
• animation = TRUE # FALSE = disabled, TRUE = enabled (also needs to be compiled with animation support to work)

Inlcuded themes use configurable colours and can be adjusted in Theme Preferences under GNOME.

Thanks to all of you who have provided feedback so far, it has helped catch many things that would otherwise have gone unnoticed. And as always feedback is appreciated.


Known Issues:
• Ugly widgets in: OpenOffice, Java applications
&#8728; Unfortunately I can't really do anything here to make them look better. I can only hope that their emulation of Gtk themes will improve over time

Installation:
• Gtk 2.10+ is required for this engine
• Includes both the GtkRc themes, and the Gtk engine


To install the theme engine extract it to somewhere convenient and in that directory,
run: "./configure --prefix=/usr" then "make"
For animation support add "-enable-animation" when running "./configure"
Then as a root user "make install".

Then install the gtkrc themes by extracting them to your ~/.themes directory (3 themes in total).

To change your current theme to Aurora (under GNOME) open up Theme Preferences (usually somewhere under System > Preferences) click the Customize button and under the controls tab select the theme you want.

Finally thanks to everyone along the line who have worked on the clearlooks and clearlooks based engines as without their work this engine would not exist.

Now go download and enjoy!



Changelog:
1.4
NEW/REDISGNED
• sunken menubar engine option
• reworked progressbars

CHANGES
• scrollbars ebmedded in scroll window (requires Gtk 2.12+)
• increased contrast in widget shading
• smoother button shading

FIXES/ENHANCEMENTS
• Evolution calendar crash
• Other visual tweaks and fixes



**License: GPL**

copy-pasted from gnome-look.org..
hope this helps..

---

### Post by wdaniels on 2008-05-22
> **RAOF said:**
> Finally, someone looked at packaging the Aurora engine for Hardy.  I forget who it was who put it up, but I looked at it on REVU.  There were a bunch of problems with it, of which the one that springs to mind was that the Aurora code was license-less, and that there didn't really seem to be any way to contact the upstream developer.  This makes it unlikely as a default engine for Ubuntu :).

The original upload (the one with the list of problems) on 19th Jan was me. It was my first stab at packaging and though I would have happily dealt with the other issues, I did not get any reply from the author about the license. So I tried to trace the copyrights myself back through the Clearlooks code on which it is based, but found that that seemed to be in exactly the same state as regarding copyrights and licensing, even though there is a Clearlooks package accepted in the repository. I concluded that I just don't have enough experience with packaging to know how best to deal with it, so I left it in my PPA and eventually I just forgot all about it.

The second upload from someone else on 29th March, as far as I can tell has not been reviewed yet, so that one might go through OK since the uploader (Mike) seems to know more about what he's doing with it all than I did...

---

### Post by meborc on 2008-05-22
guys... don't you think that the team that worked on new hardy look (which was postponed to intrepid) already has chosen the engine? i mean there is no point in reinventing the wheel

---

### Post by wdaniels on 2008-05-22
> **meborc said:**
> guys... don't you think that the team that worked on new hardy look (which was postponed to intrepid) already has chosen the engine? i mean there is no point in reinventing the wheel

True, but we're talking about engines not wheels :p  These things get reinvented time and again anyway - I don't see any reason to be overly presumptuous on that, and the discussion is not without value, regardless.

---

### Post by temcat on 2008-05-22
I think the best GTK theme would be the one that has way smaller widgets. Some time ago I saw a post comparing the look of Firefox 3 on Windows, Mac and Linux, and it struck me just how big widgets are on Linux and how much screen real estate they waste. A good source of inspiration *for widget sizing* would be the Redmond GTK theme.

---

### Post by RAOF on 2008-05-22
> **wdaniels said:**
> The original upload (the one with the list of problems) on 19th Jan was me. It was my first stab at packaging and though I would have happily dealt with the other issues, I did not get any reply from the author about the license. So I tried to trace the copyrights myself back through the Clearlooks code on which it is based, but found that that seemed to be in exactly the same state as regarding copyrights and licensing, even though there is a Clearlooks package accepted in the repository. I concluded that I just don't have enough experience with packaging to know how best to deal with it, so I left it in my PPA and eventually I just forgot all about it.
...

Yeah; having copyright headers in all files is not an absolute requirement.  It just depends on which archive admin (not MOTU) is reviewing the upload in the NEW queue.  It is *much* easier getting well-licensed code into the archives, and there is really a higher bar to get in than to stay in.

Hm.  I guess I should review the new package sometime (a quick look suggests there's plenty of comments to make :().  I'm not convinced that it's a good package to include, though.  At best, it looks like it would be difficult to pass bugs on to upstream, given that there doesn't seem to be any public VCS, mailing list, homepage, bugtracker, or such like.  It's quite a nice engine (although you can find something similar in the **Unity** theme for Clearlooks in gnome-themes-extras).  If the author made it a project in, say, launchpad, with public bzr repository, bugtracker, etc, that would make it much more attractive to include.

---

