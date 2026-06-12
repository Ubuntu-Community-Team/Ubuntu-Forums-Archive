---
title: "HOWTO: Upgrade to Intrepid (Pre-Alpha)"
date: 2008-06-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Raptor45 on 2008-06-19
There have been a lot of users having problems with the upgrade to Intrepid. With the delay in Alpha 1, and large interest in testing, I created this howto to get new testers into Intrepid on the right foot, and hopefully cut down on the number of posts asking for help with various issues.

For those who are new to development testing, and think Intrepid may be over your heads, it probably is. However, right now there is a [call]("http://ubuntuforums.org/showpost.php?p=5218520&postcount=6") for testers for the packages in the hardy-proposed repository (updates to hardy which have not yet been released, and may include bugs). This is much easier and safer, yet still very necessary, and could be a more appropriate way for you to contribute to Ubuntu. You can read about enabling the proposed repositories [here]("http://ubuntuforums.org/showthread.php?t=836541") and [here]("http://blog.omma.net/?p=11"). For the rest, who are still interested in Intrepid, please read on.

**Please note the following before upgrading to Intrepid:**

[LIST]
[*]Intrepid is a development release. Breakages are common and to be expected, so only use if you have the time and knowledge to deal with such breakages. It is not recommended to use Intrepid as your main OS, as serious damage may occur.

[*]These instructions only apply while Intrepid is in a pre-alpha state. Once the Alpha 1 iso's are released, installing by CD is the easiest and most reliable method. You can check the release schedule [here]("https://wiki.ubuntu.com/IntrepidReleaseSchedule").
[/LIST]

**To upgrade to Intrepid 8.10:**

[LIST=1]
[*]Start with a fresh install of Hardy 8.04, right off the CD. Do NOT update at this point.

[*]Open your sources.list file for editing by running the following command in a terminal:
```
gksudo gedit /etc/apt/sources.list
```

[*]Use the "Search">"Replace" tool to replace all references to "hardy" with "intrepid". Save and exit the file.

[*]Start Update Manager, hit "Check". If a window comes up asking for a "partial update" press "Cancel" to return to the main update-manager window, and then continue to the next step. NEVER do "partial upgrades" or "dist-upgrades" without checking what is being changed!

[*]Uncheck the "debconf" update, as it will not install properly unless another update has already been applied.

[*]Hit "Install Updates".

[*]Once this is done, start Synaptic, and carefully apply the remaining updates manually. They will appear in the "Installed (upgradeable)" category. Before installing make sure that the update will not remove any important packages, however installing other packages should be fine. If you are unsure whether a specific package should be removed, feel free ask on the forum or IRC.

[*]Once this is done, you can restart and you should be successfully be running Intrepid.
[/LIST]

**Some post install notes:**
[LIST]
[*]If it fails to boot, it may not necessarily be your fault; as Intrepid is in heavy development, the system is not always in a bootable state. You can wait and hope a fix is release, or try to diagnose the problem. You can always check the forum to see if people are having problems similar to yours.
[*]Never install updates by doing a "dist-upgrade" or a partial upgrade. These tools can remove important packages if dependencies are not met, which occurs quite often in the developmental version. The better solution is to do a regular update, and then use synaptic to check what is being removed. If it is a dependency issue, just wait until all the correct packages are added to the repository.
[/LIST]

Let me know if you see any issues or have any suggestions to make on the above. Good luck!

---

### Post by Amaranth on 2008-06-21
I would say if you don't know this already it is way too early to run intrepid. Look at the work I had to do just to get the nvidia driver right now. I don't think people that needs this guide would be able to get nvidia working.

---

### Post by Raptor45 on 2008-06-21
I would agree that those who don't already know this information probably aren't ready, but that has never been a barrier to the curious.

There is a lot of misinformation about running a developmental release (namely "dist-upgrade"), which causes a lot of inexperienced users to run into some unnecessary problems. My hope for this howto is that it will cut down on some of the posts about issues caused by installing or updating incorrectly, as well as providing some decent basic knowledge for new testers.

You don't need the nvidia driver to run Intrepid, so I don't really see that as a barrier. You can just use vesa or nv and wait it out. Compiling the nvidia driver from source really isn't a good long-term solution anyway, and is not necessarily helpful from a testing standpoint.

---

### Post by mouz_forum on 2008-06-21
About hardy-backports testing:

> **Raptor45 said:**
> 
This is much easier and safer, yet still very necessary, and could be a more appropriate way for you to contribute to Ubuntu.


