---
title: "Official Upgrade Guide is not working for me (kubuntu)"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by exhuma.twn on 2007-10-19
I wanted to upgrade from Feisty to Gutsy this morning, but [the official guide](http://www.ubuntu.com/getubuntu/upgrading) is not working for me. For some reason the "Version Upgrade" Button never shows up. I followed the guide to the letter, re-read id tree times to be sure. I even went as far and disabled the third-party repositories I added a while back. Yet, I still do not get a "Version Upgrade" button.

I know that I can force it using "adept_manager --version-upgrade" but I was hit in the face several times already by forcing/overruling too much. Unless, this *is* the standard way of doing this.

What could be the reason for the button not showing up?

If "adept_manager --version-upgrade" really *is* the standard way, why is it not easily accessible via the menu? For people that are afraid of the CLI ;)

---

### Post by Kaptain Chaos on 2007-10-19
Hello,
I'd hold off for a few days, there seems to be a few problems surfacing with upgrading at the moment. Besides, servers are usually overloaded when a new release is issued. I've 2 pcs running Ubuntu, my main and a testing machine. Main pc is on Feisty but I upgraded the other yesterday (18/10) but there are issues with the new kernel hanginging during the boot up process and the display keeps reverting back to a 'safe mode'. I'm going to wait for a few more weeks before considering upgrading the main pc while trying to fix the test one.

---

### Post by exhuma.twn on 2007-10-19
Good point. It's just so hard to wait while knowing that the new shiny version is out there waiting to be downloaded :biggrin:

Is there any place you suggest to look for any news? The forum has quite a lot of traffic and I cannot afford the time to check back every 5 minutes :|

---

### Post by JarkkoP on 2007-10-19
I upgraded my Kubuntu Feisty to Gutsy, with success.

However, I found again that adept is a very poor front-end to manage your packages. First try on "version upgrade" stopped on error: "could not verify the integrity of the upgrader application. This program will now exit.". Second identical run passed that, but failed after installing a few packages (seg faults), tried to continue and just stopped to "preparing to configure libidl0".

At this point there certainly were broken & unconfigured packages.

I had no choice but cancel the upgrade at that point. Apt was locked in spite of adept was closed normally, could not see what process automatically started dpkg to set the lock. Solved this by:

```
fuser -vki /var/lib/dpkg/lock; dpkg --configure -a
```

After forcing to download the missing package dependencies I was able to dist-upgrade:

```
apt-get dist-upgrade
```

The rest went quite nicely.

---

### Post by brel on 2007-10-19
My problem is the 'full upgrade' button in adept never activates--I see it but can't click on it. I've run 'fetch updates' about seven times now. I also tried deactivating all my third party URLs. 

I'm going to wait a bit before trying again but it would obviously be better if I had ANY indication of what I'm doing wrong or a msg telling me the upgrade servers are not working if that is indeed the problem.

---

### Post by brel on 2007-10-20
I've run 'kdesu "adept_manager --version-upgrade"' and things seem to be moving along quite nicely. Let's face it, the interface for adept_manager is crap. Hopefully it's one of the things upgraded in 7.10 :)

---

### Post by exhuma.twn on 2007-10-22
> **brel said:**
> I've run 'kdesu "adept_manager --version-upgrade"' and things seem to be moving along quite nicely. Let's face it, the interface for adept_manager is crap. Hopefully it's one of the things upgraded in 7.10 :)

Shouldn't it work automatically without the "--version-upgrade" flag? I am a bit reluctant to force the upgrade, as it deviates from the Recommended Method. And as said earlier, doing this resulted in some nasty itches already (with (k)ubuntu).

As I am using Linux already since around '96 or so, I know enough to get a broken system up and running again. But I am actually using Ubuntu because it is said to "just work". And I am too tired to go ahead and fiddle around with my OS just to get X back up and running ;) So I'd really like to see the Recommended Method working the way it's advertised.

---

### Post by opm8 on 2007-10-22
Adept should be renamed Retard.

I wish the "official" upgrade method didn't rely on a piece of crap GUI that calls dpkg and apt-get in the background. Why is it so hard to have a command-line official method?  This ticks me off to no end.  This is exactly the reason Windows is such a nightmare to administer, because of all the clunky GUIs.  Ubuntu should not mimic this behavior.

opm8

---

