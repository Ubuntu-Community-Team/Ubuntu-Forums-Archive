---
title: "Synaptic removed in Lucid?"
date: 2010-03-04
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Dragonbite on 2010-03-04
I have heard that Synaptic is being phased out for the Software Center.

For most purposes, that probably isn't going to be too bad, but thre is a feature in Synaptic that I don't see is available in teh Software Center.

I'm talking about the ability to back up the list of applications installed on your system  to a text file, which can then be easily pulled into Synaptic and by clicking "Apply", have all of your programs installed on a new system.

Does anybody know anything about this?

---

### Post by sisco311 on 2010-03-04
They plan to make Ubuntu Software Center a viable alternative to Synaptic in Ubuntu 10.10

[uwiki]SoftwareCenter#Roadmap[/uwiki]

---

### Post by FuturePilot on 2010-03-04
When it does get removed it will still be available in the repos.

---

### Post by arnab_das on 2010-03-04
i think its a very good idea.

however i'm not sure if such a huge switch is possible in lucid lynx.

---

### Post by Shpongle on 2010-03-04
> **Dragonbite said:**
> I have heard that Synaptic is being phased out for the Software Center.

For most purposes, that probably isn't going to be too bad, but thre is a feature in Synaptic that I don't see is available in teh Software Center.

I'm talking about the ability to back up the list of applications installed on your system  to a text file, which can then be easily pulled into Synaptic and by clicking "Apply", have all of your programs installed on a new system.

Does anybody know anything about this?
 not sure , but i didnt know about that feature , thanks for sharing

---

### Post by The Toxic Mite on 2010-03-04
If synaptic was to be removed in 10:04 or 10:10, there better be a similar package installation interface in the Software Centre.

---

### Post by Madspyman on 2010-03-04
](*,)

---

### Post by VCoolio on 2010-03-04
I don't really care; I do all package management in the commandline which is much faster than a gui. I do think ubuntu could use an app from which to do everything, instead of having 'add/remove', synaptic, update manager and also a software sources entry in the menus. I hope the software center is going to be all that in one.

---

### Post by Lightstar on 2010-03-04
I'd find it ironic to install it from the repos, it's like installing an installer to install other things.

I don't know how well I will live without synaptic.

---

### Post by Dragonbite on 2010-03-04
> **DillByrne said:**
> not sure , but i didnt know about that feature , thanks for sharing

It can be done with code, though, but part of Ubuntu's appeal is for the average person to do everything WITHOUT having to rely on the command line.

---

### Post by PC_load_letter on 2010-03-04
Remove Synaptic? Are these guys nuts????? How could someone install individual libraries then, the dev versions, if, God forbid, you plan to compile some code? Or how about Python modules? 

Using **sudo apt-get install** is not that convenient when there are a few libraries. Synaptic is a brilliant compromise between the power of CLI tools w/ GUI. 

This is really depressing if it is indeed true. Unless I'm missing something, in such case, someone please enlighten me.

---

### Post by FuturePilot on 2010-03-04
> **PC_load_letter said:**
> Remove Synaptic? Are these guys nuts????? How could someone install individual libraries then, the dev versions, if, God forbid, you plan to compile some code? Or how about Python modules? 

Using **sudo apt-get install** is not that convenient when there are a few libraries. Synaptic is a brilliant compromise between the power of CLI tools w/ GUI. 

This is really depressing if it is indeed true. Unless I'm missing something, in such case, someone please enlighten me.

If you need any of those things you probably know enough that you can install Synaptic from the repositories.

---

### Post by swoll1980 on 2010-03-04
```
sudo apt-get install synaptic
```

---

### Post by jrothwell97 on 2010-03-04
> **PC_load_letter said:**
> Remove Synaptic? Are these guys nuts????? How could someone install individual libraries then, the dev versions, if, God forbid, you plan to compile some code? Or how about Python modules?

Then you install Synaptic. However, considering the majority of users probably don't want or need to compile software/install individual libraries/install dev versions, it makes sense to save space by not including this functionality by default.

Despite the fact someone, somewhere in the world probably uses their computer to compose music based upon the decimal places of pi, Windows does not include an app called SongPie. There's a reason for that. ;)

---

### Post by PC_load_letter on 2010-03-04
> **jrothwell97 said:**
> Then you install Synaptic. However, considering the majority of users probably don't want or need to compile software/install individual libraries/install dev versions, it makes sense to save space by not including this functionality by default.

