---
title: "The Packagekit Thread."
date: 2009-04-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Slug71 on 2009-04-27
Hopefully it will really happen this time round. One of the big features i've been looking forward to.

---

### Post by erkiha on 2009-04-28
What is this big and better feature in Packagekit that we do not have now?

---

### Post by Neon Lights on 2009-04-28
Well, Kubuntu has it already, right?
Here's to hoping Ubuntu gets it integrated in Karmic too! :) That'd be super awesome.

---

### Post by gnomeuser on 2009-04-28
> **erkiha said:**
> What is this big and better feature in Packagekit that we do not have now?

PolicyKit integration so I don't need to type my sudo password every 5 secs to install updates. This makes it much easier to set defaults for your users with superb granularity.

Aside that PackageKit is a package system agnostic way application developers can rely on to install support on demand. This means we don't not have to patch applications to have hooks. It is a win for developers and for users. Imagine a world where if a font isn't installed e.g. you will be offered to install it, the same thing can happen for typing in commands in the terminal if the program isn't installed you will be offered the option. This world exists today already, and it is expanding every day.

PackageKit allows some exciting web integration, there is a mozilla pluging which communicates with PackageKit. Now imagine going to a review of an application and at the buttom there will be a single click way to install the application (and you could even be told if it was available in the same version or better as was being reviewed - or if it is regretably not available in your distro). Application developers could do the same thing on their websites, instead of having a long boring list of how to install on different distros it would just be "the right way" and source code.

PackageKit also lets us abstract our tools from the packaging backend. If we ever (and I hope we do soon) find ourselves in a position where replacing dpkg with a new system and evolution of the codebase isn't a viable option. Then you can code your replacement and add a packagekit backend, and your existing tools and all the existing integration will remain functional for both. It makes it viable to experiment with this kind of progress which would otherwise not be viable. (naturally there is also the large repo of packages to convert and maintainer retraining to content with but the major technical hurdle of having your package manager ingrained into your system is gone).

Aside that PackageKit maintains a lot of functionality and well tested and well designed usable UI we can use. This cuts down the time needed to maintain existing tools, time that can be spend otherwise. Additionally if the same tools are available it makes it easier for users to switch without losing familiarity and makes for a smoother experience overall for this group.

PackageKit already has some very useful additions to package management I haven't seen before, like hooking up to network manager to check if you are on a mobile internet connection and it will inform you, asking if you are on a metered connection which might make the update expensive. 

The integration, abstraction and the little bits polish makes PackageKit a very attractive bit of technology.

---

### Post by SKLP on 2009-04-28
I like PackageKit(tried it in Fedora) for the nice unattended upgrades. ;-)
Think there is a problem with using it in ubuntu though, mainly because APT askes you questions when you install stuff ( "Do you want to replace config file X?", etc). Though this could be solves by defaulting to some nice behaviour (maybe "yes"), which would also benefit the users in other ways...
It's time for PackageKit! (hopefully)

---

### Post by gnomeuser on 2009-04-28
> **SKLP said:**
> I like PackageKit(tried it in Fedora) for the nice unattended upgrades. ;-)
Think there is a problem with using it in ubuntu though, mainly because APT askes you questions when you install stuff ( "Do you want to replace config file X?", etc). Though this could be solves by defaulting to some nice behaviour (maybe "yes"), which would also benefit the users in other ways...
It's time for PackageKit! (hopefully)

I agree debhelper is anything but, it is in fact my number 1 annoyance with dpkg.

---

### Post by dudude on 2009-04-28
I don't know about Synaptic, but KPackageKit is a large step up from Adept, at least in terms of stability.

---

### Post by xens on 2009-04-28
> **gnomeuser said:**
> PolicyKit integration so I don't need to type my sudo password every 5 secs to install updates. This makes it much easier to set defaults for your users with superb granularity.

Aside that PackageKit is a package system agnostic way application developers can rely on to install support on demand. This means we don't not have to patch applications to have hooks. It is a win for developers and for users. Imagine a world where if a font isn't installed e.g. you will be offered to install it, the same thing can happen for typing in commands in the terminal if the program isn't installed you will be offered the option. This world exists today already, and it is expanding every day.

PackageKit allows some exciting web integration, there is a mozilla pluging which communicates with PackageKit. Now imagine going to a review of an application and at the buttom there will be a single click way to install the application (and you could even be told if it was available in the same version or better as was being reviewed - or if it is regretably not available in your distro). Application developers could do the same thing on their websites, instead of having a long boring list of how to install on different distros it would just be "the right way" and source code.

PackageKit also lets us abstract our tools from the packaging backend. If we ever (and I hope we do soon) find ourselves in a position where replacing dpkg with a new system and evolution of the codebase isn't a viable option. Then you can code your replacement and add a packagekit backend, and your existing tools and all the existing integration will remain functional for both. It makes it viable to experiment with this kind of progress which would otherwise not be viable. (naturally there is also the large repo of packages to convert and maintainer retraining to content with but the major technical hurdle of having your package manager ingrained into your system is gone).

Aside that PackageKit maintains a lot of functionality and well tested and well designed usable UI we can use. This cuts down the time needed to maintain existing tools, time that can be spend otherwise. Additionally if the same tools are available it makes it easier for users to switch without losing familiarity and makes for a smoother experience overall for this group.

PackageKit already has some very useful additions to package management I haven't seen before, like hooking up to network manager to check if you are on a mobile internet connection and it will inform you, asking if you are on a metered connection which might make the update expensive. 

The integration, abstraction and the little bits polish makes PackageKit a very attractive bit of technology.

Thanks your explanations!

---

### Post by Merk42 on 2009-04-28
> **dudude said:**
> I don't know about Synaptic, but KPackageKit is a large step up from Adept, at least in terms of stability.

It's called KPackageKit? Really? I guess KitPackager would be pronounceable.  KSometimes I KThink the naming of KProgrames are KStupid.

Not that GNOME is any GBetter.

---

### Post by ronacc on 2009-04-28
"Do you want to replace config file X?" is exactly the kind of question I INSIST on being asked . I often have customised cofig files that I do not want messed with and it is far less anoying to me to make a case by case selection than to try to undo the dammage done by an installer that thought it knew better than me how my system should work . With that said , as long as one of the options is "always ask" I can accept that .The increased functionality would be welcome as long as it doesn't come at too high a price .

---

### Post by gnomeuser on 2009-04-28
> **ronacc said:**
> "Do you want to replace config file X?" is exactly the kind of question I INSIST on being asked . I often have customised cofig files that I do not want messed with and it is far less anoying to me to make a case by case selection than to try to undo the dammage done by an installer that thought it knew better than me how my system should work . With that said , as long as one of the options is "always ask" I can accept that .The increased functionality would be welcome as long as it doesn't come at too high a price .

The point is finding ways to not ask the question in the first place.

If you make changes then they should be retained, if the config file changes syntax then your changes should be migrated by the application not the package manager. It should never be about overwriting one file with another.

The fundamental idea is flawed.

Aside that there are many times when this question is posed for no reason at all or it asks nebulous questions like "want to upgrade libc" which has no meaning to 99.9% of the worlds population. These are questions we just should not ask in the first place.

Find the questions we really need to ask, then we can examine ways to handle those situations better. Halting the upgrade process to ask poorly worded questions 99% of all people would never understand is poor usability and a workaround for solving the hard problems involved here.

---

### Post by Gina on 2009-04-28
I totally agree!!

---

### Post by ronacc on 2009-04-28
I agree that some of the questions could be better worded , I also think that an expalanation of what it wants to do and why should be provided . I do not agree that the idea of choice is fundamentaly flawed . nor do I agree that all of those who are now ignorant of the workings of their system wish to remain so ( thats where the explanation part come in ).The handeling of config files etc is a thorny problem if you wish to automate it completely , there are basicly 3 ways to do it as far as I can see. 1 get hundreds of apps written/rewritten so that they can do it themselves , 2 Build the packagemanager with enough AI that it will make the right decission atleast 99% of the time ( and always backup whatever it replaces ) , 3 dont automate ,ask (preferably in an understandable way) .

---

### Post by SKLP on 2009-04-28
When I install Ubuntu on other people's (which may not be that "technically inclined") computer, I would like them to be able to get upgrades. As it is now, they could be asked a rather odd question about "/etc/something.conf" in the middle of the installation, and they wouldn't necessarily know what to do. Would be awesome if updates (including update-manaer upgrades to a new distribution release) were unattended in their nature.

---