Please add some pointer to an explanation on how to do hardy-backports testing.

---

### Post by Gina on 2008-06-21
Personally, although I had already been testing development versions before, I found the HowTo useful in correcting some misconceptions (such as using dist-upgrade) and clarifying a few points.  And... whilst far from expert in Linux I enjoy learning and sorting out problems but I believe I take a responsible view of the safety of data.  Also, I have had a career in computer programming and systems development and maintenance.

I do agree that a decent knowledge of computer systems and problem solving is a prerequisite of testing an OS at this early stage in development of a new version.  OTOH if someone with a spare machine feels like having a dabble and is happy to "jump in at the deep end"... then why not?

---

### Post by Raptor45 on 2008-06-21
> **mouz_forum said:**
> About hardy-backports testing:



Please add some pointer to an explanation on how to do hardy-backports testing.

I added a link to a post made by Henrik about testing proposed, as well as a link to his blog describing how to get started. I think that pretty much covers it, but if theres anything better let me know.

---

### Post by Gina on 2008-06-21
I have Hardy proposed selected on all my machines and use the updated Hardy for all my main computing.  I also run the Hardy release version (without proposed updates) to check maintenance updates.  Plus Intrepid on my test desktop (AMD64 with NVidia graphics) and laptop (older 32 bit with ATI graphics) when I'm in the mood for testing the very latest stuff.

I should add... The Hardy versions are working fine and it's going well.  Intrepid is fine on my laptop (avoiding partial updates) and usable (albeit at low res) on my AMD64.  I'm not bothering to fiddle with compiling patches to the NVidia driver at this time as I agree that it would not really achieve anything useful towards the testing schedule.

---

### Post by plun on 2008-06-21
> **Raptor45 said:**
> I added a link to a post made by Henrik about testing proposed, as well as a link to his blog describing how to get started. I think that pretty much covers it, but if theres anything better let me know.

If possible more users must be involved.

Within the "cafe" there are a lot of "lost users" which just
spend their time with endless discussions if the "earth is round or flat".

Invite also them to testing and maybe a "newbie warning" about risks.

:)

---

### Post by Manosdoc on 2008-06-22
Virtual Boxes Ready to Test And report:)

---

### Post by autocrosser on 2008-06-22
I did setup the nVidia driver because it's fun to play UT2004 whilst waiting for updates ;)

---

### Post by philinux on 2008-06-23
Followed this even though I've done this last year for Hardy testing. Memory goes when you've slept.

Anyway, just an account as someone new to testing might see it.

1. ok fresh install no problems. No updates.
2. Change hardy to intrepid, piece of cake.
3. update manager says partial upgrade so close that.
4. Update icon in system tray show 608 updates. Advice to install these one by one checking as you go. No chance.

5. Did apt-get upgrade and this says. 608 upgraded 0 to remove and 146 not upgraded, meaning held back.

Surely this is a better way to go using apt-get updrade, if any removed wait?

---

### Post by plun on 2008-06-23
> **philinux said:**
> 

5. Did apt-get upgrade and this says. 608 upgraded 0 to remove and 146 not upgraded, meaning held back.

Surely this is a better way to go using apt-get updrade, if any removed wait?

dist-upgrade  :)

And to mix **apt** and **aptitude** commands.

But... there is no exact "wisdom" when to perform what.

Its about when and where it brakes, if its several breakages and what specific Aptitude solution you chooses.


Also a paper and pencil or a printer for removing solutions and later installs.  (this can also be from a tty if X brakes)


For the moment only **libdb-dev** is kept back for me.


O:)

---

### Post by philinux on 2008-06-23
The stick says don't do dist-upgrade.

Last time with hardy I only ever used apt-get update and upgrade. If anything was indicated for removal I waited or double checked what it was.

---

### Post by plun on 2008-06-23
> **philinux said:**
> The stick says don't do dist-upgrade.

Last time with hardy I only ever used apt-get update and upgrade. If anything was indicated for removal I waited or double checked what it was.

Well, some users have a tag with the difference between Debian and Ubuntu and this is the difference...:)

It is impossible to say "Yes or No" because of how a package system works.


This is **our Mums** basic knowledge :):

