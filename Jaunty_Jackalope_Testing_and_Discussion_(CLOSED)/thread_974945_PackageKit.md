---
title: "PackageKit?"
date: 2008-11-08
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Mr. Picklesworth on 2008-11-08
Does anyone know if something will be happening with PackageKit (in Ubuntu land) this release?

Playing with Fedora, it supports everything at this point that Ubuntu currently has downstream patches for, like auto codec install and launching package installations via web sites. PackageKit does it better by being a widespread piece of software that will hopefully find its way into everything. It is basically our only hope for some exceptionally cool functionality like Nautilus automatically finding applications to open certain files based on MIME type, which would of course be astounding.

I will be sad if nobody knows when Ubuntu will adopt the thing :(

---

### Post by plun on 2008-11-08
PackageKit is within Intrepids repo, one of the last packages which was updated.

The challenge I see is racing conditions with the apt-backend.

Intrepids Kernel is slow, Disk I/0.

It works great with 2.62.8-RC2 but with RC3 the fork error message is back again..


I would like to see a longer test and a removal of Ubuntus add/remove


PackageKit is also a strong project for the moment:
[http://www.packagekit.org/pk-authors.html](http://www.packagekit.org/pk-authors.html)

Sebastian Heinlein for Ubuntu.

---

### Post by Gina on 2008-11-08
Must admit I find it rather strange to have apps available in two places.  I generally use synaptic but some apps are not available there and you have to use add/remove.  I wonder why that is.

---

### Post by gnomeuser on 2008-11-08
> **Gina said:**
> Must admit I find it rather strange to have apps available in two places.  I generally use synaptic but some apps are not available there and you have to use add/remove.  I wonder why that is.

That is very likely a bug

That being said, if Ubuntu fails to adopt PackageKit for Jaunty it will be left in the dust. Upstreams are adopting PackageKit for installation of components on demand so it will need to present in Ubuntu.

We already have support in GStreamer to do automatic look up for the required plugin when doing playback. Many other places will join this way of doing things (Anjuta just announced some support for this as well e.g.).

Other use cases for PackageKit can be seen here:
[http://ubuntuforums.org/showpost.php?p=6036549&postcount=3](http://ubuntuforums.org/showpost.php?p=6036549&postcount=3)

---

### Post by bash on 2008-11-08
Gotta say, Packagekit looks nicer every time I check back on their site.

---

### Post by plun on 2008-11-08
Yup... its nice also for more experienced users, really fast.

This is the trouble bug
[https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/272410](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/272410)

I can clearly identify and say that this is a kernel Disk I/0 issue.


Just to install for everyone

sudo apt-get install packagekit packagekit-gnome

Repo ref
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=packagekit](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=packagekit)

---

### Post by Slug71 on 2008-11-08
> **Gina said:**
> Must admit I find it rather strange to have apps available in two places.  I generally use synaptic but some apps are not available there and you have to use add/remove.  I wonder why that is.

Have wondered about this too.

+1 for Packagekit.

---

### Post by bash on 2008-11-08
Thanks for the install instructions plun. I think I'll give it (and with that Jaunty) a try in the VM. And do those instructions already take care of apt integration or do I need to edit anything manually so that Packagekit uses the apt-backend that comes with Ubuntu?

---

### Post by plun on 2008-11-08
> **bash said:**
> Thanks for the install instructions plun. I think I'll give it (and with that Jaunty) a try in the VM. And do those instructions already take care of apt integration or do I need to edit anything manually so that Packagekit uses the apt-backend that comes with Ubuntu?

Nope just install  packagekit and packagekit-gnome

Then

Meny System > Administration > Add/remove Software. 


Also note that this version IS available also for Intrepid  !

I am rather sure that we can nail this bug....:)


On a faster PC I am also sure that this error doesn't occur.

---

### Post by bash on 2008-11-08
Updated my Ibex VM and installed Packagekit. When I tried the first time I got the fork error, but that was because I was still running on the old Ibex Kernel. After I rebooted it works for me without any problems. 

Really like the interface and the speed of the searches. A lot nicer in that area than synaptic (imho). Just one thing I haven't figured out yet: When I open the Packagekit Software-Sources window, there is no way to add or remove repos. I can only tick or untick certain repos but that is all. Am I missing something? Or if not how do you add new repos in Packagekit (and I don't mean editing /etc/apt/sources.list)

---

