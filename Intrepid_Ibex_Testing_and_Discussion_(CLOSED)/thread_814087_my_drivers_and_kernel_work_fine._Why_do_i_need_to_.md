---
title: "my drivers and kernel work fine. Why do i need to upgrade them for the next release?"
date: 2008-05-31
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by madjr on 2008-05-31
if i upgrade to intrepid, why can't i keep my old kernel and drivers in case they brake my hardware.

why can't we keep some of the stuff that "just works" with my hardware.


**[SIZE="4"]oh and i don't want to hear the word "[COLOR="Sienna"]recompile from source[/COLOR][/SIZE]**"

not my case, but I've seen many go back to gutsy because of kernel/driver issues.

shouldn't it be **optional** for one to upgrade kernel and drivers if these already work for them and let's say they just want the lattest gnome and the updated repos.

if the new kernel/drivers works for you then great, but if not you could fall back to the old kernel/drivers without having to recompile everything **from scratch**.

**i.e:**
someone reported that my same model laptop has issues with the new kernel.

what if i could upgrade to Intrepid but select to keep my old kernel.


**basically we're [COLOR="DarkRed"]forced[/COLOR] to upgrade if we want latest gnome and updated repos...** :(

---

### Post by smbm on 2008-05-31
> **madjr said:**
> 
**[SIZE="5"]oh and i don't want to hear the word "[COLOR="Sienna"]recompile from source[/COLOR][/SIZE]**"

That's 3 words

---

### Post by 23meg on 2008-05-31
[QUOTE=madjr]if i upgrade to intrepid, why can't i keep my old kernel and drivers in case they brake my hardware.[/QUOTE]

Because it's not practical to maintain and support multiple kernel versions for a single release, at least not in Main.

[QUOTE=madjr]why can't we keep some of the stuff that "just works" with my hardware.[/QUOTE]

Because your stuff that "just works" should most likely also "just work" with the next kernel as well, and if it doesn't, it should ideally be fixed in the new kernel (with help from you and others who have the same hardware, that is, good bug reports and feedback), and because "we" can't be held back for "your" convenience alone, especially when it's completely unknown whether an older kernel is actually the only fix, how large a user base is affected by the mysterious potential issues or by the "new kernel = breakage" paranoia. If you can find the workforce to maintain an old kernel for a new release in a PPA, or even Universe, do that. I've seen people do it.

