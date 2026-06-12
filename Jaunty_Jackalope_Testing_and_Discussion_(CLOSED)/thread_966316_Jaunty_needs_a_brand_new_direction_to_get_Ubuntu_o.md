---
title: "Jaunty needs a brand new direction to get Ubuntu on top"
date: 2008-11-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by SunnyRabbiera on 2008-11-01
Alright so far I have not jumped in to talk about the development of the next release of Ubuntu, but now more then ever I feel we need to make some effort to make JJ what both Ibex and Hardy could have been.
With new themes, new tools and new ideas to make ubuntu attractive and usable.

Now here is part one of my idea for Jaunty: A NEW THEME NEEDS TO TAKE TOP PRIORITY.
Ibex is such a letdown with its 300 clearlooks like themes, I think we should either A: pull Ubuntulooks out of the grave and fork it
B: Fork Murrine
or C: Create a brand new engine

I think C is what we need to do, but the efforts to do so were seriously lacking.
I think the new theme should be both usable and attractive, we cannot rely on browns here as proposed for Hardy or Ibex.
We need a theme that speaks attractiveness but also friendliness.
A theme that is appealing too, I feel a overly dark and brown theme will not be attractive to the average windows or OSX user, I think we should go orange.
I mean orange is a very neutral color, its away from the "kitchenware' themes that Mark Shuttleworth, I sort of like this theme:
[https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Intrepid_Ibex_GTK_proposal?action=AttachFile&do=view&target=screenshot.png](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Intrepid_Ibex_GTK_proposal?action=AttachFile&do=view&target=screenshot.png)