### Post by exhuma.twn on 2007-10-22
> **opm8 said:**
> Adept should be renamed Retard.

I wish the "official" upgrade method didn't rely on a piece of crap GUI that calls dpkg and apt-get in the background. Why is it so hard to have a command-line official method?  This ticks me off to no end.  This is exactly the reason Windows is such a nightmare to administer, because of all the clunky GUIs.  Ubuntu should not mimic this behavior.

opm8

I have to disagree. Windows is a nightmare to administer because you *only* have the GUI's do perform certain tasks. With Linux (in this case Ubuntu), you *can* use the GUI. If you really want to, there are always alternatives. Either by using the shell or by using anoter GUI. I would not be surprised that you can use the "Server upgrade instructions" as well for desktop installations. For example:

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

However, I would like to follow the instructions as mentioned for kubuntu. The problem I ran into here, and finding the solution to it, might help some lost user searching this forum.

Mindlessly flaming a distro or whatever else does not accomplish anything. But I have to agree that Windows administration sucks, compared to Linux administration :neutral:.

---

### Post by opm8 on 2007-10-22
> **exhuma.twn said:**
>  I would not be surprised that you can use the "Server upgrade instructions" as well for desktop installations. For example:

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

However, I would like to follow the instructions as mentioned for kubuntu. The problem I ran into here, and finding the solution to it, might help some lost user searching this forum.

Mindlessly flaming a distro or whatever else does not accomplish anything. But I have to agree that Windows administration sucks, compared to Linux administration :neutral:.

You might not be surprised if those work for a desktop, but do you know for sure if they do?  Of course not, because the official method is to use the crappy Adept gui.  My argument is that instead of forcing the use of Adept, command line options should also exist for those of us who know what they're doing and don't like to guess at what a gui is doing.

---

### Post by exhuma.twn on 2007-10-23
I agree. But when you opt for ubuntu, you kind of expect it to be more GUI-centric. If you want something else, there are other distros. And there are surely other active threads that deal more in detail with the neverending GUI/CLI dispute. As for this topic, we are digressing.

**Back to topic**: Is there a solution for the aforementioned problem?

---

### Post by zmolnar on 2007-10-23
I have the very same problem on both my home and workplace computer. :( I think I postpone the upgrade to Gutsy for a while...

---

### Post by exhuma.twn on 2007-10-23
Is this a general problem for Kubuntu? Or did it actually work for someone as advertised?

---

### Post by Beanalby on 2007-10-23
Got the same problem; following the official guide and got "could not verify integrity of the upgrader application."

---

### Post by seantellis on 2007-10-25
I'm seeing something similar to the original poster, but even more so. 

The "manage repositories" dialog is effectively just a fancy text editor with the text of sources.list in it, not the nice tabbed dialog shown in the screen shots that accompany the official guide. I do have a number of 3rd party repositories as well, in case that's of any import.

I see no "version upgrade" button at all, enabled or not. It is also not in the list of buttons in the "configure toolbars" dialog.

My Adept version number is 2.1 Cruiser, (2.1.2ubuntu26.1) which Adept itself suggests is up-to-date, but to be frank I don't actually believe it.

Any ideas gratefully appreciated. If I find the problem, I'll follow up here myself.

By the way, here is my /etc/apt/sources.list file:

```
deb http://download.skype.com/linux/repos/debian/ stable non-free
deb-src http://seveas.imbrandon.com/ feisty-seveas extras seveas-meta custom
deb http://seveas.imbrandon.com/ feisty-seveas extras seveas-meta custom
deb-src http://packages.freecontrib.org/ubuntu/plf feisty-plf free non-free
deb http://packages.freecontrib.org/ubuntu/plf feisty-plf free non-free
deb http://archive.canonical.com/ubuntu feisty-commercial main

deb http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security universe multiverse

```

---

### Post by seantellis on 2007-10-25
Right. The snazzy repo list dialog is in fact the small print at the bottom of the screenshots page: "Note: you should have software-properties-kde installed first."

Sigh. Always read the small print. Seems to be going now. Apologies for the incovenience.

---

### Post by ahalawei on 2007-10-25
Not sure if this is the right thread, but bear with me.

   I have been running vista (which I dislike) along with Ubunutu Feisty 7.04. Just decided to upgrade to Gutsy 7.10 using the following commands:

sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

Process went well and after restart, when i choose to boot in ubuntu 7.10, it leads me to a blank window with a cursor at the top, nothing else.


Any ideas? HELP???

---

### Post by exhuma.twn on 2007-11-06
So I tought I waited long enough now..... I ran adept again, but I still don't see the "version upgrade" button. So I thought "What the hell" and ran "adept_manager --version-upgrade" and clicked the "version upgrade" button. This is what I get when running it from the shell:

```
kapture::PkgSystem::PkgSystem()
libasound2
libc6
mpg321
libasound2
libc6
mpg321
kdecore (KProcess): WARNING: _attachPty() 46
KCrash: Application 'adept_manager' crashing...
```

Woohoo. So no version upgrade for me. Any ideas?
Has anyone tried to use the Gnome update-manager with KDE? Any success with that? This issue starts to bug the hell out of me. Other distros manage the version upgrades very smoothly. But none of them are as desktop-friendly as ubuntu.

This is the third time I try to follow the official upgrade guides to the letter with no success. I see a pattern emerging there. And I am surely not the only one. Can the **k**ubuntu devs please look a bit more in detail to the version upgrades?

Well. To be honest. Upgrading ubuntu is still easier than windows once you get it working ;)