[http://www.debian.org/doc/manuals/apt-howto/](http://www.debian.org/doc/manuals/apt-howto/)

[http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/](http://algebraicthunk.net/~dburrows/projects/aptitude/doc/en/)


Easiest for a newbie is to forget about it and just wait... for someone
which wants to learn this is basic knowledge about Debians package system which we all uses.

dist-upgrade or just a upgrade... a user with knowledge checks everything before any command is done.

And in the beginning it will be breaks sometimes also complete breaks.

Don't be afraid of learning this stuff... !!

---

### Post by Raptor45 on 2008-06-23
> **philinux said:**
> Followed this even though I've done this last year for Hardy testing. Memory goes when you've slept.

Anyway, just an account as someone new to testing might see it.

1. ok fresh install no problems. No updates.
2. Change hardy to intrepid, piece of cake.
3. update manager says partial upgrade so close that.
4. Update icon in system tray show 608 updates. Advice to install these one by one checking as you go. No chance.

5. Did apt-get upgrade and this says. 608 upgraded 0 to remove and 146 not upgraded, meaning held back.

Surely this is a better way to go using apt-get updrade, if any removed wait?

You are missing a step. After closing the partial upgrade window (your step 3 here) it is safe to press Install Updates. This will proceed to install all the updates which do not have dependency conflicts. (This is equivalent to an apt-get upgrade). Afterwards you will be left with a rather smaller list of packages which it couldn't install, which you should go into synaptic and examine one at a time. If you question whether a package is safe to remove or not, feel free to ask here or on IRC.

EDIT: I tried to make the process a little clearer in the original post. Is that more helpful?

---

### Post by philinux on 2008-06-23
Much clearer, I was posing this as if someone new to testing wanted to have a go.

I've got a spare HD and three VM's so it's not going to break my main system.

Although I think the debconf issue has gone away with later updates.

The last VM I installed had no such issue.

---

### Post by dgf on 2008-06-23
Why should one use update-manager? The first time I really heard of it, was after hardy, but then it was too late. I always upgraded with aptitude using dist-upgrade, and it worked fine, resolving conflicts, too.
What is the benefit for me if I use update-manager for a update from hardy to intrepid?
I was only allways reading that one should use update-manager but not why.

---

### Post by plun on 2008-06-24
> **dgf said:**
> Why should one use update-manager? The first time I really heard of it, was after hardy, but then it was too late. I always upgraded with aptitude using dist-upgrade, and it worked fine, resolving conflicts, too.
What is the benefit for me if I use update-manager for a update from hardy to intrepid?
I was only allways reading that one should use update-manager but not why.

Well, you cannot use the update-manager.

This is **development software under transient conditions** and until
this i more stable forget about the update-manager

This the method I follows, also with a mix with Aptitude commands and proposals for a solution.

[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)

Every tester uses this method...  partial-upgrade and be lost in the djungle...

I also saw that new meta packages was accepted so maybe the update-manager can be used for a while until it breaks again...:)

---

### Post by Raptor45 on 2008-06-24
> **plun said:**
> Well, you cannot use the update-manager.

This is **development software under transient conditions** and until
this i more stable forget about the update-manager

This the method I follows, also with a mix with Aptitude commands and proposals for a solution.

[https://help.ubuntu.com/community/FeistyUpgradesManual](https://help.ubuntu.com/community/FeistyUpgradesManual)

Every tester uses this method...  partial-upgrade and be lost in the djungle...

I also saw that new meta packages was accepted so maybe the update-manager can be used for a while until it breaks again...:)

The facts here are very incorrect.

Yes, of COURSE you CAN use update-manager, it has never been broken.

Following that guide could lead to issues and is old, I wouldn't advise looking at it.

---

### Post by plun on 2008-06-24
> **Raptor45 said:**
> The facts here are very incorrect.

Yes, of COURSE you CAN use update-manager, it has never been broken.

Following that guide could lead to issues and is old, I wouldn't advise looking at it.

No the facts is not incorrect if you read the manual.

This is NOT a newbie forum or a forum for a distribution upgrade.
Of course the update-manager should be used for stable software.


This IS unstable, often broken development software and users which ** must learn the package system and Launchpad**.


Otherwise this user must wait until a more stable "test point".


Its better to learn more users "the noble art" of package handling.
and also when something goes totally wrong.

IMHO...:)


PS BACKUPS...!!!  Home on separate partition ? and so on... DS

---

### Post by Raptor45 on 2008-06-24
Your manual itself says that following that method is not recommended:

> Please note - this method is less reliable. If you use this method, you MUST be prepared to fix problems manually, such as packages being unexpectedly removed, apt crashing unexpectedly, etc. It is highly recommended that you use the automatic upgrade instructions on FeistyUpgrades instead. 