and yes even this theme in ibex despite its ties to clearlooks:
[https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Kin_Intrepid?action=AttachFile&do=view&target=kin_clear_1.png](https://wiki.ubuntu.com/Artwork/Incoming/Intrepid/Kin_Intrepid?action=AttachFile&do=view&target=kin_clear_1.png)

But it might be too orange.
We need somthing bold here, not old thus why I really feel clearlooks needs to be abandoned here in favor of a new revolutionary theme.

The second Part of my idea for jaunty is a new control center.
Seriously Ubuntu lacks a major tool that will break it apart from the others, it needs its own application that stands out.

My proposal is a new control center that I proposed once called ubuntu ground control, a new all in one control center similar to mandrivas control center but with some implementations to make it stand out.

here was my proposal for that:
If its one thing I think Ubuntu needs I think its a control center, but one BETTER then gnome control center.
So I propose Ubuntu Ground Control as an idea, a super control center built for Ubuntu to make it easy and fun for the new user.
Here is how I see it, take the basic ideas of Drakconfig, the mandriva control center and merge them with some ideas that I have seen for Ubuntu like Ubuntu tweak.

The basic idea:
The control center itself should be simplistic but customizable, a customizable interface is something that drakconfig lacks.
If you change the iconset it should change inside this control center.
Also have something that can change more complex settings like monitor or sound without the need of the default gnome apps that dont have as many options.
It should overall be a hybrid of drakconfig and Ubuntu tweak.

Ideas borrowed from drakconfig:
Monitor settings: a better way to set up the monitor, with displayconfig-gtk gone and the default screen resolution app severely limited there needs to be a new application for editing monitor preferences for the local user and the administrator.

Sound configuration: Pulse and alsa have caused a lot of issues and even though the sound server selection tool provided by gnome does a basic job there needs to be something that can change all aspects of the system sound.
Like start up volume, system sounds and the like. This can hopefully improve Gnomes Volume Applet a bit too, like help enable extra devices and such.

Ideas from Ubuntu tweak:
Add/remove: with the next synaptic featuring a quick search function add/remove is a little less needed in the future releases of Ubuntu, plus I have always seen it as a hindrance.
Maybe if we can make a menu or something with two options:
basic installer (add/remove) or advanced installer (synaptic)
replace the add/remove option in the menus with this "Ground control" app to encourage new users not to use add/remove as a primary.

Computer information: change the host name of the computer, change user information, make things easier for people who like to mess around with their computers a bit.
Desktop icons: helps the user make desktop icons for home folders, trash bins and even links to applications if we are talking about deperate beginners. No more going into gconf editor, no more having to figure out how to use gconf editor... that thing is great for advanced users but for beginners its a nightmare.

Templates installer: helps install extra templates

Font installer: we have been lacking a good one, its time to get one.

My own ideas:
Easycenter (aka Rocketship): provides Medibuntu integration (or at least make it easier to put it in the repositories), Canonical store access and Codec buying via partners(for those who want codecs "legally")

Astronaut: Provides easy and direct access to support via both the forums and the IRC chat.

Venture: The all in one package converter, provides tools to convert RPM packages, download tools to help compile from source, and other stuff to help the newbie install packages that are not on the repositories... heck throw in a easy way to install and configure wine in there too.

Enterprise: to provide... shock enterprise support for businesses

my idea here is just maybe there should be an easier way to add extra repositories then like medibuntu for beginners so they wont have to touch the terminal.
As for venture it could be used as a front end for alien or checkinstall, so that cuts down the terminal use for that part too.

Venture should help install source packages or RPM's and make them manageable for the new user, the confusion of RPM and tar packages is what throws people off so maybe there should be a non CLI frontend to checkinstall and Alien.
at least give alien a frontend, I know its not always on par but it will help out when there is a package someone needs that is RPM only.

As for checkinstall and compiling, at least lets try to make it somewhat easier for the newbie to convert source packages without the terminal.
I am just thinking of something that could be useful to newcommers here, I know both ideas are not perfect but its better then scaring newbies with a terminal.
I have always wondered why alien has not got a gui yet, it seriously needs one. I know the flaws in alien yes but it does the job most of the time when it is needed.
I know this wont be a very popular idea but we need something to make ubuntu stand out.

Part three: We need once again to focus on stability, I have said it a million times but it is needed... also there must be an easier way then to upgrade the whole OS to get newer packages, we definitely need more help on backports already!

---

### Post by jfernyhough on 2008-11-01
Personally, I would like Jackalope to take the Snow Leopard approach this time.

Speed.
Stability.
Polish.

Get PA working flawlessly (heh), get the kernel optimised, get boot time to ~10 seconds (first impressions count), reduce power usage (GUI tool to enable power saving for laptop users), make everything shiny.

---

### Post by exploder on 2008-11-01
I feel that the priorities should go like this.

001- Create an outstanding appearance for the system. This must be a top priority, theme, usplash, icons and program splash screens. The appearance has been a problem for everyone for long enough.

002- Focus on bug fixes. There are far too many regressions left in new releases. What good are higher version numbers when you can not do the simple things like burn a CD? There really needs to be focus on EVERYTHING working.

These are not easily obtained goals by any means. These are the reasons that linux in general is not the mainstream standard though. There needs to be work done on the existing technology before new things are added.An example would be the eject buttons that were added to Intrepid. This feature was added and it doesn't even work! The tray opens and then quickly closes and it compounds the existing problems with burning CDs. System sounds have not worked for the last three releases either. How good is pulse audio when this type of regression exists? A release that focuses on fixing existing bogs and pleasant default appearance would be very welcome.

---

### Post by meastp on 2008-11-01
> **jfernyhough said:**
> Personally, I would like Jackalope to take the Snow Leopard approach this time.

Speed.
Stability.
Polish.

Get PA working flawlessly (heh), get the kernel optimised, get boot time to ~10 seconds (first impressions count), reduce power usage (GUI tool to enable power saving for laptop users), make everything shiny.

Indeed! With the recent performance results from Phoronix, I'd say speed needs to be addressed, along with stability and power saving.

@OP : Instead of e.g recreating Gnome Control Center for Ubuntu, why not address what's wrong with Gnome Control Center, and make it rock? Fixing things upstream is, in most cases, always *better*. If we create something ourselves, that means we have to remove Gnome Control Center in Gnome, and add Ubuntu Control Center + patch upstream, which is *more work*.

---

### Post by meastp on 2008-11-01
> **jfernyhough said:**
> Personally, I would like Jackalope to take the Snow Leopard approach this time.

Speed.
Stability.
Polish.

Get PA working flawlessly (heh), get the kernel optimised, get boot time to ~10 seconds (first impressions count), reduce power usage (GUI tool to enable power saving for laptop users), make everything shiny.

Indeed! With the recent performance results from Phoronix, I'd say speed needs to be addressed, along with stability and power saving.

@OP : Instead of e.g recreating Gnome Control Center for Ubuntu, why not address what's wrong with Gnome Control Center, and make it rock? Fixing things upstream is, in most cases, always *better*. If we create something ourselves, that means we have to remove Gnome Control Center in Gnome, and add Ubuntu Control Center + patch upstream, which is *more work*.

---

### Post by darco on 2008-11-01
I hate to say it but maybe they shouldnt be cranking out new releases every 6mos and concentrate on releasing a new OS 'when its ready"?

darco

---

### Post by Slug71 on 2008-11-01
> **jfernyhough said:**
> Personally, I would like Jackalope to take the Snow Leopard approach this time.

Speed.
Stability.
Polish.

Get PA working flawlessly (heh), get the kernel optimised, get boot time to ~10 seconds (first impressions count), reduce power usage (GUI tool to enable power saving for laptop users), make everything shiny.

+1

PA needs a good kick up the butt.

EXT4, PA and a new Theme need priority.

---

### Post by Slug71 on 2008-11-01
> **darco said:**
> I hate to say it but maybe they shouldnt be cranking out new releases every 6mos and concentrate on releasing a new OS 'when its ready"?

darco

Well i personally think this will happen eventually. Since there is gonna be no 3.x Kernel and seeing how well this new Kernel works with Hardware/Software, i suspect things will start slowing down in that department. Also LSB 4.0 is due sometime this month which is suppose to have a lot of changes.

---

### Post by lukjad on 2008-11-01
@SunnyRabbiera in the OP.

Could you space it out just a bit more? It's a bit thick to read.

---

### Post by Naddiseo on 2008-11-01
To be honest, I quite like the current default Human Theme, so I don't see it as top priority. That being said, I would like a different/new one, though not in Jaunty. A new theme is something I'd prefer to see once every LTS release, or so. The releases inbetween should focus more on the performance, and features aspect. I'm totally for fixing up the sound system this release, as well as speeding up boot time / shutdown time. The last one isn't so important though, the only reason I'd vote for it is because my computer is in my bedroom, so I shut it down every night, and boot it up every morning - it's really load so can't sleep while it's on.

The Control Centre sounds like a good idea, but like previous posts have mentioned, I think it'd be better to address the short comings of the gnome control center. I'd also like to add an easier way to edit the gconf settings, gconf-editor feels too much like windows' regedit, which is definately not user friendly.

Perhaps this release I'll try to actually contribut some of my coding time, which I've been meaning to do for a while.

---

### Post by jfernyhough on 2008-11-01
I posted a new brainstorm item: [http://brainstorm.ubuntu.com/idea/15115/](http://brainstorm.ubuntu.com/idea/15115/)

--edit
Ooo, having never used brainstorm before I found this:

[[IMG]http://brainstorm.ubuntu.com/idea/15115/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15115/)

Cool!

---

### Post by SunnyRabbiera on 2008-11-01
> **meastp said:**
> Indeed! With the recent performance results from Phoronix, I'd say speed needs to be addressed, along with stability and power saving.

@OP : Instead of e.g recreating Gnome Control Center for Ubuntu, why not address what's wrong with Gnome Control Center, and make it rock? Fixing things upstream is, in most cases, always *better*. If we create something ourselves, that means we have to remove Gnome Control Center in Gnome, and add Ubuntu Control Center + patch upstream, which is *more work*.

I said I am not suggesting recreating gnome control center... but replace it entirely

---

### Post by meastp on 2008-11-01
> **SunnyRabbiera said:**
> I said I am not suggesting recreating gnome control center... but replace it entirely

Yeah.. Isn't that the same thing, though? Unless you'd want Gnome Control Center to be replaced with something that doesn't (completely) overlap the goals Gnome Control Center has...

As long as Gnome Control Center accepts patches / redesigns, I don't see the justification.

---

### Post by Hairy_Palms on 2008-11-02
im curious as to what people think is wrong with gnome control centre, im always a fan of control centers in general because they look more polished, but since gnome-control-center adopted the crappy SLAB control center its too slow to load for me so i always end up just using the menu system.

---

### Post by glasen on 2008-11-02
> **meastp said:**
> Indeed! With the recent performance results from Phoronix, I'd say speed needs to be addressed, along with stability and power saving.

The Phoronix test results are completely false. Ubuntu 8.10 is as fast as Ubuntu 7.04 and all other versions of Ubuntu. For more information look at these threads in the phoronix forums :

[http://www.phoronix.com/forums/showthread.php?t=13577](http://www.phoronix.com/forums/showthread.php?t=13577)

and

[http://www.phoronix.com/forums/showthread.php?t=13486&page=9](http://www.phoronix.com/forums/showthread.php?t=13486&page=9)

P.S:

I don't understand why there are so many people out there who believe that Ubuntu is a slow distribution.
There is no scientific proof that other distributions are so much faster. And faster means for me faster applications and not faster boottime or "it seems to be faster, because i think it's faster!"

---

### Post by gnomeuser on 2008-11-02
There are several problems with these control centers.. every distro seems to feel the need to make them (except Fedora, more on this in a second). Mandriva has their own Drake something or another, openSUSE has YaST and so on. There are several problems with this duplication of effort, including consistency, interacting, translation of the many many different tools into hundreds of languages and finally the pure polish and coverage of the separate tools.

What we need is not another damn control center, what we need is standards for configuration and the same tools everywhere. A PackageKit for system management if you will. This will make it easy to move from distro to distro as well as for system administrators to configure a large number of different system using the same methods.

To do this we need first to embrace that we are different, we all put things in different places, the solution short term cannot be building an Elektra like full system configuration database. We will never get everyone to agree on everything, there needs to be room for innovation and historically differences in tool choices. 

So the common ground we need to seek would be a shim that provides a common API which can be used for the greatest common benefactor terms of configuration with backends to map to the existing solutions. This is very much what PackageKit does for package management, same tools and a chance of integration equally despite the choice of backend in your distro of choice. Basically we want to be able to invoke changes in e.g. the bootloader using a simple interface and have that alter the backend regardless of what that is be it extlinux, lilo, grub, etc. We also want to be able to take this kind of configuration and centralize it for the cases where we manage a large network and want to handle upgrades, bootloader configuration and such.

Such a system exists, and now we get back to Fedora as promised, Red Hat' emerging technology labs and the Fedora community have several projects going which are along this line of thinking.

[http://augeas.net/](http://augeas.net/) - Augeas, a configuration API, which does a lot of the above
[http://freeipa.org/page/Main_Page](http://freeipa.org/page/Main_Page) - FreeIPA
[https://fedorahosted.org/spacewalk](https://fedorahosted.org/spacewalk) - Spacewalk, system management.

I would suggest expanding the backends for Augeas while writing tools that use that interface, this can be done upstream using FreeDesktop.org e.g.. It would be important to gain too adoption for sitting down with the openSUSE and Fedora guys when designing the UI would be good. Also accommodating both major desktops would be good in gaining adoption. For the extended identity and system management we can look to FreeIPA and Spacewalk. For a first step a FreeDesktop.org single user desktop control center written under the guise of FreeDesktop.org would be a great start and a way to get adoption.

So there you go, we should not distinguish ourselves by re-inventing the wheel, we should instead seek to sell a product on it's merits and give people common tools.

---

### Post by moopere on 2008-11-02
> **exploder said:**
> I feel that the priorities should go like this.

001- Create an outstanding appearance for the system. This must be a top priority, theme, usplash, icons and program splash screens. The appearance has been a problem for everyone for long enough.


Goodness me!  I almost spat chunks of muesli through my nose when I read this.  

Not to be rude, but honestly, we want things to be shiny -before- they work properly?  We'd prefer it to remain broken but so long as it looks nice we're happy?

Anyway, I personally love the brown themes and always have.  Whenever I have to use a different Linux I always change its default theme to a human type thing from gnomelook.

Cheers, Craig

---

### Post by Slug71 on 2008-11-02
> **gnomeuser said:**
> What we need is not another damn control center, what we need is standards for configuration and the same tools everywhere. A PackageKit for system management if you will. This will make it easy to move from distro to distro as well as for system administrators to configure a large number of different system using the same methods.

+1 
Perhaps this will be more possible with LSB 4.0?

> **moopere said:**
> Goodness me!  I almost spat chunks of muesli through my nose when I read this.

:lolflag::lolflag: 

> **moopere said:**
> Not to be rude, but honestly, we want things to be shiny -before- they work properly?  We'd prefer it to remain broken but so long as it looks nice we're happy?

+1
I strongly agree that things need to be fixed FIRST! We're still fixing bugs from previous versions as well as trying to improve and implement new things and it is clearly not working. Freeze IMHO needs to be early for Jaunty or Release delayed until Everything is working as it should.

---

### Post by Merk42 on 2008-11-02
About the whole bug fixes vs. new theme that just came up, which I knew it would...

Those are two completely different issues with two completely different teams.  So we could work on an attractive new look without sacrificing time/manpower to fix bugs.

---

### Post by denzilla on 2008-11-02
Speed and reliability are job #1. It doesn't reflect well on Ubuntu or Linux in general if hardware that worked in a previous release doesn't work in the newest version. I would also like to see official support for backports for critical apps like FF, OOo, Gimp, etc. 

What was that I read about no 3x Linux kernel?

---

### Post by exploder on 2008-11-02
> 
Not to be rude, but honestly, we want things to be shiny -before- they work properly? We'd prefer it to remain broken but so long as it looks nice we're happy?


Unfortunately, bugs and regressions seem to be a way of life now. We have Pulse Audio but most of the system sounds do not work. We now have "eject" buttons but the CD-ROM tray immediately closes after opening... We have gvfs but now floppy drives no longer work. We have Evolution but it can't remember a password. We have a new xorg, but it doesn't work with many previously supported video cards.

People have been after "Shiny" for a log time and I will concede that I was mistaken about first priority. Perhaps the mass of broken things should come first.

---

### Post by Slug71 on 2008-11-02
> **denzilla said:**
> What was that I read about no 3x Linux kernel?

It's unlikely there will be a 3.x.x Kernel.
Read here.
[http://www.daniweb.com/blogs/entry1607.html](http://www.daniweb.com/blogs/entry1607.html)

---

### Post by denzilla on 2008-11-02
> **Slug71 said:**
> It's unlikely there will be a 3.x.x Kernel.
Read here.
[http://www.daniweb.com/blogs/entry1607.html](http://www.daniweb.com/blogs/entry1607.html)

Thanks for the link :)

---

### Post by Slug71 on 2008-11-02
> **exploder said:**
> Unfortunately, bugs and regressions seem to be a way of life now. We have Pulse Audio but most of the system sounds do not work. We now have "eject" buttons but the CD-ROM tray immediately closes after opening... We have gvfs but now floppy drives no longer work. We have Evolution but it can't remember a password. We have a new xorg, but it doesn't work with many previously supported video cards.

People have been after "Shiny" for a log time and I will concede that I was mistaken about first priority. Perhaps the mass of broken things should come first.

Agreed.
JJ needs to be a fixed stable release of 8.04 and 8.10, OR it needs to be a release with all the "new toys" and "shineyness" which will probably have lots of bugs and probably not be suitable for a production machine but means KK will be that stable working version we all want.
It really needs to be one or the other but we can't keep on the same path as 8.04 or 8.10 or else the next LTS will be another 8.04.

I personally would prefer all the "new toys and shineyness" now even as early as Alpha 1 so that we can start bug fixing from the get go.
I'd even prefer Jaunty ship with the version of Gnome and Compiz 8.10 has now so that it can get properly fixed.

What i would like to see in Alpha 1 and be shipped with Jaunty is:

Ext4
Grub2
Kernel 2.6.28(with Alsa 1.0.18 and PA 0.9.14-which should be out soon)
LSB 4.0 (release is Nov 11)
OOo. 3
Firefox 3.1
A new Theme

Have Brainstormed it.
[[IMG]http://brainstorm.ubuntu.com/idea/15155/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/15155/)

---

### Post by exploder on 2008-11-02
Slug71, I like your list, it seems realistic to me. We do need all of the above mentioned issues worked out in this release.

---

### Post by itisbasi on 2008-11-02
Why is it that OOo 3 didn't come bundled with intrepid? I have been running it on hardy and now on intrepid, and have had no problems thus far....
With regard to the theme, Well I don't quite like the idea of going the leopard way...The ubuntu theme has it's distinct identity and I like it that way.

---

### Post by Slug71 on 2008-11-02
> **exploder said:**
> Slug71, I like your list, it seems realistic to me. We do need all of the above mentioned issues worked out in this release.

Thanks exploder, the way i see it most of that will be around for a while after release so why not bring it on now.

---

### Post by Slug71 on 2008-11-02
> **itisbasi said:**
> Why is it that OOo 3 didn't come bundled with intrepid? I have been running it on hardy and now on intrepid, and have had no problems thus far....
With regard to the theme, Well I don't quite like the idea of going the leopard way...The ubuntu theme has it's distinct identity and I like it that way.

The devs felt it was to new for Intrepid and could possibly have lots of bugs still. Which is why i think it should be included from Alpha 1 of Jaunty. 

As for the new Theme, i dont care which way we go but it would be nice to have a new one. Agree with something unique though.

---

### Post by smartboyathome on 2008-11-02
> **Slug71 said:**
> The devs felt it was to new for Intrepid and could possibly have lots of bugs still. Which is why i think it should be included from Alpha 1 of Jaunty. 

As for the new Theme, i dont care which way we go but it would be nice to have a new one. Agree with something unique though.

No, it was because the devs were sticking to a schedule. That schedule said that feature freeze had past, and that you would have to put together a freeze exception to get it even to be decided if it got in. Since no one did (that I know of), OOo 3 didn't get in.

---

### Post by antiloop on 2008-11-02
I want a control center. 

It should have the option to hide advanced settings from new users. Maybe three pre-customized alternatives to choose from, easy/moderate or advanced user. It's too cluttered right now.  

I would also want some kind of guide (like in XP on first boot, with the option to skip of course). It should let you choose between a few standard themes for GTK and the terminal, with thumbnails. 
Also maybe let you configure mouse buttons and the likes...

Other than that polish...

A newbie friendly terminal is a dream of mine too. With all commands explained and divided into groups. It's so overwhelming and powerful for new users right now. :p

I mean holding a new users hand shouldn't be too much to ask from a distrobution like Ubuntu.

---

### Post by Slug71 on 2008-11-02
> **smartboyathome said:**
> No, it was because the devs were sticking to a schedule. That schedule said that feature freeze had past, and that you would have to put together a freeze exception to get it even to be decided if it got in. Since no one did (that I know of), OOo 3 didn't get in.

Was the Freeze Exception not made because of what i said though?
Could be wrong but i'm sure that's what i read in the Intrepid Testing and Discussion forum when all the new Threads came about it around Beta.

---

### Post by gjoellee on 2008-11-02
I totally agree, if you take a look back at the first Ubuntu distro the changes are actually little.......But that is GNOME's fault as well I believe

---

### Post by smartboyathome on 2008-11-02
> **Slug71 said:**
> Was the Freeze Exception not made because of what i said though?
Could be wrong but i'm sure that's what i read in the Intrepid Testing and Discussion forum when all the new Threads came about it around Beta.

It may be. I don't know all the reasons of the developers. ;)

---

### Post by Slug71 on 2008-11-02
> **smartboyathome said:**
> It may be. I don't know all the reasons of the developers. ;)

Thanks for helping clear that up anyways.

---

### Post by Slug71 on 2008-11-02
> **gjoellee said:**
> I totally agree, if you take a look back at the first Ubuntu distro the changes are actually little.......But that is GNOME's fault as well I believe

That's how it needs to go back to for a couple versions i think and big changes need to be in from Alpha 1. Maybe then we'll have a very good version for the next LTS.

---

### Post by olskar on 2008-11-02
I say, don't care as much about the boot-time but concentrate on the startup times of the applications!


Openoffice 2.4 and Firefox for example opens very slow on my system, anyone else who is also suffering from this?

Edit: At their first opening

---

### Post by Slug71 on 2008-11-02
> **olskar said:**
> i say, don't care as much about the boot-time but concentrate on the startup times of the applications!


Openoffice 2.4 and firefox for example opens very slow on my system, anyone else who is also suffering from this?

Edit: At their first opening

+1

---

### Post by jfernyhough on 2008-11-03
> **olskar said:**
> I say, don't care as much about the boot-time but concentrate on the startup times of the applications!


Openoffice 2.4 and Firefox for example opens very slow on my system, anyone else who is also suffering from this?

Edit: At their first openingOOo is fixed in version 3, 2.4.1 needs to have Java disabled and it's quick.

For Firefox, if you've been using it for a while the sqlite databases get large and unoptimised - they need vacuuming:

$ cd ~/.mozilla/firefox/PROFILE/
$ for i in *.sqlite; do echo "VACUUM;" | sqlite3 $i ; done

This improves startup time noticeably. I'm not entirely sure why this isn't done automatically every n loads (or exits).

---

### Post by oomingmak on 2008-11-03
> **moopere said:**
> Not to be rude, but honestly, we want things to be shiny -before- they work properly?  We'd prefer it to remain broken but so long as it looks nice we're happy?
This is bogus reasoning. It's not an "either" "or" situation.

Do you really think that developers take a break from patching the kernel (or writing low level drivers etc.) in order to sketch a wallpaper or create a few icons in their spare time?

The people who work on the UI's *aesthetics *(as opposed to UI *functionality*) are **not **programmers. They are artists, and they can therefore work totally independently of the developers who are busy fixing bugs. So no matter how much time is spent refining a visual theme, it's not taking anything away from code development.

To suggest that bugs should be fixed first before attending to aesthetics is also misguided. No system with the complexity of an OS is ever going to be 100% bug free, so if you adopt an approach that stipulates that bugs must be dealt with first, then you'll be waiting for ever before any one gets round to focusing on looks. There's always *something *that needs fixing.

It's reasoning like this that causes Ubuntu to look so crap. Aesthetics are always given a low priority, ignored until the very last minute and then hurriedly put together by amateurs. If Ubuntu really wants to up its game visually (as Mark Shuttleworth has said) then there should be a dedicated team of artists constantly refining and improving Ubuntu's look and meeting new visual 'milestone' targets with each release, just like developers do for code. 

So, just as new functions, features and fixes are added from alpha to alpha, then so should colour schemes get more polished, icon themes become more complete and consistent etc. with each subsequent test release. Doing nothing at all visually through the early stages of development and then quickly throwing together a naff wallpaper minutes before the beta turns to RC (because there was simply not enough time to do anything else like create an entire icon set) is not going to convince anyone that Ubuntu is serious about being "visually appealing" no matter what Mark Shuttleworth says in his blogs.

[**[COLOR=DarkOrange]http://www.markshuttleworth.com/archives/63[/COLOR]**]("http://www.markshuttleworth.com/archives/63")

[[COLOR=DarkOrange]**http://www.markshuttleworth.com/archives/162**[/COLOR]]("http://www.markshuttleworth.com/archives/162")

---

### Post by Slug71 on 2008-11-03
Theres plenty of community Themes and Icon sets, Wallpapers etc out there. 
Yes they can be done independently but that doesn't mean it should take priority during Alpha phases. Yes theres always going to be bugs but Ubuntu has LOTS and some of them big ones at the moment. Stability really should be Priority throughout the dev phase of JJ and thats why i think any big addition need to be done ASAP with JJ.

Believe me, i'd like a new Look too but Stability really needs to be priority. If lots of people continue to have Hardware/Software issues they're gonna walk away from Ubuntu.

---

### Post by Merk42 on 2008-11-03
> **Slug71 said:**
> Stability really should be Priority throughout the dev phase of JJ and thats why i think any big addition need to be done ASAP with JJ.

But given what oomingmak just said, couldn't stability and attractiveness BOTH be a priority?

---

### Post by ronacc on 2008-11-03
Give it up folks Ubuntu is never going to get a new default theme either get used to brown or suck it up and change it youselves . click click change change oh what a reilef it is .

---

### Post by Slug71 on 2008-11-04
> **ronacc said:**
> Give it up folks Ubuntu is never going to get a new default theme either get used to brown or suck it up and change it youselves . click click change change oh what a reilef it is .

Exactly, most people change the defaults anyways. I'd rather see JJ be a version that Most people can just put in the disc, install, and everything works and works well. Especially for new comers and people that have tried Linux before but got scared away but it because things weren't working.

---

### Post by Lorenz on 2008-11-04
I think there is an easy, yet valid formula:
No new shiny theme = no success

And yes, first impression counts. And no, it doesn't count that you can change it anyway.

---

### Post by iponeverything on 2008-11-04
> **Lorenz said:**
> I think there is an easy, yet valid formula:
No new shiny theme = no success

And yes, first impression counts. And no, it doesn't count that you can change it anyway.

I think you need to define success.

If success is keeping old hardware out of landfills, ubuntu has it.

If success is sharing knowledge for the betterment of humanity, ubuntu has it.

If success is opening up computing to the developing world, ubuntu has it.

Its not a competition, linux can't be put out of business. As long as its useful it will continue to grow.  

Linux has been my sole operating system since 1993. I recently moved to ubuntu from strait debian because I like Mark Shuttleworth and his vision, he reminds me of Bono. 

One person can change the world.

---

### Post by ronacc on 2008-11-04
WARNING politicaly incorrect formula follows : If they are A so shallow that the default theme runs them off AND B too lazy/uncaring to explore the very easy steps necessary to change said theme/apearence they are C not worth worrying about.

---

### Post by Magnes on 2008-11-04
I thought that the control centre was ready when 7.10 was about to come out. I saw screenshots, heard that there are some problems (clearing user home or sth like that, nothing that couldn't be fixed and then... silence). It was like the control center for editing Compiz preferences with search but the applets to do the settings where the old ones (so there was not much work to be done!).

I was very startled when I didn't see one in 8.04 and now in 8.10 there is none also. What happened?

---

### Post by ronacc on 2008-11-04
> **Magnes said:**
> I thought that the control centre was ready when 7.10 was about to come out. I saw screenshots, heard that there are some problems (clearing user home or sth like that, nothing that couldn't be fixed and then... silence). It was like the control center for editing Compiz preferences with search but the applets to do the settings where the old ones (so there was not much work to be done!).

I was very startled when I didn't see one in 8.04 and now in 8.10 there is none also. What happened?

its there , in 8.04 its in system>preferences in 8.10 you have to activate it in system>preferences>main menu

---

### Post by Changturkey on 2008-11-04
> **ronacc said:**
> Give it up folks Ubuntu is never going to get a new default theme either get used to brown or suck it up and change it youselves . click click change change oh what a reilef it is .

Never?

---

### Post by plun on 2008-11-04
> **Changturkey said:**
> Never?

Well.. who knows ?, there are a few at Gnome which apparently blocks everything.
[B]
"Metacity is the boring window manager for the adult in you." [/B]):P

[http://live.gnome.org/Metacity](http://live.gnome.org/Metacity)


Maybe KDE is the only way...:confused:

---

### Post by snowpine on 2008-11-04
My thoughts on JJ:
1) II is really nice, so keep up the good work!
2) #1 priority should be making all the code stable, elegant, bug-free, fast.
3) Make an official Openbox Ubuntu that is super-light for old hardware (much lighter than Xubuntu).
4) Full support for eee PC and other netbooks out of the box.
5) Keep the brown/orange theme.

---

### Post by ronacc on 2008-11-04
> **Changturkey said:**
> Never?

[http://ubuntuforums.org/showthread.php?t=18447](http://ubuntuforums.org/showthread.php?t=18447)

I rest my case .

---

### Post by swj on 2008-11-04
1. Fix the panel icons.  See OS X.

2. Hopefully the hired art help will take ideas from Dust and all the other great themes submitted.

3. Fur, Skin, and / or dried blood will never be taken seriously as a professional wallpaper...  

4. And the most important thing with respect to the default theme, make a 'shiny' and 'happy' theme that makes people 'feel good' using black and orange colors.

"happy little clouds" and "happy little trees"
  Bob Ross

---

### Post by marcusklaas on 2008-11-04
Guys, there really shouldn't be so much hassle about new default themes. It's so easy to download and install your own themes, it's pretty much obsolete to add them by default. But yea, the default one is ugly. To be honest, I've never been happier with Ubuntu. I really think it's approaching perfection REAL fast I mean I personally thought Gutsy was good, HARDY SUCKED MONKEY *** BALLS, but man I'm loving the Inteprid hardcore. Every little flaw seems fixed and I just can't stop loving. Things that got better? Theme-management, audio-management (MAN THAT PISSED ME OFF IN HARDY) and Pidgin. I don't know, but it feels a heck a-lot faster now too. Not as fast as Windows XP on lighter PCs though, I wonder why that is. 

If I have to say something for future releases:
- Keep yo **** clean. Prevent Ubuntu from being littered with small programs that are barely used yea? Like for instance I think the password key manager or something, does it have to be there? Maybe it does, but it should be used if it's there.
- Try to speed it up further if possible. Is it possible? It's pretty quick now, don't get me wrong.
- Pretty much every feature you'd want in by default is in, so don't keep cramming new programs in. I think Ubuntu has reached the point where it should tweak some shizzle, n ****. Make it all come together nicely, know what I'm saying?
- For heaven's sake, make the Proprietary drivers work (I know you aint lovin' 'em, but do it anyways). Make worst case scenarios and test them, when you tested it all, test some moar, in as much setups as you can think of. And then make it work. It's reel frustrating not to have a proper video driver, yea?

---

### Post by ronacc on 2008-11-04
> **marcusklaas said:**
> 
- For heaven's sake, make the Proprietary drivers work (I know you aint lovin' 'em, but do it anyways). Make worst case scenarios and test them, when you tested it all, test some moar, in as much setups as you can think of. And then make it work. It's reel frustrating not to have a proper video driver, yea?

thats what we here in the dev forum are for , so test the apropriate driver for YOUR setup and then file meaningful bug reports with as much info as you can.

---

### Post by Lorenz on 2008-11-04
Who are we to define who is worthy to use Ubuntu and who is not?
If Ubuntu strives to be a real alternative to Windows and be profitable without the support of Mark, it will need to have a shiny eye-candy desktop that rivals or better even surpassed Vista/Windows 7 and Leopard. 
We "hardcore" guys can think what we want, our focus on minimalism and what we perceive to be usability (terminal!) doesn't really matter for the majority of people. They look at a screenshot, if it is not nice, they won't take it. Believe me. And I don't know if that is what you want Ubuntu to be, but I think that is the goal. Success fuels innovation and success only goes via looks.

Edit: Don't we all know that you can change the theme with minimal effort? 
But don't we all know too that almost everyone who posts here is far more than Joe-average user?

---

### Post by ronacc on 2008-11-04
the average preteen will figure out how to change the looks rather quickly , I don't have a preteen handy right now or I would get out my stopwatch and see how long it took . I didn't say that anyone was "unworthy" of ubuntu , I said they aren't worth worrying about . I am not a "hardcore terminal hound" I only use a terminal when that is the most convienent way of doing something and have lobbied long and hard for more gui apps . I stand by my comment about "shallow "  people though , are they really worth courting when they will soon be gone chasing the next shiny ? a broken email program or video driver or browser will chase off more people than bad wallpaper .

---

### Post by Lorenz on 2008-11-04
I'm not only talking about preteens, those are the curious users I would worry about least. Problems with drivers and non-compatible programs are show-stoppers for sure, but the first thing anyone sees is the desktop. I have heard plenty comments from friends, colleagues, journalists or just users who post on newspaper's websites etc. who think that Ubuntu currently looks ugly and those people are often opinion leaders. 

It is in my opinion crucial and vital for the success of Ubuntu to have a absolutely shiny and flawlessly looking default desktop. I understand all points that everything can be customized easily, that the looks are not the most important - I know those points, I accept them, but I think that the looks are the most important for most people thinking of switching.

That said - I know very well that this argument may seem superficial to many - but that is how most users think and feel.

---

### Post by jerrylamos on 2008-11-04
In my humble opinion,
Rule #1!
Jaunty should RUN for the average joe user!

The fancy stuff can be there, available for the enthusiast.

Intrepid FORGOT RULE #1!

Scan back over Installation & Upgrades.  Any number of people are screwed because they did an upgrade from 8.04 without knowing 8.10 compiz hangs pc's with some common Intel graphics chips. See bug #259385.

They get a black screen and can't run.  Period.  Can't get their old files, they are stuck.  They are out of a running computer.  The install doesn't work.  Since it's an "upgrade" as recommended by Ubuntu, they have nothing to fall back on.  

There's finally a fix which disables compiz for the affected chips but it didn't make it into the release code.   Two months lead time on bug #259385 wasn't enough.

The crucial error was making compiz DEFAULT without checking to see if it would run on ALL the expected Ubuntu users.

And yes there are workarounds for those of us who can poke around forums long enough.  I'd hazard many will try Ubuntu, get screwed, and trash Ubuntu.

Now I'd expect the developers to be running high end machines, but perhaps they would like Ubuntu to run for us ordinary users.  O.K., we get on Alpha at an early stage, but the "won't run" bugs aren't worked on.  Maybe they are busy working getting fancy new features to work.

Some of us ordinary users will try Jaunty soon.  Hopefully they will be ankle biters like some fancy stuff doesn't work or some optional extra doesn't or some new feature is broken.  Please don't put out a Jaunty that hangs basic operations like boot like Intrepid does.

Thanks much, Jerry

---

### Post by Merk42 on 2008-11-04
In the week Ibex has been out there have been so many threads asking for a new theme (again). Maybe that means something?

I'd like to tackle the two most common negative responses to the idea

1. (which I hear SO often it drives me insane) "I don't care how it looks, fix the bugs, make it run faster. That's more important"
The team fixing the bugs are an entirely different team than that working on the look.  So time spent on the theme would **not** be time lost on fixing bugs.

2. "Users can just download a theme"
First impressions are important. If Ubuntu ever gets demoed in a brick & mortar store, you can bet they'll have on the default theme.

Here's a much longer hypothetical:
The job of a theme is to be visualy appealing, yes? And with so many threads asking for a new theme, it seems that the default fails in this regard (for the majority of people).
Say Ubuntu released a web browser in Jaunty. Only, it didn't render a lot of pages properly, so it really didn't do its job.  Would you like it if everyone's response was "just go download firefox/epiphany/opera"?  No, you'd want to Ubuntu to fix on the flaw that came with Jaunty

---

### Post by Slug71 on 2008-11-04
Maybe the devs should just change the Theme to shut some of these guys up that just dont get STABILITY is way more important!!!!!:mad:

---

### Post by ronacc on 2008-11-04
I will make this prediction . When and if they ever do change the theme it won't matter what they change it to . This thread will be in every dev forum because one theme will never please everone .

---

### Post by Merk42 on 2008-11-04
> **Slug71 said:**
> Maybe the devs should just change the Theme to shut some of these guys up that just dont get STABILITY is way more important!!!!!:mad:

Did you even read my post???

> **Merk42 said:**
> 
1. (which I hear SO often it drives me insane) "I don't care how it looks, fix the bugs, make it run faster. That's more important"
The team fixing the bugs are an entirely different team than that working on the look.  So time spent on the theme would **not** be time lost on fixing bugs.

---

### Post by ronacc on 2008-11-04
we certainly read your post and believe me when I say that I would love to see Ubuntu ship with the best and most beautiful look of ANY OS . I just do not see that as nearly as important as a smoothly WORKING desktop . 
I suppose no one EVER downloads a new theme for windows or apple .
  Your example of a browser that does not render correctly is totaly bogus . That would be a REAL bug as opposed to a theme that someone dosen't like which is a matter of taste and 100% certain to happen no matter what theme is default.

---

### Post by Merk42 on 2008-11-04
Well I give up

You can't seem to get it through your head that a good theme and well working desktop are not mutually exclusive.

---

### Post by ikt on 2008-11-05
To me the biggest amount of complaining I see happening is when everyone upgrades to the latest version, for many people so many things break it requires a complete reinstall.

I think there are a lot of things that need to be done and people are working to get those things done, we just have to give it time.

---

### Post by ronacc on 2008-11-05
> **Merk42 said:**
> Well I give up

You can't seem to get it through your head that a good theme and well working desktop are not mutually exclusive.

Who said they were mutualy exlcusive ? I certainly never did . I personaly do not remember a single post in any of the multiple itterations of this thread going all the way back to Hoary ( as I earlier provided a link to ) that made a statement like that .  So lets just agree to disagree on the matter of priority .

---

### Post by Jay_Bee on 2008-11-05
You can't prioritize stability over new theme, those two things are done by two different teams. So really, while the "stability" team is working on stability, the artwork team should also work on stability because that is more important (even when they have no clue about it)?

---

### Post by ronacc on 2008-11-05
You certainly can prioritize them . Since I am playing the "bad guy " here I'll ask the question , considering the results so far, wouldn't the money spent on the "paid artwork team "have been better spent else where ? And they had better have a clue because the theme interacts with the desktop , for instance a theme that required "desktop effects" would be a no go because it would shut out those with lesser hardware .Why am I doing this ? I don't have a dog in this fight , I customise ANY distro shortly after first boot , I have my own tastes and don't expect the world to cater to them .

---

### Post by yuminig on 2008-11-05
I hope jaunty has a new powerful and unique 3d engine that can par up with microsoft's directx

---

### Post by phoenix_snake on 2008-11-05
> **yuminig said:**
> I hope jaunty has a new powerful and unique 3d engine that can par up with microsoft's directx
lol ubuntu cannot change opengl, its an upstream project and forking it would make things worse.

---

### Post by yuminig on 2008-11-05
> **phoenix_snake said:**
> lol ubuntu cannot change opengl, its an upstream project and forking it would make things worse.

that's the problem with linux. everyone has their own project it's like there are no standardized or unification

---

### Post by Merk42 on 2008-11-05
> **ronacc said:**
> You certainly can prioritize them . Since I am playing the "bad guy " here I'll ask the question , considering the results so far, wouldn't the money spent on the "paid artwork team "have been better spent else where ? 

I never considering the money aspect I always considered talent and time.  Regardless of the whole priority issue (I btw think they´re **equally** important). Does anyone know how the budget for Ubuntu is even set up?

---

### Post by Slug71 on 2008-11-05
> **yuminig said:**
> I hope jaunty has a new powerful and unique 3d engine that can par up with microsoft's directx

All i can say is, :lolflag::lolflag:


> **yuminig said:**
> that's the problem with linux. everyone has their own project it's like there are no standardized or unification

Thats what LSB is for. LSB 4.0 is supposed to be a big step forward and should be out in a few days.

---

### Post by Slug71 on 2008-11-05
> **Jay_Bee said:**
> You can't prioritize stability over new theme, those two things are done by two different teams. So really, while the "stability" team is working on stability, the artwork team should also work on stability because that is more important (even when they have no clue about it)? 

You realize that if the Artwork Team do something wrong or forget something or anything that goes wrong which is likely and makes the theme have issues with Gnome or Compiz that the Stability Team then has to work on fixing things right? As well as trying to fix and tie in new and better features as well as LOTS of broken stuff already in Ubuntu.


Just download a community Theme and install it. You can also get Icon sets and Wallpapers and anything for the Desktop and it will take you 2 mins.
There a whole category in the Forum dedicated to Desktop Effects and Customization.

---

### Post by yuminig on 2008-11-05
Let's just hope everyone complies, they already have problems with debian

---

### Post by phoenix_snake on 2008-11-05
for the last time the art team is completely different for regular developers in **organized** projects so focusing on art should have no effect on stability unless of course the regular developers are drawing icons as well.

---

### Post by Naddiseo on 2008-11-05
> **yuminig said:**
> that's the problem with linux. everyone has their own project it's like there are no standardized or unification

Which is both its weakness, and its strength.

---

### Post by Changturkey on 2008-11-05
Integrate OpenGL 3.0/3.x more?

---

### Post by oomingmak on 2008-11-06
> **ronacc said:**
> Who said they were mutualy exlcusive ? I certainly never did

Oh, really?  You may not have actually used those particular words, but the implication is right there.

> **ronacc said:**
> I would love to see Ubuntu ship with the best and most beautiful look of ANY OS. I just do not see that as nearly as important as a smoothly WORKING desktop

You're asserting that a smoothly "*working *"desktop can only come at the expense of a "beautiful" desktop. You're suggesting that they cannot both be done at the same time, because any time or effort spent on improving aesthetics is somehow taking that time and effort away from stability and functionality. 

Therefore, one of these two options *has* to be prioritized over the other (because you can't have both) and seeing as a working desktop is more important than appearance, then aesthetics must be relegated because it is not "*nearly as important as a smoothly WORKING desktop*".

Let me ask you this; what's "more important"? Properly working audio or properly working wireless networking? Which of those two features should be abandoned to make way for the other?

> **ronacc said:**
> considering the results so far, wouldn't the money spent on the "paid artwork team "have been better spent else where?

So, again you're saying that resources (in this case "money") can either be spent on an artwork team **or **it can be spent elsewhere. That is the very definition of "mutual exclusivity".

The money issue is a red herring anyway. Canonical has a minuscule team of paid developers, with the vast majority of code coming from upstream. Therefore there is nothing to suggest that Ubuntu needs to spend money on a paid artwork team. It just needs a dedicated artwork team, period. These can be unpaid (as most of the people contributing to Free Software are) they just need to be properly vetted and have some ability (and not only be called upon at the very last minute).

In any event, this is all academic for me. I really couldn't care less one way or the other. I was simply pointing out that Mark Shuttleworth has made several comments about specifically improving Ubuntu's aesthetics, and if he means what he says, then something is going to have to change, because the existing structure for dealing with UI appearances issues is clearly not delivering.

---

### Post by Therion on 2008-11-06
Seems to me it's easier to fix an "ugly" distro than it is to fix an unstable distro.

A plethora of options for fixing the "ugly" default theme (I happen to like it, personally, but that's beside the point) already exist.  That's not the case for a buggy, unstable system that's flawed at it's foundation. 

I don't see the point in lots of flash and eye candy that will supposedly draw in this huge base of new users since an inherently unstable system will only serve to leave them with a bad taste in their mouth and with the opinion that "Linux/Ubuntu sucks" based on their exposure to an inherently flawed distro.  

Infrastructure, while rarely popular, really should be job/priority one.

---

### Post by Slug71 on 2008-11-06
This Thread needs to be killed. It appears the new direction is just looks.

Priority #1: Looks
         #2: Speed
         #3  Looks
         #4  Speed
         #5  see Priority #1&2.....

:popcorn::guitar:
:lolflag:

---

### Post by sdowney717 on 2008-11-06
that is an interesting idea about the terminal.
Why not a terminal gui.
A field where terminal commands run and on another side indexed searches for terminal commands and help on how to do terminal type commands with examples.
did you know that ps -aux lists out all running processes?
I keep coming across tidbits here or there. Would be nice to have it all in one search-able application.

---

### Post by plun on 2008-11-06
> **sdowney717 said:**
> that is an interesting idea about the terminal.
Why not a terminal gui.


I think we misses the goal with Ubuntus bug No1 using the terminal.

For 99% of all users the terminal is something for emergency repairs.

1% "nerds" including myself using it for more purposes. :)

---

### Post by Ramptu on 2008-11-06
I would like to Ubuntu use a color scheme like Maroon,Kaki and Navy Blue. That would still maintain its "earthy" scheme.

---

### Post by rbmorse on 2008-11-06
Make one, then. It's easy.  A bit tedious, but mostly a matter of selecting and picking colors for the various screen elements.

---

### Post by Gina on 2008-11-07
The only thing I've changed in the appearance of 8.10 is the wallpaper.  Just displayed one of my photos in Firefox - right-click - set as desktop background - done :)  It's a view of the goats in our home paddock looking across the valley.  For anyone who doesn't have a suitable photo, there are thousands on the web to choose from including other Ibex related.  We can't please everyone whatever is chosen - though, of course, we all have an opinion on what a majority of users might like - and they differ!

---

### Post by gnomeuser on 2008-11-07
And once again, upstream prevails with a solution..
[http://live.gnome.org/SystemSettings](http://live.gnome.org/SystemSettings)

---

### Post by Gina on 2008-11-07
Hooray!! :) :)

---

### Post by phoenix_snake on 2008-11-07
> **gnomeuser said:**
> And once again, upstream prevails with a solution..
[http://live.gnome.org/SystemSettings](http://live.gnome.org/SystemSettings)
yes but is it as good as mandriva control center or yast?

---

### Post by gnomeuser on 2008-11-07
> **phoenix_snake said:**
> yes but is it as good as mandriva control center or yast?

attention of detail and cross distro support.. I think we just surpass both. Additionally we have the chance to invoke PolicyKit to get away from the insane idea that such a tool needs to have its entire state elevated to root.

Really, this has every chance of being a superior tool and hopefully in time a full replacement for both. Bringing unity to yet another area within Linux.

I know the Fedora developers are looking into this project for F11 (though anyone would be a fool to assume that would mean such a project would only take 6 months to complete). I am hoping other distros will buy in to the idea and help develop it.

Here is a full set of whiteboard ideas for further inspiration:
[https://fedoraproject.org/wiki/Desktop/Whiteboards](https://fedoraproject.org/wiki/Desktop/Whiteboards)

---

### Post by Slug71 on 2008-11-07
> **gnomeuser said:**
> And once again, upstream prevails with a solution..
[http://live.gnome.org/SystemSettings](http://live.gnome.org/SystemSettings)

I like, I like=D>

Could be another step forward IMO.
Its things like this that will make more Windows users switch to Linux.

---

### Post by gnomeuser on 2008-11-07
> **Slug71 said:**
> I like, I like=D>

Could be another step forward IMO.
Its things like this that will make more Windows users switch to Linux.

Slightly off topic:

Must that be the measuring stick? Consider the millions and millions of non-computer users currently available for the picking, or the fact that more people have cellphones than computers making it a huge potential market for Linux (and the GNOME stack for that matter).

Stop thinking of Windows as our competitor, it is a dying platform, the desktop is a dying metaphor. If we make it the goal solely to beat Windows at its game that is the equivalent of attempting to breed a superior race of dinosaurs as the meteor is seen huddling towards the Earth.

---

### Post by Sand &amp; Mercury on 2008-11-07
> **yuminig said:**
> I hope jaunty has a new powerful and unique 3d engine that can par up with microsoft's directx
It already does, it's called OpenGL

---

### Post by ronacc on 2008-11-07
While Microsoft has suffered some setbacks recently , it would be dangerous to count them out . The desktop is too useful a metaphor to disapear anytime soon , it may change and extend but the very fact that it is so flexible will insure its continued existance . Similarly I do not see the standalone destop pc (as in the box on or under your desk) ceaseing to be popular anytime soon and for the same reason . Smartphone are wonderful "on the go " data acess devices but until flawless voice command becomes a reality they will remain essentialy useless for many of the things that a clunky old desktop excells at , try typing a multipage buisness letter on a blackberry or worse yet an Iphone and you will agree .I have several desktops , a full size laptop, an eeepc and a webenabled smartphone and if all but one had to go what would remain would be one of the desktops . By all means embrace other paradigms but dont dump the desktop just yet.

---

### Post by Gina on 2008-11-07
I don't think the desktop is anywhere near dying soon either - I too use a desktop in preference to a laptop.

---

### Post by plun on 2008-11-07
[B]
What's Up with the GNOME Linux Desktop?[/B]

[http://www.internetnews.com/dev-news/article.php/3782496/Whats+up+with+the+GNOME+Linux+Desktop.htm](http://www.internetnews.com/dev-news/article.php/3782496/Whats+up+with+the+GNOME+Linux+Desktop.htm)

Metacity....

---

### Post by Slug71 on 2008-11-07
> **gnomeuser said:**
> Slightly off topic:

Must that be the measuring stick? Consider the millions and millions of non-computer users currently available for the picking, or the fact that more people have cellphones than computers making it a huge potential market for Linux (and the GNOME stack for that matter).

Stop thinking of Windows as our competitor, it is a dying platform, the desktop is a dying metaphor. If we make it the goal solely to beat Windows at its game that is the equivalent of attempting to breed a superior race of dinosaurs as the meteor is seen huddling towards the Earth.


I just meant that slightly OT.
I think at the moment Linux scares a lot of people because its a different enviroment. Things like that will make the transition easier.
I don't see Windows as a competitor but it would be nice to have more people using it and being interested in it.

---

