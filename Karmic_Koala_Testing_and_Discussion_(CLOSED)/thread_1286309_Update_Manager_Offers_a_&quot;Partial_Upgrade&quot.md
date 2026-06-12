---
title: "Update Manager Offers a &quot;Partial Upgrade&quot;? Read This."
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 23meg on 2009-10-08
After the release of Ubuntu 9.10 Beta, we've been flooded with threads asking for assistance related to issues caused by careless usage of the "Partial Upgrade" feature of Update Manager. This document aims to clarify what a "Partial Upgrade" is, and why, **in most cases, you'll want to avoid it**.


[SIZE="4"]**Summary**[/SIZE]
[SIZE="1"]**or "I don't really care if I keep messing things up and wasting my and others' time with preventable problems, and you have 30 seconds to convince me to care!"**[/SIZE]

If you use Update Manager to upgrade your packages, and it offers to do a "Partial Upgrade", do not accept it without thoroughly checking what packages it offers to remove, upgrade and install. If you do, you will most likely end up removing packages that shouldn't be removed, and waste time and effort repairing your testing installation and asking for assistance. 

Most "Partial Upgrade" situations occur due to package archive inconsistencies, which will typically be resolved within a few hours. If your package manager is confused, and so are you, **simply wait** and hold off the updates until things settle down. 


[SIZE="4"]**Short Version**[/SIZE]
[SIZE="1"]or **"Hmm, so I shouldn't blindly do "Partial Upgrade"s and dist-upgrade? I didn't know that..."**[/SIZE]

Due to the fact that uploads to the repositories of the active development release (Karmic, as of now) are asynchronous and uncoordinated, dependencies of certain packages may arrive later than the dependent package. This causes package management tools such as Update Manager, which are mainly meant to be used with stable releases of Ubuntu where the package archive is always consistent, to interpret the situation as requiring a dist-upgrade to install new packages and/or repair packages in a "reqreinst" (requires reinstallation) state. What Update Manager performs when doing a "Partial Upgrade" is a dist-upgrade.

When testing development releases, most of the time, a "Partial Upgrade" is undesired. The situations where it's needed are limited to new packages obsoleting old ones (as in the case of the software-center package replacing software-store) and package removals from the archive.

Do not assume that since you're running a development release, a "Partial Upgrade" is necessarily warranted.


**[SIZE="4"]Long Version[/SIZE]**
[SIZE="1"]**or "I want to be a better tester! I care! Tell me more!"**[/SIZE]

In its normal operating mode, Update Manager will not offer to remove packages. This is the equivalent of "apt-get upgrade"ing your existing packages. In "Partial Upgrade" mode, it can. Sometimes, the removal is warranted, such as when a package is obsoloted by a new one. Other times, it will not be, and a "Partial Upgrade" can offer to remove important packages due to missing dependencies.

Now, the key question: 

"**How do I know whether a package is actually meant to be replaced or removed?**"

There's more than one way:

[list][*] Check the changelog of the package in question. You can do this via "Package > Download Changelog" in Synaptic, or "aptitude changelog package_name", or by going to [packages.ubuntu.com]("http://packages.ubuntu.com") and clicking "Ubuntu changelog" for the package you're curious about, or visiting the URL 