### Post by Mr. Picklesworth on 2008-11-08
I remember downloading a package which automatically added a repository when I was playing with Fedora recently. I wasn't paying much attention, though:
[http://rpmfusion.org/Configuration](http://rpmfusion.org/Configuration)

The weird thing is that it's an rpm package; not a .install file or anything specific to PackageKit. (Though that *would* be a nice idea, if we could add or remove repositories, with a click, within the same interface there).

---

### Post by gnomeuser on 2008-11-08
> **Mr. Picklesworth said:**
> I remember downloading a package which automatically added a repository when I was playing with Fedora recently. I wasn't paying much attention, though:
[http://rpmfusion.org/Configuration](http://rpmfusion.org/Configuration)

The weird thing is that it's an rpm package; not a .install file or anything specific to PackageKit. (Though that *would* be a nice idea, if we could add or remove repositories, with a click, within the same interface there).

PackageKit is NOT a replacement for rpm/dpkg/conary e.g. as such it will use the underlying technology to manage repos. Clicking the rpm incidently will open PackageKit, install the package (ask for gpg key confirmation and such), then voila there you go, repo added.

---

### Post by apoclypse on 2008-11-11
I've used packagekit in Fedora and imo, it is an inferior user experience compared to what Ubuntu has now. Not only is Ubuntu's solution more polished but I've found it to be more stable. If Synaptic goes, I go. The add/remove application is far more polished in Ubuntu than the packagekit UI. I can understand that there are some cool features that packagekit provides that are not available now but I personally don't see what the big deal is since to me one of the best things about Ubuntu is the way it handles packaging in both the UI and the underlying system (apt-get). 

Fedora's packaging system is rather unstable and I've had the updater stall trying to find updates on more than one occasion, this may be an issue with YUM but it only really happens when I try to update via packagekit.

---

### Post by Changturkey on 2008-11-11
> **apoclypse said:**
> I've used packagekit in Fedora and imo, it is an inferior user experience compared to what Ubuntu has now. Not only is Ubuntu's solution more polished but I've found it to be more stable. If Synaptic goes, I go. The add/remove application is far more polished in Ubuntu than the packagekit UI. I can understand that there are some cool features that packagekit provides that are not available now but I personally don't see what the big deal is since to me one of the best things about Ubuntu is the way it handles packaging in both the UI and the underlying system (apt-get). 

Fedora's packaging system is rather unstable and I've had the updater stall trying to find updates on more than one occasion, this may be an issue with YUM but it only really happens when I try to update via packagekit.

PackageKit is still in development. Your mentality is like saying gasoline cars do all the same thing as electric cars; electric cars are too experimental, why would we need them? PackageKit, from what I think, is trying to get a universal appearance/function of package manager for every type of distro.

---

### Post by gnomeuser on 2008-11-11
Personally I cannot wait for the day PackageKit becomes default installed on Ubuntu. What the poster above forgets is that it does not replace synaptic and the other existing tools. He is still free to use them as the rest of us enter the 21th century. 

Is PackageKit bugfree, no, not at all. &#323;o software is without bugs, but PackageKit upstream is very responsive to bugreports and eager to take patches. Bugs get fixed really quickly if the developers know about it, e.g. the last PK bug I filed had a fix commited to GIT 10 mins later.

---

### Post by apoclypse on 2008-11-11
> **Changturkey said:**
> PackageKit is still in development. Your mentality is like saying gasoline cars do all the same thing as electric cars; electric cars are too experimental, why would we need them? PackageKit, from what I think, is trying to get a universal appearance/function of package manager for every type of distro.

First of all you have no idea what my mentality is. I've used packagekit extensively and I can tell you without a doubt that its inferior to what Ubuntu  offers now in-terms of user experience. It may still be in development which is all the more reason not to jump on the bandwagon just because everyone else is doing it. 

Compare what we have now in Ubuntu and packagekit and you wlll find package kit severely lacking. That type of crap can fly on Fedora which has a history of spotty package management but on a Debian based disro you need to come better than that. Package management is the corner stone of Ubuntu/Debian and frankly I have yet to see any other distro come close to the updater/package management that Ubuntu provides.  

Your analogy is flawed anyway. Gasoline cars have many advantages that electric cars have yet to work around, that is why car manufacturers have compromised and chose to go with a hybrid solution. Besides that unlike gasoline cars Ubuntu's updater/package management isn't polluting our environment.

---

### Post by Changturkey on 2008-11-11
> **apoclypse said:**
> First of all you have no idea what my mentality is. I've used packagekit extensively and I can tell you without a doubt that its inferior to what Ubuntu  offers now in-terms of user experience. It may still be in development which is all the more reason not to jump on the bandwagon just because everyone else is doing it. 

Compare what we have now in Ubuntu and packagekit and you wlll find package kit severely lacking. That type of crap can fly on Fedora which has a history of spotty package management but on a Debian based disro you need to come better than that. Package management is the corner stone of Ubuntu/Debian and frankly I have yet to see any other distro come close to the updater/package management that Ubuntu provides.  

Your analogy is flawed anyway. Gasoline cars have many advantages that electric cars have yet to work around, that is why car manufacturers have compromised and chose to go with a hybrid solution. Besides that unlike gasoline cars Ubuntu's updater/package management isn't polluting our environment.

Sorry, I guess I had to infer your 'mentality'. Anyways, the idea is that just because something has performed well so long does not mean it is perfect, rather is is stagnating or will slowly become obsolete when something better arrives. If you want something really fast, use the command line. Other than that, PackageKit will probably be the new standard.

---

### Post by of_darkness on 2008-11-11
Why not make synaptic use packagekit ? as synaptic in the way of interface is the only sensible packagebrowser that i have looked at..

for me its all about the gui-interface and there i find synaptic dosent have any ugly big kidz-like icons and have alot more ways of loking at packages etc etc..

---

### Post by Neon Lights on 2008-11-11
Last I heard, the Apt backend wasn't finished enough to be adopted in Ubuntu, though it looks like that's been fixed. We'll see I guess, I agree it would be awesome to have. :]

---

### Post by ronacc on 2008-11-11
I have distros  that use all 3 major package systems and IMHO synaptic is the best for a combination of saftey and dependency resolution and ease of use  , only when packagekit excedes what we already have should we think about replacing synaptic .

---

### Post by autocrosser on 2008-11-11
I just used PackageKit for the updates I did this evening & I will say that it did the job--Not verbose enough by a very long shot as far as I would wish, but for the normal user it would work--"give me the updates & I don't care as long as it is painless".  I prefer far more information that it gave, so I for one will still use Synaptic/Update-Manager instead---but I can see a use-case for PackageKit.

I could see a "blend" between PK & Synaptic--could be the best of both worlds--I will agree with another poster that Apt/Synaptic is one of the main reasons I came to a Debian distro & I for one want far more info before (and during) a update--I would be interested in trying (if available), a version of PK with increased verbosity.

---

### Post by gnomeuser on 2008-11-11
> **ronacc said:**
> I have distros  that use all 3 major package systems and IMHO synaptic is the best for a combination of saftey and dependency resolution and ease of use  , only when packagekit excedes what we already have should we think about replacing synaptic .

*Sigh*

Again, nobody is talking Synaptic away, PackageKit does not replace it, it compliments it. It's not a question of either or, you get both if you want them. 

Now the default should be PackageKit but people who enjoy synaptic can easily keep it. Upgraded systems could have both without any issues. 

Secondly, synaptics does not do dependency resolution, it merely calls down into apt, PackageKit does the same thing and will thus give the very same result.

Thirdly, When you examine what PackageKit gives you it is not just a set of nicely designed tools for upgrading the distro, installing/removing packages. It gets you an easy way for application designers to call into the package manager to get packages installed on demand. Such as your archiver or media player installing say an compression handler or codec when an unsupported file is attempted opened. Synaptic cannot do this in it's wildest fantasy. Any solution to such problems involving apt would be horribly tied to the Debian platform whereas PackageKit allows a solution that can be adopted universally (meaning upstreams might actually start implementing these very useful features in applications you use every day).

All that is asked for is for PackageKit to be installed by default, I would like to see the updater and the install/remove applications used by default as well. 

Nobody proposed removing synaptic for good not making it impossible to install by hand should it not be found in the default install. Nobody is calling for replacement of the dpkg system. Anyone laboring under this impression should kindly read up on what PackageKit really is and why we need it before posting.

---

### Post by ronacc on 2008-11-11
sorry I should have been more careful and specified apt as what actualy does the resolution . I was not comparing synaptic/apt to packagekit but to yast/RPM  or the various guis into portage .

---

### Post by MaX on 2008-11-12
I've tried using Packagekit several times but it always fail on some timeout from a layer below. So far I've found it overly complicated and right now update-manager is much easier to use.

We're Debian based and as long as the packages (rpm, tar.gz, deb) don't merge I think we should stick to whatever Debian chooses.

---

### Post by plun on 2008-11-12
**Announcement: PyGTK PackageKit**

[http://www.glatzor.de/blog/blog-details/article/announcemnet-pygtk-packagekit/?tx_ttnews](http://www.glatzor.de/blog/blog-details/article/announcemnet-pygtk-packagekit/?tx_ttnews)[backPid]=4&cHash=7c9e59bd39

Also 2 demos

""The API is not yet set into stone. So I am open for comments and feedback!""

-----
ver 3.10 is not in ppa yet as I can see.
[https://edge.launchpad.net/~packagekit/+archive](https://edge.launchpad.net/~packagekit/+archive)

---

### Post by mirons on 2008-11-21
Does anybody knows if there is a plan to insert packagekit as default in Jaunty? I've just discovered this app and I falled in love...

---

### Post by Slug71 on 2008-11-21
> **mirons said:**
> Does anybody knows if there is a plan to insert packagekit as default in Jaunty? I've just discovered this app and I falled in love...

We don't know yet but a lot of us here are hoping :)

I'll be installing it anyway.

---

### Post by Eclipse. on 2008-11-21
All I'm really caring about is the version that is in jaunty atm getting sync for the time being.:lolflag:
Hopefully it will happen in the next few days.

---

### Post by Changturkey on 2008-11-21
Fedora has been using PackageKit since 8; I think Ubuntu should integrate it by 9.04/9.10.

---

### Post by gnomeuser on 2008-11-22
> **Changturkey said:**
> Fedora has been using PackageKit since 8; I think Ubuntu should integrate it by 9.04/9.10.

Fedora 9 actually, but I would certainly hope that Ubuntu adopt PackageKit solutions in 9.04 anything else would be at the height of ill guided decision making.

---

### Post by meastp on 2008-11-22
PK in Ubuntu would be brilliant! Cooperation across distros, instead of reinventing the wheel x times is great.

---

### Post by Changturkey on 2008-11-22
> **gnomeuser said:**
> Fedora 9 actually, but I would certainly hope that Ubuntu adopt PackageKit solutions in 9.04 anything else would be at the height of ill guided decision making.

Woops, yeah I mean't 9.

---

### Post by meastp on 2008-11-22
> **gnomeuser said:**
> Fedora 9 actually, but I would certainly hope that Ubuntu adopt PackageKit solutions in 9.04 anything else would be at the height of ill guided decision making.

Well, at least have some usability people provide some feedback on what is preventing it from being included, like what was done with Empathy/Pidgin.

---

### Post by MaX on 2008-11-22
Today my Update Applet (0.3.6) have been in "Refreshing software list" all day.
Nothing I do seems to make it finish..

Packagekit is NOT ready for Ubuntu...

---

### Post by plun on 2008-11-22
> **MaX said:**
> Today my Update Applet (0.3.6) have been in "Refreshing software list" all day.
Nothing I do seems to make it finish..

Packagekit is NOT ready for Ubuntu...


Jaunty IS a development version..... it should be unstable...:)


I dont know why Ubuntu tests old software such as ver 0.3.6 for PackageKit.... maybe a Debian never ending problem...:confused:

---

### Post by Eclipse. on 2008-11-22
> **plun said:**
> Jaunty IS a development version..... it should be unstable...:)


I dont know why Ubuntu tests old software such as ver 0.3.6 for PackageKit.... maybe a Debian never ending problem...:confused:

The reason why is because debain doesnt have packagekit in its repos, so it hasnt been upgraded with the debian syncs.Hopefully the latest version will get into jaunty soon.

---

### Post by plun on 2008-11-22
> **Eclipse. said:**
> The reason why is because debain doesnt have packagekit in its repos, so it hasnt been upgraded with the debian syncs.Hopefully the latest version will get into jaunty soon.

Yup... I knows that and also about a never ending typical Debian discussion within back yards....

Nevertheless 3.11 is out upstream

I hope that Sebastian can get support for the apt-backend.

Reference:
[http://www.packagekit.org/pk-download.html](http://www.packagekit.org/pk-download.html)

---

### Post by MaX on 2008-11-22
> **plun said:**
> Jaunty IS a development version..... it should be unstable...:)


I dont know why Ubuntu tests old software such as ver 0.3.6 for PackageKit.... maybe a Debian never ending problem...:confused:

0.3.6 is in Intrepid...

Packagekit in Jaunty kept telling me that there was an update although there wasn't, it wouldn't stop until I told it to "upgrade" the whole system. Where it did SOMETHING but didn't tell me what...

I like to see the terminal output in both Synaptic and update-manager...

---

### Post by plun on 2008-11-22
> **MaX said:**
> 0.3.6 is in Intrepid...

Packagekit in Jaunty kept telling me that there was an update although there wasn't, it wouldn't stop until I told it to "upgrade" the whole system. Where it did SOMETHING but didn't tell me what...

I like to see the terminal output in both Synaptic and update-manager...

Well.... file a bug and/or remove PackageKit   !

But... when upstream is at total another level its maybe spoiled time.

Ubuntu must throw in the highest possible version in the beginning of a dev cycle.

Just ridiculous to wait and wait for Debian.... and loose time.

PulseAudio is for example the same...  FF3.1 also...  

"It must be stable"....:lolflag:

---

### Post by Slug71 on 2008-11-22
> **plun said:**
> Well.... file a bug and/or remove PackageKit   !

But... when upstream is at total another level its maybe spoiled time.

Ubuntu must throw in the highest possible version in the beginning of a dev cycle.

Just ridiculous to wait and wait for Debian.... and loose time.

PulseAudio is for example the same...  FF3.1 also...  

"It must be stable"....:lolflag:

Agreed! I guess we can only hope.

---

### Post by plun on 2008-11-22
> **Slug71 said:**
> Agreed! I guess we can only hope.

Well... I just read PAs mailing list and apparently something is wrong.

You have a "handful" apps/functions which are important so throw them in as soon as possible....

But.... then devs must rank those....):P  "We are cannibals"...:)