Despite the fact someone, somewhere in the world probably uses their computer to compose music based upon the decimal places of pi, Windows does not include an app called SongPie. There's a reason for that. ;)

Great, completely understandable, but could the fact that it will replaced by the software center mean that it will be get less and less attention? Or that it may cause conflicts or problems with other parts of the system?

---

### Post by Mr. Picklesworth on 2010-03-04
> **PC_load_letter said:**
> Remove Synaptic? Are these guys nuts????? How could someone install individual libraries then, the dev versions, if, God forbid, you plan to compile some code? Or how about Python modules? 

Using **sudo apt-get install** is not that convenient when there are a few libraries. Synaptic is a brilliant compromise between the power of CLI tools w/ GUI. 

This is really depressing if it is indeed true. Unless I'm missing something, in such case, someone please enlighten me.

That's where the whole “making software-center a viable alternative” part comes in. Right after Karmic, software-center has listed every package available, as Synaptic does, and that has been given a lot of attention throughout Lucid's development. At this point it does subcategories, including a really thoughtful arrangement for all kinds of development tools. There is also a good one-click route for installing a package so you don't need to open its information page to do so any more.

The search feature is excellent, too, lack of stemming (and Tracker :b) aside.

Granted, Synaptic does a nice job presenting dependencies and the like before going on to install stuff (software-center hides those intricacies for now, though it's intended to present fairly sophisticated information when it is really important to, at some point). Still, software-center is rapidly approaching excellent :)

Oh, and did I mention reviews and ratings, which are incoming?
It also really nicely lists packages that come from different sources, so an extra repository can be examined individually. Synaptic does that, too, but elegance enhances the functionality in this case by making it something that's actually natural to do.

---

### Post by matthew on 2010-03-04
As of today's updates of alpha3, Synaptic is still in the default installation. I have heard absolutely nothing about it being removed from the default installation and sincerely doubt the idea is true (since I've been involved with the entire development cycle since the UDS and this is the first I have heard of it). Granted, I am not omniscient...

---

### Post by RiceMonster on 2010-03-04
> **PC_load_letter said:**
> Remove Synaptic? Are these guys nuts????? How could someone install individual libraries then, the dev versions, if, God forbid, you plan to compile some code? Or how about Python modules? 

I do that with command line package managers all the time...

---

### Post by Mr. Picklesworth on 2010-03-04
> **matthew said:**
> As of today's updates of alpha3, Synaptic is still in the default installation. I have heard absolutely nothing about it being removed from the default installation and sincerely doubt the idea is true (since I've been involved with the entire development cycle since the UDS and this is the first I have heard of it). Granted, I am not omniscient...

Oh, yes, I forgot to mention! Don't worry, Synaptic is *not* being removed from Lucid. It isn't being removed until Software Center does everything it does, better, and with impeccable reliability. That's 10.10, probably, though maybe 11.04, or maybe later depending on where things go. It's being done quite carefully :)

---

### Post by 3rdalbum on 2010-03-04
Remember, whenever you run Update Manager, it actually calls Synaptic to draw the progress dialog box. Whenever you use AptURL it does the same thing. And whenever you try to set up Samba when you don't have it installed, it will call Synaptic to install it.

Ubuntu 10.04 will ship with Synaptic; there's not enough time to patch everything to call Software Center. Maybe 10.10 will have everything migrated across, but you can always use Software Center to install Synaptic.

---

### Post by doorknob60 on 2010-03-05
sudo apt-get install synaptic? Problem solved.

> Great, completely understandable, but could the fact that it will replaced by the software center mean that it will be get less and less attention?