[https://launchpad.net/ubuntu/+source/](https://launchpad.net/ubuntu/+source/)[COLOR="DarkRed"]package_name[/COLOR]/+changelog

where [COLOR="DarkRed"]package_name[/COLOR] is the name of the source package you're curious about. The most recent changelog entry will indicate the reason for the removal or replacement, if there is one.


[*] Keep an eye on the changes mailing list or RSS feed for the active development release. The current ones are the [karmic-changes mailing list]("https://lists.ubuntu.com/mailman/listinfo/karmic-changes"), and [its RSS counterpart]("http://feeds.ubuntu-nl.org/KarmicChanges").

For an example scenario of using the list of recent changes to determine whether a package removal and "Partial Upgrade" is safe, see [post #101]("http://ubuntuforums.org/showpost.php?p=8142730&postcount=101").


[*] Check the [build status information page]("https://launchpad.net/ubuntu/+builds") for Ubuntu and the [queue of new uploads to Karmic]("https://launchpad.net/ubuntu/karmic/+queue") on Launchpad to see if those mysterious missing dependencies are coming down the pipes, or there are problems preventing them from being built.


[*] Do a forum search, or [join the #ubuntu+1 channel on irc.freenode.net]("https://help.ubuntu.com/community/InternetRelayChat") and ask around to see whether other people are having problems with the same package(s).


[*] If you're still confused, simply **wait** and see if things are magically fixed within a few hours. If not, start a new thread or post to an existing one on the same issue to check with others.[/list]

A typical interaction with a package manager involves the following three steps:

[list] [*] You select some packages to be installed / removed / upgraded


[*] The package manager resolves your intention according to its package management logic, the available software sources, and the priorities you've indicated (as in APT pinning), if any, to a set of actions it has to perform, and outputs a list of those actions


[*] You check this list, confirm it if you're happy with it, or cancel it and refine your selection until you're happy with it.[/list]

If you skip the third step, assuming that simply updating your package information and hitting "Apply" or pressing "Enter" when the prompt comes up will give you the latest changes, and/or that since you're running a development release, any kind of package conflict / removal / replacement, even those that seem to intentionally remove lots of packages, are to be expected, you'll keep breaking your installation unnecessarily. Don't do that. Review that list of changes.

While asking for and providing assistance regarding testing is one of the main functions of this forum, learning [the basics of using development releases]("https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases") is a prerequisite for doing useful testing, and if lots of people keep messing up their testing installations due to being unfamiliar with those basics, the forum will get flooded with duplicate threads and quicky become much less useful to everyone. 

Please take some time to learn the basics, and if you need help with that, don't hesitate to ask!

---

### Post by douham on 2009-10-08
+1

Well done 23meg
Maybe we need a post like this as a sticky as soon as the 10.04 testing forum is opened.

---

### Post by emarkay on 2009-10-08
Excellent! 
I understand this also goes for "Apt-get upgrade" and "Fix Broken Packages" in the Recovery boot; if it says " xx Packages Removed" be EXTRA AWARE of what is being removed.  For example, removing the kernel can really ruin your day...

---

### Post by andrewabc on 2009-10-08
sometimes I go into synaptic and "mark all packages for upgrade", and it selects the unselected packages. Also, sometimes a package gets renamed and thus it will get removed and the newly named package will get installed (make sure before updating, synaptic should show it).

But I definitely agree with waiting 24 hours before attempting to upgrade, and do more investigating as to why it is offering partial upgrade.

---

### Post by novafluxx on 2009-10-08
+1 great write-up, we need this for 10.04 too!

---

### Post by ranch hand on 2009-10-08
The idea of starting the 10.04 cycle with a sticky like this is a GREAT idea.

Good job.

Thanks.

---

### Post by Squonk07 on 2009-10-09
+1

Thank you for explaining all this. I had been wondering just why Partial Upgrades were offered at all, given their potential for serious breakage. Now I understand why the option exists, and what is going on in the underlying logic.

This definitely needs to be made a Sticky for 10.04. I think a lot of people would be very grateful to have read this before considering clicking that Partial Upgrade button.

---

### Post by HarshReality on 2009-10-09
I did one of these yest. or so using the Karmic Beta and now its telling me it failed and then the system is updated and um will now close. I figure its a lag on servers but we will see.

:)

---

### Post by rburkartjo on 2009-10-09
23 tks for the info this sticky should be included in all testing forms just my 2 cents

---

### Post by dino99 on 2009-10-09
maybe the best solution should be:

 partial updates( greyed packages) not shown in the list. If you agree, brainstorm can promote this.

---

### Post by andresmh on 2009-10-09
so when assessing partial upgrades, one should worry only about package removals? or also about package updates?

---

### Post by psyke83 on 2009-10-09
> **andresmh said:**
> so when assessing partial upgrades, one should worry only about package removals? or also about package updates?

A Partial Upgrade only occurs when one or more packages are to be removed. Otherwise it's a regular upgrade. New packages are inconsequential.

---

### Post by Regenweald on 2009-10-09
Why even offer a partial upgrade in the first place ? If the partial is offered in the case of unmet dependencies which almost certainly break systems, why is it a feature ? Unmet dependencies = unresolved packages + breakage, so if upgrade manager cannot resolve dependencies, why not this message:

"Update manager has discovered package dependency issues that may potentially harm the system. Please run the update manager at a later time"

---

### Post by BCurtisWX on 2009-10-09
Don't forget the option of running "sudo apt-get update; sudo apt-get upgrade" in the terminal.  I may be mistaken but I think doing it this way, the apt-get interface will "keep back" packages with unmet dependencies.  This information is more relevant for those that really really want to install the good package updates, and ignore the bad ones.

---

### Post by ranch hand on 2009-10-09
Yes.  Apt even holds back packages that Synaptic (with Smart Upgrade enabled) lets through.  I recommend synaptic for those who insist on a gui.  I use it on some of my 9.10 installs and apt on the others.

Apt is safer.

Update-manager needs to be just the way it is to test it, just like the other apps, in the real world of users.  Hopefully those users are smart enough to realize that this is a "testing" release.

---

### Post by psyke83 on 2009-10-09
> **BCurtisWX said:**
> Don't forget the option of running "sudo apt-get update; sudo apt-get upgrade" in the terminal.  I may be mistaken but I think doing it this way, the apt-get interface will "keep back" packages with unmet dependencies.  This information is more relevant for those that really really want to install the good package updates, and ignore the bad ones.

That is true, but it's not the whole story.

A dist-upgrade is sometimes necessary to allow the installation of *new* packages, and sometimes a "Partial Upgrade" is actually necessary in order to replace an obsolete package with another (e.g. software-store -> software-center).

Theoretically, using "apt-get upgrade" could leave packages perpetually held-back, which is also not ideal.

---

### Post by ranch hand on 2009-10-09
Yup, you are right.  That is one reason that I have several 9.10 versions installed.  I can afford to really screw some up and still have some that work.

I am fighting with the new update right now.  Both the synaptic and apt updates have buggered things up.

This is testing, you do need to take a chance now and then.

---

### Post by Nerd_bloke on 2009-10-09
There was [a bug]("https://bugs.launchpad.net/bugs/438164") logged on this a couple days ago. 

It might benefit from some constructive comments.

---

### Post by zaphodbblx on 2009-10-09
Ahhhh I so wish I had seen this first! I guess my britches got too big after having so few problem with the Jaunty beta!  I done broke my system. C'est la vie. No complaints  I will most likely fool around with a few new distros until karmic goes final


I will consider this a teachable moment

---

### Post by popejeremy on 2009-10-10
I was told on this forum a while ago to use apt-get to upgrade, and that it's O.K. to do so as long as no packages are being removed, even if some packages are being held back.

But now the kernel and ubuntu-netbook-remix have been held back for a week or more. Did I do it wrong? Or do I just need to keep waiting?

---

### Post by ranch hand on 2009-10-10
I would use synaptic, making sure that the default setting is for "Smart Update" (or smart upgrade, can't remember).  This is not as safe as apt-get but close.

You probably have a bunch more updates that are not coming to you because of the lack of the new kernal (31-13.43).

---

### Post by popejeremy on 2009-10-10
> **ranch hand said:**
> I would use synaptic, making sure that the default setting is for "Smart Update" (or smart upgrade, can't remember).  This is not as safe as apt-get but close.

You probably have a bunch more updates that are not coming to you because of the lack of the new kernal (31-13.43).

I looked at what you suggest, and fired up Synaptic set for Smart Update. Synaptic wants to upgrade the kernel and ubuntu-netbook-remix, which looks good to me. But it wants to *remove* libgd2-noxpm, and wants to newly install libgd2-xpm. It looks like this plan is okay, so I'm running the upgrade now. I'll let you know how it worked after I reboot and try it out for a while.

---

### Post by psyke83 on 2009-10-10
> **popejeremy said:**
> I looked at what you suggest, and fired up Synaptic set for Smart Update. Synaptic wants to upgrade the kernel and ubuntu-netbook-remix, which looks good to me. But it wants to *remove* libgd2-noxpm, and wants to newly install libgd2-xpm. It looks like this plan is okay, so I'm running the upgrade now. I'll let you know how it worked after I reboot and try it out for a while.

This is a perfect example of a situation in which a partial upgrade is both necessary and safe.

---

### Post by andrewabc on 2009-10-10
> **popejeremy said:**
> I was told on this forum a while ago to use apt-get to upgrade, and that it's O.K. to do so as long as no packages are being removed, even if some packages are being held back.

But now the kernel and ubuntu-netbook-remix have been held back for a week or more. Did I do it wrong? Or do I just need to keep waiting?

What packages are going to be removed? Is there similar named packages that are new that want to be installed?

---

### Post by popejeremy on 2009-10-10
> **popejeremy said:**
> I looked at what you suggest, and fired up Synaptic set for Smart Update. Synaptic wants to upgrade the kernel and ubuntu-netbook-remix, which looks good to me. But it wants to *remove* libgd2-noxpm, and wants to newly install libgd2-xpm. It looks like this plan is okay, so I'm running the upgrade now. I'll let you know how it worked after I reboot and try it out for a while.

Everything seems to work!

---

### Post by ranch hand on 2009-10-10
I like the new kernal too.  Things look to be coming together.

---

### Post by ikisham on 2009-10-11
We hear from sidux that we should 'never' upgrade from inside the X environment. Of course Ubuntu's Update Manager takes care of this...if it's a stable release.
I would recommend to update from outside X (ctrl+alt+f1). In Karmic the Gnome environment is proned to tantrums during system upgrades.

---

### Post by VMC on 2009-10-11
> **ikisham said:**
> We hear from sidux that we should 'never' upgrade from inside the X environment. Of course Ubuntu's Update Manager takes care of this...if it's a stable release.
I would recommend to update from outside X (ctrl+alt+f1). In Karmic the Gnome environment is proned to tantrums during system upgrades.

That's probably due to the fact most sidux users use that "smxi" script.

---

### Post by kansasnoob on 2009-10-13
Regarding the closing of my new thread:

[http://ubuntuforums.org/showthread.php?t=1290557](http://ubuntuforums.org/showthread.php?t=1290557)

I'm sure everyone reads all the sticky notes:P

We'll see!

I see no harm in incremental warnings by those who are involved in testing.

I think that was a bit rude!

---

### Post by 23meg on 2009-10-13
> **kansasnoob]Regarding the closing of my new thread:

[http://ubuntuforums.org/showthread.php?t=1290557](http://ubuntuforums.org/showthread.php?t=1290557)

I'm sure everyone reads all the sticky notes:P

We'll see![/QUOTE]

I'm not so sure either said:**
> I did voice my skepticism[/URL] before starting this thread. It's indeed largely a "We'll see" experiment. But...

[QUOTE=kansasnoob]I see no harm in incremental warnings by those who are involved in testing. 

I think that was a bit rude!


You could have posted that update to this thread, instead of starting a new one. Multiple threads on the exact same subject just waste space and increase noise. 

Also note that there's no way to tell whether "there's a partial upgrade now", since people will be using different mirrors and updating at different times, thus issuing repetetive warnings will only be marginally useful. If people are unsure whether to go ahead with an update, they can ask.

In the future, if you have an issue with moderation, please post to the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123").

---

### Post by lovinglinux on 2009-10-14
Thanks for the info.

I did a partial upgrade just after installing the Beta, which removed **libgd2-noxpm** and installed **libgd2-xpm**. 

After checking Synaptic history, I realized these might also be due to a partial upgrade:

**libpostproc51** replaced with **libpostproc-extra-51**

There are also the package **guile-1.8-libs**. I don't know if should be in the default installation or not. It seems to be added by a partial upgrade, but does not have any dependency when I mark it for removal.

Any info on these packages?

---

### Post by kansasnoob on 2009-10-14
> **23meg said:**
> I'm not so sure either; [I did voice my skepticism]("http://ubuntuforums.org/showpost.php?p=8051755&postcount=30") before starting this thread. It's indeed largely a "We'll see" experiment. But...



You could have posted that update to this thread, instead of starting a new one. Multiple threads on the exact same subject just waste space and increase noise. 

Also note that there's no way to tell whether "there's a partial upgrade now", since people will be using different mirrors and updating at different times, thus issuing repetetive warnings will only be marginally useful. If people are unsure whether to go ahead with an update, they can ask.

In the future, if you have an issue with moderation, please post to the [Resolution Center]("http://ubuntuforums.org/forumdisplay.php?f=123").

Well, in hind site (why is hind site always 20/20?) you were right and I was wrong.

Please accept my aplogies:redface:

---

### Post by 23meg on 2009-10-14
> **lovinglinux said:**
> Thanks for the info.

I did a partial upgrade just after installing the Beta, which removed **libgd2-noxpm** and installed **libgd2-xpm**. 

After checking Synaptic history, I realized these might also be due to a partial upgrade:

**libpostproc51** replaced with **libpostproc-extra-51**

Those are examples of cases when you *need* a "Partial Upgrade" (if you're using Update Manager, that is), since a package is being replaced with a new one.

> **lovinglinux]There are also the package **guile-1.8-libs**. I don't know if should be in the default installation or not. It seems to be added by a partial upgrade, but does not have any dependency when I mark it for removal.

Any info on these packages?[/QUOTE]

Have you purposefully removed the default GNOME games? That package is pulled in by Aisleriot.

[QUOTE=kansasnoob said:**
> Well, in hind site (why is hind site always 20/20?) you were right and I was wrong.

Please accept my aplogies:redface:

No worries :)

---

### Post by lovinglinux on 2009-10-14
> **23meg said:**
> Have you purposefully removed the default GNOME games? That package is pulled in by Aisleriot.

Yep, that clarifies it. I did remove gnome games. Thanks.

---

### Post by aimwin on 2009-10-16
> **23meg said:**
> After the release of Ubuntu 9.10 Beta, we've been flooded with threads asking for assistance related to issues caused by careless usage of the "Partial Upgrade" feature of Update Manager. This document aims to clarify what a "Partial Upgrade" is, and why, **in most cases, you'll want to avoid it**.


Dear all the Guru_s

Please remove the "Partial Upgrade" from the Update Manager, or please add the above message to the "Partial Upgrade" message in the Update Manager in the Ubuntu 9.10.

It is too late for me when I saw this above message, I did the mess up to my Ubuntu 9.10 beta already with the Partial Upgrade and now, I cannot update anything anymore, not even reinstall ubuntu from with in package manager or I don't know how?

I had.
E: The package linux-image-2.6.31-13-generic needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

9.04 is verygood, 9.10 beta is the worst of all version I have tested.
I mean gave me the worst experience with ubuntu because of this issue.

I don't care what is the advantage of the Partial Upgrade, but the old package manager from 8.04 till 9.04 never have this mess.

Remove it please or make it the old way or what ever ways??????\\\\\

or make it an option in the package manager and don't enable it by default.

And let the advance user enable that function if they want to do that.
All the newbies like me and many other new user who want to try, majority of them will answer yes to partial upgrade.
Since always UBUNTU 'S defualt options are good.

Who would know that it must answer NO.
And if it must answer NO, why it should be there in the first place. 

I waste 8 hours to solve the problems, only lucky now that I found this "thread".

I wish "23meg" can put his post underneath the "Partial Upgrade" in the Package manager.

Please do it as the old 8.04 till 9.04

Thanks
UBUNTU SUPPORTER

---

### Post by aimwin on 2009-10-16
I have to reinstall 9.10beta now for the 4th times, after

1. Crashed and never start up successfully after I upgrade to Nvidia Hardware driver.

2. Hang up at the start after spending install so many packages and update automatically.

3. Cannot update anything anymore, but other functions are perfect so far.

I will try the 4th and it will be the last for 9.10 beta.

I wish I am not a 9.10 beta, it is the worst of all my bad experience with ubuntu.

I hope those "want to try ubuntu" user will not get to this package.

Why?

For me I use Ubuntu instead of Fedora and others, because I found in the older package 8.04-9.04, the package manager are the best, and the most reliable.

Now not any more.

I am about to launch a new website promoting ubuntu in Thailand.

I am thinking twice and will now wait to see if this feature is going to be in 9.10.

If it is in there, I will delay the promotion of 9.10 and will "curse the 9.10 version" for make ubuntu the worse package of all present day linux.

Very Frustrating and Down.

---

### Post by VMC on 2009-10-16
aimwim, I understand your frustrations. That reason alone is why I don't use update manager and instead use aptitude and have **never** had any problems. I started with alpha 3 and I am current as of today. Never an issue.

I agree. Something needs to be done in this area. Hopefully your words will not fall on deaf ears. I don't know if filling a bug report or if it has already be done would help.

Please don't give up on karmic. For me and a lot of others, it's just the best.

---

### Post by lovinglinux on 2009-10-16
> **aimwin said:**
> Dear all the Guru_s

Please remove the "Partial Upgrade" from the Update Manager, or please add the above message to the "Partial Upgrade" message in the Update Manager in the Ubuntu 9.10.

Developers do not track this forum. If you want to report a bug go to [Launchpad](https://bugs.launchpad.net/ubuntu/). If you want to suggest changes or new features, go to [Ubuntu Brainstorm](http://brainstorm.ubuntu.com/).

> **aimwin said:**
> 
It is too late for me when I saw this above message, I did the mess up to my Ubuntu 9.10 beta already with the Partial Upgrade and now, I cannot update anything anymore, not even reinstall ubuntu from with in package manager or I don't know how?

9.04 is verygood, 9.10 beta is the worst of all version I have tested.
I mean gave me the worst experience with ubuntu because of this issue.

That's what happens when new users install a distro under development on a production environment. IT IS A BETA! Bugs are expected and updates can and most likely will break your system. Ubuntu 9.04 is a stable release that has been released for a while, so you can't compare it with the first Beta of a new release in terms of stability.

So, you are not supposed to use it if you depend on stability. The Beta is available for TESTING, so people can report the bugs and help improve it.

> **aimwin said:**
> And let the advance user enable that function if they want to do that. All the newbies like me and many other new user who want to try, majority of them will answer yes to partial upgrade.

If you don't have experience with package management and beta testing, you shouldn't be installing a Beta release or shouldn't be complaining about it the way you are doing. No one forced you to install it or forced it through Jaunty update manager.

> **aimwin said:**
> I have to reinstall 9.10beta now for the 4th times, after

1. Crashed and never start up successfully after I upgrade to Nvidia Hardware driver.

2. Hang up at the start after spending install so many packages and update automatically.

3. Cannot update anything anymore, but other functions are perfect so far.

I will try the 4th and it will be the last for 9.10 beta.

I wish I am not a 9.10 beta, it is the worst of all my bad experience with ubuntu.

I hope those "want to try ubuntu" user will not get to this package.

Why?

For me I use Ubuntu instead of Fedora and others, because I found in the older package 8.04-9.04, the package manager are the best, and the most reliable.

Now not any more.

I am about to launch a new website promoting ubuntu in Thailand.

I am thinking twice and will now wait to see if this feature is going to be in 9.10.

If it is in there, I will delay the promotion of 9.10 and will "curse the 9.10 version" for make ubuntu the worse package of all present day linux.

Very Frustrating and Down.

OMG. Please stop whining. Do yourself a favor and install final releases only. 

Karmic Koala is the best version a have used so far and since I started to use Ubuntu it has been getting better and better. Of course there are such bugs you have described and have suffered with them myself, but I was fully aware that it could happen when I installed the Beta release.

BTW, "Partial Upgrades" has always been there, they are just not common for final and stable releases.

---

### Post by aimwin on 2009-10-16
Thanks for comments, I will goto lunch pad and brain storm.

The purpose is to respond that there are problems, and that are the reasons we help testing.

I made this complains be cause I found more problems than previous versions.
And I hope I would contribute to the improvement of Ubuntu.

But may be I use a too yelling complain, I hope you all understand, that just to show the level of the problems. So who ever responsible can compare the response if the problems are mild or strong or very important matter regarding the users' point of view.

Thanks again.

---

### Post by aimwin on 2009-10-16
> **lovinglinux said:**
> Developers do not track this forum. If you want to report a bug go to [Launchpad](https://bugs.launchpad.net/ubuntu/). If you want to suggest changes or new features, go to [Ubuntu Brainstorm](http://brainstorm.ubuntu.com/).
-----------------------------------------------
--------------------------

BTW, "Partial Upgrades" has always been there, they are just not common for final and stable releases.

Are you saying that in the Final and the Stable Release, they won't put this feature, Partial Upgrades, as a default function?

But certainly the 8.10 beta and 9.04 beta had no problems like 9.10 beta.

Anyway I think for my experience I have more problems with 9.10 beta more than the previous version.

But I will do what VMC said I will try to use command line only for the time being.

Thanks

---

### Post by lovinglinux on 2009-10-16
> **aimwin said:**
> Are you saying that in the Final and the Stable Release, they won't put this feature, Partial Upgrades, as a default function?

No, what I'm saying is that the Partial Upgrade requests are probably less common on a final release and usually required. The thing with the Beta version is that it is under heavy development, so Partial Upgrades are more frequent and sometimes should not be applied, as already explained by the OP.

---

### Post by aimwin on 2009-10-16
> **lovinglinux said:**
> No, what I'm saying is that the Partial Upgrade requests are probably less common on a final release and usually required. The thing with the Beta version is that it is under heavy development, so Partial Upgrades are more frequent and sometimes should not be applied, as already explained by the OP.


Then my comment will be valid that the warning of 23meg's message, at the beginning of this thread, should accompanied the "Partial Upgrade Message" then.

I cannot file the bug report at lunchpad nor Brainstorm.
I spend an hour already, I hope someone from there got my complain so they would compile with other complains so they can judge better of what they should do.

Thanks everyone.

---

### Post by lovinglinux on 2009-10-16
> **aimwin said:**
> Then my comment will be valid that the warning of 23meg's message, at the beginning of this thread, should accompanied the "Partial Upgrade Message" then.

I cannot file the bug report at lunchpad nor Brainstorm.
I spend an hour already, I hope someone from there got my complain so they would compile with other complains so they can judge better of what they should do.

Thanks everyone.

Yes, your suggestion is valid, I never said it wasn't.

---

### Post by 23meg on 2009-10-16
> **lovinglinux said:**
> No, what I'm saying is that the Partial Upgrade requests are probably less common on a final release and usually required. The thing with the Beta version is that it is under heavy development, so Partial Upgrades are more frequent and sometimes should not be applied, as already explained by the OP.

As long as you don't have broken packages, Update Manager will *never* offer a Partial Upgrade in a stable release, so it's a non-issue.

---

### Post by manfer on 2009-10-17
> **23meg said:**
> This causes package management tools such as Update Manager, which are mainly meant to be used with stable releases of Ubuntu where the package archive is always consistent,

Thanks for all the thread and the good explanation. And just this text I quote is what I most wanted to know.

There is only one thing I'm cuious about and would like to have even better clear. Why it is possible to make it consistent during release lifetime and not during development?

---

### Post by aimwin on 2009-10-18
Dear Guru_s

1. I would like to edit my previous posts, since I understood "Partial Upgrade" to a large extent now. So to make the post more beneficial to Newbies like me and less "whining" but still represent the serious of the weakness of information display in the "Testing Version" for Normal User like me.

Can I or should I try to edit them?

2. The current message of Partial Upgrading.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=132301&stc=1&d=1255866167[/IMG]

3. my suggested new message.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=132300&stc=1&d=1255866167[/IMG]

[COLOR="Red"][B]Not all update can be install.

Do not run Partial Upgrade if you are not a developer team or an advance ubuntu tester.
Because Partial Upgrade could result in destruction of your current Ubuntu, 
and at certain conditions could result even in lost of data in your hardisks 
(even they are in other partitions).

You should instead use "aptitude"
sudo apt-get update followed by sudo apt-get upgrade ??[/B][/COLOR]


???? I don't fully understand the alternative to Update Manager 
and what VMC wrote "I don't use update manager and instead use **_[COLOR="Red"]aptitude[/COLOR]_**????

4. My question ==(after read all the posts and "learning the basics of using development releases is a prerequisite for doing useful testing,
@ the [https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases](https://wiki.ubuntu.com/UbuntuDevelopment/UsingDevelopmentReleases))

still is

What should a normal user like me do?
when I want to help testing, but also would like to upgrade or update the installed Ubuntu.

I don't really understand "aptitude" that VMC said.

I reinstall 9.10 beta already but cannot decide how to update,
since I got the Partial Upgrade message immediatly after flesh installation and click on update manager.

Thanks in advance again[ATTACH]132286[/ATTACH]

---

### Post by the.lost.one on 2009-10-18
Is partial UPDATE the same as partial UPGRADE? It shouldn't be.

I installed Karmic beta directly through a Karmic beta DVD. When I click on Update Manager, it says not all updates can be installed and give an option for partial UPDATE.

I had previously upgraded my Jaunty to Karmic beta (on another machine) and it offered partial UPGRADE. That I understand one shouldn't do in most cases.

But what about partial UPDATE? How do I update my Karmic beta if its offering me partial updates?

---

### Post by the.lost.one on 2009-10-18
Ok. I just did a **sudo apt-get update** followed by **sudo apt-get upgrade**.

It showed no packages would be removed and some 451 to be upgraded. Thats fine I suppose?

---

### Post by manfer on 2009-10-18
> **manfer said:**
> Thanks for all the thread and the good explanation. And just this text I quote is what I most wanted to know.

There is only one thing I'm cuious about and would like to have even better clear. Why it is possible to make it consistent during release lifetime and not during development?

I still would like an explanation, an answer to that question if possible.

And would like to point something else. People can decide to test an ubuntu release and even have no idea of the existence of ubuntu forums, so do you think a sticky on forums is enough? to say "DON'T DO PARTIAL UPGRADES", I'm going to exagerate a little, "YOU STUPID NEWBIE TESTING, DON'T LET US AND YOU WASTE TIME. READ STICKIES. NEVER DO PARTIAL UPGRADES" (I know this is done nowhere so rude, the ubuntu community is always there to help).

I repeat, a person can start testing ubuntu and don't know anything about ubuntu forums (they read an article on a blog and decide to test, a friend recomends them ubuntu, ....). And many many more now during BETA realease because even ubuntu home page is suggesting it and with a very very big ad: "Ubuntu 9.10 coming soon! can't wait? Download the beta now. Test it and give us your feedback to make an even better release" (and the only warning it has is "don't use in production environments", I don't see any don't do partial upgrades warning, do you think people are going to magically know about ubuntu forums and read stickies before testing?).

So I think it is a big big big mistake the way update manager works during development suggesting partial upgrades that (at first) noone have to magically know are not safe (at least me had the idea I could trust on the update system till I get into trouble and learned I couldnt). I think it is a big big mistake that people can't trust in the OS update system.

And when I learned I could not trust on update manager, the first thing comming to my mind was "wow, and is this the same during release lifetime? I'm not going to trust update manager anymore". And my perception of how good was Ubuntu as OS went into a spin.

Now, at least, I'm glad to hear during release lifetime you can trust because:
> 
The package archive is always consistent.
As long as you don't have broken packages, Update Manager will never offer a Partial Upgrade in a stable release, so it's a non-issue.


But still I think it is a big big mistake that during development it is not and a big big mistake an OS update system giving wrong suggestions during development.

Just to finish and in my modest opinion **the update system is one critical piece of an OS and should be always reliable**.

---

### Post by manfer on 2009-10-18
And I was forgeting, I totally agree with **aimwin** you only have to look at the partial upgrade warning.

Which button you think someone only involved on testing and not development is going to press with such a message? A warning that starts, "Run partial upgrade...". Of course, until for some reason they realize it is not safe (or they just know), they are going to run it thinking one of the listed causes is happening to him because an OS update system is supposed to be reliable. It can solve bugs and introduce others of course, nothing is perfect, but an OS update system breaking the system?, :-\" :-\"

---

### Post by sameer.india on 2009-10-18
i'm using karmic beta
update-manager asks for partial upgrade
dist-upgrade asks for removal of libgd2-noxpm and rtkit
i can't understand the changelog
should i go ahead

---

### Post by luvr on 2009-10-18
> **sameer.india said:**
> dist-upgrade asks for removal of libgd2-noxpm and rtkit

When I got the *"Partial Upgrade"* warning, suggesting the removal of **libgd2-noxpm** and another package (don't remember if that was **rtkit,** actually), I let the *Update Manager* install the partial upgrade. Afterwards, there remained two updates awaiting installation, and I installed these, too. Everything has been fine ever since.

It seems that *libgd2-noxpm* got removed, and replaced by *libgd2-xpm* or some such, and this operation had to be postponed until the other updates were installed. Should likely have been possible to do in one operation (the update manager could have figured out that it had to install the two troublesome updates last, and that doing so would have allowed it to do a *full* upgrade), but something apparently made the system refuse to do so. I have no idea whether the package managing software supports (or is even *supposed* to support) this type of manipulation, though.

---

### Post by stevetxt on 2009-10-18
Based on this report
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/406702](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/406702)
it appears removing rtkit with today's upgrades to pulseaudio related packages is the right way to go.

---

### Post by sameer.india on 2009-10-18
thanks

---

### Post by linusr on 2009-10-18
> **stevetxt said:**
> Based on this report
[https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/406702](https://bugs.edge.launchpad.net/ubuntu/+source/linux/+bug/406702)
it appears removing rtkit with today's upgrades to pulseaudio related packages is the right way to go.

missed out this thread..

but after partial upgrade things were working fine though

---

### Post by jatinps on 2009-10-19
looking at this thread I am going to go ahead then - fingers crossed :)
pulse audio packages are greyed out

---

### Post by todak on 2009-10-19
> **ranch hand said:**
> I would use synaptic, making sure that the default setting is for "Smart Update" (or smart upgrade, can't remember).  This is not as safe as apt-get but close.

You probably have a bunch more updates that are not coming to you because of the lack of the new kernal (31-13.43).

Per the synaptic help documentation: 

> **3.4. To Upgrade the Whole System**
 
Synaptic Package Manager provides two methods for marking packages for upgrade:
 
 **Default Upgrade** The default upgrade method marks upgrades of installed packages only. If the later version of a package depends on not installed packages or conflicts with an already installed package, the upgrade will not be marked.
 
 **Smart Upgrade (Dist-Upgrade)** The smart upgrade method tries to resolve package conflicts intelligently. This includes installing additional required packages and preferring packages with higher priority. Smart upgrade is also known as dist-upgrade in the console tool apt-get. 

---

### Post by aimwin on 2009-10-19
> **manfer said:**
> I still would like an explanation, an answer to that question if possible.

-------------

I repeat, a person can start testing ubuntu and don't know anything about ubuntu forums (they read an article on a blog and decide to test, a friend recomends them ubuntu, ....). And many many more now during BETA realease because even ubuntu home page is suggesting it and with a very very big ad: "Ubuntu 9.10 coming soon! can't wait? Download the beta now. Test it and give us your feedback to make an even better release" 

(and the only warning it has is "don't use in production environments",

I don't see any [COLOR="Red"]don't do partial upgrades warning,[/COLOR] do you think people are going to magically know about ubuntu forums and read stickies before testing?).

So I think it is a big big big mistake the way update manager works during development suggesting partial upgrades .........

Just to finish and in my modest opinion **the update system is one critical piece of an OS and should be always reliable**.

That problems bring me here and my earlier posts. 
And also the result in other posts such as "by bamboomy"
[http://ubuntuforums.org/showthread.php?t=1293294&page=2](http://ubuntuforums.org/showthread.php?t=1293294&page=2)

I hope it won't be too hard for the guru_s have 2 different versions of messages.

1. for the developing OS and
2. for the released OS.

Put up a nice Graphic with the words,

[COLOR="Red"][SIZE="4"][B]This is testing Version of Ubuntu that contains many bugs,
Do not use this if you are not advance user.[/B][/SIZE]

Do not run Partial Upgrade if you are not a developer team or an advance ubuntu tester.
Because Partial Upgrade could result in destruction of your current Ubuntu,
and at certain conditions could result even in lost of data in your hardisks
(even they are in other partitions).[/COLOR]

I do support "manfer" details, And we should help the Guru_s pushing the ideas to the developing teams.

Then "The Guru_s" don't have to spend their valuable time on "The Unnecessary Technical Issues".

---

### Post by aimwin on 2009-10-19
Dear 23meg:

What should normal users do if they want to up date the "beta" while they help testing? So they would not wreck the installed OS and help reflecting the bugs on their system better.

Thanks in Advance for your time.

---

### Post by 23meg on 2009-10-19
> **aimwin said:**
> Dear 23meg:

What should normal users do if they want to up date the "beta" while they help testing? So they would not wreck the installed OS and help reflecting the bugs on their system better.

Thanks in Advance for your time.

They should read the first post of this thread, and/or the wiki page linked to in that post.

---

### Post by manfer on 2009-10-19
> **23meg said:**
> They should read the first post of this thread, and/or the wiki page linked to in that post.

[LIST]
[*]A user knows nothing about ubuntu forums.
[*]That user has read articles about ubuntu.
[*]That user goes to ubuntu home page.
[*]That user finds an ad there to test a beta release.
[*]That user downloads the beta release.
[*]That user installs beta release.
[*]That user in his testing decide to run System->Admin->Update manager.
[*]That user is presented with a message that suggest a Partial Upgrade is needed, Run Partial Upgrade... bla bla bla... for one of this causes... bla bla bla.
[*]That user accepts the partial upgrade.
[*]Unluckily that was not a secure upgrade and the user system is broken.
[/LIST]

No problem, he would sure find another computer or just probably another OS or ubuntu version on other partition, do a www research, maybe find ubuntu forums and his first contact with it, maybe he will find karmic release forum, then maybe he would notice the stikies, then maybe he starts to read, then maybe he would learn for the next time.

Or most probable he would have a very very very poor concept about ubuntu.

And that's not my case, but it is a probable situation.

But if you think there is nothing wrong and the lot of messages in karmic forum because of a bad use of partial upgrade is testers fault, well, I have nothing to say, everyone can has his own opinion.

Mine as I mentioned before, is: that is a mistake.

---

### Post by snkiz on 2009-10-19
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=132301&stc=1&d=1255866167[/IMG]

As you pointed out. The reasons for a partial upgrade are clearly marked. I agree maybe a note that it is possible the repos are being updated, and that can cause breakage. Recommend you try again in an hour. But your suggest the devs hold your hand? during a beta?? You want everything to be rewritten to scare people into reading the cautionary notes, whats that going to say about Ubuntu? If people can't be bothered to read the information right in front of them. I'd say they should stay away form computers entirely, for their own safety.

---

### Post by andrewabc on 2009-10-19
My extremely small ISP has keyword "exchange" blocked.
I cannot update libexchange and evolutionexchange.
Can I go ahead with updates ignoring those two and stuff will work? I don't use evolution. Computer 95% used for firefox.

Before people start attacking the ISP they have been the only high speed isp in my area for 7 years, and it is wirelessly over 10km distance. Landline high speed should be here soon.

---

### Post by manfer on 2009-10-19
And what an user could think reading that update manager message is:

[LIST]
[*]I think a OS update system is reliable.
[*]It is suggesting me **RUN** partial upgrade, to install as many updates as possible. Causes: blablabla.
[*]One of those causes must be happening to me.
[*]Hit button Partial Upgrade.
[/LIST]

But if you think the message is self explanatory so it is not going to happen, ok, it is your oppinion. Even someone could start to analize the causes, when he reach the last one: "Normal changes of a pre-release..." and being over-confident of and update system, it has a lot of possibilities to hit accept.

My opinion is it has happened so many times that it all points that is not a correct message.

> I'd say they should stay away form computers entirely, for their own safety

And what I would say is that it is not very probable the user stay away from computer, but probable away from ubuntu.

**The OS is the most important piece of sotfware of a computer and it is the one which has to provide the most safety to the user. Is not the user who has to safe the OS.**

---

### Post by luvr on 2009-10-19
> **manfer said:**
> even ubuntu home page is suggesting it and with a very very big ad: "Ubuntu 9.10 coming soon! can't wait? Download the beta now. Test it and give us your feedback to make an even better release" (and the only warning it has is "don't use in production environments").

I think you're right here: A new user coming to the Ubuntu home page finds the **"Download the beta now"** message, and almost automatically gets directed to that--instead of the *(supposedly)* stable 9.04. Doesn't sound like such a great idea to me...

---

### Post by VMC on 2009-10-19
> **manfer said:**
> And what an user could think reading that update manager message is:

[LIST]
[*]I think a OS update system is reliable.
[*]It is suggesting me **RUN** partial upgrade, to install as many updates as possible. Causes: blablabla.
[*]One of those causes must be happening to me.
[*]Hit button Partial Upgrade.
[/LIST]

But if you think the message is self explanatory so it is not going to happen, ok, it is your oppinion. Even someone could start to analize the causes, when he reach the last one: "Normal changes of a pre-release..." and being over-confident of and update system, it has a lot of possibilities to hit accept.

My opinion is it has happened so many times that it all points that is not a correct message.
Good point! It's self-explanatory to those of us that "know" better. To someone coming from Windows and the like, we need a bigger hammer, like:
 [COLOR="Red"]**[SIZE="3"]STOP or WARNING: before doing "Partial Upgrade", Read this !!![/SIZE]**[/COLOR]


> **manfer said:**
> And what I would say is that it is not very probable the user stay away from computer, but probable away from ubuntu.Then again, what brought them to Ubuntu in the first place. Curiosity or unsatisfied with Windows.

---

### Post by arpanaut on 2009-10-19
While I can empathize with users who are bitten by this quirk of the development process, and I understand the concerns of manfer and others and maybe the wording of the warning on the popup needs to be stronger. 

I think the problem runs deeper... It used to be that "alpha", "beta" and even "release canidate"  offers automatically meant CAUTION,BEWARE, This software has a high likelyhood of not working properly and may hose your system. 

Now with the ubiquity of the internet and so many people have access to this kind of developmental stuff, people are less cautious, and willy-nilly install things that may be beyond their ability to recover from, and quite honestly I have little sympathy for those who install "alpha" or "beta" software on their production/ everyday machine then have problems.  

Especially if they have not taken the time to research what is going on, and taken measures to back-up their data, and ensure that they have an "escape plan" should things go badly.

Personally, the first time I saw a partial update/upgrade, my first reaction was "I don't think so!" CANCEL, and went to find out what was going on, did some research and learned that patience was indded a virtue. My experiences with Windows had taught me long ago to not trust their default options, and to do some research BEFORE I just willy-nilly went ahead with things I was not sure of.  Maybe that's just me and what my experience has taught me...

But then again some of the best lessons I have learned have been the hard way, and tend to be not forgotten.

I've got Windows on it's own hard drive, I've got stable installs of both Hardy and Jaunty on another drive and I'm testing Karmic on it's own separade drive, my data backed up on a fourth, and Images of the first three backed up on an external. That's just the way I roll...I can test all the development stuff I want, my back is covered.  

And now that I've shot off my mouth, I think I'll be off to do some incremental back-ups 'cause you know...

Later

---

### Post by ranch hand on 2009-10-19
> **manfer said:**
> 
[LIST]
[*]A user knows nothing about ubuntu forums.
[*]That user has read articles about ubuntu.
[*]That user goes to ubuntu home page.
[*]That user finds an ad there to test a beta release.
[*]That user downloads the beta release.
[*]That user installs beta release.
[*]That user in his testing decide to run System->Admin->Update manager.
[*]That user is presented with a message that suggest a Partial Upgrade is needed, Run Partial Upgrade... bla bla bla... for one of this causes... bla bla bla.
[*]That user accepts the partial upgrade.
[*]Unluckily that was not a secure upgrade and the user system is broken.
[/LIST]

No problem, he would sure find another computer or just probably another OS or ubuntu version on other partition, do a www research, maybe find ubuntu forums and his first contact with it, maybe he will find karmic release forum, then maybe he would notice the stikies, then maybe he starts to read, then maybe he would learn for the next time.

Or most probable he would have a very very very poor concept about ubuntu.

And that's not my case, but it is a probable situation.

But if you think there is nothing wrong and the lot of messages in karmic forum because of a bad use of partial upgrade is testers fault, well, I have nothing to say, everyone can has his own opinion.

Mine as I mentioned before, is: that is a mistake.

A user that is installing ANY OS in the development stage should be doing extremely painstaking research before installing such a potentialy dangerous critter on his/her box.

That, to me, would include knowing the best sources of information (this is the offical voice of the Ubuntu community, listed on the Ubuntu home page), and more than the default way to update the system (Update Manager is a convenience gui, not a versatile tool), and, hopefully, be aware that in this case they are dealing with Linux (noted for powerful, versatile, CLI, tools).

I am a noob myself.  I see that you have been a member of this forum longer than I have.

I have trouble with the idea that some "user" (say myself when I got Ubuntu for the first time) is going to get a "testing" version of an unreleased OS.  I just do not see it as the least bit likely.

---

### Post by manfer on 2009-10-19
> **VMC said:**
> Good point! It's self-explanatory to those of us that "know" better. To someone coming from Windows and the like, we need a bigger hammer, like:
 [COLOR="Red"]**[SIZE="3"]STOP or WARNING: before doing "Partial Upgrade", Read this !!![/SIZE]**[/COLOR]


Then again, what brought them to Ubuntu in the first place. Curiosity or unsatisfied with Windows.

Sorry you are the only one mentioning Windows, just to clarify. And as ubuntu isn't, windows is not the only OS on the universe.

And even just to clarify I'm not one of those ones so much affected by a very very destructive partial upgrade. I only had some degradate, well a lot of degradate performance while testing this karmic beta, and lots of issues many more than on any previous development release I tested.

All is solved now, some more or least with new upgrades, some others with my own repair.

---

### Post by manfer on 2009-10-19
> **arpanaut said:**
> While I can empathize with users who are bitten by this quirk of the development process, and I understand the concerns of manfer and others and maybe the wording of the warning on the popup needs to be stronger. 

I think the problem runs deeper... It used to be that "alpha", "beta" and even "release canidate"  offers automatically meant CAUTION,BEWARE, This software has a high likelyhood of not working properly and may hose your system. 

Now with the ubiquity of the internet and so many people have access to this kind of developmental stuff, people are less cautious, and willy-nilly install things that may be beyond their ability to recover from, and quite honestly I have little sympathy for those who install "alpha" or "beta" software on their production/ everyday machine then have problems.  

Especially if they have not taken the time to research what is going on, and taken measures to back-up their data, and ensure that they have an "escape plan" should things go badly.

Personally, the first time I saw a partial update/upgrade, my first reaction was "I don't think so!" CANCEL, and went to find out what was going on, did some research and learned that patience was indded a virtue. My experiences with Windows had taught me long ago to not trust their default options, and to do some research BEFORE I just willy-nilly went ahead with things I was not sure of.  Maybe that's just me and what my experience has taught me...

But then again some of the best lessons I have learned have been the hard way, and tend to be not forgotten.

I've got Windows on it's own hard drive, I've got stable installs of both Hardy and Jaunty on another drive and I'm testing Karmic on it's own separade drive, my data backed up on a fourth, and Images of the first three backed up on an external. That's just the way I roll...I can test all the development stuff I want, my back is covered.  

And now that I've shot off my mouth, I think I'll be off to do some incremental back-ups 'cause you know...

Later

For sure you have to have precautions testing a beta. Things can go wrong and you are risking.

But I think that is not the question, the question is if that update manager message is self-explanatory. I can ensure you I'm not a new user to computers and I got into that problem not undertanding the message.


[LIST]
[*]I trust on an OS update system.
[*]The message, though a warning, shows causes that could make you think is correct and you are being affected.
[*]You accept the partial upgrade.
[/LIST]


If it is self-explanatory for some, it is obvious it is not for others. So it seems something is not correct. With that posibility of system destruction, all, and a say all or almost all people, should understand it with no doubt.

---

### Post by manfer on 2009-10-19
> **ranch hand said:**
> A user that is installing ANY OS in the development stage should be doing extremely painstaking research before installing such a potentialy dangerous critter on his/her box.

That, to me, would include knowing the best sources of information (this is the offical voice of the Ubuntu community, listed on the Ubuntu home page), and more than the default way to update the system (Update Manager is a convenience gui, not a versatile tool), and, hopefully, be aware that in this case they are dealing with Linux (noted for powerful, versatile, CLI, tools).

I am a noob myself.  I see that you have been a member of this forum longer than I have.

I have trouble with the idea that some "user" (say myself when I got Ubuntu for the first time) is going to get a "testing" version of an unreleased OS.  I just do not see it as the least bit likely.

Some people are more curious than others, and of course they are going to be less, but some will test.

Again that's not enough, at least for me, obvious reason to know ubuntu forums. And even not enough though they knew. Because they would look at ubuntu forums after they get affected not before.

And if the number of people affected (so finally the answers start to show you are tired of people complaints) and finally just including a sticky about the issue is not enough to indicate something is not totally correct. OK, no problem for me.

And just to warm you if you dont read the message. I don't know it is so or not but read. Maybe you know more to clarify. Please consult this message [http://ubuntuforums.org/showpost.php?p=8127414&postcount=57]("http://ubuntuforums.org/showpost.php?p=8127414&postcount=57") in this same thread. Maybe the synaptic way you are suggesting is not safe, it looks being a dist-upgrade too, which seems to be what needs to be avoided.

---

### Post by xigen on 2009-10-19
23Meg ... thank you.

I now see the error in my ways.

Unfortunately, I did exactly what you advise not to do and ran a partial upgade on my AMD64 Ubuntu 9.10 installation.  

Previously the upgrade (9.04-->9.10) worked just fine.  Now I get 3 minutes worth of use and then a kernel panic and complete system freeze.

How would you suggest I restore my system?
What commands can I run to help diagnose what to do next?

Chers,
MW

---

### Post by ranch hand on 2009-10-19
> **manfer said:**
> Some people are more curious than others, and of course they are going to be less, but some will test.

Again that's not enough, at least for me, obvious reason to know ubuntu forums. And even not enough though they know. Because they would look at ubuntu forums after they get affected not before.

And if the number of people affected (so finally the answers start to show you are tired of people complaints) and finally just including a sticky about the issue is not enough to indicate something is not totally correct. OK, no problem for me.

And just to warm you if you dont read the message. I don't know it is so or not but read. Maybe you know more to clarify. Please consult this message [http://ubuntuforums.org/showpost.php?p=8127414&postcount=57](http://ubuntuforums.org/showpost.php?p=8127414&postcount=57) in this same thread. Maybe the synaptic way you are suggesting is not safe, it looks being a dist-upgrade too, which seems to be what needs to be avoided.
Yup, I got that message.  I also know that synaptic will, with smart upgrade, install things that apt-get upgrade will not, but apt-get dist-upgrade will install things that synaptic (with smart upgrade) will not.

That is part of the reason for 12 variations of 9.10 on my test platforms.  So that I can try things on some and other things on others.  This way you find out how things really work in a development phase.

As far as Update Manager goes, doing any thing to it that is different in testing from what it will be in the final release is just silly.  We are here to test the thing, as it will be used.  As has been said many times this is not an issue with a stable release.  Most updates run through it in this testing cycle have been fine.

Many updates run other ways have been wrecks.  It is just the users of Update Manager that are complaining about the delivery system of the updates.  Kind of like killing the messenger.

---

### Post by ST.x on 2009-10-21
I just got a partial upgrade from update-manager for:
```
Remove gstreamer0.10-schroedinger
Install libkate1
Install libmimic0
Upgrade gstreamer0.10-plugins-bad
Upgrade software-center
```

Anyone get similar ones?

---

### Post by the.lost.one on 2009-10-21
[COLOR=Red]Update: The partial release did not break anything. I initially tested (simulated) the packages it was removing through sudo apt-get -s remove <package name> and it didnt show any errors so I proceeded.[/COLOR]
I get this. I am running Karmic beta.
                                 [B]The following packages will be REMOVED: 
   gstreamer0.10-schroedinger libgd2-noxpm rtkit [/B]



Here is the complete

                            ```
xxx@xxx-laptop:~$ sudo apt-get dist-upgrade  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 Calculating upgrade... Done  
 The following packages will be REMOVED: 
   gstreamer0.10-schroedinger libgd2-noxpm rtkit  
 The following NEW packages will be installed:  
   libdirac0c2a libgd2-xpm libkate1 libpst4 linux-headers-2.6.31-14  
   linux-headers-2.6.31-14-generic linux-image-2.6.31-14-generic  
   xserver-xorg-input-mouse xserver-xorg-input-vmmouse  
 The following packages will be upgraded:  
   evolution-plugins gstreamer0.10-plugins-bad libpulse-browse0  
   libpulse-mainloop-glib0 libpulse0 linux-generic linux-headers-generic  
   linux-image-generic pulseaudio pulseaudio-esound-compat  
   pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev  
   pulseaudio-module-x11 pulseaudio-utils ubuntu-desktop xserver-xorg-input-all  
 17 upgraded, 9 newly installed, 3 to remove and 0 not upgraded.  
 Need to get 42.5MB of archives.  
 After this operation, 174MB of additional disk space will be used.  
 Do you want to continue [Y/n]?  

```Normal apt get update and upgrade gives this:
                          ```
sudo apt-get upgrade  
 Reading package lists... Done  
 Building dependency tree        
 Reading state information... Done  
 The following packages have been kept back:  
   evolution-plugins gstreamer0.10-plugins-bad libpulse-browse0  
   libpulse-mainloop-glib0 libpulse0 linux-generic linux-headers-generic  
   linux-image-generic pulseaudio pulseaudio-esound-compat  
   pulseaudio-module-bluetooth pulseaudio-module-gconf pulseaudio-module-udev  
   pulseaudio-module-x11 pulseaudio-utils ubuntu-desktop xserver-xorg-input-all  
 0 upgraded, 0 newly installed, 0 to remove and 17 not upgraded.  
 
```Will this be a safe partial upgrade?

---

### Post by aimwin on 2009-10-21
Dear Guru_s and Developing Team.

I am still consider myself to be newbies, for Ubuntu.
and mid ability as computer user.
I threw away Linux in the bin every year. Until I found UBUNTU 8.04 beta.

I am about to start website promoting ubuntu. We are organising more support for UBUNTU in our country.

Ok I am for UBUNTU.

Why do I yell out?
Why another advance_computer user "bamboomy" whine out in the other thread I mentioned.?
Why manfer try to explain his point.

Because We love UBUNTU AND ubuntu & opensouce community.

We want more people to use UBUNTU and we want to tell them UBUNTU is better than other OS.

And we want them not to have negative views about Ubuntu.

Linux has been for years, belong to computer programers' and Guru_s' operating system. 

And Linux won all other OS to be the most stable OS in the world(2009).
That is why 95% of Top 500 supercomputers are using linux.

Until UBUNTU arrived, TO FIGHT THE DESKTOP AREANA.
Linux, now, has gone to be General Public.

Especially UBUNTU was based on user's requirement.
And that results on UBUNTU won the trust and popularity from the public,
including us over other older Linux Distro.

We are asking that UBUNTU promoting BETA on the website, for whom?

General public or advance user or for Computer Programers?

We are criticizing and make suggestion in the hope that we can contribute to the development of UBUNTU from the user point of view.

Not from the developer nor the Guru_s and advance users' point of views.

But we still respect and give our heart to all of those mentioned above.

We, as a user, found a "BUG".

Not a programming bug that give UBUNTU a clash.

But a "BUG" in the "message" that led user to clash their UBUNTU 
and would give bad names for UBUNTU.

Since mid users like us have crash our system.
But lucky we love Ubuntu so much and knows that the forum could help.

Unfortunately the most average users would not know that.
Even they know the existence of the forum. 
They probably wouldn't bother even to come for help.

We have many Millions more of users, how many come down here.

Ubuntu should not advertise for beta if it is so bad.
But the schedule is there to keep release beta.
And many user will be mid user like me, want to help testing.
And we need the crowd to test.
So we have to advertise beta, I support this.

And the last 3 beta were excellent, that fool me about this 9.10 beta.

A lot of new users even newer than me will try the beta.

If they tried,
 it is likely they would end up promoting the wrong side of the stories.

I hope our attempt to contribute to the development of UBUNTU will not get the negative feeling from the Guru_s and the development team.

I would like to emphasize that we found the "Bug" - message bug.
We do our best to report and push to remove the bugs.

Of course if we have enough support we would like to ask people to vote.

[COLOR="Red"]If we should have a better messages in many places in the BETA Version.?[/COLOR]

[COLOR="Red"]so it will improve the usability and reliability for normal user[/COLOR].
[COLOR="Blue"]
who would not even know how to come here for help.[/COLOR]

Since with the adequate warning we could solve majority of the problems.
And that would remove this Thread from sticky (just joking, no we still should have this sticky, even though if we successfully change the message to whatever the better one.)

Last but not least, 

I volunteer to sell UBUNTU for free to the public.

And my response is from the sales team. 
That is my STAND

We should provide easy to use product for customers (public).
And should do anything we can to reduce complication
of the after sale service.

And any misleading messages should be "Remove" or "Modify",
so customers (public) will be happier.

And I am fighting with Microsoft products which are very user friendly.
We must improve ours,
to beat them.

---

### Post by psyke83 on 2009-10-21
> **aimwin said:**
> Dear Guru_s and Developing Team.

<snip>

Come on. A new user will be presented with the [Release Notes]("http://www.ubuntu.com/testing/karmic/beta") before seeing the beta download link, which contains the warning:

> **Note: This is a beta release. Do not install it on production machines. The final stable version will be released on October 29th, 2009.**

If you want to evangelize Ubuntu or Linux, more power to you, but you should **never** encourage new users to try a development release, especially if you yourself seem not to have a lot of experience dealing with it.

Knowledge of Partial Upgrades happens to one of several prerequisites for testing a development release. Not all users are expected to have this knowledge, since the development release is not aimed at the widest possible audience (not until the release candidate, and ultimate release).

Partial Upgrades are not an issue in a stable release.

---

### Post by aimwin on 2009-10-21
> **23meg said:**
> They should read the first post of this thread, and/or the wiki page linked to in that post.

I tried VMC's aptitude got confused and stop use it.
I did not know and have not got time to read everything in the links.
But read through the thread, and now confused even more,

runch hand said 
.......... I also know that synaptic will, with smart upgrade, install things that apt-get upgrade will not, but apt-get dist-upgrade will install things that synaptic (with smart upgrade) will not.
.............

My synaptic is already set for smart upgrade, as defualt I think.

But the update manager still show partial update always.

I decide to do nothing at the moment.

---

### Post by aimwin on 2009-10-21
> **psyke83 said:**
> Come on. A new user will be presented with the [Release Notes]("http://www.ubuntu.com/testing/karmic/beta") before seeing the beta download link, which contains the warning:...

Is there anything wrong or bad image or negative toward Ubuntu if we put extra warning or more realistic details of partial update as we suggested.


FOR YOUR " If you want to evangelize Ubuntu or Linux, more power to you, but you should **never** encourage new users to try a development release, especially if you yourself seem not to have a lot of experience dealing with it."

I will definitely promoting and telling all standard users not to touch the not released version, for sure.

[COLOR="Red"][SIZE="5"]But the one who promoting the testing of the "beta" version is not me,
it is [www.ubuntu.com](www.ubuntu.com).[/SIZE][/COLOR]

That brought me here and that is why I suggest more and better warning.
So it will not upset our potential customers.

I would like to have more critics on this.

Can anyone express the negative results or image which will effect the promotion or the proposed warning of beta Ubuntu.?

I can see one.

It will discourage people help testing? 
 
Will that is true or not?

---

### Post by 23meg on 2009-10-21
> **aimwin said:**
> 
[COLOR="Red"][SIZE="5"]But the one who promoting the testing of the "beta" version is not me,
it is [www.ubuntu.com](www.ubuntu.com).[/SIZE][/COLOR]


With ample warning.

[www.ubuntu.com:](www.ubuntu.com:)

> We would like your help in testing and improving the pre-release version, but we don't yet recommend its use in production environments.

* click *  -> [http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta):

> **Note: This is a beta release. Do not install it on production machines. The final stable version will be released on October 29th, 2009.**

* click * -> [http://releases.ubuntu.com/releases/9.10/](http://releases.ubuntu.com/releases/9.10/):

> Ubuntu 9.10 (Karmic Koala) Beta

You also get a warning that this is not a stable version in the installer.

---

### Post by ranch hand on 2009-10-21
+1

---

### Post by aimwin on 2009-10-21
I have finally learn how to use Brain Storm.
And post the proposal there as "lovinglinux" told me to do.

I have post [http://brainstorm.ubuntu.com/idea/21976/](http://brainstorm.ubuntu.com/idea/21976/)

The point was not the problems of using beta for production.
(I have stable 2 more partitions of 9.04 Edubuntu on my notebook)

The point I try to get across is as i post there.

[I][COLOR="Blue"]I would like to propose a better warning for beta and even to alpha as well. 
If [www.ubuntu.com](www.ubuntu.com) is going to keep advertising beta testing on the home page.

or 
suggest to withdraw "beta testing" advertising from [WWW.UBUNTU.COM](WWW.UBUNTU.COM).

And let it advertise only in the forums homepage of all other sites 
which have more advance Ubuntu users interaction than the main General Public Pages"

Since it will produce negative image more than positive if it has a buggy beta. And with "not adequate warning" for "the Normal User"[/COLOR][/I]

It won't effect much if they were good as the previous beta versions.

But since we have this buggy "9.10 beta" we should learn from the lesson and not to repeat it.

It take too much time of the Guru_s who have to come and support the problems as well as we creating the negative image unnecessary.

And I am sorry to ask your(23meg) permission after I post there,
on copying your warning message that I think is very good, very valid, and it should be advertised along the beta or even alpha version.

If they just put only "all your words" there that will give me satisfactory to "one level too". And all "our" efforts are worth while.

Those who agree please support our proposal, 
(not mine only, since it came from many people, I just sum it up)
Please help support at
[http://brainstorm.ubuntu.com/idea/21976/](http://brainstorm.ubuntu.com/idea/21976/)

Thanks 23meg for starting the thread, and gave me the education and direction. 

and "lovinglinux", "VMC"and "manfer" for give me the courage to walk on.
I wish I can put "manfer" comments in the brainstorm thread as well.
But it would be better if "manfer" can do it "yourself".

I ask permission in advance if "manfer" did not come back here in due time, I would like to copy and post your comments at "brain storm" too.

Best Wish to everyone.

---

### Post by lovinglinux on 2009-10-21
> **aimwin said:**
> or 
suggest to withdraw "beta testing" advertising from [WWW.UBUNTU.COM](WWW.UBUNTU.COM).

And let it advertise only in the forums homepage of all other sites 
which have more advance Ubuntu users interaction than the main General Public Pages

I think that would be a better option. I was thinking about creating a new thread about this, since there are a lot of newcomers using the Beta version and posting about it on the Absolute Beginner Talk and General Help forum. IMO, Canonical shouldn't advertise Beta versions on Ubuntu home page, at least not with a huge banner.

---

### Post by ranch hand on 2009-10-21
In a free and open environment, it is not Ubuntus responcability to protect people from their own actions.

You can run Nautilus as root, you can stick -rm (DO NOT DO THIS) in every command in terminal, and you can, as a noob or long time user with no knowledge, install an alpha/beta on your production box.  All can certainly lead to disasster (-rm will).  You are welcome to do them though, it is your box.

If we are so worried about competing with OS' that do not give you freedom that we remove ours, that is also our fault.

This babysitter needed attitude toward users is insulting to them and looks (and feels) condicending coming from the vendor.  It is just a bad idea.

---

### Post by lovinglinux on 2009-10-21
> **ranch hand said:**
> In a free and open environment, it is not Ubuntus responcability to protect people from their own actions.

You can run Nautilus as root, you can stick -rm (DO NOT DO THIS) in every command in terminal, and you can, as a noob or long time user with no knowledge, install an alpha/beta on your production box.  All can certainly lead to disasster (-rm will).  You are welcome to do them though, it is your box.

If we are so worried about competing with OS' that do not give you freedom that we remove ours, that is also our fault.

This babysitter needed attitude toward users is insulting to them and looks (and feels) condicending coming from the vendor.  It is just a bad idea.

I agree, but why they publish such a huge banner about a Beta version on the front-page? That's an invite for newcomers to install it and I bet most of them will do on a production environment. Most people are already familiar with Beta Google web applications that doesn't offer real risks to their machines, but not every user is aware of the risks of installing an OS under beta stage. So when they see a Beta download on Ubuntu's home page they will probably trust it. I think that is ultimately bad for Ubuntu's image, because lot's of users will think the OS doesn't even work. 

I have just replied to another thread in the Desktop Environment forum regarding the nvidia driver issue, that makes Ubuntu unbootable.

---

### Post by VMC on 2009-10-21
> **ranch hand said:**
> In a free and open environment, it is not Ubuntus responcability to protect people from their own actions.

You can run Nautilus as root, you can stick -rm (DO NOT DO THIS) in every command in terminal, and you can, as a noob or long time user with no knowledge, install an alpha/beta on your production box.  All can certainly lead to disasster (-rm will).  You are welcome to do them though, it is your box.

If we are so worried about competing with OS' that do not give you freedom that we remove ours, that is also our fault.

This babysitter needed attitude toward users is insulting to them and looks (and feels) condicending coming from the vendor.  It is just a bad idea.AMEM to that!

I don't want Ubuntu to discourage anyone from testing the "testing" distros. The more the better, even if some poor inexperienced newby wonders in. It's their computer and their responsibility to read the [SIZE="1"]fine print[/SIZE]. 

The more testers, the more bugs to uncover. Not withstanding VM users, which really only check the installation process. And how many of them do we need. We need more hardware testers!

---

### Post by ranch hand on 2009-10-21
> **lovinglinux said:**
> I agree, but why they publish such a huge banner about a Beta version on the front-page? That's an invite for newcomers to install it and I bet most of them will do on a production environment. Most people are already familiar with Beta Google web applications that doesn't offer real risks to their machines, but not every user is aware of the risks of installing an OS under beta stage. So when they see a Beta download on Ubuntu's home page they will probably trust it. I think that is ultimately bad for Ubuntu's image, because lot's of users will think the OS doesn't even work. 

I have just replied to another thread in the Desktop Environment forum regarding the nvidia driver issue, that makes Ubuntu unbootable.
Then, as responcible members of the human race, they will learn to read all the information before they get in over their heads.

If they do not know enough to know what "beta" means, they should not be installing ANYTHING on their box and it is time they learned that.

I have, in spite of a number of posts to this forum back in ALPHA when the install process started wit han escape page stating nothing but a warning, a better opinion of people than you appear to.  I think that they can THINK.  I also think that it is a good trait to incourage.

The Ubuntu "image" is not going to be improved by baby sitting idiots.  There is already the perfect OS for them out there.  They should use it.  They probably are silly enough to trust it too.  Doesn't seem to hurt their image much.

---

### Post by MaindotC on 2009-10-21
> **ST.x said:**
> I just got a partial upgrade from update-manager for:
```
Remove gstreamer0.10-schroedinger
Install libkate1
Install libmimic0
Upgrade gstreamer0.10-plugins-bad
Upgrade software-center
```

Anyone get similar ones?

I got this.  Sorry I just woke up.  After doing the upgrade, it wanted to remove libmyth0 and libmysqlclient15off.  I followed through with the procedure and I didn't notice anything bad happening.

---

### Post by ranch hand on 2009-10-21
Just removing outmoded junk.

---

### Post by manfer on 2009-10-21
> **ranch hand said:**
> Then, as responcible members of the human race, they will learn to read all the information before they get in over their heads.

If they do not know enough to know what "beta" means, they should not be installing ANYTHING on their box and it is time they learned that.

I have, in spite of a number of posts to this forum back in ALPHA when the install process started wit han escape page stating nothing but a warning, a better opinion of people than you appear to.  I think that they can THINK.  I also think that it is a good trait to incourage.

The Ubuntu "image" is not going to be improved by baby sitting idiots.  There is already the perfect OS for them out there.  They should use it.  They probably are silly enough to trust it too.  Doesn't seem to hurt their image much.

You don't need to be disrespectful to anyone to give your opinion.

---

### Post by manfer on 2009-10-21
> **ranch hand said:**
> In a free and open environment, it is not Ubuntus responcability to protect people from their own actions.

You can run Nautilus as root, you can stick -rm (DO NOT DO THIS) in every command in terminal, and you can, as a noob or long time user with no knowledge, install an alpha/beta on your production box.  All can certainly lead to disasster (-rm will).  You are welcome to do them though, it is your box.

If we are so worried about competing with OS' that do not give you freedom that we remove ours, that is also our fault.

This babysitter needed attitude toward users is insulting to them and looks (and feels) condicending coming from the vendor.  It is just a bad idea.

The examples you gave about an incorrect use of nautilus as root or a CLI destroy command are very very far from the accidental bad use of the OS intagrated update system (update manager) because a misunderstood of how it must be used during development and misunderstood of its partial upgrade message.

---

### Post by flipper9 on 2009-10-21
Even though Ubuntu Karmic 9.10 is still currently "Beta", what's the difference between what it is today, and what it will be when it is released?  Very little.  There might be a show-stopper bug, but then none have showed up with the current crop of testers as of right now.  Whether that one person (or group) find the critical bug today, or when we arbitrarily call Ubuntu 9.10 released won't make any difference at this point.  You just have to accept the fact that there are bugs now and there will always be bugs.  At this point in the development cycle, Ubuntu 9.10 is pretty stable.  The label "beta" is just arbitrary.

This brings up the point that maybe we should change how we label alphas, betas, and release candidates.  I think we have too many alphas, the right amount of betas, and not enough release candidates.  There is really very little time where a "release candidate" is allowed to "bake"...just a matter of a couple of days.   I'd consider the current Beta of Ubuntu similar to a Release Candidate of Windows.

Besides, everyone knows it's risky to install any initial release of any software.  That's why many people wait for the "released" software to get some patches out there (or service packs) before they upgrade.

P.S.: I'm running Ubuntu Karmic 9.10 since the later Alphas on my production system, and am willing to deal with any issues.  It's my choice.

---

### Post by psyke83 on 2009-10-21
> **flipper9 said:**
> Even though Ubuntu Karmic 9.10 is still currently "Beta", what's the difference between what it is today, and what it will be when it is released?  Very little.  There might be a show-stopper bug, but then none have showed up with the current crop of testers as of right now.  Whether that one person (or group) find the critical bug today, or when we arbitrarily call Ubuntu 9.10 released won't make any difference at this point.  You just have to accept the fact that there are bugs now and there will always be bugs.  At this point in the development cycle, Ubuntu 9.10 is pretty stable.  The label "beta" is just arbitrary.

The label is not arbitrary at all.

Please read 23meg's post again. During the development process, unsafe Partial Upgrades are possible. After release, Partial Upgrade scenarios will be safe to perform (due to the [StableReleaseUpgrades]("https://wiki.ubuntu.com/StableReleaseUpdates") policy).

> This brings up the point that maybe we should change how we label alphas, betas, and release candidates.  I think we have too many alphas, the right amount of betas, and not enough release candidates.  There is really very little time where a "release candidate" is allowed to "bake"...just a matter of a couple of days.   I'd consider the current Beta of Ubuntu similar to a Release Candidate of Windows.

Microsoft butchered the meaning of Release Candidate. Release Candidate means that it is a candidate for release - if no show-stopping bugs are found, then the release candidate and final version will be bit-for-bit identical.

Microsoft's definition of Release Candidate is simply wrong.

> Besides, everyone knows it's risky to install any initial release of any software.  That's why many people wait for the "released" software to get some patches out there (or service packs) before they upgrade.

That kind of received wisdom applies more to Microsoft products than anything else. Case in point - Windows XP prior to Service Pack 2. Due to the fact that pre-SP2 XP did not ship with a firewall enabled, most users who were not behind NAT would see their computer infected by a trojan (MSBlast, if my memory serves me correctly) within minutes of being connected to the internet, causing their system to reboot before any security patches could download from Windows Update. Yes, this is not just anti-Microsoft FUD posted on the internet - it happened to me.

You don't need "service packs" for Ubuntu, or other Linux distributions. It's true that Ubuntu's LTS releases have point releases (such as 8.04.1), but that's more a matter of convenience (to avoid having to download all security updates after a fresh install).

---

### Post by flipper9 on 2009-10-21
True, Ubuntu does have definitions for alpha/beta/rc...but it really is all about user perception of the definitions.  We have people worried that Ubuntu is inviting regular users to "try out the Beta", but to me it really doesn't matter.  Google has corrupted, among others, the ideas of Betas, Microsoft has their own definition, Linux it's own, and so forth.  It all comes down to what has been allowed to "bake", with releases of service packs/patches/point releases/"call it what you will" (whatever you want to call them, doesn't matter except to the Linux-haters and the Microsoft-haters).   I see no difference between service packs, 6 month releases of Ubuntu with cute names (which I think are great), or whatever the developer of the software wishes to call their releases/updates.

IMHO all that really matters and is accepted by most people is the concept of Stable vs. Unstable.  Ubuntu has the LTR release, which to me is Stable, and the regular 6-month release cycle, which to me is Unstable.  I wish we could go back to that kind of labelling as it made sense.

So back to my point, it all comes down to testing.  The number of testers isn't going to go up until the software is released.  Then all of the many bugs will rise to the surface, and eventually get fixed.  It doesn't matter that it's labelled "whatever".  It just depends on what the user is comfortable with dealing with if their are issues.  I'm fine with people trying out the latest Beta as I think Karmic, at this point, is pretty stable for final release barring any major issues...that will get fixed.  And if those errors are not found, and they are there lurking, they'll get fixed later on with a patch/point release/update/service pack/"whatever your label du jour is".

---

### Post by VMC on 2009-10-21
That's why it's important to have more testers during each milestone. I blew it again and didn't participate. Next time hopefully, I'll be ready. The milestone testing is a barrage of several legs of tests run. I would think this is where we need the most support.

---

### Post by ranch hand on 2009-10-21
> **VMC said:**
> That's why it's important to have more testers during each milestone. I blew it again and didn't participate. Next time hopefully, I'll be ready. The milestone testing is a barrage of several legs of tests run. I would think this is where we need the most support.
And have the most FUN.

---

### Post by jis on 2009-10-21
What if user has applied some partial upgrade and he/she is not sure, if it is causing some problems? Is there a convenient recovery procedure?

---

### Post by adempewolff on 2009-10-21
As someone who is not incredibly experienced with Linux here is my experience:

Ran update manager to be offered a partial upgrade and a huge amount of updates.  Noticed this thread which suggested going through and looking at the changelogs for the updates to see what is going on.  I was overwhelmed by the amount of searching it would require to find out what was wrong.  I tried just waiting for a few days but the problem did not go away.

So...
I ran:
```
sudo apt-get update
sudo apt-get upgrade
```

This did all the updates but did not remove any packages.

Then I looked in the update manager gui and saw which packages were left as it offered me a partial upgrade.

Finally I went into synaptic, made sure it was set to "Smart upgrade" clicked "mark all upgrades" and hit apply.  Then I saw that there were two packages (gstreamer.shroe*, and some library) that were to be removed and some others to be upgraded and installed.  This all seemed reasonable and not likely to break my system so I hit apply.

Problem solved.

Is this a safe way to approach any partial upgrade problem that doesn't go away after waiting a little while?

---

### Post by flipper9 on 2009-10-21
Sounds like we need to rethink how updates are presented, or at the very least have a help button that takes the user to a location that explains what is exactly happening and the consequences.  Before I read this page, I had no idea what the "error" message meant, and just happily clicked through it.

---

### Post by ranch hand on 2009-10-21
That is the system I use by default.  I don't use Update Mangler at all, even on my older stable OS'.

---

### Post by 23meg on 2009-10-21
Here's a typical scenario where I figured out whether it was fine to let Synaptic remove *gstreamer0.10-schroedinger*, a package I knew nothing about previously, using one of the methods I suggested in the first post. This could have been any other package manager, such as Update Manager offering a "Partial Upgrade" to remove that package.

[list=1][*] Synaptic offered to remove the package *gstreamer0.10-schroedinger*. At this point I did not know whether Synaptic was offering to remove it due to temporary archive flux, or it was actually meant to be removed.

[[IMG]http://img16.imageshack.us/img16/2705/67492748.png[/IMG]](http://img16.imageshack.us/my.php?image=67492748.png)


[*] To figure out, I decided to check the karmic-changes mailing list. Since I'm subscribed to it, I actually did this **much faster** in my mail client, but for the sake of illustrating how it could have been done without being subscribed (by the way: **subscribing is very beneficial if you're serious about testing** - there's also [an RSS feed]("http://feeds.ubuntu-nl.org/KarmicChanges") if you don't want mail), and even only vaguely remembering the location of it, I'll pretend I browsed it at the web archives.


[*] At [https://lists.ubuntu.com/mailman/listinfo/Karmic-changes](https://lists.ubuntu.com/mailman/listinfo/Karmic-changes) (at which I may have arrived with a web search, or through [https://lists.ubuntu.com](https://lists.ubuntu.com)), I clicked the link leading to the archives.

[[IMG]http://img17.imageshack.us/img17/9418/65689993.png[/IMG]](http://img17.imageshack.us/my.php?image=65689993.png)


[*] I then clicked the "Date" link for the current month, since I was looking for what's probably a recent change, and I wanted the changes ordered by date.

[[IMG]http://img8.imageshack.us/img8/4152/74695720.png[/IMG]](http://img8.imageshack.us/my.php?image=74695720.png)


[*] I hit "Ctrl + F" in Firefox to search for the word "schroedinger", which is part of the package name, among the list of recent changes. I only typed the first few letters.

[[IMG]http://img12.imageshack.us/img12/2108/48677299.png[/IMG]](http://img12.imageshack.us/my.php?image=48677299.png)


[*] That highlighted what looked like a relevant change! I clicked on it to see the changelog.

[[IMG]http://img14.imageshack.us/img14/4971/85014317.png[/IMG]](http://img14.imageshack.us/my.php?image=85014317.png)


[*] I scanned through [the changelog]("https://lists.ubuntu.com/archives/karmic-changes/2009-October/010163.html") for a hint of whether this package is actually being removed. Searching the page for the words "remove", "drop" or "deprecate" was practical at this point, since I was looking to see if one of those things had happened to the suspected package.


[*] And there it was!
> debian/gstreamer0.10-schroedinger.install:
      - Dropped GStreamer plugin, it's now in gstreamer0.10-plugins-bad.


[[IMG]http://img8.imageshack.us/img8/4224/48655391.png[/IMG]](http://img8.imageshack.us/my.php?image=48655391.png)



[*] OK, it seems the GStreamer plugin for Schroedinger is being merged into the  *gstreamer0.10-plugins-bad* package, and the old package *gstreamer0.10-schroedinger* is being deprecated. So it should be fine to remove it.


[*] Just to make sure, and to satisfy my detective urge, I went back to archive page, and this time, searched for "plugins-bad", which led me to [a change entry for *gstreamer0.10-plugins-bad*]("https://lists.ubuntu.com/archives/karmic-changes/2009-October/011527.html").


[*] I looked for "schro..", and there we go:

>      + debian/gstreamer-plugins-bad.install:
       - Add new asfmux, frei0r, kate and schroedinger plugins.

[/list]

Now I know what's going on, and can comfortably let *any* package manager remove the suspected package. It's fine to accept a "Partial Upgrade" that wants to remove it.

---

### Post by thecow on 2009-10-21
Ubuntu keeps trying to get me to do a partial upgrade.  The updates left out are all related to pulse-audio.  In reading this thread it seems that I should accept this partial upgrade and not worry about pulse-audio.  However in also reading this thread it seems that I shouldn't do a partial upgrade at all.  Any response to this?

```
The following packages have been kept back:
  gstreamer0.10-plugins-bad libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11
  pulseaudio-utils xserver-xorg-input-all

```

---

### Post by DodgeV83 on 2009-10-21
> **23meg said:**
> Here's a typical scenario where I figured out whether it was fine to let Synaptic remove *gstreamer0.10-schroedinger*, a package I knew nothing about previously, using one of the methods I suggested in the first post. This could have been any other package manager, such as Update Manager offering a "Partial Upgrade" to remove that package.

...



Thanks for that!  I've been looking at the "Partial Upgrade" screen for days waiting for it to go away :)  I had the same issue with it wanting to remove gstreamer0.10-schroedinger.

I just did the update cleanly, nothing broke.

Thanks again!

---

### Post by psyke83 on 2009-10-21
> **thecow said:**
> Ubuntu keeps trying to get me to do a partial upgrade.  The updates left out are all related to pulse-audio.  In reading this thread it seems that I should accept this partial upgrade and not worry about pulse-audio.  However in also reading this thread it seems that I shouldn't do a partial upgrade at all.  Any response to this?

```
The following packages have been kept back:
  gstreamer0.10-plugins-bad libpulse-browse0 libpulse-mainloop-glib0 libpulse0
  pulseaudio pulseaudio-esound-compat pulseaudio-module-bluetooth
  pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11
  pulseaudio-utils xserver-xorg-input-all

```

23meg did a great service by providing this sticky thread and taking the time to give an example in detail ([post #101]("http://ubuntuforums.org/showpost.php?p=8142730&postcount=101")), but the point of that example is so that you will learn how to verify *any* Partial Upgrade scenario *yourself*.

Your output is from "sudo apt-get upgrade" - that will never trigger a partial upgrade. You need to check the "sudo apt-get dist-upgrade" output to see what packages are getting removed, etc. It's explained in the first post.

---

### Post by flipper9 on 2009-10-22
23meg: thanks for the detailed info and screenshots!  Very helpful. :KS

But stepping back, do we expect regular home users to go through all that to decide whether or not they should update or not?  We really need to work on the update process (which is kick donkey [seriously, I can't say the three letter version?], and better than Windows' or Macintosh's update system) to make it either simpler or with lots of hand holding for those that need it (even if it is just a button for "more options") and options to do whatever you want for those that need advanced needs.

---

### Post by VMC on 2009-10-22
> **flipper9 said:**
> But stepping back, do we expect regular home users to go through all that to decide whether or not they should update or not?Your Absolutely right. We need a better approach. Users especially coming from Windows won't  go that route.

For geeks, this is how we analyze questionable packages, but your just not going to get "wanting to be ex" Window users or even Mac users to comply.

I'm afraid this topic of Partial Upgrade will be with us for the foreseeable future. You can make harsh warnings and try to threaten or coerce, but in the end don't be surprised if you still see this topic raise its ugly head.

Until you remove Partial Upgrade from users hands its going to be questioned. And the hullabaloo that 23meg suggested is just going to be ignored.

---

### Post by ranch hand on 2009-10-22
I do not think that "regular" home users are testing.  The reason for testing is so that the "regular" home user can get the stable release with some assurance that it is stable.

Then the "regular" user can expect that kick posterior "normal" update.

---

### Post by 23meg on 2009-10-22
> **flipper9 said:**
> 23meg: thanks for the detailed info and screenshots!  Very helpful. :KS

But stepping back, do we expect regular home users to go through all that to decide whether or not they should update or not?  

No. Because we don't expect regular home users to run the development branch in the first place.

> **flipper9 said:**
> We really need to work on the update process (which is kick donkey [seriously, I can't say the three letter version?], and better than Windows' or Macintosh's update system) to make it either simpler or with lots of hand holding for those that need it (even if it is just a button for "more options") and options to do whatever you want for those that need advanced needs.

The update process is dead simple in stable releases. We should rather work on educating our semi-regular testers better on good testing practices.

> **VMC said:**
> Your Absolutely right. We need a better approach. Users especially coming from Windows won't  go that route.

What route? "Users coming from Windows" should not be expected to dive straight into the development branch without the minimum amount of awareness regarding what they're getting into and why. If they are, at any significant rate, we should work on fixing *that*.

> **VMC said:**
> For geeks, this is how we analyze questionable packages, but your just not going to get "wanting to be ex" Window users or even Mac users to comply.

Again..

> **VMC said:**
> I'm afraid this topic of Partial Upgrade will be with us for the foreseeable future. You can make harsh warnings and try to threaten or coerce, but in the end don't be surprised if you still see this topic raise its ugly head.

I'm not sure why you phrased it like that, but nobody has threatened or coerced anyone into anything, in this thread or elsewhere, regarding this issue. But indeed, until we can do reasonably well at educating people on the very basic good practices in testing, we're going to have to keep telling people how not to needlessly wreck their testing installations. 

> **VMC said:**
> Until you remove Partial Upgrade from users hands its going to be questioned. And the hullabaloo that 23meg suggested is just going to be ignored.

I'm not that pessimistic. The "Partial Upgrade" prompt does need a redesign (and it's on my agenda to discuss that with Michael Vogt and others at UDS), but ultimately whether people keep falling into similar traps depends on how well they get informed on basic testing procedures.

If the above sounds like "hullabaloo" to many, we have a lot of work to do in that department.

---

### Post by flipper9 on 2009-10-22
The main page of Ubuntu says to try out the Beta.  The news is reporting that Karmic is the best Linux distribution upgrade ever.  People are going to try it out, they are going to click through the "Partial Upgrade" button with no clue as to what it means (and even though I'm a programmer, I still have no clue what that actually means or what it does) just like everyone clicks through anything they don't understand (whether it's a cryptic error message/number, long EULA license full of legalease, or an OK button with lots of warnings that make no sense).  

You just have to accept the fact that people, regular people or "power users", are going to run the development version and if things go horribly wrong after they clicked on a button they don't understand, they're gonna blame Ubuntu for it.  I'd suggest that we just take the time to add more HELP and info to end-user tools (like Update Manager) that hand-hold someone and explain what is going on step by step.  Then if they continue down the wrong path, they have nobody to blame but themselves.

My vision for upgrades (and I understand that Ubuntu wants to combine update manager, software center, and synaptic into one tool) is to have a single tool with options for beginner/intermediate/advanced. Beginners would be hand-held through the process, and protected from screwing things up.  Intermediate users would be given warnings and info  but allowed to screw things up if they want, and advanced lets you do everything.  IMHO Update Manager is no different than "beginner mode".  Anything it does shouldn't allow the user to screw things up.  The Partial Upgrade thing at first glance looks like it won't screw things up, and it will just update things that can be upgraded.  My reading seems to be false as in certain circumstances, that nobody has been able to explain as of yet, Update Manger and Partial Upgrade can screw up your system.  That doesn't seem right for an end-user tool to do that.  I'd expect that I'd screw up my system in Synaptic.

---

### Post by ranch hand on 2009-10-22
+1

Well put 23meg.

I am a very green noob.  Yes, I have had some breakage.  Some, no doubt, MY fault.  Some was just to be expected.

We were, I feel, well warned by the warning on the opening page of the install process.  I thought, and continue to think, that was sufficient warning.  The warning in the sticky was just icing on the cake.

With those two things I feel that anyone that loaded 9.10-testing, got just what they wanted.  I know that I did.  It has been very frustrating at times but always educational and, really, FUN.

The only thing that I think might make it better is to not remove the warning on the install process until the RC.

The rest is just "Hey if you stick your finger in the socket and flip the switch and get shocked - YOU HAVE BEEN WARNED".

Thank you for your patience.  I am a grumpy geezer and have always been short in that department.

---

### Post by the.lost.one on 2009-10-22
I am a Home user, windows user and an accountant. I had never seen Ubuntu until a few weeks back. Luckily I have managed to do a successful partial upgrade (thanks to simulation switch and some research and some wait). The only reason why I moved from Jaunty to still in beta Karmic is that Jaunty's graphics performance was pathetic on my machine. I mean I couldn't properly watch youtube videos or any flash based videos in full screen. Karmic has improved a LOT in that area.

---

### Post by VMC on 2009-10-22
> **23meg said:**
> No. Because we don't expect regular home users to run the development branch in the first place.
..(I'm in here somewhere)....

I see the error of my ways...or rather my thinking. You are absolutely correct. New users from any OS should know better than start using a "testing" OS. Or at least know what their getting into.

Your description of how to weed out Partial Upgrade issues was/is the correct avenue to take. Partial Upgrade is a non issue with released distributions.

I personally have had no issue with the Partials, and know how to take care of them, but I keep seeing topics and posts come up in rabbit fashion.

I keep forgetting or need to tell myself to weigh the experience level of each post I see. It is their responsibility to know what their getting into and know the difference of testing vs release.

Edit:
If the above sounds like "hullabaloo" to many, we have a lot of work to do in that department.

edit:> If the above sounds like "hullabaloo" to many, we have a lot of work to do in that department.
It doesn't. Forget what I said. I was thinking of the poor lost soul that wanders in here, "Fat, Dumb, and Happy",  only to be presented with a Partial Upgrade, and then like a deer in headlights, thinking WTF???

---

### Post by linusr on 2009-10-22
how smooth is upgrade from 9.04 to 9.10 going to me? I guez it can't be trusted 100%!!

so ppl end up doing fresh install every 6 months?

---

### Post by linusr on 2009-10-22
how smooth is upgrade from 9.04 to 9.10 going to me? I guez it can't be trusted 100%!!

so ppl end up doing fresh install every 6 months?

---

### Post by lovinglinux on 2009-10-22
> **linusr said:**
> how smooth is upgrade from 9.04 to 9.10 going to me? I guez it can't be trusted 100%!!

so ppl end up doing fresh install every 6 months?

I do only fresh installs. I personally don't trust upgrades. This time I even started with a clean home partition, since my first attempt to install Karmic created some weird high CPU usage. Probably a bad config file in my old home, since a newly created user account didn't suffer from the same probem.

---

### Post by flipper9 on 2009-10-22
> **linusr said:**
> how smooth is upgrade from 9.04 to 9.10 going to me? I guez it can't be trusted 100%!!

so ppl end up doing fresh install every 6 months?

Event though Ubuntu's upgrade capabilities are better than Windows, I reinstall every three months whether I'm using the same distribution of Ubuntu or Windows.  I'm always tweaking and seem to make my system unstable after awhile, LOL :D

For the general user, I'd say that using the upgrade procedure for a distribution of Ubuntu is pretty safe (if not near perfect) if they have used the stock PPAs.  If you've tricked out your system with non-supported stuff, then things get dicey.

---

### Post by ranch hand on 2009-10-22
Why install every 6 months?  The last LTS release was 8.04 and it still works great.  The next is 10.04 and I am sure that it will be great.

Looks to me like every 2 or 3 years is all you NEED  to do an install.

---

### Post by flipper9 on 2009-10-22
> **ranch hand said:**
> Why install every 6 months?  The last LTS release was 8.04 and it still works great.  The next is 10.04 and I am sure that it will be great.

Looks to me like every 2 or 3 years is all you NEED  to do an install.
Depends on what kind of user you are. Some people want a stable system, and don't care about new features.  Some people want the latest and greatest, but want stability.  Some people are crazy (like me) and want the freshest crack that the developers are pushing. 

For example, I want the latest OpenOffice that will allow me to want to leave Microsoft Office 2007.  I want something easy to use, that doesn't keep popping up toolbars, can read MS documents without formatting issues, and looks good on a netbook screen.

Another example, I want the latest Firefox.  I want the latest wine to see if I can get Windows Live Sync to finally work.  I want something that can sync my iPhone.

Finally, once I get an email program that can support Microsoft Exchange 5.5 (2007), I can finally delete my Windows install once and for all.

For that reason, I upgrade all the time.  Sometimes I get totally frustrated with Linux and it's inability to do the above, run back to Windows for awhile, then come back when Ubuntu comes out with the latest upgrade and try again.  With Jaunty, I got such bad video performance I wanted to stay with Ubuntu, but ran back to Windows.  With Karmic, things are so great I think I'm going to finally stay and use dual-boot with Windows 7 until the time I can finally delete Windows.

---

### Post by slakkie on 2009-10-22
> **linusr said:**
> how smooth is upgrade from 9.04 to 9.10 going to me? I guez it can't be trusted 100%!!

so ppl end up doing fresh install every 6 months?

This shouldn't be asked in this thread. But upgrades are very stable, been doing it all my Ubuntu-life.

Regarding this thread. I think I'm going to be Cpt Obvious, but if people hit OK when they see a partial upgrade and they don't know what they are doing on a development release then should feel all the pain of doing that partial upgrade. Read before you do something. 
This isn't the US where people can be ignorant and blame someone else for their mistake. But it didn't say that.. Well think for yourself mate, read the documentation!

---

### Post by flipper9 on 2009-10-22
> **slakkie said:**
> This shouldn't be asked in this thread. But upgrades are very stable, been doing it all my Ubuntu-life.

Regarding this thread. I think I'm going to be Cpt Obvious, but if people hit OK when they see a partial upgrade and they don't know what they are doing on a development release then should feel all the pain of doing that partial upgrade. Read before you do something. 
This isn't the US where people can be ignorant and blame someone else for their mistake. But it didn't say that.. Well think for yourself mate, read the documentation!

When you get the dialog about the partial upgrade, it says NOTHING about what is about to happen.  It looks like a simple informational dialog, and makes it look like it is a pretty innocuous procedure.  What is needed is some more explaination in the dialog, maybe a LINK TO MORE INFO or something like that.  When I first clicked on it, I thought it was going to just going to update things that could be updated and leave alone those things that couldn't be updated.  I was wrong, and only found this forum and thread when things went wrong.  

You can blame the users for ignorance, but is that really improving Ubuntu?  I thought we were about ease of use?  Update Manager is supposed to be an end-user, easy-to-use utility. It SHOULD NOT screw things up.

---

### Post by 23meg on 2009-10-22
> **flipper9 said:**
> 
You can blame the users for ignorance, but is that really improving Ubuntu?  I thought we were about ease of use?  Update Manager is supposed to be an end-user, easy-to-use utility. It SHOULD NOT screw things up.

And does not, in stable releases, which end users use, as has been said many times in this thread.

---

### Post by VMC on 2009-10-22
> **flipper9 said:**
> You can blame the users for ignorance, but is that really improving Ubuntu?  I thought we were about ease of use?  Update Manager is supposed to be an end-user, easy-to-use utility. It SHOULD NOT screw things up.I don't see any complaints coming from seasoned users.As far as Ubuntu being ease of use, that's an individual viewpoint. As has been stated many times, "TESTING is not for the faint of heart" or for those lacing experience.

---

### Post by neglesaks on 2009-10-22
> **linusr said:**
> how smooth is upgrade from 9.04 to 9.10 going to me? I guez it can't be trusted 100%!!

so ppl end up doing fresh install every 6 months?


No, when upgrading distributions, and the Partial Ungrade notification pops up, the proper procedure to follow is this:

1) Click cancel. Perform a regular update of your packages, and reboot.
2) Run Upgrade Manager again, this time say OK to a Partial Upgrade.

That is, however, if you *want* to do a partial upgrade (which is the name for an upgrade that also *removes* certain, obsolete or superseded packages). It can create problems on occasion, but shouldn't for non-development users that haven't been doing too much amateur surgery on the innards of their operating system.

In case you end up with a broken system anyway, keep a stable version live-cd handy.

Happy upgrading, folks!

---

### Post by flipper9 on 2009-10-22
> **VMC said:**
> I don't see any complaints coming from seasoned users.As far as Ubuntu being ease of use, that's an individual viewpoint. As has been stated many times, "TESTING is not for the faint of heart" or for those lacing experience.
I'm a seasoned user of Linux, have been for well  over a decade.  And I'm complaining.  Now, am I willing to deal with the issues?  Yes. I reinstall all the time, tweak, etc.  But my point still stands.  We need more information presented when the dialog pops up.  You can't assume that everyone knows, even seasoned users, what that button will do.  

Side note:  what kind of "seasoned" vs. "non-seasoned" kind of comment is that?  We should be thinking about all users, not the attitude that non-seasoned users should be left in the dust.

---

### Post by neglesaks on 2009-10-22
> **flipper9 said:**
> I'm a seasoned user of Linux, have been for well  over a decade.  And I'm complaining.  Now, am I willing to deal with the issues?  Yes. I reinstall all the time, tweak, etc.  But my point still stands.  We need more information presented when the dialog pops up.  You can't assume that everyone knows, even seasoned users, what that button will do.  


I agree. I'm kind of a linux newbie, but I'm not new to computers and their innards, and first time I got the "PU" dialog, I was stumped, but asked it to perform a PU anyway out of ignorance. Fortunately, the PU only wrecked my system once (which was the upgrade from alpha 4 to a5 or KK.)

---

### Post by Aero-Z on 2009-10-22
When I installed the Beta (about 4-5 days ago) I also saw the popup about partial upgrade. And ofcourse I didn't know what was that about so I accepted it. At least nothing broke after that :)

---

### Post by VMC on 2009-10-22
> **flipper9 said:**
> I'm a seasoned user of Linux, have been for well  over a decade.  And I'm complaining.  Now, am I willing to deal with the issues?  Yes. I reinstall all the time, tweak, etc.  But my point still stands.  We need more information presented when the dialog pops up.  You can't assume that everyone knows, even seasoned users, what that button will do.  

Side note:  what kind of "seasoned" vs. "non-seasoned" kind of comment is that?  We should be thinking about all users, not the attitude that non-seasoned users should be left in the dust.

23meg painstakingly [**_[SIZE="4"]explained[/SIZE]_**]("http://ubuntuforums.org/showpost.php?p=8142730&postcount=101") what to do !!!

---

### Post by 23meg on 2009-10-22
[QUOTE=flipper9]We need more information presented when the dialog pops up. You can't assume that everyone knows, even seasoned users, what that button will do.[/QUOTE]

No, we need to entirely redesign the way the "Partial Upgrade" is presented to the user, and that includes changing the name "Partial Upgrade" itself. "More information" is not a cure. If we bombard people with information at a time when they're trying to get a tedious piece of computer maintenance work like software updates done, that information will be ignored by the majority. And if we're talking about more information regarding the "Partial Upgrade", it's entirely unneeded in a stable release.

To recap:

[list][*] People using stable releases, regardless of whether they're "seasoned" users or not, are not affected by the horrors of the "Partial Upgrade", since Update Manager will not offer it in stable releases unless things are wildly broken
 

[*] People running the development branch with an understanding of what they're doing, and basic knowlegde of where to find out information regarding how updates work in the development phase will, at worst, wreck their installation once, and be unaffected in the future


[*] People running the development branch with little or no understanding of how the essentials work, and why they work the way they do, will soon run into other kinds of trouble than the "Partial Upgrade" phenomenon anyway, and will not be able to contribute anything substantial to quality assurance, since they'll keep messing up their installations, contaminating them with unofficial libraries and hacks, rendering them useless for any serious testing, etc.

[/list]

As should be obvious, we only need to get better at working with the third group of people.

---

### Post by flipper9 on 2009-10-22
Thanks for the info 23meg, makes it easier to understand and clear.

---

### Post by ranch hand on 2009-10-22
> **flipper9 said:**
> Depends on what kind of user you are. Some people want a stable system, and don't care about new features.  Some people want the latest and greatest, but want stability.  Some people are crazy (like me) and want the freshest crack that the developers are pushing. 

For example, I want the latest OpenOffice that will allow me to want to leave Microsoft Office 2007.  I want something easy to use, that doesn't keep popping up toolbars, can read MS documents without formatting issues, and looks good on a netbook screen.

Another example, I want the latest Firefox.  I want the latest wine to see if I can get Windows Live Sync to finally work.  I want something that can sync my iPhone.

Finally, once I get an email program that can support Microsoft Exchange 5.5 (2007), I can finally delete my Windows install once and for all.

For that reason, I upgrade all the time.  Sometimes I get totally frustrated with Linux and it's inability to do the above, run back to Windows for awhile, then come back when Ubuntu comes out with the latest upgrade and try again.  With Jaunty, I got such bad video performance I wanted to stay with Ubuntu, but ran back to Windows.  With Karmic, things are so great I think I'm going to finally stay and use dual-boot with Windows 7 until the time I can finally delete Windows.
Did you, by any chance, glance at my sig?  I actually do use Hardy as my "business" OS.  Jaunty (actually Stoner Edition 1.0) is the one I use the most.

The thing that linuser was implying was that you need to upgrade every six months.

All I was saying is that you do not need to at all.  Use a LTS release.

As you point out, there are some of us that are a little out there.

There is a limit on the size of your sig on these forums, by the way.  Mine, for instance, does give a pretty good idea of my box but not much of a hint as to the 30 OS' on various drives, none of which is WinWhatever or Hackintosh.

I prefer Ubuntu although Debian (particularly the respin PhatDebian that runs 2.6.30) is a close 2nd.  Mandriva is real nice too, particularly the 2009-1 or "spring" (Live DVD download and you can choose Gnome, KDE, Lxde or all three to install) is pretty cool.

---

### Post by ranch hand on 2009-10-22
> **neglesaks said:**
> I agree. I'm kind of a linux newbie, but I'm not new to computers and their innards, and first time I got the "PU" dialog, I was stumped, but asked it to perform a PU anyway out of ignorance. Fortunately, the PU only wrecked my system once (which was the upgrade from alpha 4 to a5 or KK.)
I do not like Update Mangler, I do not use it on any of my installs, however, the update you are talking about can not be blamed, in any way, on U-M.

I think a majority of testing platforms had, at least some trouble with that.  I had one install that was unbootable for 4 days although I could get to a terminal and update from there and it finally came around.

---

### Post by slakkie on 2009-10-22
> **flipper9 said:**
> When you get the dialog about the partial upgrade, it says NOTHING about what is about to happen.


Well, if you don't know what a partial update is you should figure it out. Googling on partial upgrades is very informative, since you see tons of results where a partial upgrade fails. So that should give an indication on what button NOT to press. If you don't know ASK (or Google preferably, then ask if you're still not sure). This is even mentioned in the Code of Conduct, which you should have read because you have a launchpad account since you are running a development release.

> 
You can blame the users for ignorance, but is that really improving Ubuntu?  I thought we were about ease of use?  Update Manager is supposed to be an end-user, easy-to-use utility. It SHOULD NOT screw things up.

Well, blaming a user for being ignorance will not help Ubuntu, but hopefully it will change the mind set of a user of doing things without thinking. That would be a nice change in attitude :) 

If one uses a development release, one is supposed to know that packages will not arrive in a consistent state on the archive (meaning that not all dependencies will be present at the same time, packages can be removed, etc). So this will lead to situations not seen on normal stable releases (as meg23 pointed out already). 
You are a normal user and you want ease of use? Use a stable release. There are currently 4 stable releases: Dapper/Hardy/Intrepid/Jaunty. Running a development release means: This is not stable, this is not ready for daily usage, this is not something you want to run when you are not willing to break stuff or not willing to fix breakage. This is meant for people who want to help testing and want to develop against our upcoming release. Normal users should not run a development release. And if they do, they should use all the resources they have available to make it a pleasant ride.

PS. I didn't mean you as in you personally btw :)

---

### Post by flipper9 on 2009-10-22
True; Googling would help.  But the dialog says nothing about this particular partial upgrade having the possibility of causing problems.  It looks like it would do nothing potentially dangerous.  Not a warning in red letters, or anything.  "Partial Upgrade" seems pretty innocuous.  People won't Google "Partial Upgrade" until things go wrong.  Do we really want things to go wrong? Is this some kind of initiation to becoming a "seasoned user"?  I don't think that's a good plan.

As for stable releases, I found the full Jaunty release and all associated updates to be pretty UNSTABLE on my laptop.  I have found the Karmic unstable alpha/beta releases to be pretty STABLE on my laptop.  Karmic really is the only way to go for those with Intel graphics on their laptops, whether it's a beta or not.  For me running Ubuntu on my laptop, I really had no choice but to run Karmic instead of Jaunty or run something really older without features that I wanted.  It was either that or go back to Windows that fully supported my laptop without issues. (not trying to be a Troll; I really like Linux and want to use it, but things are not as good as in Windows, especially with the attitudes about developers vs. users mentality).

---

### Post by ranch hand on 2009-10-22
When you are getting 3 kernel updates in 3 days it is a pretty good clue that things are in flux.

---

### Post by Rifester on 2009-10-22
I have had to do a clean re-install of Karmic.   Should I hold off on updates completely at this point?  How will I know when it is safe?

---

### Post by ranch hand on 2009-10-22
It should be "safe" after the Final Release.  That is why this is called "testing".  To find out what breaks and get it fixed.

---

### Post by psyke83 on 2009-10-22
> **MRife said:**
> I have had to do a clean re-install of Karmic.   Should I hold off on updates completely at this point?  How will I know when it is safe?

You will know after thoroughly reading 23meg's post, and applying the steps to your installation.

---

### Post by Rifester on 2009-10-22
Thanks, I would not have thought that updates would wreck the whole system.   I am not complaining about testing (just curious).  My curiosity is what prodded me to install Karmic and it has been a learning experience.

---

### Post by aimwin on 2009-10-28
> **VMC said:**
> AMEM to that!

I don't want Ubuntu to discourage anyone from testing the "testing" distros. The more the better, even if some poor inexperienced newby wonders in. It's their computer and their responsibility to read the [SIZE="1"]fine print[/SIZE]. 

The more testers, the more bugs to uncover. Not withstanding VM users, which really only check the installation process. And how many of them do we need. We need more hardware testers!

[B]I agree, Beta should be advertise. 
But only with the conditions.

[COLOR="Red"]_Better warning message._[/COLOR][/B]

Can we debate on _[COLOR="Red"]what is the negative or bad image [/COLOR]_of "better warning message"?

---

### Post by aimwin on 2009-10-28
> **23meg said:**
> And does not, in stable releases, which end users use, as has been said many times in this thread.

Dear 23meg,

Please comment if there is any negative effect if we have a better warning, especially your "statements" or "warning" which I quoted as a "better warning in beta"

Thank you, with great respect.

---

### Post by 23meg on 2009-10-28
> **aimwin said:**
> Dear 23meg,

Please comment if there is any negative effect if we have a better warning, especially your "statements" or "warning" which I quoted as a "better warning in beta"

Thank you, with great respect.

I'm not sure it's feasible to include a different warning during the pre-release phase, since during that phase we also need to test Update Manager itself the way it will work in a stable release. 

If what you mean by "better warning" is bigger, flashy letters shouting at testers that Update Manager is about to break their system, I don't think that will be beneficial. And going too far in that direction may cause people to simply refrain from updating some packages indefinitely, and asking for assistance on whether or not to remove them every time, the same way they do now. As long as people don't learn how to figure out what needs to be done when a package is being held back or removed, the problems will remain.

---

### Post by flipper9 on 2009-10-28
> **23meg said:**
> I'm not sure it's feasible to include a different warning during the pre-release phase, since during that phase we also need to test Update Manager itself the way it will work in a stable release. 

If what you mean by "better warning" is bigger, flashy letters shouting at testers that Update Manager is about to break their system, I don't think that will be beneficial. And going too far in that direction may cause people to simply refrain from updating some packages indefinitely, and asking for assistance on whether or not to remove them every time, the same way they do now. As long as people don't learn how to figure out what needs to be done when a package is being held back or removed, the problems will remain.

How can not warning the user that they are about to break their system going to help things?  You say you want people to understand what a partial upgrade does, and then you say you don't want them to know it will break their system because you want to test out Update Manger.  That doesn't jive.

I think there should be more information on that dialog than just the words "Partial Upgrade", which nobody will understand unless they go and research and find out that an innocuous sounding thing is actually probably going to destroy their system (potentially).  I think there should at least be a link to help or somewhere online to explain what it does.  Keeping users in the dark isn't a good practice.

---

### Post by ranch hand on 2009-10-28
No, 23meg is saying that you have been warned, you need to know how to check into these things your self and that changing the system more defeats the purpose of testing as UM would no longer be the one we use in the Final release.

None of this is hard to understand.  It is plainly stated, in clear language.

I am having trouble understanding these continuing troll attacks on 23meg as if there is some personal harm being done to you because 23meg will not come to your computer and guard you from yourself.

Give it a damned break.  These juvenile looping arguments  are a waste of forum space and silly, besides being insulting to 23meg who started this thread so that people would have exactly the type of warning and support you, apparently, want hand delivered by your nanny.

---

### Post by flipper9 on 2009-10-28
I'm attacking no one.  I'm suggesting changes to the system that I would think benefit the users.  Take a break or something.

And if we can't speak our minds about a topic that is important to us, or there is some kind of hiearchy where certain users can speak and others have to yield to the wishes of others, then what's the point of the forum?  No disrespect to 23meg, who appears to be important, but I disagree with his thinking.  If that's insulting him, then there is a problem with the Ubuntu system where we can't disagree.

---

### Post by 23meg on 2009-10-28
> **flipper9 said:**
> How can not warning the user that they are about to break their system going to help things?  You say you want people to understand what a partial upgrade does, and then you say you don't want them to know it will break their system because you want to test out Update Manger.  That doesn't jive.

I'm not advocating not warning people that a "Partial Upgrade" *can be* dangerous if they don't know what they're doing. "*Can be*" is the part you seem to miss.

What I'm saying is that a "Partial Upgrade" is not *necessarily* harmful, and is actually *needed* in many cases, and that bigger, flashier letters shouting "I'm about to break your system - Would you like to continue?" at testers is not a solution. The solution, as I've stated a few times, is to redesign the entire way the Partial Upgrade is presented to pre-release testers and stable release users, perhaps separately, and work harder and do better at educating semi-regular and irregular testers on what they should do when faced with one.

> **flipper9 said:**
> I think there should be more information on that dialog than just the words "Partial Upgrade", which nobody will understand unless they go and research and find out that an innocuous sounding thing is actually probably going to destroy their system (potentially).  I think there should at least be a link to help or somewhere online to explain what it does.  Keeping users in the dark isn't a good practice.

There's already more information than just the words "Partial Upgrade", but it doesn't work well enough.

---

### Post by flipper9 on 2009-10-28
Thanks 23meg.  I think I understand.  Maybe necessary partial upgrades can be detected, and ones that cause problems (due to being mid-way in an update with not all updates available) can be detected and the message can be different depending.  As long as these types of updates never come up during the regular life of a release then I guess it's not too big of an issue.

I only brought it up because, as a power user, the description and title presented seemed to be pretty innocuous, and no more dangerous than running a alpha/beta/development release that we all accept when we use such a system.  Guess education is the key, but as we know not everyone gets their education until something goes wrong, and some will just choose not to listen. 

Thanks again, and glad to hear someone is considering these issues.

---

### Post by dadedo123 on 2009-10-29
Wohoo! We'll be getting the final release today! So no need to worry about Partial Upgrades from now! xD

---