---

### Post by Slug71 on 2008-11-23
Does the latest version of PK allow you to add PPA's in Software Sources yet?

---

### Post by Slug71 on 2008-11-24
Found this on Brainstorm. 
It ain't mine and is was done before Intrepid but figured i'll post it here to help further promote anyways.


[[IMG]http://brainstorm.ubuntu.com/idea/64/image/1/[/IMG]](http://brainstorm.ubuntu.com/idea/64/)

---

### Post by super.rad on 2008-11-24
Tried out packagekit on Fedora 10 last night and was really impressed with it, Jaunty definatley needs to include this

---

### Post by MaX on 2008-11-24
What (besides the new look) makes Packagekit better than add-remove programs or synaptic? or update-manager?

---

### Post by mirons on 2008-11-24
A better approach to package installing (uniform interface among multiple package system and standard way to install features such as codec "just-in-time", use of standard communication service such as dbus). IMHO it has all features in order to become a new standard (this is rather inappropriate, in fact is just a layer and not a brand new packaging system), and because of this it has to be in Jaunty.

---

### Post by Slug71 on 2008-11-24
Also if Ubuntu decides to adopt Packagekit it will be used by 2 major Distributions(Fedora & Ubuntu) with others likely to follow. It is already supported by Mandriva and OpenSuse too. So it is likely to become the first cross-platform Package Managment System which means with so many Distros using it the sky will be the limit as far as development goes and it will also become extremely stable.

Also for a piece of Software that is still really in development it is pretty impressive already. If Ubuntu does get it, just with Fedora and Ubuntu using it alone is going to make this piece of software go a long way.

All we need then is a good backend Distro's can agree on. :lolflag:

---

### Post by ronacc on 2008-11-24
> **Slug71 said:**
> 
All we need then is a good backend Distro's can agree on.

and there in lies the rub I can see a real "foodfight" developing over that:lolflag:

---

### Post by Slug71 on 2008-11-24
> **ronacc said:**
> and there in lies the rub I can see a real "foodfight" developing over that:lolflag:


:lolflag:

---

### Post by RAOF on 2008-11-24
> **Slug71 said:**
> ...
All we need then is a good backend Distro's can agree on.

Why?  We're unlikely to get this, since it'll require one or more distributions to totally drop their current packaging systems.  One of the points of PackageKit is that you *don't* need a common backend to do useful things.  It's an abstraction of the package-manager, not a (total) replacement for it.

In the unlikely event that we decided to replace apt/dpkg, it would be to get useful new features like rollback (or multi-arch).  There's no benefit to abandoning apt for PackageKit (even if that made sense) - there's less that you can do with PackageKit.

---

### Post by plun on 2008-11-25
> **RAOF said:**
> 
In the unlikely event that we decided to replace apt/dpkg, it would be to get useful new features like rollback (or multi-arch).  There's no benefit to abandoning apt for PackageKit (even if that made sense) - there's less that you can do with PackageKit.

Yup, most unlikely and "going down" to others package backends is not a good idea...  but maybe Conary  ?

The first step must be to use PackageKit instead of the update-manager and Ubuntus add/remove, the backend comes later. 

A unified way to handle updates and installs is a big step.

---

### Post by MaX on 2008-11-25
> **plun said:**
> Yup, most unlikely and "going down" to others package backends is not a good idea...  but maybe Conary  ?

The first step must be to use PackageKit instead of the update-manager and Ubuntus add/remove, the backend comes later. 

A unified way to handle updates and installs is a big step.

I'm sorry but I just don't seem to get it...

What does it matter if the package system is "unified" when the backend's aren't?

My mother still won't be able to take an rpm and just install it instead of an deb.

Oh, wow it looks the same on Fedora and Ubuntu, who cares? Users ordinarily only run ONE distribution so why should the package manager care?

Last but not least: Pushing for a software that has a "demo" interface (all interface mockups on the packagekit developers blog looks like crap) is just insane.
If someone ports add-remove-programs and update-manager so that it uses packagekit in the background I'll probably not care, but as long as they look and work better I will.

---

### Post by plun on 2008-11-25
> **MaX said:**
> I'm sorry but I just don't seem to get it...

What does it matter if the package system is "unified" when the backend's aren't?

My mother still won't be able to take an rpm and just install it instead of an deb.

Oh, wow it looks the same on Fedora and Ubuntu, who cares? Users ordinarily only run ONE distribution so why should the package manager care?

Last but not least: Pushing for a software that has a "demo" interface (all interface mockups on the packagekit developers blog looks like crap) is just insane.
If someone ports add-remove-programs and update-manager so that it uses packagekit in the background I'll probably not care, but as long as they look and work better I will.

There are several benefits to start with the frontend, just to do something in the same way for all major distributions is great.

PackageKit is also really good...also for a more skilled user because its fast. 

PackageKit is also a strong project for the moment and something for the future

[http://www.packagekit.org/pk-authors.html](http://www.packagekit.org/pk-authors.html)

Debian sits within their corner in the eco-system and for them this is probably not a big deal....  just stupid IMHO to join them within this "dead end".

---

### Post by ronacc on 2008-11-25
packagekit does seem to offer some nice features as a frontend and if it works with multiple backends all the better . As one who does "play" with multiple distributions a unified frontend would be welcome . I can say about backends that I get less "grief" with apt/dpkg than with other offerings.

---

### Post by Slug71 on 2008-11-25
> **Slug71 said:**
> All we need then is a good backend Distro's can agree on.

> **RAOF said:**
> Why?  We're unlikely to get this, since it'll require one or more distributions to totally drop their current packaging systems.  One of the points of PackageKit is that you *don't* need a common backend to do useful things.  It's an abstraction of the package-manager, not a (total) replacement for it.

In the unlikely event that we decided to replace apt/dpkg, it would be to get useful new features like rollback (or multi-arch).  There's no benefit to abandoning apt for PackageKit (even if that made sense) - there's less that you can do with PackageKit.

It was only a joke. I know that aint gonna happen anytime soon if ever.
Ronacc got it right :lolflag:

---

### Post by Mr. Picklesworth on 2008-11-25
> **MaX said:**
> I'm sorry but I just don't seem to get it...

What does it matter if the package system is "unified" when the backend's aren't?

My mother still won't be able to take an rpm and just install it instead of an deb.

Oh, wow it looks the same on Fedora and Ubuntu, who cares? Users ordinarily only run ONE distribution so why should the package manager care?

Last but not least: Pushing for a software that has a "demo" interface (all interface mockups on the packagekit developers blog looks like crap) is just insane.
If someone ports add-remove-programs and update-manager so that it uses packagekit in the background I'll probably not care, but as long as they look and work better I will.

Interface is way more than looks, though. What PackageKit gives us is a unified interface for other software to achieve software installation tasks. For example, Totem's automatic codec install in Ubuntu is a somewhat distro-specific hack. It was done for PackageKit and now works anywhere. There are examples of Nautilus automatically finding and installing software to open files based on their MIME types.
The current glchess (Applications -> Games -> Chess) makes a really cryptic request for certain packages it needs for 3D mode. It's ugly, but that's the best it can do. With PackageKit, it could have a magical ability to select those for installation.

If I recall correctly, PackageKit is getting a web plugin to jump in to package installation from a web page!

It's not just an identical interface for you (which isn't actually true because you one jump in and modify the GUI); it's an identical interface for everyone, so software can consistently help with package management to make it easy for Grandma to install stuff.

---

### Post by meastp on 2008-11-25
> **Mr. Picklesworth said:**
> Interface is way more than looks, though. What PackageKit gives us is **a unified interface for other software to achieve software installation tasks**. For example, Totem's automatic codec install in Ubuntu is a somewhat distro-specific hack. It was done for PackageKit and now works anywhere. There are examples of Nautilus automatically finding and installing software to open files based on their MIME types.
The current glchess (Applications -> Games -> Chess) makes a really cryptic request for certain packages it needs for 3D mode. It's ugly, but that's the best it can do. With PackageKit, it could have a magical ability to select those for installation.

If I recall correctly, PackageKit is getting a web plugin to jump in to package installation from a web page!

It's not just an identical interface for you (which isn't actually true because you one jump in and modify the GUI); it's an identical interface for everyone, so software can consistently help with package management to make it easy for Grandma to install stuff.