I'm pretty sure Synaptic is maintained by Debian, so no, it wouldn't get less attention (at least I wouldn't think so).

---

### Post by rudihawk on 2010-03-05
What is so wrong with synaptic in the first place? If it ain't broke, why change it? It seems like they adding stuff for the sake of adding stuff.

---

### Post by Keyper7 on 2010-03-05
> **rudihawk said:**
> What is so wrong with synaptic in the first place? If it ain't broke, why change it? It seems like they adding stuff for the sake of adding stuff.

You know, there exists a [HUGE AND DETAILED EXPLANATION PAGE](https://wiki.ubuntu.com/SoftwareCenter) about the Software Center which is the first occurrence for "ubuntu software center" in Google.

You might not agree with its contents, but don't talk about it like it is a mysterious, obscure thing developed in complete silence.

---

### Post by haydoni on 2010-03-05
> **Keyper7 said:**
> You know, there exists a [HUGE AND DETAILED EXPLANATION PAGE](https://wiki.ubuntu.com/SoftwareCenter) about the Software Center which is the first occurrence for "ubuntu software center" in Google.

You might not agree with its contents, but don't talk about it like it is a mysterious, obscure thing developed in complete silence.

from the huge page: "The version shipped in Ubuntu 10.04 should be at least 2.0." Does this mean we are expecting a software centre upgrade before 10.04, it's not currently in lucid, along with a fancy green bag?

---

### Post by bigbrovar on 2010-03-05
aptitude ftw

---

### Post by forrestcupp on 2010-03-05
> **swoll1980 said:**
> ```
sudo apt-get install synaptic
```

Right.  I guess that will be another thing we need to add to the post-installation list.

I hope the Software Center gets better.  It seems too clunky and slow.  I didn't spend much time with it, but I didn't quickly and easily find a way to set it up to install a lot of things at once.  It seemed like you can only install one thing at a time.  But I didn't spend a lot of time trying to figure it out.

---

### Post by Dragonbite on 2010-03-05
> **Mr. Picklesworth said:**
> Oh, yes, I forgot to mention! Don't worry, Synaptic is *not* being removed from Lucid. It isn't being removed until Software Center does everything it does, better, and with impeccable reliability. That's 10.10, probably, though maybe 11.04, or maybe later depending on where things go. It's being done quite carefully :)

Ok, as long as everything is covered. I only recenlty learned about the ability to backup a list of programs installed and didn't want it to dissappear just as I stared using it ;)  That's becoming part of my backup scheme which includes getting me up-and-running when I upgrade to the next distro version ;)

> **rudihawk said:**
> What is so wrong with synaptic in the first place? If it ain't broke, why change it? It seems like they adding stuff for the sake of adding stuff.

The rationale of putting Synaptic (install/edit/update) and cleanup (computer janitor) and such into one "omniscient" controller makes sense.  Just keep it _just_ that, otherwise why re-invent the wheel; just reconfigure Yast (please ... don't).

---

### Post by PC_load_letter on 2010-03-06
> **Mr. Picklesworth said:**
> That's where the whole “making software-center a viable alternative” part comes in. Right after Karmic, software-center has listed every package available, as Synaptic does, and that has been given a lot of attention throughout Lucid's development. At this point it does subcategories, including a really thoughtful arrangement for all kinds of development tools. There is also a good one-click route for installing a package so you don't need to open its information page to do so any more.

The search feature is excellent, too, lack of stemming (and Tracker :b) aside.

Granted, Synaptic does a nice job presenting dependencies and the like before going on to install stuff (software-center hides those intricacies for now, though it's intended to present fairly sophisticated information when it is really important to, at some point). Still, software-center is rapidly approaching excellent :)

Oh, and did I mention reviews and ratings, which are incoming?
It also really nicely lists packages that come from different sources, so an extra repository can be examined individually. Synaptic does that, too, but elegance enhances the functionality in this case by making it something that's actually natural to do.

Good to hear, then there would be no problem then. The software center in Karmic is nowhere near Synaptic's functionality, hence my initial shock.

---

### Post by Psumi on 2010-03-06
I don't use the default ubuntu nor gnome install. I have xfce4, and I don't use synaptic, I use apt-get.

Problem solved.

---

### Post by phrostbyte on 2010-03-06
Synaptec feels like a sysadmin tool, I support the decsion to remove it in the default install, and replace it with something more user friendly and social networky (hopefully with reviews/screenshots). :D Synaptec is still very useful for advanced package management tasks, but not something I would expect to be there by default.

---

### Post by Ewingo401 on 2010-03-06
I prefer to use sudo apt-get install "x" to install my software, but synaptic is my preferred method of searching for software in the repos.

---

### Post by mpt on 2010-03-06
> **forrestcupp said:**
> I hope the Software Center gets better.  It seems too clunky and slow.  I didn't spend much time with it, but I didn't quickly and easily find a way to set it up to install a lot of things at once.  It seemed like you can only install one thing at a time.  But I didn't spend a lot of time trying to figure it out.

Ubuntu Software Center 1.0 was, and is, faster at installing multiple things than Synaptic — because it didn’t wait until after you’d chosen the final item before it started downloading all the others.

However, my design made many people — including you, apparently — think USC could install only one thing at a time. I was surprised by this, but even if I’d known that ahead of time, I doubt I’d have designed it any differently. Ideally we would have shown installation/removal progress inside the software item screen, but since we didn’t have time to implement that, I specified that it should switch to the “In Progress” screen whenever starting something when nothing was already happening. I guess that made people think they couldn’t switch back and do anything else.

In Lucid we got time to implement progress display for an item both inside the list and on the software item screen, so we don’t need to switch to the “In Progress” screen, so it should be more obvious that you can do multiple things at once.

For a future version, it would be awesome if someone juiced up the [aptdaemon]("https://launchpad.net/aptdaemon") engine (which USC uses) so that it can download the next thing at the same time as it’s installing/removing the current thing.

---

### Post by takisan on 2010-03-06
At least there's going to be APT and Aptitude. I prefer to use Synaptic because of the check and apply mass download and install method to get stuff done when going out to eat.

---

### Post by MasterNetra on 2010-03-06
Its in Alpha 3 still so I dunno if there is any truth in them actually removing it from default install. But software center seems to be better then in Karmic.

> **sisco311 said:**
> They plan to make Ubuntu Software Center a viable alternative to Synaptic in Ubuntu 10.10

[uwiki]SoftwareCenter#Roadmap[/uwiki]

Aye and no where do they say they are gonna remove Synaptic. So I guess they most likely have no plans on removing it any time soon from the default install and probably never from repo (Unless it becomes a dead app at some point).

---

### Post by mpt on 2010-03-06
> **MasterNetra said:**
> Aye and no where do they say they are gonna remove Synaptic. So I guess they most likely have no plans on removing it any time soon from the default install and probably never from repo (Unless it becomes a dead app at some point).

For Ubuntu 10.10, Canonical developers will be concentrating on making the software purchase system bulletproof. So whether USC 3.0 *also* does everything useful that Synaptic did will, I expect, be up to volunteer developers. And because they’re volunteers, it’s pretty much impossible to predict what they’ll have the time and interest to implement over the next six months.

If anyone reading this is interested in helping out, a simple task you could start with would be porting Synaptic’s “Remove Completely” command to [aptdaemon]("http://launchpad.net/aptdaemon") (if it’s not implemented already), and then adding it to USC’s “File” menu.

---

### Post by Psumi on 2010-03-07
> **mpt said:**
> For Ubuntu 10.10, Canonical developers will be concentrating on making the software purchase system bulletproof. So whether USC 3.0 *also* does everything useful that Synaptic did will, I expect, be up to volunteer developers. And because they&#8217;re volunteers, it&#8217;s pretty much impossible to predict what they&#8217;ll have the time and interest to implement over the next six months.

If anyone reading this is interested in helping out, a simple task you could start with would be porting Synaptic&#8217;s &#8220;Remove Completely&#8221; command to [aptdaemon]("http://launchpad.net/aptdaemon") (if it&#8217;s not implemented already), and then adding it to USC&#8217;s &#8220;File&#8221; menu.

Will codec packages force us to purchase them even if we get them from another repo like medibuntu?

Obviously based on GeoIP System so that only countries that observe patent laws (IE: USA) get charged.

Will apt-get also be changed to force people to pay for packages? IE: ask for a download key that's encrypted?

---

### Post by Giant Speck on 2010-03-07
> **Psumi said:**
> Will codec packages force us to purchase them even if we get them from another repo like medibuntu?

Obviously based on GeoIP System so that only countries that observe patent laws (IE: USA) get charged.

Will apt-get also be changed to force people to pay for packages? IE: ask for a download key that's encrypted?

Yes.  And from Lucid on, Ubuntu will cost $99.95 and you will need to enter a key upon installation, or else Canonical will deactivate your computer.

---

### Post by Khakilang on 2010-03-07
At first I got confuse with Add/Remove software with Synaptic. I mess up my software with broken dependencies error message. After a while I came to understand Synaptic but I hardly use with 9.10. The Ubuntu Software center is all I ever use. I hardly need any new software apart from what I have install. But its good to have just in case.

---

### Post by Psumi on 2010-03-07
> **Giant Speck said:**
> Yes.  And from Lucid on, Ubuntu will cost $99.95 and you will need to enter a key upon installation, or else Canonical will deactivate your computer.

You don't know when to not joke do you.

I was being serious.

---

### Post by NCLI on 2010-03-07
> **Psumi said:**
> You don't know when to not joke do you.

I was being serious.

In Lucid, you can easily see PPAs from the USC, so I can't see how Canonical could prevent you from using the Medibuntu repo, or why they would want to.

---

### Post by dragos240 on 2010-03-07
Well hey, at least synaptic is in the repo for lucid.

---

### Post by Nerd King on 2010-03-07
Synaptic's an excellent piece of software, much lighter than USC. I hope that USC manages to trim some of the fat so it can become a truly useful application, as it's likely to be a program inexperienced users see often (like Apple's App Store).

---

### Post by Psumi on 2010-03-07
> **NCLI said:**
> In Lucid, you can easily see PPAs from the USC, so I can't see how Canonical could prevent you from using the Medibuntu repo, or why they would want to.

Did I say they wouldn't?

I said they wouldn't allow you to install certain packages from it (IE: w32codecs, w64codecs, etc.)

---

### Post by MasterNetra on 2010-03-07
> **mpt said:**
> For Ubuntu 10.10, Canonical developers will be concentrating on making the software purchase system bulletproof. So whether USC 3.0 *also* does everything useful that Synaptic did will, I expect, be up to volunteer developers. And because they&#8217;re volunteers, it&#8217;s pretty much impossible to predict what they&#8217;ll have the time and interest to implement over the next six months.

If anyone reading this is interested in helping out, a simple task you could start with would be porting Synaptic&#8217;s &#8220;Remove Completely&#8221; command to [aptdaemon]("http://launchpad.net/aptdaemon") (if it&#8217;s not implemented already), and then adding it to USC&#8217;s &#8220;File&#8221; menu.

True, all this "they're removing synaptic" is unfounded still as they have made no claims that I'm aware of that they will be doing such a thing. People are just jumping to conclusions. Bettering Software Center != Synaptic Removal. We will just have to wait and see. I have my doubts though about them removing it for Lucid. 10.10 maybe, again we will have to wait and see.

---

### Post by Slug71 on 2010-03-07
> **MasterNetra said:**
> True, all this "they're removing synaptic" is unfounded still as they have made no claims that I'm aware of that they will be doing such a thing. People are just jumping to conclusions. Bettering Software Center != Synaptic Removal. We will just have to wait and see. I have my doubts though about them removing it for Lucid. 10.10 maybe, again we will have to wait and see.

Well it seems the Blueprint has changed a little. The overall goal for USC was to have one program(USC) which rolls Computer Janitor, dpkg, gdebi, Add/Remove, Software Sources, Synaptic and maybe Update Manager into 1.

Lucid's USC was suppose to have Add/Remove, Synaptic, Software Sources done. And maybe gdebi or dpkg too. Cant remember. However i dont believe this will be done for Lucid anymore. Maybe 10.10 as we are already passed Feature Freeze for Lucid. 

But like i said earlier, it seems the blueprint has changed a little so im not really sure whats happening with it now and its likely to change again. We will just have to wait and see. I think Synaptic it safe in Lucid though.

I am also pretty sure that USC will have Packagekit as the backend, replacing aptdaemon, for 10.10 as work is under way in both PK and debconf to get the issues sorted out which is what led to PK being dropped in favour of USC and aptdaemon in the first place.

Here is the blueprint for Lucid
[https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-backend](https://blueprints.launchpad.net/ubuntu/+spec/foundations-lucid-software-center-backend)

however work hadnt got far enough for the change to happen in Lucid.
Should be done by PK v.0.6.3/4/5.

---

### Post by Post Monkeh on 2010-03-07
> **mpt said:**
> Ubuntu Software Center 1.0 was, and is, faster at installing multiple things than Synaptic — because it didn’t wait until after you’d chosen the final item before it started downloading all the others.


this may be true from the perspective of the time it takes to install a lot of software, but that's not the most important thing i don't think.
in synaptic i can select all the things i want to install in 5 minutes, click install, and go and do other things for the 30 minutes it takes to download and install them.

in USC, i have to click INTO each individual package i want to install, then click install, then wait while it processes that information (anywhere from 5 to 10 seconds) then go to my next package and begin installing it.
so while that 35 minute install time may be reduced to 30 thanks to it starting as soon as i clicked the first package, the time i actually spend working on it is increased to maybe 15 minutes.

in theory it's a good system, but i feel it requires the addition of an install button on each package that i can click without needing to go in to view the full description & thumbnail, and a simple "mark" button that lets me do things the synaptic way and choose all my packages then install them at the end, making the computer do one big calculation (presumably dependencies etc) instead of loads of little ones.

---

### Post by NCLI on 2010-03-07
> **Psumi said:**
> Did I say they wouldn't?

I said they wouldn't allow you to install certain packages from it (IE: w32codecs, w64codecs, etc.)

How, exactly, would they do this while still keeping the OS open source, and preventing easy workarounds?

---

### Post by mpt on 2010-03-07
> **Psumi said:**
> Will codec packages force us to purchase them even if we get them from another repo like medibuntu?

I don&#8217;t know how that would even work. How would Ubuntu know that a particular package from a third-party repository did the same job as a commercial package?

> *Will apt-get also be changed to force people to pay for packages? IE: ask for a download key that's encrypted?*

Obviously trying to &#8220;force&#8221; that in apt wouldn&#8217;t work, because people would just replace it with a copy of apt that didn&#8217;t have that requirement.

The mechanism we&#8217;ve discussed for commercial packages (though this is *highly* preliminary) is that when you buy something, it will be copied from the vendor&#8217;s PPA into your own personal private PPA. To apt, your PPA will be just another repository.

> **Nerd King said:**
> Synaptic's an excellent piece of software, much lighter than USC. I hope that USC manages to trim some of the fat so it can become a truly useful application, as it's likely to be a program inexperienced users see often (like Apple's App Store).

I could point out that Apple&#8217;s App Store is embedded bizarrely inside a music player, which is over **90 times** as &#8220;fat&#8221; as Ubuntu Software Center (software-center 1.16.1, 1630 kilobytes; iTunes 9.0.3 for Mac OS X, 147711 kilobytes).

But perhaps more interesting would be for you to give a specific example of the &#8220;fat&#8221; you&#8217;re referring to. What do you mean, exactly?

> **Post Monkeh said:**
> in theory it's a good system, but i feel it requires the addition of an install button on each package that i can click without needing to go in to view the full description & thumbnail,

&#8220;My name&#8217;s Post Monkeh, and [Ubuntu 10.04 was my idea]("http://lh5.ggpht.com/_FJH0hYZmVtc/S1z5ZQyTSVI/AAAAAAAAFgA/iVHekf8CnWk/s1600-h/image%5B7%5D.png").&#8221;

> *and a simple "mark" button that lets me do things the synaptic way and choose all my packages then install them at the end, making the computer do one big calculation (presumably dependencies etc) instead of loads of little ones.*

Except that it wouldn&#8217;t be &#8220;a simple &#8216;mark&#8217; button&#8221;. We would also need to provide an understandable way to see the list of pending changes, an understandable way of distinguishing whether a pending change was an installation, a reinstallation, a removal, a removal-with-settings, or a reconfiguration, an understandable way of resetting some or all of the pending changes, and an understandable way for marked changes to coexist alongside immediate changes. Synaptic has never presented (and, to be fair, never tried to present) any of these in a way suitable for a mass audience. And some it doesn&#8217;t manage at all: for example, mark something for removal and then choose &#8220;Mark All Upgrades&#8221;, and whoops, your selection gets forgotten.

---

### Post by Post Monkeh on 2010-03-07
> **mpt said:**
> 

“My name’s Post Monkeh, and [Ubuntu 10.04 was my idea]("http://lh5.ggpht.com/_FJH0hYZmVtc/S1z5ZQyTSVI/AAAAAAAAFgA/iVHekf8CnWk/s1600-h/image%5B7%5D.png").”] that'll help, good work, that post monkeh fella deserves a medal.



> Except that it wouldn’t be “a simple ‘mark’ button”. We would also need to provide an understandable way to see the list of pending changes, an understandable way of distinguishing whether a pending change was an installation, a reinstallation, a removal, a removal-with-settings, or a reconfiguration, an understandable way of resetting some or all of the pending changes, and an understandable way for marked changes to coexist alongside immediate changes. Synaptic has never presented (and, to be fair, never tried to present) any of these in a way suitable for a mass audience. And some it doesn’t manage at all: for example, mark something for removal and then choose “Mark All Upgrades”, and whoops, your selection gets forgotten.

i don't pretend to be a software designer so i don't know how simple or not something would be from a development standpoint, i meant simple for me ;)

obviously there has to be some change. while i find synaptic a great tool to use, i can understand that for a lot of people there simply is just too much information to digest.  i just hope that the right balance can be struck where it is easy to use for the new user, but still provides all the functionality that the experienced user appreciates. 
for me personally, i'm impatient, and moving from synaptic, where i can select multiple packages for installation then wait 5 seconds to see ALL the dependencies, to USC where it takes 5 seconds each time i install a single package, i just find it a little frustrating - but maybe in future versions that slight delay will be removed, which would actually negate the whole need for me having a multiple mark option at all.

it IS a nice piece of software from a usability POV. it's neatly laid out, and it's nice and easy to find what you're looking for, hopefully as it improves it will get to a point where installing a list of 30 apps can be as quick and painless (in *real* time terms AND *my* time terms) in USC as it is in synaptic.

---

### Post by zekopeko on 2010-03-07
> **mpt said:**
> The mechanism we&#8217;ve discussed for commercial packages (though this is *highly* preliminary) is that when you buy something, it will be copied from the vendor&#8217;s PPA into your own personal private PPA. To apt, your PPA will be just another repository.

Where would this PPA reside? On Launchpad tied to the users Ubuntu Single Sign-On account? Or on the users computer?

> I could point out that Apple&#8217;s App Store is embedded bizarrely inside a music player, which is over **90 times** as &#8220;fat&#8221; as Ubuntu Software Center (software-center 1.16.1, 1630 kilobytes; iTunes 9.0.3 for Mac OS X, 147711 kilobytes).

But perhaps more interesting would be for you to give a specific example of the &#8220;fat&#8221; you&#8217;re referring to. What do you mean, exactly?

Well the "Provided by Ubuntu" list brings my quad-core to its knees. Overall it fills sluggish when navigating around.

EDIT: Let me expand with some other thoughts since you are reading this thread.

Could we get more contrast in the list? Alternating rows could have a light grey/neutral-color so that the list isn't so bland and its easier to see where one app's short description ends and another one starts.

What is with that fugly background in the Departments (categories would be better since its no longer titled as a shop) screen? Having such stuff hardcoded is evil.
IMO the Departments screen could be much better, more beautiful. Hovering over the department should put a highlight box (with rounded corners) instead of simply turning the mouse pointer into a pointing hand. AFAIK you are using webkit to draw that (not sure about the rest of main pane) so why not create something really pretty since you have all of HTML and CSS at your fingertips?

---

### Post by mpt on 2010-03-08
> **zekopeko said:**
> Where would this PPA reside? On Launchpad tied to the users Ubuntu Single Sign-On account? Or on the users computer?

On Launchpad, most likely.

> *Well the "Provided by Ubuntu" list brings my quad-core to its knees. Overall it fills sluggish when navigating around.*

As the saying goes in Ubuntu, “[iz GTK boog]("http://launchpad.net/bugs/524567")”.

> *Could we get more contrast in the list? Alternating rows could have a light grey/neutral-color so that the list isn't so bland and its easier to see where one app's short description ends and another one starts.*

That could easily be confused with selection, especially now that in the Light themes the selection color is grey.

> *What is with that fugly background in the Departments (categories would be better since its no longer titled as a shop) screen? Having such stuff hardcoded is evil.*

So’s your mom.

> *IMO the Departments screen could be much better, more beautiful. Hovering over the department should put a highlight box (with rounded corners) instead of simply turning the mouse pointer into a pointing hand. AFAIK you are using webkit to draw that (not sure about the rest of main pane) so why not create something really pretty since you have all of HTML and CSS at your fingertips?*

“My name’s zekopeko, and [Ubuntu 10.04 was my idea]("http://imgur.com/CSzH3").”

---

### Post by ronacc on 2010-03-08
If Ubuntu is going to put commercial software in USC , getting a cut of the action and thereby "sanctioning" it , are they also going to take responsibility for its stability , bugs ,and patches ?

---

### Post by zekopeko on 2010-03-08
> **mpt said:**
> That could easily be confused with selection, especially now that in the Light themes the selection color is grey.

But it needs some contrast IMO. Banshee uses a light grey color to alternate between rows.

[http://i.imgur.com/1MmKY.png](http://i.imgur.com/1MmKY.png)

Thats with that new light theme.

> So&#8217;s your mom.

Not when fugly backgrounds and hardcoded values are in question ;)

> &#8220;My name&#8217;s zekopeko, and [Ubuntu 10.04 was my idea]("http://imgur.com/CSzH3").&#8221;

That looks super nice. Might want to rethink that (I'm guessing) basket thingy in the upper right corner. It looks like some kind of a weird smiley face.

Also, please explain this "My name's..." meme. I missed the memo on it.

---

### Post by zekopeko on 2010-03-08
> **ronacc said:**
> If Ubuntu is going to put commercial software in USC , getting a cut of the action and thereby "sanctioning" it , are they also going to take responsibility for its stability , bugs ,and patches ?

Why should they take the responsibility for it? Its from a 3rd party. Canonical would only be responsible for USC infrastructure.

---

### Post by psyke83 on 2010-03-08
> **zekopeko said:**
> Also, please explain this "My name's..." meme. I missed the memo on it.

Windows 7's [advertising]("http://www.youtube.com/watch?v=SnolmuFgW7w") [campaign]("http://www.youtube.com/watch?v=gnXVPwLLXHM"). It's better than [Seinfeld's]("http://www.youtube.com/watch?v=NNjGGFTVu-g"), though that isn't saying much... ;)

---

### Post by ronacc on 2010-03-08
> **zekopeko said:**
> Why should they take the responsibility for it? Its from a 3rd party. Canonical would only be responsible for USC infrastructure.

that they have "chosen" it for inclusion in the USC seems at least to imply that they have found it to be reasonably usable for its stated purpose .

---

### Post by MCVenom on 2010-03-08
> **ronacc said:**
> that they have "chosen" it for inclusion in the USC seems at least to imply that they have found it to be reasonably usable for its stated purpose .
I think what you're asking is if the "for purchase" programs will be held to the same standards as the free programs/packages contained in the repositories now (no viruses, no spyware, stability(?), etc.), is that it?

---

### Post by zekopeko on 2010-03-08
> **ronacc said:**
> that they have "chosen" it for inclusion in the USC seems at least to imply that they have found it to be reasonably usable for its stated purpose .

I'm going with no here. Canonical may provide some rough guidelines but bugs and stability of said software are the responsibility of the creator/seller. What Canonical will get is part of the price for giving a simple, robust distribution system for commercial software.

---

### Post by ronacc on 2010-03-08
My concern is that Ubuntu's USC is not compusa or amazon.com , if they allow caveat emptor to be the criterion for inclusion they run the risk of damaging their image .

---

### Post by VMC on 2010-03-08
I forgot about the mission of USC, and usually use Synaptic to remove Firefox, for example. Since reading what all's going on with USC on this topic, I decided to give it another try.

Normally I use Aptitude to do my dirty work, but since, Firefox is tied to meta packages, or parts of it anyway, I use Synaptic, because it gives me a list of what is going to be removed.

 Aptitude, if ones not careful, will attempt to remove the whole-ball-of-wax. I ended up not long ago removing gnome desktop by mistake.

So will USC also display what will also be remove so I don't make that mistake. 

I'm probably not making myself clear, but Synaptic has a dialog that list what's remove, what will be updated, so on.

 I just used USC to remove Firefox and it just did it. How can I prevent that in the future, or can I. That's one great benefit of Synaptic.

---

### Post by mpt on 2010-03-10
> **ronacc said:**
> that they have "chosen" it for inclusion in the USC seems at least to imply that they have found it to be reasonably usable for its stated purpose .

I doubt there will be any “choosing” involved.

> **VMC said:**
> Normally I use Aptitude to do my dirty work, but since, Firefox is tied to meta packages, or parts of it anyway, I use Synaptic, because it gives me a list of what is going to be removed … So will USC also display what will also be remove so I don't make that mistake.

You are mistaken in thinking that Firefox is “tied to meta packages”. ubuntu-desktop Recommends it, but does not Depend on it.

So if you remove Firefox, USC doesn’t tell you what else it will remove (it’s just branding and Ubuntu integration stuff). But if you try to remove something like, say, libgtk2.0-0, USC gives you the laundry list of things that will also be removed if you continue.

---