---

### Post by FSHero on 2007-11-08
hi there guys,

I am having the same problem: the "Full Upgrade" button is displayed, but is greyed out. I have two computers exhibiting this problem.

However, if I run K-Menu --> System --> Update Manager (to run /usr/bin/update-manager, the GNOME update manager), there is conveniently a button for "Upgrade", with a message saying "New distribution release '7.10' is available'. (I have this on my older computer.)

Let me start by saying that Kubuntu is a fantastic GNU/Linux distro overall. (I haven't tried any others really... :P but it is worlds apart from M$ Windows) But I have the feeling that the Ubuntu developers give Kubuntu a second thought.

For example, 7.04 brought Ubuntu the restricted drivers manager, but only Kubuntu 7.10 has brought a native KDE version. Also, the Adept manager ("Add/Remove Programs") for Kubuntu 7.04 does not show as much information as the Ubuntu and Xubuntu 7.04 releases.

My message is: please don't leave Kubuntu as an afterthought! Give it the same attention that Ubuntu gets!

/rant

But back to topic: I thought that I was having problems because, early in my installation of Kubuntu, I installed the package ubuntu-desktop on my older comp, because I wanted to see what Ubuntu users got. I thought this because of the aforementioned update-manager having the option to upgrade, but Adept not; I thought that update-manager had somehow 'taken over' the role of upgrading the whole distribution.


Is using the alternate cd to upgrade a good idea? Because I downloaded it, and am itching to use Gutsy (once I verify that my wireless card works with it ;).

---

### Post by exhuma.twn on 2007-11-11
> **FSHero said:**
> ... But I have the feeling that the Ubuntu developers give Kubuntu a second thought.

To clarify: The Ubuntu developers have nothing to do directly with Kubuntu. Kubuntu is developed by a separate team. The same way that all the other *ubuntu's are "ubuntu-mods" developed by a separate team each.

So you should target the rants at the kubuntu devels ;)

---

### Post by exhuma.twn on 2007-11-11
Oh... and I nearly forgot to say. A "clean" kubuntu installation won't have the menu-point you suggested.

---

### Post by FSHero on 2007-11-16
I checked my Adept Updater today (Friday 16th November 2007), and it finally offered me an upgrade.

Had to decline though; I'm on a wireless network so all the packages would download a bit slow and the wireless connection is often unreliable. Furthermore, (with live-cd) Gutsy broke my wireless support... ;(

---

### Post by exhuma.twn on 2007-11-17
Indeed! Upgrade running... now! :D
Patience pais off afterall.

---

### Post by exhuma.twn on 2007-11-18
Apparently I wasn't so lucky afterall. The updater crashed. And it even wouldn't let me send a bug report. Unfortunately I did not have the idea of posting the bug manually. Maybe because I was talking to someone at that point. Well... bad luck.

So, now I sit here with a half-finished update process. Naturally, the "version upgrade" button is now gone again from adept, which makes sense, because I a already switched to the gutsy branch in the sources.list.

Now I am running the rest of the update manually using the conventional "apt". But apart from that, does the updater tool do other things apart from the "dist-upgrade" ? If yes, I would like to know what, so I can work my way through those steps manually.

---