Yes, if the major distros adapt PackageKit, then KDE and Gnome applications can use PackageKit's interface/API to install software/codecs/etc. PK will get lots of exposure, and turn into a very stable product, and distros don't have to integrate their package system every release.

Application developers will only have to implement package management in their application once, and distributions will not have to modify this for their package system.

**Summary:**
So, it is not the equal *graphical* interface that is the largest benefit, but the time and frustration saved by application developers and distributions.

---

### Post by el_itur on 2008-11-25
> **Mr. Picklesworth said:**
> so software can consistently help with package management to make it easy for Grandma to install stuff.

Also when we finish putting togheter this kind of stuff, the "grandma" we are talking about will be your now-20-years-old-girlfriend :lolflag:

---

### Post by of_darkness on 2008-11-25
But pk i still ugly as hell compared to synaptic.. and who thef** uses install upgrade shitty stuff?? you use synaptic always one program that is god loking and powerfull.

so why not add the pk. stuff to synaptic and make it the one and only app, and when ppl are in way of addin and subtracting ,why not add the aptitude poweruser features to synaptic then one would have an truly awsome app.

(pk=pakagekit)

---

### Post by Slug71 on 2008-11-25
> **of_darkness said:**
> But pk i still ugly as hell compared to synaptic.. and who thef** uses install upgrade shitty stuff?? you use synaptic always one program that is god loking and powerfull.