[https://help.launchpad.net/PPAQuickStart](https://help.launchpad.net/PPAQuickStart)
[https://help.launchpad.net/PPA101](https://help.launchpad.net/PPA101)
[https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages](https://wiki.ubuntu.com/UbuntuDevelopment/NewPackages)

[QUOTE=madjr]oh and i don't want to hear the word "recompile from source"[/QUOTE]

And you just want to demand that others do the work while you sit and issue orders? That kind of attitude won't get much sympathy and won't get you very far.

---

### Post by ajackson on 2008-05-31
> **madjr said:**
> why can't i keep my old kernel and drivers in case they brake my hardware.
Following that logic, don't walk up/down stairs as you may fall, don't cross the road as you might get hit by a bus.

If you are unwilling to test out new stuff because it might break (despite the general notice that Ibex should not be used as your main OS) I do wonder why you are even in this part of the forum.

---

### Post by meborc on 2008-05-31
if everything is working, why upgrade to intrepid? i mean, you could stay on hardy until the next LTS comes out

---

### Post by 23meg on 2008-05-31
> **meborc said:**
> if everything is working, why upgrade to intrepid? i mean, you could stay on hardy until the next LTS comes out

The OP didn't say that everything was working. This is about keeping certain parts of the OS while upgrading others, not about upgrading the whole thing vs. not upgrading.

---

### Post by meborc on 2008-05-31
> **23meg said:**
> The OP didn't say that everything was working. This is about keeping certain parts of the OS while upgrading others, not about upgrading the whole thing vs. not upgrading.

he also didn't say that something was broken :) 

and even if there is, LTS should be well maintained over the next years

the fact that ubuntu releases every 6 months has made people feel like the "old" version is automatically outdated and that they NEED to upgrade... that is not so of course

but i see i have missed the point probably :)

---

### Post by issih on 2008-05-31
The reality is that the newest kernel is the one most likely to support the largest variety of hardware well. Sadly some people will have problems, that is just life, but if you carry on using an old kernel, new hardware won't be supported, hardware that doesn't work with that kernel will never ever work, progress just stops completely.

Why can't you personally keep the old kernel?...well you can, but it'll have to be under your own steam, Having as many people as possible running the same basic system makes support feasible, if you can pick and choose what you want to use, you have to expect that no one else will have the same set up...and then no one else can really help you out when things go wrong.

In order to have the ability to help people easily, it helps if the majority of people are using the same kernel, and the one that is used has to be chosen to be the one that works for the MOST people, not just you.

Pain when it craps up on you, but thats just the reality of things

---

### Post by gnomeuser on 2008-05-31
New support for protocols and hardware (just in case you get a new gadget), improved drivers (no driver is perfect, we approximate especially with wifi drivers right now so if you have that new kernels will provide a better experience) and naturally fixed security problems (a biggie) would be good reasons. 

If anything breaks naturally that is a regression and we would love that you told us about it by filing a bug. Such situations are taken very seriously.

Now there is another reason some features outside of the kernel such as providing a smooth flickerfree boot requires changes to the DRM stack in the kernel. This means that new functionality depends on that change being present and you will need to upgrade to get it.

If you are otherwise happy with your Hardy system, you can just keep using it. It is supported for many years, and once it is discontinued a clean upgrade path will be ensured to existing releases, if you want to be extra conservative, just ungrade to the release prior to the latest stable. It should have gotten 6 months worth of good testing, and you should easily be able to do a few searches on the forums for problems with your type of hardware in preparation for the upgrade.

---

### Post by ronacc on 2008-05-31
you don't have to upgrade to intrepid , if you have a system that is running well and does what you need and want keep using it . Hardy is an LTS relese and will be around for years . If you wan't to try the "latest and greatest" do a seperate install , really the only safe thing to do during the dev cycle as things WILL break . Heck my "main system" is always a couple of releases behind .

---

### Post by Sef on 2008-06-01
> Hardy is an LTS relese and will be around for years . 

Specifically, Hardy desktop will be supported for 3 years and the server for 5 years.

---

### Post by madjr on 2008-06-01
oops i was running fast so my first post was a bit incomplete.

just updated it

---

### Post by madjr on 2008-06-01
> **Sef said:**
> Specifically, Hardy desktop will be supported for 3 years and the server for 5 years.

i would like to use hardy for it's lifetime.

but gnome and the repos get outdated every 6 months.

basically we're **forced** to upgrade if we want latest gnome and updated repos... :(

---

### Post by smbm on 2008-06-01
> **madjr said:**
> 
basically we're **forced** to upgrade if we want latest gnome and updated repos... :(

You're not forced to do anything.

It's just a question of finding out how to do what you want to do. Linux is virtually infinitely customisable, 

You can build any kernel you want.

---

### Post by inportb on 2008-06-01
And what's wrong with building your own packages? If the latest binaries had to be supplied for every version of every system that has ever existed, it would be crazy. I'm guessing you're expecting to have the latest Gnome and updated repositories for Linux 0.01 as well, aren't you?

Why upgrade to Intrepid when it's still in development? If you want to find bugs, that's great; then you should have nothing to complain about. Otherwise, I don't see any reason to upgrade now except for thrill-seeking purposes.

---

### Post by olskar on 2008-06-01
> **madjr said:**
> i would like to use hardy for it's lifetime.

but gnome and the repos get outdated every 6 months.

basically we're **forced** to upgrade if we want latest gnome and updated repos... :(

I can agree with you that this is kind of bad..but I think it is what makes Ubuntu somewhat stable..if you just keep pushing in updated software in the repos as soon as it is released, the stableness (is there such a word?) will suffer.

---

### Post by ronacc on 2008-06-01
> **madjr said:**
> i would like to use hardy for it's lifetime.

but gnome and the repos get outdated every 6 months.

basically we're **forced** to upgrade if we want latest gnome and updated repos... :(

don't confuse needs and wants , to be blunt my Amiga would still do everything I NEED if it hadn't died from a lightning strike circa 1998 .My wants and expectations however change with time . If you WANT all the latest and greatest, yes upgrading is the best way . If upgrading every 6 months offends you , you can as has been noted build from source those packages you desire. You are free to choose the method that suits you.

---

### Post by durand on 2008-06-01
And thats what the backports repository is for, right? So that you can stay on a stable version while still updating some software.

---

### Post by madjr on 2008-06-02
> **olskar said:**
> I can agree with you that this is kind of bad..but I think it is what makes Ubuntu somewhat stable..if you just keep pushing in updated software in the repos as soon as it is released, the stableness (is there such a word?) will suffer.

so if i stay with Hardy, the new gnome versions won't be available in the repos?

thus forcing me to upgrade to intrepid?

oh and people upgrade simply because they want the new stuff but not have to compile it from scratch

---

### Post by smbm on 2008-06-02
> **madjr said:**
> so if i stay with Hardy, the new gnome versions won't be available in the repos?

thus forcing me to upgrade to intrepid?

oh and people upgrade simply because they want the new stuff but not have to compile it from scratch

You're not **forced** to upgrade.

You can do as you please.

---

### Post by RAOF on 2008-06-02
> **madjr said:**
> so if i stay with Hardy, the new gnome versions won't be available in the repos?

thus forcing me to upgrade to intrepid?

oh and people upgrade simply because they want the new stuff but not have to compile it from scratch

Feel free to request (and test) a [backport](https://help.ubuntu.com/community/UbuntuBackports) for interesting versions of stuff available in Intrepid but not Hardy.  You won't get all of GNOME, but if you actually *want* all of GNOME, you should either upgrade or choose a different distro.  The various different distros have different release policies, ranging from near-total-freeze (Debian stable, Ubuntu) through new-versions-of-non-libraries (Fedora) to rolling-release (Debian testing, Sid, Gentoo, etc).  If Ubuntu's release policy doesn't support your needs, there's nothing wrong with picking a different distro with a release policy closer to your desires.

---

### Post by madjr on 2008-06-03
> **RAOF said:**
> Feel free to request (and test) a [backport](https://help.ubuntu.com/community/UbuntuBackports) for interesting versions of stuff available in Intrepid but not Hardy.  You won't get all of GNOME, but if you actually *want* all of GNOME, you should either upgrade or choose a different distro.  The various different distros have different release policies, ranging from near-total-freeze (Debian stable, Ubuntu) through new-versions-of-non-libraries (Fedora) to rolling-release (Debian testing, Sid, Gentoo, etc).  If Ubuntu's release policy doesn't support your needs, there's nothing wrong with picking a different distro with a release policy closer to your desires.

thanks for the info, this not something thats clear when one enters the linux world

anyway, what are the advantages/disavantages of these different "**release policies**" and why has ubuntu choosen the freeze 1.

could this change in the future?

also, where would **windows** fit in? a combo of LTS and rolling (updated software and service packs with improvements)?

---

### Post by dzzsky on 2008-06-03
> **madjr said:**
> thanks for the info, this not something thats clear when one enters the linux world

anyway, what are the advantages/disavantages of these different "**release policies**" and why has ubuntu choosen the freeze 1.

could this change in the future?

also, where would **windows** fit in? a combo of LTS and rolling (updated software and service packs with improvements)?

Windows release policy is comparable to ubuntu.  I.e. they still release bug fixes and patches but neither update core components of the system.  You also have to upgrade to the newest version to get the biggest changes (xp to vista for windows or 8.4 to 8.10 for ubuntu).  

Ubuntu uses this policy for it's inherent stability.  Each release is tested as a whole before it's released to the general populas.

A rolling update means you don't have huge upgrade cycles (i.e. 8.4 to 8.10) and your software is the newest available version.  This of course has a negative effect on system stability.

---

### Post by durand on 2008-06-03
Ubuntu tries to be stable for new users. If something breaks, many people won't know what to do. I think ubuntu should update non essential apps more frequently but thats just my view. The whole idea of freezing is to keep it stable and as bug free as possble.

Gentoo uses rolling releases and it's really stable because when a package is released, it is kept in testing for a while and only then does it update on your system. However, portage (gentoo's equivalent to apt-get/dpkg) allows for different versions of the same package so the user can choose whether to use a stable, testing or unstable package.

dpkg probably supports this but debian, which is where dpkg originated, is supposed to be extremely stable and it is and I guess that kind of mentality was fed into dpkg.

---

### Post by RAOF on 2008-06-03
> **madjr said:**
> ...
anyway, what are the advantages/disavantages of these different "**release policies**" and why has ubuntu choosen the freeze 1.
...

In the simplest possible terms it's a tradeoff between *stability*[1] and *new features*.  The closer to 'complete freeze' you are (and Ubuntu releases are fairly close) the more sure you can be that everything you could do yesterday you can still do today.  The closer to 'rolling release' you go, the sooner you'll be able to do neat new things with your PC.

[1] Where stability is defined as "The system works **exactly** the same way today as it did yesterday", not the more familiar "doesn't crash".

---

### Post by madjr on 2008-06-03
> **durand said:**
> I think **ubuntu should update non essential apps more frequently** but thats just my view. 


+1

this is exactly what am trying to figure out for the LTS.

why would they freeze the repos even for normal apps.

After a year the LTS will feel **outdated** since there won't be any updates for your apps in the repos.

LTS means "long term **security**" more than "long term **support**".

what good is to use an **desktop** OS for 3 years if you can't update your apps or at least get binaries for them?

i mean even if i use **windows 2000** (a 8 year old OS) i can still get updated binaries for most apps.

or am i missing something?

---

### Post by RAOF on 2008-06-03
One man's non-essential app is another man's paycheck.  It's perfectly reasonable to use a desktop unchanged for many years - people who only want to do *work* on their machines may prefer to have this stability.  Corporate desktops *certainly* want this stability.

If you mostly like this stability, but would like one or two updated apps, then that's precisely what the backports are for.

---

### Post by ronacc on 2008-06-03
many if not most apps can be updated if you search around a bit or will you only accept things that are pushed out as "official" updates ? You want a cutting edge system without building from source occasionaly or installing a new release.Sorry it ain't gonna happen .
PS please post a screenshot of aeroglass running on your windows 2000 box.

---

### Post by madjr on 2008-06-04
> **ronacc said:**
> 
PS please post a screenshot of aeroglass running on your windows 2000 box.

here u go:

[IMG]http://cfs2.tistory.com/upload_control/download.blog?fhandle=YmxvZzEwMzQ4NEBmczIudGlzdG9yeS5jb206L2F0dGFjaC8xLzE4OC5naWY=[/IMG]

[http://www.docs.kr/entry/Download-Shock-Aero3D-en](http://www.docs.kr/entry/Download-Shock-Aero3D-en)

for Windows XP/**2000**/2003/Vista

oh and take a look at shock-desktop3d, i want something like  that in linux :(

[http://www.docs.kr/entry/Download-Shock-Desktop3D-en](http://www.docs.kr/entry/Download-Shock-Desktop3D-en)

i guess the backports aren't very popular, so the best way is the developers offering binaries with all dependencies from their own websites (like they do now for windows).

some are already doing so in sourceforge, etc

---

### Post by ronacc on 2008-06-04
You make my points quite nicely . You seem willing to run windows stuff that is not delivered by Windows Update, but want everything for Ubuntu delivered from the official repos via update-manager. And what I was asking for was a screenshot of THE aero glass from MS runing in windows 2000 not a lookalike hack.

---

### Post by meborc on 2008-06-04
> **madjr said:**
> ...

what good is to use an **desktop** OS for 3 years if you can't update your apps or at least get binaries for them?

i mean even if i use **windows 2000** (a 8 year old OS) i can still get updated binaries for most apps.

or am i missing something?
yes you are! :) windows update does not provide for "most app updates"


> **ronacc said:**
> You make my points quite nicely . You seem willing to run windows stuff that is not delivered by Windows Update, but want everything for Ubuntu delivered from the official repos via update-manager.
 ...

yeah... for example you will not get a new version of firefox when you run windows update manager, why do you want ubuntu to provide that capability

this would put a lot of strain on developers just to maintain backports repos for all apps to be compatible with all kernel versions... that work could be used more efficiently in making the recent version of ubuntu more bug-free and stable

---

### Post by cariboo on 2008-06-04
There is nothing to stop someone from using the Debian unstable repositories, but of course you have to try and get support from Debian too.

Jim

---

### Post by lisati on 2008-06-04
"Just works" might be fine if you're thinking "Just get on with it". But isn't "works really well" better?

---

### Post by autocrosser on 2008-06-04
In regards to the OP---I thought that we are all here to test NEW software--not blend old & new into a custom mix..

I'm here to see what's new--& if it breaks, I'll fix it/ask for help or boot into my "safe" backup install & wait til the problem has a answer. Maybe I'm crazy---but I LIKE testing new stuff.

And if you want to try the latest Gnome stuff--there is always the Garnome project.....  [http://www.gnome.org/projects/garnome/](http://www.gnome.org/projects/garnome/)

Current info from Garnome:

GARNOME 2.23.2 has been released 

[INDENT]**"**Hope you enjoy the ride.  We are pleased to announce the release of GARNOME 2.23.2 [Desktop]("http://www.linuxcompatible.org/GARNOME_2.23.2_s112050.html#") and [Developer]("http://www.linuxcompatible.org/GARNOME_2.23.2_s112050.html#") Platform. This is the second development release on our trip to GNOME 2.24, which will be out in September. 

This release is for anyone who wants to get his hands dirty on the development branch, or who'd like to get a peek at future features. If you want to help spot issues in GARNOME, this release is for you as well. 

As usual, you can get the tarball directly from the gnome.org site: 
 [http://download.gnome.org/sources/garnome/2.23/](http://download.gnome.org/sources/garnome/2.23/) 

Note: GNOME 2.23.x is an unstable branch and is assumed to be a moving target. Therefore, things in this release may not work as advertised. 

If you find any issues with this release, feel free to contact the GARNOMEies in the #garnome channel on GIMPNet (irc://irc.gnome.org), where we hang out, or post to the mailing list. 

More information is available at our project website:  [http://www.gnome.org/projects/garnome/](http://www.gnome.org/projects/garnome/) 

Enjoy, 

  The GARNOME Team**"**[/INDENT]

---

### Post by 23meg on 2008-06-04
Another option if you want to test the latest GNOME is the [GNOME Developer Kit]("http://live.gnome.org/GnomeDeveloperKit"), which provides a Foresight-based VMWare image or ISO with the latest GNOME, which you can upgrade with PackageKit after installing.

---