### Post by BwackNinja on 2009-04-29
It only asks those questions on files that have been manually edited anyway. If you don't edit those files, you wont get the dialog, and if you do edit the files, you should probably be able to handle (and would probably like having) the dialog.

---

### Post by gnomeuser on 2009-04-29
> **BwackNinja said:**
> It only asks those questions on files that have been manually edited anyway. If you don't edit those files, you wont get the dialog, and if you do edit the files, you should probably be able to handle (and would probably like having) the dialog.

Untrue, debhelper also sticks it's nose into other things like the aformentioned case of upgrading special packages like glibc or asking the user to set meaning like defaults like which mail server they want to run.

It is not just about configuration files, debhelper is unhelpful and counterproductive on a number of impressive levels.

---

### Post by ronacc on 2009-04-29
and exactly how is it "unhelpful and counterproductive " to be asked what defaults I want ? As it is I spend enough time reseting things to "my way" .

---

### Post by gnomeuser on 2009-04-29
> **ronacc said:**
> and exactly how is it "unhelpful and counterproductive " to be asked what defaults I want ? As it is I spend enough time reseting things to "my way" .

There are far better ways to handle it. E.g. if there are several options offer several packages and have a meta package with the default.

We also have virtual providers for a reason, if you need a mail server depend on the virtual one and let the user select by installation. This also allows for selecting a default very simply.

It's not hard to avoid asking questions.

---

### Post by Gina on 2009-04-29
I get those questions when I haven't touched the files.  I found it disconcerting myself and I think I can say I'm an old hand at debugging etc.  I just thought "I've not edited it" so accepted the new version.  Nothing appeared to have gone wrong so that's alright then, I guess... :confused:

---

### Post by super.rad on 2009-04-29
the sooner we get package kit the better, it's a big improvement over synaptic and update manager

---

### Post by Slug71 on 2009-04-29
Correct me if im wrong but i thought Synaptic wasnt being replaced, only Add/Remove and Update Manager? Either way i think Packagekit is going to be good.

---

### Post by gnomeuser on 2009-04-29
> **Slug71 said:**
> Correct me if im wrong but i thought Synaptic wasnt being replaced, only Add/Remove and Update Manager? Either way i think Packagekit is going to be good.

PackageKit itself does not replace synaptic. Synaptic continues to live on, advanced users can install it separately or it can coexist with the PackageKit tools. I would favor a solution where PackageKit is the default toolset simply because PackageKit would cover all the common cases (and then some) and synaptic thus becomes more a point of preference. Something people naturally are entitled to and should have available.

---

### Post by Slug71 on 2009-04-29
> **gnomeuser said:**
> PackageKit itself does not replace synaptic. Synaptic continues to live on, advanced users can install it separately or it can coexist with the PackageKit tools. I would favor a solution where PackageKit is the default toolset simply because PackageKit would cover all the common cases (and then some) and synaptic thus becomes more a point of preference. Something people naturally are entitled to and should have available.

Thanks and agreed.

Now if we had Packagekit as default and one were to install Synaptic to coexist, would there still be 2 Update managers and 2 Software Sources in the System-Admin menu like there is if you install Packagekit now? 

If so they should make it that only Synaptic will appear and use Packagekits tools like you have said.

---

### Post by bash on 2009-04-29
> **Slug71 said:**
> Thanks and agreed.

Now if we had Packagekit as default and one were to install Synaptic to coexist, would there still be 2 Update managers and 2 Software Sources in the System-Admin menu like there is if you install Packagekit now? 

If so they should make it that only Synaptic will appear and use Packagekits tools like you have said.

The current update-manager is a seperate package from synaptic. So if you were to install synaptic you would just have one update-manager - the one from Packagekit. As for Software-Sources: Both read/write to the same backend-file (apt/source.list); so a change made in one would also be seen in the other. So you could probably remove the entry for the synaptic software-sources from the menu and leave only the PK one.

---

### Post by Slug71 on 2009-04-30
> **bash said:**
> The current update-manager is a seperate package from synaptic. So if you were to install synaptic you would just have one update-manager - the one from Packagekit. As for Software-Sources: Both read/write to the same backend-file (apt/source.list); so a change made in one would also be seen in the other. So you could probably remove the entry for the synaptic software-sources from the menu and leave only the PK one.

Thanks bash, 
however i actually prefer the Synaptic Software Sources at the moment since you can add repos via the gui which last i checked couldnt be done with the Packagekit one though it was being worked on.

---

### Post by yelo3 on 2009-04-30
The only problem I have with packagekit is that you can't search for packages during downloading/installing/upgrading packages.
You have to wait until the operation is finished (which is a big limitation!)

but I like the fact that operations can be queued.

---

### Post by Sense on 2009-04-30
I read somewhere that Canonical is brainstorming about some application centre, meant to handle all installation stuff. I'm not sure if they'll use PackageKit for that.

---

### Post by Slug71 on 2009-04-30
> **Sense said:**
> I read somewhere that Canonical is brainstorming about some application centre, meant to handle all installation stuff. I'm not sure if they'll use PackageKit for that.

Im guessing they'll use Packagekit for it. Packagekit is actually still in development so im guessing thats what they would eventually like it to become.

---

### Post by lamalex on 2009-05-01
I would love to see ubuntu adopt packagekit, as a devloper it would be fantastic if there was a simple api I could use to check packages, and have hooks to install ones that I need, while remaining distro agnostic. The packagekit UI is simple, attractive, and intuitive, and the design paradigm of "dont bug me once ive started" is elegant. Packagekit all the way!

---

### Post by gnomeuser on 2009-05-01
> **Sense said:**
> I read somewhere that Canonical is brainstorming about some application centre, meant to handle all installation stuff. I'm not sure if they'll use PackageKit for that.

They have mockups for this intensely wrong application that does everything in one go.

Add/remove programs is a separate use case from updating the system. I should not have to launch the ultra mega app from hell to update my system. Doing so would scare even the cutest of kittens. In the same vein why should add/remove programs have all the update magic in it's UI.

It's like kicking the synaptic horse that just refuses to die.

It has yet to be decided if they will hardcode it to dpkg or do the smart thing and at least use the PackageKit API to handle it. 

This disaster must be averted.

---

### Post by tom56 on 2009-05-01
PackageKit looks great, and its definitely a much-needed project. That said, I would be worried if it was included in 9.10. Right now it is still moving at too fast a pace that would make documentation a nightmare, not to mention the inevitable changes would throw people off in 10.04.

---

### Post by Jay_Bee on 2009-05-02
I tried Packagekit in Fedora 11 Preview but I am not satisfied with it, it seems very slow, especially the first time it's started when it's doing *something* and until it's done you can't do anything.

---

### Post by SKLP on 2009-05-02
> **Jay_Bee said:**
> I tried Packagekit in Fedora 11 Preview but I am not satisfied with it, it seems very slow, especially the first time it's started when it's doing *something* and until it's done you can't do anything.Actually, I think it's just fedoras underlying package manager that is slow. I remember when I had I think it was fedora 9, on my old laptop (with 512MB ram), and simply initializing YUM (I guess loading the database) made it eat a BIG chunk of the ram. APT is much more lightweight, but I also believe zypper(or whatever it's called) that they have in opensuse is also more lightweight than fedora when it comes to RAM. Although when I used it on a machine with 2GB of ram it wasn't a problem, and I think it was faster than apt in that situation.

---

### Post by gnomeuser on 2009-05-02
> **SKLP said:**
> Actually, I think it's just fedoras underlying package manager that is slow. I remember when I had I think it was fedora 9, on my old laptop (with 512MB ram), and simply initializing YUM (I guess loading the database) made it eat a BIG chunk of the ram. APT is much more lightweight, but I also believe zypper(or whatever it's called) that they have in opensuse is also more lightweight than fedora when it comes to RAM. Although when I used it on a machine with 2GB of ram it wasn't a problem, and I think it was faster than apt in that situation.

The thing taking up a lot of ram in big updates for Fedora is RPM, however in RPM 4.7 there is a sizable optimization that really slashed this resource use and speeds up things. 

Yum itself is very speedy these days.

I can't really speak for the state of the packagekit backend for yum, it has never really caused me many problems and I was always well pleased by it's awesomeness.

---