so why not add the pk. stuff to synaptic and make it the one and only app, and when ppl are in way of addin and subtracting ,why not add the aptitude poweruser features to synaptic then one would have an truly awsome app.

(pk=pakagekit)

Ahh, PK looks way better than Synaptic IMO.
You can even schedule updates and stuff with it.

Why do you wanna add the PK stuff to Synaptic if Synaptic is better?

---

### Post by meastp on 2008-11-26
> **Slug71 said:**
> Ahh, PK looks way better than Synaptic IMO.
You can even schedule updates and stuff with it.

Why do you wanna add the PK stuff to Synaptic if Synaptic is better?

I seldomly use Synaptic, because it's really, *really* slow. Searching for packages takes ages...

Anyway, I tried to point out that the common programming interface is PK's most important feature. With PK across several distros, you can be certain that some of the usability wizards will look at it.

---

### Post by of_darkness on 2008-11-26
> **Slug71 said:**
> Ahh, PK looks way better than Synaptic IMO.
You can even schedule updates and stuff with it.

Why do you wanna add the PK stuff to Synaptic if Synaptic is better?

No big icons and stuff:/ looks simple,childish like remove programs etc:/ but well if you like that then well..

and still the sorting , the quick managing of alot of apps etc, filtering  those are the strong sides of synaptic.

aptitude can be better but it can also tacke ages to resolv dependencys, and that by using alot of 3påarty repos is somthing one is used to.

there the smart depndecy solver i good.

and the simpla fackt that its faster somtimes in handeling multiple posts, and somtimes aptitude is faster ,and if one is using all kebord scourtcuts then prob. aptitude can do all that synptic does and faster and better.

but i realy fail to se where in packagekit is that good judging by the screens.

and i do also find the structur/laout of menus bars windows etc inside the synaptic gui is near perfect.

but this is my personal reflactions based on how i use it.

---

### Post by Jay_Bee on 2008-11-26
You can still use Synaptic with PK so I don't really see the problem there.

---

### Post by Slug71 on 2008-11-26
> **of_darkness said:**
> No big icons and stuff:/ looks simple,childish like remove programs etc:/ but well if you like that then well..

and still the sorting , the quick managing of alot of apps etc, filtering  those are the strong sides of synaptic.

aptitude can be better but it can also tacke ages to resolv dependencys, and that by using alot of 3påarty repos is somthing one is used to.

there the smart depndecy solver i good.

and the simpla fackt that its faster somtimes in handeling multiple posts, and somtimes aptitude is faster ,and if one is using all kebord scourtcuts then prob. aptitude can do all that synptic does and faster and better.

but i realy fail to se where in packagekit is that good judging by the screens.

and i do also find the structur/laout of menus bars windows etc inside the synaptic gui is near perfect.

but this is my personal reflactions based on how i use it.

PK has more categories, better sorted, in add/remove than Synaptic does. Also there isnt two different places with stuff like Synaptic has with Synaptic and Add/Remove. 

Also PK is still in development so i wouldnt worry about looks too much yet. If it does get adopted by all the major and non major Distros im sure they will customize it to make it unique in their own way.

And like Jay-BEE said, you can use them side by side and im sure that if PK does become default that Synaptic will still be available in add/remove for the users that like Synaptic better.
But if lots of Distros begin to use PK it will become an extremely stable piece of software with lots of possibilities.

---

### Post by Slug71 on 2008-12-04
Are there any PPAs out there with a newer version of Pakagekit since they still havent been updated in the repos?

---

### Post by Eclipse. on 2008-12-04
> **Slug71 said:**
> Are there any PPAs out there with a newer version of Pakagekit since they still havent been updated in the repos?

I have had look, dont think so unfortunetly.

---

### Post by ato on 2008-12-04
> **Slug71 said:**
> Are there any PPAs out there with a newer version of Pakagekit since they still havent been updated in the repos?