FeistyUpgrades uses the upgrade-manager to upgrade, because for moving between stable releases the upgrade-manager does some extra work, and is much safer.

However, the entire guide is irrelevant as it refers to upgrading to a stable version of Feisty. That is why it says to use dist-upgrade, as in general on a stable release this is a safe procedure (although still not one I would recommend.) The reason it is generally safe when upgrading to a stable release is that there should not be any dependency issues in the repositories at that point, and any packages a dist-upgrade would remove or add should be safe.

This is not the case in the developmental release, as it is quite likely that there will be dependency issues. The update-manager can be used in either stable or unstable conditions. It performs essentially the same functions as apt-get, except with a GUI. "Check" does the same as "apt-get update", "Install updates" as "apt-get upgrade", and "Partial upgrade" as "dist-upgrade". Either tool can be used at any point in development.

> This IS unstable, often broken development software and users which  must learn the package system and Launchpad.

Otherwise this user must wait until a more stable "test point".

There is no reason that at any point in development the package system should be broken or unstable. If packages do not yet have appropriate dependencies in the repository, they should simply not be installed; nothing must be broken to "force" them in. That kind of breakage will only occur by wayward dist-upgrades removing important packages. From a package standpoint, no point in development is really more or less stable than another, some packages just may need to be held-back until they are ready. The software itself may be buggy, but that is another problem entirely.

---

### Post by plun on 2008-06-24
> **Raptor45 said:**
> Your manual itself says that following that method is not recommended:



There is no reason that at any point in development the package system should be broken or unstable. If packages do not yet have appropriate dependencies in the repository, they should simply not be installed; nothing must be broken to "force" them in. That kind of breakage will only occur by wayward dist-upgrades removing important packages. From a package standpoint, no point in development is really more or less stable than another, some packages just may need to be held-back until they are ready. The software itself may be buggy, but that is another problem entirely.


The manual says that you must be prepared for manual fixes , thats the key point.

Everything IS "time less" for this, this is **basic stuff** for Debian package management.

If its feisty, intrepid, dapper is the same just to change whatever you want. In this case hardy > intrepid.


At the moment we are running nearly **_Debian Sid _** and for sure
its unstable with several brakes...


If OO or Rhythmbox or whatever is broken doesn't stop me from upgrading
other packages after checking Ubuntus package database or if I knows it already.


I am not going to argue more with you about this.

"A Ubuntu user CAN run Debian", 100% sure....:)

Let the testing begin...!

---

### Post by psyke83 on 2008-06-24
> **plun said:**
> If OO or Rhythmbox or whatever is broken doesn't stop me from upgrading
other packages after checking Ubuntus package database or if I knows it already.

The operative word is "**me**". The problem is that other less experienced users will use those instructions, then potentially allow dist-upgrade to remove half of their system without even realizing what they did.

---

### Post by plun on 2008-06-24
> **psyke83 said:**
> The operative word is "**me**". The problem is that other less experienced users will use those instructions, then potentially allow dist-upgrade to remove half of their system without even realizing what they did.

No, the operative word should be "**learning**"....

"Aha, its broken.. well I download todays ISO instead of learning
howto fix a breakage." What a waist of band with...:)

More users must learn these secrets...

Aha, this package depends on this and this...

Looks scary or OK to remove. (or find a walk around)

I think the MOTU group needs more users and also bug squad
and this is indeed basic knowledge.

I dont know any other way to learn this....:confused:

---

### Post by Raptor45 on 2008-06-24
You don't have to be prepared for fixes, or do any kind of manual repairs, if you follow a reasonable process... as nothing will break in the first place.

Although Ubuntu is based on Debian and they are very closely related, we are not running Debian Sid. Thats just plain wrong.

If OO is broken, as you suggest, then the correct solution is to simply not upgrade it yet. Doing a dist-upgrade to force it in is just an outright bad idea, while an ordinary upgrade will hold back the broken packages and just do everything else, leaving your system in a stable state. If you want to force packages to install thats your call, but there is no benefit to it, and can only lead to all kinds of hell down the road.

Reading your replies, it seems clear that you yourself don't have a very good understanding of how the system functions, despite your claims otherwise. Although you seem unwilling to correct your ignorance, I would greatly appreciate if you did not confuse other users in this regard. The subject can be confusing enough, without new people reading incorrect statements which further common misconceptions.

> "Aha, its broken.. well I download todays ISO instead of learning
howto fix a breakage." What a waist of band with...