### Post by Simian Man on 2009-05-02
I find that most of the time when yum is slow it is caused by mirror issues.  Every now and then, yum would choose a bad mirror (I don't know how it chooses anyway) and things would grind to a halt.  Now I install the yum fastest-mirror plugin which measures the response time of all of them and saves the fastest to be used each time.  Since doing that, yum and PackageKit are as fast as anything else I've used.

---

### Post by gnomeuser on 2009-05-02
> **Simian Man said:**
> I find that most of the time when yum is slow it is caused by mirror issues.  Every now and then, yum would choose a bad mirror (I don't know how it chooses anyway) and things would grind to a halt.  Now I install the yum fastest-mirror plugin which measures the response time of all of them and saves the fastest to be used each time.  Since doing that, yum and PackageKit are as fast as anything else I've used.

It is a problem, people see slowness and instantly blames the tool in front of them and start saying it sucks without understanding that it takes a whole stack to provide that frontend and the problem they see can be any place in that puzzle, it might also not be permanent (like your occasional bad mirror).

It's also why it annoys me that people say Pulseaudio or Network Manager sucks when they completely fail to investigate or educate themselves. At least 90% of those issues are driver bugs and not related to the application in front of you.

---

### Post by Jay_Bee on 2009-05-02
At that time I didn't really care what it was that made it slow, Packagekit or mirror or whatever and I doubt many users would, it just killed the whole experience for me. 
I have never before used a RPM based distro before so I didn't know about those database issues.
I know that F11 is still in development but in that moment I hoped that Ubuntu wouldn't take that route.

That said, I do understand the advantages of Packagekit and hope to see it included and done properly.

BTW judging by the blueprints, there will be a discussion at the UDS about a new "Add/Remove programs" application called Application Center, so we'll see what's that going to be like.
And it looks like there is still nothing about packagekit here:
[https://blueprints.launchpad.net/sprints/uds-karmic/+specs](https://blueprints.launchpad.net/sprints/uds-karmic/+specs)

---

### Post by Slug71 on 2009-05-02
Yeh i didnt see anything on the UDS Blueprints in either but it might fall under another discussion of some sort. 

I left a message at this Launchpad entry asking if we may see it.

Bug #316162.

---

### Post by RAOF on 2009-05-03
> **Iamalex said:**
> I would love to see ubuntu adopt packagekit, as a devloper it would be fantastic if there was a simple api I could use to check packages, and have hooks to install ones that I need, while remaining distro agnostic. The packagekit UI is simple, attractive, and intuitive, and the design paradigm of "dont bug me once ive started" is elegant. Packagekit all the way!

Applications are perfectly welcome to depend on PackageKit *right now* - the daemon & various front-ends have been working perfectly happily in Universe for a while.  If you want a cross-distro "please install me a package matching this" API, go for it - it'll work on Ubuntu just fine.

The PackageKit frontend itself is more likely to be used by default if something we already care about *actually uses it* :).

---

### Post by gnomeuser on 2009-05-03
for reference, there is a ppa for newer builds of packagekit as Jaunty only has the 0.3.x series. This hopefully means we will start seeing packages trickle into Koala as well.

[https://launchpad.net/~packagekit/+archive/0.4.x](https://launchpad.net/~packagekit/+archive/0.4.x)

---

### Post by super.rad on 2009-05-04
Got excited for a minute, had some updates for packagekit but it turned out to be for kubuntu (have both installed) Still waiting for ubuntu to get it

---

### Post by gnomeuser on 2009-05-04
> **RAOF said:**
> 
The PackageKit frontend itself is more likely to be used by default if something we already care about *actually uses it* :).

Pray tell me how does one depend on a graphical frontend for package upgrades. Sure the backend and the dbus API but the frontend.

No, the reasonable way to determine this must be:
1) Does it cover all common use cases
2) Does it add additional functionality we desire

Packagekit does both, it handles package management as well as the update scenerio. You get policykit integration, handling of scenerios where the internet connection is missing or where it's on a metered mobile connection, integration for applications along with well defined update and package handling frontends that follow the guidelines for the platforms they integrate with (gnome and kde). You also integrate with upstreams translations so they will be consistent with the rest of the desktop and cover a wider selection of languages.

---

### Post by Gourgi on 2009-05-04
> **gnomeuser said:**
> 
Packagekit does both, it handles package management as well as the update scenerio. You get policykit integration, handling of scenerios where the internet connection is missing or where it's on a metered mobile connection, integration for applications along with well defined update and package handling frontends that follow the guidelines for the platforms they integrate with (gnome and kde). You also integrate with upstreams translations so they will be consistent with the rest of the desktop and cover a wider selection of languages.

all those things really make PK sound ideal but you can't deny one thing:
PK (or at least its apt frontend) is slow as turtle compared to update-manager.

---

### Post by gnomeuser on 2009-05-04
> **Gourgi said:**
> all those things really make PK sound ideal but you can't deny one thing:
PK (or at least its apt frontend) is slow as turtle compared to update-manager.

I have not measured this, nor have I experienced any slowdown myself. As you have not provided metrics either I think it would be perfectly reasonable to deny this.

Once you actually provide said data please do so against the 0.4 branch not the ancient 0.3 release that ships with Jaunty.

---

### Post by Slug71 on 2009-05-22
Anyone know if this is being discussed at UDS or have any new info on it for Karmic?

---

### Post by super.rad on 2009-05-22
Nearly got excited over this thread aswell, until I noticed it was you that posted. Guessed you would be posting to see if there was any updates on this :p

---

### Post by Slug71 on 2009-05-22
> **super.rad said:**
> Nearly got excited over this thread aswell, until I noticed it was you that posted. Guessed you would be posting to see if there was any updates on this :p

:lolflag:

---

### Post by ronacc on 2009-05-22
gpk has developed a very anoying behavior , every few minutes it pops up a warning box ( see screenshot ) . Then when you select "show details" the details window cannot be expanded to make it eaisly readable (see screenshot1 ).

---

### Post by super.rad on 2009-05-22
I'm not getting any errors with gpk, been using it since I upgraded to karmic.

---

### Post by ronacc on 2009-05-22
I wasn't until a couple of days ago .

---

### Post by RAOF on 2009-05-23
> **gnomeuser said:**
> Pray tell me how does one depend on a graphical frontend for package upgrades. Sure the backend and the dbus API but the frontend.
...

Indeed, you don't.  But the big advantage - the killer feature, if you will - I've seen people tout for PackageKit is that applications can use it to install needed packages, etc.  You'd have an easier time selling PackageKit if *anything actually used it*.  Once software actually does use it, you've got a much stronger argument for replacing the tried and tested add/remove + update-manager system we currently have.  *Then* it'll be pretty much a no-brainer, modulo ensuring feature-completeness.

Until then, what's wrong with the status-quo?  PackageKit is already getting testing in Jaunty & Karmic, so if and when we need to swap out add/remove it'll be better tested anyway.

---

### Post by super.rad on 2009-05-23
What about automatically installing fonts and mime-types? Surely thats enough of a reason to use packagekit.
[http://fedoraproject.org/wiki/Features/AutoFontsAndMimeInstaller](http://fedoraproject.org/wiki/Features/AutoFontsAndMimeInstaller)
I tried opening the text file in abiword on fedora and it pops up telling me new fonts are needed, tried on ubuntu and abiword opens but half the languages are displayed incorrectly as symbols

---

### Post by zekopeko on 2009-05-23
^^^^^^
the situation above is exactly the reason for implementing packagekit in ubuntu. it sucks when you either enable the plugin in an app and it doesn't work for some reason or it pops up a window saying that you need to install some cryptic package (very user un-friendly).

---

### Post by ranch hand on 2009-05-23
From synaptic;
> 
PackageKit allows to perform simple software management tasks over a DBus
interface e.g. refreshing the cache, updating, installing and removing
software packages or searching for multimedia codecs and file handlers.

The work is done by backends which make use of the package manager shipped by
the corresponding distribution. PackageKit is not meant to replace
advanced tools like Synaptic.

The main benefits are:
 - unified interface on several distributions
 - fine grained privilleges by using PolicyKit
 - independecy from a running desktop session during the processing

You can install this now in Gnome.  It is not as important in gnome as we have synaptic instead of "inept" but it seems like it may turn into something really great.

---

### Post by olskar on 2009-06-09
I'm writing this on latest Fedora, a very nice distro but PackageKit is not very userfriendly. I opened it to add OpenOffice instead of the default AbiWord.

I wrote openoffice in the searchfield and got ~100 packages. 

Among others; "A fig to sxd file converter". Yay. That shouldn't perhaps even be showed to a normal desktop user.

I begun to scroll through the list in search for the writer application.

I choose Office on the left side to try to narrow down my search.

Aha, what is this? I can not choose both a category on the left and search at the same time? Nice! 

I have not yet found it ):P