[https://launchpad.net/~packagekit/+archive](https://launchpad.net/~packagekit/+archive)

---

### Post by Eclipse. on 2008-12-04
> **ato said:**
> [https://launchpad.net/~packagekit/+archive]("https://launchpad.net/%7Epackagekit/+archive")

Finally they updated it.:P

I checked it the other day and .6 was on it.lol

---

### Post by Slug71 on 2008-12-04
Awesome thanks!

---

### Post by MaX on 2008-12-05
> **Slug71 said:**
> PK has more categories, better sorted, in add/remove than Synaptic does. Also there isnt two different places with stuff like Synaptic has with Synaptic and Add/Remove. 

Also PK is still in development so i wouldnt worry about looks too much yet. If it does get adopted by all the major and non major Distros im sure they will customize it to make it unique in their own way.

And like Jay-BEE said, you can use them side by side and im sure that if PK does become default that Synaptic will still be available in add/remove for the users that like Synaptic better.
But if lots of Distros begin to use PK it will become an extremely stable piece of software with lots of possibilities.

The whole point of having both Synaptic and Add/Remove is to NOT have the libs exposed to the ordinary user. You shouldn't need to care about what libs the programs you install need, they should be installed automatically. This is how it works now.
Go to add/remove and install a program, everything will work.
If you are a little more of a power user you can find the libs in Synaptic.

Why would I be interested in seeing libs, ever?
Requirements and recommendations in .deb files should be enough.
And when it isn't you have synaptic or the command line.

Until someone who actually know how to do a user interface takes a look and fixes PK, I'd consider it not for use.

---

### Post by Slug71 on 2008-12-05
> **MaX said:**
> The whole point of having both Synaptic and Add/Remove is to NOT have the libs exposed to the ordinary user. You shouldn't need to care about what libs the programs you install need, they should be installed automatically. This is how it works now.
Go to add/remove and install a program, everything will work.
If you are a little more of a power user you can find the libs in Synaptic.

Why would I be interested in seeing libs, ever?
Requirements and recommendations in .deb files should be enough.
And when it isn't you have synaptic or the command line.

Until someone who actually know how to do a user interface takes a look and fixes PK, I'd consider it not for use.

Again, its still in development.

---

### Post by tretle on 2008-12-05
+1 for packagekit as default for jaunty, not because of the interface but because its currently really freaking annoying for developers to try and figure out a way to integrate package lookups into their apps and have it compatible with all distros systems(.rpm,.deb,apt,conary etc).

Packagekit = The sane front end

If you disagree I don't care, All I care about is ubuntu not being left behind when it comes to package integration in apps. Anjuta is a prime example of how this will be useful.

---

### Post by Changturkey on 2008-12-05
Will Kubuntu have decent PK integration as well?

---

### Post by Slug71 on 2008-12-06
> **Changturkey said:**
> Will Kubuntu have decent PK integration as well?

I dont see why not. It should be in Kubuntu's repos now too. Try it out.

---

### Post by ShirishAg75 on 2008-12-07
Kubuntu and ubuntu have been sharing the same repos for a long time AFAIK. The below is on Intrepid. 

```

~$ aptitude show kubuntu-desktop
Package: kubuntu-desktop
State: not installed
Version: 1.101
Priority: optional
Section: metapackages
Maintainer: Jonathan Riddell <jriddell@ubuntu.com>
Uncompressed Size: 49.2k
Depends: acpi, acpi-support, acpid, alsa-base, alsa-utils, anacron, apmd, ark, bc, ca-certificates, cups,
         cups-bsd, cups-client, cups-driver-gutenprint, dc, dolphin, dragonplayer, foomatic-db,
         foomatic-db-engine, foomatic-filters, genisoimage, ghostscript-x, hal, hotkey-setup, inputattach,
         kde-window-manager, kde-zeroconf, kdebase-workspace-bin, kdemultimedia-kio-plugins, kdepasswd, kdm,
         khelpcenter4, klipper, kmix, konsole, ksnapshot, ksysguard, ksystemlog, kubuntu-artwork-usplash, kuser,
         language-selector-qt, lftp, libgl1-mesa-glx, libglut3, libpam-ck-connector, libsasl2-modules, libxp6,
         okular, openprinting-ppds, pcmciautils, phonon-backend-xine, pnm2ppa, powermanagement-interface,
         readahead, screen, smbclient, software-properties-kde, systemsettings, ttf-bitstream-vera,
         ttf-dejavu-core, ttf-freefont, unzip, usplash, wireless-tools, wpasupplicant, x-ttcidfont-conf,
         xdg-user-dirs, xkb-data, xorg, zip
Recommends: adept, akregator, amarok, apport-qt, avahi-autoipd, avahi-daemon, bluez-cups, bluez-utils, bogofilter,
            brltty, cdparanoia, cdrdao, dvd+rw-tools, foo2zjs, foomatic-db-gutenprint, foomatic-db-hpijs,
            fortune-mod, gcc, gdebi-kde, gnupg-agent, gtk-qt-engine, guidance-power-manager, gwenview,
            hal-cups-utils, hpijs-ppds, hplip, hplip-gui, ijsgutenprint, im-switch, install-package, jockey-kde,
            k3b, kaddressbook, kamera, kate, kde-printer-applet, kdebase-plasma, kdebluetooth,
            kdegraphics-strigi-plugins, kdepim-kresources, kdepim-strigi-plugins, kdepim-wizards,
            kdeplasma-addons, kdesudo, kgrubeditor, kmag, kmail, kmousetool, knotes, konqueror,
            konqueror-nsplugins, konqueror-plugin-searchbar, kontact, konversation, kopete, korganizer, krdc,
            krfb, ktimetracker, ktorrent, kubuntu-default-settings, kubuntu-docs, kubuntu-konqueror-shortcuts,
            kvkbd, kwalletmanager, laptop-detect, libgl1-mesa-dri, libnss-mdns, libqca2-plugin-ossl,
            linux-headers-generic, make, mediamanager, min12xxw, network-manager-kde, okular-extra-backends,
            openoffice.org-calc, openoffice.org-impress, openoffice.org-kde, openoffice.org-math,
            openoffice.org-writer, oxygen-cursor-theme, pinentry-qt4, plasmoid-quickaccess, powernowd, pxljr,
            rdesktop, speedcrunch, splix, strigi-client, system-config-printer-kde, ttf-arabeyes,
            ttf-arphic-uming, ttf-indic-fonts-core, ttf-kochi-gothic, ttf-kochi-mincho, ttf-lao, ttf-thai-tlwg,
            ttf-unfonts-core, update-notifier-kde, wodim, wvdial, xcursor-themes, xdg-utils
Conflicts: kubuntu-kde4-desktop
Replaces: kubuntu-kde4-desktop
Provides: kubuntu-kde4-desktop
Description: Kubuntu desktop system
 This package depends on all of the packages in the Kubuntu desktop system. Installing this package will include
 the default Kubuntu KDE installation. It is safe to remove this package if some of the desktop system packages
 are not desired.

``` 

and 

```

$ apt-cache policy kubuntu-desktop
kubuntu-desktop:
  Installed: (none)
  Candidate: 1.101
  Version table:
     1.101 0
        500 http://archive.**ubuntu**.com intrepid/main Packages

```

As can be seen they share the same archive.

---

### Post by Kow on 2008-12-07
My opinion: Keep PK aside from the main ubuntu system (ie not preinstalled) until 9.10 and perhaps then more aggressive measures could be taken like having it installed by default.

---

### Post by Slug71 on 2008-12-07
> **Kow said:**
> My opinion: Keep PK aside from the main ubuntu system (ie not preinstalled) until 9.10 and perhaps then more aggressive measures could be taken like having it installed by default.

By 9.10 Ubuntu will probably be the only distro to not have it. Opensuse and Mandriva now have support for PK and Fedora have had it by default since F-9. There are probably lots of smaller distros out there that are already using it by default too or considering to include it by default.

Could you imagine how stable and how fast PK will develop yet maintaining its stability if most Distros, at least the big ones, begin to use it.

All the functions and features people would like in a package manager front-end, like time based updates for those who get cheaper rates at night etc, will be able to happen regardless of what distro your using. And it wont be long till we can see these kind of features. The GUIs could be completely customizable.

---

### Post by ronacc on 2008-12-07
While packagekit has some nice features until they make the package list alphabetical , or give it atleast some decernable order it is unacceptable.

---

### Post by MaX on 2008-12-07
> **ronacc said:**
> While packagekit has some nice features until they make the package list alphabetical , or give it atleast some decernable order it is unacceptable.

Yes... if Fedora uses it since F-9 why hasn't the interface improved "dramatically" since then?

Because it's only "geeks" using the damn system. Geeks don't care about interface, unless they are an interface geek (as me...)

I say go for it in 9.10 and keep it of main and let it mature, Ubuntu doesn't have to be first with everything.

---

### Post by castrojo on 2008-12-07
Hi guys,

I am at UDS and asked Sebastian Heinlein and Michael Vogt about the PK plan for Jaunty. Right now it's looking like the daemon will be installed by default so that things like the Ajunta and whatnot will work.

Don't have anymore detail yet, keep an eye on [https://blueprints.edge.launchpad.net/sprints/uds-jaunty](https://blueprints.edge.launchpad.net/sprints/uds-jaunty) and [http://summit.ubuntu.com](http://summit.ubuntu.com)

---

### Post by Slug71 on 2008-12-07
> **whiprush said:**
> Hi guys,

I am at UDS and asked Sebastian Heinlein and Michael Vogt about the PK plan for Jaunty. Right now it's looking like the daemon will be installed by default so that things like the Ajunta and whatnot will work.

Don't have anymore detail yet, keep an eye on [https://blueprints.edge.launchpad.net/sprints/uds-jaunty](https://blueprints.edge.launchpad.net/sprints/uds-jaunty) and [http://summit.ubuntu.com](http://summit.ubuntu.com)


Thanks very much for the info. Looking forward to it!

---

### Post by super.rad on 2008-12-17
Any news on this? As were not getting plymouth, login experience and who knows if we'll finally see a new theme it would be a real shame if they dont include packagekit as default.

EDIT: Found [this](http://web.mornfall.net/blog/farewell__44___adept.html) on planetkde which answers my question. Jaunty will be getting packagekit as default

---

### Post by tretle on 2008-12-19
waiting patiently for some other confirmation from ubuntu devs, hopefully this wont be a kubuntu move only.

---

### Post by OzzyFrank on 2008-12-19
Thanks guys - interesting thread. I hadn't even heard of this before now, but since it seems it won't mess with Synaptic in any way, I might try it.

As for the **Synaptic vs Add/Remove...** I can tell you that since Ubuntu 6.10, I have found they wildly differ on what they tell me is and isn't installed. And I can tell you that it isn't Synaptic that is at fault... especially when Add/Remove tells me I haven't got things like Wine, restricted codecs, and a bunch of apps I use every day. I have looked at that since then, on upgraded systems and fresh installs, and it is always the same. Add/Remove, in my humble opinion, is so utterly flawed, so hideously inept, I can't see why it is still in Ubuntu. If this is a "bug", then it is something that hasn't been addressed in over 2 years from what I can see! And considering both of these are installed by default, you wouldn't expect this. (I apparently don't have OpenOffice.org installed... what a joke, hehehe!)

---

### Post by tretle on 2008-12-22
Still no official confirmation to be found for the gnome side.

---

### Post by Slug71 on 2009-01-09
Any Devs have some news regarding Packagekit in Jaunty?

I see we are also falling behind with the version as 0.4.1 is now out.

---

### Post by Slug71 on 2009-01-11
Have filed a bug for a version update of Packagekit in Jaunty's repos.

[https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/316162](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/316162)

---

### Post by uBeer on 2009-01-11
> **OzzyFrank said:**
> Thanks guys - interesting thread. I hadn't even heard of this before now, but since it seems it won't mess with Synaptic in any way, I might try it.

As for the **Synaptic vs Add/Remove...** I can tell you that since Ubuntu 6.10, I have found they wildly differ on what they tell me is and isn't installed. And I can tell you that it isn't Synaptic that is at fault... especially when Add/Remove tells me I haven't got things like Wine, restricted codecs, and a bunch of apps I use every day. I have looked at that since then, on upgraded systems and fresh installs, and it is always the same. Add/Remove, in my humble opinion, is so utterly flawed, so hideously inept, I can't see why it is still in Ubuntu. If this is a "bug", then it is something that hasn't been addressed in over 2 years from what I can see! And considering both of these are installed by default, you wouldn't expect this. (I apparently don't have OpenOffice.org installed... what a joke, hehehe!)

Whenever I use Add/Remove it works fine and I see what I've installed with Add/Remove. When I use Synaptic and install the right set of packages I can see it change in Add/Remove as well, but the behavior is not that consistent. But I can see when it comes in useful: when less experienced users use it (and don't use Synaptic)!! One of my brothers was like a little child again when I showed him how easy it can be to install stuff. Some other friends of mine were impressed to. It *is* easy :popcorn: (I use it alot to find apps for obscure tasks...)
About OpenOffice.org: you'll probably see in Add/Remove that Writer, Presenter and Spreadsheet are installed and not the whole office set, saves space on the CD.

Anyways, the idea of Add/Remove is really great, but there are still some inconsistencies for 'advanced' (Synaptic) users.

Edit: And it prevents unexperienced users from ruining their system by letting them not remove too much stuff! Very convenient! And less convenient for the more experienced, but he, we've got apt-get :D

---

### Post by RAOF on 2009-01-11
> **tretle said:**
> Still no official confirmation to be found for the gnome side.

It doesn't *really* matter whether packagekit is installed by default, does it?  Programs that want to use it (Ajunta, or whatever) will just depend on the daemon, and it'll get installed.

Not that I'm against installing it by default, but it's likely that'll happen after something in the default install depends on it.  Before then, it's not really very useful, is it :).

---

### Post by gnomeuser on 2009-01-11
> **RAOF said:**
> It doesn't *really* matter whether packagekit is installed by default, does it?  Programs that want to use it (Ajunta, or whatever) will just depend on the daemon, and it'll get installed.

Not that I'm against installing it by default, but it's likely that'll happen after something in the default install depends on it.  Before then, it's not really very useful, is it :).

Yes it matters. At least it matters if you are serious about commiting to upstream (and remember more and more applications are going to be depending on it to install things on demand, users will also want to be able to use the same tools to manage their installs). Additionally for the target they are aimed the tools are superior to what we have, e.g. on an average desktop we could preconfigure packagekit to not require a password for updating the system which would be very handy.

---

### Post by RAOF on 2009-01-11
> **gnomeuser said:**
> Yes it matters. At least it matters if you are serious about commiting to upstream (and remember more and more applications are going to be depending on it to install things on demand, users will also want to be able to use the same tools to manage their installs). Additionally for the target they are aimed the tools are superior to what we have, e.g. on an average desktop we could preconfigure packagekit to not require a password for updating the system which would be very handy.

Ah.  You're thinking of replacing Add/Remove with a PackageKit frontend.  But since PackageKit (the library/daemon) works over apt, there need not be a lot of UI associated with application-requested package installation. I'm not sure how much of a clash Add/Remove would be over this.

My last experience with the PackageKit frontend while playing around with Fedora 9 wasn't particularly positive; it seemed to spend a lot of time blocking.  I presume it's got substantially better since then.

---

### Post by Slug71 on 2009-01-11
I wonder if the plan is to eventually have Packagekit as the frontend and Smart Package Manager as the backend?

---

### Post by RAOF on 2009-01-11
> **Slug71 said:**
> I wonder if the plan is to eventually have Packagekit as the frontend and Smart Package Manager as the backend?

No, I don't think so :).

---

### Post by Slug71 on 2009-01-11
> **RAOF said:**
> No, I don't think so :).

Thats what i keep telling myself but then cant help but wonder why Canonical would be funding a project since 2005 and have Devs working on it if it has no intention of using it. :confused:

---

### Post by Slug71 on 2009-01-13
Did Packagekit hit Jaunty? I had some stuff come through updates this morning.

---

### Post by Slug71 on 2009-01-21
Less than a month to Feature Freeze and still no Packagekit. :(
I suppose this too will only now happen in 9.10.

---

### Post by RAOF on 2009-01-22
Ok.  Appart from the bad dbus permissions, packagekit appears to work just fine.

---

### Post by garba on 2009-01-22
> **super.rad said:**
> Any news on this? As were not getting plymouth, login experience and who knows if we'll finally see a new theme it would be a real shame if they dont include packagekit as default.

EDIT: Found [this](http://web.mornfall.net/blog/farewell__44___adept.html) on planetkde which answers my question. Jaunty will be getting packagekit as default

nice, they're finally getting rid of adept, it was about time ^^

---

### Post by super.rad on 2009-01-22
Yeah it's about time, I can't stand adept.
Looks like it's starting to come in, wasnt paying too much attention but had a few packagekit libarys and things installed earlier

---

### Post by Slug71 on 2009-01-22
Just had some stuff for Packagekit come in too. :)

---

### Post by BGFG on 2009-03-23
I tried packagekit in Intrepid and it crashed, Just installed it in jaunty though and all seems well. Would like to see more detaile progress when it's downloading package lists though.

safe to remove update manager now ? :)

---

### Post by biasquez on 2009-03-23
i don't think that packagekit will replace update-manager or adept...infact, ubuntu/kubuntu is on alpha 6 stage and packagekit isn't updated/supported enough. according to me, packagekit is better than update-manager but packagekit doesn't support apport like update-manager.

---

### Post by BGFG on 2009-03-23
Crash ? will check for reports.
Message: Launch helper exited with unknown return code 1

---

### Post by Slug71 on 2009-03-23
> **biasquez said:**
> i don't think that packagekit will replace update-manager or adept...infact, ubuntu/kubuntu is on alpha 6 stage and packagekit isn't updated/supported enough. according to me, packagekit is better than update-manager but packagekit doesn't support apport like update-manager.

Kpackagekit has replaced Adept in Kubuntu AFAIK.

---

### Post by Reiger on 2009-03-23
> **Slug71 said:**
> Kpackagekit has replaced Adept in Kubuntu AFAIK.

Well not on _this_ Jaunty Kubuntu machine. And I hope it will not until that fork error gets fixed first.

---

### Post by biasquez on 2009-03-24
now i'm testing packagekit 0.4.6 (git version), it's very stable and complete ;)

p.s. if you want, i can paste here simple script that compile and install latest version of packagekit (for gnome)

---

### Post by screaminj3sus on 2009-03-25
can't stand package kit, had nothing but trouble with it in fedora. Never had any problems with synaptics.

---

### Post by Scotty Bones on 2009-03-25
So... **this** is what the horrid monstrosity, that led to me killing Fedora10 15 minutes after installing it, is called.  I hope the dev's keep a 15 foot poll between this and Ubuntu's default install.

---

### Post by screaminj3sus on 2009-03-25
> **Scotty Bones said:**
> So... **this** is what the horrid monstrosity, that led to me killing Fedora10 15 minutes after installing it, is called.  I hope the dev's keep a 15 foot poll between this and Ubuntu's default install.

Couldn't agree more. I never had any problems in fedora 9 with pirut but package kit is AWFUL, it constantly freezes loading repository info ect and you can't cancel it and then you can't do ANYTHING else with the package manager without a restart, I had such a myriad of problems with that crap.

Synaptics>packagekit any day.

---

### Post by Reiger on 2009-03-26
After an update or 2 ago I haven't seen the fork error anymore... Starting to warm up to package kit, altough that icon which looks like it came straight out of an WinXP install may be a bit 'dated' for my taste.

---