I'm not entirely sure how you are running your own computer, but there is no reason you should wind up with a broken package in the first place, unless you are doing something wrong. And in fact, for testing purposes, it is far better to be running a fresh install rather than one you've hacked up with random fixes which may cause new problems.

If you, or anyone, would like to learn more, please ask questions and read up on materials online. I am happy to help those who help themselves, and are receptive to improving their understanding. Know-it-alls who spread inaccurate information are a detriment to the community as a whole.

---

### Post by plun on 2008-06-25
> **Raptor45 said:**
> You don't have to be prepared for fixes, or do any kind of manual repairs, if you follow a reasonable process... as nothing will break in the first place.

Although Ubuntu is based on Debian and they are very closely related, we are not running Debian Sid. Thats just plain wrong.

If OO is broken, as you suggest, then the correct solution is to simply not upgrade it yet. Doing a dist-upgrade to force it in is just an outright bad idea, while an ordinary upgrade will hold back the broken packages and just do everything else, leaving your system in a stable state. If you want to force packages to install thats your call, but there is no benefit to it, and can only lead to all kinds of hell down the road.

Reading your replies, it seems clear that you yourself don't have a very good understanding of how the system functions, despite your claims otherwise. Although you seem unwilling to correct your ignorance, I would greatly appreciate if you did not confuse other users in this regard. The subject can be confusing enough, without new people reading incorrect statements which further common misconceptions.



I'm not entirely sure how you are running your own computer, but there is no reason you should wind up with a broken package in the first place, unless you are doing something wrong. And in fact, for testing purposes, it is far better to be running a fresh install rather than one you've hacked up with random fixes which may cause new problems.

If you, or anyone, would like to learn more, please ask questions and read up on materials online. I am happy to help those who help themselves, and are receptive to improving their understanding. Know-it-alls who spread inaccurate information are a detriment to the community as a whole.

Well.....

- What is a Debian import ?  from where ?

- If a package is broken, X days,  I am not joining a **"whining" thread** about this, I remove this package/packages or find a walk around. (a simple remove or uses aptitude for a solution, also checking Ubuntus package database).

- When its fixed I installs it again.


This is not inaccurate information....


Your argumentation reminds me about a company from Redmond and their
thoughts about users.:(  Just terrible testing.

[http://connect.microsoft.com/](http://connect.microsoft.com/)


Users which cannot afford a break should stay away from testing....!

More users must learn real package management.

"over and out"...

---

### Post by Raptor45 on 2008-06-25
> **plun said:**
> - What is a Debian import ?

Ubuntu does import packages from Debian, and devs do try to keep packages as close as possible by sending stuff upstream, but to say Ubuntu=Debian would be a stretch. Closely related, yes. Running Sid, no.

> - If a package is broken, X days,  I am not joining a **"whining" thread** about this, I remove this package/packages or find a walk around. (a simple remove or uses aptitude for a solution, also checking Ubuntus package database).

- When its fixed I installs it again.

You are welcome to do as you like, of course. However I'm a bit confused about what you're doing here.

Do you mean to say that if, say, part of open office hits the repositories, you remove the conflicting packages? This is where I'm not understanding your argument. It sounds to me like you are forcing unready upgrades with a dist-upgrade, even if it requires removing things. Why do this? It isn't necessary, by any means.

You can, instead, simply leave unready packages in the "held-back" state as a normal upgrade does. You are free to update everything else, but those packages which are unready (openoffice in this case) will simply remain at their current version until the upgraded ones are ready. This is really a much safer alternative, and does not require you to manually install the packages which got removed by the dist-upgrade later; as they never had to be removed in the first place.

> Your argumentation reminds me about a company from Redmond and their
thoughts about users.:(  Just terrible testing.

Unnecessarily bringing Microsoft into an argument is just an easy cheap shot, which I really don't appreciate, and does not contribute. Please refrain from this in the future.

---

### Post by tz1 on 2008-09-06
So are the ISOs a complete waste of bandwidth and time?  Why make them and post them?

I have an Intrepid ISO DVD build, post alpha-4 for 64bit.  I dual boot hardy in 32bit and 64bit with a shared /home, and thought I could just do a "dist-upgrade" and try 64bit intrepid.  But it doesn't seem to see the DVD as a new/upgrade disk.  How do I point apt at it, is it just adding a cdrom line to apt/sources.list?

---

### Post by cacharreo on 2008-09-29
update-manager -d :guitar:

---