There must surely be a better way than scrolling through the list :)

Any ideas?



Edit: Ah, found it! Ok, other packages needs to get downloaded in order to install OpenOffice :) How much must I download? It would be nice to know since I am on a 3G-modem. Oh? PackageKit does not tell me :(

Seriosly, this is far from ready.

---

### Post by afv on 2009-06-09
> **olskar said:**
> I'm writing this on latest Fedora, a very nice distro but PackageKit is not very userfriendly. I opened it to add OpenOffice instead of the default AbiWord.

I wrote openoffice in the searchfield and got ~100 packages. 

Among others; "A fig to sxd file converter". Yay. That shouldn't perhaps even be showed to a normal desktop user.

I begun to scroll through the list in search for the writer application.

I choose Office on the left side to try to narrow down my search.

Aha, what is this? I can not choose both a category on the left and search at the same time? Nice! 

I have not yet found it ):P

There must surely be a better way than scrolling through the list :)

Any ideas?



Edit: Ah, found it! Ok, other packages needs to get downloaded in order to install OpenOffice :) How much must I download? It would be nice to know since I am on a 3G-modem. Oh? PackageKit does not tell me :(

Seriosly, this is far from ready.

Hmm, I don't use Packagekit but maybe you're searching for both description and name? Try to search only by package name, if it is possible, to narrow the search results&#8230;

---

### Post by olskar on 2009-06-09
> **afv said:**
> Hmm, I don't use Packagekit but maybe you're searching for both description and name? Try to search only by package name, if it is possible, to narrow the search results&#8230;


You add another good point why PK is not ready. As far as I can see, it is not possible to choose if you want to search by name or description ;)

---

### Post by zekopeko on 2009-06-09
packagekit-gnome (the GUI for packagekit) sucks. it's like a bad mix of add/remove programs and synaptic.

appcenter could probably use some parts of packagekit for font/codec install and it could provide and api for apps to install extra packages if needed.
imagine enabling 3d in chess and getting asked to install needed packages with a single click. or enabling a plugin in gnome-do/banshee/totem/openoffice and getting it automatically installed.

---

### Post by olskar on 2009-06-09
> **zekopeko said:**
> packagekit-gnome (the GUI for packagekit) sucks. it's like a bad mix of add/remove programs and synaptic.

appcenter could probably use some parts of packagekit for font/codec install and it could provide and api for apps to install extra packages if needed.
imagine enabling 3d in chess and getting asked to install needed packages with a single click. or enabling a plugin in gnome-do/banshee/totem/openoffice and getting it automatically installed.

Aha, sorry for wrongfully accusing PackageKit. Yes, a bad mix of add/remove programs and synaptic was exactly what it felt like.

---

### Post by psyke83 on 2009-06-09
I just downloaded Fedora 11 (as it was released today), so here's some random thoughts on PackageKit (since we don't have any 0.4 series packages available in Karmic)...

General PackageKit system integration:
[LIST]
[*]The notification icon for PackageKit is a nice feature; the icon changes depending on the type of transaction that occurs, and you can see all transactions taking place (and recent history) by clicking on the icon.

[*]Adding software repositories is much easier on Fedora. I visited rpmfusion.org (which I was told is the closest equivalent of medibuntu), and I was able to directly add the repositories via PackageKit (although adding the nonfree repository gave a strange warning that the repository was already present, when it wasn't).

[*]After adding the rpmfusion repositories, I then tried to open an .avi file in Totem - it displayed an error about missing codecs and didn't offer any means to install the missing packages/codecs - what happened to the codec buddy integration? I remember it being present in a previous version of Fedora, so that left a bad impression.
[/LIST]

Console tools:
[LIST]
[*]The "pkcon" utility is easy to use; it doesn't take much effort to learn "pkcon install vlc" instead of "apt-get install vlc" ;). The commands are fairly self-explanatory, and the output gives information on each transaction that takes place.
[/LIST]


Thoughts on packagekit-gnome frontend:
[LIST]
[*]The interface of packagekit-gnome isn't significantly better than the 0.3 series (has it changed at all?). The interface seems to be a mixture of Synaptic and Ubuntu's "Add/Remove Applications", and somehow, it seems to have inherited the worst aspects of both of these applications.

[*]When you attempt to view software by type, querying seems quite sluggish.

[*]When you attempt a text search (which does not give any indication of what type of search is being performed, e.g. by package name, description, etc.), the results can be quite confusing; "**Multi-Platform MPEG, DVD and DivX Player**" is the result for VLC. It seems they have set no standard (or sane) naming convention for displaying the results clearly. As another user mentioned, searching for "openoffice" gives a long list (perhaps 50 or more) of packages and it takes some effort to determine the correct package will actually **install** OpenOffice...

[*]There is no capability to easily select multiple packages (you cannot control or shift-select a range of packages).

[*]I'm not impressed with packagekit-gnome at all.
[/LIST]

Thoughts on Software Updates:
[LIST]
[*]The Software Update applications is excellent; it displays the available updates and clicking on each update displays the changelog. 
[*]It also indicates when a restart will be necessary before you elect to install updates.
[*]You can uncheck individual updates (but control/shift clicking is not available).
[*]Overall, it's very similar to Ubuntu's implementation, but superior due to the integration with the PackageKit notification icon.
[/LIST]

In all, using PackageKit in its current form is a bittersweet experience ;). I would like to see PackageKit deployed to handle system updates, and if it were possible to whip up a quick hack to allow Synaptic hook into PackageKit (to avail of the transaction notifications and integration), perhaps it would be more worth our while...

---

### Post by ktp on 2009-06-09
I guess the real question is...should Ubuntu spend time on developing something new or help make PackageKit better.  It is hard question to answer but to me it might be better, for Linux in general, not just Ubuntu, to help make PackageKit better specially the UI.  Maybe this is exactly what will happen only time will tell.

---

### Post by zekopeko on 2009-06-09
> **ktp said:**
> I guess the real question is...should Ubuntu spend time on developing something new or help make PackageKit better.  It is hard question to answer but to me it might be better, for Linux in general, not just Ubuntu, to help make PackageKit better specially the UI.  Maybe this is exactly what will happen only time will tell.

there will be nothing stoping packagekit upstream to take ubuntu appcenter, re-brand it and hook it with pk.

---

### Post by Merk42 on 2009-06-09
What, if anything, is stopping Ubuntu from using PackageKit?

Is AppCenter at a point where it could use PackageKit, but hasn't decided yet? If Ubuntu has decided to not use PackageKit, what is the reason?

I read [the blueprint](https://blueprints.edge.launchpad.net/ubuntu/+spec/software-library), but it seems the status was still undecided as to whether to use PK or not, is this correct?

---

### Post by zekopeko on 2009-06-09
> **Merk42 said:**
> What, if anything, is stopping Ubuntu from using PackageKit?

Is AppCenter at a point where it could use PackageKit, but hasn't decided yet? If Ubuntu has decided to not use PackageKit, what is the reason?

I read [the blueprint](https://blueprints.edge.launchpad.net/ubuntu/+spec/software-library), but it seems the status was still undecided as to whether to use PK or not, is this correct?

i think that you don't understand that pk isn't a all or nothing deal. you can use parts like autoinstallers. but as far as i can see it doesn't provide some of the advanced things dpkg and apt provide. debtags are just one of the way you can provide GUI applications for endusers without stuff such as dependencies. users don't need to know that.

---

### Post by 23meg on 2009-06-09
> **olskar said:**
> ...
Seriosly, this is far from ready.

For Ubuntu, and as of now.

For Fedora, which is a project with significantly different design goals and development policies, as well as a different audience in terms of technical aptitude with and expectations from personal computers (to sum up roughly), it may arguably be the right choice.

I'm puzzled by the constant treatment of Fedora as a direct equivalent and/or competitor to Ubuntu which just happens to use RPMs and be dressed in blue, or vice versa.

---

### Post by Slug71 on 2009-06-09
> **zekopeko said:**
> there will be nothing stoping packagekit upstream to take ubuntu appcenter, re-brand it and hook it with pk.

Why would you want to rebrand something that already exists and is improving all the time with something that barely exists? 
It makes more sense to do it the other way.

---

### Post by psyke83 on 2009-06-10
> **23meg said:**
> For Ubuntu, and as of now.

For Fedora, which is a project with significantly different design goals and development policies, as well as a different audience in terms of technical aptitude with and expectations from personal computers (to sum up roughly), it may arguably be the right choice.

I'm puzzled by the constant treatment of Fedora as a direct equivalent and/or competitor to Ubuntu which just happens to use RPMs and be dressed in blue, or vice versa.

I agree with regards to design goals and development policies, but that's not necessarily something that end users will reflect upon. 

A simpler explanation is that Ubuntu doesn't have a lot of competition lately, and Fedora is probably second (or third, considering openSUSE) to Ubuntu in terms of mindshare and the amount of users.

PackageKit sounds compatible with the philosophy of "Linux for human beings" on paper, but its implementation currently falls short in some areas (at least that's my impression from testing PackageKit in Fedora).

---

### Post by ranch hand on 2009-06-10
I don't know how many of you work with RPMS on a regular basis, but I do.  Just about anything would be better than the apps for handling RPMS.

PCLOS-Gnome is not a distro that I currently have on my box as I just don't really like it.  It does have the best RPM handling that I have run into.  It uses Synaptic, apt-get, etc.

As I said before, folks using RPMs or KDE may want to change there system now.  Gnome users, I suspect, generally would like to have whatever "improvements" to actually be better than what we are using now.

Package kit is not such an app at this point at all.

---

### Post by zekopeko on 2009-06-10
> **Slug71 said:**
> Why would you want to rebrand something that already exists and is improving all the time with something that barely exists? 
It makes more sense to do it the other way.

You are implying that ubuntu takes packagekit-gnome and rebrands it ubuntu appcenter if i read correctly? i said it the other way around. ubuntu creates appcenter and packagekit upstream takes it for the gnome ui of packagekit (re-branded).
on another note: packagekit-gnome isn't the best UI i have seen for package management. and i think that appcenter tries to solve a different set of problems (and there is nothing saying that pk can't be used for PARTS of it, if it meet devs expectations).
and let's get one thing straight. packagekit-gnome sucks monkey balls. hard. i used it in fedora 10 and it was such a mess that i deleted the VM within 5min. and as far as i can tell the UI hasn't changed much since then.

---

### Post by ranch hand on 2009-06-10
> **zekopeko said:**
> 
and let's get one thing straight. Packagekit-gnome sucks monkey balls. Hard. I used it in fedora 10 and it was such a mess that i deleted the vm within 5min. And as far as i can tell the ui hasn't changed much since then.

+1

---

### Post by olskar on 2009-06-10
> **zekopeko said:**
> and as far as i can tell the UI hasn't changed much since then.

It has not.

---

### Post by 23meg on 2009-06-10
> **psyke83 said:**
> I agree with regards to design goals and development policies, but that's not necessarily something that end users will reflect upon. 

But the design of the software installation and removal experience is something that directly concerns end users, and should be done with them in mind.

[QUOTE=psyke83]A simpler explanation is that Ubuntu doesn't have a lot of competition lately, and Fedora is probably second (or third, considering openSUSE) to Ubuntu in terms of mindshare and the amount of users.[/QUOTE]

In the sense that "Ubuntu doesn't have a lot of competition lately, so it has more freedom to deviate from upstream"? If that's what you mean, I may make an effort to disagree in detail :)

---

### Post by psyke83 on 2009-06-10
> **23meg said:**
> But the design of the software installation and removal experience is something that directly concerns end users, and should be done with them in mind.

Absolutely, I agree.

> In the sense that "Ubuntu doesn't have a lot of competition lately, so it has more freedom to deviate from upstream"? If that's what you mean, I may make an effort to disagree in detail :)

No need ;). I only meant that Fedora and openSUSE are the only major alternatives* around these days (that rival Ubuntu in terms of mass appeal). Users who aren't aware of the forces that drive the development process of these distributions can be (somewhat) forgiven for thinking: that's the brown GNOME distro (Ubuntu), blue GNOME distro (Fedora), and there's that green KDE (openSUSE)... ;)

*I'm not counting Ubuntu derivatives, and Debian is popular for the more technically-inclined users, perhaps.

---

### Post by jppr on 2009-06-16
there... [http://feeds.ubuntu-nl.org/KarmicChanges](http://feeds.ubuntu-nl.org/KarmicChanges) is coming updatet packagekit-gnome and packagekit. i don´t have read this line so much, may be these packages don´t are same what you are talking this line...

[https://launchpad.net/ubuntu/karmic/+source/packagekit/0.4.8-0ubuntu1](https://launchpad.net/ubuntu/karmic/+source/packagekit/0.4.8-0ubuntu1)
[https://launchpad.net/ubuntu/karmic/+source/packagekit-gnome/2.27.2-0ubuntu1](https://launchpad.net/ubuntu/karmic/+source/packagekit-gnome/2.27.2-0ubuntu1)

---

### Post by ranch hand on 2009-06-16
That is just great news:-(.

In an attempt to give this app a chance I installed Suse11.1.

I just love packagekit.  Won't load past 1% "initializing".  Great stuff.

---

### Post by Slug71 on 2009-06-16
Well im not sure that means it will be default. It may just be an update for Karmics repos.

Apparantly 0.4.8 works well but i have not used it yet.

---

### Post by Slug71 on 2009-06-16
> **ranch hand said:**
> That is just great news:-(.

In an attempt to give this app a chance I installed Suse11.1.

I just love packagekit.  Won't load past 1% "initializing".  Great stuff.

Seems the bugs like you ranch hand, both PK and Grub2. :p

---

### Post by ranch hand on 2009-06-17
Grub2 is all right.  It is not supposed to do what I want it to until A3.  The only thing I haven't been able to do is set it to be boot root.

Packagekit on the other hand does not work in Suse11.1 well and crashes continually in Fedora10.  I am going to try reinstalling Fedora10 to see if there is some problem that will go away but I doubt it as this will be the third install.  I thought about downloading a fresh copy but the checksum is correct so I don't think I will bother just to test an app that I have used before and got about the same results from.

---

### Post by plun on 2009-06-17
> **jppr said:**
> there... [http://feeds.ubuntu-nl.org/KarmicChanges](http://feeds.ubuntu-nl.org/KarmicChanges) is coming updatet packagekit-gnome and packagekit. i don´t have read this line so much, may be these packages don´t are same what you are talking this line...

[https://launchpad.net/ubuntu/karmic/+source/packagekit/0.4.8-0ubuntu1](https://launchpad.net/ubuntu/karmic/+source/packagekit/0.4.8-0ubuntu1)
[https://launchpad.net/ubuntu/karmic/+source/packagekit-gnome/2.27.2-0ubuntu1](https://launchpad.net/ubuntu/karmic/+source/packagekit-gnome/2.27.2-0ubuntu1)


For unknown reasons all package are on hold....:confused:

> Build details
Package: 	packagekit in ubuntu
Built on: 	Ubuntu Karmic amd64
Status: 	Successfully built
Queued: 	12 hours ago
Finished: 	**8 hours ago** 

> 
Resulting binaries

**Binaries awaiting acceptance:**:---)

    * gstreamer0.10-packagekit 0.4.8-0ubuntu1
    * libpackagekit-glib-dev 0.4.8-0ubuntu1
    * libpackagekit-glib11 0.4.8-0ubuntu1
    * libpackagekit-qt-dev 0.4.8-0ubuntu1
    * libpackagekit-qt11 0.4.8-0ubuntu1
    * mozilla-packagekit 0.4.8-0ubuntu1
    * packagekit 0.4.8-0ubuntu1
    * packagekit-backend-apt 0.4.8-0ubuntu1
    * packagekit-backend-aptcc 0.4.8-0ubuntu1
    * packagekit-backend-smart 0.4.8-0ubuntu1



---

### Post by Slug71 on 2009-06-17
> **plun said:**
> For unknown reasons all package are on hold....:confused:

* packagekit-backend-smart 0.4.8-0ubuntu1

Good to see the backend for smart is updated too.

---

### Post by Slug71 on 2009-06-17
> **ranch hand said:**
> Grub2 is all right.  It is not supposed to do what I want it to until A3.  The only thing I haven't been able to do is set it to be boot root.

Packagekit on the other hand does not work in Suse11.1 well and crashes continually in Fedora10.  I am going to try reinstalling Fedora10 to see if there is some problem that will go away but I doubt it as this will be the third install.  I thought about downloading a fresh copy but the checksum is correct so I don't think I will bother just to test an app that I have used before and got about the same results from.

Try F-11 instead of 10. I think 10 still had 0.3.X version of PK.

Gonna try find someone fom PK on Freenode today and propose a new GUI.

---

### Post by ranch hand on 2009-06-17
As a matter of fact F-11 is about 52% downloaded right now.  I thought I would give it a whack.

---

### Post by Slug71 on 2009-06-17
> **ranch hand said:**
> As a matter of fact F-11 is about 52% downloaded right now.  I thought I would give it a whack.

Argh, wish i had space on my HDD :(

---

### Post by ranch hand on 2009-06-17
> **Slug71 said:**
> Argh, wish i had space on my HDD :(

I have 5x320Gb HDDs, 2 internal and 3 external.  I have the room.  I love it.

15 minutes burn time left.  I got the 4Gb package (Gnome).

---

### Post by ranch hand on 2009-06-17
4Gb torrent was bad.  LiveCD will not download.  There is a reason that fedora is not one of my favorites.

---

### Post by ktp on 2009-06-17
> **ranch hand said:**
> 4Gb torrent was bad.  LiveCD will not download.  There is a reason that fedora is not one of my favorites.

that sucks.

---

### Post by zekopeko on 2009-06-17
> **ranch hand said:**
> 4Gb torrent was bad.  LiveCD will not download.  There is a reason that fedora is not one of my favorites.

hmmmm.... did you download it via torrent? try rechecking it if so.
or perhaps rsync if fedora offers that.

---

### Post by psyke83 on 2009-06-17
> **ranch hand said:**
> 4Gb torrent was bad.  LiveCD will not download.  There is a reason that fedora is not one of my favorites.

Highly unlikely. Torrents are checked for integrity during the entire download process, and can be manually verified when the download is complete (and corrupt chunks will get re-downloaded). It was probably a bad burn.

The Live CD also has torrent links: [http://torrent.fedoraproject.org/](http://torrent.fedoraproject.org/)

---

### Post by ranch hand on 2009-06-18
It may be unlikely but i have several OSs with several burning utilities and non of them could read the file.

Had the same thing with the LiveCd that I downloaded from the link on Fedoraa website too.

I did however get a good Live CD from a mirror listed by Linuxquestions.org.  I am installing it in VB now.

---

### Post by ranch hand on 2009-06-18
Goodness this is an improvement.  The help file even works on the "gpk-application-2.27.2 package manager for Gnome".  Didn't have to go to the website to download the bugger.

Maybe this one won't crash as soon as I try to use it.

I will report.

---

### Post by Slug71 on 2009-06-18
So the new GUI i proposed for PK doesnt seem to be doing to well in the Packagekit camp. Its very similiar to the Kpackagekit one.
This is what its about:


> Foresight and Ubuntu have an Add/Remove entry in the Applications menu. Add/Remove, Software Sources and Update System in System->Admin and Software Updates in System ->Prefs. and i have not used Fedora in a couple of years but im guessing its pretty much the same.
 
 
What i propose is just one entry, a single entry under System->Admin called Packagekit or something like that. You click on that and this pops up: v

[http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PackagekitDefault.jpg](http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PackagekitDefault.jpg)

> A GUI with 3 tabs, Add/Remove, Software Updates and Update System.
 


If you click on System in the top left of the GUI you have all the options thats usually there plus 2 Additional entries which are CHECK BOXES, namely
enable Software Sources and enable Advanced.
 
If you CHECK: enable Software Sources, then you will see this: v

[http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKDefaultSoftwareSources.jpg](http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKDefaultSoftwareSources.jpg)

> If you CHECK: enable Advanced, then you will see something like this: v

[http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKDefaultAdvanced.jpg](http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKDefaultAdvanced.jpg)

> Yes it has the feel and look of Synaptic giving advanced users that extra functionality. ^
 
 
If you have Software Sources and Advanced CHECKED, then you GUI will look as follows with the selected Tabs:

[http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PackagekitAdd-Remove.jpg](http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PackagekitAdd-Remove.jpg)

[http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKSoftwareUpdates.jpg](http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKSoftwareUpdates.jpg)

[http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKUpdateSystem.jpg](http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKUpdateSystem.jpg)

[http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKSoftwareSources.jpg](http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PKSoftwareSources.jpg)

[http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PackagekitAdvanced.jpg](http://s45.photobucket.com/albums/f53/courtney2721/?action=view&current=PackagekitAdvanced.jpg)

> Perhaps to enable Software Sources and Advanced in the System menu at the top left of the GUI, password authentification could be required??

Please share your views/ideas.

---

### Post by ranch hand on 2009-06-18
The updating went nice and smooth and so did the installation of support for my APC UPS.

The feel of the Gnome Gui seems a little nicer than the KDE version but that is not a fair comparision as I never got the KDE version to actually work.

This is much better than the last time I fooled with it.  I still do not see what the excitement is about.  It is doing nothing that sysnaptic does not do, and in pretty much the same way.

That said, it is a lot better than the Add/Remove feature.

---

### Post by ronacc on 2009-06-18
the add-remove "feature" is sorry at best and infuriating at worst , also needed is a way to turn off that worthless "quick search" box in synaptic .

---

### Post by Slug71 on 2009-06-18
> **ranch hand said:**
> This is much better than the last time I fooled with it.  I still do not see what the excitement is about.  It is doing nothing that sysnaptic does not do, and in pretty much the same way.

Well in some way, This is a C/P by Gnomeuser from the Jaunty thread.

> When you examine what PackageKit gives you it is not just a set of nicely designed tools for upgrading the distro, installing/removing packages. It gets you an easy way for application designers to call into the package manager to get packages installed on demand. Such as your archiver or media player installing say an compression handler or codec when an unsupported file is attempted opened. Synaptic cannot do this in it's wildest fantasy. Any solution to such problems involving apt would be horribly tied to the Debian platform whereas PackageKit allows a solution that can be adopted universally (meaning upstreams might actually start implementing these very useful features in applications you use every day).

---

### Post by ranch hand on 2009-06-18
ronacc
I really like synaptic and think it is about as handy as sliced bread.  I would really like for someone to explain to me what that "quick search" thing is actually for, let alone good for.

Slug71
I just got back from that partition and I still do not see the point.  I have read in the manual about it being a great improvement for developers.  This may be, but it does not effect me.  It would be nice if I got to the point that I would need that.

It does seem to work well in Fedora11-Gnome.  As an Ubuntu user I am relieved.  I have to admit I have always run into it on KDE.

I loath Adept (inept).  I saw that Fedora and Suse used this other thing.  It did not do the job and I still can't get it to work on KDE OSs (right now I am to the point of trying to reinstall Suse due to being totaly screwed after a 3 hour update of around 90Mb - I could do that on Ubuntu in 9 hours on dial up).

On my Kubuntu partitions I have installed Synaptic and Update manager from Gnome and it works great.

I tried PCLOS (I need to install it again sometime) and it used synaptic for its package management and I liked it better than any other RPM manager although I think that Mandrivas works alright.

The package management folks working on Ubuntu seem to me to be the best around as far as trying to get something that really works.  I am sure that if they use packagekit they will integrate it well.  It would definately be great if they got it to work on Kubuntu.

---

### Post by SKLP on 2009-06-18
Regardless of whether ubuntu adopts PackageKit, it would in my opinion be awesome if we had something like Hughsie's law ([http://www.packagekit.org/pk-faq.html#hughsies-law](http://www.packagekit.org/pk-faq.html#hughsies-law))

---

### Post by gnomeuser on 2009-06-18
> **Slug71 said:**
> So the new GUI i proposed for PK doesnt seem to be doing to well in the Packagekit camp. Its very similiar to the Kpackagekit one.

Managing software (add/remove) and updating the system are separate tasks that have nothing what so ever to do with each other. This is also my big UI design problem with AppCenter.

Updating should be as slim a task as possible UI-wise, PackageKit's new updater even seems a touch heavy for me. Ideally we would be able to enable automatic background updates, a bit like Windows Vista does which is perfect for keeping peoples systems updated. If action is desired on the users part a very slim UI like what PK used to have would be nice, perhaps the new one will turn out nicely as well but I am definitely thinking it is to heavy a step up from automatic updating. I'd like 3 steps like Windows offers. Automatic, download only and ask to apply and more granular selections like the new updater allows.. 

Managing software is a separately formed GUI from this entirely and should not be shoe horned into the same window just because we can. It's like say applying an axe to ones testies, just because you can doesn't mean it's a good idea.

Think of the workflow involved here. Updating is a background task that happens as the systems initiates a request to have this maintenance task performed on say a weekly basis in probably 99% of all regular cases. Installing/removing software is a user interaction that happens here and now for a specific purpose.

When do you want to add "stuff". Missing functionality should be installed on demand e.g. the gstreamer or font plugins, installing a program would often be missing a specific bit of functionality so a quick search of the repos or browsing the categories/tags would do the job and give you a number of offers. It could also be reading a review and wanting to try something out, here the pk-mozilla plugin is awesome, get reviewers to put this in the review and it's a single click to install the application. 

Removing is separate still, there are many UI ideas to play with here, we may want to have a context menu entry in the menu to remove unwanted programs but there are many different things in play here. There is definitely room to experiment with the optimal solution to the problem of allowing flexibility and ease of use while retaining simplicity and a discoverable interaction. For now the best we can do is probably what pk does currently namely muzzling removing and adding in the same interface.

This is not to say that a separately installable "synaptic/yumex" like tool couldn't be available for power users who want this type of interface.

In short mashing several use cases into the same gui is what makes your proposal problematic. I think the rewarding process here would be to look at what users attempt to do and do some quickly hacked up tools to test ideas and look for feedback. Perhaps this is a job for something like BetterDesktop to seek usability input on.

---

### Post by ronacc on 2009-06-18
as I see it part of the problem is PK's attempt to be "all things to all people" , this inevitably leads to conflicts Ui wise , too much information here , not enough there , or else results in something so complex and cumbersome that it defeats its own purpose . While some of PK's functionality is certainly needed , for instance automatic fetching of needed "add ons" and non native app installs (rpm's in debian etc ) much of it duplicates existing apps that already do a good job .

---

### Post by Reiger on 2009-06-18
> **gnomeuser said:**
> Managing software (add/remove) and updating the system are separate tasks that have nothing what so ever to do with each other. This is also my big UI design problem with AppCenter.

That depends from use case to use case. The problem is I think, that by design package management like we know it encourages you to try and update your system first before you install new things. Actually, often you can't install something without updating (sometimes completely unrelated) parts first.

The problem with Kpackagekit and packagekit in general is that it is *way too slow*. I find it totally unacceptable for a tool to spend lots of time appearing to be stuck at what is a relatively trivial taks of wget-'ing something from somewhere. A tool that doesn't work is no good, no matter how nice its API. [And I verified this problem with both Kubuntu and Fedora 11.]

I find it totally unacceptable to get less visual feedback from a tool that manages a critical portion of my OS with the power to thoroughly kill it if a crucial transaction breaks midway then I get from aptitude or apt-get.

And the search functions (nevermind showing a description or dependencies or actually any sort of information apart from the package name at all) Just Work outside Packagekit. That's more than can be said for Packagekit in the Kubuntu repositories... 

The Gnome counterpart on Fedora has as much ease-of-use as commandline yum, or rather: a good deal less since yum provides better feedback. Plus: yum actually works, even though the package naming scheme of Fedora hurts it somewhat (you need to type an awful lot).

At which point I'd say that so far Packagekit basically fails to live up to its name and should not be included in a distribution that calls out "linux for human beings" with the implication that ease-of-use comes first. Ease of use is 0 if the tool doesn't work. Ease of use drops below 0 if it means that apart from the tool not working in the general case, you must also avoid it when the update notifier pops up helpfully suggesting to lock software management away for as long as you have the patience to let the updater remain stuck at the first download. And I would go so far as to say that the current software add/remove tool we have in Ubuntu by far outshines packagekit when it comes to usability and accessibility of the UI: simply because it is more responsive (not spending 5 seconds to query a database each time you do *anything* goes a long way to making your UI more responsive).

---

### Post by seeker5528 on 2009-06-18
> **ronacc said:**
> as I see it part of the problem is PK's attempt to be "all things to all people" , this inevitably leads to conflicts Ui wise , too much information here , not enough there , or else results in something so complex and cumbersome that it defeats its own purpose .

I don't understand that line of thinking.

From: [http://www.packagekit.org/pk-intro.html](http://www.packagekit.org/pk-intro.html) 

> PackageKit itself is a system activated daemon called packagekitd. Being system activated means that it's only being run when the user is using a text mode or graphical tool, and quits when it's no longer being used. This means we don't delay the boot sequence or session startup and don't consume memory when not being used. 

The UI stuff is seperate.

> While some of PK's functionality is certainly needed , for instance automatic fetching of needed "add ons" and non native app installs (rpm's in debian etc ) much of it duplicates existing apps that already do a good job .

But the majority of these are developed more or less independently and the left hand doesn't know what the right hand is doing.

If I am already running synaptic, update-manager shouldn't pop up telling me there are updates ready to be installed. 

If PK does it's job right, you should be able to have the full blown management interface, the add/remove programs interface, the updater, codec installer, etc... all [s]without stomping on each others toes so much[/s] while providing better feedback if you run one UI while tasks are in progress in another one. If it doesn't allow for that, I don't really see the point.

Later, Seeker

---

### Post by mpt on 2009-06-18
> **gnomeuser said:**
> Managing software (add/remove) and updating the system are separate tasks that have nothing what so ever to do with each other. This is also my big UI design problem with AppCenter.

Actually I’m still undecided about whether AppCenter should be the primary interface for installing updates. On one hand, installing updates at the same time as you’re installing/removing other applications could help reduce the number of times you get nagged to install updates. ;) On the other hand, installing/removing other applications usually won’t be that frequent even if we make it awesomely fun, so it wouldn’t save *that* much nagging.

> *Updating should be as slim a task as possible UI-wise, PackageKit's new updater even seems a touch heavy for me.*

Yeah, that’s another issue. As I’ve been sketching out changes to make Update Manager simpler for Karmic, I’ve been thinking “hmm, this is looking less and less like it could be a subset of AppCenter”. (The original idea was that the auto-opening updates window would be a highly collapsed version of the AppCenter window, so that you could expand it if you wanted to do other stuff at the same time.)

> *Removing is separate still, there are many UI ideas to play with here, we may want to have a context menu entry in the menu to remove unwanted programs but there are many different things in play here.*

We probably wouldn’t make a context menu the only interface for uninstalling stuff, because that would make the function invisible to about half the target audience. (And because giving menu items their own context menus is rather skanky in general.) But we do need to solve the twin problems of (a) “Okay, I’ve installed an application, where do I find how to launch it?” and (b) “Here’s the launcher for an application I don’t want any more, how do I get rid of it?”.

> *There is definitely room to experiment with the optimal solution to the problem of allowing flexibility and ease of use while retaining simplicity and a discoverable interaction. For now the best we can do is probably what pk does currently namely muzzling removing and adding in the same interface.*

What do you mean by “muzzling”?

> *In short mashing several use cases into the same gui is what makes your proposal problematic. I think the rewarding process here would be to look at what users attempt to do and do some quickly hacked up tools to test ideas and look for feedback. Perhaps this is a job for something like BetterDesktop to seek usability input on.*

As far as I can tell, BetterDesktop has been dead for over two years. However, we are doing pretty much what you suggest. In Canonical’s Design team we currently have a [Season of Usability]("http://season.openusability.org/") intern helping us investigate different possibilities for presenting the various tasks. We’ll be sketching out half a dozen different arrangements, and doing some paper prototyping to see how many people understand which one. So if you have a layout to suggest (everything in one window somehow? two windows? three?), by all means post it in this forum. Perhaps in a different thread, though, out of respect to the topic.

---

### Post by biasquez on 2009-06-20
one question: compiling latest Packagekit from git i have this error:

checking for POLKIT... configure: error: Package requirements (			  polkit-gobject-1 >= 0.91) were not met:

No package 'polkit-gobject-1' found

this package doesn't exist...how can i solve this problem?

---

### Post by Slug71 on 2009-06-20
> **biasquez said:**
> one question: compiling latest Packagekit from git i have this error:

checking for POLKIT... configure: error: Package requirements (			  polkit-gobject-1 >= 0.91) were not met:

No package 'polkit-gobject-1' found

this package doesn't exist...how can i solve this problem?

Seems like a Policykit error. Perhaps Policykit version update is required.

---

### Post by Slug71 on 2009-06-20
Ok, so i have submitted a bug report, Bug #389935, requesting that Ubuntu Karmic(Gnome) be released in 2 versions. One with AppCenter installed as default and the other with Packagekit installed by default.
I feel its only fair to those that have voted in Brainstorm and those that have supported it here in the Forums and on Launchpad.

So go add to the bug report guys.

---

### Post by taavikko on 2009-06-20
> **Slug71 said:**
> Ok, so i have submitted a bug report, Bug #389935, requesting that Ubuntu Karmic(Gnome) be released in 2 versions. One with AppCenter installed as default and the other with Packagekit installed by default.
I feel its only fair to those that have voted in Brainstorm and those that have supported it here in the Forums and on Launchpad.

So go add to the bug report guys.

Pretty sure that's going to marked as "Won't fix" regardless the input we provide...

---

### Post by ranch hand on 2009-06-20
I would like someone to explain the "vote" to me.

I saw no place to vote against.  I am ambivolent on this issue but it seemed to be loaded and rather silly the way it appeared to me to be set up.

---

### Post by zekopeko on 2009-06-20
> **Slug71 said:**
> Ok, so i have submitted a bug report, Bug #389935, requesting that Ubuntu Karmic(Gnome) be released in 2 versions. One with AppCenter installed as default and the other with Packagekit installed by default.


Why don't you install it from the repos?

> 
I feel its only fair to those that have voted in Brainstorm and those that have supported it here in the Forums and on Launchpad.
So go add to the bug report guys.

Ubuntu isn't a democracy. It's a meritocracy. And Brainstorm is only (at best) a guide for the developers.

---

### Post by gnomeuser on 2009-06-20
> **biasquez said:**
> one question: compiling latest Packagekit from git i have this error:

checking for POLKIT... configure: error: Package requirements (			  polkit-gobject-1 >= 0.91) were not met:

No package 'polkit-gobject-1' found

this package doesn't exist...how can i solve this problem?

There is a major upgrade coming to PolicyKit, it is finally reaching 1.0 and thus all users need to be updated to this 1.0 stable API. PackageKit obviously has had this work done in git. 

Other users have been converted in Fedora's builds the last few weeks so patches should be available and the transition hopefully painfree.

---

### Post by Starks on 2009-06-20
> **Slug71 said:**
> Ok, so i have submitted a bug report, Bug #389935, requesting that Ubuntu Karmic(Gnome) be released in 2 versions. One with AppCenter installed as default and the other with Packagekit installed by default.
I feel its only fair to those that have voted in Brainstorm and those that have supported it here in the Forums and on Launchpad.

So go add to the bug report guys.
Will do!

---

### Post by biasquez on 2009-06-20
> **gnomeuser said:**
> There is a major upgrade coming to PolicyKit, it is finally reaching 1.0 and thus all users need to be updated to this 1.0 stable API. PackageKit obviously has had this work done in git. 

Other users have been converted in Fedora's builds the last few weeks so patches should be available and the transition hopefully painfree.

thanks for info!

---

### Post by mpt on 2009-06-21
> **Slug71 said:**
> Ok, so i have submitted a bug report, Bug #389935, requesting that Ubuntu Karmic(Gnome) be released in 2 versions. One with AppCenter installed as default and the other with Packagekit installed by default.
I feel its only fair to those that have voted in Brainstorm and those that have supported it here in the Forums and on Launchpad.

That’s an intriguing idea. Why apply it to PackageKit, though? There are other far more popular ideas in Brainstorm. For example, we could release one version of Ubuntu where the installer sets up a separate /home partition by default, and another where it doesn’t; a separate home partition has [*nine times* as many Brainstorm votes]("http://brainstorm.ubuntu.com/idea/5390/") as PackageKit does. Then we could release one version of Ubuntu that includes Disk Manager by default, and another that doesn’t; Disk Manager has [nearly six times as many Brainstorm votes]("http://brainstorm.ubuntu.com/idea/323/") as PackageKit does.

But seriously, if you’re going to treat AppCenter and PackageKit as mutually exclusive, and Brainstorm votes as imperative, you’re going to be disappointed. After all, “Improve Add/Remove Programs” [has nearly four times as many Brainstorm votes]("http://brainstorm.ubuntu.com/idea/103/") as PackageKit does.

Or you could try to appreciate what I’ve said all along [[1]("http://ubuntuforums.org/showpost.php?p=7349884&postcount=6"), [2]("http://ubuntuforums.org/showpost.php?p=7353101&postcount=63"), [3]("http://ubuntuforums.org/showpost.php?p=7424788&postcount=121")]: AppCenter and PackageKit are *not* mutually exclusive, and it is quite possible that Ubuntu will use PackageKit for some things. AppCenter and packagekit-gnome *are* mutually exclusive (in the sense that Ubuntu wouldn’t ever install both by default), but if there’s something you particularly like about packagekit-gnome, you’d get better results from telling me what it is so we can take it into account for AppCenter, than from launching quixotic campaigns for Ubuntu variants.

---

### Post by 23meg on 2009-06-21
> **Slug71 said:**
> Ok, so i have submitted a bug report, Bug #389935, requesting that Ubuntu Karmic(Gnome) be released in 2 versions. One with AppCenter installed as default and the other with Packagekit installed by default.
I feel its only fair to those that have voted in Brainstorm and those that have supported it here in the Forums and on Launchpad.

So go add to the bug report guys.

Please avoid using the bug tracker for anything not pertaining to specific, reproducible software defects, including development and design policy matters such as this, which should go to the forums, Brainstorm or ubuntu-devel-discuss.

---

### Post by zekopeko on 2009-06-21
> **mpt said:**
> That’s an intriguing idea. Why apply it to PackageKit, though? There are other far more popular ideas in Brainstorm. <snip>

Noooooo!!!!! Why did you have to bring reason to this discussion? It was all going so well with emotions and stuff... :P

---

### Post by Bou on 2009-06-21
> **mpt said:**
> we could release one version of Ubuntu where the installer sets up a separate /home partition by default, and another where it doesn’t; a separate home partition has [*nine times* as many Brainstorm votes]("http://brainstorm.ubuntu.com/idea/5390/") as PackageKit does. Then we could release one version of Ubuntu that includes Disk Manager by default, and another that doesn’t; Disk Manager has [nearly six times as many Brainstorm votes]("http://brainstorm.ubuntu.com/idea/323/") as PackageKit does.

Hey, I sent those two! My ego is about to explode right now :D

---

### Post by Hairy_Palms on 2009-06-21
just to bring it back to a technical issue, when i install the packagekit PPA into jaunty its entirely empty, no packages are listed, anyone know what i need to do?

---

### Post by Slug71 on 2009-06-21
> **23meg said:**
> Please avoid using the bug tracker for anything not pertaining to specific, reproducible software defects, including development and design policy matters such as this, which should go to the forums, Brainstorm or ubuntu-devel-discuss.

I did post it in the Forums, you read it didnt you. Its also posted in the Packagekit entry in Brainstorm and it can be marked as 'Wishlist' in Launchpad.

---

### Post by Slug71 on 2009-06-21
> **Hairy_Palms said:**
> just to bring it back to a technical issue, when i install the packagekit PPA into jaunty its entirely empty, no packages are listed, anyone know what i need to do?

Im not sure there is a PPA for Jaunty. It should be in Synaptic though.

---

### Post by Hairy_Palms on 2009-06-21
sorry, dont think i made myself clear, i mean ive installed packagekit-gnome from the PPA but when i open gpk-application theres nothing in it at all, the repo list shows up as empty, despite synaptic showing everything fine.

---

### Post by Swarms on 2009-06-21
So how is Appcenter going? Can we compare the systems yet?

---

### Post by 23meg on 2009-06-21
> **Slug71 said:**
> I did post it in the Forums, you read it didnt you. Its also posted in the Packagekit entry in Brainstorm 

I didn't say that you didn't post it in the forums or Brainstorm. I said that the bug tracker [isn't the right place to suggest and discuss this kind of thing]("https://help.ubuntu.com/community/ReportingBugs#When%20not%20to%20file%20a%20bug").

---

### Post by ktp on 2009-06-21
> **Swarms said:**
> So how is Appcenter going? Can we compare the systems yet?

I would also like to know more about "prototype"....something little more then on paper...just to get the feel of the UI and user interactions.  I am also more interested in how the update management going to play out...letting user chose what to automatically install, including all recommended updates, and more importantly the notification part if it is not going to be auto installed.  I am not to happy with the current default opening of the update manager.  

I do like the notification options PK has, i.e. I can chose to update now with a click or have notification icon to install when I want.  I also like that it notifies user that some updates will require restarting before the transaction starts.  It just seems to give minimal information but let the user be under control.  PK is not perfect, but I think it's good start in the right direction.

---

### Post by mpt on 2009-06-21
> **Swarms said:**
> So how is Appcenter going? Can we compare the systems yet?

Good question. So as not to derail this PackageKit thread, [I’ve replied in the AppCenter thread]("http://ubuntuforums.org/showthread.php?p=7494831#post7494831").

---

